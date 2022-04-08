(ml)=
# Aprendizaje automático
En física de altas energías (HEP) los datos obtenidos de experimentos son sumamente complejos y de grandes dimensiones. A medida que alcanzamos mayores energías en los aceleradores de partículas, conseguimos nuevos desafíos debido al aumento en el tamaño de los eventos, el volumen de datos y su complejidad. Por esto, en la última década ha existido un enfoque en el estudio y la mejora de métodos y herramientas de análisis de datos, puesto que el alcance de los experimentos puede ser limitado por el rendimiento de algoritmos y de recursos computacionales. El aprendizaje automático es una herramienta que promete mejoras en estas áreas.

En este capítulos se presentan brevemente conceptos básicos de aprendizaje automático y un resumen de su uso en HEP. Información más detallada sobre este tema se encuentra en {cite}`Mehta_2019,Bourilkov_2019`. Una recopilación al día de las investigaciones relacionadas a aprendizaje automático y física de partículas se encuentra en {cite}`hepmllivingreview`
(ml-conceptos)=
## Conceptos básicos
El aprendizaje automático es un subcampo de la inteligencia artificial. Tiene como objetivo el desarrollo de algoritmos que mejoran su desempeño de manera cuantificable en una tarea determinada mediante un proceso de entrenamiento que utiliza grandes conjuntos de datos.

Típicamente los problemas hacen uso de un conjunto de datos $\mathcal{D}=(\mathbf{X},\mathbf{y})$ donde $\mathbf{X}$ es una matriz de variables independientes $\mathbf{y}$ es un vector de variables dependientes. La tarea es optimizar un modelo $f(\mathbf{x};\mathbf{\theta})$ tal que $f:\mathbf{x}\rightarrow y$ de los parámetros $\mathbf{\theta}$. Esto es, *f* es una función utilizada para predecir una única salida de un vector de varibles de entrada. Esta función optimiza alguna métrica escogida que se conoce como función de pérdida o costo $\mathcal{L}(\mathbf{y},f(\mathbf{x}))$. Esto se logra encontrando el valor de $\mathbf{\theta}$ que minimiza $\mathcal{L}${cite}`Mehta_2019`.

El **proceso de aprendizaje** de un algoritmo se puede resumir en los siguientes pasos:
1. Usualmente es necesario pre-procesar los datos. En HEP esto puede ser, por ejemplo, mediante el calculo de variables físicas. En este paso es común incluir el normalizar o escalar los datos y disminución de dimensiones.
2. Se divide aleatoreamente $\mathcal{D}$ en dos conjuntos mutuamente exclusivos de entrenamiento y prueba. $\mathcal{D}_{train}$ y $\mathcal{D}_{test}$, respectivamente. Se suele utilizar la mayor parte de los datos para entrenamiento. Por ejemplo, 70% entrenamiento y 30% prueba.
3. El ajuste del modelo se hace minimizando la función de pérdida utilizando los datos de entrenamiento $\mathbf{\hat{\theta}}=\text{arg min}_{\theta}\{\mathcal{L}(\mathbf{y}_{train},f(\mathbf{X}_{train};\mathbf{\theta}))\}$
1. Finalmente, el rendimiento del modelo se evalua calculando la función de pérdida con los datos de prueba $\mathcal{L}(\mathbf{y}_{test},f(\mathbf{X}_{test};\mathbf{\hat{\theta}}))$.

El aprendizaje automático se puede dividir en tres categorías: aprendizaje supervisado, aprendizaje no-supervisado y aprendizaje reforzado. Aunque la distinción es útil, se suelen combinar estos tipos de aprendizaje, por lo que los términos se suelen utilizar de manera imprecisa y pueden ser confusos.

En este proyecto es de interés el aprendizaje supervisado y no supervisado debido al tipo de problemas que se quieren 
(ml-supervisado)=
## Aprendizaje supervisado
El aprendizaje supervisado se refiere al aprendizaje a partir de datos etiquetados (por ejemplo, en HEP podría ser datos etiquetados como que *contienen señal* o que *no contienen señal*). Las tareas comunes incluyen *clasificación*, cuando el objetivo de aprendizaje *y* es discreto y finito, y *regresión*, cuando *y* es continuo o discreto e infinito{cite}`Karagiorgi_2021`.

Los problemas que se tratan en este proyecto son de clasificación binaria, es decir, clasificación de dos clases. Por esot, el siguiente segmento estará enfocado en la presentación de álgunos algoritmos de clasificación, enfocado en el caso de clasificación binaria. Sin embargo, algunos son modelos combinados y es necesario presentar primero los *métodos de ensamble*.

### Métodos de ensamble 
Los *métodos de ensamble* utilizan conjuntos de algoritmos de aprendizaje automático cuyas decisiones se combinan para mejorar el rendimiento del sistema en general. Estos métodos han probado solucionar deficiencias estadísticas, computacionales y de representación. Estas están explicadas en la siguiente discusión de {cite}`louppe2015understanding`

> La primera razón es estadística. Cuando el conjunto de aprendizaje es muy pequeño, el algoritmo de aprendizaje normalmente puede encontrar varios modelos en el espacio de hipótesis $\mathcal{H}$ que dan el mismo rendimiento en los datos de entrenamiento. Siempre que sus predicciones no estén correlacionadas, promediar varios modelos reduce el riesgo de elegir la hipótesis incorrecta. La segunda razón es computacional. Muchos algoritmos de aprendizaje se basan en algunas suposiciones codiciosas o búsquedas locales que pueden atascarse en los óptimos locales. Como tal, un conjunto formado por modelos individuales construidos a partir de muchos puntos de partida diferentes puede proporcionar una mejor aproximación de la verdadera función desconocida que cualquiera de los modelos individuales. Finalmente, la tercera razón es representacional. En la mayoría de los casos, para un conjunto de aprendizaje de tamaño finito, la verdadera función no puede ser representada por ninguno de los modelos candidatos en $\mathcal{H}$. Al combinar varios modelos en un conjunto, puede ser posible expandir el espacio de funciones representables y modelar mejor la verdadera función.

Existen varios métodos de ensamble. De acuerdo a los algoritmos que se explicaran más adelante, es de interés el método de *boosting*
#### Boosting
El *boosting* es un tipo de método de ensamble basado en la idea de que hallar varias reglas generales aproximadas puede ser más sencillo que hallar una regla general altamente precisa{cite}`Schapire2003`. Este método se aplica utilizando un conjunto de algoritmos con poca precisión o *aprendices débiles* $\{g_k(\mathbf{x})\}$. Inicialmente, un aprendiz débil halla una regla aproximada haciendo uso de un subconjunto de datos de entrenamiento. A cada clasificador se le asocia un peso $\alpha_k$ que indica cuánto contribuye al clasificador general

$$
    g_A(\mathbf{x})=\sum_{K=1}^{M} \alpha_K g_K(\mathbf{x})
$$ (ml-boosting)

donde $\sum_k \alpha_k=1$

### Algoritmos de clasificación
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
El análisis de discriminante cuadrático es un *modelo discriminante* con un límite de decisión cuadrático. 

#### Redes neuronales

(ml-nosupervisado)=
## Aprendizaje no-supervisado
Este tipo de aprendizaje se ocupa de hallar patrones y estructuras en datos no etiquetados. Ejemplos de tareas comunes de algoritmos no-supervisados incluyen agrupamiento, reducción de dimensiones, modelado generativo y detección de anomalías.

### K-means

(ml-metricas)=
## Métricas de rendimiento

## Aprendizaje automático en HEP
https://arxiv.org/pdf/1912.08245.pdf 
https://arxiv.org/pdf/1806.11484.pdf

### Clasificación y selección de eventos

### Detección de anomalías
