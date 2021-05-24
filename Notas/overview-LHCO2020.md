---
Tags: Tesis, Notas
---
Overview: Olimpiadas LHC 2020
===

Interpretar los datos producidos por el LHC no es una tarea fácil. Los protones son estructuras complejas, lo que hace difícil interpretar exactamente que sucede en el nivel fundamental de cada colisión. 

Para mejorar la hábilidad de decifrar la información correctamente, se crearon las Olimpiadas LHC.

En las olimpiadas se simulan tres conjuntos de datos que podrían generarse en el acelerador. Los participantes deben interpretar estos datos, buscando partículas y evidencia de teorías que no han sido presenciados o confirmados.

> "La idea principal es que si no lo puedes hacer para el caso simulado, es mucho menos probable que lo puedas hacer para el caso real. 
> Hace que las personas aprendan a pensar de manera diferente y aborden el problema de la forma en que habría que abordarlo" 
> 
> -Gordy Kane

La busqueda de nueva física es una de las mayores partes del programa de investigación en el LHC. Estas busquedas están mejorando constantemente, pero se ha hecho evidente que se requiere de un paradigma complementario para explorar la complejidad de los datos.

Una posible explicación de por qué aún no hemos descubierto nueva física es la dependencia del modelo en las busquedas actuales. Se utilizan algunas busquedas independientes del modelo, como bump hunt, pero estas no son particularmente sensibles porque no incluyen otras propiedades más allá de características resonantes.

Machine learning ofrece un gran potencial para mejorar y extender la busqueda independiente del modelo, específicamente el área de detección de anomalías. Por esto, es necesario tener conjuntos de datos públicos para desarollar y calificar estos nuevos enfoques, ya que los datos en HEP son diferentes a los que proporcionan imágenes naturales u otro tipo de datos comúnes utilizados al desarrollar herramientas para este fin.

Siguiendo esta idea, se desarrollaron el desafío y el conjunto de datos para las Olimpiadas LHC 2020.

Las olimpiadas de 2020 tuvieron un estado final enfocado en eventos genéricos de multiples jets, con un espacio de fase observable y espacio de parámetros potencialmente de más allá del Modelo Estándar(BSM) grande: todos los hadrones pueden ser utilizados para aprender.

Un ejemplo de topología para este desafío:

![Dijet event](https://i.imgur.com/deLO09t.jpg)

# Datos
Proporcionaron dos tipos de archivos:
- **Simulación de Monte Carlo del fondo**: una muestra simulada que no tiene señal. 
- **Datos**: Tres cajas negras que pueden contener señal.

Tanto la simulación como los datos tienen al menos un jet anti-kT R = 1.0 con:
- Pseudorapidez $|\eta|<2.5$
- Momento transversal pT > 1.2 TeV

Para cada evento proporcionaron una lista de todos los hadrones (pT, $\eta$, $\phi$, pT, $\eta$, $\phi$) con relleno de ceros hasta 700 hadrones.

Especifícamente:

## Conjunto de datos R&D
Consiste en un millon de eventos del SM compuestos por dos jets producidos por la interacción fuerte, referidos como eventos dijets de cromodinámica cuántica (QCD) y 100,000 eventos $Z'\rightarrow XY$ con $X\rightarrow q\bar{q}$ y $Y\rightarrow q\bar{q}$. Las masas de nuevas partículas BSM Z', X y Y son 3.5 TeV, 500 GeV y 100 GeV, respectivamente. 

Los eventos se produjeron usando Pythia y Delphes con la configuración por defecto.

![Feynman diagram for signals of R&D dataset and Black Box 1](https://i.imgur.com/7IKoJQi.png) <figcaption>**Figura 1**: Diagramas de Feynman para la señal en el conjunto de datos R&D y la caja negra 1.</figcaption>

## Caja Negra 1

Esta caja contiene la misma topología que el conjunto R&D pero con masas para Z', X y Y de 3.823 TeV, 732 GeV y 378 GeV, respectivamente. Un total de 834 eventos de señal fueron incluidos (del total de 1M eventos).

Los eventos de fondo en la Caja Negra 1 son diferentes a los de el conjunto de datos R&D. Se utilizaron los mismos generadores, algunas configuraciones por defecto de Pythia y Delphes fueron cambiadas.

## Caja Negra 2

Esta muestra contiene 1M de eventos de fondo. 

El fondo se produjo usando Herwig++ en vez de Pythia, y se utilizo una carta detectora diferente que la utilizada en la caja negra 1, pero modificaciones similares sobre el conjunto R&D.

## Caja Negra 3

Consiste en una resonancia pesada (graviton KK) con masa 4.2 TeV que tiene dos modos de decaimiento diferentes. El primer modo deca a dijets(gluones) y el segundo a una resonancia neutral más ligera R (el radion IR) de masa 2.217 TeV mas un gluon, con $R\rightarrow gg$. 1200 eventos dijet y 2000 eventos trijet fueron incluidos, con fondo de QCD. 

El fondo fue simulado con una configuración modificada de  Pythia y Delphes.

![Feynman diagrams for black box 3](https://i.imgur.com/E2IXyBi.png)<figcaption>**Figura 2**: Diagramas de Feynman para la señal en la caja negra 3.</figcaption>


# Requisitos

Los participantes debieron reporta al menos alguno de los siguientes puntos:
- Un valor p asociado al conjunto de datos no teniendo nuevas partículas.
- Una descripción completa de la nueva física. Por ejemplo: masas y modos de decaimiento de las nuevas partículas (con incertidumbre)
- Cuantos eventos de señal (+incertidumbre) hay en el conjunto de datos (antes de cualquier criterio de selección)

# Participantes

Los participantes se agruparon en tres categorías generales:
- No supervisado (NS): No proveen información etiquetada al algoritmo de machine learning(ML) durante el entrenamiento. 
- Débilmente Supervisado (DS): Proveen etiquetas "ruidosas" (posiblemente sin señal/posiblemente señal)
- (Semi-)Supervisado (SS): Utilizan simulación de señal para construir sensibilidad. 

Un **resumen de los participantes** con los métodos y los análisis se encuentra en la siguiente tabla. La columna de resultados hace referencia a los datos con la que los participantes hicieron el análisis y si fue cegado (c ) o no cegado (nc):

| Nombre | Método | Resultado|
|--------|------|----------- |
|   VRNN |    NS| BB2,3(c ) y BB1(nc)|
|   ANODE|    NS|     R&D(nc)|
| BuHuLaSpa|  NS| BB2,3(c ) y BB1(nc) |
|  GAN-AE|    NS| BB2,3(c ) y BB1(nc) |
|     GIS|    NS|    BB1(c )|
|     LDA|    NS|  BB1-3(c )|
|     PGAE|    NS| BB1,2(c )|
| Reg. Likelihoods| NS| R&D(nc)|
| UCluster|   NS|  BB2,3(c )|
|   CWoLa|    DS| BB1,2(nc)|
|CWoLa AE Compare|D/NS| R&D(nc)|
|Tag N' Train|DS| BB1-3(c )|
|   SALAD|    DS| R&D(nc)|
|SA-CWoLa|    DS| R&D(nc)|
|Deep Ensemble|SS|   BB1(c )|
| Factorized Topics| SS| R&D(nc)|
|    QUAK|    SS| BB2,3(c  ) y BB1(nc)|
|    LSTM|    SS| BB1-3(c ) |