<h1 align="center">Trabajo especial de grado</h1>

> En este repositorio se encuentra la [tesis de grado de Mariana Vivas](https://marianaiv.github.io/tesis_grado_UCV/intro.html), requisito parcial para obtener la licenciatura en física en la Universidad Central de Venezuela (UCV)

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC_BY--SA_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

## Contenido del repositorio
El repositorio se encuentra organizado de la siguiente forma:
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

El **trabajo completo** se encuentra en un Jupyter Book publicado en [este link](https://marianaiv.github.io/tesis_grado_UCV/intro.html)

### Tutores
| Nombre | Role | Email | Github | 
| --- | --- | --- | --- |
| Reina Camacho Toro | Investigadora en LPNHE/CNRS  | [reina.camacho@cern.ch](mailto:reina.camacho@cern.ch) | [@camachoreina](https://camachoreina.github.io) |
| Camila Rangel Smith | Investigadora científica de datos en El Instituto Alan Turing | [crangelsmith@turing.ac.uk](mailto:crangelsmith@turing.ac.uk) |[@crangelsmith](https://github.com/crangelsmith) |
| José Antonio López | Universidad Central de Venezuela | [jal.ccs@gmail.com](mailto:jal.ccs@gmail.com) |- |

## Reproducción de resultados
La [comparación de los algoritmos](https://marianaiv.github.io/tesis_grado_UCV/capitulos/resultados/comparacion-algoritmos.html) se realiza utilizando `benchtool`, el paquete de herramientas basado en Python desarrollado para este trabajo. Instrucciones sobre como instalar el paquete y utilizar el pipeline de `benchtools` se encuentran en el archivo README [del repositorio](https://github.com/marianaiv/benchtools).

Específicamente, el pipeline se utilizó para el conjunto R&D de la siguiente forma:
```
benchtools_run --RD --all_data --training --ext_clf ext-RnD.txt --name RnD
```
Y luego para el conjunto BB1:
```
benchtools_run --box 1 --all_data --ext_clf ext-BB1.txt --name BB1
```
## Construcción del Jupyter Book
El documento del trabajo se realizó en un [Jupyter Book](https://jupyterbook.org/en/stable/intro.html). Para usarlo y construirlos se siguen los pasos a continuación:

Primero, hay que clonar el repositorio.
```
git clone https://github.com/marianaiv/tesis_grado_UCV.git
```
Entramos al repositorio.
```
cd tesis_grado_UCV
```
Creamos un ambiente virtual con el archivo eviroment.yml (agregado proximamente*) usando conda y lo activamos.
```
conda env create -f environment.yml
conda activate tesis_UCV
```
Construimos el book:
```
jb build tesis
```

Para construir el documento en latex:
```
git checkout latexpdf
jb build tesis --builder pdflatex
```
## Licencia
El contenido del trabajo escrito está licenciado bajo [Licencia Internacional Pública de Atribución-CompartirIgual 4.0 Internacional](https://creativecommons.org/licenses/by-sa/4.0/legalcode.es).

El código está licenciado bajo [GNU General Public License v3.0 (GNU GPLv3)](https://choosealicense.com/licenses/gpl-3.0/).
