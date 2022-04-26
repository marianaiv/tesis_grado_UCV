(ml)=
# Aprendizaje automático
En física de altas energías (HEP) los datos obtenidos de experimentos son sumamente complejos y de grandes dimensiones. A medida que alcanzamos mayores energías en los aceleradores de partículas, conseguimos nuevos desafíos debido al aumento en el tamaño de los eventos, el volumen de datos y su complejidad. Por esto, en la última década ha habido un enfoque en el estudio y la mejora de métodos y herramientas de análisis de datos, puesto que el alcance de los experimentos puede ser limitado por el rendimiento de algoritmos y de recursos computacionales. El aprendizaje automático es una herramienta que promete algunas soluciones a estos problemas.

Estos métodos han encontrado múltiples aplicaciones en HEP. Por ejemplo, en reconstrucción de hits y trayectorias en los detectores, identificación de partículas, clasificación y selección de eventos a nivel de detectores, simulaciones, procesamiento de datos, detección de anomalías, búsquedas independientes de modelo, entre otros{cite}`Bourilkov_2019,Guest_2018`.  Notablemente, estas herramientas han tenido un gran impacto en la medición de la masa del quark top{cite}`Bhat:1997rc` en 1997 y el descubrimiento del bosón de Higgs{cite}`201230,20121` en 2012{cite}`jimenez:tel-02402488`. Un resumen al día del uso de aprendizaje automático en HEP se puede encontrar en *[A Living Review of Machine Learning for Particle Physics](https://iml-wg.github.io/HEPML-LivingReview/)*{cite}`hepmllivingreview`.

A continuación, se presentan brevemente conceptos básicos de aprendizaje automático y su uso en HEP, utilizando como referencia{cite}`Mehta_2019`.

(ml-conceptos)=
## Conceptos básicos
El aprendizaje automático es un subcampo de la inteligencia artificial que tiene como objetivo el desarrollo de algoritmos que mejoran su desempeño de manera cuantificable en una tarea determinada, "aprendiendo" mediante un proceso de entrenamiento que utiliza grandes conjuntos de datos. El objetivo de un algoritmo de aprendizaje automático es utilizar un conjunto de datos para identificar patrones y tomar decisiones informadas con una mínima intervención humana. Estas técnicas se utilizan para problemas de estimación y predicción, pero en este trabajo nos enfocamos en problemas de predicción. 

De manera general, un algoritmo de aprendizaje automático utilizado para resolver un problema de predicción se entrena utilizando un conjunto de datos $\mathbf{X}$ asociados a algún vector $\mathbf{y}$. A través del proceso de entrenamiento, aprende un mapeo $f:\mathbf{x}\longrightarrow y$, donde $x\in\mathbf{X}$. El objetivo es utilizar el mapeo para hacer predicciones $\hat{y}$ dado un nuevo conjunto de datos $\hat{x}$.

El aprendizaje automático se puede dividir en tres categorías: aprendizaje supervisado, aprendizaje no-supervisado y aprendizaje reforzado. Aunque la distinción es útil, se suelen combinar estos tipos de aprendizaje, por lo que los términos se suelen usar de manera imprecisa y pueden ser confusos. En este proyecto se utilizarán métodos de aprendizaje supervisado y no supervisado.

(ml-supervisado)=
## Aprendizaje supervisado
El aprendizaje supervisado se refiere al aprendizaje a partir de datos etiquetados (por ejemplo, en HEP podría ser datos etiquetados como *contiene señal* o *no contiene señal*). Las tareas comunes incluyen *clasificación*, cuando el objetivo de aprendizaje $y$ es discreto y finito, y *regresión*, cuando $y$ es continuo o discreto e infinito{cite}`Karagiorgi_2021`. En este trabajo nos enfocamos en la tarea de clasificación.

Los algoritmos supervisados mayormente utilizados suelen ser modelos combinados de algoritmos más simples. Estos algoritmos se combinan utilizando *métodos de ensamble*.

### Métodos de ensamble 
Los *métodos de ensamble* utilizan conjuntos de algoritmos de aprendizaje automático cuyas decisiones se combinan para mejorar el rendimiento del sistema en general. Se ha probado que solucionan deficiencias estadísticas, computacionales y de representación. Las razones para utilizarlos están explicadas en {cite}`louppe2015understanding`:

1. **Estadística**: Cuando el conjunto de aprendizaje es muy pequeño, el algoritmo de aprendizaje normalmente puede encontrar varios modelos en el espacio de hipótesis $\mathcal{H}$ que resultan en el mismo rendimiento. Siempre que sus predicciones no estén correlacionadas, promediar varios modelos reduce el riesgo de elegir la hipótesis incorrecta.
2. **Computacional**: Muchos algoritmos de aprendizaje se basan en suposiciones o búsquedas locales que pueden atascarse en los óptimos locales. Un conjunto formado por modelos individuales construidos a partir de muchos puntos de partida diferentes puede proporcionar una mejor aproximación de la verdadera función desconocida, que cualquier aproximación de los modelos individuales.
3. **Representacional**: En la mayoría de los casos, para un conjunto de aprendizaje de tamaño finito, la verdadera función no puede ser representada por ninguno de los modelos candidatos en $\mathcal{H}$. Al combinar varios modelos en un conjunto, puede ser posible expandir el espacio de funciones representables y modelar mejor la verdadera función.

Existen varios métodos de ensamble, pero, de acuerdo a los algoritmos utilizados en este trabajo, es de interés el método de *impulso*.
#### Impulso
El *impulso* es un tipo de método de ensamble basado en la idea de que hallar varias reglas generales aproximadas puede ser más sencillo que hallar una regla general altamente precisa{cite}`Schapire2003`. Este método se aplica utilizando un conjunto de algoritmos con poca precisión o *aprendices débiles* $\{g_k(\mathbf{x})\}$. Inicialmente, un aprendiz débil halla una regla aproximada haciendo uso de un subconjunto de los datos destinados al entrenamiento del modelo. A cada clasificador se le asocia un peso $\alpha_k$ que indica cuánto contribuye al clasificador general. El clasificador general se puede expresar matemáticamente como:

$$
    g_A(\mathbf{x})=\sum_{K=1}^{M} \alpha_K g_K(\mathbf{x})
$$ (ml-boosting)

donde $\sum_k \alpha_k=1$.

(ml-nosupervisado)=
## Aprendizaje no-supervisado
Este tipo de aprendizaje se ocupa de hallar patrones y estructuras en datos no etiquetados. Estos algoritmos funcionan descubriendo patrones ocultos o grupos en los datos. Ejemplos de tareas comunes de algoritmos no-supervisados incluyen agrupamiento, reducción de dimensiones, modelado generativo, detección de anomalías y clasificación. 

(ml-metricasderendimiento)=
## Métricas de rendimiento
La clasificación es una de las tareas más comunes en el aprendizaje automático. Sin embargo, no existe un algoritmo que funcione mejor para todos los problemas; cada algoritmo tiene ventajas y desventajas. Por lo tanto, requerimos formas de medir el grado en que la clasificación sugerida y la real coinciden. 

Algunas métricas númericas comúnes son la exactitud, precisión, recuperación, especificidad y puntaje f1. También se utilizan métricas gráficas como la *curva característica de funcionamiento del receptor* (curva ROC) y la *curva precisión-recuperación* (curva PR). El uso de estas métricas depende del problema de clasificación específico. Un resumen general de las métricas se presentará más adelante, en la {numref}``.

(ml-HEP)=
## Aprendizaje automático en HEP
Como se mencionó anteriormente, el uso de aprendizaje automático en HEP es amplio. Sin embargo, este trabajo se enfoca en las técnicas de *detección de anomalías* y *búsquedas libres de modelo*.

### Detección de anomalías
Hasta ahora no se ha confirmado ninguna señal de nueva física. Parte de la dificultad recae en diferenciar la pequeña cantidad de eventos que podrían ser señales nuevas de los eventos de fondo o que no son de interés. Debido a esto, se ha planteado el uso de algoritmos de detección de anomalías para clasificación de los eventos de señal. La tarea de detección de anomalías tiene como objetivo predecir la categoría a la que pertenece una muestra: "normal" o "anómala".

Las técnicas de detección de anomalías se pueden dividir en dos tipos{cite}`Fraser_2022`. 
- Algunas señales son cualitativamente distintas de del fondo y se utilizan técnicas para caracterizar estos eventos como anómalos. 
- Algunos eventos de señal son similares a los de fondo, por lo que se explota información sobre la distribución de probabilidad esperada del fondo para hallar señal. 

Este último caso es el que se trata en este proyecto y los detalles se discutirán en la [última sección](lhco) de este capítulo.

### Búsquedas de nueva física independiente de modelo
La mayor parte de la búsqueda de nueva física está guiada por modelos específicos de BSM, supersimetría o materia oscura. Sin embargo, con la introducción del aprendizaje automático, se han propuesto métodos para la búsqueda independiente de modelo. El objetivo general de estas búsquedas es que sean lo más agnósticas posibles al proceso físico subyacente que puede ser responsable de la señal de nueva física{cite}`jimenez:tel-02402488`.

Un ejemplo de una búsqueda independiente de modelo es {cite}`De_Simone_2019`, donde se plantea el uso de aprendizaje no supervisado para comparar las distribuciones de densidad de probabilidad de dos muestras: simulaciones de eventos del modelo estándar, o lo que sería el fondo para las búsquedas de nueva física, y datos reales.

Una búsqueda de este tipo es{cite}`Fraser_2022`:
- *Libre de modelo*: sin suposiciones sobre las densidades
- *No-paramétrica*: compara las densidades como un todo, no valores específicos asociados a estas.
- *No-clasificada*: usa la dimensionalidad completa de la información.

La relación entre la detección de anomalías y la búsqueda libre de modelo es evidente, ya que el objetivo en ambos casos es realizar una búsqueda no-específica, o más general, de eventos de nueva física.