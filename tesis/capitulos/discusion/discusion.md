(discusion)=
# Discusión de resultados

En el capítulo anterior, se presentó la clasificación realizada por distintos modelos de aprendizaje automático, y la comparación con los algoritmos participantes de las LHCO 2020, UCluster y GAN-AE. A continuación, se analizarán los resultados obtenidos.

Como se observa en la {numref}`clas-feature-imp`, las variables más importantates para la clasificación de eventos, de acuerdo a los algoritmos RFC y GBC, son la variable de subestructura $\tau$ y el $p_T$, de los dos jets principales, $\Delta R$ y el número de hadrones del evento. Que estas variables sean relevantes para la clasificación es positivo, porque nos interesa que los modelos puedan diferenciar la señal del fondo por características que no sean inherentes de una señal en específico. 

Un mayor $p_T$ de los jets es característica natural de una partícula de nueva física masiva, al igual que una distancia angular $\Delta R$ más angosta ({numref}`datospp-vardiff-RnD`). Sin embargo, igualmente se limita la clasificación a partículas nuevas que decaigan a otras partículas masivas, de manera que los eventos de señal posean menos hadrones (como se observa en la {numref}`rawdata-nhadrones`), y señales cuyos jets posean una estructura de dos o más subjets, que son las que coinciden con un menor valor de subjettiness. 

Las variables menos relevantes son $\phi$ y $\eta$ de ambos jets, que son las que presentan menos diferencias entre señal y fondo de acuerdo a la {numref}`datospp-vareq-RnD`. La variable $E$ también se encuentra entre las menos relevantes. Esto se puede deber a que esta variable está correlacionada con $p_T$, pero las distribuciones de $p_T$ de señal y fondo tiene un menor grado de superposisión que las distribuciones de $E$, por lo que son más útiles para distinguir clases.

Las variables más relevantes coinciden para ambos modelos, y da un indicio de los criterios de clasificación de otros modelos. Sin embargo, no significa que estas sean las variables más relevantes para todos los modelos.

Como se mencionó anteriormente, los modelos fueron entrenados utilizando un subconjunto aleatorio del 70% de los eventos del conjunto R&D. Por lo tanto, los resultados obtenidos para el conjunto R&D consisten en el 30% restante. En general, los resultados obtenidos para este conjunto son mejores para los modelos supervisados que para los modelos no supervisados, incluyendo UCluster y GAN-AE.

Sin embargo, es necesario definir cuáles métricas son de mayor importancia en la tarea específica de clasificación de eventos de señal en HEP. Como se discute en {cite}, en el problema de clasificación de eventos en HEP, los datos son altamente desbalanceados y a nivel cualitativo también existe un desbalance; la correcta clasificación de eventos de fondo (TN) es irrelevante.  

El considerar esto implica que cualquier métrica que dependa de TN, es de limitada relevancia para comparar los modelos. Si se observa la {numref} y la eq. {eqref}, vemos que la exactitud balanceada considera la efectividad del clasificador para identificar eventos de fondo, ya que incluye la eficiencia de fondo o especificidad. De las métricas gráficas, la curva de eficiencia de señal vs. rechazo de fondo y la curva ROC inversa, consideran la eficiencia de señal en alguno de sus ejes, y por ende, el AUC es una métrica basada en la eficiencia de señal.

De estas variaciones de la curva ROC, además del hecho de que incluyen los TN, se debe tomar en cuenta que, en general, es una métrica no recomendada para tareas de clasificación con datos altamente desbalanceados debido a que no utiliza ambas columnas de la matriz de confusión{cite}, es decir, la distribución de clases no afecta la métrica. Esto puede conducir a evaluaciones demasiado optimistas.

