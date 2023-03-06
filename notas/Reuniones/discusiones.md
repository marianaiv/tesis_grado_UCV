---
tags: Notas
---

Discusiones tesis de Mariana
===

[Link al github de la tesis](https://github.com/marianaiv/tesis_grado_UCV)

[Link al github del benchmarking](https://github.com/marianaiv/benchmark_clalgoritmos)

## Mayo

### Viernes, 20 de Mayo 2022
#### Participantes
- Camila
- Mariana
#### Agenda
- Aplicación: [Leeds Institute for Data Analytics Data Scientist](https://jobs.leeds.ac.uk/Vacancy.aspx?ref=MHLDA1040)
    - [Cover letter](https://docs.google.com/document/d/1JZSpnR1I-VOonsP5zYLa5rP49UdLxcab2iw71MT5FZ4/edit?usp=sharing)
    - [Supporting Statements](https://docs.google.com/document/d/1g7io0SITLZTb6Qk67GbSYm-lbmB3Y_4u65Dd4-KXSKI/edit?usp=sharing)
    - No entiendo como llenar esto:
        ![](https://i.imgur.com/J2QuWaA.png)
    - Debería agregar aquí los cursos de Coursera?
        ![](https://i.imgur.com/Te3dq9I.png)
    - Completar referees
        ![](https://i.imgur.com/Z0jOG7q.png)

Camila:
    - correo: crangelsmith@turing.ac.uk
    - Position: Senior Data Scientist
    - Tel: +44 7445146454
- 
- Aplicación: Mathematical Physics MSc, The University of Edinburgh
- Tesis
    - Discusión y conclusiones.
    - Introducción, abstract y otros.
    - Correcciones
- Monografía: José Antonio me dijo que tiene que ser con el formato de la facultad
    - Él propone que haga una monografía muy corta y mande a la gente al Jupyter Book
    - Yo propongo pegar todo en el formato y decir que se puede conseguir como Jupyter book
        - O lograr aplicarle la clase cuando hago el rendering del jupyter book a latex
#### Notas

#### Acciones
#### Links relevantes


### Viernes, 6 de Mayo 2022
#### Participantes
- Reina
- Camila
- Mariana
#### Agenda
- Update del documento escrito
#### Notas
- Hablar con José Antonio del formato
#### Acciones
#### Links relevantes
- https://www.chevening.org/scholarship/venezuela/

## Abril

### Viernes, 15-22-29 de Abril 2022

#### Notas
- Reuniones sobre el desarrollo del documento escrito.

### Viernes, 8 de Abril 2022
#### Participantes
- Mariana
- Camila
#### Agenda
- Arreglé el código
    - Resultados BB1
- [Capítulos marco teórico](https://github.com/marianaiv/tesis_grado_UCV/tree/marco-teorico/tesis/capitulos/marco-teorico)
    - Falta: 
        - Terminar machine learning
        - Reproducibilidad
        - LHCO: agrego la comparación de reproducibilidad? [Algoritmos LHCO 2020](/rJUFRvAKTZubT1AzUaaMng) (Tabla resumen)
- Test del pipeline?
#### Notas
#### Acciones
#### Links relevantes

## Marzo

### Viernes, 18 de Marzo 2022
#### Participantes
- Reina
- Camila
- Mariana
#### Agenda
- [Clasificación KMeans](https://github.com/marianaiv/benchmark_clalgoritmos/blob/pipeline/notebooks/16.0-pipeline-KMeans-performance.ipynb) 
- Importar clase de [pipeline](https://github.com/marianaiv/benchtools/blob/pipeline/benchtools/scripts/run.py) a [script](https://github.com/marianaiv/benchtools/blob/pipeline/benchtools/scripts/UCluster_data.py)
- Los modelos de sklearn no se estan guardando entrenados (funcion linea 150 de [run.py](https://github.com/marianaiv/benchtools/blob/pipeline/benchtools/scripts/run.py))
- Las citas de este [capitulo](https://github.com/marianaiv/tesis_grado_UCV/blob/main/tesis/capitulos/marco-teorico/modelo-estandar.md) no salen cuando hago el build
#### Notas
#### Acciones
- A partir 191 que le pasa al objeto en [pipeline](https://github.com/marianaiv/benchtools/blob/pipeline/benchtools/scripts/run.py)
- Asignar el fit a otra variable [pipeline](https://github.com/marianaiv/benchtools/blob/pipeline/benchtools/scripts/run.py)
- Embajada de Francia Calle Madrid c/c Trinidad Las Mercedes Caracas , Venezuela. Téléphone. + 58 212 762 99 76
- campusfrance.caracas@gmail.com
- Revisar las citas en The Turing Way
#### Links relevantes

### Viernes, 11 de Marzo 2022
#### Participantes
- Reina
- Mariana
#### Agenda
- Output del pipeline
    - Agregar algo más?

#### Notas
#### Acciones
- Comenzar a hacer el documento de la tesis
#### Links relevantes

## Febrero

### Viernes, 18 de Febrero 2022
#### Participantes
- Camila
- Mariana
#### Agenda
- UCluster: [notebook](https://github.com/marianaiv/benchmark_clalgoritmos/blob/LHCO-algorithms/notebooks/10.0-UCluster-data.ipynb)
    - Hay que usar --train_full

#### Notas
#### Acciones
- Arreglar la tabla de métricas
#### Links relevantes

### Viernes, 11 de Febrero 2022
#### Participantes

#### Agenda
- Hice los plots con lo que da UCluster: [notebook](https://github.com/marianaiv/benchmark_clalgoritmos/blob/LHCO-algorithms/notebooks/10.0-UCluster-data.ipynb)
    - Arreglé el último error que mandé por mattermost y lo corrí varias veces con algunos cambios (pero igual da todo fondo)
- No entiendo por qué la roc invertida no da bien: comparar fig. 42 [aquí](https://arxiv.org/pdf/2101.08320.pdf) con celda 10 [aquí](https://github.com/marianaiv/benchmark_clalgoritmos/blob/LHCO-algorithms/notebooks/11.0-GAN-AE-data.ipynb)
- Un draft de [El módelo estándar](/AMUD-82yTWeG-SEfrC0F5w)
    - Sugerencias sobre qué más agregar :slightly_smiling_face: 
- Como estructurar el pipeline
    - Algoritmos, entrenamiento, guardar resultados y obtener las métricas
#### Notas
- ROC inversa: escala logarimitmica en el eje y
#### Acciones
#### Links relevantes
- https://github.com/alan-turing-institute/Palaeoanalytics


### Viernes, 4 de Febrero 2022
#### Participantes
- Camila
- Reina
- Mariana
#### Agenda
- Pre-procesamiento GAN-AE
- UCluster: No puedo graficar con los resultados que da
- Backbone de la tesis
#### Notas
- Incluir benchtools en preprocesamiento
- Merge comparación de algoritmos con resultados 
- Incluir busqueda dijet
- Cambiar de lugar reproducibilidad y LHCO
#### Acciones
#### Links relevantes
- https://github.com/alan-turing-institute/rds-course
- https://jupyterbook.org/intro.html

## Enero

### Viernes, 28 de Enero 2022
#### Participantes
- Camila
- Reina
- Mariana
#### Agenda
- Clasificación con KMeans: [09.0-Kmeans-classification.ipynb](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/09.0-Kmeans-classification.ipynb)
- Input y output data de UCluster: [10.0-UCluster-data.ipynb](https://github.com/marianaiv/benchmark_clalgoritmos/blob/LHCO-algorithms/notebooks/10.0-UCluster-data.ipynb)
    - El output de la evaluación con todos los datos me da solo fondo (penultima celda o celda [51])
    - No entiendo max_pool output de UCluster: [script](https://github.com/ViniciusMikuni/UCluster/blob/master/scripts/evaluate_kmeans_seg.py)
- Input y output data de GAN-AE: [11.0-GAN-AE-data.ipynb](https://github.com/marianaiv/benchmark_clalgoritmos/blob/LHCO-algorithms/notebooks/11.0-GAN-AE-data.ipynb)
#### Notas
- Significancia: sig/sqrt{bkg} (curva de probabilidad)
- Intentar utilizar un bumphunter
#### Acciones
#### Links relevantes

### Viernes, 21 de Enero 2022
#### Participantes
- Reina
- Mariana
#### Agenda
- Clasificación con KMeans: [09.0-Kmeans-classification.ipynb](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/09.0-Kmeans-classification.ipynb)
    - Hay que revisar las curvas 
- Input y output data de UCluster: [10.0-UCluster-data.ipynb](https://github.com/marianaiv/benchmark_clalgoritmos/blob/LHCO-algorithms/notebooks/10.0-UCluster-data.ipynb)
    - El output de la evaluación con todos los datos me da solo fondo (penultima celda o celda [51])
- No entiendo max_pool output de UCluster: [script](https://github.com/ViniciusMikuni/UCluster/blob/master/scripts/evaluate_kmeans_seg.py)
- [Pre-procesamiento de GAN-AE](https://gitlab.cern.ch/idinu/lhc-olympics-preprocessing/-/tree/master): dónde definen las variables?
- Distancias euclideas GAN-AE en figura 13 (página 24-27) en el [pdf del paper común](https://arxiv.org/pdf/2101.08320.pdf): se refieren a la mean euclidean distance?
#### Notas
- Agregar significancia
#### Acciones
#### Links relevantes

### Viernes, 14 de Enero 2022
#### Participantes
- Camila
- Mariana
#### Agenda
- Algoritmos de clustering
#### Notas
- PCA: utilizar varianza (95%) para escoger nro. de componentes 
#### Acciones
#### Links relevantes

## Diciembre
### Viernes, 3 de Diciembre 2021
#### Participantes
- Reina
- Camila
- Mariana
#### Agenda
- Update
#### Notas
- Reina en github: camachoreina
#### Acciones
- Correr UCluster en el servidor
- Agregar a Reina al repo
- Hacer los PR pertinentes
#### Links relevantes

## Noviembre
### Viernes, 26 de Noviembre 2021
#### Participantes
- Reina
- Camila
- Mariana
#### Agenda
- Update
#### Notas

#### Acciones
- Escribirle un correo a arturos.cern@gmail.com pidiendole las notas
#### Links relevantes
- https://stackoverflow.com/questions/35545402/how-to-run-an-ipynb-jupyter-notebook-from-terminal
- https://github.com/alan-turing-institute/rds-course

## Octubre

### Viernes, 15 de Octubre 2021
#### Participantes
- Reina
- Mariana
#### Agenda
- Presentación de seminario
#### Notas
- En **busqueda de nueva física**:
    - Varias teorias que resuelven problemas planteados incluyen nuevas resonancia particulas que decaen a jets.
    - En el LHC se producen muchos jets asi que es interesante este tipo de busqueda.
    - Varios análisis que utilizan estas busquedas pero utilizando métodos sencillos.
    - Intentar usar ML para mejorar analisis
- **Reproducibilidad**:
    - Mover LCHO reproducibilidad a antes de reproducibilidad
#### Acciones
- Arreglar presentación
#### Links relevantes
- https://iopscience.iop.org/book/978-0-7503-2112-9/chapter/bk978-0-7503-2112-9ch8

### Viernes, 8 de Octubre 2021
#### Participantes
- Camila
- José Antonio
- Mariana
#### Agenda
- Discutir fecha del seminario
#### Notas
- fecha para seminario: 25 o 26 de octubre 
- api kernel
#### Acciones
#### Links relevantes

## Septiembre 

### Viernes, 17 de Septiembre 2021
#### Participantes
- Reina
- Camila
- Mariana
#### Agenda
- Packaging
- [Plots con los valores no estandarizados](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/GBC-clasificacion.ipynb)
#### Notas
- Volver build_features.py funciones
- Hacer el packaging desde afuera
- [wget de python](https://stackoverflow.com/questions/24346872/python-equivalent-of-a-given-wget-command)
#### Acciones
- Packaging
#### Links relevantes
- https://github.com/alan-turing-institute/Palaeoanalytics/blob/main/setup.py
### Viernes, 10 de Septiembre 2021
#### Participantes
- Camila
- Reina
- Mariana
#### Agenda
- [Correlación de los datos](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/correlacion-data.ipynb)
- [Estructura del repositorio](https://hackmd.io/@marianaiv/rJ6BqE_fF)
    - Cómo ordenar para el packaging 
#### Notas
- Enviar correo preguntando por clave informatique@lpnhe.in2p3.fr
#### Acciones
- Hacer los plots con los datos no estandarizados
#### Links relevantes

### Viernes, 03 de Septiembre 2021
#### Participantes
- Camila
- Mariana
#### Agenda
- [Correlación de los datos](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/correlacion-data.ipynb)
- [Clasificación BB1](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/GBC-clasificacion.ipynb)
- [Pre-procesamiento BB1](https://github.com/marianaiv/benchmark_clalgoritmos/blob/preprocesamiento/scripts/pre-procesamiento.py)
  - Agregué una función para leer los labels como dataframe y concatené los label al dataframe de los datos antes del clustering
- [Estructura para proyectos de ciencias de datos](https://drivendata.github.io/cookiecutter-data-science/)

#### Notas
- Revisar [correlación de los datos](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/correlacion-data.ipynb) con Reina
- Dummy classifier
#### Acciones
- Separar data y fondo para estudiar la correlacion
  - Poner los puntos con alpha mas bajo para poder ver donde se acumulan 
- Ver la correlacion del delta phi de ambos jets y del delta eta
- Agregar la masa a las correlaciones
- Tratar de escribir códico para energy correlation o alguna otra variable de subestructura
- Correr una copia del notebook de comparación sin estandarizar, para poder comparar
- Cursos de la conga: revisar lo del kernel
- Averiguar como hacer las funciones un paquete (revisar links)
#### Links relevantes
- https://github.com/alan-turing-institute/monitoring-ecosystem-resilience/tree/master/pyveg
- https://github.com/alan-turing-institute/Palaeoanalytics

## Agosto

### Viernes, 27 de Agosto 2021
#### Participantes
- Camila
- Mariana
#### Agenda
- [Overfitting](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/GBC-overfitting.ipynb)
- [Otro tipo de ROC](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/comparacion-algoritmos-sencillos.ipynb)
#### Notas
#### Acciones
- Investigar Mean Absolute Error cero
- Investigar sobre variables colineales
  - Feature importance 
- Estandarizar las variables 
- Reorganizar los scripts según pipeline de reproducibilidad
  - How to structure a datascience project
#### Links relevantes

### Viernes, 20 de Agosto 2021
#### Participantes
- Camila
- Mariana
#### Agenda
- [Clasificación con Gradient Boosting](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/GBC-clasificacion.ipynb)
- [Resultados de los algoritmos supervisados](https://hackmd.io/@marianaiv/ByBQASFgK)
- [Distribuciones de mj1 y mj2, constituyentes en log](https://github.com/marianaiv/tesis_grado_UCV/blob/main/Analisis/Analisis_datos_RD.ipynb), etc.
- [Intento de fine tuning](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/fine-tuning-clasificador.ipynb)
  - Da unos warnings con infinitos
-  [ReadMe en scripts](https://github.com/marianaiv/benchmark_clalgoritmos/blob/preprocesamiento/scripts/README.md)
- Tuve que agregarle una excepción a la [función de subjettiness](https://github.com/marianaiv/benchmark_clalgoritmos/blob/preprocesamiento/scripts/subestructura.py) que no está en el [código original](https://github.com/ViniciusMikuni/UCluster/blob/master/scripts/prepare_data_unsup.py)
- Posible [flujo del seminario](https://hackmd.io/@marianaiv/SkNqvgset)?
#### Notas
- Flujo del seminario
  - Olimpiadas: hablar de que es complicado comparar los algoritmos porque no hay métrica estándar
#### Acciones
- Graficar el ROC del 1/eficiencia de señal vs eficiencia de fondo para la comparación de algoritmos sencillos
- Revisar overfitting
- Hacer la clasificación con la BB1
- Utilizar los parametros del fine tuning para comparar
  - Hacer ROC

#### Links relevantes

### Viernes, 14 de Agosto 2021
#### Participantes
- Reina
- Camila
- Mariana
#### Agenda
- Revisar
  - El [script de preprocesamiento](https://github.com/marianaiv/benchmark_clalgoritmos/tree/preprocesamiento)
  - [Grafico para hadrones asociados a cada jet](https://github.com/marianaiv/tesis_grado_UCV/blob/main/Analisis/Analisis_datos_RD.ipynb) y de correlacion de m_jj y nro de hadrones
 - Feature importance
#### Notas
- Arreglar labels plots de distribucion en https://github.com/marianaiv/tesis_grado_UCV/blob/main/Analisis/Analisis_datos_RD.ipynb
- Pensar en algo de preprocesamiento de imagenes

#### Acciones
- Valor máximo de nro. de constituyentes en el jet
  - Ver en escala logaritmica
- Agregar plot de distribución para masa del j1 y j2 
- Revisar los resultados de los algoritmos mas sencillos del paper
- Ver si puedo hacer algo con imagenes
- Aplicar algoritmos no supervisados
- Escribirle a José Antonio
- Arreglar correcciones del resumen

#### Links relevantes

## Julio

### Viernes, 30 de Julio 2021
#### Participantes
- Reina
- Camila
- Mariana
#### Agenda
- [Comparación de algoritmos sencillos](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/comparacion-algoritmos-sencillos.ipynb)
#### Notas

#### Acciones
- Sklearn: ver como entrenar maximizando métricas en específico
- Averiguar qué tan configurable son las funciones de costo
- Qué es el treshole de roc y auc
- Por qué el algoritmo que es mejor es mejor
- Una vez que clasifique, volver a hacer plots de señal y fondo (mjj)
- Importance de los features
- Plot de correlacion mjj y numero de hadrones
- Hadrones asociados a cada jet: ver como sacar ese valor de cada jet
- Arreglar el script de pre-procesamiento
#### Links relevantes

### Viernes, 16 de Julio 2021
#### Participantes
- Reina
- Mariana
- 
#### Agenda
- [Comparación de algoritmos sencillos](https://github.com/marianaiv/benchmark_clalgoritmos/blob/easy-algorithms/notebooks/comparacion-algoritmos-sencillos.ipynb)
  - Qué otros valores estadísticos puedo revisar, de qué otra forma puedo analizar y comparar los algoritmos
- Script de pre-procesamiento
  - No puedo correrlo porque no puedo cargar todo el archivo de datos como en el notebook 
- [Resumen del proyecto](https://docs.google.com/document/d/1nHJRCc5W9etmus8x02Bt9eOsSETJykbXqcvm7RK9fdc/edit?usp=sharing)
- Seminario? 
#### Notas
- Background vs signal efficiency 
- Titulo y objetivo principal: busqueda de nueva física, investigación abierta y reproducible. 
#### Acciones
- Cambios en el resumen
  - Eliminar LCHO del titulo y objetivo principal en el resumen
- Agregar plot de background vs signal efficiency
- Aplicar algoritmos no supervisados
- Revisar iteraciones en scripts de pre-procesamiento
#### Links relevantes


### Viernes, 9 de Julio 2021
#### Participantes
- Camila
- Mariana
#### Agenda
- Discutir acerca del seminario
- Revisar la implementación del decision tree
#### Notas
- Feature importance, specificity ...
#### Acciones
- Pasar el preprocesamiento en script
- Dividir el clustering en dos funciones
- Función de estadisticas principales
- Algoritmos de clasificación de sklearn
  - Logistic regression por ejemplo
  - Bosted decision tree
  - etc 
#### Links relevantes

### Lunes, 5 de Julio 2021

#### Participantes
- Camila (solo por 20m)
- Mariana
- Reina
#### Agenda

### Notas

### Acciones
- Implementar BDT simple
- Intentar usar lo que envió Julia
- Seguir revisando el pre-procesamiento de datos 
- Rellenar la plantilla de TEG de la facultad

#### Links relevantes
- https://gitlab.com/escueladefisicaucv/teg_info

## Junio
### Viernes, 25 de junio 2021
#### Participantes
- Camila
- Mariana
#### Agenda
- Análisis de datos
  - Lo que agregué al análisis de R&D
  - NSubjettiness y EnergyCorrelator
  - Intento de análisis de Black Box 1
#### Notas
- Ejes en mismo rango en señal y fondo
- Celda 32, arreglar plot.
#### Acciones

- Abstraer codigo en funciones 
- Mirar codigo de pyjet a ver si se le puede sacar mas informacion sobre los jets desde el fastjet
- Leer para tener mas ideas sobre otras variables de. Substructure a calcular/graficar: https://arxiv.org/abs/1510.05821
- Crear repositorio para codigo de procesamiento y analysis de datos

#### Links relevantes
- https://github.com/scikit-hep/pyjet/issues/18
- https://github.com/scikit-hep/pyjet/pull/17

### Viernes, 18 de junio 2021
#### Participantes
- Camila
- Reina
- Mariana
#### Agenda
- Discutir sobre el análisis de datos hecho
  - Pyjet no tiene documentación?
  - Qué más podría graficar
- Revisar el resumen de teorias BSM 
#### Notas

- distancia = Sqrt ( (phi1-phi2)^2 + (eta2-eta1)^2 )

#### Acciones

- Usar una muestra mas grande, 10K eventos?
- Calcular % de señal de la muestra total de eventos.
- Hacer figuras normalizadas
- Masa de jet vs pt jet, para señal y fondo
- Numero promedio hadrones para señal y fondo
- Numero promedio de jets para señal y fondo
- pT, eta, phi of the leading hadron, señal y fondo
- La distancia entre los constituyentes de los jets mas energéticos -> esto deberia dartelo fastjet?
- Buscar como obtener con fastjet: Nsubjettiness  y EnergyCorrelator
- Leer para tener mas ideas sobre otras variables de. Substructure a calcular/graficar: https://arxiv.org/abs/1510.05821
 
#### Links relevantes
- [Análisis datos R&D](https://github.com/marianaiv/Tesis_grado_UCV/blob/main/Analisis/Analisis_datos_RD.ipynb)
- [Teorias BSM](https://github.com/marianaiv/Tesis_grado_UCV/blob/main/Notas/teorias_BSM.md)
- [Plot jet areas y ejemplo de input a algorimos]( https://github.com/ndawe/pyjet/blob/master/examples/plot_jet_areas.py)

### Viernes, 11 de junio 2021
#### Participantes
- Mariana
- Camila
- Reina

#### Agenda
- Seguir la discusión sobre los algoritmos que se han corrido
#### Notas
- Como los algoritmos no se pueden correr fácilmente, se va a hacer un análisis de los datos para entender cómo están procesando los datos los algoritmos de la competencia.
#### Acciones
- Analizar los datos en un notebook: hacer plots, entender el clustering.
#### Links relevantes

### Lunes, 7 de junio 2021
#### Participantes
- Mariana
- Camila
- Reina

#### Agenda
- Discutir sobre los algoritmos que he corrido
#### Notas
- Se acordó continuar intentando correr los algoritmos. Sobretodo UCluster que es el que más se ha podido correr.
#### Acciones
- Revisar mas a fondo el algoritmo de UCluster
#### Links relevantes
- [Algoritmos que se han intentado correr](https://hackmd.io/psDFtTXURMq972b1zGuu2w)

## Mayo

### Viernes, 28 de mayo 2021

#### Participantes
- Mariana
- Camila
- Reina
#### Agenda
- Algoritmos del LHCO 2020
#### Notas

#### Acciones
- Escoger algoritmos a utilizar en la tesis

#### Links relevantes
- [Resumen de los algoritmos](https://github.com/marianaiv/Tesis_grado_UCV/blob/main/Notas/overview-algoritmos-LHCO2020.md)
- [Resumen de las olimpiadas](https://github.com/marianaiv/Tesis_grado_UCV/blob/main/Notas/overview-LHCO2020.md)

### Viernes, 21 de mayo 2021

#### Participantes:
- Mariana
- Camila
- Reina

#### Agenda
- Book Dash :)
- Organizar el proyecto
  - Valdría la pena hacer un diseño de proyecto? Como un registered report, quizás no tan formal.
  - Como ordenar github. Gitflow para el programa de benchmarking?
- Comentarios sobre el repositorio.

#### Notas
- Se va a empezar a organizar el proyecto en [github](https://github.com/marianaiv/Tesis_grado_UCV/projects/1)

#### Acciones
- Sprint para estudiar los algoritmos que se usaron en LHC Olympics. Hacernos una presentación. (Crear un issue al respecto)
- Tabla resumen de los algoritmos del LHC Olympics (highlevel) - tipo de algoritmo, referencia (paper, github), breve descripción, quizás plot, CPU power.
- Cost funtion Olympics.
- Investigar qué tipo de física tiene un estado final por el estilo.  

#### Links relevantes
- https://arxiv.org/pdf/1903.10563.pdf
- Este link puede ser util, tiene referencia a papers de ML en HEP en casi todos los metodos que te puedas imaginar https://iml-wg.github.io/HEPML-LivingReview/ (key: "modern reviews" puede ser útil)
### Viernes, 14 de mayo 2021
No hubo reunión por fallas de internet.

### Viernes, 7 de mayo 2021
#### Participantes:
- Camila
- Mariana

#### Agenda
- No hay agenda en este caso, para las próximas reuniones proponemos que Mariana cree una pequeña agenda de qué se quiere discutir.

#### Notas
- Se discutió test de hipótesis y comparación de distribuciones.
- Se acordó empezar a registrar el progreso del proyecto en el repositorio donde va a vivir.
- El curso de Research software engineering va por: [programación funcional](https://github.com/alan-turing-institute/rsd-engineeringcourse/blob/master/ch07dry/020Functional.ipynb).

#### Acciones
- Mariana le va a recordar a JoséO que actualice las láminas de estadística.
- Crear el repositorio abierto principal del proyecto. El repositorio debería tener al menos 3 subdirectorios.
    ```
        - tesis: donde el documento de la tesis va a vivir.
        - notas: donde guardar documentos que se vayan creando.
        - análisis: Donde viviran los notebooks, datos y código que se use para crear resultados para la tesis.```                 
- El repositorio deberia tener un Readme general (que explique el proyecto), y también Readmes de cada sub-directorio (el texto de estos READMES progresará con el tiempo).
- El repositorio debe tener también una licencia.
- Ver el video de OLS para informarse de READMEs y Licencias.
- Crear una tabla con los metodos usados en la LHC Olympics. 
    
#### Links relevantes
- [Video de OLS](
https://www.youtube.com/watch?v=Enn2NGMGC2k&ab_channel=OpenLifeSci).
- [Slides de OLS](https://openlifesci.org/ols-3/schedule/#week-04).

### Template
#### Participantes
#### Agenda
#### Notas
#### Acciones
#### Links relevantes
