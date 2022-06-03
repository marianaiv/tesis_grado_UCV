(discusion)=
# Discusión de resultados

En el capítulo anterior, se presentó la clasificación realizada por distintos modelos de aprendizaje automático, y la comparación con los algoritmos participantes de las LHCO 2020, UCluster y GAN-AE. A continuación, se analizarán los resultados obtenidos.

## Clasificación
Como se observa en la {numref}`clas-feature-imp`, las variables más importantates para la clasificación de eventos, de acuerdo a los algoritmos RFC y GBC, son la variable de subestructura $\tau$ y el $p_T$, de los dos jets principales, $\Delta R$ y el número de hadrones del evento. Que estas variables sean relevantes para la clasificación es positivo, porque nos interesa que los modelos puedan diferenciar la señal del fondo por características que no sean inherentes de una señal en específico. 

Un mayor $p_T$ de los jets es característica natural de una partícula de nueva física masiva, al igual que una distancia angular $\Delta R$ más angosta ({numref}`datospp-vardiff-RnD`). Sin embargo, igualmente se limita la clasificación a partículas nuevas que decaigan a otras partículas masivas, de manera que los eventos de señal posean menos hadrones (como se observa en la {numref}`rawdata-nhadrones`), y señales cuyos jets posean una estructura de dos o más subjets, que son las que coinciden con un menor valor de subjettiness. 

Las variables menos relevantes son $\phi$ y $\eta$ de ambos jets, que son las que presentan menos diferencias entre señal y fondo de acuerdo a la {numref}`datospp-vareq-RnD`. La variable $E$ también se encuentra entre las menos relevantes. Esto se puede deber a que esta variable está correlacionada con $p_T$, pero las distribuciones de $p_T$ de señal y fondo tiene un menor grado de superposisión que las distribuciones de $E$, por lo que son más útiles para distinguir clases.

Las variables más relevantes coinciden para ambos modelos, y da un indicio de los criterios de clasificación de otros modelos. Sin embargo, no significa que estas sean las variables más relevantes para todos los modelos.

Como se mencionó anteriormente, los modelos fueron entrenados utilizando un subconjunto aleatorio del 70% de los eventos del conjunto R&D. Por lo tanto, los resultados obtenidos para el conjunto R&D consisten en el 30% restante. En general, los resultados obtenidos para este conjunto son mejores para los modelos supervisados que para los modelos no supervisados, incluyendo UCluster y GAN-AE.

Al considerar las métricas númericas, observamos que el rendimiento de los modelos varía de acuerdo a la métrica, es decir, no existe un único modelo que posea mayores o menores puntajes de acuerdo a todas las métricas. De acuerdo a la {numref}`comp-metricas-num-RnD`, la exactitud balanceada es mayor para el clasificador de TensorFlow, seguido de MLP, QDA, RFC, UCluster, GAN-AE, KMeans y GBC. Sin embargo, para el puntaje f1, que contiene la precisión y recuperación, el mejor rendimiento resulta del modelo MLP, seguido de RFC, GBC, QDA, el clasificador de TensorFlow, GAN-AE, KMeans y UCluster.

Por otra parte, las métricas gráficas parecen coincidir. De acuerdo a el AUC y la precisión media, el modelo con mejor rendimiento es MLP, seguido del clasificador de TensorFlow, RFC, GBC, QDA y GAN-AE. Los modelos con menores puntajes son UCluster y KMeans. Según el AUC UCluster tiene un mejor rendimiento que KMeans, pero según la precisión promedio KMeans tiene un mejor rendimiento que UCluster.

Sin embargo, es necesario definir cuáles métricas son de mayor importancia en la tarea específica de clasificación de eventos de señal en HEP. Como se discute en {cite}`valassi_2019`, en el problema de clasificación de eventos en HEP los datos son altamente desbalanceados, y a nivel cualitativo también existe un desbalance; la correcta clasificación de eventos de fondo (TN) es irrelevante.  

El considerar esto, implica que cualquier métrica que dependa de TN es de limitada relevancia para comparar los modelos. Si se observa la {numref}`ml-metricas` y la eq. {eq}`ml-exactitudbalanceada`, vemos que la exactitud balanceada considera la efectividad del clasificador para identificar eventos de fondo, ya que incluye la eficiencia de fondo o especificidad. De las métricas gráficas, la curva de eficiencia de señal vs. rechazo de fondo y la curva ROC inversa consideran la eficiencia de señal en alguno de sus ejes y, por ende, el AUC es una métrica basada en la eficiencia de señal.

La curva ROC, además de que icluir los TN, es una métrica no recomendada para tareas de clasificación con datos altamente desbalanceados, debido a que no utiliza ambas columnas de la matriz de confusión{cite}`Fawcett_2004`, es decir, la distribución de clases no afecta la métrica. Esto puede conducir a evaluaciones demasiado optimistas.

Teniendo en cuenta lo anteriormente discutido, entre las métricas númericas, el puntaje f1 es mejor métrica para este problema de clasificación, y entre las métricas gráficas, el gráfico de precisión-recuperación da una evaluación más realista de los modelos. 

En el caso de la clasificación del conjunto R&D, las métricas gráficas concuerdan sobre el rendimiento de los modelos, salvo entre el rendimiento de UCluster y KMeans. Sin embargo, de acuerdo al puntaje f1 y el gráfico de precisión-recuperación, que son las métricas más relevantes para esta tarea, KMeans tiene un mejor rendimiento que UCluster para este conjunto.

Los resultado obtenidos por las métricas concuerdan con lo observado en las distribuciones predichas. De acuerdo a las {numref}, el modelo MLP es el obtiene una distribución más cercana de la señal y KMeans obtiene las distribuciones menos precisas. 

Las distribuciones también nos permiten tener una idea de cómo están clasificando los modelos de las LHCO 2020. De acuerdo con el puntaje f1, el modelo GAN-AE tiene un menor rendimiento que el clasificador de TensorFlow, pero mejor rendimiento que KMeans, por lo que se espera que las distribuciones predichas por GAN-AE sean mejores que las de KMeans, pero distingue menos entre clases que el clasificador de TensorFlow. Igualmente, UCluster tiene un menor puntaje f1 que KMeans, por lo que en las distribuciones predichas por UCluster distinguen menos entre clases.

La clasificación del conjunto BB1 fue, en general, menos exitosa que para el conjunto R&D. De acuerdo a la exactitud balanceada ({numref}`comp-metricasnumericas-BB1`), el modelo con mejor resultado es GAN-AE, seguido de el clasificador de TensorFlow, MLP, KMeans, UCluster, GBC, RDC y QDA. Según el puntaje f1, el modelo que obtuvo el mejor resultado es GBC, seguido de RFC, QDA, GAN-AE, el clasificador de TensorFlow, KMeans, MLP y UCluster. 

De acuerdo a las métricas gráficas ({numref}`comp-metricas-graf-BB1`), GAN-AE tiene un mayor rendimiento que todos los modelos y UCluster es el que posee menor rendimiento. Según el AUC, después de GAN-AE se encuentra MLP, GBC, RFC, el clasificador de TensorFlow, QDA, KMeans y UCluster. Sin embargo, según la precisión promedio, después de GAN-AE se encuentra GBC, el clasificador de TensorFlow, QDA, MLP, RFC, KMeans y UCluster.

De las distribuciones predichas para el conjunto BB1, no es evidente cuál algoritmo realiza una mejor clasificación. Sin embargo, según las distribuciones en la {numref} y el puntaje f1, GAN-AE obtiene una distribución de señal predicha con mejor separación de clases que el modelo de TensorFlow, pero menor que QDA. UCluster obtiene una separación de clases menor que MLP.

## Reproducibilidad
A nivel de reproducibilidad, el material publicado de ambos modelos fue sencillo de utilizar. 

El pre-procesamiento de los datos para UCluster se logra directamente siguiendo las instrucciones dadas por los autores. El problema principal para reproducir los resultados de este modelo es que no proporcionan información del ambiente computacional, específicamente, de las versiones de las librerías utilizadas.

Además, para el entrenamiento y clasificación hay varias configuraciones posibles. Las configuraciones utilizadas para obtener los resultados en {cite}`Kasieczka_2021` no se especifican, por lo que se utilizó la configuración por defecto.

Para GAN-AE, el pre-procesamiento implicó algunas modificaciones al código para que funcionara correctamente. Entre la información proporcionada para reproducir los resultados, tampoco se incluye información sobre las versiones de las librerías utilizadas, lo que dificulta la utilización del código. También se tuvo que escribir un código aparte para realizar la clasificación del conjunto BB1 con etiquetas.