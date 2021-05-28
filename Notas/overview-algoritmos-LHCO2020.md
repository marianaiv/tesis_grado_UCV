---
tags: Tesis
---
Algoritmos LHCO 2020
===

# No supervisados

## VRNN

El método Variational Recurrent Neural Network sustituye el paso encoder/decoder de una Red Neuronal Recurrente (RNN) con un Autoencoder Variacional (VAE). La idea es obtener los beneficios de ambas aproximaciones:
- Modela secuencias
- Interferencia variacional: herramienta para detección de anomalías

Supone los jets como un elemento anómalo de un conjunto de datos contaminados. La VRNN modela los jets como secuencias de cuadrivectores de constituyentes.

### Arquitectura

![Arquitectura VRNN](https://i.imgur.com/hNubWFf.png)

## ANODE

Anomaly Detection with Density Estimation asume que la señal está localizada, por lo que se puede estimar la densidad de probabilidad en las bandas laterales e interpolarla a la región de señal, construyendo una proporción de verosimilitudes entre datos y fondo.

Utiliza flujos normalizantes, en particular Masked Autoregressive Flow (MAF): estos métodos estiman las densidades mediante el uso de una sucesión de redes neuronales para asignar gradualmente los datos originales a un conjunto de datos transformado que sigue una distribución simple (por ejemplo, normal o uniforme).

## BuHuLaSpa

Bump Hunting in Latent Space asume que los eventos fueron generados por un proceso estocástico descrito por un modelo probabilistico generativo con variables latentes continuas.

Utiliza redes neuronales como aproximadores de verosimilitud y distribuciones a posteriori del modelo, y la arquitectura de autoencoder variacional (VAE) para optimizarlas.

## GAN-AE 

Combina dos algoritmos independientes:
- GAN-AE: intento de asociar la arquitectura de autoencoder con una red neuronal discriminante (MLP) como una red de confrontación generativa (GAN).
- BumpHunter: compara la distribución de la data con una referencia, evaluando un valor p y la importancia de cualquier desviación. 

Analisis completo: Usar autoencoder entrenado con GAN-AE para reducir fondo y BumpHunter para evaluar el valor p y el potencial de señal.

**Necesita fondo de referencia para usar BumpHunter**

## GIS

La idea principal es buscar exceso de densidad en una región estrecha de un parámetro de interés, en vez de en las colas de varias distribuciones de datos como se suele hacer (in-distribución). 

Hacen una estimación de densidad condicional con Gaussianizing Iterative Slicing (GIS) y construyen un puntaje de anomalía de in-distribución basado en sobredensidad local para revelar la señal de manera ciega.

## LDA** 

Latent Dirichlet Allocation es un modelo probabilísto generativo para datos discretos. La suposición básica es que cada evento individual puede ser modelado por una mezcla de una cantidad finita de distribuciones latentes llamadas *topicos*. 

Desagrupan los jets y en cada corte se extrae y se agrupa un conjunto de observable de la subestructura. 

En cada grupo, realizan una optimización de hiperparámetros utilizando la perplejidad para encontrar el mejor modelo LDA. Definen un test estádistico y un umbral para la selección de datos, habiendo seleccionado los tópicos de señal y fondo en el modelo mirando las distribuciones latentes. Finalmente realizan un bump hunt.


**Requiere conocimiento exacto del modelo de señal y fondo**

## PGAE

Particle graph autoencoders basados en redes neuronales de grafos. 

Al incorporar jets como grafos, las Graph Neural Networks(GNN) pueden explotar las relaciones partícula-partícula para codificar y decodificar de manera eficiente la información a nivel de partícula dentro de los jets.

### Esquema

![Esquema PGAE](https://i.imgur.com/4PWj3pf.png)

## Reg. Likelihoods

Utiliza un método basado en flujo (Normalizaing Flows) - proporciona una verosimilitud explícita.

Específicamente utilizan el modelo M-flows: combina la idea de la reconstrucción de error de autoencoders con una densidad manejable de NF. Si existe una variedad de datos de menor dimensión en el espacio de datos, este método intenta aprender tanto la forma de esta variedad de datos M como la densidad sobre esa variedad.

## UCluster

Consiste en dos componentes:
- Clasificación: asegurar que eventos con propiedades similares estas juntos en el embedding space creado por la red neuronal.
- Agrupación: la red aprende a agrupar eventos similares.

Reducir la dimensionalidad de los datos utilizando una red neuronal que retenga las propiedades principales del evento de colisión. En esta representación reducida, se agrega un objetivo de agrupamiento al entrenamiento para que los puntos en este espacio estén cerca cuando comparten propiedades similares y lejos si no.

**Diseñado para ser independiente de la arquitectura de ML**. Para las olimpiadas utilizaron ABCNet, una implementación basada en grafos donde cada particula reconstruida es un nodo.

### Arquitectura ABCNet

![Arquitectura ABCNet](https://i.imgur.com/prLqhhI.png)

# Débilmente Supervisados

## CWoLa

Classification Without Labels es un paradigma en el que un clasificador es entrenado para distiguir mezclas estadísticas de clases.

Utiliza un clasificador binario para distinguir la región de eventos de señal de los eventos de bandas laterales, haciendo uso de muestras mezcladas de señales y fondo. Emplean cuatro bucles de aprendizaje.

Por construcción, es sensible solo a señales que resulten del decaimiento de una resonancia pesada a dos partículas significativamente más ligeras que decaen a jets. Por lo tanto, puede ser sensible a R&D y BB1 pero no a BB3.

## CWoLa AE Compare

Comparan CWoLa y deep autoencoders.
- CWoLa: mejor actuación para gran cantidad de señal.
  - Dense NN con cuatro capas.
- AE: robustos en el límite de bajas señales estadísticas. 
  - Un autoencoder entrenado para cada jet. Dense NN con siete capas. 

Pueden tener una intersección en el rendimiento en diferentes secciones transversales que sería de gran interés para búsquedas experimentales reales. 

## Tag N' Train

La técnica se basa en que los eventos de señal contienen dos o mas objetos anómalos que se pueden usar independientemente para clasificación. Utiliza un clasificador débil (autoencoder) en uno de los objetos para etiquetar muestras ricas en señales y ricas en fondo. Estas muestras luego se utilizan para entrenar a un clasificador más fuerte (CWoLa) para el otro objeto.

Utiliza imagenes de jet como entrada para ambos autoencoders, el clasificador TNT y un modelo basado en CNN.

### Diagrama

En general, toma una entrada de data sin etiqueta y dos clasificadores iniciales, y tiene como salida dos nuevos clasificadores con actuación mejorada.

![Ilustración de la técnica TNT](https://i.imgur.com/nKQrwtV.png)

## SALAD

Simulation Assisted Likelihood-free Anomaly Detection (SALAD) es una aproximación que usa redes neuronales basadas en el protocolo Deep neural networks using Classification for Tuning and Reweighting (DCTR) entrenada en una región del espacio de fase que está en gran parte desprovista de señales.

En una busqueda de resonancia, esta región puede ser aislada usando bandas laterales en la característica resonante. El modelo se interpola a la region de señal y la simulación reponderación del fondo se puede usar para mejorar la sensibilidad de señal y la estimación del fondo. 

Intuitivamente, la idea es entrenar a un clasificador para distinguir datos y simulación en la región de señal. Sin embargo, pueden haber diferencias entre el fondo de los datos y de la simulación, por lo que una función de reponderación se aprende en las bandas laterales que hace que la simulación parezca más al fondo en los datos.

## SA-CWoLa

Dos aproximaciones: Classification without Labels (CWoLa) y Simulation Assisted Likelihood-free Anomaly Detection (SALAD).

Se introduce la aproximación SA-CWoLa que aumenta la función de pérdida de CWoLa para penalizar al clasificador por aprender diferencias entre la región de señal y de bandas laterales en la simulación, que es libre de señal por construcción.

# Semi-supervisados


## Deep Ensemble

Mezcla de redes neuronales con capas convolucionales (CNN) y Boosted Decision Trees (BDT). Basado en un pipeline de dos pasos para asignar probabilidades evento-por-evento en categorías señal y fondo. El modelo es entrenado con los datos etiquetados de señal y fondo.
- Tiene como entrada imágenes de los eventos.
- CNN para clasificación de la imagen: pre-entrenada ResNet-34 como preclasificador. 
- BDT con las predicciones del ResNet-34 y la información cinemática.

## Factorized Topics

Partiendo del marco de "jet topics ", hacen uso un teorema de factorización para la subestructura del jet (la sección transversal para la producción de dijets satisface un teorema de factorización de primer orden, lo que implica que ambos jets son estadísticamente independientes) para construir un modelo generativo, y demuestran un procedimiento para optimizarlo, recuperando ambas fracciones relativas de diferentes tipos de jets dentro de una muestra mixta, así como la distribución de componentes para un observable dado.

Utilizan la norma de Frobenius como función de pérdida.

## QUAK

Para construir QUAK:

- Escoger un fondo y un conjunto de señales previamente aproximadas que capturen las caracteristicas de nueva física.
- Entrenar N modelos probabilisticos no supervisados, separados, para cada señal previa o fondo previo
- Construir un espacio 'QUAK' N-dimensional que consista en la pérdida de cada modelo probabilistico no supervisado
- Explotar el espacio QUAK para buscar anomalías.

Utilizan un variational autoencoder con flujos normalizantes en el espacio latente, para transformar la distribución posterior en una distribución más flexible que sea representativa de los datos correspondientes.

### Arquitectura

![Normalizing flow variational autoencoder](https://i.imgur.com/7rSaQLd.png)

## LSTM

Agrupa los hadrones en jets anti-kT R = 0,7 y ejecuta la secuencia de jets en un red neuronal recurrente (RNN) simple.

Se emplearon dos capas Long Short-Term Memory (LSTM), con algunas capas densas después y una única salida que identifica si es señal o no.

# Tabla resumen

| Nombre | Método | Referencia | Descripción | Resultado |
|--------|------|------------|-------------|-----------|
|   VRNN |    NS|[Paper](https://arxiv.org/pdf/2105.09274.pdf), [Slides](https://indico.cern.ch/event/809820/contributions/3632656/attachments/1971110/3278934/AnomalyScore_LHCOlympics.pdf) | Red neuronal recurrente con Autoencoder variacional | BB1-3 |
|   ANODE|    NS| [Paper](https://arxiv.org/pdf/2001.04990.pdf), [Slides](https://indico.cern.ch/event/809820/contributions/3699483/attachments/1971094/3278905/george_stein_LHCO.pdf)| Flujo normalizante: Masked Autoregressive Flow | R&D|
| BuHuLaSpa|  NS| [Paper](https://arxiv.org/pdf/2103.06595.pdf)| Autoencoder variacional| BB1-3 |
|  GAN-AE|    NS| [GitHub](https://github.com/lovaslin/GAN-AE_LHCOlympics), [BumpHunter](https://github.com/lovaslin/pyBumpHunter), [Slides](https://www.dropbox.com/s/mml3xk6c4ecd9qr/lhco_lpc%20-%20Ioan%20Dinu.pdf?dl=0) | Perceptron multicapa con autoencoder de forma GAN + BumpHunter | BB1-3 |
|     GIS|    NS| [Paper](https://arxiv.org/pdf/2012.11638.pdf) | Flujo normalizante: Gaussianizing Iterative Slicing| BB1|
|     LDA|    NS| [GitHub](https://github.com/bmdillon/lda-jet-substructure), [Paper](https://arxiv.org/pdf/1904.04200.pdf), [Slides](https://indico.cern.ch/event/809820/contributions/3632625/attachments/1971084/3278910/ML4Jets_talk_barrydillon.pdf)| Latent Dirichlet Allocation + Bump hunt| BB1-3|
|     PGAE|    NS| [GitHub](https://github.com/stsan9/AnomalyDetection4Jets) | Red neuronal de grafos + Autoencoder(edge convolutional network)| BB1,2|
| Reg. Likelihoods| NS| [Github modelo](https://github.com/johannbrehmer/manifold-flow)| Flujos normalizantes: M-flow | R&D|
| UCluster|   NS| [Github](https://github.com/ViniciusMikuni/UCluster), [Paper](https://arxiv.org/pdf/2010.07106.pdf) | Independiente del modelo ML. Utilizaron ABCNet(GNN)| BB2,3|
|   CWoLa|    DS| [GitHub sin README](https://github.com/Jackadsa/CWoLa-Hunting/tree/tf2/LHCO-code)| Clasificador binario| BB1,2|
|CWoLa AE Compare|D/NS| [Paper](https://arxiv.org/pdf/2104.02092.pdf) | CWoLa y autoencoders| R&D|
|Tag N' Train|DS| [GitHub](https://github.com/OzAmram/TagNTrain), [Paper](https://arxiv.org/pdf/2002.12376.pdf), [Slides](https://indico.cern.ch/event/809820/contributions/3632634/attachments/1970254/3277173/TagNTrain_ML4Jets.pdf) | Autoencoder, técnica TNT y red neuronal convolucional| BB1-3|
|   SALAD|    DS| [GitHub](https://github.com/bnachman/DCTRHunting), [Paper](https://arxiv.org/abs/2001.05001) | DCTR| R&D|
|SA-CWoLa|    DS| [GitHub](https://github.com/bnachman/DCTRHunting), [Paper](https://arxiv.org/pdf/2009.02205.pdf)| SALAD+CWoLa| R&D|
|Deep Ensemble|SS| [GitHub](https://github.com/FFFreitas/Deep-Ensemble-Anomaly-Detection)| Red neuronal convolucional + Bosted decision tree | BB1|
| Factorized Topics| SS| [GitHub](https://github.com/nilais/factorized-topic-modeling)| Restricción estadística | R&D|
|    QUAK|    SS| [Paper](https://arxiv.org/abs/2011.03550) |Autoencoder variacional + Flujo normalizante | BB1-3|
|    LSTM|    SS| ?? | Red neuronal recurrente: Long Short-Term Memory| BB1-3|

# Resultado de las olimpiadas 
## BB1
Estos resultados son el análisis ciego de la Black Box 1.
### Masa resonante
![Resultados de masa resonante](https://i.imgur.com/GiCMmhN.png)

### Número de eventos
![Resultados de numero de eventos ](https://i.imgur.com/h7JEaCv.png)

### Masas hija
![Resultado masa hija](https://i.imgur.com/pLHMIGR.png)

### Ganadores
- Conditional density estimation for anomaly detection (GIS)
- Tag N' Train (TNT)

## Black Box 2
Algunas resonancias fueron detectadas a pesar de la falta de señal:
- PCA: 4.2 TeV
- VRNN: 4.6 TeV
- QUAK: 5 TeV
- LDA: sin señal

## Black Box 3
Las resonancias detectadas:
- PCA: una resonancia que decae a hadrones y partículas invisibles
- LDA: 5.6-6.4 TeV
- QUAK: 5-5.5 TeV
- VRNN: sin señal

La resonancia de 4.2 TeV y los dos modos de decaimiento no fueron detectados por ningún algoritmo.

# Conceptos útiles
- **Espacio latente**: Es una representación de datos comprimidos en los que puntos similares están juntos en un espacio. El espacio latente es útil para aprender características de los datos y hallar representaciones más simples para su análisis. [[1]](https://towardsdatascience.com/understanding-latent-space-in-machine-learning-de5a7c687d8d)
- **Modelo generativo**: Es una clase de modelos para aprendizaje supervisado donde, dados unos datos para entrenamiento, el objetivo es generar nuevas muestras de la misma distribución. Los modelos generativos modelan la distribución de clases individuales.[[2]](https://towardsdatascience.com/generative-deep-learning-lets-seek-how-ai-extending-not-replacing-creative-process-fded15b0561b) 
  En comparación con un modelo discriminativo [[3]](https://en.wikipedia.org/wiki/Generative_model):
  - Un modelo **discriminativo** modela la probabilidad condicional en el objetivo Y dada una observación x (P(Y|X=x))
  - Un modelo **generativo** modela la probabilidad condicional de un observable X, dado un objetivo y (P(X|Y=y))
- **Autoencoder**: Un autoencoder acepta entradas, las comprime y recrea las entradas originales.[[4]](https://jamesmccaffrey.wordpress.com/2018/07/03/the-difference-between-an-autoencoder-and-a-variational-autoencoder/)  
  Los usos principales de un autoencoder son:
  - Comprimir datos a dos (o tres) dimensiones para que puedan ser graficados. 
  - Comprimir y descomprimir imágenes y documentos, lo que remueve ruido de los datos.
- **Autoencoder variacional**: Un autoencoder variacional asume que los datos de entrada tienen algún tipo de distribución de probabilidad subyacente (como una Gaussiana) e intenta hallar los parametros de la distribución. El uso principal de un autoencoder variacional es generar nuevos datos que se relacionen a la fuente original de datos.[[4]](https://jamesmccaffrey.wordpress.com/2018/07/03/the-difference-between-an-autoencoder-and-a-variational-autoencoder/)
- **Flujo normalizante**: Los flujos normalizantes son modelos generativos que producen distribuciones manejables donde la evaluación de la muestra y de la densidad pueden ser eficientes y exactas. Aprenden un mapeo biyectivo entre la distribución de los datos y una Gaussiana multivariada.[[5]](https://arxiv.org/pdf/1908.09257.pdf)   
  El nombre se puede interpretar [[6]](https://deepgenerativemodels.github.io/notes/flow/):
  - Flujo: significa que las transformaciones invertibles se pueden componer entre si para crear transformaciones invertibles más complejas.
  - Normalizante: significa que el cambio de variables da una densidad normalizada después de aplicar una transformación invertible.
- **Masked Autoregressive Flow (MAF)**: Consiste en construir una "pila" de modelos autoregresivos, cada uno modelando un número aleatorio del siguiente modelo en la pila, obteniendo un tipo de flujo normalizante apropiado para estimación de densidad. [[7]](https://arxiv.org/pdf/1705.07057.pdf),[[8]](https://arxiv.org/pdf/1705.07057.pdf)
- **Red adversaria generativa**: Estas redes tienen como tarea la discriminación entre muestras reales y generadas. O, se podria decir, una tarea de no-discriminación ya que se quiere que la discriminiación falle lo más posible. En una arquitectura GAN se tiene [[9]](https://towardsdatascience.com/understanding-generative-adversarial-networks-gans-cd6e4651a29),[[10]](https://youtu.be/6v7lJHFaZZ4):
  - Un discriminador, que toma muestras de los datos realeas y generados e intenta clasificarlos lo mejor posible
  - Un generador que está entrenado para engañar al discriminador lo mejor posible.
- **Perceptron multicapa** (MLP): es un tipo de red neuronal feedfoward (ANN)
- **Gaussian Iterative Slicing (GIS)**: funciona pareando iterativamente la distribución marginalizada en 1D de los datos a una Gaussiana.[[11]](https://arxiv.org/pdf/2012.11638.pdf)
- **Latent Dirichlet Allocation** (LDA): Es un modelo estadístico generativo que permite que conjuntos de observaciones sean explicados por grupos no observados, explicando por qué algunas partes de los datos son similares.  
  Por ejemplo, si las observaciones son palabras recopiladas en documentos, postula que cada documento es una mezcla de una pequeño número de tópicos y que la presencia de cada palabra es atribuible a alguno de los tópicos del documento. LDA es un ejemplo de un modelo de tópico. [[12]](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation)
- **Deep neural networks using Classification for Tuning and Reweighting**: (DCTR, pronounced “doctor”) es una técnica para [[13]](https://github.com/bnachman/DCTR)
  - Repesar un conjunto de datos en otro utilizando toda la información del espacio de fase (asumiendo que tienen soporte en el mismo dominio)
  - Si uno de los conjuntos de datos fue generado con Monte Carlo, DCTR puede inferir los parámetros óptimos de MC para reproducir el conjunto de datos (típicamente datos experimentales). Esto se conoce como MC Tuning.
- **Long Short-Term Memory**: es un tipo de red neuronal recurrente capaz de aprender ordenes de dependencia en problemas de predicción de secuencia. Este es un comportamiento requerido en el dominio de problemas complejos como traducción de máquinas, reconocimiento de voz, entre otros. [[14]](https://machinelearningmastery.com/gentle-introduction-long-short-term-memory-networks-experts/)