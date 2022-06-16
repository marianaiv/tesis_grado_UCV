(bsm)=
# Más allá del modelo estándar
A pesar de que en los últimos 40 años se han verificado exitosamente múltiples predicciones hechas a partir del modelo estándar{cite}`Kobayashi_2021,NAP6045`, es evidente que no es una teoría final debido a que no explica varios fenómenos observados experimentalmente. A partir de estas limitaciones, se han planteado múltiples teorías que intentan responder las preguntas para las que el modelo estándar no tiene explicación. Estás teorías se conocen como teorías *más allá del modelo estándar* (BSM) y su verificación/refutación es uno de los objetivos del programa del LHC.

El LHC{cite}`Evans:2008zzb` es el acelerador de partícula más grande y de mayor energía del mundo, siendo el experimento de colisionador principal en física de altas energías. Se encuentra ubicado en el laboratorio europeo de física de partículas CERN en la frontera Franco-Suiza, cerca de Geneva en Suiza. Consiste en un anillo de 27 kilometros de circunferencia conformado por imanes superconductores con estructuras aceleradoras que aumentan la energía de las partículas a lo largo del camino. Fue diseñado para acelerar protones o iones a altas energías y producir una alta tasa de colisiones, y es utilizado principalmente para probar predicciones teóricas en física de partículas, especialmente aquellas asociadas al modelo estándar.

En esta sección se describirán algunas de las limitaciones que presenta el modelo estándar, teorías BSM que intentan resolver estas limitaciones y la búsqueda de nueva física en eventos de dos jets, la topología a estudiar en este trabajo.
(bsm-limitaciones)=
## Limitaciones del modelo estándar
Las limitaciones del modelo estándar se pueden separar en *fenomenológicas* y *teóricas*. A continuación se describiran algunas de estas siguiendo {cite}`BSMlectures`.
 
Las *limitaciones fenomenológicas* indican inconsistencias de la teoría con observaciones experimentales o observaciones experimentales que el modelo estándar no puede explicar. Algunas de estas son:

- **Asimetría materia-antemateria**: De acuerdo al modelo estándar, en el universo temprano se debio crear igual cantidad de materia que de antimateria. Sin embargo, se observa mucha mas matería que antimateria y la teoría no explica esta asimetría.
- **Masa de los neutrinos**: no se conoce el mecanismo mediante el cual los neutrinos adquieren masa y no se explica por qué la brecha entre la masa de los neutrinos y cualquier otro fermión cargado es mucho más grande que entre cualquier otro par de fermiones{cite}`deGouvea_2009` ({numref}`bsm-neutrinos`)
- **Materia oscura y energía oscura**: la existencia de la materia oscura se ha inferido por los efectos gravitacionales que tiene en la materia visible{cite}`Ellis2012-rh` y la energía oscura se utiliza para explicar la tasa de expansión del universo y su aceleración{cite}`1607.00330`. La naturaleza de ambas no está incluida en el modelo estándar.

```{figure} ./../../figuras/bsm-neutrinos.png
---
width: 300px
name: bsm-neutrinos
---
Masa de los fermiones del modelo estándar. Para la masa de los neutrinos, se asumió la jerarquía usual de masas entre generaciones, con un límite superior de  $m_i$ < 1 eV {cite}`deGouvea_2009`.
```
Por otra parte, las *limitaciones teóricas* hacen referencia a predicciones no observadas o valores y parámetros para los que la teoría no tiene explicación. Entre estas se encuentran:
- **Descripción cuántica de la gravedad**: la fuerza gravitatoria no está incluida en el modelo estándar y no se ha logrado construir una teoría cuántica de campos que reconcilie la gravedad con la física de partículas debido a que la relatividad general no es renormalizable.
- **Origen de las masas/mezclas**: el modelo estándar no explica el origen del mecanismo de Brout–Englert–Higgs, solo se sabe que es necesario para poder coincidir con las observaciones experimentales. Además, la masa de los fermiones ({numref}`bsm-neutrinos`) y los ángulos de mezcla de los quarks parecen presentar un patrón. Estos sólo representan parámetros en el modelo y no se entiende por qué presentan una estructura.
- **Problema CP fuerte**: En la QDC se predice violación *CP*{cite}`Creutz_2018,Mannel:2007zz`, pero esto no se ha observado experimentalmente.
- **Problema de jerarquía**: Teóricamente, la masa del bosón de Higgs debería ser del orden de la escala de Planck{cite}`Smith_2019`. Sin embargo, el valor experimentar hallado es $10^19$ órdenes de magnitud menor. Para lograr teóricamente el valor experimental, se requiere hacer un ajuste fino que no se considera natural y representa problemas con respecto a la universalidad de la teoría.
(bsm-nuevafisica)=
## Búsqueda de nueva física
La búsqueda de una teoría del todo, que relacione los fenómenos físicos conocidos y prediga el resultado de cualquier experimento, es un tema en curso en la física, como se puede observar en la {numref}`bsm-unificacion`.

```{figure} ./../../figuras/bsm-unificacion.png
---
width: 900px
name: bsm-unificacion
---
Secuencia histórica de la unificación de leyes físicas {cite}`Elert_1998`. 
```
Se cree que el modelo estándar es una aproximación a bajas energías que unifica las cuatro interacciones fundamentales. Hasta ahora, no se ha propuesto una teoría que logre este objetivo. Sin embargo, existen teorías que intentan explicar los fenómenos que el modelo estándar no explica.

Por ejemplo, el modelo de **supersimetría** (SUSY), específicamente la mínima extensión supersimétrica del modelo estándar (MSSM), duplica el espectro de masa al agregar partículas supersimétricas, o spartículas, como se ilustra en la {numref}`bsm-sparticulas`. Se plantea con la motivación teórica de eliminar el problema de jerarquía, unificar las fuerzas fundamentales y ofrece un candidato para la materia oscura {cite}`Virdee2016-dd`. 

```{figure} ./../../figuras/bsm-sparticulas.png
---
width: 700px
name: bsm-sparticulas
---
Diagrama ilustrativo de las partículas supersimétricas planteadas por SUSY {cite}`york`.
```
También se han propuesto modelos con **dimensiones espaciales adicionales**, como Kaluza y Klein{cite}`KALUZA_2018,Klein:1926tv`, que propone una quinta dimensión, unificando la relatividad general y el electromagnetismo. Desde entonces, se han estudiado varios modelos que plantean nuevas dimensiones{cite}`P_rez_Lorenzana_2005`.

Entre estos modelos se encuentra la **teoría de cuerdas**, que intenta reconciliar la relatividad general con el modelo estándar{cite}`Wray_2011`. Esta teoría solo funciona con dimensiones adicionales e incluye partículas supersimétricas que podrían ser realmente masivas.

Sin embargo, las partículas supersimétricas no han sido observadas{cite}`ATLAS_SUSY`, ninguno de los experimentos diseñados para detectar materia oscura ha detectado la partícula ligera que predice SUSY, y no hay evidencia para la unificación de las fuerzas ni para las dimensiones adicionales.
(bsm-dijes)=
## Eventos dijet
La búsqueda de nuevas partículas es fundamental en la búsqueda de física BSM. Los modelos mencionados anteriormente y muchos otros incluyen en su formulación nuevas partículas que permiten explicar alguna de las limitaciones del modelo estándar. Históricamente, uno de los métodos utilizados para descubrir nuevas partículas es la búsqueda de estructuras de resonancia en espectros de masas invariantes de los productos de desintegración de la partícula. 

A diferencia de las búsquedas dirigidas a estados finales más complejos, para una topología específica, las búsquedas de resonancia de dos cuerpos solo son sensibles a dos parámetros: la masa de la nueva partícula y la sección transversal de producción. Como resultado, estas búsquedas establecen poderosas restricciones en una variedad de modelos específicos de física BSM{cite}`Kim_2020`. Existen múltiples estados finales de dos cuerpos que se pueden considerar para la búsqueda de física BSM, pero en este trabajo nos enfocamos en el estado final de dos jets o dijet.

En el LHC, una alta fracción de los eventos de colisión resultan en la formación de jets. Varios modelos de física BSM predicen la existencia de nuevas partículas masivas que decaen a quarks o gluones, o que decaen hadrónicamente formando jets{cite}`Harris_1996`. Además, los jets son la firma experimental de los quarks y gluones, y son productos en el decaimiento hadrónico de los bosones *W/Z*, y el estado final del decaimiento a quarks del bosón de Higgs. Así, su estudio no está motivado únicamente por la búsqueda de nueva física, sino también para ganar una mejor comprensión de la QCD.

La búsqueda de resonancias dijet tienen una larga historia en los colisionadores de hadrones que data desde 1980. Más recientemente, desde 2015, por los experimentos ATLAS y CMS en el CERN en colisiones *pp* a energías de centro de masa de 13 TeV{cite}`Sirunyan_2020,Aaboud_2017,Aad_2016`. Todas las búsquedas realizadas hasta ahora no han encontrado evidencia de nuevas resonancias. Sin embargo, con el aumento de energía de centro de masa del LHC, se vuelven accesibles mayores masas. Además, con el aumento en el tamaño del conjunto de datos, también aumenta la sensibilidad a resonancias con secciones transversales pequeñas. La energía del centro de masa y el tamaño del conjunto de datos son los factores clave que determinan la sensibilidad de la búsqueda, y ambos han aumentado significativamente con el tiempo{cite}`Beresford:2642397`.

En {cite}`Kim_2020` se pueden hallar múltiples modelos de partículas de nueva física que decaen a dos cuerpos, y específicamente, que decaen a dos jets, además de información sobre el estado actual de su búsqueda. Entre estos, se encuentra el modelo utilizado para generar los datos que se usan en este trabajo. Se trata de un modelo de la forma $A\rightarrow BC$ donde $A$, $B$ y $C$ son partículas BSM, y $B$ y $C$ decaen a partículas similares del modelo estándar. En los datos usados en este trabajo, $B$ y $C$ decaen a quarks y $A$ es un bosón Z pesado{cite}`Langacker_2009`.