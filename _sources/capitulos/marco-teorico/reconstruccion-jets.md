(jets)=
# Reconstrucción de jets
En colisiones de hadrones a altas energías, la libertad asintótica y el confinamiento son los conceptos principales que explican la formación de jets, el proceso de dispersión fuerte con mayor tasa de producción en colisiones hadrónicas{cite}`Mangano:2674114`. Los jets son lluvias de partículas colimadas, conformadas principalmente por hadrones, pero también por fotones y leptones. Debido a su alta tasa de producción, los jets se han vuelto objetivo de estudio para "redescubrir" procesos esperados del modelo estándar y garantizar que los detectores se comporten correctamente{cite}`Marshall:1308447`.

En esta sección se explicará la formación de jets a partir de colisiones protón-protón (*pp*), así como los métodos para reconstruirlos y las variables para analizarlos. 

(jets-formacion)=
## Formación de jets

Al colisionar dos protones altamente energéticos, existe una alta tasa de probabilidad de formación de jets. Un diagrama de la formación de un jet se encuentra en la {numref}`jets-desarrollo` y los procesos que intervienen se explican a continuación{cite}`HARRIS_2011,Beresford:2642397`.

El proceso principal es la **dispersión fuerte**: los protones colisionan a altas energías, produciéndose una interacción con alta transferencia de momento $Q$ entre los constituyentes o partones de los protones. Por la libertad asintótica, los partones se comportan como partículas libres y la teoría de perturbación es válida. En la dispersión fuerte se puede crear una partícula resonante de corta vida o puede suceder un proceso de QCD estándar ({numref}`jets-qcd`). Luego, se generan otras partículas mediante decaimientos o procesos de QCD.

También se consideran procesos de **radiación de estado inicial** (ISR) y **radiación de estado final** (FSR): las partículas entrantes y salientes pueden radiar otras partículas. 

Por último, están los **eventos subyacentes** (UE), que son las interacciones entre partones que no participan en la dispersión fuerte y que pueden generar otras partículas.

```{figure} ./../../figuras/jets-qcd.png
---
width: 500px
name: jets-qcd
---
Diagramas de Feynmann que representan la producción de dos jets en colisiones hadrónicas por procesos de QCD{cite}`Mangano:2674114`, construidos a partir de los vértices permitidos ({numref}`qcd-quarkgluon` y {numref}`qcd-gluongluon`)
```
A muy altas energías las partículas generadas se puedan dividir para generar más partículas mediante procesos que todavía no se comprenden completamente{cite}`cottingham_greenwood_2007`. Esta lluvia de partículas se dice colimada porque se generan a ángulos pequeños del partón original.

La evolución perturbativa del jet se detendrá una vez que las partículas alcancen bajas energías. A bajas energías, el confinamiento domina el proceso y las partículas creadas se unen para formar partículas de color neutro. Este proceso no-perturbativo se conoce como **hadronización** y ocurre técnicamente fuera del radio del protón{cite}`10.1088/2053-2563/ab1be6ch4`. La hadronización, en conjunto con la radiación de estado final, se conoce como **fragmentación**. A la colección de todos los hadrones resultantes cerca de la dirección del partón original se le llama jet{cite}`burgess_moore_2013_hadronic`.

El proceso explicado anteriormente se muestra en el siguiente diagrama:

```{figure} ./../../figuras/jets-formacion.png
---
width: 600px
name: jets-desarrollo
---
Esquema de la formación de jets{cite}`camachotoro:tel-00818796`.
```
A pesar de ser un proceso complejo, las propiedades cinemáticas de un jet son las mismas que las del parton original, en primera aproximación.

(jets-agrupamiento)=
## Agrupamiento de jets
La definición de un jet no es única. De hecho, la existencia de un jet es dependiente de la regla matemática que lo defina. Esta regla matemática agrupa los constituyentes del jet de acuerdo a propiedades cinemáticas y se conoce como *algoritmo de agrupamiento de jets*. A continuación, se explicará acerca de estos algoritmos siguiendo{cite}`10.1088/2053-2563/ab1be6ch3,Marshall:1308447,Huth:1990mi`

De manera general, un algoritmo de agrupamiento hace un mapeo del conjunto de hadrones del estado final con cuadri-momento $\{p_1^{had},p_2^{had},\dots,p_n^{had}\}$ a un conjunto de jets con cuadri-momento $\{p_1^{jet},p_2^{jet},\dots,p_m^{jet}\}$, donde usualmente $m<n$. El momento de cada jet es la suma de los momentos de las partículas que lo constituyen y la suma vectorial define el eje del jet.

Todos los algoritmos agrupan objetos cercanos alrededor del ángulo polar de los protones entrantes $\phi$ y la pseudo-rapidez $\eta$, definida como: 

$$
    \eta\equiv -\ln\left[\tan\left(\frac{\theta}{2}\right)\right]
$$ (eta)

donde $\theta$ es el ángulo azimutal entre los constituyentes y los protones entrantes.

Los jets se pueden reconstruir a partir de objetos experimentales, como depósitos de energía en calorímetros y trayectorias de partículas cargadas, o de objetos teóricos, como partones y hadrones obtenidos mediante simulaciones.

```{figure} ./../../figuras/jets-types.png
---
width: 700px
name: jets-types
---
Esquema que muestra los diferentes tipos de jet. Se producen partículas de color por la dispersión fuerte, creando partículas de color neutro en la fragmentación. Estas partículas pueden producir distintas señales en los detectores{cite}`camachotoro:tel-00818796`.
```
Se espera que un algoritmo posea ciertas características:
- Ser robusto con respecto al tipo de datos de entrada.
- Teóricamente, debe ser *colinealmente estable*: la separación de un partón en dos partones colineales no debe cambiar el resultado del agrupamiento del jet ({numref}`jets-colineal`).
- Cumplir con la *estabilidad infrarroja*: la radiación de un gluon suave no debe cambiar el agrupamiento ({numref}`jets-infrarrojo`).
- Baja sensibilidad a los UE y el pileup (PU), que son señales remanentes de otras colisiones.
- Fácil de utilizar en cálculos teóricos y análisis experimentales, así como computacionalmente rápidos de ejecutar.

```{figure} ./../../figuras/jets-colineal.png
---
width: 500px
name: jets-colineal
---
Esquema de la estabilidad colineal. La separación de un parton en partones colineales no debe cambiar la configuración de un jet{cite}`10.1088/2053-2563/ab1be6ch3`.
```

```{figure} ./../../figuras/jets-infrarrojo.png
---
width: 500px
name: jets-infrarrojo
---
Esquema de la estabilidad infrarroja. La emisión de un gluon suave entre dos jets no debe resultar en su unión{cite}`10.1088/2053-2563/ab1be6ch3`. 
```
### Tipos de algoritmos
Existen dos tipos principales de algoritmos de agrupamiento: *algoritmos de cono* y *algoritmos de recombinación secuencial*

#### Cono
Los algoritmos de cono asumen que el jet se encuentra en regiones cónicas del espacio $(\eta-\phi)$, por lo que los jets reconstruidos por estos algoritmos tienen bordes circulares. Son de fácil implementación, pero no son colinealmente estables{cite}`Atkin_2015`.

Se puede pensar que su aproximación es de arriba hacia abajo. En general, un algoritmo de cono sigue los pasos a continuación{cite}`Schieferdecker_2009`:
1. Hallar el constituyente más energética del evento, o semilla.
2. Colocar un cono de radio *R* alrededor de esta semilla y sumar el momento de todas las partículas que constituyen el cono, formando un jet de prueba.
3. Comparar el eje de la semilla con el del jet de prueba.
   1. Si el eje del del jet de prueba y la semilla coinciden: El jet se prueba se toma como jet
   2. De otra forma: Se repiten los pasos anteriores con el eje del jet de prueba como semilla.

Estos pasos se repiten hasta estos pasos hasta que no haya semillas sobre un umbral de energía escogido.

Ejemplos de algoritmos de cono son: *Midpoint Cone*, utilizado en Tevatron, *Iterative Cone* y *SISCone*{cite}`Salam_2007`, utilizados anteriormente por CMS.
#### Recombinación secuencial
Los algoritmos de recombinación secuencial asumen que los constituyentes de un jet poseen una pequeña diferencia en el momento transverso. Por esto, las partículas son agrupadas en el espacio de momento, resultando en jets con fluctuaciones en el espacio $(\eta-\phi)${cite}`Atkin_2015`.  

En general, los algoritmos de recombinación secuencial utilizan las siguientes medidas de distancia entre dos constituyentes:

$$
    d_{ij} = min(p_{Ti}^{2p},p_{Tj}^{2p})\times \frac{\Delta R_{ij}^2}{R}
$$ (dist_const)

donde $p_T$ es el momento transverso de las partículas, $\Delta R_{ij} = \sqrt{(\eta_i-eta_j)^2+(\phi_i-\phi_j)^2}$ es la distancia entre dos constituyentes en el espacio $(\eta-\phi)$, $R$ es el radio final del jet, usualmente entre 0.4-0.7 y $p$ es un parámetro referente al tipo de algoritmo.

También utilizan la distancia entre el eje del haz y el constituyente detectado:

$$
    d_{iB}=p_{Ti}^{2p}
$$ (dist_eje)

Se puede pensar que el funcionamiento de estos algoritmos es de abajo hacia arriba:

1. Hallar el mínimo en el conjunto $\{d_{ij},d_{iB}\}$.  
   1. Si el mínimo es $d_{ij}$: los constituyentes *i* y *j* se unen en un solo constituyente *ij*, sumando el cuadri-momento y eliminando *i* y *j*  de la lista de constituyentes.   
   2. Si el mínimo es $d_{iB}$: *i* se considera jet y eliminado de la lista de constituyentes.   

Los pasos anteriores se repiten hasta que todas las partículas son parte de un jet, con distancias $\Delta R_{ij}$ entre los ejes de los jets mayores a $R$ (agrupamiento inclusivo), o hasta que se obtenga una cantidad específica de jets (agrupamiento exclusivo).

Los algoritmos de recombinación utilizados son:

- *Kt*{cite}`PhysRevD.48.3160`: para este algoritmo $p=1$. Es sensible a los UE y PU. Este algoritmo representa una aproximación de la inversión del proceso de ramificación de QCD porque preserva la historia de agrupamiento.
- *Anti kt*{cite}`Cacciari_2008`: para este algoritmo $p=-1$. Contrario al *kt*, es poco sensible a los UE y el PU. En este algoritmo el agrupamiento no está relacionada a la manera en la que los partones se dividen.
- Cambridge/Aachen{cite}`Dokshitzer_1997`: para este algoritmo $p=0$. Es el mejor para estudiar la subestructura de los jets, pero es más complicado que *kt*. También es susceptible a los UE y el PU. 

Los algoritmos de recombinación son los más utilizados desde su implementación en el programa *FastJet*{cite}`FastJet`, un paquete de C++ que proporciona herramientas para agrupar y analizar jets.

(jets-subestructura)=
## Variables de subestructura
La subestructura de un jet puede analizarse para diferenciar si el jet proviene de un gluon, un quark suave o partículas aún no descubiertas. A continuación se describirán algunas de las variables que se calculan para estudiar la subestructura de un jet, utilizando como referencia {cite}`10.1088/2053-2563/ab1be6ch8`.

### Masa
La masa es la variable mas evidente para discriminar entre jets provenientes de distintas partículas. La masa de un jet es cercana a la masa de la partícula de la cual se origina, asumiendo que los productos del decaimiento están contenidos en el jet. Está definida como la suma de la masa invariante de todos los constituyentes del jet calculada a partir del cuadri-momento de cada constituyente.

### N-subjettiness
Esta variable intenta diferenciar jets de acuerdo al número N de subjets que conforman un jet. Para lograr esto, se hace un agrupamiento exclusivo de N jets con los constituyentes del jet y se calcula la variable $\tau_N$

$$
    \tau_N = \left(\frac{1}{d_0}\right)\sum_{i=0}^{i=N} p_{Ti} \times \Delta R_{min,i}
$$ (subjettiness) 

Donde $\Delta R_{min,i}$ es la menor distancia entre el constituyente *i* del subjet más cercano y $d_0$ es la suma de $p_T$ de todos los constituyentes multiplicada por el radio del jet, para obtener $0<\tau_N<1$. Un valor menor de $\tau_N$ corresponde a una cantidad de subjets igual a N o menor, mientras que un valor mayor indica más de N subjets. Sin embargo, se prefiere utilizar una variable adimensional:

$$
\tau_{N-1,N}=\frac{\tau_{N-1}}{\tau_N}
$$ (ratio_subjettiness)

Un jet con N-1 subjets tendrá un valor de $\tau_{N-1,N}$ menor a un jet conformado de N o más subjets.

### Funciones de correlación de energía

Las funciones de correlación de energía logran esencialmente lo mismo que N-subjettines, sin la necesidad de definir N ejes de referencia {cite}`Marzani_2019`. Su finalidad es identificar una estructura de N-subjets o depósitos de energía. Las funciones de correlación de energía (ECF) están definidas de la siguiente forma{cite}`Jankowiak_2012,Larkoski_2013`:

\begin{gather}
    ECF(1,\beta)=\sum p_{Ti}\\
    ECF(2,\beta)=\sum_{i<j} p_{Ti}p_{Tj}(\Delta R_{ij})^\beta\\
    ECF(3,\beta)=\sum_{i<j<k} p_{Ti}p_{Tj}p_{Tk}(\Delta R_{ij}\Delta R_{jk}\Delta R_{ki})^\beta\\
    \dots\\
    ECF(N,\beta)=\sum_{\text{all N}} \left(\prod^{N}_{a=1} p_{Ta}\right)\left(\prod^{N-1}_{b=1}\prod^{N}_{c=b+1} \Delta R_{ib}\Delta R_ic\right)
\end{gather}

donde el parámetro angular $\beta$ permite sensibilidad a distintas escalas angulares. Si un jet tiene N depósitos de energía, ECF(N+1) es menor que ECF(N).

Al igual que en N-subjettiness, se definen variables adimensionales utilizando proporciones:

$$
    r_N = \frac{ECF(N+1)}{ECF(N)}
$$ (ecf_ratio)

Y se ha hallado que las proporciones tienen mayor poder de discriminación, por ejemplo:

$$
    C_N = \frac{r_N}{r_{N-1}}
$$ (ecf_double)

Existen otras proporciones{cite}`Marzani_2019` y se construyen para amplificar características específicas de los jets.