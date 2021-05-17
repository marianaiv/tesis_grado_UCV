---
tags: Notas, Teoria
---

Nueva física
===

El Modelo Estándar es uno de los mayores triunfos científicos del siglo pasado. Durante los últimos 20 años se han verificado exitosamente predicciones obtenidas a partir de este modelo. Sin embargo, deja muchas preguntas abiertas[^general]:

[^general]: https://summerstudent.web.cern.ch/lectures-2019/beyond-standard-model

## Problemas fenomenológicos
### Asimetría materia-antimateria: 
La simetría materia-antimateria puede ser acomodada, pero no explicada por el Modelo Estándar. En 1967, Sakharov propuso tres condiciones necesarias para crear la concentración significativa de bariones en el universo temprano[^sakharov]:
    *    Interacciones que puedan cambiar quarks a leptones (violación del número bariónico).
    *    Condiciones en las que el equilibrio termodinámico no se sostenga. Esto pudo haber ocurrido durante la expansión del universo temprano.
    *    Violación C y CP, que se observa experimentalmente dada la diferencia en cantidad de materia y antimateria.  
    
  Sin embargo, la violación C y CP descrita por el Modelo Estándar no es suficiente para generar la cantidad de materia que se observa en el universo.[^cp]
  
[^sakharov]: https://cds.cern.ch/record/573673/files/0207323.pdf
[^cp]: https://www.vanderbilt.edu/AnS/physics/panvini/babar/sakharov.pdf

### Masa de los neutrinos
La masa de los neutrinos es al menos seis ordenes de magnitud más pequeña que la masa de los electrones. La brecha entre la masa del neutrino y cualquier otro fermión cargado es mucho más grande que entre cualesquiera de los demás fermiones[^neutrinos]:

![Masa de los fermiones de acuerdo al Modelo Estándar](https://i.imgur.com/hpNwRoy.png)

  El Modelo Estándar predice neutrinos no masivos, por lo que se necesita nueva física para explicar cómo los neutrinos adquieren masa y por qué es tan pequeña.

[^neutrinos]: https://indico.cern.ch/event/26995/contributions/604958/attachments/484295/669764/hql08_AndreDeGouvea.pdf

- **Materia oscura**
Se estima que la materia oscura forma aproximadamente el 27% del universo, mientras que la materia que conocemos forma solo el 5%. La existencia de esta se ha inferido por los efectos gravitacionales que tiene en la materia visible, ya que las estructuras del universo no serían posibles sin la fuerza de gravedad de algún tipo de materia invisible y no relativista.[^darkm]

  El Modelo Estándar no explica la materia oscura.

[^darkm]: https://royalsocietypublishing.org/doi/pdf/10.1098/rsta.2011.0452
## Problemas teóricos
### Descripción cuántica de la gravedad
La evidencia más clara de que se necesita física más allá del Modelo Estándar es que no incluya la gravedad. La gravedad afecta a la física de partículas a escalas pequeñas cuántificadas por la escala de Planck $M_{Planck}\approx10^{19}GeV$, escala que se considera el límite de validez del Modelo Estándar[^scales]. 

  Sin embargo, la gravedad es no renormalizable, por lo que no se ha logrado construido una teoría cuántica de campos que reconcilie la gravedad con la física de partículas.[^gravedad]

[^gravedad]: https://inspirehep.net/files/747d3869d8f6692ae97fe1ae7f0968b4
[^scales]: https://arxiv.org/pdf/1503.02636.pdf

### Origen de las masas/mixings
El Modelo Estándar no tiene una explicación para la masa de los fermiones, los angulos de mezcla de los quarks o por qué existen tres generaciones, o "sabores", de fermiones.

  El mecanismo de ruptura de simetría espontánea, que explica como las partículas obtienen masa, es agregado al Modelo Estándar de manera conveniente. El Modelo Estándar no explica el origen de este mecanismo, solo se sabe que es necesario para poder coincidir con las observaciones experimentales.[^masas]

  Por otra parte, las tres generaciones de fermiones muestran un jerarquía regular en sus masas y los angulos de mezcla de los quarks parecen tener un patrón o estructura en sus valores.[^flavors]

  Estos sólo representan parámetros en el Modelo Estándar y no entendemos por qué presentan una estructura.


[^masas]: https://cds.cern.ch/record/1475083/files/CERN-THESIS-2012-107.pdf
[^flavors]: https://inspirehep.net/files/747d3869d8f6692ae97fe1ae7f0968b4


### Problema CP fuerte
La cromodinámica cuántica depende de pocos parámetros: la constante de acoplamiento fuerte, la masa de los quarks y un parametro relacionado a la estructura del vacio de QCD $\theta$.[^qcd] Este último se encuentra en un término de interacción que permite la violación CP: 
 $$
 \mathcal{L}_\theta=\frac{\theta g_s^2}{32\pi^2}G^a_{\mu\nu}\tilde{G}_{a\mu\nu}
 $$
   Donde $G^{a}_{\mu\nu}$ son las fuerzas de los campos de QCD y $g_s$ es la contante de acoplamiento.
  
   Este parámetro aparece en el cálculo del momento dipolar del neutron, indicando que $\theta$ debe ser muy pequeño.[^cpfuerte] Experimentalmente no se ha observado violación CP en la interacción fuerte.
 
   El problema de por qué el parámetro $\theta$ es tan pequeño no se ha resuelto.

[^qcd]: https://arxiv.org/pdf/1810.03543.pdf
[^cpfuerte]: https://indico.cern.ch/event/427023/contributions/1050624/attachments/912026/1288208/Lancester-Mannel-Proc.pdf

### Problema de jerarquía
El boson de Higgs es la única partícula fundamental escalar en el Modelo Estándar, por lo que su masa es modificada por terminos correctivos en todas las escalas en las que interactua; términos proporcionales a estas escalas[^correccion] :
 $$
m^2\equiv m_0^2+\delta m^2
 $$
  Donde $m_0$ corresponde a la 'masa desnuda' del Higgs y $\delta m^2$ a las correciones radiativas.
  
  En el Modelo Estándar se consideran escalas hasta $M_{Planck}\approx10^{19}GeV$, por lo que teóricamente $\delta m^2\approx M_{Planck}$.
 
  Se tiene un valor experimental de $m^2\approx125GeV$, lo que requeriría un valor de $m_0^2$ escogido muy específicamente para cancelar la mayoría de las correcciones. El ajuste fino de este parámetro se considera no-natural y representa problemas con respecto a la universalidad de la teoría.
  
  El problema de jerarquía es consecuencia de la diferencia entre escalas de la fuerza electro-débil y la fuerza gravitacional.[^jerarquia]


[^correccion]: http://hamilton.uchicago.edu/~sethi/Teaching/P445-S2019/Emily_Smith_QFT_III_Final_Paper.pdf
[^jerarquia]: https://cds.cern.ch/record/1475083/files/CERN-THESIS-2012-107.pdf