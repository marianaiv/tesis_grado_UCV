(met)=
# Métricas de rendimiento
Al intentar resolver problemas con aprendizaje automático, es necesario comparar distintos métodos. Esto se hace calculando las métricas de rendimiento mencionadas en la {numref}`ml-metricasderendimiento`. Un resumen de las métricas más comúnes para la tarea de clasificación binaria, y las utilizadas en este trabajo, se presenta a continuación.

(met-num)=
## Métricas numéricas
La métrica de evaluación primaria es la *matriz de confusión*. En esta matriz se resumen el número de etiquetas predichas correctamente e incorrectamente.  

```{table} Matriz de confusión.
:name: ml-matriz-confusion

|                                                           |Clase: **P**ositivos<br>(HEP: **señal** $S_{tot}$)|Clase: **N**egativos<br>(HEP: **fondo** $B_{tot}$)|
|-----------------------------------------------------------|--------------------------------------------------|--------------------------------------------------|
|Clasificado como: **P**ositivos<br>(HEP: **seleccionados**)|**Verdaderos Positivos (TP)**<br>(HEP: señal seleccionada $S_{sel}$)|**Falsos Positivos (FP)**<br>(HEP: fondo seleccionado $B_{sel}$)|
|Clasificado como: **N**egativos<br>(HEP: **rechazados**)   |**Falsos Negativos(FN)**<br>(HEP: señal rechazada $S_{rej}$)|**Verdaderos Negativos (TN)**<br>(HEP: fondo rechazado $B_{rej}$)|
```
La diagonal representa las etiquetas predichas correctamente, mientras que los elementos fuera de la diagonal son las predicciones incorrectas. A partir de los valores de esta matriz se definen el resto de las métricas.

En la {numref}`ml-metricas` se presenta un resumen de las métricas utilizadas comúnmente para clasificación binaria{cite}`SOKOLOVA2009427`.

```{table} Métricas para la clasificación binaria utilizando la notación en la matriz de confusión.
:name: ml-metricas

| Métrica       | Ecuación                                           | Enfoque de evaluación                                               |
|---------------|----------------------------------------------------|---------------------------------------------------------------------|
| Exactitud     | $\frac{TP+TN}{TP+FP+FN+TN}$                        | Número correcto de predicciones sobre todas las predicciones hechas |
| Precisión     | $\frac{TP}{TP+FP}$                                 | Proporción de tasa de verdaderos positivos                          |
| Recuperación  | $\frac{TP}{TP+FN}$                                 | Efectividad del clasificador para identificar etiquetas positivas   |
| Especificidad | $\frac{TN}{TN+FP}$                                 | Efectividad del clasificador para identificar etiquetas negativas   |
| Puntaje f1    | $\frac{(\beta^2+1)TP}{(\beta^2+1)TP+\beta^2FN+FP}$ | Promedio ponderado de precisión y sensibilidad                      |

```
El nombre de las métricas varía en distintas áreas. En HEP, la recuperación y especificidad se conocen como *eficiencia de señal* ($\epsilon_s$) y *rechazo de fondo* ($1-\epsilon_{b}$), respectivamente. La precisión se conoce como *pureza* ($\rho$){cite}`valassi_andrea_2018_1405727`.

Las métricas utilizadas dependen del problema de clasificación. Para datos altamente desbalanceados, se descarta la exactitud ya que puede resultar en valores altos a pesar de estar prediciendo incorrectamente la etiqueta para la clase minoritaria. Sin embargo, se puede utilizar la *exactitud balanceada*:

$$
    \text{Exactitud balanceada}= \frac{\text{eficiencia de señal}+\text{rechazo de fondo}}{2}
$$ (ml-exactitudbalanceada)

(met-plot)=
## Métricas gráficas
Las métricas gráficas más conocidas son la *curva característica de funcionamiento del receptor* (curva ROC) y la *curva precisión-recuperación* (curva PR).

### Curva ROC
Los clasificadores usualmente asignan un puntaje $\mathcal{D}$ de manera que una puntuación más alta significa mayor probabilidad de ser señal. La clasificación discreta se logra escogiendo un *punto de operación*, es decir, escogiendo un umbral de decisión $\mathcal{D}_{thr}$, de manera que todas las muestras $\mathcal{D}\geq\mathcal{D}_{thr}$ se clasifican como positivas, o señal, y todas las demás como negativas, o fondo{cite}`valassi_2019`.

La *curva ROC* se construye graficando la recuperación vs. 1-especificidad para varios umbrales de decisión. En términos de HEP, la eficiencia de señal vs. la eficiencia de fondo. 

```{figure} ./../../figuras/ml-roc.png
---
width: 600px
name: ml-roc
---
Ilustración de la curva ROC. La diagonal representa a un clasificador aleatorio o que no distingue entre clases. En este caso, el clasificador con la curva azul es mejor distinguiendo entre clases. De MartinThoma, CC0, via [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Roc-draft-xkcd-style.svg).
```
El *área debajo de la curva* (AUC) representa la habilidad del clasificador para distinguir entre clases.

$$
    \text{AUC}=\int_0^1\epsilon_s\text{d}\epsilon_b
$$ (ml-auc)

Un valor de AUC de 0.5 indica que la predicción no es mejor que una clasificación aleatoria. Menor a 0.5 indica que el clasificador está clasificando de manera inversa{cite}`Kohl_2012`.

En HEP se utilizan versiones de esta curva. Es común graficar ***eficiencia de señal* vs. *rechazo de fondo***, en vez de la curva ROC clásica, y el AUC se calcula en términos de estas variables. También se suele graficar el ***inverso de la eficiencia de fondo* vs. *eficiencia de señal***.

```{figure} ./../../figuras/ml-otrasroc.png
---
width: 800px
name: ml-otrasroc
---
Ejemplos de otras versiones de la curva ROC. A la izquierda la curvas de eficiencia de señal vs. rechazo de fondo. A la derecha, inverso de la eficiencia de fondo vs. eficiencia de señal. De {cite}`Kasieczka_2021`
```

La curva ROC y el AUC tienen sus limitaciones{cite}`valassi_2019`:
- La comparación de dos curvas ROC que se cruzan no es tan evidente, ya que el AUC se construye como una integral que otorga el mismo peso a todas las partes de la curva. Sin embargo, para la clasificación se escoge un punto específico. En este caso, otras métricas se deben utilizar para definir cuál clasificador proporciona mejor rendimiento en la región donde se elija el umbral de decisión.
- El uso de las curvas ROC puede no ser apropiado para problemas que incluyan datos altamente desbalanceados, debido a que conduce a evaluaciones demasiado optimistas. La curva PR puede ser más informativa en este caso
  
### Curva PR
Para datos altamente desbalanceados se suele sugerir el uso de la curva PR:

> Si la proporción de instancias positivas y negativas en un conjunto de prueba cambia, la curva ROC no cambia. [...]Métricas como la exactitud, la precisión, las curvas de aumento y el puntaje F usan valores de ambas columnas de la matriz de confusión. Cuando la distribución de clases cambia, estas métricas también cambian, incluso si el rendimiento del clasificador no cambia. Las curvas ROC se basan en la tasa de TP y FP, en la cual cada dimensión es una proporción de la columna, por lo que no depende de la distribución de clases.
>
> — ROC Graphs: Notes and Practical Considerations for Data Mining Researchers, 2003{cite}`Fawcett_2004`.

```{figure} ./../../figuras/ml-curvapr.png
---
width: 500px
name: ml-curvapr
---
Ejemplos de curva precisión-recuperación. De {cite}`valassi_andrea_2018_1405727`
```

Análogo al AUC, se utiliza el área bajo la curva PR (AUCPR) y la precisión promedio (AP). La precisión promedio resume la curva PR utilizando la media ponderada de las precisiones logradas en cada umbral, utilizando como peso el aumento en recuperación del umbral anterior{cite}`AP`.

$$
    AP=\sum_n (R_n - R_{n-1})P_n
$$ (ml-precisionpromedio)

donde $P_n$ y $R_n$ son la precisión y la recuperación del umbral enésimo.

### Mejora significativa
Otra medida utilizada regularmente en HEP es la *mejora significativa* definida como:

$$
    \text{Mejora significativa} = \frac{\epsilon_s}{\sqrt{\epsilon_b}}
$$ (ml-mejorasignificativa)

Una mejora significativa = 2 significa que la mejora significativa inicial es amplificada por un factor de 2 después de utilizar la estrategia de clasificación{cite}`Kasieczka_2021`.

Así, se grafica la *mejora significativa* vs. *eficiencia de señal* con el fin de visualizar la mejora significativa del clasificador en múltiples umbrales.

```{figure} ./../../figuras/ml-significancia.png
---
width: 500px
name: ml-significancia
---
Ejemplo de curva de mejora significativa. De {cite}`Kasieczka_2021`
```