(alglhco)=
# Algoritmos LHCO 2020
El rendimiento de los distintos métodos que utilizaron los participantes de las LHCO 2020 sólo se puede comparar mediante los resultados que obtuvieron. Sin embargo, como se puede observar en la {numref}`lhco-resultados`, la mayoría de los modelos no reportaron el error asociado al resultado obtenido. Más aún, cada participante reportó los resultados y rendimiento del modelo de acuerdo al método utilizado, dificultando la comparación directa de la calidad del análisis. 

Uno de los objetivos principales de este trabajo es comparar directamente algunos modelos participantes de las LHCO 2020. Para ello, es necesario poder reproducir el resultado de dichos modelos. Sin embargo, estos deben cumplir múltiples de los requisitos para hacer investigación reproducible explicados en la {numref}`rpd-investigacion`, a manera de asegurar que se pueda obtener el resultado de los modelos en un rango de tiempo adecuado para el desarrollo de este trabajo. 

A continuación, se hablará del análisis de los algoritmos participantes a nivel de la reproducibilidad de sus resultados y se explicarán los modelos a comparar en este trabajo.

(alglhco-rep)=
## Reproducibilidad
Para escoger los algoritmos a comparar, se hizo una revisión extensiva de la información proporcionada por los participantes mencionados en la {numref}`lhc-participantes`. Como se explica en {numref}`rpd-investigacion`, para poder reproducir el resultado es necesario principalmente que se encuentre pública la información sobre el pre-procesamiento de los datos, el código del modelo, instrucciones para utilizarlo, información acerca del entorno computacional y licencia. Se halló lo siguiente,

```{table} Información disponible de los participantes de las LHCO 2020
:name: alglhc-participantesrep

| Nombre | Referencia | Pre-procesamiento | Código| Instrucciones | Entorno| Licencia|
|:------:|:----------:|:-----------------:|:-----:|:-------------:|:------:|:-------:|
| VRNN   | [Artículo](https://arxiv.org/pdf/2105.09274.pdf), [Presentación](https://indico.cern.ch/event/809820/contributions/3632656/attachments/1971110/3278934/AnomalyScore_LHCOlympics.pdf)|✔️ |✔️ |✔️ |- |- |
| ANODE  | [Artículo](https://arxiv.org/pdf/2001.04990.pdf), [Presentación](https://indico.cern.ch/event/809820/contributions/3699483/attachments/1971094/3278905/george_stein_LHCO.pdf)|- |- |- |- |- |
| BuHuLaSpa| [Artículo](https://arxiv.org/pdf/2103.06595.pdf)|- |✔️ |- |- |- |
| GAN-AE | [GitHub](https://github.com/lovaslin/GAN-AE_LHCOlympics), [BumpHunter](https://github.com/lovaslin/pyBumpHunter), [Presentación](https://www.dropbox.com/s/mml3xk6c4ecd9qr/lhco_lpc%20-%20Ioan%20Dinu.pdf?dl=0) |✔️ |✔️ |✔️ |✔️ |- |
| GIS    | [Artículo](https://arxiv.org/pdf/2012.11638.pdf) |- |- |- |- |- |
|  LDA   | [GitHub](https://github.com/bmdillon/lda-jet-substructure), [Artículo](https://arxiv.org/pdf/1904.04200.pdf), [Presentación](https://indico.cern.ch/event/809820/contributions/3632625/attachments/1971084/3278910/ML4Jets_talk_barrydillon.pdf)|✔️ |✔️ |✔️ |✔️ |- |
|  PGAE  | [GitHub](https://github.com/stsan9/AnomalyDetection4Jets) |✔️ |✔️ |✔️ |✔️ |- |
| Reg. Likelihoods| [Github modelo](https://github.com/johannbrehmer/manifold-flow)|- |- |- |- |- |
|UCluster| [Github](https://github.com/ViniciusMikuni/UCluster), [Artículo](https://arxiv.org/pdf/2010.07106.pdf) |✔️ |✔️ |✔️ |✔️ |✔️ |
| CWoLa  | [GitHub](https://github.com/Jackadsa/CWoLa-Hunting/tree/tf2/LHCO-code)|- |✔️ |- |- |- |
|CWoLa AE Compare| [Artículo](https://arxiv.org/pdf/2104.02092.pdf) |- |- | |- |- |
|Tag N' Train| [GitHub](https://github.com/OzAmram/TagNTrain), [Artículo](https://arxiv.org/pdf/2002.12376.pdf), [Presentación](https://indico.cern.ch/event/809820/contributions/3632634/attachments/1970254/3277173/TagNTrain_ML4Jets.pdf) |✔️ |✔️ |- |✔️ |- |
| SALAD  | [GitHub](https://github.com/bnachman/DCTRHunting), [Artículo](https://arxiv.org/abs/2001.05001) |- |✔️ |- |✔️ |- |
|SA-CWoLa| [GitHub](https://github.com/bnachman/DCTRHunting), [Artículo](https://arxiv.org/pdf/2009.02205.pdf)|- |✔️ |- |✔️ |- |
|Deep Ensemble| [GitHub](https://github.com/FFFreitas/Deep-Ensemble-Anomaly-Detection)|- |✔️ |✔️ |✔️ |- |
|Factorized Topics| [GitHub](https://github.com/nilais/factorized-topic-modeling)|- |✔️ |- |- |✔️ |
| QUAK   | [Artículo](https://arxiv.org/abs/2011.03550) |- |- |- |- |- |
| LSTM   | - |- |- |- |- |- |
```
