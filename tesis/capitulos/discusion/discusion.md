(discusion)=
# Discusión de resultados

En el capítulo anterior, se presentó la clasificación realizada por distintos modelos de aprendizaje automático, y la comparación con los algoritmos participantes de las LHCO 2020, UCluster y GAN-AE. A continuación, se analizarán los resultados obtenidos.

Como se observa en la {numref}`clas-feature-imp`, las variables más importantates para la clasificación de eventos, de acuerdo a los algoritmos RFC y GBC, son la variable de subestructura $\tau$ y el $p_T$, de los dos jets principales, $\Delta R$ y el número de hadrones del evento. Que estas variables sean relevantes para la clasificación es positivo, porque nos interesa que los modelos puedan diferenciar la señal del fondo por características que no sean inherentes de una señal en específico. 

Un mayor $p_T$ de los jets es característica natural de una partícula de nueva física masiva, al igual que una distancia angular $\Delta R$ más angosta ({numref}`datospp-vardiff-RnD`). Sin embargo, igualmente se limita la clasificación a partículas nuevas que decaigan a otras partículas masivas, de manera que los eventos de señal posean menos hadrones (como se observa en la {numref}`rawdata-nhadrones`), y señales cuyos jets posean una estructura de dos o más subjets, que son las que coinciden con un menor valor de subjettiness. 

Las variables menos relevantes son $\phi$ y $\eta$ de ambos jets, que son las que presentan menos diferencias entre señal y fondo de acuerdo a la {numref}`datospp-vareq-RnD`. La variable $E$ también se encuentra entre las menos relevantes. Esto se puede deber a que esta variable está correlacionada con $p_T$, pero las distribuciones de $p_T$ de señal y fondo tiene un menor grado de superposisión que las distribuciones de $E$, por lo que son más útiles para distinguir clases.




