(datos)=
# Conjuntos de datos
El estado final de las LHCO 2020 estuvo enfocado en múltiples jets. A pesar de esto, en los conjuntos de datos proporcionan la información de todos los hadrones de cada evento. 

Los eventos se generaron utilizando *Pythia*, *Herwig++* y *Delphes*. Pythia y Herwig++ son programas para la generación de eventos de colisión en HEP, categorizados como generadores de eventos Monte Carlo de propósito general. Delphes simula la respuesta de un detector multipropósito.

Cada evento está compuesto por una lista de todos los hadrones ($p_T,\eta,\phi,p_T,\eta,\phi,\dots$), con relleno de ceros hasta 700 hadrones. En caso de tener la etiqueta para el tipo de evento (señal o fondo), esta se encuentra en la última columna. Todos los eventos tienen al menos un jet anti-kT con $R=1.0$, pseudorapidez $|\eta|<2.5$ y momento transversal $p_T > 1.2$ TeV.

En este trabajo utilizamos el conjunto R&D y el conjunto BB1, descritos a continuación.

## Conjunto R&D
Este es el conjunto de datos proporcionado para investigación y desarrollo (Research & Development). Se utiliza para analizar los datos y entrenar modelos supervisados, es decir, contiene una etiqueta que define si un evento es señal (1) o es fondo (0). 

Consiste en 1,000,0000 de eventos dijet de QCD, o eventos de fondo, y 100,000 eventos de BSM, o de señal, $Z'\rightarrow XY$ con $X\rightarrow q\bar{q}$ y $Y\rightarrow q\bar{q}$. Las masas de las partículas *Z'*, *X* y *Y* son 3.5 TeV, 500 GeV y 100 GeV, respectivamente.

```{figure} ./../../figuras/lhco-RnD.png
---
width: 400px
name: datos-RnD
---
Diagrama de Feynmann para la señal del conjunto R&D y la BB1. Producción del boson *Z'* de física BSM y su decaimiento a las partículas *X* y *Y * de física BSM. Estas últimas, decayendo a jets.
```
Los eventos de este conjunto de datos se produjeron utilizando Pythia y Delphes con la configuración por defecto.

## Caja negra 1 (BB1)
Este conjunto posee la misma señal que el conjunto R&D pero con masas para *Z'*, *X* y *Y* de 3.823 TeV, 732 GeV y 378 GeV. Consiste en 1,000,000 de eventos, de los cuales 834 son señal.

Los eventos de fondo en la caja negra 1 son diferentes a los del conjunto R&D. Algunas configuraciones por defecto de Pythia y Delphes fueron cambiadas.