(bsm)=
# Más allá del modelo estándar
A pesar de que en los últimos 40 años se han verificado exitosamente múltiples predicciones hechas a partir del modelo estándar{cite}`Kobayashi_2021,NAP6045`, es evidente que no es una teoría final debido a que no explica varios fenómenos observados experimentalmente. A partir de estas limitaciones, se han planteado múltiples teorías que intentan responder las preguntas para las que el modelo estándar no tiene explicación. Estás teorías se conocen como teorías *más allá del modelo estándar* (BSM) y su verificación/refutación es uno de los objetivos del programa del LHC.

En esta sección se explicarán algunas de las limitaciones que presenta el modelo estándar. Seguido de esto, se presentarán las teorías BSM más conocidas y, más específicamente, teorías BSM relacionadas a eventos dijet, la topología a estudiar en este trabajo.

## Limitaciones del modelo estándar
Las limitaciones del modelo estándar se pueden separar en *fenomenológicas*, que se refiere a inconsistencias de la teoría con observaciones experimentales o observaciones experimentales que el modelo estándar no puede explicar, y *teóricas*, que hace referencia a predicciones no observadas o valores y parámetros para los que la teoría no tiene explicación. La referencia principal para esta sección es {cite}`BSMlectures`.

### Problemas fenomenológicos
#### Asimetría materia-antimateria
La asimetría materia-antimateria puede ser acomodada, pero no explicada por el modelo estándar. En 1967, Sakharov propuso tres condiciones necesarias para crear una concentración significativa de materia en el universo temprano{cite}`Sather:1996cz`:

- Interacciones que puedan cambiar quarks a leptones (violación del número bariónico).
- Condiciones en las que el equilibrio termodinámico no se sostenga. Esto pudo haber ocurrido durante la expansión del universo temprano. 
- Violación de carga *C* y carga-paridad *CP*, observada experimentalmente dada la diferencia en cantidad de materia y antimateria.  
    
Sin embargo, la violación *C* y *CP* descrita por el modelo estándar no es suficiente para generar la cantidad de materia que se observa en el universo.

#### Masa de los neutrinos
La masa de los neutrinos es al menos seis ordenes de magnitud más pequeña que la masa de los electrones. La brecha entre la masa de los neutrinos y cualquier otro fermión cargado es mucho más grande que entre cualquier otro par de fermiones{cite}`deGouvea_2009`:

```{figure} ./../../figuras/bsm-neutrinos.png
---
width: 300px
name: bsm-neutrinos
---
Masa de los fermiones del modelo estándar. Para la masa de los neutrinos, se asumió la jerarquía usual de masas entre generaciones, con un límite superior de  $m_i$ < 1 eV. De {cite}`deGouvea_2009`.
```
El modelo estándar predice neutrinos no masivos, por lo que se necesita nueva física para explicar el mecanismo mediante el cual los neutrinos adquieren masa y por qué es tan pequeña.

#### Materia oscura y energía oscura
Se estima que la materia oscura forma aproximadamente el 27% del universo, mientras que la materia visible forma menos del 5%. La existencia de la materia oscura se ha inferido por los efectos gravitacionales que tiene en la materia visible. Las estructuras del universo no serían posibles sin la fuerza de gravedad debido a algún tipo de materia invisible y no relativista{cite}`Ellis2012-rh`. 

La materia oscura en conjunto con la materia visible conforma aproximadamente el 32% de la energía del universo. El resto se conoce como *energía oscura* y está asociada con el vacío en el espacio. La energía oscura se utiliza para explicar la tasa de expansión del universo y su aceleración{cite}`1607.00330`.

La naturaleza de la materia oscura y la energía oscura no está incluida en el modelo estándar.

### Problemas teóricos
#### Descripción cuántica de la gravedad
La evidencia más clara de que se necesita nueva física es que el modelo estándar no incluye la gravedad. La fuerza gravitatoria afecta la física de partículas a escalas pequeñas, cuantificadas por la escala de Planck $M_{Planck}\approx10^{19}GeV$, escala que se considera el límite de validez del modelo estándar{cite}`Gripaios_2015`. Sin embargo, la relatividad general, que es la teoría de la gravedad, no es renormalizable. Debido a esto, no se ha logrado construir una teoría cuántica de campos que reconcilie la gravedad con la física de partículas{cite}`Allison:2014sjw`

#### Origen de las masas/mezclas
El mecanismo de ruptura espontánea de simetría, que explica como las partículas obtienen masa, es agregado al modelo estándar de manera conveniente. La teoría no explica el origen de este mecanismo, solo se sabe que es necesario para poder coincidir con las observaciones experimentales{cite}`camachotoro:tel-00818796`.

Por otra parte, las tres generaciones de fermiones muestran una jerarquía regular en sus masas ({numref}`bsm-neutrinos`) y los ángulos de mezcla de los quarks parecen tener un patrón o estructura en sus valores. Estos sólo representan parámetros en el modelo estándar y no se entiende por qué presentan una estructura.

#### Problema CP fuerte
La cromodinámica cuántica depende de pocos parámetros: la constante de acople fuerte, la masa de los quarks y un parámetro relacionado a la estructura del vacío de QCD $\theta${cite}`Creutz_2018`. Este último se encuentra en un término de interacción que permite la violación CP: 

$$
    \mathcal{L}_\theta=\frac{\theta g_s^2}{32\pi^2}G^a_{\mu\nu}\tilde{G}_{a\mu\nu}
$$ (bsm-qcdcp)

donde $G^{a}_{\mu\nu}$ son las fuerzas de los campos de QCD y $g_s$ es la contante de acople.

El parámetro aparece en el cálculo del momento dipolar del neutrón, e indica que $\theta$ debe ser muy pequeño{cite}`Mannel:2007zz`. 

Experimentalmente no se ha observado violación *CP* en la interacción fuerte y el problema de por qué el parámetro $\theta$ es tan pequeño no se ha resuelto.

#### Problema de jerarquía
El bosón de Higgs es la única partícula fundamental escalar en el modelo estándar, por lo que su masa es modificada por términos correctivos en todas las escalas en las que interactúa; términos proporcionales a estas escalas{cite}`Smith_2019`:

$$
    m^2\equiv m_0^2+\delta m^2
$$ (bsm-masahiggs)

donde $m_0$ corresponde a la 'masa desnuda' del Higgs y $\delta m^2$ a las correcciones radiativas.

En el modelo estándar se consideran escalas hasta $M_{Planck}\approx10^{19}GeV$, por lo que teóricamente $\delta m^2\approx M_{Planck}$.

Sin embargo, se tiene un valor experimental de $m^2\approx125GeV$, lo que requeriría un valor de $m_0^2$ escogido muy específicamente para cancelar la mayoría de las correcciones. El ajuste fino de este parámetro no se considera natural y representa problemas con respecto a la universalidad de la teoría.

El problema de jerarquía es consecuencia de la diferencia entre escalas de la fuerza electro-débil y la fuerza gravitacional{cite}`camachotoro:tel-00818796`.

## Búsqueda de nueva física
La búsqueda de una teoría del todo, que relacione los fenómenos físicos conocidos y prediga el resultado de cualquier experimento, es un tema en curso en la física. 

```{figure} ./../../figuras/bsm-unificacion.png
---
width: 900px
name: bsm-unificacion
---
Secuencia histórica de la unificación de leyes físicas. De {cite}`Elert_1998`. 
```
Se cree que el modelo estándar es una aproximación a bajas energías que unifica las cuatro interacciones fundamentales. Hasta ahora, no se ha propuesto una teoría que logre este objetivo. Sin embargo, existen teorías que intentan explicar los fenómenos que el modelo estándar no explica.

### Supersimetría
La supersimetría (SUSY) es una simetría de teoría cuántica de campos que relaciona fermiones y bosones. La mínima extensión supersimétrica del modelo estándar (MSSM) duplica el espectro de masa al agregar partículas supersimétricas, o spartículas.

```{figure} ./../../figuras/bsm-sparticulas.png
---
width: 700px
name: bsm-sparticulas
---
Diagrama ilustrativo de las partículas supersimétricas planteadas por SUSY. De {cite}`york`.
```
Entre las motivaciones teóricas de este modelo se encuentra{cite}`Virdee2016-dd`:

- Las contribuciones de las partículas supersimétricas en el cálculo de la masa del bosón de Higgs cancelan las contribuciones de las partículas del modelo estándar, eliminando el problema de jerarquía.
- Ofrece una ruta para la unificación de las fuerzas fundamentales del modelo estándar en una escala de $10^{15}$ GeV ({numref}`bsm-susyunificacion`).
- La partícula más ligera predicha por el modelo es estable y eléctricamente neutra, por lo que es un candidato para la materia oscura.

```{figure} ./../../figuras/bsm-susyunificacion.png
---
width: 400px
name: bsm-susyunificacion
---
Evolución de las constantes de acople en función de la energía para el modelo estándar (líneas punteadas) y para MSSM (líneas sólidas). En rojo la interacción electromagnética, en azul la interacción débil y en verde la interacción fuerte. De {cite}`Cornell_2015`
```
Sin embargo, las partículas supersimétricas no han sido observadas{cite}`ATLAS_SUSY`, ninguno de los experimentos diseñados para detectar materia oscura ha detectado la partícula ligera que predice SUSY y tampoco hay evidencia para la unificación de las fuerzas.

### Dimensiones extra
Desde 1920 se ha considera la existencia de dimensiones espaciales nuevas, más allá de las cuatro que conocemos. La primera idea, por Kaluza y Klein{cite}`KALUZA_2018,Klein:1926tv`, propone una quinta dimensión, unificando la relatividad general y el electromagnetismo. Desde entonces, se han estudiado varios modelos que plantean nuevas dimensiones. Por ejemplo, la teoría de cuerdas en todas sus versiones contempla más de cuatro dimensiones.

La motivación detrás de las dimensiones extras, es que al considerarlas se podrían resolver alguno de los problemas que presenta el modelo estándar. Por ejemplo, el modelo Arkani-Dimopoulos-Dvali (ADD){cite}`Arkani_Hamed_1998` agrega dimensiones extra grandes en las que se propaga la gravedad. Este modelo podría resolver el problema de jerarquía al acercar la escala fundamental a la escala electrodébil.

Sin embargo, no es claro cómo se manifestarían estas dimensiones. Algunas de las maneras de probar experimentalmente su existencia sería mediante el descubrimiento de partículas que solo puedan existir si las dimensiones extra existen o mediante la producción de agujeros negros microscópicos.

Una explicación más detallada sobre modelos que incluyen dimensiones extras se puede encontrar en {cite}`P_rez_Lorenzana_2005`.

### Teoría de cuerdas
Hasta ahora, los intentos para incorporar la relatividad general en el modelo estándar no han sido exitosos. La teoría de cuerdas intenta reconciliar estas teorías planteando que las partículas fundamentales no son puntuales, sino más bien cuerdas unidimensionales que vibran. En la teoría de cuerdas uno de los muchos estados de vibración de la cuerda corresponde al gravitón, la partícula que en la mecánica cuántica es responsable de la fuerza gravitacional{cite}`Wray_2011`.

En los 80s se plantearon distintas versiones de la teoría de cuerdas que en los 90s resultaron ser parte de una teoría que se conoce como la teoría M. Sin embargo,
- La teoría solo funciona con dimensiones adicionales para las que no se tiene evidencia.
- Introduce partículas supersimétricas que no se han hallado. Estas partículas podrían ser realmente masivas, explicando por qué no se han producido en los aceleradores de partículas.
- El número de soluciones posibles es del orden de $10^{500}$, cada una con su conjunto único de partículas fundamentales y valores para las constantes fundamentales. Estas posibles soluciones puede que indiquen que el universo es una gran cantidad de universos posibles, haciendo que la teoría sea difícil de comprobar experimentalmente.

La teoría de cuerdas es un trabajo en proceso, pero es una de las mayores promesas para la unificación de todas las fuerzas fundamentales en una teoría cuántica de campos.

## Eventos dijet
La búsqueda de nuevas partículas es parte importante de la búsqueda de física BSM. Los modelos explicados anteriormente y muchos otros incluyen en su formulación nuevas partículas que permiten explicar alguna de las limitaciones del modelo estándar.

En el LHC se utilizan haces de protones, por lo que una alta fracción de los eventos de colisión resultan en formación de jets. Para este proyecto es de particular interés la topología de dos jets, o dijet.

```{figure} ./../../figuras/bsm-dijets.png
---
width: 250px
name: bsm-dijets
---
Diagrama de la producción de una resonancia *X* por la interacción de dos partones y su decaimiento. De {cite}`Beresford:2642397`
```
Debido a la falta de evidencia de física BSM, existen varios modelos de producción dijet que se utilizan para mejorar y optimizar los métodos de análisis{cite}`Beresford:2642397,Allen:2636572`.

### Mediador Z' de materia oscura
Para incluir la materia oscura en el modelo estándar, se plantea una *partícula masiva de interacción débil* (WIMP). Sus características principales son:
- Interactúa principalmente a través de la fuerza nuclear débil y la gravedad.
- Masa de mayor magnitud que cualquier partícula del modelo estándar.
- Estable o de larga vida. 

La partícula Z' se acopla a la materia oscura y a todos los quarks del modelo estándar, pero no a los leptones. Debido a que no interactúa con la materia a través de la fuerza electromagnética ni fuerza fuerte, no es visible directamente en los detectores. Por su masa, se movería relativamente lento.

```{figure} ./../../figuras/bsm-wboson.png
---
width: 500px
name: bsm-wboson
---
Diagrama de Feynman para los decaimientos de *Z'*. (a) Decaimiento a dos partículas de materia oscura con ISR. (b) Decaimiento a dijets. De {cite}`Allen:2636572`.
```

Partículas como estas son parte de varios modelos BSM como SUSY, dimensión extra universal (UED) y little Higgs. Otros modelos postulan un "sector oscuro" de partículas que no interactúan directamente con la materia regular, sino a través de una partículas mediadoras que se acoplan tanto al modelo estándar como a la materia oscura. Estas podrían producirse y ser detectadas en el LHC. La forma en la que se podrían detectar depende del modo de decaimiento. Si el decaimiento es a partículas de materia oscura, se puede detectar como falta de energía. En cambio, si decae a partículas del modelo estándar, sus productos se podrían observar directamente ({numref}`bsm-wboson`).

El modelo Z' es recomendado por ATLAS/CMS Dark Matter Forum{cite}`Abercrombie_2020`.

### Bosón W' pesado
Algunas teorías que plantean un grupo de gauge adicional introducen un bosón *W'*. Un modelo comúnmente utilizado para análisis es el *modelo estándar secuencial* (SSM). Este nuevo bosón es una versión más pesada del bosón *W* del modelo estándar. La tasa de decaimiento a un estado final de dos quarks ($W'\longrightarrow qq$) es del 75%.

### Quarks excitados
Los quarks excitados *q\** son característicos de los modelos de quarks complejos{cite}`PhysRevD.42.815`. En estos modelos, los quarks no son partículas fundamentales, más bien son estados ligados de otras partículas. 

Los modelos compuestos buscan abordar la jerarquía de masa de los quarks y la aparente organización de fermiones en generaciones, explicando también el comportamiento de hadrones.

Se plantea que en una colisión *pp* un quark puede ser excitado a aun estado superior mediante la absorción de un gluon y luego radiar un bosón cuando regresa a su estado fundamental.

```{figure} ./../../figuras/bsm-quark.png
---
width: 300px
name: bsm-quark
---
Diagrama de Feynman de la producción de un quark excitado *q\** por la dispersión fuerte de un quark *q* y un gluon *g*, y subsecuente decaimiento a dos jets. De {cite}`Ruiz_2015`.
```
Un quark excitado puede decaer a un par quark-gluon ($q^*\longrightarrow qg$). Este decaimiento tiene una tasa de ramificación del $\sim 85\%$.

### Agujeros negros cuánticos

La escala fundamental de la fuerza gravitatoria, escala de Planck se encuentra $\sim 10^{16}$ órdenes de magnitud sobre la escala electrodébil. Para explicar esto, se plantea que la fuerza gravitatoria se encuentra en la escala electrodébil, pero que parece más débil porque se propaga en dimensiones adicionales. Evidencia de estas dimensiones se pueden buscar en el LHC a través de los efectos gravitatorios que producen.

La introducción de dimensiones extra disminuye la escala fundamental de la gravedad $M_D$ a TeV, lo que permitiría la producción de agujeros negros cuánticos en colisiones *pp*. Si los agujeros negros producidos poseen masa $\sim M_D$, pueden decaer a un estado final de 2 cuerpos{cite}`Meade_2008`.

Dos modelos populares que incluyen dimensiones extra son el modelo ADD{cite}`Arkani_Hamed_1998`, discutido anteriormente, y el modelo Randall-Sundrum (RS){cite}`Randall:1999ee`.