(alg)=
# Algoritmos para detección de anomalías
En este proyecto se trata de resolver un problema de clasificación binaria con los datos de las LHCO 2020, que son altamente desbalanceados. Esto se conoce como una tarea de *detección de anomalías*, que en el caso de este trabajo hace referencia a la detección de los eventos de señal.

La implementación de aprendizaje automático en este trabajo está comprendida por los siguientes pasos:
1. Pre-procesamiento de los datos utilizando `benchtool`, descrito en la {numref}`bench-pre`
2. Divición de los datos en conjuntos mutuamente excluyentes. 70% en un conjunto de entrenamiento y 30% en uno de prueba. 
3. Ajuste del modelo minimizando una función de pérdida específica, utilizando los datos de entrenamiento. Estas funciones se describirán más adelante en esta sección.
4. Evaluación del rendimiento del modelo calculando la función de pérdida con los datos de prueba.

Los algoritmos utilizados en este trabajo se escogieron a partir de su rendimiento, estudiado durante el desarrollo de las herramientas de análisis de datos. Más información sobre cómo se escogieron estos algoritmos se encuentra en la sección *[notebooks](https://github.com/marianaiv/benchtools/tree/main/notebooks)* del repositorio de `benchtools`.

A continuación, se explicarán los algoritmos utilizados, enfocándonos en su uso para la tarea de clasificación binaria. También se resumirán algunos métodos necesarios para explicar más adelante los algoritmos de las LHCO 2020 utilizados en este trabajo. La referencia principal de esta sección es {cite}`Mehta_2019`.

(alg-bosques)=
## Bosque aleatorio
Los bosques aleatorios son algoritmos supervisados ampliamente utilizados para tareas complejas de clasificación. Estos algoritmos son ensambles de árboles de decisión.

Un **árbol de decisión** utiliza una serie de preguntas para realizar la partición jerárquica de los datos. Su objetivo es hallar un conjunto de reglas que separen naturalmente el espacio de características{cite}`myles_2004`. La partición de los datos se hace hallando los parámetros que minimizan el *criterio de impureza*. Uno de los criterios más utilizado es el criterio *Gini*, que mide cuánto ruido tiene una categoría:

$$
    H(Q_m)=\sum_{k} p_{mk}(1-p_{mk})
$$ (gini)

donde $Q_m$ representa los datos en el nodo $m$ y $p_{mk}$ es la proporción de clase $k$ observada en el nodo $m$, donde las clases para clasificación binaria son 0 y 1. Un diagrama de un árbol de decisión se observa en la {numref}`ml-arboldecision`.

```{figure} ./../../figuras/ml-arboldecision.png
---
width: 450px
name: ml-arboldecision
---
Ejemplo de un árbol de decisión. Para una conjunto de características $\mathbf{x}$, su etiqueta $y$ es predicha, recorriéndolo desde su raíz, pasando por las hojas, siguiendo las ramas que satisface {cite}`Mehta_2019`.
```
Para crear un ensamble de árboles de decisión y obtener un bosque aleatorio, se deben utilizar procesos de aleatorización, con el propósito de disminuir la correlación entre los árboles y así, disminuir la varianza. Usualmente se utilizan en conjunto dos métodos. Los subconjutos de datos utilizados para entrenar cada árbol se obtienen del conjunto de entrenamiento mediante bootstrapping, un método de muestreo con remplazo. Luego, en la construcción de los árboles de decisión, en cada nodo se utiliza un subconjunto aleatorio de las características de entrada. 

Usualmente, cada árbol emite un voto unitario para la clase más popular dada una entrada y la clase con más votos es asignada a esta entrada{cite}`Breiman:2001hzm`, como se observa en la {numref}`ml-bosquealeatorio`. Sin embargo, la implementación utilizada en este trabajo combina los árboles individuales promediando su predicción probabilística{cite}`RFC`.

```{figure} ./../../figuras/ml-bosquealeatorio.png
---
width: 550px
name: ml-bosquealeatorio
---
Representación visual del funcionamiento de un bosque aleatorio {cite}`chauhan_2021`
```
(alg-gbc)=
## Clasificador del gradiente del impulso

El clasificador del gradiente del impulso (GBC) usualmente utiliza árboles de regresión como aprendiz débil. Es un modelo supervisado y aditivo que avanza por etapas{cite}`GBC`. En cada etapa, se ajusta el árbol al error residual, es decir, el error asociado al árbol anterior. Su formulación matemática es la siguiente{cite}`GTBC`:

La predicción $y_i$ del modelo para la entrada $x_i$ está dada por:

$$
    \hat{y}_i=F_M(x_i)=\sum_{m=1}^{M}h_m(x_i)
$$ (ml-gbcpred)

$h_m$ son los aprendices débiles. En el caso de clasificación, el mapeo del valor de $F_M(x_i)$ a una clase o probabilidad es dependiente de la pérdida. La probabilidad de que $x_i$ pertenezca a la clase positiva se modela usando la función sigmoid $p(y_i=|x_i)=\sigma(F_M(x_i))$

El GBC se construye de la siguiente manera:

$$
    F_m(x)=F_{m-1}(x)+h_m(x)
$$ (ml-gbc)

$h_m$ se ajusta para minimizar la suma de las pérdidas dado el ensamble anterior $F_{m-1}$

$$
    h_m\approx\text{arg min}_h\sum_{i=1}^{n}h(x_i)g_i
$$ (ml-gbcaprendizdebil)

donde $g_i$ es la derivada de la función de pérdida con respecto a su segundo parámetro, evaluada en $F_{m-1}(x)$. La suma en la ec.{eq}`ml-gbcaprendizdebil` se minimiza si $h(x_i)$ se ajusta para predecir un valor proporcional al gradiente negativo $−g_i$. Por lo tanto, en cada iteración, el estimador $h_m$ está ajustado para predecir los gradientes negativos de las muestras. Estos gradientes se actualizan en cada iteración. El proceso puede considerarse como una especie de descenso de gradiente en un espacio funcional.

(alg-qda)=
## Análisis de discriminante cuadrático
El análisis de discriminante cuadrático{cite}`QDA` es un clasificador supervisado con un límite de decisión cuadrático. El modelo asume que las densidades condicionales de clase $P(\mathbf{X}|y=k)$, para cada clase $k$, están distribuidas normalmente.

Las predicciones para cada muestra de entrenamiento $x$ se obtienen utilizando el teorema de Bayes:

$$
    P(y=k|x) = \frac{P(x|y=k)P(y=k)}{P(x)}
$$

Donde se selecciona la clase $k$ que maximice esta probabilidad. Un ejemplo de clasificación utilizando este método se observa en la {numref}`ml-qda`.

```{figure} ./../../figuras/ml-qda.png
---
width: 500px
name: ml-qda
---
Clasificación con QDA. a) Los puntos a ser clasificados, b) los límites o fronteras de decisión. La barra de color indica la probabilidad de pertenecer a la clase 1. De {cite}`QDAimg`
```

(alg-neural)=
## Redes neuronales
Las redes neuronales son modelos supervisados y no-lineales inspirados en las neuronas. Aunque su uso es extenso, nos enfocaremos en su aplicación para clasificación binaria.

Las redes neuronales se definen mediante una serie de transformaciones que mapean la entrada $x$ a estados "ocultos" $\mathbf{h}_i$. Finalmente, una última transformación mapea estos estados a una función de salida $\mathbf{y}${cite}`Guest_2018`. Esto también se conoce como perceptrón multicapas.

Las transformaciones se pueden escribir matemáticamente como:

$$
    \mathbf{h}_i = g_i(W_i\mathbf{h}_i+\mathbf{b}_i)
$$ (ml-nnneurona)

donde $g_i$ es una función conocida como *función de activación* y $\mathbf{h}_i$ representa la transformación iésima de $\mathbf{x}$, llamada *encaje*. $W$ es la matriz de los *pesos* y $\mathbf{b}$ el vector de los *sesgos*.

El objetivo es hallar los pesos y sesgos que optimizan la función de pérdida. Esto se logra utilizando las etiquetas de los datos y calculando el gradiente de la función de pérdida con respecto a los parámetros del modelo. Este proceso se conoce como *retropropagación* y requiere que las funciones sean diferenciables.

Las transformaciones se ordenan en capas, como se observa en la {numref}`ml-nn`, donde la salida de una capa es la entrada de la siguiente.

```{figure} ./../../figuras/ml-nn.png
---
width: 400px
name: ml-nn
---
Diagrama de una red neuronal. Las transformaciones se ordenan por capas, donde la salida de una capa es la entrada de la siguiente. De {cite}`Mehta_2019`
```
La tarea de la red depende de su arquitectura. Para utilizar una red neuronal como clasificador binario, se utiliza la función sigmoid como función de activación de la última transformación. Se suele utilizar la *entropía cruzada binaria* como función de pérdida, que calcula la entropía cruzada entre las clases predichas y las clases reales. 

$$
    \mathcal{L}_{BC} = -\frac{1}{N}\sum_{i=1}^N y_i\log(p(y_i))+(1-y_i)\log(1-p(y_1))
$$ (binary-crossentropy)

donde $N$ es el número de muestras a clasificar, $y_i$ es la etiqueta de la muestra iésima y $p(y_i)$ es la probabilidad de que la muestra sea de clase 1. 

(alg-kmeans)=
## K-means
*K-means* es un algoritmo no-supervisado que separa los datos en $K$ grupos con igual varianza. Los grupos están caracterizados por la media de los datos pertenecientes al grupo. Estos se conocen como "centroides" y se representan con $\mu_k${cite}`Kmeans`. 

El objetivo del algoritmo es minimizar la *inercia* o *criterio de suma de cuadrados* dentro del grupo, definida como: 

$$
    \mathcal{C}(\{x,\mu\})=\sum_{k=1}^{K}\sum_{n=1}^{N}r_{nk}(\mathbf{x}_n-\mu_k)^2
$$ (ml-kmeansinertia)

donde $\mathbf{x}_n$ es la observación enésima y $r_{nk}$ es la asignación. $r_{nk}$ es 1 si $x_n$ pertenece al grupo y 0 de otra forma.

El algoritmo funciona mediante los siguientes pasos:

```{prf:algorithm} K-means
:label: alg-kmeans

1. Escoger los centroides. En la primera inicialización se escogen puntos aleatorios de los datos.
2. Asignar cada muestra al centroide más cercano, minimizando $\mathcal{C}$
3. Crear nuevos centroides tomando el valor medio de todas las muestras asignadas a cada centroide anterior.
4. Calcular la diferencia entre los centroides anteriores y los nuevos.
```

Los últimos tres pasos se repiten hasta que la diferencia entre los centroides esté debajo de un umbral, es decir, hasta que los centroides no se muevan significativamente.

Como la inicialización de los centroides es aleatoria, usualmente se realizan múltiples inicializaciones y se escoge la que resulte en un menor valor de la inercia.

(alg-ae)=
## Codificador automático
Los codificadores automáticos (AE) son algoritmos de aprendizaje no supervisado que mapean una entrada a una representación comprimida latente y luego vuelve a sí misma. Al aprender como reproducir la salida original, el modelo extrae características de los datos de entrada{cite}`Nakai_2019`.

Estas redes se pueden dividir en dos partes. El codificador, que comprime los datos a un espacio latente, y el decodificador que produce la reconstruccion{cite}`Goodfellow-et-al-2016`. Una medida de qué tan bien funciona el codificador es la diferencia entre la entrada y la salida de acuerdo a alguna métrica de distancia conocida como "error de reconstrucción".

```{figure} ./../../figuras/alg-ae.png
---
width: 600px
name: alg-aefig
---
Diagrama del funcionamiento de un codificador automático. La entrada se mapea a una representación de dimensionalidad reducida y luego es reconstruida {cite}`PhysRevD.101.075021`.
```
Este algoritmo se ha empezado a utilizar en HEP como detector de anomalías puesto que, al entrenar el codificador automático en una muestra de eventos de fondo, va a aprender las características de fondo y se espera que un evento de señal no sea reconstruido correctamente. Así, se puede utilizar un corte en el error de reconstrucción como un umbral de anomalía{cite}`PhysRevD.101.075021`. 

(alg-gan)=
## Red generativa antagónica
Una *red generativa antagónica* (GAN) está basada en modelado generativo y en conceptos de teoría de juegos.

El modelado generativo es una tarea de aprendizaje no supervisado en la que los modelos aprenden automáticamente regularidades o patrones en los datos de entrada, con el objetivo de generar nuevos ejemplos que podrían haberse extraído del conjunto de datos original.

Una GAN se construye a partir de dos redes neuronales conocidas como *generador* y *discriminador*. El generador aproxima una función generadora $G(z)$,

$$
    G(\mathbf{z})=\mathbf{\hat{x}}
$$(alg-generativa)

donde $\mathbf{z}$ es muestreado a partir de una distribución de probabilidad a priori en un espacio latente y $\mathbf{\hat{x}}$ son las muestras generadas.El discriminador aproxima una función discriminadora $D$ que distingue entre muestras $\mathbf{x}$ de los datos originales y muestras $\mathbf{\hat{x}}$ sintéticas. 

El discriminador se entrena para diferenciar entre las muestras sintéticas y los datos reales y el generador se entrena para engañar al discriminador. Las función de costo del discriminador depende de los parámetros del generador y viceversa. Los modelos se entrenan juntos hasta que el discriminador es engañado una cantidad de veces sobre algún umbral, lo que significa que el generador está generando ejemplos plausibles.