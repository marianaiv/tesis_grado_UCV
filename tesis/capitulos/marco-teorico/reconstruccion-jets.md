(jets)=
# Reconstrucción de jets
Como se explicó en la {numref}`qcd-jets`, la formación de un jet resulta en múltiples partículas de color neutro. Las características de estas partículas del estado final es lo que se mide en los detectores, es decir, es la información que se obtiene de los jets. Por lo tanto, para analizar los eventos de jets es necesario reconstruirlos. En esta sección se explicarán los algoritmos más conocidos para reconstruirlos y algunas de las variables que se utilizan para caracterizarlos. 

(jets-agrupamiento)=
## Agrupamiento de jets
La definición de un jet no es única. De hecho, la existencia de un jet es dependiente de la regla matemática que lo define. Esta regla matemática agrupa los constituyentes del jet de acuerdo a propiedades cinemáticas y se conoce como *algoritmo de agrupamiento de jets*. A continuación, se explicará acerca de estos algoritmos siguiendo{cite}`10.1088/2053-2563/ab1be6ch3,Marshall:1308447,Huth:1990mi`.

De manera general, un algoritmo de agrupamiento hace un mapeo del conjunto de hadrones del estado final con cuadrimomento $\{p_1^{had},p_2^{had},\dots,p_n^{had}\}$ a un conjunto de jets con cuadrimomento $\{p_1^{jet},p_2^{jet},\dots,p_m^{jet}\}$, donde $m<n$. El momento de cada jet es la suma de los momentos de las partículas que lo constituyen y la suma vectorial define el eje del jet.

Todos los algoritmos agrupan objetos cercanos en $\phi$, el ángulo azimutal alrededor del eje del haz, y la pseudorapidez $\eta$, definida como: 

$$
    \eta\equiv -\ln\left[\tan\left(\frac{\theta}{2}\right)\right]
$$ (jets-eta)

donde $\theta$ es el ángulo polar entre los constituyentes y el haz de protones entrantes. Los valores de pseudorapidez indican directamente a qué distancia del centro del detector se produce una partícula y varían de menos a más infinito dentro de la geometría del detector. Este sistema de coordenadas del detector se muestra en la {numref}`jets-coordenadas`, junto con la conversión de ángulo polar a pseudorapidez.

```{figure} ./../../figuras/jets-coordenadas.png
---
width: 600px
name: jets-coordenadas
---
Ilustración del sistema de coordenadas utilizado en los experimentos del LHC (izquierda) y una conversión entre el ángulo polar y la pseudorapidez (derecha). El eje z se encuentra a lo largo de la dirección del haz de protones entrante, y el ángulo azimutal $\phi$ se define con respecto al plano x–y, como es usual. La pseudorapidez $\eta$ se define para aprovechar la simetría cilíndrica, y aumenta de valor a medida que nos alejamos del centro del detector{cite}`Marshall:1308447`.
```
La distancia angular entre dos objetos en el detector está dada en función de $\eta$ y $\phi$,

$$
    \Delta R = \sqrt{\Delta\eta^2+\Delta\phi^2}.
$$ (delta-R)

Los jets se pueden reconstruir a partir de objetos experimentales, como depósitos de energía en calorímetros y trayectorias de partículas cargadas ({numref}`jets-types`), o de objetos teóricos, como partones y hadrones obtenidos mediante simulaciones.

```{figure} ./../../figuras/jets-types.png
---
width: 600px
name: jets-types
---
Esquema que muestra los diferentes tipos de jet. Se producen partículas de color por la dispersión fuerte, creando partículas de color neutro en la fragmentación. Estas partículas pueden producir distintas señales en los detectores{cite}`camachotoro:tel-00818796`.
```
Se espera que un algoritmo posea ciertas características:
- Ser robusto con respecto al tipo de datos de entrada.
- Teóricamente, debe ser *colinealmente estable*: la separación de un partón en dos partones colineales no debe cambiar el resultado del agrupamiento del jet ({numref}`jets-colineal`).
- Cumplir con la *estabilidad infrarroja*: la radiación de un gluon suave no debe cambiar el agrupamiento ({numref}`jets-infrarrojo`).
- Baja sensibilidad a los UE y el pileup (PU, por sus siglas en inglés), que son señales remanentes de otras colisiones.
- Fácil de utilizar en cálculos teóricos y análisis experimentales, así como computacionalmente rápidos de ejecutar.

```{figure} ./../../figuras/jets-colineal.png
---
width: 350px
name: jets-colineal
---
Esquema de la estabilidad colineal. La separación de un partón en partones colineales no debe cambiar la configuración de un jet{cite}`10.1088/2053-2563/ab1be6ch3`.
```

```{figure} ./../../figuras/jets-infrarrojo.png
---
width: 350px
name: jets-infrarrojo
---
Esquema de la estabilidad infrarroja. La emisión de un gluon suave entre dos jets no debe resultar en su unión{cite}`10.1088/2053-2563/ab1be6ch3`. 
```
### Tipos de algoritmos
Existen dos tipos principales de algoritmos de agrupamiento: *algoritmos de cono* y *algoritmos de recombinación secuencial*
#### Algoritmos de cono
Los algoritmos de cono asumen que el jet se encuentra en regiones cónicas del espacio $(\eta-\phi)$, por lo que los jets reconstruidos por estos algoritmos tienen bordes circulares. Son de fácil implementación, pero no son colinealmente estables{cite}`Atkin_2015`.

Se puede pensar que su aproximación es de arriba hacia abajo. En general, un algoritmo de cono sigue los pasos a continuación{cite}`Schieferdecker_2009`:

```{prf:algorithm} Algoritmo de cono
:label: jets-algcono

**Inputs** Constituyentes del evento

1. Hallar el constituyente más energético del evento, o semilla.
2. Colocar un cono de radio *R* alrededor de esta semilla y sumar el momento de todas las partículas que constituyen el cono, formando un jet de prueba.
3. Comparar el eje de la semilla con el del jet de prueba:

	1. *Si el eje del del jet de prueba y la semilla coinciden*: El jet de prueba se toma como jet
    2. *De otra forma*: Se repiten los pasos anteriores con el eje del jet de prueba como semilla.
```
Estos pasos se repiten hasta que no haya semillas sobre un umbral de energía escogido.

Ejemplos de algoritmos de cono son: *Midpoint Cone*, utilizado en Tevatron, *Iterative Cone* y *SISCone*{cite}`Salam_2007`.
#### Recombinación secuencial
Los algoritmos de recombinación secuencial asumen que los constituyentes de un jet poseen una pequeña diferencia en el momento transverso. Por esto, las partículas son agrupadas en el espacio de momento, resultando en jets con fluctuaciones en el espacio $(\eta-\phi)${cite}`Atkin_2015`.  

En general, los algoritmos de recombinación secuencial utilizan las siguientes medidas de distancia entre dos constituyentes:

$$
    d_{ij} = min(p_{Ti}^{2p},p_{Tj}^{2p})\times \frac{\Delta R_{ij}^2}{R}
$$ (dist_const)

donde $p_T$ es el momento transverso de las partículas, $\Delta R_{ij} = \sqrt{(\eta_i-\eta_j)^2+(\phi_i-\phi_j)^2}$ es la distancia entre dos constituyentes en el espacio $(\eta-\phi)$, $R$ es el radio final del jet, usualmente entre 0.4-0.7 y $p$ es un parámetro referente al tipo de algoritmo.

También utilizan la distancia entre el eje del haz y el constituyente detectado:

$$
    d_{iB}=p_{Ti}^{2p}
$$ (dist_eje)

Se puede pensar que el funcionamiento de estos algoritmos es de abajo hacia arriba:
```{prf:algorithm} Algoritmo de recombinación secuencial
:label: jets-algsecuencial

**Inputs** Constituyentes del evento

1. Hallar el mínimo en el conjunto $\{d_{ij},d_{iB}\}$:

	1. *Si el mínimo es $d_{ij}$*: los constituyentes *i* y *j* se unen en un solo constituyente *ij*, sumando el cuadri-momento y eliminando *i* y *j*  de la lista de constituyentes.   
    2. *Si el mínimo es $d_{iB}$*: *i* se considera jet y eliminado de la lista de constituyentes.  
```

Los pasos anteriores se repiten hasta que todas las partículas son parte de un jet, con distancias $\Delta R_{ij}$ entre los ejes de los jets mayores a $R$ (agrupamiento inclusivo), o hasta que se obtenga una cantidad específica de jets (agrupamiento exclusivo).

Los algoritmos de recombinación utilizados son:

- ***Kt***{cite}`PhysRevD.48.3160`: para este algoritmo $p=1$. Es sensible a los UE y PU. Este algoritmo es una aproximación inversa del proceso de ramificación de QCD porque preserva la historia de agrupamiento.
- ***Anti-kt***{cite}`Cacciari_2008`: para este algoritmo $p=-1$. Contrario al *kt*, es poco sensible a los UE y el PU. En este algoritmo el agrupamiento no está relacionada a la manera en la que los partones se dividen.
- ***Cambridge/Aachen***{cite}`Dokshitzer_1997`: para este algoritmo $p=0$. Es el mejor para estudiar la subestructura de los jets, pero su implementación es más complicada. También es susceptible a los UE y el PU. 

Los algoritmos de recombinación son los más utilizados en la actualidad desde su implementación en el programa *FastJet*{cite}`FastJet`, un paquete de C++ que proporciona herramientas para agrupar y analizar jets. En este trabajo se agrupan los jets utilizando el algoritmo anti-kt.

(jets-subestructura)=
## Variables de subestructura
La subestructura de un jet puede analizarse para diferenciar si el jet proviene de un gluon, un quark, un bosón que decae hadrónicamente o partículas masivas aún no descubiertas.
 
```{figure} ./../../figuras/jets-diagramajets.png
---
width: 500px
name: jets-diagramajets
---
Representación de jets producto de: quarks y gluones (arriba a la izquierda), quark bottom (arriba en el centro), y topologías de jets impulsados: bosones de alto $p_T$ *W* y *Z* (arriba a la derecha), bosón de Higgs (abajo a la izquierda) y quark top (abajo a la derecha) decayendo a un estado final de quarks{cite}`PhysRevD.102.012010`.
```
Como se observa en la {numref}`jets-diagramajets`, a alto momento transverso, un bosón, un quark top e inclusive una partícula de nueva física que decaiga a dos o más quarks, puede ser reconstruida como un jet único debido a que los productos de decaimiento se encuentran muy cercanos. A continuación se describirán algunas de las variables que se calculan para diferenciar entre jets provenientes de distintas partículas, utilizando como referencia {cite}`10.1088/2053-2563/ab1be6ch8`.
### Masa
La masa es la variable mas evidente para discriminar entre jets provenientes de distintas partículas. La masa de un jet es cercana a la masa de la partícula de la cual se origina, asumiendo que los productos del decaimiento están contenidos en el jet. Está definida como la suma de la masa invariante de todos los constituyentes del jet, calculada a partir del cuadri-momento de cada constituyente. 

La distribución de masa del jet se utiliza para diferenciar jets provenientes de partículas masivas con alto momento transverso, que se caracterizan por una distribución mas angosta y alta, de fondo que cae suavemente, debido a jets ordinarios de quarks y gluones{cite}`PhysRevD.102.012010`. En la {numref}`jets-masa`, se presenta un ejemplo de la distribución de la masa del jet principal de eventos provenientes de quarks y gluones, o fondo, y para una señal de nueva física con partículas de 500 y 100 GeV que decaen a jets.

```{figure} ./../../figuras/jets-masa.png
---
width: 350px
name: jets-masa
---
Distribuciones de la masa del jet principal para jets de quarks y gluones, o fondo, y de una señal de nueva física con partículas de 500 y 100 GeV.
```
### N-subjettiness
Esta variable intenta diferenciar jets de acuerdo al número N de subjets que conforman un jet{cite}`10.1088/2053-2563/ab1be6ch5`. Para lograr esto, se hace un agrupamiento exclusivo de N jets, utilizando los constituyentes del jet, y se calcula la variable $\tau_N$,

$$
    \tau_N = \left(\frac{1}{d_0}\right)\sum_{i=0}^{i=N} p_{Ti} \times \Delta R_{min,i}
$$ (jets-subjettiness) 

donde $\Delta R_{min,i}$ es la menor distancia entre el constituyente *i* del subjet más cercano y $d_0$ es la suma de $p_T$ de todos los constituyentes multiplicada por el radio del jet, para obtener $0<\tau_N<1$. Un valor menor de $\tau_N$ corresponde a una cantidad de subjets igual a N o menor, mientras que un valor mayor indica más de N subjets. Sin embargo, se prefiere utilizar variables adimensionales:

$$
    \tau_{N,N-1}=\frac{\tau_{N}}{\tau_{N-1}}
$$ (jets-ratio_subjettiness)

Un jet con N-1 subjets tendrá un valor de $\tau_{N,N-1}$ mayor a un jet conformado por N o más subjets. En la {numref}`jets-tau`, se presenta un ejemplo de la distribución de $\tau_{21}$ para jets provenientes de quarks y gluones, o fondo, y para una señal de nueva física que decae a jets con una subestructura de 2 o más subjets.

```{figure} ./../../figuras/jets-tau.png
---
width: 350px
name: jets-tau
---
Distribuciones de $\tau_{21}$ para jets de quarks y gluones, o fondo, y de una señal de nueva física con jets que tienen subestructura de 2 o más jets.
```