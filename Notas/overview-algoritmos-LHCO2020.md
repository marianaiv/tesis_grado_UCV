---
tags: Tesis
---
Algoritmos LHCO 2020
===

---

# No supervisados

---

## VRNN

Utiliza un método de búsqueda de objetos en decaimiento hadrónico potenciados tratándolos como elementos anómalos de un conjunto de datos contaminados. Se utiliza una red neuronal recurrente variacional (VRNN) para modelar jets como secuencias de cuatro vectores constituyentes.


---

## ANODE

Estimando la densidad de probabilidad condicional en una región de señal y en las bandas laterales, e interpolando esta última en la región de señal, se puede construir una proporción de verosimilitudes de datos vs. fondo a partir de los datos.

---

## BuHuLaSpa

Asume que los eventos fueron generados por un proceso estocástico descrito por un modelo probabilistico generativo con variables latentes continuas.
Utiliza redes neuronales como aproximadores de verosimilitud y posterior distribución del modelo, y la arquitectura de codificador automático variacional (VAE) para optimizarlas.

---

## GAN-AE 

Combina dos algoritmos independientes:
- GAN-AE: intento de asociar la arquitectura auto-encoder con una red neuronal discriminante (MLP) en una manera GAN.
- BumpHunter: compara la distribución de la data con una referencia, evaluando un valor p y la importancia de cualquier desviación. 

Analisis completo: Usar GAN-AE para reducir fondo y BumpHunter para evaluar el valor p y el potencial de señal.

**Necesita fondo de referencia para usar BumpHunter**

---

## GIS

Buscar exceso de densidad en una región estrecha de un parámetro de interés en vez de en las colas de varias distribuciones de datos (in-distribución). Hacen una estimación de densidad condicional con Gaussianizing Iterative Slicing y construyen un puntaje de anomalía de in-distribución basado en sobredensidad local para revelar la señal de manera ciega.

---

## LDA** 

Latent Dirichlet Allocation es un modelo probabilísto generativo para datos discretos.
La suposición básica es que cada evento individual puede ser modelado por una mezcla de una cantidad finita de distribuciones latentes, llamadas *topicos*. 

Desagrupan los jets y en cada corte se extrae y agrupa un conjunto de observable de la subestructura.

**Requiere conocimiento exacto del modelo de señal y fondo**

---

## PGA

Particle graph autoencoders basados en redes neuronales de grafos. 

Al incorporar jets como grafos, los GNN pueden explotar las relaciones partícula-partícula para codificar y reconstruir de manera eficiente la información a nivel de partículas dentro de los jets.

---

## Reg. Likelihoods

Utiliza un método basado en flujo (Normalizaing Flows) - proporciona una verosimilitud explícita.

Aprenden un mapeo biyectivo entre la distribución de datos y una gaussiana multivariada. 

Específicamente utilizan el modelo M-flows: combina la idea de la reconstrucción de error de autoencoders con una densidad manejable de NF. Si existe una variedad de datos de menor dimensión en el espacio de datos, este método intenta aprender tanto la forma de esta variedad de datos M como la densidad sobre esa variedad.

---

## UCluster

Reducir la dimensionalidad de los datos utilizando una red neuronla que retenga las propiedades principales del evento de colisión. En esta representación reducida, se agrega un objetivo de agrupamiento al entrenamiento para que los puntos en este espacio estén cerca cuando comparten propiedades similares y lejos si no.

**Diseñado para ser independiente de la arquitectura de ML**. Para las olimpiadas utilizaron ABCNet, una implementación basada en grafos donde cada particula reconstruida es un nodo.

---

# Débilmente Supervisados

---

## CWoLa

Dada una hipótesis de masa resonante y un ancho, se construye una región de señal seleccionando los eventos en una ventana alrededor de la hipótesis de masa resonante.
Utiliza un clasificador binario para distinguir la región de eventos de los eventos laterales. Cuatro loops de aprendizaje.

- Bump hunt y test de hipótesis de Poisson en la tasa observada de eventos en la región de señal comparada con el parámetro esperado. 
- ReLU, Adam

---

## CWoLa AE Compare

Comparan CWoLa y deep autoencoders.
- CWoLa: mejor actuación para gran cantidad de señal
- AE: robustos en el límite de bajas señales estadísticas.
Pueden tener una intersección en el rendimiento en diferentes secciones transversales que sería de gran interés para búsquedas experimentales reales. 

CWoLa: lamina anterior
AE: Dos autoencoders entrenados en jet 1 y 2. Entrenaron 20 modelos y reconstruyeron el error para cada uno. El error final con la media. 

NN: ReLU - Linear. 
Loss Function: Minimum squared error. 
Adam optimizer

---

## Tag N' Train

La técnica utiliza un clasificador débil (autoencoder) en uno de los objetos para etiquetar muestras ricas en señales y ricas en fondo. Estas muestras luego se utilizan para entrenar un clasificador más fuerte (CWoLa) para otro objeto.

Utiliza imagenes de jet como entrada para ambos autoencoders y el clasificador TNT y un modelo basado en CNN entrenado con un optimizador Adam.

---

## SALAD

Tiene una aproximación que utiliza simulación de fondo de manera que depende lo menos posible de la simulación. En particula, una red neuronal basada en redes neuronales profundas que utilizan clasificación para tuning y reweighting es entrenada en una region del espacio de fase que carece en gran medida de señales. Esta región puede ser aislada utilizando bandas laterales en la característica resonante. El modelo se interpola a la region de señal y la simulación de fondo reweighted se puede usar para mejorar la sensitividad de señal y la estimación del fondo. 

---

## SA-CWoLa

Dos aproximaciones: Classification without Labels (CWoLa) y Simulation Assisted Likelihood-free Anomaly Detection (SALAD).
Se introduce la aproximación SA-CWoLa que aumenta la función de perdida de CWoLa para penalizar al clasificador por aprender diferencias entre la región de señal y de bandas laterales en la simulación, que es libre de señal por construcción.

---

# Semi-supervisados

---

## Deep Ensemble

Mezcla de redes neuronales con capas convolucionales y Boosted Decision Trees. Basado en un pipeline de dos pasos para asignar probabilidades evento-por-evento es categorías señal y fondo. El modelo es entrenado para los datos etiquetados de señal y fondo.
- CNN para clasificación de la imagen: pre-entrenada ResNet-34 como preclasificador. 
- BDT con las predicciones del ResNet-34 y la información cinemática.

---

## Factorized Topics



---

## QUAK

- Escoger un fondo y un conjunto de señales previamente aproximadas que capturen las caracteristicas de nueva física.
- Entrenar N modelos probabilisticos no supervisados, separados, para cada señal previa o fondo previo
- Construir un espacio 'QUAK' N-dimensional que consista en la pérdida de cada modelo probabilistico no supervisado
- Explotar el espacio QUAK para buscar anomalías.

---

## LSTM

Agrupa los hadrones en jets anti-kT R = 0,7 y ejecuta la secuencia de jets en un RNN simple (aprendizaje supervisado). La secuencia está ordenada por el pT de los jets de alto a bajo. Dos capas de LSTM, con algunas capas densas después y una única salida que identifica si es señal o no.

---

# Tabla resumen

| Nombre | Tipo | Referencia | Descripción | Participa |
|--------|------|------------|-------------|-----------|
|   VRNN |    NS|[Paper](https://arxiv.org/pdf/2105.09274.pdf) |  | BB1-3 |
|   ANODE|    NS| [Paper](https://arxiv.org/pdf/2001.04990.pdf)| | R&D|
| BuHuLaSpa|  NS| [Paper](https://arxiv.org/pdf/2103.06595.pdf)| | BB1-3 |
|  GAN-AE|    NS| [GitHub](https://github.com/lovaslin/GAN-AE_LHCOlympics), [BumpHunter](https://github.com/lovaslin/pyBumpHunter) | | BB1-3 |
|     GIS|    NS| [Paper](https://arxiv.org/pdf/2012.11638.pdf) | | BB1|
|     LDA|    NS| [GitHub](https://github.com/bmdillon/lda-jet-substructure), [Paper](https://arxiv.org/pdf/1904.04200.pdf)| | BB1-3|
|     PGA|    NS| [GitHub](https://github.com/stsan9/AnomalyDetection4Jets) | | BB1,2|
| Reg. Likelihoods| NS| [Github modelo](https://github.com/johannbrehmer/manifold-flow)| | R&D|
| UCluster|   NS| [Github](https://github.com/ViniciusMikuni/UCluster), [Paper](https://arxiv.org/pdf/2010.07106.pdf) | | BB2,3|
|   CWoLa|    DS| [GitHub sin README](https://github.com/Jackadsa/CWoLa-Hunting/tree/tf2/LHCO-code)| | BB1,2|
|CWoLa AE Compare|D/NS| [Paper](https://arxiv.org/pdf/2104.02092.pdf) | | R&D|
|Tag N' Train|DS| [GitHub](https://github.com/OzAmram/TagNTrain), [Paper](https://arxiv.org/pdf/2002.12376.pdf), [Slides](https://indico.cern.ch/event/809820/contributions/3632634/attachments/1970254/3277173/TagNTrain_ML4Jets.pdf) | | BB1-3|
|   SALAD|    DS| [GitHub](https://github.com/bnachman/DCTRHunting), [Paper](https://arxiv.org/abs/2001.05001) | | R&D|
|SA-CWoLa|    DS| [GitHub](https://github.com/bnachman/DCTRHunting), [Paper](https://arxiv.org/pdf/2009.02205.pdf)| | R&D|
|Deep Ensemble|SS| [GitHub](https://github.com/FFFreitas/Deep-Ensemble-Anomaly-Detection)| | BB1|
| Factorized Topics| SS| [GitHub](https://github.com/nilais/factorized-topic-modeling)| | R&D|
|    QUAK|    SS| [Paper](https://arxiv.org/abs/2011.03550)| | BB1-3|
|    LSTM|    SS| ?? | | BB1-3|