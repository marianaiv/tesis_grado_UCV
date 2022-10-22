(datos)=
# Conjuntos de datos
El estado final de las LHCO 2020 estuvo enfocado en múltiples jets. Los eventos se generaron utilizando *Pythia*{cite}`Sj_strand_2015`, *Herwig++*{cite}`B_hr_2008` y *Delphes*{cite}`de_Favereau_2014`. Pythia y Herwig++ son programas para la generación de eventos de colisión en HEP, categorizados como generadores de eventos Monte Carlo de propósito general. Delphes simula la respuesta de un detector multipropósito, explicado en la {numref}`det`.

Cada evento está compuesto por una lista de todos los hadrones y su cinemática ($p_T,\eta,\phi$), con posibilidad de obtener hasta 700 hadrones por evento. En caso de tener la etiqueta para el tipo de evento (señal o fondo), esta se encuentra en la última columna. Todos los eventos tienen al menos un jet anti-*kt* con $R=1.0$, pseudorapidez $|\eta|<2.5$ y momento transversal $p_T > 1.2$ TeV.

En este trabajo utilizamos los conjuntos de datos abiertos de las LHCO 2020 conocidos como R&D{cite}`gregor_kasieczka_2019_2629073` y la caja negra 1{cite}`kasieczka_gregor_2019_4536624`, descritos a continuación.

## Conjunto de datos R&D
Este es el conjunto de datos proporcionado para investigación y desarrollo (R&D, por sus siglas en inglés) de los métodos de aprendizaje automático. Se utiliza para analizar los datos y entrenar modelos supervisados, es decir, contiene una etiqueta que define si un evento es señal (1) o es fondo (0). 

Esta compuesto por 1,000,0000 de eventos dijet de QCD, o eventos de fondo, y 100,000 eventos de BSM, o de señal, $Z'\rightarrow XY$ con $X\rightarrow q\bar{q}$ y $Y\rightarrow q\bar{q}$, donde $Z'$, $X$ y $Y$ son partículas BSM. Un diagrama de el evento de señal se encuentra en la {numref}`datos-RnD`. 

```{figure} ./../../figuras/lhco-RnD.png
---
width: 300px
name: datos-RnD
---
Diagrama de Feynmann para la señal del conjunto R&D y la BB1. Producción del bosón $Z'$ de física BSM y su decaimiento a las partículas $X$ y $Y$ de física BSM. Estas últimas, decayendo a jets.
```
Las masas de las partículas $Z'$, $X$ y $Y$ son 3.5 TeV, 500 GeV y 100 GeV, respectivamente. 

Los eventos de este conjunto de datos se produjeron utilizando Pythia y Delphes.

## Caja negra 1 (BB1)
Este conjunto de datos posee la misma señal que el conjunto R&D, pero con masas para $Z'$, $X$ y $Y$ de 3.823 TeV, 732 GeV y 378 GeV. Contiene 1,000,000 de eventos, de los cuales 834 son señal.

Los eventos de fondo en la caja negra 1 son diferentes a los del conjunto R&D. Algunas configuraciones de Pythia y Delphes difieren de las utilizadas para producir los datos del conjunto R&D, y se encuentran descritas en {cite}`Kasieczka_2021`.

El objetivo de este conjunto de datos, que contiene una señal similar a la del conjunto R&D pero con masas distintas, es probar los algoritmos desarrollados utilizando el conjunto R&D, para asegurar que puedan hacer búsquedas generales independientes de modelo.