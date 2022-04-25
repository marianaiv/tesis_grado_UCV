(qcd)=
# Cromodinámica cuántica
Como se mencionó en la [sección anterior](ms-interacciones), la cromodinámica cuántica (QCD) es la teoría de la interacción fuerte y describe la dinámica de los quarks y gluones. Es una teoría cuántica de campos no-Abeliana asociada al grupo de simetría $SU(3)_C$ y construida en analogía a la electrodinámica cuántica{cite:p}`Sutton2016-eh`.

El bosón predicho por la teoría es el gluon. Al igual que el fotón, es una partícula no-masiva de espín 1 que interactúa con partículas que poseen *carga de color*. La carga de color es el análogo a la carga eléctrica y es el número cuántico conservado en la teoría. Existen tres tipos de carga para los quarks: rojo, verde y azul (para los anti-quarks: anti-rojo, anti-verde y anti-azul). 

Los gluones poseen carga de color, contrario a los fotones que no poseen carga eléctrica. Existen ocho gluones con superposiciones de cargas de color. Así, los gluones median la interacción fuerte pero también interactúan entre sí, haciendo que el análisis de la QCD sea más complejo. 

Los vértices de interacción permitidos por la cromodinámica cuántica son el acople quark-gluon, $gq\bar{q}$, como se observa en la {numref}`qcd-quarkgluon`, y la interacción propia de tres y cuatro gluones, *ggg* y *gggg*, que se puede observar en la {numref}`qcd-gluongluon`.

```{figure} ./../../figuras/qcd-quarkgluon.png
---
width: 300px
name: qcd-quarkgluon
---
Vértice de interacción $gq\bar{q}$. En este vértice en particular, un quark con carga de color rojo ($r$) cambia a un quark con carga de color azul ($b$) emitiendo un gluon rojo-antiazul ($r\bar{b}$){cite:p}`griffiths_1987`.
```

```{figure} ./../../figuras/qcd-gluongluon.png
---
width: 400px
name: qcd-gluongluon
---
Vértice de interacción permitidos en QCD. De izquierda a derecha, interacción propia de tres y cuatro gluones{cite:p}`griffiths_1987`.
```
En teoría de campos, el acople efectivo de un vértice de interacción es modificado por la interacción{cite:p}`altarelli2005standard`. Como resultado la intensidad de la fuerza depende del cuadri-momento al cuadrado ($Q^2$) entre los participantes. La medida de intensidad de la interacción es la constante de acople de QCD $\alpha_s$($Q^2$). El acople es grande para pequeños valores de $Q$ y disminuye a medida que $Q$ aumenta. Esto se conoce como confinamiento y libertad asintótica, respectivamente.

(qcd-libertadasintotica)=
## Libertad asintótica
La libertad asintótica explica que a altas energías las partículas dentro de un hadrón se comportan como libres. El comportamiento de la constante de acople de QCD es contrario al de QED: para QCD la constante de acople disminuye en función de $Q$. La libertad asintótica se refiere a que el acople efectivo disminuye al aumentar $Q$ y desaparece asintóticamente ({numref}`qcd-alphas`). Por lo tanto, las interacciones de QCD son débiles para valores grandes de $Q$. Esto implica que en regiones donde $Q^2$ es grande, o a distancias pequeñas, $\alpha_s$ es pequeño y la teoría de perturbación puede ser utilizada para calcular observables. 

La libertad asintótica fue descubierta en 1973 por David Gross, Frank Wilczek y David Politzer. Por ello obtuvieron el premio Nobel de física en 2004{cite:p}`nobel2004`.

```{figure} ./../../figuras/qcd-alphas.png
---
width: 600px
name: qcd-alphas
---
Resumen de medidas experimentales de la constante de acople $\alpha_s$ en función de la escala de energía $Q${cite:p}`alphas`.
```

(qcd-confinamiento)=
## Confinamiento
Contrario al concepto de libertad asintótica se encuentra el confinamiento. La fuerza de la interacción, o constante de acople $\alpha_S$, aumenta a largas distancias o pequeñas transferencias de momento $Q$, como se puede observar en la {numref}`qcd-alphas`. Esta propiedad explica la imposibilidad de separar partículas con carga de color, es decir, explica por qué no se observan quarks y gluones libres. También explica que los hadrones se encuentren en estados compuestos de quarks estrechamente unidos y de carga de color neutra. Por ejemplo, al intentar separar un mesón neutro conformado por un quark y un anti-quark, la energía crece hasta que se crean pares de quarks y anti-quarks a partir del vacío y se forman nuevos mesones neutros en lugar de obtener quarks libres

El aumento de la constante de acople implica que donde $Q$ es pequeño, o a distancias grandes, los cálculos con teoría de perturbación ya no son válidos; esta región se conoce como no-perturbativa.

(qcd-jets)=
## Formación de jets
En colisiones de hadrones a altas energías, la libertad asintótica y el confinamiento son los conceptos principales que explican la formación de jets, el proceso de dispersión fuerte con mayor tasa de producción en colisiones hadrónicas{cite}`Mangano:2674114` y el objeto de estudio de este trabajo. Los jets son lluvias de partículas colimadas, conformadas principalmente por hadrones, pero también por fotones y leptones. Debido a su alta tasa de producción, los jets se han vuelto objetivo de estudio para "redescubrir" procesos esperados del modelo estándar y garantizar que los detectores se comporten correctamente{cite}`Marshall:1308447`. A continuación se se explicará la formación de jets a partir de colisiones protón-protón (*pp*).

Al colisionar dos protones altamente energéticos, existe una alta tasa de probabilidad de formación de jets. Un diagrama de la formación de un jet se encuentra en la {numref}`jets-desarrollo` y los procesos que intervienen se explican a continuación{cite}`HARRIS_2011,Beresford:2642397`.

El proceso principal es la **dispersión fuerte**: los protones colisionan a altas energías, produciéndose una interacción con alta transferencia de momento $Q$ entre los constituyentes o partones de los protones. Por la libertad asintótica, los partones se comportan como partículas libres y la teoría de perturbación es válida. En la dispersión fuerte se puede crear una partícula resonante de corta vida o puede suceder un proceso de QCD estándar ({numref}`jets-qcd`). Luego, se generan otras partículas mediante decaimientos o procesos de QCD.

También se consideran procesos de **radiación de estado inicial** (ISR) y **radiación de estado final** (FSR): las partículas entrantes y salientes pueden radiar otras partículas. 

Por último, están los **eventos subyacentes** (UE), que son las interacciones entre partones que no participan en la dispersión fuerte y que pueden generar otras partículas.

```{figure} ./../../figuras/jets-qcd.png
---
width: 500px
name: jets-qcd
---
Diagramas de Feynmann que representan la producción de dos jets en colisiones hadrónicas por procesos de QCD, construidos a partir de los vértices permitidos {cite}`Mangano:2674114`.
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
A pesar de ser un proceso complejo, en primera aproximación, las propiedades cinemáticas de un jet son las mismas que las del parton original.