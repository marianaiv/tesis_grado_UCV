(lhco)=
# Olimpiadas LHC 2020
La búsqueda de física BSM es parte principal del programa de investigación del LHC. Hasta ahora no ha sido exitosa, pero se mejora constantemente. Sin embargo, es evidente que se requieren mejoraras en las herramientas de análisis para que podamos aprovechar la gran cantidad y complejidad de los datos.

Con el fin de mejorar el uso de estas herramientas para análisis de datos, se crearon las olimpiadas LHC (LHCO). Para las olimpiadas, se simulan conjuntos de datos con eventos de nueva física que podrían observarse en el acelerador. El objetivo es que los participantes interpreten los datos en términos de modelos de física BSM.

> "La idea principal es que si no lo puedes hacer para el caso simulado, es mucho menos probable que lo puedas hacer para el caso real. 
> Hace que las personas aprendan a pensar de manera diferente y aborden el problema de la forma en que habría que abordarlo" 
> 
> — Gordy Kane, Universidad de Michigan. Organizador de las LHCO{cite}`lhco_2006`.

Las olimpiadas de 2020 estuvieron enfocadas en el desarrollo técnicas de aprendizaje automático para la búsqueda de partículas resonantes de BSM. 

El desarrollo de estas herramientas para su uso en HEP se ha visto limitado porque los datos relacionados a colisiones *pp* no se encuentran públicamente disponibles y son muy diferentes a los datos que se utilizan comúnmente para estudiar estos métodos. Sin embargo, el aprendizaje automático posee un gran potencial para ampliar la búsqueda de nueva física porque permite una aproximación más amplia al problema, como las búsquedas libres de modelo. 

En el caso de las LHCO 2020, se plantean eventos BSM de una partícula resonante con un ancho de decaimiento pequeño y que tenga como producto eventos de múltiples jets. Un ejemplo de esta topología se ilustra a continuación.

```{figure} ./../../figuras/lhco-topologia.png
---
width: 400px
name: lhco-topologia
---
Un tipo de topología que se puede encontrar en los datos de las LHCO 2020. Evento dijet por el decaimiento de una partícula de nueva física en dos partículas de nueva física que decaen a jets. Tomada de {cite}`lhco_2020`.
```
En esta sección se hará un resumen de los conjuntos de datos, los algoritmos participantes y los resultados.  Para mayor información acerca de cualquiera de los puntos, consultar {cite}`Kasieczka_2021`.

(lhco-datos)=
## Conjuntos de datos
Para las olimpiadas publicaron dos tipos de archivo: una simulación de Monte Carlo del fondo, sin eventos de nueva física o señal, un conjunto de datos con señal para investigación y desarrollo (conjunto R&D) y tres cajas negras(BB1, BB2 y BB3), que pueden o no contener señal. 

Las cajas negras son los conjuntos de datos proporcionado para probar los modelos previamente desarrollados. Su contenido es desconocido para los participante. Una vez dados los resultados de las olimpiadas, se proporcionaron las etiquetas de señal y fondo para estos conjuntos.

El **conjunto R&D** y la **BB1** posee un evento de nueva física $Z'\rightarrow XY$ con $X\rightarrow q\bar{q}$ y $Y\rightarrow q\bar{q}$ con $Z'$, $X$ y $Y$ partículas de nueva física.

```{figure} ./../../figuras/lhco-RnD.png
---
width: 250px
name: datos-RnD
---
Diagrama de Feynmann para la señal del conjunto R&D y la BB1. Producción del boson *Z'* de física BSM y su decaimiento a las partículas *X* y *Y* de física BSM. Estas últimas, decayendo a jets.
```

La **BB2** no contiene señal.

La **BB3** contiene una resonancia pesada (graviton KK) con dos modos de decaimiento. El primer modo decae a dijets y el segundo a una resonancia neutral más ligera R (el radión IR), más un gluon con $R\rightarrow gg$. 

```{figure} ./../../figuras/lhco-BB3.png
---
width: 250px
name: lhco-BB3
---
Diagrama de Feynmann para la señal del conjunto BB3. Arriba, el modo de decaimiento a tres jets. Abajo, el modo de decaimiento a dos jets.
```
Los conjuntos utilizados en este trabajo son el conjunto R&D y el conjunto BB1. Detalles sobre el contenido de los datos se explicará en el capítulo siguiente.

(lhco-participantes)=
## Participantes
Los participantes reportaron al menos alguno de los siguientes resultados:
- Un valor p asociado a la falta de nuevas partículas en el conjunto de datos.
- Una descripción completa de la nueva física: masas y modos de decaimiento de las nuevas partículas.
- Numero de eventos de señal en el conjunto de datos (antes de cualquier criterio de selección).

Los modelos están agrupados dependiendo del método utilizado:
- **(Semi-)Supervisado**: los modelos supervisados necesitan datos etiquetados acerca de la señal para construir sensibilidad.
- **Débilmente supervisado**: utilizan etiquetas ruidosas (posiblemente sin señal/posiblemente sin fondo) en el proceso de entrenamiento.
- **No supervisados**: no necesitan datos etiquetados para el entrenamiento.

En la siguiente tabla se encuentra un **resumen de los participantes**, con el método, referencias y los datos que analizaron:

```{table} Participantes de las LHCO 2020
:name: lhc-participantes

| Nombre | Método | Referencia | Resultado |
|--------|------|------------|-------------|
|   VRNN | No supervisado| [Artículo](https://arxiv.org/pdf/2105.09274.pdf), [Presentación](https://indico.cern.ch/event/809820/contributions/3632656/attachments/1971110/3278934/AnomalyScore_LHCOlympics.pdf)| BB1-3 |
|   ANODE| No supervisado| [Artículo](https://arxiv.org/pdf/2001.04990.pdf), [Presentación](https://indico.cern.ch/event/809820/contributions/3699483/attachments/1971094/3278905/george_stein_LHCO.pdf)| R&D|
| BuHuLaSpa| No supervisado| [Artículo](https://arxiv.org/pdf/2103.06595.pdf)| BB1-3 |
|  GAN-AE|    No supervisado| [GitHub](https://github.com/lovaslin/GAN-AE_LHCOlympics), [BumpHunter](https://github.com/lovaslin/pyBumpHunter), [Presentación](https://www.dropbox.com/s/mml3xk6c4ecd9qr/lhco_lpc%20-%20Ioan%20Dinu.pdf?dl=0) | BB1-3 |
|     GIS|    No supervisado| [Artículo](https://arxiv.org/pdf/2012.11638.pdf) |BB1|
|     LDA|    No supervisado| [GitHub](https://github.com/bmdillon/lda-jet-substructure), [Artículo](https://arxiv.org/pdf/1904.04200.pdf), [Presentación](https://indico.cern.ch/event/809820/contributions/3632625/attachments/1971084/3278910/ML4Jets_talk_barrydillon.pdf)| BB1-3|
|     PGAE|    No supervisado| [GitHub](https://github.com/stsan9/AnomalyDetection4Jets) | BB1,2|
| Reg. Likelihoods| No supervisado| [Github modelo](https://github.com/johannbrehmer/manifold-flow)| R&D|
| UCluster|   No supervisado| [Github](https://github.com/ViniciusMikuni/UCluster), [Artículo](https://arxiv.org/pdf/2010.07106.pdf) | BB2,3|
|   CWoLa|Débilmente supervisado| [GitHub](https://github.com/Jackadsa/CWoLa-Hunting/tree/tf2/LHCO-code)| BB1,2|
|CWoLa AE Compare|Débilmente/No supervisado| [Artículo](https://arxiv.org/pdf/2104.02092.pdf) | R&D|
|Tag N' Train|Débilmente supervisado| [GitHub](https://github.com/OzAmram/TagNTrain), [Artículo](https://arxiv.org/pdf/2002.12376.pdf), [Presentación](https://indico.cern.ch/event/809820/contributions/3632634/attachments/1970254/3277173/TagNTrain_ML4Jets.pdf) | BB1-3|
|   SALAD|Débilmente supervisado| [GitHub](https://github.com/bnachman/DCTRHunting), [Artículo](https://arxiv.org/abs/2001.05001) | R&D|
|SA-CWoLa|Débilmente supervisado| [GitHub](https://github.com/bnachman/DCTRHunting), [Artículo](https://arxiv.org/pdf/2009.02205.pdf)| R&D|
|Deep Ensemble|Semi-supervisado| [GitHub](https://github.com/FFFreitas/Deep-Ensemble-Anomaly-Detection)| BB1|
| Factorized Topics|Semi-supervisado| [GitHub](https://github.com/nilais/factorized-topic-modeling)| R&D|
|    QUAK|Semi-supervisado| [Artículo](https://arxiv.org/abs/2011.03550) | BB1-3|
|    LSTM|Semi-supervisado| - | BB1-3|
```

(lhco-resultados-cap)=
## Resultados 
Los resultados individuales de cada modelo se encuentran en {cite}`Kasieczka_2021`. Sin embargo, se pueden resumir cronológicamente en tres etapas
### ML4Jets workshop 
Durante este taller se publicó la BB1. En la siguiente figura se resumen los resultados de los nueve participantes de esta etapa:
```{figure} ./../../figuras/lhco-resultados.png
---
width: 700px
name: lhco-resultados
---
Resultados de la primera caja negra. En la figura se encuentran las predicciones de la masa resonante (arriba a la izquierda), el número de eventos de señal (arriba a la derecha), la masa de la primera partícula hija (abajo a la izquierda) y de la segunda partícula hija (abajo a la derecha). En un panel más pequeño se encuentra el "pull" *(respuesta-verdadera)/incertidumbre*
```
Los modelos LSTM, Tag N Train y GIS identificaron la masa correcta de la resonancia en una ventana de $\pm 200$ GeV y PCA (análisis de componentes principales) identificó dentro del error. Las predicciones de otros observables fueron logradas únicamente por GIS.
### Verano 2020
Los conjuntos de datos BB2 y BB3 fueron publicados en el verano de 2020. Para la BB2, el modelo LDA fue el único que predijo ausencia de señal. Ningún participante logró detectar la resonancia de la BB3.

### Revelación de las cajas negras
Después de revelar las señales de las cajas negras y publicar las etiquetas de los eventos para cada caja, algunos modelos enviaron mejoras para el conjunto BB1 únicamente.
- VRNN y BuHuLaSpa reportaron una mejora en la masa invariante debajo de 4 TeV,
- Deep Ensemble detectó una resonancia en 3.5 Tev,
- LDA una resonancia no incompatible con 3.8 TeV,
- PGA detectó una resonancia en 3.9 TeV
- CWoLa observó una resonancia en 3.5 TeV

En el siguiente capítulo se describirá con mayor detalle los datos de las olimpiadas y los algoritmos participantes utilizados en este trabajo.