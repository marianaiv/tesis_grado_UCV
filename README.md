# Trabajo especial de grado

En este repositorio se encuentra la tesis de grado de Mariana Vivas para la licenciatura en física en la Universidad Central de Venezuela (UCV)

## Contenido del repositorio
El contenido de este repositorio se encuentra organizado de la siguiente forma:
* :bar_chart: [Análisis](Analisis): Datos y código utilizado para obtener los resultados.
* :pencil2: [Notas](Notas): Documentos relacionados con el desarrollo del proyecto. 
* :book: [Tesis](Tesis): Aquí se encuentra el documento de la tesis.

## Proyecto

### Búsqueda de nueva física utilizando técnicas de aprendizaje automático en eventos de múltiples jets: análisis comparativo de algoritmos de clasificación en términos de reproducibilidad y rendimiento
### Objetivos 
* Objetivo general: 
   * Búsqueda de nueva física utilizando jets y aprendizaje automático bajo un concepto de investigación reproducible.  
* Objetivos específicos:  
   * Analizar datos de eventos de múltiples jets de nueva física simulados para las [olimpiadas LHC 2020](https://lhco2020.github.io/homepage/).
   * Aplicar y comparar diferentes algoritmos de clasificación sencillos: supervisados y no supervisados.
   * Analizar comparativamente alguno de los algoritmos de clasificación participantes en las [olimpiadas LHC 2020](https://lhco2020.github.io/homepage/).
   * Desarrollar un programa que caracterice algoritmos de clasificación para eventos de múltiples jets.
   * Hacer una investigación reproducible bajo los lineamientos de [The Turing Way](https://the-turing-way.netlify.app/welcome.html).

### Resumen

**Este proyecto se plantea a partir de la necesidad de buscar nueva física** para responder las preguntas que surgen del modelo estándar. 

El modelo estándar no explica la gravedad, la materia oscura o energía oscura, la masa de los neutrinos, la asimetría materia-antimateria, por qué hay tres generaciones de quarks y leptones o la aparente jerarquía de masas, el valor de la masa del bosón de Higgs, entre otros. Debido a esto, la búsqueda de física más allá del modelo estándar ha sido uno de los ejes principales de investigación en distintos centros de investigación, como en el Gran Colisionador de Hadrones (o LHC por sus siglas en inglés). 

Hasta ahora, la búqueda de nueva física no ha sido exitosa. En el caso particular del LHC, la gran cantidad de datos que se generan y la complejidad de los mismos dificultan su análisis. **Se requiere una herramienta de búsqueda que sea capaz de aprovechar la gran cantidad de datos que se generan y que pueda buscar con cierta independencia de modelo. Las redes neuronales cumplen estas características** y han sido estudiadas en las olimpiadas LHC 2020, utilizando eventos de múltiples jets simulados. 

En la olimpiadas, los participantes desarrollaron algoritmos de clasificación utilizando estas técnicas para la búsqueda de nuevas partículas. Sin embargo, los resultados de los algoritmos no son directamente comparables; no es evidente cuál aproximación da un mejor resultado.

A partir de esto, **se plantea un proyecto en el que se desarrolle una herramienta que proporcione información sobre el rendimiento de algoritmos de clasificación** de eventos de dijets de manera comparativa. El proyecto está divido en dos partes: 
*	El desarrollo de la herramienta de comparación que se utilizará para hacer este análisis.
*	El análisis de algunos algoritmos que participaron en las LHCO 2020 a partir de algunas métricas de reproducibilidad y rendimiento.

Para desarrollar la herramienta de comparación es necesario estudiar la topología de dijet, hacer un análisis de los datos con Python utilizando herramientas de agrupación de jets y la implementación algoritmos sencillos de aprendizaje automático para comparar con los algoritmos escogidos de la competencia. Con esto desarrolla un pipeline que compare los algoritmos sencillos con los resultados reproducidos de los algoritmos de la competencia y luego se utiliza este para hacer el análisis comparativo.

**Se requiere que la investigación se haga de manera reproducible por la naturaleza de los datos y algoritmos a utilizar en el proyecto**, que son open source. Por esto, se siguen los lineamientos planteados en The Turing Way, un manual para hacer ciencia de datos de forma reproducible, ética y colaborativa. Esto permitirá que los resultados obtenidos se puedan utilizar fácilmente, de manera que signifique un aporte útil para esta comunidad y cualquier ente interesado en el estudio de estos métodos.


### Tutores
| Nombre | Role | email | Github | 
| --- | --- | --- | --- |
| Reina Camacho Toro | Investigadora en LPNHE/CNRS  | [reina.camacho@cern.ch](mailto:reina.camacho@cern.ch) | [@camachoreina](https://camachoreina.github.io) |
| Camila Rangel Smith | Científica de datos en El Instituto Alan Turing | [crangelsmith@turing.ac.uk](mailto:crangelsmith@turing.ac.uk) |[@crangelsmith](https://github.com/crangelsmith) |
