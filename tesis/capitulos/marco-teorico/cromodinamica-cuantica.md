(qcd)=
# Cromodinámica cuántica
Como se mencionó en la [sección anterior](ms-interacciones), la cromodinámica cuántica (QCD) es la teoría de la interacción fuerte y describe la dinámica de los quarks y gluones. Es una teoría cuántica de campos no-Abeliana asociada al grupo de simetría $SU(3)_C$ y construída en analogía a la electrodinámica cuántica (QED){cite:p}`Sutton2016-eh`.

El boson predicho por la teoría es el gluon. Al igual que el foton, es una partícula no-masiva de espín 1 que interactúa con partículas que poseen *carga de color*. La carga de color es el análogo a la carga eléctrica y es el número cuántico conservado en la teoría. Existen tres tipos de carga para los quarks: rojo, verde y azul (para los anti-quarks: anti-rojo, anti-verde y anti-azul). 

Los gluones poseen carga de color, contrario a los fotones que no poseen carga eléctrica. Existen ocho gluones con superposiciones de cargas de color. Así, los gluones median la interacción fuerte pero también interactúan entre sí, haciendo que el análisis de la QCD sea más complejo. 

Los vértices de interacción permitidos por la cromodinámica cuántica son el acople quark-gluon, $gq\bar{q}$, como se observa en la {numref}`qcd-quarkgluon`:

```{figure} ./../../figuras/qcd-quarkgluon.png
---
width: 300px
name: qcd-quarkgluon
---
Vértice de interacción $gq\bar{q}$. En este vértice en particular, un quark con carga de color rojo ($r$) cambia a un quark con carga de color azul ($b$) emitiendo un gluon rojo-antiazul ($r\bar{b}$){cite:p}`griffiths_1987`.
```
Y los vértices de interacción propia del gluon, que se puede observar en la {numref}`qcd-gluongluon`. La interacción de tres y cuatro gluones, *ggg* y *gggg*, respectivamente.

```{figure} ./../../figuras/qcd-gluongluon.png
---
width: 400px
name: qcd-gluongluon
---
Vértice de interacción permitidos en QCD. De izquierda a derecha, interacción propia de tres y cuatro gluones{cite:p}`griffiths_1987`.
```

En teoría de campos, el acople efectivo de un vertice de interacción es modificado por la interacción{cite:p}`altarelli2005standard`. Como resultado la intensidad de la fuerza depende del cuadri-momento al cuadrado ($Q^2$) entre los participantes. La medida de intensidad de la interacción es la constante de acople de QCD $\alpha_s$($Q^2$). El acople es grande para pequeños valores de $Q$ y disminuye a medida que $Q$ aumenta. Esto se conoce como confinamiento y libertad asintótica, respectivamente.

(qcd-libertadasintotica)=
## Libertad asintótica
La libertad asintótica explica que a altas energías las partículas dentro de un hadron se comportan como libres. El comportamiento de la constante de acople de QCD es contrario al de QED: en QED la constante de acople aumenta en función de *Q*. Para QCD la constante de acople disminuye. La libertad asintótica se refiere a que el acople efectivo disminuye al aumentar $Q^2$ y desaparece asintóticamente ({numref}`qcd-alphas`). Por lo tanto, las interacciones de QCD son débiles para valores grandes de $Q^2$. Esto implica que en regiones donde $Q^2$ es grande, o a distancias pequeñas, $\alpha_s$ es pequeño y la teoría de perturbación puede ser utilizada para calcular observables. 

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
Contrario al concepto de libertad asintótica se encuentra el confinamiento. La fuerza de la interacción, o constante de acople $\alpha_S$, aumenta a largas distancias o pequeñas transferencias de momento $Q$, como se puede observar en la {numref}`qcd-alphas`. Esta propiedad explica la imposibilidad de separar partículas con carga de color, es decir, explica por qué no se observan quarks y gluones libres. También explica que los hadrones se encuentren en estados compuestos de quarks estrechamente unidos y de carga de color neutra. Por ejemplo, al intentar separar un meson neutro conformado por un quark y un anti-quark, la energía crece hasta que se crean pares de quarks y anti-quarks a partir del vacío y se forman nuevos mesones neutros en lugar de obtener quarks libres

El aumento de la constante de acople implica que donde $Q^2$ es pequeño, o a distancias grandes, los cálculos con teoría de perturbación ya no son válidos; esta región se conoce como no-perturbativa.