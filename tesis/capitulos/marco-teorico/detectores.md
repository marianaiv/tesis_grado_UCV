(det)=
# Detectores de partículas
En los aceleradores de partículas, como el LHC, se registran datos sobre eventos de colisión de haces de iones o protones a altas energías. Los datos registrados representan estado final de la colisión, ya que información sobre la colisión no se puede medir directamente. Estos se obtienen utilizando detectores, que detectan el paso de partículas y son capaces de medir su localización, momento y/o energía. En el LHC hay cuatro detectores especializados, cada uno con un propósito ({numref}`ms-lhc`). Sin embargo, todos los detectores en física de alta energías (HEP, por sus siglas en inglés) tienen un principio subyacente similar, independiente de las partículas involucradas en las colisiones. Los detectores se pueden categorizar en dos tipos principales: detectores de trazas, que revelan la trayectoria de partículas cargadas eléctricamente, y lo calorímetros, que absorben y miden la energía depositada por la partícula. A continuación, discutiremos brevemente los principios físicos de un detector de propósito general, utilizando como referencia {cite}`10.1088/2053-2563/ab1be6ch3,Vasquez_2019`.

(det-tr)=
## Detector de trazas
El detector de trazas tiene como objetivo medir la trayectoria de las partículas cargadas al emerger del punto de interacción (IP, por sus siglas en inglés). Usualmente, es el detector más cercano a la línea de haces (como se muestra en la {numref}`det-atlas`) porque no destruye la partícula para realizar la medición.

```{figure} ./../../figuras/det-atlas.png
---
width: 600px
name: det-atlas
---
Diagrama esquemático de un detector de propósito general, mostrando cómo diferentes subdetectores detectan diferentes partículas{cite}`Pequenao:1505342`.
```
Los detectores de traza usualmente están hechos de varias capas de píxeles y cintas, normalmente de silicio, y contienen un campo magnético solenoidal. Las trayectorias de las partículas cargadas se doblan debido al campo magnético y su radio de curvatura se utiliza para calcular el momento: cuanto mayor es la energía cinética, menor es la curvatura. Una partícula cargada pasa por varias capas de los detectores de trazas y se registra la posición en cada capa. Cada punto se conoce como *hit*, y la unión de estos hits es la trayectoria de la partícula. Las trayectorias se extrapolan al punto de origen y, mediante el uso de varias trayectorias, se reconstruye el vértice de colisión. 

Las partículas cargadas más comunes en los detectores son electrones, muones y piones. De los electrones se miden trayectorias curvas cortas, mientras que de los muones se miden trayectorias largas, puesto que son más pesados. Sin embargo, se requieren medidas tomadas por múltiples detectores para poder identificar las partículas.

(det-cal)=
## Calorímetros
Los calorímetros tienen como objetivo medir la energía de la partícula entrante, sea esta cargada o neutra. Para esto, absorben la energía de la partícula en el volumen del detector. Las partículas incidentes interactúan con el material del calorímetro, generando una cascada que genera diferentes depósitos de energía en las capas del detector. La señal final es proporcional a la energía total depositada por la partícula. Existen dos tipos de calorímetros: electromagnéticos y hadrónicos.

En los calorímetros electromagnéticos la pérdida de energía resulta de procesos debido a la interacción de la partícula cargada con la materia. Los procesos principales son producción de pares y Bremsstrahlung. En los calorímetros hadrónicos la energía se pierde debido a la interacción inelástica con los núcleos del material que conforma al calorímetro. Los calorímetros detienen a la mayoría de las partículas, exceptuando los muones y los neutrinos.

El calorímetro electromagnético se coloca luego del detector de trazas, y antes del calorímetro hadrónico, ya que no absorbe la energía de los hadrones. Esto se observa en la {numref}`det-atlas`.

(det-muon)=
## Espectrómetro de muones
Los muones tienen características similares a los electrones, excepto que son significativamente más pesados y no interactúan con los materiales de los calorímetros. Un espectrómetro de muones consta de un detector sensible a la posición que registra las trayectorias de partículas cargadas y un campo magnético para que la carga y el momento puedan deducirse de la curvatura de la trayectoria, al igual que un detector de trazas. La identificación de muones a menudo se basa en la gran cantidad de material absorbente frente al detector de muones, que solo permite el paso de muones (y neutrinos){cite}`Hebbeker2012`.