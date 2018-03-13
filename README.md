## Tabla de contenidos
* [Programa](#programa)
    * [Equipo](#equipo)
    * [Objetivos](#objetivos)
    * [Contenidos](#contenidos)
    * [Metodología](#metodología)
    * [Evaluación](#evaluación)
    * [Bibliografía](#bibliografía)
    * [Política de integridad académica](#política-de-integridad-académica)
* [Proyectos](#proyectos)
* [Wiki](#wiki)
    * [Getting Started](#getting-started)
* [Foro](#foro)
    * [Etiquetas](#etiquetas)
    * [Procedimiento](#procedimiento)

# Programa

## Equipo

### Profesor

| Nombre               | Github        |  Email         |
|:-------------------- |:--------------| :--------------|
| Gabriel Vidal        |  [@gpvidal](https://github.com/gpvidal)| gpvidal@uc.cl |

### Ayudantes

| Nombre                | Github        | Email         |
|:--------------------- |:--------------|:--------------|
| Felipe Garrido        |  [@figarrido](https://github.com/figarrido)| figarrido@uc.cl |
| Felipe Pezoa          |  [@MainScientist](https://github.com/MainScientist)| fipezoa@uc.cl |
| Ignacio Acevedo       |  [@iqacevedo](https://github.com/iqacevedo)| iqacevedo@uc.cl |
| Ignacio Toresano      |  [@itoresano](https://github.com/itoresano)| ijtoresano@uc.cl |


## Objetivos

El objetivo de este curso es que los alumnos conozcan la infraestructura tecnológica sobre la cual descansa la World Wide Web y aprendan a manejar las principales tecnologías que se utilizan para construir sitios y aplicaciones en la plataforma Web. Además se busca entregar una base conceptual suficiente como para que el alumno pueda entender las nuevas tecnologías y propuestas que surgen día a día. Al finalizar el curso los alumnos:
* Conocerán los principales estándares que hacen posible la WWW.
* Conocerán la arquitectura tecnológica de sitios y aplicaciones Web.
* Podrán construir sitios Web con contenido dinámico.
* Podrán construir aplicaciones Web usando diversas tecnologías y herramientas.
* Estarán capacitados para entender y evaluar los méritos de las nuevas tecnologías.

## Contenidos
* Preliminares:
    * Pasado, presente y futuro de la Web
    * La Web como plataforma de desarrollo
    * Arquitectura de una aplicación Web típica (modelo MVC)
    * Lenguajes y Frameworks para desarrollo Web
* Introducción a NodeJS y koa:
    * Una primera mirada a la plataforma y al framework
    * Introducción al lenguaje de programación JavaScript
    * Presentación de la aplicación que desarrollaremos en clases
* Desarrollo de una aplicación típica:
    * Controladores y Vistas
    * El Protocolo HTTP
    * HTML y templating engines
    * Modelo y ORM
    * Clases, tablas, migraciones
    * Validación de la entrada (*input*)
    * Control de la presentación con CSS
* Una Web de APIs de programación:
    * Introducción a los servicios web
    * REST
    * Diseñando una API Restful
* Aplicaciones web de cliente enriquecido (RIA):
    * JavaScript y el DOM
    * Introducción a frameworks en el lado del cliente
    * AJAX: Mejorando la experiencia del usuario
* Aspectos finales:
    * Introducción a aspectos de seguridad
    * Protocolo seguro HTTPS
    * Aspectos de performance

## Metodología

A lo largo del semestre el profesor desarrolla sistemáticamente ejercicios en clases. Las distintas tecnologías, estándares y técnicas van siendo introducidas a medida que la aplicación se completa, en el momento que se hacen necesarios. Por otra parte, los alumnos trabajan en equipos desarrollando una aplicación propia durante el semestre. Cada cierto número de semanas, los alumnos son evaluados por su grado de avance en el proyecto.
Se espera un trabajo personal significativo por parte de los alumnos, ya sea:
* Lectura y estudio de aspectos específicos del lenguaje y/o del framework.
* Lecturas complementarias que profundizan y amplían lo que se discute en clases.
* Desarrollo del proyecto a lo largo del semestre.

## Evaluación

Se llevarán a cabo tres interrogaciones escritas que cubren el material visto en clases y lo asignado como lectura o estudio personal, más un examen final que cubre todo el material del semestre. Adicionalmente, la nota del examen puede reemplazar a la nota de una de las tres interrogaciones, ya sea se haya rendido o no.
El trabajo práctico en el proyecto será evaluado de la siguiente forma: un 50% de la nota corresponderá al promedio de las evaluaciones periódicas parciales y un 50% corresponderá a la entrega del producto final. Para tener derecho a la entrega final debe acreditarse un avance de al menos un 50% al completar la última evaluación parcial.
La nota final considera las interrogaciones, el examen práctico y el proyecto de la siguiente forma:

* **Nota Teórica: (I1 + I2 + I3 + 2 * Ex - min(I1, I2, I3, Ex)) / 4**
* **Nota Práctica: (Promedio entregas parciales) * 0.5 + (Entrega final) * 0.5**
* **Nota final:**
  * Si notas Teórica y Práctica son mayores o iguales a 4 entonces es el promedio de ambas.
  * En caso contrario, la menor entre ambas
* **Fechas de interrogaciones:**
  * **I1:** 13 de Abril
  * **I2:** 16 de Mayo
  * **I3:** 14 de Junio
  * **Exámen:** 29 de Junio

Durante el semestre podrían haber evaluaciones y/o acividades, con o sin previo aviso, que aunque no serán consideradas directamente en la nota final, podrían significar bonificaciones en alguna de las evaluaciones listadas anteriormente.

## Bibliografía
* JavaScript, NodeJS
    * Haverbeke M. "Eloquent JavaScript, 2nd Ed.: A Modern Introduction to Programming" No Starch Press 2014
    * Crockford D. "JavaScript: The Good Parts" O'Reilly 2008
    * Flanagan D. "JavaScript: The Definitive Guide: Activate Your Web Pages" O'Reilly 2011
    * Simpson, K. "You Don't Know JS" O'Reilly – not yet publushed
    * Cantelon M., Harter M., Holowaychuk TJ, Rajlich N. "Node.js in Action" Manning 2013
    * Quigley E. "JavaScript by Example", Pearson 2011
* Design, HTML, XHTML, CSS, Standards
    * Beaird J. "The principles of beautiful Web Design" Sitepoint 2007
    * Vora P. "Web Application Design Patterns" Morgan Kaufman 2009
    * Niederst J. "Learning Web Design: A Beginner's Guide to (X)HTML, StyleSheets, and Web Graphics", OReilly 2007
    * Zeldman, J. "Designing with Web Standards (3rd Ed)", New Riders 2009
    * McFarland, D. "CSS: The Missing Manual", OReilly 2009
    * Collison, S. "Beginning CSS Web Development: From Novice to Professional" APress 2006
    * Lawson B., Sharp R. "Introducing HTML5", New Riders 2011
    * Keith J. "HTML 5 for Web Designers" A book apart 2011
* Javascript
    * Resig J. "Pro JavaScript Techniques" APress 2006
    * Powers, S. "Learning JavaScript" OReilly 2006
    * Keith, J. "DOM Scripting: Web Design with JavaScript and the Document Object Model" APress 2005

## Política de Integridad Académica

Los alumnos de la Escuela de Ingeniería de la Pontificia Universidad Católica de Chile deben mantener un comportamiento acorde a la Declaración de Principios de la Universidad. En particular, se espera que mantengan altos estándares de honestidad académica. Cualquier acto deshonesto o fraude académico está prohibido; los alumnos que incurran en este tipo de acciones se exponen a un Procedimiento Sumario. Es responsabilidad de cada alumno conocer y respetar el documento sobre Integridad Académica publicado por la Dirección de Docencia de la Escuela de Ingeniería en el SIDING
Específicamente, para los cursos del Departamento de Ciencia de la Computación, rige obligatoria- mente la siguiente política de integridad académica. Todo trabajo presentado por un alumno para los efectos de la evaluación de un curso debe ser hecho individualmente por el alumno, sin apoyo en material de terceros. Por “trabajo” se entiende en general las interrogaciones escritas, las tareas de programación u otras, los trabajos de laboratorio, los proyectos, el examen, entre otros. Si un alumno copia un trabajo, obtendrá nota final 1.1 en el curso y se solicitará a la Dirección de Pregrado de la Escuela de Ingeniería que no le permita retirar el curso de la carga académica semestral. Por “copia” se entiende incluir en el trabajo presentado como propio partes hechas por otra persona
Obviamente, está permitido usar material disponible públicamente, por ejemplo, libros o contenidos tomados de Internet, siempre y cuando se incluya la referencia correspondiente. Lo anterior se entiende como complemento al Reglamento del Alumno de la Pontificia Universidad Católica de Chile Por ello, es posible pedir a la Universidad la aplicación de sanciones adicionales especificadas en dicho reglamento.

# Proyectos

Pueden encontrar toda la información relacionada a los proyectos en la [sección correspondiente](proyecto).

# Wiki
Tendremos mucha información útil en la Wiki del curso, la cual pueden encontrar en el menú superior o haciendo clic [aquí](../../wiki).

## Getting Started
En particular, les sugerimos revisar [esta sección](../../wiki/Getting-Started) en la wiki antes de comenzar con su proyecto.

# Foro

La página de [Issues](../../issues) se utilizará como foro para preguntas.

## Etiquetas

Dentro de Issues, [las entradas se pueden etiquetar dentro de ciertas categorías](https://help.github.com/articles/applying-labels-to-issues-and-pull-requests/) para mantener el orden y facilitar la búsqueda de problemas similares. Una entrada puede tener múltiples etiquetas. Aunque el equipo docente irá etiquetando según corresponda, también puedes adelantarte y clasificar tu progunta en [la(s) categoría(s) que correspondan](../../labels):

* [Material](../../labels/Material): para discutir sobre el material entregado por el equipo docente.
* [Código](../../labels/C%C3%B3digo): sobre métodos, clases, sintaxis, estándares, etc.
* [Enunciado o Entrega](../../labels/Enunciado%20o%20Entrega): sobre el enunciado o situación relacionada a alguna entrega de proyecto.
* [Interrogación](../../labels/Interrogaci%C3%B3n): sobre fechas, contenido, recorreción de interrogaciones, etc.
* [Materia](../../labels/Materia): sobre conceptos y/o temas vistos en clases o fuera de éstas.
* [Duplicada](../../labels/Duplicada): pregunta repetida, se hará referencia a la pregunta original.
* [Packages](../../labels/Packages): Consultas acerca de si se puede utilizar cierto package que no está explícitamente indicado en la Wiki.
* [Git](../../labels/Git): Preguntas relacionadas con `git`
* [Inválida](../../labels/Inv%C3%A1lida): la pregunta no cumple los estándares o viola el procedimiento descrito abajo.
* [Meta-pregunta](../../labels/Meta-Pregunta): pregunta sobre cómo y qué preguntar.
* [Tengo un error](../../labels/Tengo%20un%20error): para preguntar sobre errores o bugs en códigos antes de caer en la desesperación (pero luego de haber buscado apropiadamente en la Web...).

## Procedimiento

Antes de postear:
* Busca en Internet para encontrar la solución.
* Si pasan horas y el problema persiste, entra a [Issues](../../issues).
* Busca si alguien tiene la misma pregunta o problema.
	* Si encuentras un post marcado como resuelto, pero no te satisface la respuesta, puedes comentar la issue y **volver a abrirla**.
* En caso de no encontrar un post que te sirva, lo creas presionando **[New issue](../../issues/new)**.
* Escribe una entrada **explicando bien el problema o pregunta**.
* Publica.

Tanto al publicar como comentar, debes atenerte a las **normas del curso**. Además, debes utilizar **[Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#code)** cuando sea necesario. Por ejemplo, cuando se necesita mostrar código o mensajes de error.

Una vez resuelto el problema, da las **gracias** y **cierra el issue** :smiley:.