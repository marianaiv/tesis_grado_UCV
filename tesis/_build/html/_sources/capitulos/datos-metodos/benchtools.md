(bench)=
# Paquete benchtools
Como se mencionó en la {numref}`datos`, los conjuntos de datos de las LHCO 2020 incluyen todos los hadrones producto de la colisión entre protones. A partir de estos datos, nos interesa reconstruir los jets de cada evento para analizar variables cinemáticas y de subestructura, entrenar los algoritmos explicados en la {numref}`alg` y compararlos utilizando las métricas mencionadas en la {numref}`met`, que se explicarán en la {numref}`met`. Sin embargo, para trabajar con 1,000,000 de colisiones, donde hay posibilidad tener los datos de 700 hadrones por evento, con 3 medidas por hadrón (es decir, 2,100,000,000 de variables), es necesario desarrollar algunas herramientas para facilitar su manejo. 

En esta sección se describirá de manera general el paquete `benchtools`, desarrollado para este trabajo. El paquete incluye herramientas para el manejo de datos, agrupamiento jets, comparación de algoritmos de clasificación binaria, entre otros. Información más detallada sobre el paquete y cómo utilizarlo se puede encontrar en el [repositorio](https://github.com/marianaiv/benchtools).

(bench-herramientas)=
## Funciones
El paquete se puede dividir en dos partes principales: las funciones y el pipeline. Una función es un bloque de código que resuelve un problema concreto y es lo que utilizamos para armar el pipeline. Recibe cero o más argumentos de entrada y devuelve un argumento de salida o realiza una tarea. En el caso de `benchtools`, se agruparon funciones en cinco módulos diferentes de acuerdo a su utilidad.

Las funciones se dividen en los siguientes módulos:
- **datatools**: funciones para manejar los datos. Por ejemplo, leer datos iterativamente, unir tablas de datos, entre otras. 
- **substructure**: funciones para calcular variables cinemática y de subestructura de los jets.
- **clustering**: funciones para pre-procesar los datos. Por ejemplo, agrupar los jets, calcular las variables de un jet, entre otras.
- **plotools**: funciones para graficar datos. La característica principal es que se grafican los datos separando la señal del fondo.
- **metrictools**: funciones para calcular métricas de redimiento de algoritmos de clasificación binaria.

Las funciones en *datatools* y *substructure* son utilizadas principalmente en otras funciones y su contenido no se discutirá en este trabajo. Las funciones en *plotools* se utilizarán más adelante y se observará su funcionamiento, por lo que omitiremos su explicación.

En *metrictools* hay múltiples funciones que calculan y grafican las métricas de rendimiento. Para calcular las métricas numéricas, en general se va a utilizar `compare_metrics`, que calcula la exactitud balanceada, la precisión, el puntaje f1 y la recuperación para múltiples clasificadores. Las métricas gráficas incluidas en el paquete son la curva ROC y sus variaciones (ROC inversa y eficiencia de señal vs. rechazo de fondo), la curva PR y la curva de mejora significativa. Por último, en este archivo se encuentra una clase `clasificador`. Se utiliza para guardar los resultados de la clasificación en un objeto que contenga el nombre del clasificador, el puntaje de cada evento asociado a la probabilidad de ser señal, la etiqueta binaria predicha para cada evento y la etiqueta real.

En *clustering* se encuentra la función que realiza el pre-procesamiento de los datos, `build_features`, y las funciones que la confoman.

(bench-pre)=
## Pre-procesamiento de datos
El pre-procesamiento de datos se realiza para obtener variables físicas. Estas variables son utilizadas por los modelos para entrenamiento y clasificación. Los pasos para pre-procesar son los siguientes:

```{prf:algorithm} Pre-procesamiento
:label: bench-predatos

**Input**: Datos de todos los hadrones de los eventos.

**Output**: Variables físicas para cada evento.

1. Importar una fracción de los eventos. Para cada fracción de eventos:
    1. Agrupar los jets de cada evento utilizando anti-kt con $R=1$.
    2. Seleccionar los jets que tengan $p_T>20GeV$
    3. Calcular $p_T$, $m_j$, $\eta$, $\phi$, $E$, $\tau_{21}$ y el número de hadrones constituyentes, para los dos jets más energéticos. $\Delta R$, $m_{jj}$ utilizando los dos jets principales y el número de hadrones del evento.
    4. Guardar las variables calculadas en un marco de datos.
```
Este proceso se hace iterativamente para fracciones de datos, debido a que importar todos los eventos requiere gran cantidad de memoria. Luego, se unen los archivos para tener un solo conjunto de datos pre-procesados.

Una tabla con la descripción de cada variable calculada se encuentra {numref}`bench-variables`:
```{table} Variables calculadas en el pre-procesamiento de los datos. Las variables se calculan para i=1,2, que representan el jet principal y secundario, respectivamente.
:name: bench-variables

| Variable         | Descripción                                                 |
|------------------|-------------------------------------------------------------|
| $p_T\_j_i$       | Momento transverso del jet *i*                              |
| $m_j\_j_i$       | Masa del jet *i*                                            |
| $\eta\_j_i$      | Pseudorapidez del jet *i*(ec. {eq}`jets-eta`)               |
| $\phi\_j_i$      | Ángulo azimutal en el plano transverso del jet *i*          |
| $E\_j_i$         | Energía del jet *i*                                         |
| $\tau_{21}\_j_i$ | Subjetiness del jet *i* (ec. {eq}`jets-ratio_subjettiness`) |
| n_hadrons_$j_i$  | Número de hadrones constituyentes del jet *i*               |
| $\Delta R$       | Distancia angular entre los dos jets principales            |
| $m_{jj}$         | Masa invariante de los dos jets principales                 |
| n_hadrons        | Número de hadrones del evento                               |
```

(bench-pipeline-cap)=
## Pipeline
En programación, un pipeline consiste en una serie de pasos en los que la salida de un paso es la entrada del siguiente. Uno de los objetivos de este trabajo fue la creación de un pipeline que acepta como entrada los datos proporcionados en las olimpiadas y que tiene como salida la comparación del resultado de varios algoritmos. El pipeline de `benchtools` procesa los datos, entrena los modelos explicados en la {numref}`alg`, realiza la clasificación y compara los resultados con clasificaciones realizadas externamente, utilizando las métricas de rendimiento descritas anteriormente. Los pasos se describen a continuación:

```{prf:algorithm} Pipeline
:label: bench-pipelinealg

**Input**: Datos de los eventos y lista de los clasificadores externos a comparar, salvados como un objeto `classifier`.

**Output**: Imagenes de los plots de las métricas y una tabla con las métricas númericas, así como gráficos de barra de cada variable.

1. Pre-procesar los datos de los eventos.
2. Transformar los datos para que estén confinados en un rango de valores según el clasificador a utilizar, entrenar los modelos y salvarlos.
3. Evaluar los puntajes y predicciones de cada clasificador.
4. Importar las clasificaciones externas.
5. Comparar los algoritmos utilizando las métricas en *metrictools*
```
Para entrenar los modelos, se utilizan las variables descritas en {numref}`bench-variables`, a excepción de $m_{jj}$ y $m_{ji}$, para evitar que los modelos aprendan la masa de las partículas, y obtener una clasificación lo más libre posible de modelo.

El pipeline posee opciones para realizar algunos o todos los pasos. Un diagrama de este proceso se muestra la {numref}`bench-pipeline`.

```{figure} ../../figuras/bench-pipeline.png
---
width: 800px
name: bench-pipeline
---
Diagrama del pipeline.
```
Las opciones para correr el pipeline se encuentran explicadas en el [repositorio](https://github.com/marianaiv/benchtools). Los resultados de su uso se observarán en la {numref}`comp`.