---
tags: Tesis
---
Algoritmos LHCO 2020
===

---

# No supervisados

---

## VRNN

Variational Recurrent Neural Network: Sustituye el paso encoder/decoder de una Red Neuronal Recurrente (RNN) con un Autoencoder Variacional (VAE). 
- Modela secuencias
- Interferencia variacional: herramienta para detección de anomalías

Supone los jets como un elemento anómalo de un conjunto de datos contaminados. La VRNN modela los jets como secuencias de cuadrivectores de constituyentes.

----

### Arquitectura VRNN

![Arquitectura VRNN](https://i.imgur.com/hNubWFf.png)

---

## ANODE

Asumiendo que la señal está localizada, se puede estimar la densidad de probabilidad en las bandas laterales e interpolarla a la región de señal, construyendo una proporción de verosimilitudes entre datos y fondo.

Utiliza normalizing flows, en particular Masked Autoregressive Flow (MAF): estos métodos estiman las densidades mediante el uso de una sucesión de redes neuronales para asignar gradualmente los datos originales a un conjunto de datos transformado que sigue una distribución simple (por ejemplo, normal o uniforme).

---

## BuHuLaSpa

Bump Hunting in Latent Space asume que los eventos fueron generados por un proceso estocástico descrito por un modelo probabilistico generativo con variables latentes continuas.

Utiliza redes neuronales como aproximadores de verosimilitud y distribuciones a posteriori del modelo, y la arquitectura de autocodificador variacional (VAE) para optimizarlas.

---

## GAN-AE 

Combina dos algoritmos independientes:
- GAN-AE: intento de asociar la arquitectura de autoencoder con una red neuronal discriminante (MLP) como una red de confrontación generativa (GAN).
- BumpHunter: compara la distribución de la data con una referencia, evaluando un valor p y la importancia de cualquier desviación. 

Analisis completo: Usar autoencoder entrenado con GAN-AE para reducir fondo y BumpHunter para evaluar el valor p y el potencial de señal.

**Necesita fondo de referencia para usar BumpHunter**

---

## GIS

Buscar exceso de densidad en una región estrecha de un parámetro de interés en vez de en las colas de varias distribuciones de datos (in-distribución). Hacen una estimación de densidad condicional con Gaussianizing Iterative Slicing (GIS) y construyen un puntaje de anomalía de in-distribución basado en sobredensidad local para revelar la señal de manera ciega.



---

## LDA** 

Latent Dirichlet Allocation es un modelo probabilísto generativo para datos discretos.

La suposición básica es que cada evento individual puede ser modelado por una mezcla de una cantidad finita de distribuciones latentes, llamadas *topicos*. 

Desagrupan los jets y en cada corte se extrae y agrupa un conjunto de observable de la subestructura.

En cada grupo, realizan una optimización de hiperparámetros utilizando la perplejidad para encontrar el mejor modelo LDA. Definen un test estádistico y un umbral para la selección de datos, habiendo seleccionado los tópicos de señal y fondo en el modelo mirando las distribuciones latentes. Finalmente realizan un bump hunt.


**Requiere conocimiento exacto del modelo de señal y fondo**

---

## PGAE

Particle graph autoencoders basados en redes neuronales de grafos. 

Al incorporar jets como grafos, las Graph Neural Networks(GNN) pueden explotar las relaciones partícula-partícula para codificar y decodificar de manera eficiente la información a nivel de partícula dentro de los jets.

----

### Esquema

![Esquema PGAE](https://i.imgur.com/4PWj3pf.png)

---

## Reg. Likelihoods

Utiliza un método basado en flujo (Normalizaing Flows) - proporciona una verosimilitud explícita.

Específicamente utilizan el modelo M-flows: combina la idea de la reconstrucción de error de autoencoders con una densidad manejable de NF. Si existe una variedad de datos de menor dimensión en el espacio de datos, este método intenta aprender tanto la forma de esta variedad de datos M como la densidad sobre esa variedad.

---

## UCluster

Consiste en dos componentes:
- Clasificación: asegurar que eventos con propiedades similares estas juntos en el embedding space creado por la red neuronal.
- Agrupación: la red aprende a agrupar eventos similares.

Reducir la dimensionalidad de los datos utilizando una red neuronal que retenga las propiedades principales del evento de colisión. En esta representación reducida, se agrega un objetivo de agrupamiento al entrenamiento para que los puntos en este espacio estén cerca cuando comparten propiedades similares y lejos si no.

**Diseñado para ser independiente de la arquitectura de ML**. Para las olimpiadas utilizaron ABCNet, una implementación basada en grafos donde cada particula reconstruida es un nodo.

----

### Arquitectura ABCNet

![Arquitectura ABCNet](https://i.imgur.com/prLqhhI.png)

---

# Débilmente Supervisados

---

## CWoLa

Classification Without Labels es un paradigma en el que un clasificador es entrenado para distiguir mezclas estadísticas de clases.

Utiliza un clasificador binario para distinguir la región de eventos de señal de los eventos de bandas laterales, haciendo uso de muestras mezcladas de señales y fondo. Emplean cuatro bucles de aprendizaje.

Por construcción, es sensible solo a señales que resulten del decaimiento de una resonancia pesada a dos partículas significativamente más ligeras que decaen a jets. Por lo tanto, puede ser sensible a R&D y BB1 pero no a BB3.

---

## CWoLa AE Compare

Comparan CWoLa y deep autoencoders.
- CWoLa: mejor actuación para gran cantidad de señal.
  - Dense NN con cuatro capas.
- AE: robustos en el límite de bajas señales estadísticas. 
  - Un autoencoder entrenado para cada jet. Dense NN con siete capas. 

Pueden tener una intersección en el rendimiento en diferentes secciones transversales que sería de gran interés para búsquedas experimentales reales. 

---

## Tag N' Train

La técnica se basa en que los eventos de señal contienen dos o mas objetos anómalos que se pueden usar independientemente para clasificación. Utiliza un clasificador débil (autoencoder) en uno de los objetos para etiquetar muestras ricas en señales y ricas en fondo. Estas muestras luego se utilizan para entrenar a un clasificador más fuerte (CWoLa) para el otro objeto.

Utiliza imagenes de jet como entrada para ambos autoencoders, el clasificador TNT y un modelo basado en CNN.

----
### Técnica

En general, toma una entrada de data sin etiqueta y dos clasificadores iniciales, y tiene como salida dos nuevos clasificadores con actuación mejorada.

![Ilustración de la técnica TNT](https://i.imgur.com/nKQrwtV.png)

---

## SALAD

Simulation Assisted Likelihood-free Anomaly Detection (SALAD) es una aproximación que usa redes neuronales basadas en el protocolo Deep neural networks using Classification for Tuning and Reweighting (DCTR) entrenada en una región del espacio de fase que está en gran parte desprovista de señales.

En una busqueda de resonancia, esta región puede ser aislada usando bandas laterales en la característica resonante. El modelo se interpola a la region de señal y la simulación reponderación del fondo se puede usar para mejorar la sensibilidad de señal y la estimación del fondo. 

Intuitivamente, la idea es entrenar a un clasificador para distinguir datos y simulación en la región de señal. Sin embargo, pueden haber diferencias entre el fondo de los datos y de la simulación, por lo que una función de reponderación se aprende en las bandas laterales que hace que la simulación parezca más al fondo en los datos.

---

## SA-CWoLa

Dos aproximaciones: Classification without Labels (CWoLa) y Simulation Assisted Likelihood-free Anomaly Detection (SALAD).

Se introduce la aproximación SA-CWoLa que aumenta la función de pérdida de CWoLa para penalizar al clasificador por aprender diferencias entre la región de señal y de bandas laterales en la simulación, que es libre de señal por construcción.

---

# Semi-supervisados

---

## Deep Ensemble

Mezcla de redes neuronales con capas convolucionales (CNN) y Boosted Decision Trees (BDT). Basado en un pipeline de dos pasos para asignar probabilidades evento-por-evento es categorías señal y fondo. El modelo es entrenado para los datos etiquetados de señal y fondo.
- Tiene como entrada imágenes de los eventos.
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
|   VRNN |    NS|[Paper](https://arxiv.org/pdf/2105.09274.pdf), [Slides](https://indico.cern.ch/event/809820/contributions/3632656/attachments/1971110/3278934/AnomalyScore_LHCOlympics.pdf) | Recurrent Neural Network con Variational Autoencoder | BB1-3 |
|   ANODE|    NS| [Paper](https://arxiv.org/pdf/2001.04990.pdf), [Slides](https://indico.cern.ch/event/809820/contributions/3699483/attachments/1971094/3278905/george_stein_LHCO.pdf)| Normalizing flows: Masked Autoregressive Flow | R&D|
| BuHuLaSpa|  NS| [Paper](https://arxiv.org/pdf/2103.06595.pdf)| Variational Autoencoder | BB1-3 |
|  GAN-AE|    NS| [GitHub](https://github.com/lovaslin/GAN-AE_LHCOlympics), [BumpHunter](https://github.com/lovaslin/pyBumpHunter), [Slides](https://www.dropbox.com/s/mml3xk6c4ecd9qr/lhco_lpc%20-%20Ioan%20Dinu.pdf?dl=0) | Multilayer perceptron con autoencoder de forma GAN + BumpHunter | BB1-3 |
|     GIS|    NS| [Paper](https://arxiv.org/pdf/2012.11638.pdf) | Normalizing flow: Gaussianizing Iterative Slicing| BB1|
|     LDA|    NS| [GitHub](https://github.com/bmdillon/lda-jet-substructure), [Paper](https://arxiv.org/pdf/1904.04200.pdf), [Slides](https://indico.cern.ch/event/809820/contributions/3632625/attachments/1971084/3278910/ML4Jets_talk_barrydillon.pdf)| Latent Dirichlet Allocation + Bump hunt| BB1-3|
|     PGAE|    NS| [GitHub](https://github.com/stsan9/AnomalyDetection4Jets) | Graph neural network + Autoencoder(edge convolutional network)| BB1,2|
| Reg. Likelihoods| NS| [Github modelo](https://github.com/johannbrehmer/manifold-flow)| Normalizing flows: M-flow | R&D|
| UCluster|   NS| [Github](https://github.com/ViniciusMikuni/UCluster), [Paper](https://arxiv.org/pdf/2010.07106.pdf) | Independiente del modelo ML. Utilizaron ABCNet(GNN)| BB2,3|
|   CWoLa|    DS| [GitHub sin README](https://github.com/Jackadsa/CWoLa-Hunting/tree/tf2/LHCO-code)| Clasificador binario| BB1,2|
|CWoLa AE Compare|D/NS| [Paper](https://arxiv.org/pdf/2104.02092.pdf) | CWoLa y autoencoders| R&D|
|Tag N' Train|DS| [GitHub](https://github.com/OzAmram/TagNTrain), [Paper](https://arxiv.org/pdf/2002.12376.pdf), [Slides](https://indico.cern.ch/event/809820/contributions/3632634/attachments/1970254/3277173/TagNTrain_ML4Jets.pdf) | Autoencoder, técnica TNT y convolutional neural network| BB1-3|
|   SALAD|    DS| [GitHub](https://github.com/bnachman/DCTRHunting), [Paper](https://arxiv.org/abs/2001.05001) | DCTR| R&D|
|SA-CWoLa|    DS| [GitHub](https://github.com/bnachman/DCTRHunting), [Paper](https://arxiv.org/pdf/2009.02205.pdf)| SALAD+CWoLa| R&D|
|Deep Ensemble|SS| [GitHub](https://github.com/FFFreitas/Deep-Ensemble-Anomaly-Detection)| | BB1|
| Factorized Topics| SS| [GitHub](https://github.com/nilais/factorized-topic-modeling)| | R&D|
|    QUAK|    SS| [Paper](https://arxiv.org/abs/2011.03550)| | BB1-3|
|    LSTM|    SS| ?? | | BB1-3|

# Resultado de las olimpiadas

## BB1
### Masa resonante
![Resultados de masa resonante](https://i.imgur.com/GiCMmhN.png)

### Número de eventos
![Resultados de numero de eventos ](https://i.imgur.com/h7JEaCv.png)

### Masas hija
![Resultado masa hija](https://i.imgur.com/pLHMIGR.png)

## Ganadores
- Conditional density estimation for anomaly detection (GIS)
- Tag N' Train (TNT)

# Conceptos útiles

- Espacio latente: The latent space is simply a representation of compressed data in which similar data points are closer together in space. Latent space is useful for learning data features and for finding simpler representations of data for analysis.[1](https://towardsdatascience.com/understanding-latent-space-in-machine-learning-de5a7c687d8d)
- Generative model: Generative model is a class of models for Unsupervised learning where given training data our goal is to try and generate new samples from the same distribution. Generative models model the distribution of individual classes.[2](https://towardsdatascience.com/generative-deep-learning-lets-seek-how-ai-extending-not-replacing-creative-process-fded15b0561b)  
  A Generative model is a model of the conditional probability of the observable X, given a target y, symbolically, P(X|Y=y) while a Discriminative model is a model of the conditional probability of the target Y, given an observation x, symbolically, P(Y|X=x).[3](https://en.wikipedia.org/wiki/Generative_model)  
  A generative model includes the distribution of the data itself, and tells you how likely a given example is. For example, models that predict the next word in a sequence are typically generative models (usually much simpler than GANs) because they can assign a probability to a sequence of words.[4](https://developers.google.com/machine-learning/gan/generative)
- Autoencoder: An autoencoder accepts input, compresses it, and then recreates the original input. The two main uses of an autoencoder are to compress data to two (or three) dimensions so it can be graphed, and to compress and decompress images or documents, which removes noise in the data.[5](https://jamesmccaffrey.wordpress.com/2018/07/03/the-difference-between-an-autoencoder-and-a-variational-autoencoder/)
- Variational autoencoder: A variational autoencoder assumes that the source data has some sort of underlying probability distribution (such as Gaussian) and then attempts to find the parameters of the distribution. The one main use of a variational autoencoder is to generate new data that’s related to the original source data.[5](https://jamesmccaffrey.wordpress.com/2018/07/03/the-difference-between-an-autoencoder-and-a-variational-autoencoder/)
- Normalizing flows: Normalizing Flows are generative models which produce tractable distributions where both sampling and density evaluation can be efficient and exact.[6](https://arxiv.org/pdf/1908.09257.pdf) 
  Aprenden un mapeo biyectivo entre la distribución de datos y una gaussiana multivariada. 
  The name “normalizing flow” can be interpreted as the following:
  - “Normalizing” means that the change of variables gives a normalized density after applying an invertible transformation.
  - “Flow” means that the invertible transformations can be composed with each other to create more complex invertible transformations.[7](https://deepgenerativemodels.github.io/notes/flow/)
- Masked Autoregressive Flow: By constructing a stack of autoregressive models, each modelling the random numbers of the next model in the stack, we obtain a type of normalizing flow suitable for density estimation, which we call Masked Autoregressive Flow.[8](https://arxiv.org/pdf/1705.07057.pdf),[9](https://arxiv.org/pdf/1705.07057.pdf)  
  Masked Autoregressive Flow (MAF) uses this interpretation, where the forward mapping is an autoregressive model. However, sampling is sequential and slow, in O(n) time where n is the dimension of the samples.[10](https://deepgenerativemodels.github.io/notes/flow/)
- Generative adversarial network: The downstream task of GANs is a discrimination task between true and generated samples. Or we could say a “non-discrimination” task as we want the discrimination to fail as much as possible. So, in a GAN architecture, we have a discriminator, that takes samples of true and generated data and that try to classify them as well as possible, and a generator that is trained to fool the discriminator as much as possible. [11](https://towardsdatascience.com/understanding-generative-adversarial-networks-gans-cd6e4651a29)
  - The generative network is trained to maximise the final classification error.
  - The discriminant network is trained to minimise the final classification error.[12](https://youtu.be/6v7lJHFaZZ4)
- A multilayer perceptron (MLP): is a class of feedforward artificial neural network (ANN)
- Gaussian Iterative Slicing: GIS works by iteratively matching the 1D marginalized distribution of the data to a Gaussian.[13](https://arxiv.org/pdf/2012.11638.pdf)
- Latent Dirichlet Allocation (LDA) is a generative statistical model that allows sets of observations to be explained by unobserved groups that explain why some parts of the data are similar. For example, if observations are words collected into documents, it posits that each document is a mixture of a small number of topics and that each word's presence is attributable to one of the document's topics. LDA is an example of a topic model and belongs to the machine learning toolbox and in wider sense to the artificial intelligence toolbox.[14](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation)
  Latent Dirichlet Allocation (LDA) is a “generative probabilistic model” of a collection of composites made up of parts. In terms of topic modeling, the composites are documents and the parts are words and/or phrases (n-grams). But you could apply LDA to DNA and nucleotides, pizzas and toppings, molecules and atoms, employees and skills, or keyboards and crumbs.[15](https://towardsdatascience.com/latent-dirichlet-allocation-15800c852699)
- Deep neural networks using Classification for Tuning and Reweighting (DCTR, pronounced “doctor”) is a technique for
  - Reweighting a dataset into another using the full phase-space information (assuming they have support in the same domain)
  - If one of the datasets were generated with a Monte Carlo (MC) generator, DCTR can infer what the optimal MC parameters are for reproducing the other dataset (typically experimental data). This is referred to as MC Tuning.[16](https://github.com/bnachman/DCTR)