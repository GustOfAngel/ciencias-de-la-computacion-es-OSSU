# Registro de Cambios

**Nota**: El plan de estudios se encuentra actualmente en revisión para la v9. Esto consiste principalmente en verificar nuestras recomendaciones contra nuestras [pautas curriculares](CURRICULAR_GUIDELINES.md), añadiendo temas que faltan y eliminando cursos redundantes o fuera de alcance. A medida que se completan las Solicitudes de Comentarios en este esfuerzo, los cambios se aplican inmediatamente al plan de estudios. Cuando la revisión general esté completa, anotaremos el aumento de versión a v9.

Todos los cambios notables de este proyecto se documentarán en este archivo.
Este proyecto se adhiere *en espíritu* al [Versionamiento Semántico](http://semver.org/):

- Las actualizaciones "MAJOR" corresponden a cambios en los temas estudiados dentro de una materia.
- Las actualizaciones "MINOR" corresponden a cambios de cursos sin cambiar los temas.
- Las actualizaciones "PATCH" corresponden a adiciones/eliminaciones estéticas y no esenciales o al cambio en el orden de las clases para una mejor progresión.

## [8.0.0] 2017-11-01

### Añadido

- extras/lecturas: "The System Design Primer"
- extras/lecturas: "Category Theory for Programmers: The Preface"
- extras/lecturas: "Programming Languages: Application and Interpretation"
- extras/lecturas: "Programming and Programming Languages"
- CONTRIBUTING: Sección "Aprendiendo Git" a la página de pautas para colaboradores.
- Matemáticas Fundamentales: Se añadió "La Esencia del Álgebra Lineal" como prerrequisito para "Álgebra Lineal: de los Fundamentos a las Fronteras".

### Actualizado

- Se movió "Introducción al Pensamiento Matemático" a extras/cursos.
- Se movió "Hack the Kernel" (ops-class) de Sistemas Avanzados a Sistemas Fundamentales.
- Sistemas Fundamentales: "Sistemas Operativos: Tres Piezas Fáciles" ya no es obligatorio, pero se recomienda como texto complementario a "Hack the Kernel".
- Teoría Fundamental: Se reemplazó Coursera con Lagunita como anfitrión de los Algoritmos de Stanford, ya que Coursera utiliza patrones oscuros para engañar a los usuarios para que paguen.

## [7.2.2] 2017-07-02

### Añadido

- Libro "Haskell Programming from First Principles" como alternativa de pago para aprender Haskell.
- "Think Python" a extras/lecturas.
- Entradas de FAQ y enlaces bajo los cursos relevantes.
- "Category Theory: A Gentle Introduction" a extras/lecturas.

## [7.2.1] 2017-05-14

### Actualizado

- El curso de Redes debería tomar 8 semanas en completarse.
- Se corrigió un error de ortografía.

### Añadido

- Curso de Introducción a Haskell a [extras/cursos](extras/courses.md).

## [7.2.0] 2017-04-28

### Añadido

- Curso de Pruebas de Software.
- Enlace a "Algorithms: Design and Analysis" de Stanford Lagunita.
- Se añadió un enlace a la sección de ecuaciones paramétricas y coordenadas polares del curso de Cálculo de una Variable del MIT para preparar adecuadamente a los estudiantes para el Cálculo Multivariable.

## [7.1.2] 2017-04-22

### Actualizado

- Se añadió un enlace a la "Mega Project List" en la introducción de la sección de Proyectos.

## [7.1.1] 2017-04-11

### Actualizado

- Últimos retoques para el lanzamiento.

## [7.1.0] 2017-04-10

### Actualizado

- Se revirtió el reformateo del curso de lenguajes de programación.

### Añadido

- Cursos de Algoritmos Distribuidos Confiables.
- Nuevo curso de Introducción a CS.

## [7.0.2] 2017-03-30

### Actualizado

- Se movieron los cursos opcionales de aprendizaje en línea a extras/cursos en una nueva sección.
- Se movió el curso alternativo de arquitectura de computadoras a extras/cursos.

### Añadido

- Especialización en Scala bajo Aplicaciones Avanzadas.

### Eliminado

- Se eliminaron todas las opciones excepto una para las lecturas obligatorias para simplificar el plan de estudios.

## [7.0.1] 2017-03-11

### Actualizado

- Se corrigió el enlace a la página de "DIY computer science" de Bradfield.

### Añadido

- Nota bajo "Cálculo Uno" con enlaces a erratas y recomendaciones de progresión del curso.
- Cursos opcionales bajo extras:
  - Curso de Strang sobre álgebra lineal.
  - "Structure and Interpretation of Computer Programs" de Berkeley.
- Lecturas opcionales bajo extras:
  - Libro de programación avanzada de Van Roy.
  - Libro de arquitectura de computadoras de P&H.
  - Libro de algoritmos de Skiena.
  - Libro de álgebra lineal de Strang.
  - Libro de Sistemas de Gestión de Bases de Datos.
  - Libro de Tarr sobre la creación de tu propio Lenguaje de Dominio Específico.
  - Lecturas de varios autores sobre sistemas distribuidos.

## [7.0] 2017-03-09

Revisión completa de la estructura del programa.

### Actualizado

- Se aclararon las pautas para colaboradores y se movieron a un archivo separado.
- Se cambió de muchas materias a solo cuatro materias con muchos temas.
- Se consolidaron free-books.md y paid-books.md en readings.md.
- Se consolidaron free-courses.md y paid-courses.md en courses.md.
- Se reemplazó el antiguo "How to Code" con el nuevo "How to Code" (MicroMasters en Desarrollo de Software).
- Se reemplazaron los Algoritmos de Princeton (movidos a [cursos alternativos](#extras/courses.md)) con los Algoritmos de Stanford.

### Añadido

- Se indicaron los prerrequisitos para todos los cursos.
- Requisitos: requisitos de materia/tema y requisitos de proyecto.
- Lecturas obligatorias sobre Haskell, Prolog, Sistemas Operativos.
- Cursos: "Programming Languages" de Dan Grossman.
- Cursos: De Nand a Tetris.
- Curso electivo: Introducción a la Programación Paralela.
- Curso electivo: LAFF: Programación para la Correctitud.
- Curso electivo: Introducción al Pensamiento Matemático.
- Cursos electivos: Electricidad y Magnetismo.
- Cursos electivos: "Computation Structures" del MIT.
- Curso electivo: Cálculo Multivariable.
- Curso electivo: ops-class.org.
- Curso electivo: Teoría de Autómatas.
- Curso electivo: Introducción a la Lógica.
- Curso electivo: Geometría Computacional.
- Curso electivo: Análisis Formal de Conceptos.
- Curso electivo: Teoría de Juegos.
- Especializaciones electivas:
  - Robótica
  - Minería de Datos
  - Big Data
  - Internet de las Cosas
  - Computación en la Nube
  - Desarrollo Web Full Stack
  - Ciencia de Datos
- Especializaciones profesionales:
  - Dominio del Desarrollo de Software en R
  - Ingeniero de Inteligencia Artificial
  - Ingeniero de Aprendizaje Automático
  - Ciberseguridad
  - Desarrollador de Android

### Eliminado

- Se eliminaron muchos enlaces rotos y cursos obsoletos.
- Se eliminó el requisito de proyecto por curso.
- Curso: Programación Orientada a Objetos en Java.
- Curso: Programación Funcional en Scala.
- Curso: Arquitectura de Computadoras (pero se dejó como nota al pie).
- Curso: Introducción a la Ciencia de la Computación Teórica.
- Curso: Procesos de Software y Prácticas Ágiles.
- Curso: Sistemas Operativos y Programación de Sistemas.
- Curso: Introducción a la Ciberseguridad.
- Curso: Arquitectura y Programación de Computadoras Paralelas.
- Curso: Diseño de UX para Desarrolladores Móviles.

## [6.0] 2016-10-09

### Actualizado

- Se colocó "Cálculo Uno" antes y junto con "Matemáticas para las Ciencias de la Computación".
- Se mejoró el texto en "Orden de las clases".

### Añadido

- Se creó un tablero público de Trello con la nueva versión del plan de estudios.
- Se creó la sección "Cómo seguir y mostrar tu progreso" en "Cómo usar esta guía".
- Se añadió el archivo PROJECTS.md.
- Se copiaron todas las secciones del plan de estudios a PROJECTS.md.

### Eliminado

- Se eliminó la sección "Próximos Objetivos".
- Se eliminó la referencia a la aplicación web de OSSU.

## [5.1.0] 2016-08-20

Actualización a la última versión de "Matemáticas para las Ciencias de la Computación":

### Actualizado

- Sección: **Matemáticas (Matemáticas Discretas)**
  - Matemáticas para las Ciencias de la Computación.

## [5.0.0] 2016-08-20

Debido a un curso eliminado, tuvimos las siguientes actualizaciones:

### Eliminado

- Sección: **Procesamiento de Lenguaje Natural**
  - Procesamiento de Lenguaje Natural.

### Añadido

- Sección: **Procesamiento de Lenguaje Natural**
  - Introducción al Procesamiento de Lenguaje Natural.

## [4.1.0] 2016-08-05

Debido a los cambios en la plataforma de Coursera, tuvimos las siguientes actualizaciones:

### Corregido

- Sección: **Big Data**
  - Introducción a Big Data.

## [4.0.0] 2016-07-30

Debido a los cambios en la plataforma de Coursera, tuvimos las siguientes actualizaciones:

### Eliminado

- Sección: **Teoría**
  - Autómatas.
- Sección: **Matemáticas (Álgebra Lineal)**
  - Coding the Matrix: Linear Algebra through Computer Science Applications.
- Sección: **Computación Paralela**
  - Heterogeneous Parallel Programming.
- Sección: **Procesamiento de Lenguaje Natural**
  - Natural Language Processing.

### Corregido

- Sección: **Redes de Computadoras**
  - Redes de Computadoras.
- Sección: **Compiladores**
  - Compiladores.

### Añadido

- Sección: **Teoría**
  - Introducción a la Ciencia de la Computación Teórica.
- Sección: **Matemáticas (Álgebra Lineal)**
  - Linear Algebra - Foundations to Frontiers.
- Sección: **Computación Paralela**
  - Parallel Computer Architecture and Programming.
- Sección: **Procesamiento de Lenguaje Natural**
  - Natural Language Processing.

## [3.0.0] 2016-05-04

### Eliminado

- Sección: **Introducción a las Ciencias de la Computación**:
  - Introduction to Computer Science and Programming Using Python.
  - From Nand to Tetris (Part 1).

### Añadido

- Sección: **Introducción a las Ciencias de la Computación**:
  - Introduction to Computer Science - CS50.

## [2.0.1] 2016-04-04

### Corregido

- Ahora los estudiantes deben inscribirse a través de nuestra [aplicación web](https://ossu.firebaseapp.com).

## [2.0.0] 2016-03-17

### Corregido

- Nombres y enlaces de los cursos de la sección de Diseño de Programas.

### Eliminado

- **Introducción a las Ciencias de la Computación**:
  - Introduction to Computer Science.
  - Introduction to Computational Thinking and Data Science.
- **Algoritmos**
  - Analysis of Algorithms.
- **Paradigmas de Programación**
  - Principles of Reactive Programming.
- **Matemáticas (Cálculo)**
  - Multivariable Calculus.
- **Arquitectura de Software**:
  - Web Application Architectures.
- **Ingeniería de Software**:
  - Agile Development Using Ruby on Rails - Basics.
  - Agile Development Using Ruby on Rails - Advanced.
  - Startup Engineering.
- **Arquitectura de Computadoras**:
  - The Hardware/Software Interface.
- **Sistemas Operativos**:
  - Operating System Engineering.
- **Redes de Computadoras**:
  - Introduction to Computer Networking.
- **Criptografía**:
  - Applied Cryptography.

**PD**: Estos cursos eliminados ahora se encuentran en la sección de [extras](https://github.com/ossu/computer-science/tree/master/extras).

## [1.3.12] 2016-03-17

### Añadido

- Cómo colaborar: enviar nuevos enlaces a la sección de extras.

## [1.3.11] 2016-03-06

### Corregido

- Nand to Tetris: cambio de nombre y URL.
- UC Berkeley Agile development: cambio de nombre y URL.
- Enlaces directos a especializaciones.

## [1.3.10] 2016-03-06

### Corregido

- Enlace del curso de la Parte 2 de "Diseño Sistemático de Programas".

## [1.3.9] 2015-11-09

### Corregido

- Enlace al curso correcto de Procesamiento de Lenguaje Natural.

## [1.3.8] 2015-11-07

### Añadido

- Se añadió la sección "Sugerencias de Proyectos" con más referencias.

## [1.3.7] 2015-11-01

### Eliminado

- Se eliminó el archivo project.md, movido al repositorio de **ayuda**.

## [1.3.6] 2015-10-22

### Añadido

- Última versión de CS 162, Sistemas Operativos y Programación de Sistemas.

## [1.2.6] 2015-10-19

### Añadido

- Insignia/Enlace a la lista "Awesome".

## [1.2.5] 2015-10-16

### Corregido

- Se corrigió el nombre de la sección y se añadió un hipervínculo.

## [1.2.4] 2015-10-14

### Eliminado

- Se eliminó la cita sobre el compromiso público.

## [1.2.3] 2015-10-12

### Cambiado

- Se actualizó la sección de prerrequisitos para mayor claridad.

## [1.2.2] 2015-10-12

### Corregido

- Nuevo enlace al issue destinado a la inscripción de estudiantes.

## [1.2.1] 2015-10-11

### Añadido

- Artículo "Git - la guía simple" a la sección de prerrequisitos.

## [1.1.1] 2015-10-11

### Corregido

- Se corrigieron errores tipográficos.
  - Como MOOC es un "Massive Open Online Course", "curso MOOC" es redundante.
  - Se elaboró sobre "problema real".
  - Se corrigieron algunos pequeños errores gramaticales y de redacción.

## [1.1.0] 2015-10-08

### Añadido

- Sección de Motivación y Preparación (recursos opcionales)
  - Artículo: MIT Challenge.
  - Curso: Aprendiendo a Aprender.

## [1.0.0] 2015-10-08

Lanzamiento de la primera versión **completa** del plan de estudios de Ciencias de la Computación.