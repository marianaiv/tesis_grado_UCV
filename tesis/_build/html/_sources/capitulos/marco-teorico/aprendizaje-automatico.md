(ml)=
# Aprendizaje automático
En física de altas energías (HEP) los datos obtenidos de experimentos son sumamente complejos y de grandes dimensiones. A medida que alcanzamos mayores energías en los aceleradores de partículas, conseguimos nuevos desafíos debido al aumento en el tamaño de los eventos, el volumen de datos y su complejidad. Por esto, en la última década ha habido un enfoque en el estudio y la mejora de métodos y herramientas de análisis de datos, puesto que el alcance de los experimentos puede ser limitado por el rendimiento de algoritmos y de recursos computacionales. El aprendizaje automático es una herramienta que promete algunas soluciones a estos problemas.

Estos métodos han encontrado múltiples aplicaciones en HEP. Por ejemplo, en reconstrucción de hits y trayectorias en los detectores, identificación de partículas, clasificación y selección de eventos a nivel de detectores, simulaciones, procesamiento de datos, detección de anomalías, búsquedas independientes de modelo, entre otros{cite}`Bourilkov_2019,Guest_2018`.  Notablemente, estas herramientas han tenido un gran impacto en la medición de la masa del quark top{cite}`Bhat:1997rc` en 1997 y el descubrimiento del bosón de Higgs{cite}`201230,20121` en 2012{cite}`jimenez:tel-02402488`. Un resumen al día del uso de aprendizaje automático en HEP se puede encontrar en *[A Living Review of Machine Learning for Particle Physics](https://iml-wg.github.io/HEPML-LivingReview/)*{cite}`hepmllivingreview`.

A continuación, se presentan brevemente conceptos básicos de aprendizaje automático y los algoritmos a emplear en el proyecto, utilizando como referencia{cite}`Mehta_2019`.

(ml-conceptos)=
## Conceptos básicos
El aprendizaje automático es un subcampo de la inteligencia artificial. Tiene como objetivo el desarrollo de algoritmos que mejoran su desempeño de manera cuantificable en una tarea determinada, "aprendiendo" mediante un proceso de entrenamiento que utiliza grandes conjuntos de datos.

Típicamente los problemas hacen uso de un conjunto de datos $\mathcal{D}=(\mathbf{X},\mathbf{y})$ donde $\mathbf{X}$ es una matriz de variables independientes y $\mathbf{y}$ es un vector de variables dependientes. La tarea es optimizar un modelo $f(\mathbf{x};\mathbf{\theta})$ tal que $f:\mathbf{x}\rightarrow y$ de los parámetros $\mathbf{\theta}$. Esto es, $f$ es una función utilizada para predecir una salida de un vector de varibles de entrada. La funcion $f$ optimiza alguna métrica escogida que se conoce como función de pérdida o costo $\mathcal{L}(\mathbf{y},f(\mathbf{x}))$, lo que se logra encontrando el valor de $\mathbf{\theta}$ que minimiza $\mathcal{L}${cite}`Mehta_2019`.

El **proceso de aprendizaje** de un algoritmo se puede resumir en los siguientes pasos:
1. Pre-procesamiento de datos. En HEP puede ser, por ejemplo, mediante el cálculo de variables físicas. En este paso es común normalizar o escalar los datos y disminuir sus dimensiones.
2. Se divide aleatoriamente $\mathcal{D}$ en dos conjuntos mutuamente exclusivos de entrenamiento y prueba. $\mathcal{D}_{train}$ y $\mathcal{D}_{test}$, respectivamente. Se suele utilizar la mayor parte de los datos para entrenamiento. Por ejemplo, 70% entrenamiento y 30% prueba.
3. El ajuste del modelo se hace minimizando la función de pérdida utilizando los datos de entrenamiento $\mathbf{\hat{\theta}}=\text{arg min}_{\theta}\{\mathcal{L}(\mathbf{y}_{train},f(\mathbf{X}_{train};\mathbf{\theta}))\}$
4. Finalmente, el rendimiento del modelo se evalúa calculando la función de pérdida con los datos de prueba $\mathcal{L}(\mathbf{y}_{test},f(\mathbf{X}_{test};\mathbf{\hat{\theta}}))$.

El aprendizaje automático se puede dividir en tres categorías: aprendizaje supervisado, aprendizaje no-supervisado y aprendizaje reforzado. Aunque la distinción es útil, se suelen combinar estos tipos de aprendizaje, por lo que los términos se suelen utilizar de manera imprecisa y pueden ser confusos. En este proyecto se utilizarán métodos de aprendizaje supervisado y no supervisado.

(ml-supervisado)=
## Aprendizaje supervisado
El aprendizaje supervisado se refiere al aprendizaje a partir de datos etiquetados (por ejemplo, en HEP podría ser datos etiquetados como *contiene señal* o *no contiene señal*). Las tareas comunes incluyen *clasificación*, cuando el objetivo de aprendizaje $y$ es discreto y finito, y *regresión*, cuando $y$ es continuo o discreto e infinito{cite}`Karagiorgi_2021`.

En este proyecto utilizamos algunos modelos combinados, es decir, que utilizan *métodos de ensamble*.

### Métodos de ensamble 
Los *métodos de ensamble* utilizan conjuntos de algoritmos de aprendizaje automático cuyas decisiones se combinan para mejorar el rendimiento del sistema en general. Estos métodos han probado solucionar deficiencias estadísticas, computacionales y de representación. Las razones para utilizarlos están explicadas en {cite}`louppe2015understanding`:

1. **Estadística**: Cuando el conjunto de aprendizaje es muy pequeño, el algoritmo de aprendizaje normalmente puede encontrar varios modelos en el espacio de hipótesis $\mathcal{H}$ que resultan en el mismo rendimiento. Siempre que sus predicciones no estén correlacionadas, promediar varios modelos reduce el riesgo de elegir la hipótesis incorrecta.
2. **Computacional**: Muchos algoritmos de aprendizaje se basan en suposiciones o búsquedas locales que pueden atascarse en los óptimos locales. Un conjunto formado por modelos individuales construidos a partir de muchos puntos de partida diferentes puede proporcionar una mejor aproximación de la verdadera función desconocida, que cualquier aproximación de los modelos individuales.
3. **Representacional**: En la mayoría de los casos, para un conjunto de aprendizaje de tamaño finito, la verdadera función no puede ser representada por ninguno de los modelos candidatos en $\mathcal{H}$. Al combinar varios modelos en un conjunto, puede ser posible expandir el espacio de funciones representables y modelar mejor la verdadera función.

Existen varios métodos de ensamble, pero, de acuerdo a los algoritmos que se explicarán más adelante, es de interés el método de *impulso*.
#### Impulso
El *impulso* es un tipo de método de ensamble basado en la idea de que hallar varias reglas generales aproximadas puede ser más sencillo que hallar una regla general altamente precisa{cite}`Schapire2003`. Este método se aplica utilizando un conjunto de algoritmos con poca precisión o *aprendices débiles* $\{g_k(\mathbf{x})\}$. Inicialmente, un aprendiz débil halla una regla aproximada haciendo uso de un subconjunto de datos de entrenamiento. A cada clasificador se le asocia un peso $\alpha_k$ que indica cuánto contribuye al clasificador general. El clasificador general se puede expresar matemáticamente como:

$$
    g_A(\mathbf{x})=\sum_{K=1}^{M} \alpha_K g_K(\mathbf{x})
$$ (ml-boosting)

donde $\sum_k \alpha_k=1$.

(ml-nosupervisado)=
## Aprendizaje no-supervisado
Este tipo de aprendizaje se ocupa de hallar patrones y estructuras en datos no etiquetados. Ejemplos de tareas comunes de algoritmos no-supervisados incluyen agrupamiento, reducción de dimensiones, modelado generativo, detección de anomalías y clasificación.

(ml-algoritmos)=
## Algoritmos para detección de anomalías
En este proyecto se trata un problema de clasificación binaria con datos altamente desbalanceados, lo que se conoce como una tarea de *detección de anomalías*. El objetivo de la detección de anomalías es predecir la categoría a la que pertenece una muestra: "normal" o "anómala".

A continuación, se explicarán los algoritmos utilizados en este trabajo, enfocándonos en su uso para esta tarea.

### Bosque aleatorio
Los bosques aleatorios son algoritmos supervisados utilizados ampliamente para tareas complejas de clasificación. Estos algoritmos son ensambles de árboles de decisión.

Un **árbol de decisión** utiliza una serie de preguntas para realizar la partición jerárquica de los datos. Su objetivo es hallar un conjunto de reglas que separen naturalmente el espacio de características{cite}`myles_2004`. 

```{figure} ./../../figuras/ml-arboldecision.png
---
width: 600px
name: ml-arboldecision
---
Ejemplo de un árbol de decisión. Para una conjunto de características $\mathbf{x}$, su etiqueta $y$ es predicha, recorriéndolo desde su raíz, pasando por las hojas, siguiendo las ramas que satisface. De {cite}`Mehta_2019`.
```
Los *bosques aleatorios* son clasificadores que consisten en una colección de árboles de decisión $\{h(\mathbf{x},\Theta_k),k=1,\dots\}$ donde $\{\Theta_k\}$ son vectores aleatorios e independientes con la misma distribución. Cada árbol emite un voto unitario para la clase más popular dada la entrada $\mathbf{x}${cite}`Breiman:2001hzm`. La clase con más votos es asignada a esta entrada. 

```{figure} ./../../figuras/ml-bosquealeatorio.png
---
width: 700px
name: ml-bosquealeatorio
---
Representación visual del funcionamiento de un bosque aleatorio. De {cite}`chauhan_2021`
```
### Clasificador del gradiente del impulso

El clasificador del gradiente del impulso (GBC) usualmente utiliza árboles de regresión como aprendiz débil. Es un modelo supervisado y aditivo que avanza por etapas{cite}`GBC`. En cada etapa, se ajusta el árbol al error residual, es decir, el error asociado al árbol anterior.

GBC se puede usar para regresión y clasificación. Su formulación matemática es la siguiente{cite}`GTBC`.

La predicción $y_i$ del modelo para la entrada $x_i$ está dada por:

$$
    \hat{y}_i=F_M(x_i)=\sum_{m=1}^{M}h_m(x_i)
$$ (ml-gbcpred)

donde $h_m$ son los aprendices débiles. En el caso de clasificación, el mapeo del valor de $F_M(x_i)$ a una clase o probabilidad es dependiente de la pérdida. La probabilidad de que $x_i$ pertenezca a la clase positiva se modela usando la función sigmoid $p(y_i=|x_i)=\sigma(F_M(x_i))$

El GBC se construye de la siguiente manera:

$$
    F_m(x)=F_{m-1}(x)+h_m(x)
$$ (ml-gbc)

donde $h_m$ se ajusta para minimizar la suma de las pérdidas dado el ensamble anterior $F_{m-1}$

$$
    h_m\approx\text{arg min}_h\sum_{i=1}^{n}h(x_i)g_i
$$ (ml-gbcaprendizdebil)

donde $g_i$ es la derivada de la función de pérdida con respecto a su segundo parámetro, evaluada en $F_{m-1}(x)$. La suma en {eq}`ml-gbcaprendizdebil` se minimiza si $h(x_i)$ se ajusta para predecir un valor proporcional al gradiente negativo $−g_i$. Por lo tanto, en cada iteración, el estimador $h_m$ está ajustado para predecir los gradientes negativos de las muestras. Los gradientes se actualizan en cada iteración. Este proceso puede considerarse como una especie de descenso de gradiente en un espacio funcional.

### Análisis de discriminante cuadrático
El análisis de discriminante cuadrático{cite}`QDA` es un clasificador supervisado con un límite de decisión cuadrático. El modelo asume que las densidades condicionales de clase $P(\mathbf{X}|y=k)$, para cada clase $k$, están distribuidas normalmente.

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

### Redes neuronales
Las redes neuronales son modelos supervisados y no-lineales inspirados en las neuronas. Aunque su uso es extenso, nos enfocaremos en su aplicación para clasificación binaria.

Las redes neuronales se definen mediante una serie de transformaciones que mapean la entrada $x$ a estados "ocultos" $\mathbf{h}_i$. Finalmente, una última transformación mapea estos estados a una función de salida $\mathbf{y}${cite}`Guest_2018`.

Las transformaciones se pueden escribir matemáticamente como:

$$
    \mathbf{h}_i = g_i(W_i\mathbf{h}_i+\mathbf{b}_i)
$$ (ml-nnneurona)

donde $g_i$ es una función conocida como *función de activación* y $\mathbf{h}_i$ representa la transformación iésima de $\mathbf{x}$, llamada *embedding*. $W$ es la matriz de los *pesos* y $\mathbf{b}$ el vector de los *sesgos*.

El objetivo es hallar los pesos y sesgos que optimizan la función de pérdida. Esto se logra utilizando las etiquetas de los datos y calculando el gradiente de la función de pérdida con respecto a los parámetros del modelo. Este prceso se conoce como *retropropagación* y requiere que las funciones sean diferenciables.

Las transformaciones se ordenan en capas ({numref}`ml-nn`), donde la salida de una capa es la entrada de la siguiente.

```{figure} ./../../figuras/ml-nn.png
---
width: 500px
name: ml-nn
---
Diagrama de una red neuronal. Las transformaciones se ordenan por capas, donde la salida de una capa es la entrada de la siguiente. De {cite}`Mehta_2019`
```
La tarea de la red depende de su arquitectura. Para utilizar una red neuronal como clasificador binario, se utiliza la función sigmoid como función de activación de la última transformación. Se suele utilizar la *entropía cruzada binaria* como función de pérdida, que calcula la entropía cruzada entre las clases predichas y las clases reales. 

### K-means
*K-means* es un algoritmo no-supervisado que separa los datos en $K$ grupos con igual varianza. Los grupos están caracterizados por la media de los datos pertenecientes al grupo. Estos se conocen como "centroides" y se representan con $\mu_j${cite}`Kmeans`. 

El objetivo del algoritmo es minimizar la *inercia* o *criterio de suma de cuadrados* dentro del grupo, definida como: 

$$
    \mathcal{C}(\{x,\mathbf{\mu}\})=\sum_{k=1}^{K}\sum_{n=1}^{N}r_{nk}(\mathbf{x}_n-\mu_k)^2
$$ (ml-kmeansinertia)

donde $\mathbf{x}_n$ es la observación enésima y $r_{nk}$ es la asignación. $r_{nk}$ es 1 si $x_n$ pertenece al grupo y 0 de otra forma.

El algoritmo funciona mediante los siguientes pasos:
1. Escoger los centroides. En la primera inicialización se escogen puntos aleatorios de los datos.
2. Asignar cada muestra al centroide más cercano, minimizando $\mathcal{C}$
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
Como la inicialización de los centroides es aleatoria, usualmente se realizan múltiples inicializaciones y se escoge la que resulte en un menor valor de la inercia.

(ml-metricasderendimiento)=
## Métricas de rendimiento
La clasificación es una de las tareas más comunes en el aprendizaje automático. Sin embargo, no existe un algoritmo que funcione mejor para todos los problemas; cada algoritmo tiene ventajas y desventajas. Por lo tanto, requerimos formas de medir el grado en que la clasificación sugerida y la real coinciden.

El uso de estas métricas depende del problema de clasificación específico. Sin embargo, se hará un resumen general de las más comunes en clasificación binaria.

### Métricas numéricas
La métrica de evaluación primaria es la *matriz de confusión*. En esta matriz se resumen el número de etiquetas predichas correctamente e incorrectamente.  

```{table} Matriz de confusión.
:name: ml-matriz-confusion

|                                                           |Clase: **P**ositivos<br>(HEP: **señal** $S_{tot}$)|Clase: **N**egativos<br>(HEP: **fondo** $B_{tot}$)|
|-----------------------------------------------------------|--------------------------------------------------|--------------------------------------------------|
|Clasificado como: **P**ositivos<br>(HEP: **seleccionados**)|**Verdaderos Positivos (TP)**<br>(HEP: señal seleccionada $S_{sel}$)|**Falsos Positivos (FP)**<br>(HEP: fondo seleccionado $B_{sel}$)|
|Clasificado como: **N**egativos<br>(HEP: **rechazados**)   |**Falsos Negativos(FN)**<br>(HEP: señal rechazada $S_{rej}$)|**Verdaderos Negativos (TN)**<br>(HEP: fondo rechazado $B_{rej}$)|
```
La diagonal representa las etiquetas predichas correctamente, mientras que los elementos fuera de la diagonal son las predicciones incorrectas. A partir de los valores de esta matriz se definen el resto de las métricas.

En la {numref}`ml-metricas` se presenta un resumen de las métricas utilizadas comúnmente para clasificación binaria{cite}`SOKOLOVA2009427`.

```{table} Métricas para la clasificación binaria utilizando la notación en la matriz de confusión.
:name: ml-metricas

| Métrica       | Ecuación                                           | Enfoque de evaluación                                               |
|---------------|----------------------------------------------------|---------------------------------------------------------------------|
| Exactitud     | $\frac{TP+TN}{TP+FP+FN+TN}$                        | Número correcto de predicciones sobre todas las predicciones hechas |
| Precisión     | $\frac{TP}{TP+FP}$                                 | Proporción de tasa de verdaderos positivos                          |
| Recuperación  | $\frac{TP}{TP+FN}$                                 | Efectividad del clasificador para identificar etiquetas positivas   |
| Especificidad | $\frac{TN}{TN+FP}$                                 | Efectividad del clasificador para identificar etiquetas negativas   |
| Puntaje f1    | $\frac{(\beta^2+1)TP}{(\beta^2+1)TP+\beta^2FN+FP}$ | Promedio ponderado de precisión y sensibilidad                      |

```
El nombre de las métricas varía en distintas áreas. En HEP, la recuperación y especificidad se conocen como *eficiencia de señal* ($\epsilon_s$) y *rechazo de fondo* ($1-\epsilon_{b}$), respectivamente. La precisión se conoce como *pureza* ($\rho$){cite}`valassi_andrea_2018_1405727`.

Las métricas utilizadas dependen del problema de clasificación. Para datos altamente desbalanceados, se descarta la exactitud ya que puede resultar en valores altos a pesar de estar prediciendo incorrectamente la etiqueta para la clase minoritaria. Sin embargo, se puede utilizar la *exactitud balanceada*:

$$
    \text{Exactitud balanceada}= \frac{\text{eficiencia de señal}+\text{rechazo de fondo}}{2}
$$ (ml-exactitudbalanceada)

### Métricas gráficas
Las métricas gráficas más conocidas son la *curva característica de funcionamiento del receptor* (curva ROC) y la *curva precisión-recuperación* (curva PR).

#### Curva ROC
Los clasificadores usualmente asignan un puntaje $\mathcal{D}$ de manera que una puntuación más alta significa mayor probabilidad de ser señal. La clasificación discreta se logra escogiendo un *punto de operación*, es decir, escogiendo un umbral de decisión $\mathcal{D}_{thr}$, de manera que todas las muestras $\mathcal{D}\geq\mathcal{D}_{thr}$ se clasifican como positivas, o señal, y todas las demás como negativas, o fondo{cite}`valassi_2019`.

La *curva ROC* se construye graficando la recuperación vs. 1-especificidad para varios umbrales de decisión. En términos de HEP, la eficiencia de señal vs. la eficiencia de fondo. 

```{figure} ./../../figuras/ml-roc.png
---
width: 600px
name: ml-roc
---
Ilustración de la curva ROC. La diagonal representa a un clasificador aleatorio o que no distingue entre clases. En este caso, el clasificador con la curva azul es mejor distinguiendo entre clases. De MartinThoma, CC0, via [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Roc-draft-xkcd-style.svg).
```
El *área debajo de la curva* (AUC) representa la habilidad del clasificador para distinguir entre clases.

$$
    \text{AUC}=\int_0^1\epsilon_s\text{d}\epsilon_b
$$ (ml-auc)

Un valor de AUC de 0.5 indica que la predicción no es mejor que una clasificación aleatoria. Menor a 0.5 indica que el clasificador está clasificando de manera inversa{cite}`Kohl_2012`.

En HEP se utilizan versiones de esta curva. Es común graficar ***eficiencia de señal* vs. *rechazo de fondo***, en vez de la curva ROC clásica, y el AUC se calcula en términos de estas variables. También se suele graficar el ***inverso de la eficiencia de fondo* vs. *eficiencia de señal***.

```{figure} ./../../figuras/ml-otrasroc.png
---
width: 800px
name: ml-otrasroc
---
Ejemplos de otras versiones de la curva ROC. A la izquierda la curvas de eficiencia de señal vs. rechazo de fondo. A la derecha, inverso de la eficiencia de fondo vs. eficiencia de señal. De {cite}`Kasieczka_2021`
```

La curva ROC y el AUC tienen sus limitaciones{cite}`valassi_2019`:
- La comparación de dos curvas ROC que se cruzan no es tan evidente, ya que el AUC se construye como una integral que otorga el mismo peso a todas las partes de la curva. Sin embargo, para la clasificación se escoge un punto específico. En este caso, otras métricas se deben utilizar para definir cuál clasificador proporciona mejor rendimiento en la región donde se elija el umbral de decisión.
- El uso de las curvas ROC puede no ser apropiado para problemas que incluyan datos altamente desbalanceados, debido a que conduce a evaluaciones demasiado optimistas. La curva PR puede ser más informativa en este caso
  
#### Curva PR
Para datos altamente desbalanceados se suele sugerir el uso de la curva PR:

> Si la proporción de instancias positivas y negativas en un conjunto de prueba cambia, la curva ROC no cambia. [...]Métricas como la exactitud, la precisión, las curvas de aumento y el puntaje F usan valores de ambas columnas de la matriz de confusión. Cuando la distribución de clases cambia, estas métricas también cambian, incluso si el rendimiento del clasificador no cambia. Las curvas ROC se basan en la tasa de TP y FP, en la cual cada dimensión es una proporción de la columna, por lo que no depende de la distribución de clases.
>
> — ROC Graphs: Notes and Practical Considerations for Data Mining Researchers, 2003{cite}`Fawcett_2004`.

```{figure} ./../../figuras/ml-curvapr.png
---
width: 500px
name: ml-curvapr
---
Ejemplos de curva precisión-recuperación. De {cite}`valassi_andrea_2018_1405727`
```

Análogo al AUC, se utiliza el área bajo la curva PR (AUCPR) y la precisión promedio (AP). La precisión promedio resume la curva PR utilizando la media ponderada de las precisiones logradas en cada umbral, utilizando como peso el aumento en recuperación del umbral anterior{cite}`AP`.

$$
    AP=\sum_n (R_n - R_{n-1})P_n
$$ (ml-precisionpromedio)

donde $P_n$ y $R_n$ son la precisión y la recuperación del umbral enésimo.

#### Mejora significativa
Otra medida utilizada regularmente en HEP es la *mejora significativa* definida como:

$$
    \text{Mejora significativa} = \frac{\epsilon_s}{\sqrt{\epsilon_b}}
$$ (ml-mejorasignificativa)

Una mejora significativa = 2 significa que la mejora significativa inicial es amplificada por un factor de 2 después de utilizar la estrategia de clasificación{cite}`Kasieczka_2021`.

Así, se grafica la *mejora significativa* vs. *eficiencia de señal* con el fin de visualizar la mejora significativa del clasificador en múltiples umbrales.

```{figure} ./../../figuras/ml-significancia.png
---
width: 500px
name: ml-significancia
---
Ejemplo de curva de mejora significativa. De {cite}`Kasieczka_2021`
```

(ml-HEP)=
## Aprendizaje automático en HEP
Como se mencionó anteriormente, el uso de aprendizaje automático en HEP es amplio. Sin embargo, este trabajo se enfoca en las técnicas de *detección de anomalías* y *búsquedas libres de modelo*.

### Detección de anomalías
Hasta ahora no se ha confirmado ninguna señal de nueva física. Parte de la dificultad recae en diferenciar la pequeña cantidad de eventos que podrían ser señales nuevas de los eventos de fondo o que no son de interés. Debido a esto, se ha planteado el uso de algoritmos de detección de anomalías para clasificación de los eventos de señal.

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