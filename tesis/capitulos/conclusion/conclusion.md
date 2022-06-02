# Conclusión
En el curso de este trabajo se trataron tres temas principales: el uso de aprendizaje automático para la clasificación de eventos de nueva física, comparación de algoritmos de clasificación binaria y reproducibilidad científica.

De acuerdo a los resultados obtenidos, Los modelos implementados de `scikit-learn` y `TensorFlow` presentan un rendimiento bueno para ser implementaciones sencillas con poco ajuste de parámetros. Esto demuestra la gran capacidad del aprendizaje automático para la tarea de clasificación de eventos.

A nivel general, los modelos supervisados presentan un mejor rendimiento que los no supervisados. Sin embargo, observamos que al clasificar un conjunto de datos con un evento de nueva física ligeramente distinto al evento en el conjunto de datos que se utiliza para entrenar los algoritmos, y con menor densidad de eventos de señal, un modelo no supervisado más complejo puede obtener mejores resultados.

De los modelos implementados para este trabajo, el modelo MLP obtuvo mayores puntajes en la clasificación del conjunto R&D y GBC en la clasificación del conjunto BB1. Para ambos conjuntos KMeans obtuvo los menores resultados.

De los modelos de las olimpiadas LHC 2020, GAN-AE tiene mayores puntajes que UCluster para ambos conjuntos. Incluyendo todos los modelos comparados, GAN-AE tiene el mayor puntaje de los modelos no supervisados al clasificar el conjunto R&D, pero menor puntajes que todos los modelos supervisados. Sin embargo, para el conjunto BB1, GAN-AE posee un mejor resultado en general. UCluster posee un menor puntaje en general.

Sin embargo, es evidente que se necesitan estudiar las métricas existentes, y desarrollar nuevas, para obtener una comparación más realista de las herramientas de aprendizaje automático al realizar la tarea de clasificación particular que se realiza al buscar nueva física. Como se discutió anteriormente, y de acuerdo a {cite}`valassi_2019`, las métricas que se han utilizado hasta ahora para comparar algoritmos de clasificación binaria, como la curva ROC, son de limitada relevancia para el estudio de estos métodos en HEP.

Con respecto a la reproducibilidad, los resultados de ambos modelos fueron sencillos de obtener, a pesar de no tener la información de las versiones de las librerias. Sin embargo, al no tener la configuración exacta de UCluster, no se garantiza que el resultado obtenido en este trabajo coincida con el obtenido en {cite}`Kasieczka_2021`, lo que puede explicar su bajo rendimmiento.

La falta de información respecto a otros modelos no permitió su uso en este trabajo, evidenciando que la reproducibilidad en el desarrollo de los métodos de aprendizaje automático para su uso en HEP es una característica necesaria para poder estudiar con mayor profundidad, y seguir desarrollando, el uso de estas herramientas.