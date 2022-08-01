(lhco)=
# El uso del aprendizaje automático y las Olimpiadas LHC 2020
Hasta ahora la búsqueda de nueva física no ha sido exitosa, pero se mejora constantemente. Sin embargo, es evidente que se requiere perfeccionar las herramientas de análisis para que podamos aprovechar la gran cantidad y complejidad de los datos.

Con el fin de mejorar el uso de estas herramientas para análisis de datos, se crearon las olimpiadas LHC (LHCO). Para esta competencia, se simulan conjuntos de datos con eventos de nueva física que podrían observarse en el acelerador, con el objetivo de que los grupos participantes interpreten los datos en términos de modelos de física BSM.

> "La idea principal es que, si no lo puedes hacer para el caso simulado, es mucho menos probable que lo puedas hacer para el caso real. Hace que las personas aprendan a pensar de manera diferente y aborden el problema de la forma en que habría que abordarlo" 
> 
> — Gordy Kane, Universidad de Michigan. Organizador de las LHCO 2006{cite}`lhco_2006`.

Las [olimpiadas del LHC 2020](https://lhco2020.github.io/homepage/){cite}`Kasieczka_2021` estuvieron enfocadas en el desarrollo de técnicas de detección de anomalías para la búsqueda de partículas resonantes de BSM con un ancho de decaimiento pequeño que resulten en eventos de múltiples jets, topología de interés en la búsqueda de nuevas partículas debido a la alta proporción de eventos que resultan en múltiples jets en el LHC. Un ejemplo de esta topología se muestra en la {numref}`lhco-topologia`. El objetivo es mejorar las técnicas de aprendizaje automático para capturar señales complejas y poco comunes que resulten en jets, puesto que son herramientas que poseen un gran potencial para ampliar la búsqueda de nueva física, permitiendo una aproximación más general al problema, como las búsquedas libres de modelo. Este evento se realizó de manera abierta, con el objetivo de que cualquier grupo de investigadores interesado en el estudio de estas herramientas para su aplicación en HEP pudiese participar, ampliando así la comunidad involucrada en el perfeccionamiento de estas herramientas.

```{figure} ./../../figuras/lhco-topologia.png
---
width: 500px
name: lhco-topologia
---
Un tipo de topología que se puede encontrar en los datos de las LHCO 2020. Evento dijet por el decaimiento de una partícula de nueva física en dos partículas de nueva física que decaen a jets {cite}`lhco_2020`.
```

El desarrollo de estas herramientas para su uso en HEP se ha visto limitado porque los datos relacionados a colisiones *pp* no se encuentran públicamente disponibles y son muy diferentes a los datos que se utilizan comúnmente para estudiar los métodos de aprendizaje automático. Las olimpiadas proporcionan conjuntos de datos de colisiones que resultan en múltiples jets con el fin de permitir la investigación de estas herramientas de forma abierta. Particularmente, para las LHCO 2020 se proporcionaron diferentes conjuntos de datos: una simulación de Monte Carlo del fondo, sin eventos de nueva física o señal, un conjunto de datos con señal para investigación y desarrollo (conjunto R&D) y tres cajas negras (BB1, BB2 y BB3) que pueden o no contener señal. Las cajas negras son los conjuntos de datos proporcionado para probar los modelos previamente desarrollados y su contenido es desconocido para los grupos participantes. Para este trabajo se utilizó el conjunto R&D y la caja negra 1 (BB1, por sus siglas en inglés). Detalles acerca de estos conjuntos de datos se discuten en la {numref}`datos`.

En las LHCO 2020, los grupos participantes desarrollaron modelos de detección de anomalías para buscar nuevas partículas en los conjuntos de datos simulados. Para participar, reportaron al menos alguno de los siguientes valores para uno o varios conjuntos:
- Un valor p asociado a la falta de nuevas partículas en el conjunto de datos: este valor es una medida estadística que indica la probabilidad de haber obtenido el resultado asumiendo que el conjunto no tiene partículas nuevas. Está asociado a la significancia, que cuantifica que tan probable es que el resultado halla sido obtenido por azar.
- Descripción de la nueva física: en caso de hallar nueva física en el conjunto de datos, reportar los valores de las masas de las partículas nuevas y los modos de decaimiento.
- El número de eventos de señal en el conjunto de datos, antes de cualquier criterio de selección.

Participaron 18 modelos, que fueron agrupados dependiendo del método utilizado: 9 modelos no supervisados, 5 modelos débilmente supervisados y 4 modelos semi-supervisados o supervisados. Una descripción detallada de los modelos a utilizar en este trabajo se encuentra en la {numref}`alglhco`. Los resultados individuales de cada modelo, así como mayor información acerca de cada aspecto de la competencia, se encuentra en {cite}`Kasieczka_2021`.