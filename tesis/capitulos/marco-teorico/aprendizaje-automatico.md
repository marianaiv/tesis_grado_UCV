(ml)=
# Aprendizaje automático
En física de altas energías (HEP) los datos obtenidos de experimentos son sumamente complejos y de grandes dimensiones. A medida que alcanzamos mayores energías en los aceleradores de partículas, conseguimos nuevos desafíos debido al aumento en el tamaño de los eventos, el volumen de datos y su complejidad. Por esto, en la última década ha existido un enfoque en el estudio y la mejora de métodos y herramientas de análisis de datos, puesto que el alcance de los experimentos puede ser limitado por el rendimiento de algoritmos y de recursos computacionales. El aprendizaje automático es una herramienta que promete mejoras en estas áreas.

En este capítulos se presentan brevemente conceptos básicos de aprendizaje automático y un resumen de su uso en HEP. Información más detallada sobre este tema se encuentra en {cite}`Mehta_2019,Bourilkov_2019`. Una recopilación al día de las investigaciones relacionadas a aprendizaje automático y física de partículas se encuentra en {cite}`hepmllivingreview`

(ml-conceptos)=
## Conceptos básicos
El aprendizaje automático es un subcampo de la inteligencia artificial. Tiene como objetivo el desarrollo de algoritmos que mejoran su desempeño de manera cuantificable en una tarea determinada mediante un proceso de entrenamiento que utiliza grandes conjuntos de datos.

Típicamente los problemas hacen uso de un conjunto de datos $\mathcal{D}=(\mathbf{X},\mathbf{y})$ donde $\mathbf{X}$ es una matriz de variables independientes $\mathbf{y}$ es un vector de variables dependientes. La tarea es optimizar un modelo $f(\mathbf{x};\mathbf{\theta})$ tal que $f:\mathbf{x}\rightarrow y$ de los parámetros $\mathbf{\theta}$. Esto es, $f$ es una función utilizada para predecir una única salida de un vector de varibles de entrada. La funcion $f$ optimiza alguna métrica escogida que se conoce como función de pérdida o costo $\mathcal{L}(\mathbf{y},f(\mathbf{x}))$, lo que se logra encontrando el valor de $\mathbf{\theta}$ que minimiza $\mathcal{L}${cite}`Mehta_2019`.

El **proceso de aprendizaje** de un algoritmo se puede resumir en los siguientes pasos:
1. Pre-procesamiento de datos. En HEP puede ser, por ejemplo, mediante el cálculo de variables físicas. En este paso es común normalizar o escalar los datos y disminuir sus dimensiones .
2. Se divide aleatoreamente $\mathcal{D}$ en dos conjuntos mutuamente exclusivos de entrenamiento y prueba. $\mathcal{D}_{train}$ y $\mathcal{D}_{test}$, respectivamente. Se suele utilizar la mayor parte de los datos para entrenamiento. Por ejemplo, 70% entrenamiento y 30% prueba.
3. El ajuste del modelo se hace minimizando la función de pérdida utilizando los datos de entrenamiento $\mathbf{\hat{\theta}}=\text{arg min}_{\theta}\{\mathcal{L}(\mathbf{y}_{train},f(\mathbf{X}_{train};\mathbf{\theta}))\}$
4. Finalmente, el rendimiento del modelo se evalúa calculando la función de pérdida con los datos de prueba $\mathcal{L}(\mathbf{y}_{test},f(\mathbf{X}_{test};\mathbf{\hat{\theta}}))$.

El aprendizaje automático se puede dividir en tres categorías: aprendizaje supervisado, aprendizaje no-supervisado y aprendizaje reforzado. Aunque la distinción es útil, se suelen combinar estos tipos de aprendizaje, por lo que los términos se suelen utilizar de manera imprecisa y pueden ser confusos. En este proyecto se utilizarán métodos de aprendizaje supervisado y no supervisado.

(ml-supervisado)=
## Aprendizaje supervisado
El aprendizaje supervisado se refiere al aprendizaje a partir de datos etiquetados (por ejemplo, en HEP podría ser datos etiquetados como que *contienen señal* o que *no contienen señal*). Las tareas comunes incluyen *clasificación*, cuando el objetivo de aprendizaje $y$ es discreto y finito, y *regresión*, cuando $y$ es continuo o discreto e infinito{cite}`Karagiorgi_2021`.

Los problemas que se tratan en este proyecto son de clasificación binaria, es decir, clasificación de dos clases. A continuación, se presentarán los algoritmos que se van a utilizar. Sin embargo, algunos modelos son combinados y es necesario presentar primero los *métodos de ensamble*.

### Métodos de ensamble 
Los *métodos de ensamble* utilizan conjuntos de algoritmos de aprendizaje automático cuyas decisiones se combinan para mejorar el rendimiento del sistema en general. Estos métodos han probado solucionar deficiencias estadísticas, computacionales y de representación. Las razones para usar estos métodos están explicadas en {cite}`louppe2015understanding`:

1. **Estadística**: Cuando el conjunto de aprendizaje es muy pequeño, el algoritmo de aprendizaje normalmente puede encontrar varios modelos en el espacio de hipótesis $\mathcal{H}$ que resultan en el mismo rendimiento. Siempre que sus predicciones no estén correlacionadas, promediar varios modelos reduce el riesgo de elegir la hipótesis incorrecta.
2. **Computacional**: Muchos algoritmos de aprendizaje se basan en suposiciones o búsquedas locales que pueden atascarse en los óptimos locales. Un conjunto formado por modelos individuales construidos a partir de muchos puntos de partida diferentes puede proporcionar una mejor aproximación de la verdadera función desconocida, que cualquier aproximación de los modelos individuales.
3. **Representacional**: En la mayoría de los casos, para un conjunto de aprendizaje de tamaño finito, la verdadera función no puede ser representada por ninguno de los modelos candidatos en $\mathcal{H}$. Al combinar varios modelos en un conjunto, puede ser posible expandir el espacio de funciones representables y modelar mejor la verdadera función.

Existen varios métodos de ensamble, pero, de acuerdo a los algoritmos que se explicarán más adelante, es de interés el método de *boosting*.
#### Boosting
El *boosting* es un tipo de método de ensamble basado en la idea de que hallar varias reglas generales aproximadas puede ser más sencillo que hallar una regla general altamente precisa{cite}`Schapire2003`. Este método se aplica utilizando un conjunto de algoritmos con poca precisión o *aprendices débiles* $\{g_k(\mathbf{x})\}$. Inicialmente, un aprendiz débil halla una regla aproximada haciendo uso de un subconjunto de datos de entrenamiento. A cada clasificador se le asocia un peso $\alpha_k$ que indica cuánto contribuye al clasificador general. El clasificador general se puede expresar matemáticamente como:

$$
    g_A(\mathbf{x})=\sum_{K=1}^{M} \alpha_K g_K(\mathbf{x})
$$ (ml-boosting)

donde $\sum_k \alpha_k=1$.

### Algoritmos
#### Bosque aleatorio
Los bosques aleatorios son utilizados ampliamente para tareas complejas de clasificación. Estos algoritmos son ensambles de árboles de decisión.

Un **arbol de decisión** utiliza una serie de preguntas para realizar la partición jerarquica de los datos. Su objetivo es hallar un conjunto de reglas que naturalmente separen el espacio de características, proporcionando un modelo de clasificación sólido e informativo{cite}`myles_2004`. 

```{figure} ./../../figuras/ml-arboldecision.png
---
width: 600px
name: ml-arboldecision
---
Ejemplo de un árbol de decisión. Para una conjunto de características $\mathbf{x}$, su etiqueta $y$ es predicha, recorriéndolo desde su raiz, pasando por las hojas, siguiendo las ramas que satiface. De {cite}`Mehta_2019`
```
Los *bosques aleatorios* son clasificadores que consisten en una colección de árboles de decisión $\{h(\mathbf{x},\Theta_k),k=1,\dots\}$ donde $\{\Theta_k\}$ son son vectores aleatorios e independientes con la misma distribución. Cada árbol emite un voto unitario para la clase más popular dada la entrada $\mathbf{x}${cite}`Breiman:2001hzm`. La clase con más votos es asignada a esta entrada. 

```{figure} ./../../figuras/ml-bosquealeatorio.png
---
width: 700px
name: ml-bosquealeatorio
---
Representación visual del funcionamiento de un bosque aleatorio. De {cite}`chauhan_2021`
```
#### Clasificador de boosting de gradiente

El clasificador de boosting de gradiente (GBC) usualmente utiliza árboles de regresión como aprendiz débil. Es un modelo aditivo que avanza por etapas{cite}`GBC`. En cada etapa, se ajusta el árbol al error residual, es decir, el error asociado al árbol anterior.

GBC se puede usar para regresión y clasificación. Su formulación matemática es la siguiente{cite}`GTBC`.

La predicción $y_i$ del modelo para la entrada $x_i$ esta dada por:

$$
    \hat{y}_i=F_M(x_i)=\sum_{m=1}^{M}h_m(x_i)
$$ (ml-gbcpred)

donde $h_m$ son los aprendices débiles. En el caso de clasificación, el mapeo del valor de $F_M(x_i)$ a una clase o probabilidad es dependiente de la pérdida. La probabilidad de que $x_i$ pertenezca a la clase positiva se modela usando la función sigmoid $p(y_i=|x_i)=\sigma(F_M(x_i))$

El GBC se construye de la siguiente manera:

$$
    F_m(x)=F_{m-1}(x)+h_m(x)
$$ (ml-gbc)

donde $h_m$ se ajusta para minimizar la suma de las pérdidas $L_m$, dado el ensamble anterior $F_{m-1}$

$$
    h_m\approx\text{arg min}_h\sum_{i=1}^{n}h(x_i)g_i
$$ (ml-gbcaprendizdebil)

donde $g_i$ es la derivada de la función de pérdida con respecto a su segundo parámetro, evaluada en $F_{m-1}(x)$. La suma en {eq}`ml-gbcaprendizdebil` se minimiza si $h(x_i)$ se ajusta para predecir un valor proporcional al gradiente negativo $−g_i$. Por lo tanto, en cada iteración, el estimador $h_m$ está ajustado para predecir los gradientes negativos de las muestras. Los gradientes se actualizan en cada iteración. Este proceso puede considerarse como una especie de descenso de gradiente en un espacio funcional.

#### Análisis de discriminante cuadrático
El análisis de discriminante cuadrático{cite}`QDA` es un clasificador con un límite de decisión cuadrático. El modelo asume que las densidades condicionales de clase $P(\mathbf{X}|y=k)$, para cada clase $k$, están distribuidas normalmente.

Las predicciones para cada muestra de entrenamiento $x$ se obtienen utilizando el teorema de Bayes:

$$
    P(y=k|x) = \frac{P(x|y=k)P(y=k)}{P(x)}
$$

Donde se selecciona la clase $k$ que maximice esta probabilidad.

```{figure} ./../../figuras/ml-qda.png
---
width: 700px
name: ml-qda
---
Clasificación con QDA. a) Lods puntos a ser clasificados, b) los límites o fronteras de decisión. La barra de color indica la probabilidad de pertenecer a la clase 1. De {cite}`QDAimg`
```

#### Redes neuronales
Las redes neuronales son modelos no-lineales inspirados en las neuronas. Aunque su uso es extenso, nos enfocaremos en su aplicación para clasificación binaria.

Las redes neuronales se definen mediante una serie de transformaciones que mapean la entrada $x$ a estados "ocultos" $\mathbf{h}_i$. Finalmente, una transformación final mapea estos estados a una función de salida $\mathbf{y}${cite}`Guest_2018`.

Las transformaciones se pueden escribir matemáticamente como:

$$
    \mathbf{h}_i = g_i(W_i\mathbf{h}_i+\mathbf{b}_i)
$$ (ml-nnneurona)

donde $g_i$ es una función conocida como *función de activación* y $\mathbf{h}_i$ representa la transformación i-ésima de $\mathbf{x}$, llamado *embedding*. $W$ es la matrix de los *pesos* y $\mathbf{b}$ el vector de los *sesgos*.

El objetivo es hallar los pesos y sesgos que optimizan la función de pérdida. Esto se logra utilizando las etiquetas de los datos y calculando el gradiente de la función de pérdida con respecto a los parámetross del modelo. Esto se conoce como *retropropagación* y requiere que las funciones sean diferenciables.

Las transformaciones se ordenan en capas ({numref}`ml-nn`). La salida de una capa es la entrada de la siguiente.

```{figure} ./../../figuras/ml-nn.png
---
width: 500px
name: ml-nn
---
Diagrama de una red neuronal. Las transformaciones se ordenan por capas, donde la salida de una capa es la entrada de la siguiente. De {cite}`Mehta_2019`
```
La tarea de la red depende de su arquitectura. Para utilizar una red neuronal como clasificador binario, se utiliza la función sigmoid como función de activación de la última transformación. Se suele utilizar la *entropía cruzada binaria* como función de pérdida, que calcula la entropía cruzada entre las clases predichas y las clases reales. 

(ml-nosupervisado)=
## Aprendizaje no-supervisado
Este tipo de aprendizaje se ocupa de hallar patrones y estructuras en datos no etiquetados. Ejemplos de tareas comunes de algoritmos no-supervisados incluyen agrupamiento, reducción de dimensiones, modelado generativo y detección de anomalías.

Algunos algoritmos de agrupamiento se pueden utilizar para clasificación, como es el caso de *K-means*

### Algoritmos
#### K-means
*K-means* separa los datos en $K$ grupos con igual varianza. Los grupos están caracterizados por la media de los datos pertenecientes al grupo. Estos se conocen como "centroides" y se representan con $\mu_j${cite}`Kmeans`. 

El objetivo del algoritmo es minimizar la *inercia* o *criterio de suma de cuadrados dentro del grupo*, definida como: 

$$
    \mathcal{C}(\{x,\mathbf{\mu}\})=\sum_{k=1}^{K}\sum_{n=1}^{N}r_{nk}(\mathbf{x}_n-\mu_k)^2
$$ (ml-kmeansinertia)

donde $\mathbf{x}_n$ es la observación enésima y $r_nk$ es la asignación. $r_nk$ es 1 si $x_n$ pertenece al grupo y 0 de otra forma.

El algoritmo sigue los siguientes pasos:
1. Escoger los centroides. En la primera inicialización se escogen puntos aleatorios de los datos.
2. Asignar cada muestra al centroide mas cercano, minimizando $\mathcal{C}$
3. Crear nuevos centroides tomando el valor medio de todas las muestras asignadas a cada centroide anterior.
4. Calcular la diferencia entre los centroides anteriores y los nuevos.

Los últimos tres pasos se repiten hasta que la diferencia entre los centroides esté debajo de un umbral, es decir, hasta que los centroides no se muevan significativamente.

```{figure} ./../../figuras/ml-kmeans.webp
---
width: 400px
name: ml-kmeans
---
Primeras cinco iteraciones de dos inicializaciones diferentes de K-means. De {cite}`Kmeansgif`
```
Como la inicialización de los centroides es aleatoria, usualmente se realizan múltiples inicializaciones se escoge la que resulte en un menor valor de la inercia.

(ml-metricas)=
## Métricas de rendimiento

## Aprendizaje automático en HEP
https://arxiv.org/pdf/1912.08245.pdf 
https://arxiv.org/pdf/1806.11484.pdf

### Clasificación y selección de eventos

### Detección de anomalías
