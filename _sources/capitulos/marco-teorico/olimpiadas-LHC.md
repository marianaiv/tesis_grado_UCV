(lhco)=
# El uso del aprendizaje automático y las Olimpiadas LHC 2020
Hasta ahora la búsqueda de nueva física no ha sido exitosa, pero se mejora constantemente. Sin embargo, es evidente que se requiere perfeccionar las herramientas de análisis para que podamos aprovechar la gran cantidad y complejidad de los datos.

Con el fin de mejorar el uso de estas herramientas para análisis de datos, se crearon las olimpiadas LHC (LHCO). Para esta competencia, se simulan conjuntos de datos con eventos de nueva física que podrían observarse en el acelerador, con el objetivo de que los participantes interpreten los datos en términos de modelos de física BSM.

> "La idea principal es que, si no lo puedes hacer para el caso simulado, es mucho menos probable que lo puedas hacer para el caso real. 
> Hace que las personas aprendan a pensar de manera diferente y aborden el problema de la forma en que habría que abordarlo" 
> 
> — Gordy Kane, Universidad de Michigan. Organizador de las LHCO 2006{cite}`lhco_2006`.

Las olimpiadas de 2020 estuvieron enfocadas en el desarrollo técnicas de aprendizaje automático para la búsqueda de partículas resonantes de BSM. 

El desarrollo de estas herramientas para su uso en HEP se ha visto limitado porque los datos relacionados a colisiones *pp* no se encuentran públicamente disponibles y son muy diferentes a los datos que se utilizan comúnmente para estudiar estos métodos. Sin embargo, es de interés el desarrollo de métodos de aprendizaje automático en HEP, puesto que poseen un gran potencial para ampliar la búsqueda de nueva física, permitiendo una aproximación más general al problema, como las búsquedas libres de modelo. 

En las LHCO 2020, se plantean eventos BSM de una partícula resonante con un ancho de decaimiento pequeño y que tenga como producto eventos de múltiples jets. Un ejemplo de esta topología se muestra en la {numref}`lhco-topologia`.

```{figure} ./../../figuras/lhco-topologia.png
---
width: 400px
name: lhco-topologia
---
Un tipo de topología que se puede encontrar en los datos de las LHCO 2020. Evento dijet por el decaimiento de una partícula de nueva física en dos partículas de nueva física que decaen a jets {cite}`lhco_2020`.
```
Para las LHCO 2020 se desarrollaron múltiples conjuntos de datos: una simulación de Monte Carlo del fondo, sin eventos de nueva física o señal, un conjunto de datos con señal para investigación y desarrollo (conjunto R&D) y tres cajas negras que pueden o no contener señal. Las cajas negras son los conjuntos de datos proporcionado para probar los modelos previamente desarrollados y su contenido es desconocido para los participantes. Para este trabajo se utilizó el conjunto R&D y la caja negra 1. Detalles acerca de estos conjuntos de datos se discuten en la {numref}`datos`.

Los participantes reportaron al menos alguno de los siguientes resultados:
- Un valor p asociado a la falta de nuevas partículas en el conjunto de datos.
- Una descripción completa de la nueva física: masas y modos de decaimiento de las nuevas partículas.
- Número de eventos de señal en el conjunto de datos (antes de cualquier criterio de selección).

Participaron 18 modelos que fueron agrupados dependiendo del método utilizado: 9 modelos no supervisados, 5 modelos débilmente supervisados y 4 modelos semi-supervisados o supervisados. Una descripción detallada de los modelos a utilizar en este trabajo se encuentra en la {numref}`alglhco`. Los resultados individuales de cada modelo, así como mayor información acerca de cada aspecto de la competencia, se encuentra en {cite}`Kasieczka_2021`.