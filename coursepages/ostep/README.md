# Sistemas Operativos: Tres Piezas Fáciles

Créditos para [palladian](https://github.com/palladian1)

## Introducción

Primero, debemos ser francos: es realmente difícil encontrar un buen curso en línea autónomo sobre sistemas operativos. OSTEP es el mejor curso que hemos encontrado hasta ahora. A continuación describimos dos enfoques para el curso, un enfoque "Básico" que es adecuado para la mayoría de los estudiantes, y un enfoque "Ampliado", que es apropiado para estudiantes que desean especializarse en programación de sistemas.

El enfoque "básico" cubre todos los requisitos de nuestro currículo de sistemas operativos y debería tomar aproximadamente 80 horas de trabajo.

El enfoque "ampliado" contiene todo el trabajo del enfoque básico y más. Implica aprender C y ensamblador x86 de manera seria, y profundizar en la programación del kernel. Toma significativamente más tiempo (más de 200 horas) y es mucho más desafiante. Para aquellos estudiantes interesados en esta área de la computación, también es altamente gratificante.

## Enfoque Básico

1. Lee el libro de texto gratuito en línea *Sistemas Operativos: Tres Piezas Fáciles*
2. Completa las preguntas de tarea al final de cada capítulo. (Hay un [repositorio de Github](https://github.com/remzi-arpacidusseau/ostep-homework) asociado para las tareas.)

Esto debería tomar aproximadamente 8 semanas, 10 horas/semana. ¡Eso es todo lo que necesitas hacer!

Necesitarás un sistema Unix/Linux, algunas herramientas básicas de línea de comandos y un compilador C (como GCC o Clang). En Windows, puedes instalar Ubuntu en una máquina virtual o usar WSL (Windows Subsystem for Linux). Mac OS es similar a Unix, por lo que debería ser adecuado para usar.

### Enlaces del Curso

- [Libro](https://pages.cs.wisc.edu/~remzi/OSTEP/)
- [Tareas](https://pages.cs.wisc.edu/~remzi/OSTEP/Homework/homework.html)
- [Repositorio de Código Fuente de Tareas](https://github.com/remzi-arpacidusseau/ostep-homework)
- [Soluciones de Tareas](https://github.com/xxyzz/ostep-hw)

### C

**Pregunta**: Veo algo de código C en este libro. ¿Cuánto C necesito saber?

**Respuesta**: Necesitarás leer y entender algo de código C en este libro. Necesitarás comprensión básica de arreglos, punteros y formateo de impresión. Puedes consultar el libro gratuito [Dive into Systems: Capítulos 1 y 2](https://diveintosystems.org/book/C1-C_intro/index.html). Las [páginas manuales de CS50](https://manual.cs50.io) también son útiles para buscar funciones. No deberías dedicar demasiado tiempo a aprender C.

El código que leerás es bastante simple y presentado en fragmentos cortos. El libro te ayuda bastante introduciendo manualmente muchas API de C como la API de Procesos, la API de Hilos, etc. Puedes escribir, compilar y ejecutar los fragmentos de código, y leer las explicaciones correspondientes. El libro los explica en detalle con un estilo conversacional que es divertido de leer.

También escribirás un poco de código C. Solo una minoría de los capítulos (alrededor de 10 de 50) te piden que escribas algo de código C (mientras que los otros capítulos requieren que ejecutes código de simulación proporcionado y respondas preguntas). Estos suelen ser programas C simples y cortos que imitan el código presentado en ese capítulo, con pequeñas modificaciones.
Cuando estés listo para comenzar las tareas, comienza con el [proyecto reverse](https://github.com/billmei/ostep-projects/tree/billmei/patch-1/initial-reverse), esto será una buena prueba para ver si estás listo para el resto de los proyectos. Para el resto de los proyectos de tareas, usa el enlace bajo los enlaces del curso.

Si te atascas en estos, por favor no dediques demasiado tiempo a ellos. Hay un excelente conjunto de soluciones [aquí](https://github.com/xxyzz/ostep-hw). No hay código de honor para esto, por lo que eres libre de usar las soluciones. Si te das cuenta de que estás dedicando demasiado tiempo, siéntete libre de leer y entender las soluciones en su lugar. Tu prioridad principal debe ser comprender los conceptos de sistemas operativos, no dominar la codificación en C.

## Enfoque Ampliado

Si has elegido esta opción, entonces este es el primer curso en el currículo de OSSU para el cual necesitarás aprender algunos prerrequisitos por tu cuenta antes de comenzarlo, además de los cursos que vienen antes en el currículo. También podrías encontrarte con algunos problemas al ejecutar los scripts para demostraciones de tareas y para probar tus soluciones a los proyectos (aunque esperamos haber resuelto la mayoría de esos problemas para ahora).

Dicho esto, si eres capaz de comprometerte con el tiempo requerido para los prerrequisitos, creemos que la recompensa vale bien la pena: este curso es emocionante, interesante y bastante útil para otros campos de la informática y la programación. Uno de los grandes atractivos de este curso es la oportunidad de ver un sistema operativo simplificado pero completamente funcional tipo Unix en acción y comprender los conceptos y decisiones de diseño que lo respaldan, así como los detalles de implementación de bajo nivel.

Deberías ver todos los videos de las conferencias o leer los capítulos 1 al 47 en el libro de texto (no te preocupes, los capítulos suelen tener solo unas pocas páginas de largo) además de completar los proyectos enumerados a continuación. También recomendamos encarecidamente que hagas los ejercicios de tarea según se asignan en el sitio web del curso o en los capítulos del libro; piensa en ellos como preguntas de "comprueba tu comprensión" que aparecen en medio de los videos de conferencias en sitios como Coursera o edX.

### Prerrequisitos

Esta clase requiere mucha experiencia programando en C. Deberías completar uno de los libros de C enumerados en los [recursos a continuación](#c-1) *antes* de comenzar este curso; si intentas aprender C al mismo tiempo que el material del curso, es probable que te sientas abrumado. Si nunca has usado C antes, deberías esperar dedicar mucho tiempo a esto; es difícil predecir cuánto tiempo podría tomar para cada persona, pero una estimación aproximada podría ser de 8-10 horas por semana durante 3-5 semanas. Siempre puedes aprender C junto con otro curso de OSSU o incluso repetir los ejercicios para otros cursos en C para ganar práctica con él.

También deberías completar ambas partes de Nand2Tetris antes de comenzar este curso. OSTEP se centra en las arquitecturas x86 y x86_64 del mundo real, por lo que tendrás que llenar algunos vacíos para traducir los conceptos que aprendiste en Nand2Tetris a una nueva arquitectura. Puedes hacerlo con los recursos de x86 a continuación, pero ten en cuenta que todos asumen que conoces C, así que aprende eso primero. Esto debería tomar alrededor de 6-8 horas en total.

### Enlaces del Curso

- [Sitio web del curso](https://pages.cs.wisc.edu/~remzi/Classes/537/Spring2018/)
- [Libro](https://pages.cs.wisc.edu/~remzi/OSTEP/)
- [Videos de conferencias](https://pages.cs.wisc.edu/~remzi/Classes/537/Spring2018/Discussion/videos.html)
- [Tareas](https://pages.cs.wisc.edu/~remzi/OSTEP/Homework/homework.html)
- [Repositorio de Código Fuente de Tareas](https://github.com/remzi-arpacidusseau/ostep-homework)
- [Soluciones de Tareas](https://github.com/xxyzz/ostep-hw)
- [Proyectos](https://github.com/remzi-arpacidusseau/ostep-projects)
- [xv6](https://github.com/mit-pdos/xv6-public)

### Hoja de Ruta

Este curso fue originalmente impartido como CS 537 en la Universidad de Wisconsin por el autor del libro de texto OSTEP, por lo que los proyectos se asignan en el curso de acuerdo con los mejores momentos para dar a los estudiantes de UWisconsin acceso a recursos en el campus como secciones de repaso y horas de oficina. Eso significa que no coinciden perfectamente con el material que se cubre en ese momento en las conferencias o capítulos del libro. Recomendamos hacer el curso en el siguiente orden en su lugar.

[Orden de lectura](Reading-order.md)

- Lee los capítulos 1 y 2 del libro de texto OSTEP y mira la primera mitad (la introducción) de la conferencia 1.
- Haz el proyecto `initial-utilities`; está destinado a ser una prueba para asegurarte de que estás lo suficientemente cómodo con C antes de tomar esta clase. Puedes ver la discusión 1 para obtener ayuda. Si te toma más de 2 horas escribir el código (sin contar el tiempo de discusión y cualquier tiempo dedicado a depuración), deberías considerar dedicar más tiempo a aprender C antes de avanzar en el curso. (Si quieres más práctica, también puedes hacer `initial-reverse`, pero no es obligatorio.)
- Mira las conferencias 1 a 5 y lee los capítulos 3 a 24 del libro de texto OSTEP. Recomendamos hacer las tareas según aparecen en el calendario del curso o en los capítulos del libro.
- Mira la discusión 3 y vuelve a leer el capítulo 5, luego haz el proyecto `processes-shell`.
- Lee la guía anotada de xv6 enlazada en la sección de recursos a continuación, comenzando desde el principio y deteniéndote después de la sección `System Calls: Processes`.
- Mira la discusión 2, luego haz el proyecto `initial-xv6`.
- Mira la discusión 5, luego haz el proyecto `scheduling-xv6-lottery`.
- Mira la discusión 7, luego haz el proyecto `vm-xv6-intro`.
- Mira las conferencias 6 a 9 (y opcionalmente, la conferencia de repaso) y lee los capítulos 25 a 34; nuevamente, se recomienda hacer las tareas.
- Mira la discusión 10, luego haz el proyecto `concurrency-xv6-threads`.
- Mira las discusiones 11 y 12, luego haz el proyecto `concurrency-mapreduce`.
- Mira las conferencias 10 a 14 (y opcionalmente, la segunda conferencia de repaso) y lee los capítulos 35 a 47; recuerda hacer las tareas junto con las conferencias o capítulos.
- Haz el proyecto `filesystems-checker`.

### Ejecución de los Proyectos

Este curso fue originalmente impartido como CS 537 en la Universidad de Wisconsin por el autor del libro de texto OSTEP, lo que significa que las tareas y proyectos fueron escritos con esos estudiantes como audiencia objetivo y diseñados para ejecutarse en computadoras de laboratorio de UWisconsin con versiones específicas de software preinstaladas para los estudiantes. Esperamos que esta sección solucione eso para que puedas ejecutarlos en otras computadoras, pero no lo hemos probado en todas las computadoras, así que si encuentras otros problemas, háznoslo saber en el [canal de Discord](https://discord.gg/MJ9YXyV) y trataremos de ayudar.

Para ejecutar las tareas y proyectos en Linux o macOS, necesitarás tener todos los siguientes programas instalados:

- `gcc`
- `gas`
- `ld`
- `gdb`
- `make`
- `objcopy`
- `objdump`
- `dd`
- `python`
- `perl`
- `gawk`
- `expect`
- `git`

También necesitarás instalar `qemu`, pero recomendamos usar la versión parcheada proporcionada por los autores de xv6; consulta [este enlace](https://pdos.csail.mit.edu/6.828/2018/tools.html) para detalles.

En macOS, necesitarás instalar una suite de `gcc` cruzada capaz de producir binarios ELF x86; consulta el enlace anterior para detalles también.

En Windows, puedes usar una máquina virtual de Linux para las tareas y proyectos. Algunos de estos paquetes aún no son compatibles con los ordenadores Apple M1, y el software de máquina virtual aún no se ha portado a la nueva arquitectura del procesador; algunos estudiantes han usado un VPS para hacer las tareas y proyectos en su lugar.

A continuación, clona los repositorios `ostep-homework` y `ostep-projects`:

```sh
git clone https://github.com/remzi-arpacidusseau/ostep-homework/
git clone https://github.com/remzi-arpacidusseau/ostep-projects/
cd ostep-projects
```

Tendrás que clonar [el repositorio `xv6-public`](https://github.com/mit-pdos/xv6-public) en el directorio para cada proyecto de OSTEP relacionado con xv6. Podrías usar la misma copia para todos los proyectos, pero recomendamos usar copias separadas para evitar que proyectos anteriores causen errores en los posteriores. Ejecuta los siguientes comandos en *cada uno* de los directorios `initial-xv6`, `scheduling-xv6-lottery`, `vm-xv6-intro`, `concurrency-xv6-threads` y `filesystems-checker`.

```sh
mkdir src
git clone https://github.com/mit-pdos/xv6-public src
```

### Consejos y trucos para Proyectos

- `initial-reverse`: ¡los mensajes de error que se necesitaban para pasar las pruebas estaban mal! El texto proporcionado decía `"error: ..."` pero las pruebas esperaban `"reverse: ..."` así que asegúrate de coincidir con las expectativas de las pruebas en tu código.
- [consejos y trucos para `processes-shell`](Project-2A-processes-shell.md)
- [consejos para el Proyecto 1B: `initial-xv6`](Project-1B-initial-xv6.md)
- [consejos para `scheduling-xv6-lottery`](Scheduling-xv6-lottery.md)
- [consejos para `vm-xv6-intro`](vm-xv6-intro.md)

### Recursos

#### C

Por favor no intentes aprender C de sitios como GeeksforGeeks, TutorialsPoint o Hackr.io (ni siquiera los enlazaremos aquí). Esos son grandes recursos para otros lenguajes, pero C tiene demasiadas trampas, y los tutoriales de C en línea a menudo están llenos de errores peligrosos y malas prácticas de codificación. Revisamos muchos recursos de C para las recomendaciones a continuación y desafortunadamente encontramos *muchos* malos o inseguros; solo incluiremos los mejores aquí, ¡así que no busques más!

Recomendamos aprender C trabajando a través (en su totalidad) de *Modern C* de Jens Gustedt, que está [disponible gratuitamente en línea](https://inria.hal.science/hal-02383654v2/file/modernC.pdf). Este libro es relativamente corto y te pondrá al día sobre el lenguaje C en sí mismo, así como sobre prácticas modernas de codificación para él. ¡Asegúrate de hacer todos los ejercicios en las notas al pie!

Si bien el libro anterior es nuestra recomendación por defecto, también recomendamos *C Programming: A Modern Approach* de K.N. King como una segunda opción, más amigable para principiantes. Tiene algunas desventajas: es mucho más largo (casi 850 páginas), no está disponible de forma gratuita (y las copias pueden ser difíciles de encontrar) y no es tan reciente como *Modern C* (pero sigue siendo relevante de todos modos). Dicho esto, tiene más ejercicios si deseas práctica adicional, y las secciones de preguntas y respuestas al final de cada capítulo están llenas de perlas de sabiduría en C y respuestas a preguntas frecuentes sobre C. También cubre casi la totalidad del lenguaje C y la biblioteca estándar, por lo que sirve también como libro de referencia.

CS 50 no cubre suficiente C para OSTEP, pero si ya has tomado CS 50, puedes complementarlo con los libros anteriores.

Recursos adicionales (***opcionales***) incluyen:

- [Páginas manuales de CS 50](https://manual.cs50.io): una excelente referencia para buscar funciones de la biblioteca C; la mayoría de las funciones incluyen tanto el manual habitual como una opción "menos cómoda" para principiantes (solo ten en cuenta que la versión "menos cómoda" usa `string` como alias para `char *`.)
- [cdecl](https://cdecl.org): una herramienta para traducir jerigonza de C a inglés.
- [Ruta de C en exercism.org](https://exercism.org/tracks/C): ejercicios de práctica adicionales.
- [Prácticas de Codificación Segura en C y C++](https://www.amazon.com/dp/0321822137): si quieres entender por qué otros recursos de C son tan inseguros.
- *The C Programming Language*: el libro original sobre C de sus creadores. Demasiado antiguo para OSTEP, pero una buena lectura si logras encontrar una copia.

#### Arquitectura x86 y Lenguaje Ensamblador

Nand2Tetris ya ha introducido la mayoría de los conceptos que necesitarás para entender sistemas y arquitecturas de computadoras, así que ahora solo necesitas trasladar ese conocimiento a la arquitectura x86 (de 32 bits) del mundo real.

La forma más fácil de hacerlo es viendo un subconjunto de las conferencias del curso *Computer Systems: A Programmer's Perspective* (o leyendo los capítulos correspondientes en el [libro de texto](https://www.amazon.com/dp/013409266X) del mismo nombre). Las conferencias que necesitarás son:

- [Programación a Nivel de Máquina I: Conceptos Básicos](https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=6e410255-3858-4e85-89c7-812c5845d197)
- [Programación a Nivel de Máquina II: Control](https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=fc93c499-8fc9-4652-9a99-711058054afb)
- [Programación a Nivel de Máquina III: Procedimientos](https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=2994255f-923b-4ad4-8fb4-5def7fd802cd)
- [Programación a Nivel de Máquina IV: Datos](https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=03308c94-fc20-40d8-8978-1a9b81c344ed)
- [Programación a Nivel de Máquina V: Temas Avanzados](https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=3f0bf9ca-d640-4798-b91a-73aed656a10a)
- [Enlazado](https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=0aef84fc-a53b-49c6-bb43-14cb2b175249)

Además, se recomienda hacer los siguientes laboratorios. Estos laboratorios están diseñados para enseñarte cómo trabajar con ensamblador:

- **Bomb Lab**: [Explicación](http://csapp.cs.cmu.edu/3e/bomblab.pdf), [guía de autoestudio](https://csapp.cs.cmu.edu/3e/bomb.tar).
  > Una "bomba binaria" es un programa proporcionado a los estudiantes como un archivo de código objeto. Al ejecutarse, solicita al usuario que escriba 6 cadenas diferentes. Si alguna de estas es incorrecta, la bomba "explota", imprimiendo un mensaje de error y registrando el evento en un servidor de calificaciones. Los estudiantes deben "desactivar" su bomba única desensamblando e ingeniería inversa del programa para determinar cuáles deberían ser las 6 cadenas. El laboratorio enseña a los estudiantes a entender el lenguaje ensamblador, y también los obliga a aprender a usar un depurador. También es muy divertido. Un laboratorio legendario entre los estudiantes de pregrado de CMU.
- **Attack Lab**: [Explicación](http://csapp.cs.cmu.edu/3e/attacklab.pdf), [guía de autoestudio](https://csapp.cs.cmu.edu/3e/target1.tar).
  > A los estudiantes se les da un par de ejecutables binarios x86-64 únicos y personalizados, llamados objetivos, que tienen errores de desbordamiento de búfer. Un objetivo es vulnerable a ataques de inyección de código. El otro es vulnerable a ataques de programación orientada a devolución. Se les pide a los estudiantes que modifiquen el comportamiento de los objetivos desarrollando exploits basados en inyección de código o programación orientada a devolución. Este laboratorio enseña a los estudiantes sobre la disciplina de la pila y les enseña sobre el peligro de escribir código vulnerable a ataques de desbordamiento de búfer. **Nota:** ejecuta los objetivos con la bandera -q para evitar que intenten contactar a un servidor de calificaciones inexistente.

Recursos adicionales (***opcionales***) incluyen:

- [Registros de CPU x86](https://wiki.osdev.org/CPU_Registers_x86): bueno para buscar registros específicos.
- *PC Assembly Language*: un libro corto sobre ensamblador x86.
- [GCC Inline Assembly HOWTO](https://www.ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html): una guía para escribir código ensamblador dentro de un programa C.
- *Intel 80386 Programmer's Reference Manual*: el recurso oficial (y enorme) de Intel.

#### xv6

No necesitas leer nada sobre xv6 hasta después de comenzar OSTEP; de hecho, recomendamos posponer los proyectos relacionados con xv6 hasta que hayas terminado toda la sección sobre virtualización. Después de eso, necesitarás una guía para guiarte a través del código fuente.

Los autores de xv6 proporcionan un [libro](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf) que puedes leer junto con el código fuente. También hay una útil versión [PDF con números de línea](https://pdos.csail.mit.edu/6.828/2018/xv6/xv6-rev11.pdf) del código con un índice para ver exactamente dónde se usa cada función o constante.

Sin embargo, ese libro pasa por alto muchos de los detalles en el código que podrías encontrar desafiantes, incluyendo las características avanzadas de C utilizadas, las instrucciones específicas de la arquitectura x86 y los aspectos de concurrencia (si no has terminado esa sección de OSTEP antes de comenzar los proyectos de xv6). Para resolver este problema, proporcionamos una [guía anotada de xv6](https://github.com/palladian1/xv6-annotated) que recorre todo el código de xv6 y lo analiza línea por línea con explicaciones de las características de C, especificaciones de hardware y convenciones x86 utilizadas. Eso significa que es más largo que el libro oficial de xv6, así que no tienes que leerlo todo (y probablemente puedas omitir las secciones opcionales a menos que te interesen los controladores de dispositivos), pero puedes usarlo como referencia si estás rascándote la cabeza sobre alguna parte del código.

[Aquí](https://github.com/YehudaShapira/xv6-explained) hay otra explicación en profundidad del código xv6.

También [aquí](https://www.youtube.com/playlist?list=PLbtzT1TYeoMhTPzyTZboW_j7TPAnjv9XB) hay una excelente serie de videos que recorre gran parte del código xv6.

#### Misceláneo

Necesitarás una idea general de cómo funcionan los Makefiles para usar el Makefile para xv6. [Este tutorial](https://makefiletutorial.com) cubre mucho más de lo que necesitas; solo lee las secciones "Getting Started" y "Targets" y vuelve al resto más tarde si necesitas buscar algo (pero no deberías tener que hacerlo).

Recursos adicionales (opcionales) incluyen:

- [Opciones de Comando de GCC](https://gcc.gnu.org/onlinedocs/gcc-11.1.0/gcc/Invoking-GCC.html#Invoking-GCC): una guía para banderas de línea de comandos para el compilador GNU C `gcc`.
- [Scripts de Enlazado](https://sourceware.org/binutils/docs/ld/Scripts.html#Scripts): una guía para escribir scripts para el enlazador GNU `ld`.
- [Wiki de OSDev](https://wiki.osdev.org): un gran recurso para todo tipo de conceptos y detalles de implementación de sistemas operativos.
- *Linux Kernel Development*: si quieres aplicar tu conocimiento de xv6 para contribuir al kernel de Linux, esta es una gran lectura después de OSTEP.
