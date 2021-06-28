---
tags: Notas
---

Discusiones tesis de Mariana
===

[Link al github de la tesis](https://github.com/marianaiv/tesis_grado_UCV)

[Link al github del análisis](https://github.com/marianaiv/benchmark_clalgoritmos)
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