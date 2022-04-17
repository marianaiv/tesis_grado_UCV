(rpd)=
# Reproducibilidad
En 1973, Robert Merton describió el ethos de la ciencia moderna a través de cuatro características principales{cite}`merton_storer_1973`:
- **Universalismo**: las pretensiones de verdad, cualquiera que sea su fuente, deben estar sujetas a criterios impersonales preestablecidos, en consonancia con la observación y con el conocimiento previamente confirmado.
- **Comunismo**: los hallazgos de la ciencia son producto de la colaboración social y se asignan a la comunidad.  El derecho del científico a "su propiedad" intelectual se limita al reconocimiento y la estima que, si la institución funciona con un mínimo de eficiencia, es más o menos proporcional a la importancia del aporte al fondo común de conocimiento.
- **Desinterés**: la pasión por el conocimiento, la curiosidad ociosa, la preocupación altruista por el beneficio de la humanidad y una multitud de otros motivos especiales se han atribuido al científico.
- **Escepticismo organizado**: el escepticismo organizado es un mandato metodológico e institucional. El investigador científico no preserva la división entre lo que exige un respeto acrítico y lo que puede ser analizado objetivamente.

Desde entonces, el panorama científico ha evolucionado. Hoy en día, el proceso de investigación y experimentación se lleva a cabo por redes complejas de equipos y comunidades de todas partes el mundo, involucrando a una gran cantidad de personas. Sólo en 2020, más de 2.9 millones de artículos de ingeniería e investigación científica fueron publicados mundialmente{cite}`white_2021`. Además, por la disponibilidad de recursos computacionales y de grandes cantidades de datos, se han creado nuevas formas de hacer investigación científica{cite}`NAP25303`. 

Esta evolución trajo consigo retos para mantener los ethos de la ciencia moderna. En particular, ha habido un foco de interés en los problemas relacionados con la reproducibilidad científica{cite}`Baker2016`. Tomando en cuenta la gran cantidad de publicaciones y las nuevas maneras de hacer investigación, es necesario estudiar las formas más eficientes de diseñar estudios y comunicar resultados para permitir que sean fácilmente comprobables o refutables, y que puedan servir como base para el desarrollo de nuevos conocimientos.

(rpd-definicion)=
## Definición y beneficios
La definición y los criterios de reproducibilidad varían ampliamente entre las distintas áreas de investigación{cite}`nature_2016`. Para efectos de este trabajo, utilizaremos la definición y criterios de reproducibilidad considerados por [The Turing Way](https://the-turing-way.netlify.app/welcome.html){cite}`the_turing_way_community_2021_5671094`:
> Un resultado es reproducible cuando los pasos de un análisis específico realizados en un mismo conjunto de datos producen consistentemente la misma respuesta.

*The Turing Way* es un manual para hacer ciencia de datos de forma reproducible, ética y colaborativa. Su objetivo es proporcionar la información necesaria para que los investigadores puedan realizar trabajos fáciles de reproducir y reutilizar. Es un proyecto de código abierto (todo el código utilizado es público), de colaboración abierta (cualquier persona puede colaborar), e impulsado por la comunidad.

Hacer investigación reproducible es necesario para el desarrollo del conocimiento ya que:
- La evidencia de un resultado se fortalece si puede ser reproducido y confirmado por investigadores independientes.
- Un trabajo reproducible permite que otras investigaciones utilicen más fácilmente el análisis y los resultados para desarrollar conocimiento nuevo.
- La transparencia también permite mayor colaboración y mayor complejidad en los análisis.

(rpd-investigacion)=
## Investigación reproducible
Dependiendo del tipo de investigación hay distintas consideraciones que se deben tomar para hacerla reproducible. A continuación, describiremos los criterios de reproducibilidad pertinentes para este trabajo.

Particularmente, se toma un enfoque de **investigación abierta**, lo que implica que el desarrollo y los pasos de la investigación deben estar *públicamente disponibles*, ser *trasparentes* y *reutilizable*.

El registro del desarrollo de la investigación se hace mediante el *control de versiones*. Controlar versiones es una manera de registrar los cambios hechos en un archivo de manera cronológica. En desarrollo de software es común utilizar Git para este propósito, un sistema de control de versiones de código abierto y gratuito.

Pas que esté públicamente disponible los datos utilizados, el código desarrollado, y los resultados obtenidos deben ser accesibles de manera fácil y gratuita. En este proyecto se publican utilizando [GitHub](https://github.com), una plataforma de internet para el alojamiento de desarrollo de software y el control de versiones usando Git.

Controlar las versiones y publicar cada uno de los pasos de la investigación es un buen inicio para lograr transparencia. Sin embargo, es necesario proporcionar *documentación* acerca de la información publicada. La documentación engloba los metadatos necesarios para entender el contenido de cada paso de la investigación. Específicamente, es necesario incluir información sobre los datos, instrucciones sobre cómo usar el código y pasos a seguir que se utilizaron para obtener los resultados. 

A nivel de desarrollo de software, la trasparencia y reutilizabilidad requieren consideraciones sobre la *calidad del código*. Es decir, el código debe ser escrito siguiendo continuamente parámetros preestablecidos, debe estar comentado y se deben desarrollar pruebas para comprobar su funcionamiento. Además, el entorno computacional en el que se llevó a cabo la investigación debe capturarse de tal manera que otros puedan replicarlo. El objetivo es que cualquier persona o ente que quiera reproducir los resultados o utilizar el código pueda hacerlo fácilmente.

Por último, ninguna investigación es reutilizable si no posee una *licencia*. Sin licencia todos los derechos pertenecen al autor, es decir, nadie puede usar, copiar, distribuir o modificar el trabajo sin consentimiento. Una licencia da información acerca de las condiciones de uso de cada parte de la investigación.

Existen distintas licencias según el tipo de contenido{cite}`choosealicense`. Para este proyecto se escogieron dos tipos de licencia, una para el software desarrollado y otra para los documentos. Para el software se utiliza una licencia [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.en.html), que permite el uso y modificación libre del código, siempre y cuando se utilice de manera abierta y bajo la misma licencia{cite}`GNUv3`. El resto del proyecto está licenciado bajo [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/deed.es), que permite la distribución y modificación del contenido, indicando si se realizaron modificaciones y dando crédito de manera apropiada{cite}`CCby4`.

(rpd-barreras)=
## Barreras para la reproducibilidad
A pesar de que hacer investigación reproducible es beneficioso para la comunidad científica, existe poco incentivo a nivel académico para llevarla a cabo. 
- Al publicar todos los pasos de una investigación hay mayor posibilidad de que alguien pueda encontrar errores. Compartir errores no es incentivado por la academia, por lo que puede ser difícil decidir hacer ciencia abierta.
- El sesgo hacia la publicación de hallazgos positivos o estadísticamente significativos{cite}`nature_noevidence` implica que muchas investigaciones, al no obtener el resultado deseado, son descartadas, desincentivando el proceso de documentación.
- Las investigaciones reproducibles pueden ser revisadas más a profundidad en el proceso de revisión por pares, por lo que pueden estar sujetas a mayores estándares.
- El sistema de promoción académica suele recompensar investigaciones novedosas. Publicar la investigación puede ser contraproducente para obtener financiación y promoción ya que facilita que otras investigaciones hagan el mismo trabajo.

Otras barreras están relacionadas a retos técnicos. Por ejemplo, en el área ciencia de datos, la complejidad del análisis y el alto volumen de almacenamiento de los datos dificultan el proceso de documentar y publicar toda la información necesaria para reproducir exactamente un resultado. Además, la tecnología evoluciona rápidamente, por lo que puede ser difícil reproducir resultados que se obtuvieron utilizando software que puede no ser compatible con nuevas herramientas. 

Por último, algunas barreras comunes percibidas por los investigadores también dificultan la decisión de hacer investigaciones reproducibles. Existe la percepción de que requiere un mayor esfuerzo y toma más tiempo, y que es necesario aprender habilidades adicionales. Sin embargo, este tiempo y esfuerzo se compensa con todas las facilidades que proporcionan los métodos de reproducibilidad.