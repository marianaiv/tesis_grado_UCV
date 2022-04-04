# Olimpiadas LHC 2020

La búsqueda de física BSM es parte principal del programa de investigación en el LHC. Hasta ahora no ha sido exitosa, pero se mejora constantemente. Sin embargo, es evidente que se requiere mejorar las herramientas para que puedan aprovechar la cantidad y complejidad de los datos.

Con el fin de mejorar estas herramientas y el análisis de los datos se crearon las olimpiadas LHC (LHCO). Para las olimpiadas, se simulan conjuntos de datos con eventos de nueva física que podrían observarse en el acelerador con el objetivo de que los participantes interpreten los datos en términos de modelos de física BSM.

> "La idea principal es que si no lo puedes hacer para el caso simulado, es mucho menos probable que lo puedas hacer para el caso real. 
> Hace que las personas aprendan a pensar de manera diferente y aborden el problema de la forma en que habría que abordarlo" 
> 
> — Gordy Kane, Universidad de Michigan. Organizador de las LHCO{cite}`lhco_2006`.

Las olimpiadas de 2020 estuvieron enfocadas en el desarrollo técnicas de aprendizaje automático para la búsqueda de partículas resonantes. 

El desarrollo de estas herramienta para su uso en física de altas energías se ha visto limitado porque los datos relacionados a colisiones *pp* no están públicamente disponibles y son muy diferentes a los datos comunmente utilizados para estudiar estos métodos. Sin embargo, el aprendizaje automático posee un gran potencial para ampliar la búsqueda de nueva física porque permite una aproximación más amplia al problema, eliminando la necesidad de buscar una partícula en específico, más allá de definir unos parámetros generales del tipo de partícula que se busca. A esto se le conoce como búsqueda libre de modelo.

En el caso de las LHCO 2020, se plantea una partícula resonante con un ancho de decaimiento pequeño, que produzca eventos de múltiples jets. Un ejemplo de esta topología se ilustra a continuación{cite}`lhco_2020`.

```{figure} ./../../figuras/lhco-topologia.png
---
width: 700px
name: lhco-topologia
---
Un tipo de topología que se puede encontrar en los datos de las LHCO 2020. Evento dijet por el decaimiento de una partícula de nueva física en dos partículas de nueva física que decaen a jets. Tomada de {cite}`lhco_2020`.
```

En esta sección se describirán los conjuntos de datos públicados, los algoritmos participantes y los resultados obtenidos. Para mayor información acerca de cualquiera de los puntos, consultar {cite}`Kasieczka_2021`.

## Datos
El estado final esta enfocado en múltiples jets. A pesar de esto, en los datos proporcionados, el espacio de fase de los observables y el de posibles parámetros de BSM son grandes, es decir, proporcionan la información de todos los hadrones de cada evento.

Para las olimpiadas publicaron dos tipos de archivo: una simulación de Monte Carlo del fondo, sin eventos de nueva física o señal, un conjunto de datos con señal y tres cajas negras, que pueden o no contener señal. 


Las cajas negras son los conjuntos de datos proporcionado para probar los modelos previamente desarrollados. Estos se publicaron por etapas, para permitir que los participantes ajustaran sus modelos a cada conjunto de datos. Una vez dados los resultados de las olimpiadas, se proporcionaron las etiquetas de señal y fondo para estos conjuntos.

Cada evento está compuesto por una lista de todos los hadrones ($p_T,\eta,\phi,$p_T,\eta,\phi,\dots$), con relleno de ceros hasta 700 hadrones. Todos los eventos tienen al menos un jet anti-kT con R=1.0, pseudorapidez $\abs{\eta}<2.5$ y momento transversal $p_T > 1.2 TeV$.

### Conjunto R&D
Este es el conjunto para ser usado para analizar los datos y entrenar modelos supervisados, es decir, contiene una etiqueta que define si un evento es señal (1) o es fondo (0). 

Consiste en 1,000,0000 de eventos dijets de QCD, o eventos de fondo, y 100,000 eventos de BSM $Z'\rightarrow XY$ con $X\rightarrow q\bar{q}$ y $Y\rightarrow q\bar{q}$. Las masas de las partículas *Z'*, *X* y *Y* son 3.5 TeV, 500 GeV y 100 GeV, respectivamente.

```{figure} ./../../figuras/lhco-RnD.png
---
width: 500px
name: lhco-RnD
---
Diagrama de Feynmman para la señal del conjunto R&D y la BB1. Producción del boson *Z'* de física BSM y su decaimiento a las partículas *X* y *Y * de física BSM. Estas últimas, decayendo a jets.
```
Los eventos de este conjunto de datos se produjeron utilizando Pythia y Delphes con la configuración por defecto.

### Caja negra 1 (BB1)
Este conjunto posee la misma señal que el conjunto R&D pero con masas para *Z'*, *X* y *Y* de 3.823 TeV, 732 GeV y 378 GeV.

Consiste en 1,000,000 de eventos, de los cuales 834 son señal.

Los eventos de fondo en la Caja Negra 1 son diferentes a los del conjunto R&D. Algunas configuraciones por defecto de Pythia y Delphes fueron cambiadas.

### Caja negra 2 (BB2)
La caja negra 2 no tiene señal. Contiene 1,000,0000 de eventos de fondo, producido usando Herwig++ en vez de Pythia.

### Caja negra 3 (BB3)
La última caja negra contiene una resonancia pesada (graviton KK) con masa de 4.2 TeV y dos modos de decaimiento. El primer modo decae a dijest y el segundo a una resonancia neutral más ligera R (el radion IR) de masa de 2.217 TeV, más un gluon con $R\rightarrow gg$. Del millón de eventos, 1200 eventos dijet y 2000 eventos trijet fueron incluidos, con fondo de QCD. 

```{figure} ./../../figuras/lhco-BB3.png
---
width: 500px
name: lhco-RnD
---
Diagrama de Feynmman para la señal del conjunto BB3. Arriba, el modo de decaimiento a tres jets. Abajo, el modo de decaimiento a dos jets.
```
El fondo fue simulado con una configuración modificada de Pythia y Delphes.

## Participantes
Los participantes debieron reporta al menos alguno de los siguientes resultados utilizando las cajas negras:
- Un valor p asociado a la falta de nuevas partículas en el conjunto de datos.
- Una descripción completa de la nueva física: masas y modos de decaimiento de las nuevas partículas.
- Cuantos eventos de señal hay en el conjunto de datos (antes de cualquier criterio de selección)

Los modelos participantes se encuentran agrupados dependiendo del método utilizado:
- **(Semi-)Supervisado**: los modelos supervisados necesitan datos etiquetados acerca de la señal para construir sensibilidad.
- **Debilmente supervisado**: utilizan etiquetas ruidosas (posiblemente sin señal/posiblemente sin fondo) en el proceso de entrenamiento.
- **No supervisados**: no necesitan datos etiquetados para el entrenamiento.

Un **resumen de los participantes**, con los métodos y los datos que analizaron se encuentra en la siguiente tabla. Las columnas de resultados hace referencia a los datos con los que los participantes hicieron el análisis, es decir, si utilizaron las cajas negras con o sin la información de las etiquetas de los eventos:

| Nombre | Método | Resultado sin etiqueta| Resultado con etiqueta|
|--------|------|-------------------------|-----------------------|
|   VRNN |No supervisado| BB2,3           | BB1|
|   ANODE|No supervisado|     -           | R&D|
| BuHuLaSpa|No supervisado| BB2,3         |BB1 |
|  GAN-AE|No supervisado| BB2,3           |BB1 |
|     GIS|No supervisado| BB1             | - |
|     LDA|No supervisado| BB1-3           | - |
|    PGAE|No supervisado| -               |BB1,2|
| Reg. Likelihoods| No supervisado|   -   |R&D|
| UCluster|No supervisado|  BB2,3         | - |
|   CWoLa|Debilmente supervisado|  -      |BB1,2|
|CWoLa AE Compare|Debilmente supervisado/No supervisado| - |R&D|
|Tag N' Train|Debilmente supervisado| BB1-3| - |
|   SALAD|Debilmente supervisado| -       |R&D|
|SA-CWoLa|Debilmente supervisado| -       |R&D|
|Deep Ensemble|(Semi-)Supervisado| BB1    | - |
| Factorized Topics| (Semi-)Supervisado| -|R&D|
|    QUAK|(Semi-)Supervisado| BB2,3       | BB1|
|    LSTM|(Semi-)Supervisado| BB1-3       | - |


## Resultados 
## Comparación de los algoritmos
