# Aprendizaje automático
En física de altas energías (HEP) los datos obtenidos de experimentos son sumamente complejos y de grandes dimensiones. A medida que alcanzamos mayores energías en los aceleradores de partículas, conseguimos nuevos desafíos debido al aumento en el tamaño de los eventos, el volumen de datos y su complejidad. Por esto, en la última década ha existido un enfoque en el estudio y la mejora de métodos y herramientas de análisis de datos, puesto que el alcance de los experimentos puede ser limitado por el rendimiento de algoritmos y de recursos computacionales. El aprendizaje automático es una herramienta que promete mejoras en estas áreas.

En este capítulos se presentan brevemente conceptos básicos de aprendizaje automático y un resumen de su uso en HEP. Información más detallada sobre este tema se encuentra en {cite}`Mehta_2019,Bourilkov_2019`. Una recopilación al día de las investigaciones relacionadas a aprendizaje automático y física de partículas se encuentra en {cite}`livingreview`
## Conceptos básicos
El aprendizaje automático es un subcampo de la inteligencia artificial. Tiene como objetivo el desarrollo de algoritmos que mejoran su desempeño de manera cuantificable en una tarea determinada mediante un proceso de entrenamiento que utiliza grandes conjuntos de datos.

Típicamente los problemas hacen uso de un conjunto de datos $\mathcal{D}=(\mathbf{X},\mathbf{y})$ donde $\mathbf{X}$ es una matriz de variables independientes ***y*** es un vector de variables dependientes. La tarea es optimizar un modelo $f(\mathbf{x};\mathbf{\theta})$ tal que $f:\mathbf{x}\rightarrow y$ de los parámetros $\mathbf{\theta}$. Esto es, *f* es una función utilizada para predecir una única salida de un vector de varibles de entrada. Esta función optimiza alguna métrica escogida que se conoce como función de pérdida o costo $\mathcal{L}(\mathbf{y},f(\mathbf{x}))$. Esto se logra encontrando el valor de $\mathbf{\theta}$ que minimiza $\mathcal{L}${cite}`Mehta_2019`.

El proceso de aprendizaje de un algoritmo se puede resumir en los siguientes pasos:
1. Usualmente es necesario pre-procesar los datos. En HEP esto puede ser, por ejemplo, mediante el calculo de variables físicas. En este paso es común incluir el normalizar o escalar los datos y disminución de dimensiones.
2. Se divide aleatoreamente $\mathcal{D}$ en dos conjuntos mutuamente exclusivos de entrenamiento y prueba. $\mathcal{D}_{train}$ y $\mathcal{D}_{test}$, respectivamente. Se suele utilizar la mayor parte de los datos para entrenamiento. Por ejemplo, 70% entrenamiento y 30% prueba.
3. El ajuste del modelo se hace minimizando la función de pérdida utilizando los datos de entrenamiento $\mathbf{\hat{\theta}=\text{arg min}_\theta\{\mathcal{L}(\mathbf{y}_{train},f(\mathbf{X}_{train};\mathbf{\thetaa}))\}$
4. Finalmente, el rendimiento del modelo es evaluado calculando la función de pérdida con los datos de prueba $\mathcal{L}(\mathbf{y}_{test},f(\mathbf{X}_{test};\mathbf{\hat{\theta}}))$.

El aprendizaje automático se puede dividir en tres categorías: aprendizaje supervisado, aprendizaje no-supervisado y aprendizaje reforzado. Aunque la distinción es útil, se suelen combinar estos tipos de aprendizaje, por lo que los términos se suelen utilizar de manera imprecisa y pueden ser confusos.

En este proyecto es de interés el aprendizaje supervisado y no supervisado.
## Aprendizaje supervisado
El aprendizaje supervisado se refiere al aprendizaje a partir de datos etiquetados (por ejemplo, en HEP podría ser datos etiquetados como que *contienen señal* o que *no contienen señal*). Las tareas comunes incluyen *clasificación*, cuando el objetivo de aprendizaje *y* es discreto y finito, y *regresión*, cuando *y* es continuo o discreto e infinito{cite}`Karagiorgi_2021`.

Los problemas que se tratan en este proyecto son de clasificación, por lo que se presentarán algunos de estos algoritmos a continuación.
### Algoritmos de clasificación
## Aprendizaje no-supervisado
Este tipo de aprendizaje se ocupa de hallar patrones y estructuras en datos no etiquetados. Ejemplos de tareas comunes incluyen agrupamiento, reducción de dimensiones, modelado generativo y detección de anomalías.
### Algoritmos de agrupamiento


## Métricas de rendimiento

## Aprendizaje automático en HEP
https://arxiv.org/pdf/1912.08245.pdf 
https://arxiv.org/pdf/1806.11484.pdf
### Clasificación y selección de eventos

### Detección de anomalías
