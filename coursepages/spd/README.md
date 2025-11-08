# Diseño Sistemático de Programas

Este curso ha sido desarrollado por la UBC y está disponible en edX. Te recomendamos que lo hagas desde la versión archivada en edX.

> Este curso de programación adopta un enfoque único, ya que se centra en aprender un método de programación sistemático en lugar de un lenguaje de programación. Este enfoque práctico te ayudará a canalizar tu creatividad para que puedas programar bien en cualquier lenguaje.

**Enlace del curso (Recomendado):** <https://learning.edx.org/course/course-v1:UBCx+SPD1x+2T2015>

Enlaces alternativos:

- <https://www.edx.org/learn/coding/university-of-british-columbia-how-to-code-simple-data> (Hasta la Semana 6A)
- <https://www.edx.org/learn/coding/university-of-british-columbia-how-to-code-complex-data> (Desde la Semana 6B en adelante)

## Instrucciones

**Nota:** Estas instrucciones son para la versión archivada del curso en edX, que es la que recomendamos. No se aplican a otras versiones del curso.

- El curso no tiene una página de inicio en edX, pero no te preocupes por eso. Abre el [enlace](https://learning.edx.org/course/course-v1:UBCx+SPD1x+2T2015) proporcionado arriba, inicia sesión (si no has iniciado sesión) y luego inscríbete en el curso.
- Trabaja desde la Semana 1A hasta la Semana 6A como se indica en la descripción general del curso. Mira los videos, haz los ejercicios y luego resuelve los problemas del banco de problemas.
- Después de completar la Semana 6A, resuelve el [problema de Space Invaders](https://github.com/ossu/spd-starters/blob/main/final/space-invaders-starter.rkt). Puedes encontrar más instrucciones aquí: [Instrucciones de Space Invaders](space-invaders-instructions.png). Puedes ver una ejecución de muestra del juego [aquí](https://www.youtube.com/shorts/wUg3psZl7vM).
- Luego, trabaja desde la Semana 6B en adelante. Mira los videos, haz los ejercicios y luego resuelve los problemas del banco de problemas.
- Después de eso, mira los videos adicionales en [esta lista de reproducción](https://www.youtube.com/playlist?list=PL6NenTZG6KrqdcyTwGf09uBxjI5pbXuT7).
- Después de completar todos los módulos del curso, resuelve el [problema del TA solver](https://github.com/ossu/spd-starters/blob/main/final/ta-solver-starter.rkt). Encontrarás las instrucciones en el archivo de inicio.
- La pestaña del banco de problemas tiene muchos problemas adicionales. Te sugerimos que los resuelvas todos para mejorar tu comprensión.
- Algunos enlaces a los archivos de inicio en el curso ya no funcionan. Puedes descargar los archivos de inicio desde este repositorio de GitHub: <https://github.com/ossu/spd-starters>. Puedes descargar un archivo zip con todos los archivos de inicio usando [este enlace](https://github.com/ossu/spd-starters/archive/refs/heads/main.zip).
- No podrás enviar tus respuestas para los ejercicios, pero puedes ver sus soluciones haciendo clic en "Mostrar respuesta". Revisa tus respuestas honestamente.
- No podrás enviar los problemas del banco de problemas, pero proporcionan soluciones de muestra. Puedes comparar tu solución con ellas.
- Aunque hay formas de hacer este curso en otros IDEs, te sugerimos que uses Dr. Racket, ya que configurar los archivos de inicio de los problemas para otros IDEs no vale la pena el esfuerzo. 
- Si te quedas atascado en algún punto, no dudes en hacer preguntas. Puedes unirte al chat de OSSU para este curso aquí:
  - Chat para discusiones hasta la Semana 6A: <https://discord.gg/RfqAmGJ>
  - Chat para discusiones desde la Semana 6B en adelante: <https://discord.gg/kczJzpm>

## Notas

- Dr. Racket utiliza por defecto la notación más reciente `#true #false '()`. Puedes configurar Dr. Racket para que use la notación utilizada por el curso haciendo clic en el menú en `Language > Choose Language`. Luego, elige el lenguaje requerido (BSL, ISL u otras variantes). Después, haz clic en "Show details" en la parte inferior izquierda de la ventana. A continuación, elige `true false empty` en el campo "Constant Style". Ejecuta tu archivo de nuevo para asegurarte de que utiliza la nueva configuración.

<img src="change-dr-racket-notation.png" width="600" alt="Diálogo de selección de lenguaje de Dr. Racket" />

- Puedes habilitar el cierre automático de paréntesis, corchetes y comillas. Haz clic en `Edit` en la barra de menú > `Preferences` > ve a la pestaña `Editing` > ve a la sub-pestaña `General Editing` > marca la casilla "Enable automatic parentheses, square brackets, and quotes".

<img src="automatic-parentheses.png" width="600" alt="Habilitar cierre automático de paréntesis" />

- Puedes usar `Ctrl + I` para reindentar todo el archivo.

- Si estás en Windows o Linux, usa `Alt + Retroceso` para eliminar palabras completas.

- Si por alguna razón no puedes ver los videos en edX, puedes verlos en [este canal de YouTube](https://www.youtube.com/@systematicprogramdesign7962/playlists).

## FAQ

### Este curso es aburrido. ¿Puedo saltármelo?

**No.** Este curso puede parecer aburrido al principio, pero te sugerimos que lo sigas. Es un gran curso y probablemente cambiará tu forma de pensar. Muchos estudiantes que encontraron este curso aburrido al principio se convirtieron en fanáticos del curso cuando lo completaron. Ten mucho cuidado. Las primeras partes (especialmente las reglas sobre cómo funciona la evaluación) juegan un papel muy importante en la comprensión de cómo funciona y se ejecuta el código durante el resto del curso.

### ¿Por qué este curso se enseña usando BSL? ¿No tendría más sentido enseñarlo en un lenguaje estándar de la industria?

Esta es una elección intencionada, y aquí está el porqué:

1. Lisp es la lingua franca de los científicos de la computación, es decir, de los investigadores de algoritmos con doctorado. Hay algunas razones buenas y otras meramente históricas para esto, pero es un hecho, así que si quieres leer artículos científicos, querrás saber leer Lisp. BSL es una buena introducción, y francamente, una vez que superas el infierno de los paréntesis y una vez que conoces cualquier Lisp, sabes cómo leerlos todos.

2. Este es el primer curso de ciencias de la computación en la mayoría de los planes de estudio que no se centra en enseñarte a usar un lenguaje. Porque el objetivo de las ciencias de la computación no es enseñarte un lenguaje. Ni enseñarte a programar. Ni enseñarte a ser un ingeniero de software fullstack. Las Ciencias de la Computación son una matemática aplicada muy específica con un amplio uso práctico. Pero si le quitas todo el lenguaje calificativo, son matemáticas. Lo que significa que tienen ciertas reglas generales que son completamente, totalmente independientes de tu lenguaje de implementación.

Este curso está construido en un lenguaje de estudiante desechable, específicamente para que no te centres en el lenguaje y, en su lugar, te centres en lo que estás haciendo con el lenguaje. No nos importa el `public static void main` o el estilo PEP8. Queremos ver formas de estructurar un programa en cualquier lenguaje. Así que no nos centramos en las cosas que hacen único a Java, ni en las cosas que hacen único a Python, sino en las cosas que mejoran el código.

Puede parecer difícil aprender un nuevo lenguaje solo para tomar este curso, pero BSL te libera de tener que preocuparte por el linting de estilo, los problemas de tiempo de ejecución, la compartimentalización del código, la compilación o el entorno de codificación. Es un regalo. Tómalo. Los patrones de diseño ya son lo suficientemente difíciles.

### ¿Por qué hay diferentes versiones del curso, HTC, SPD? ¿Por qué recomiendan la versión archivada?

Hay dos razones por las que la gente hace estos cursos:

- El Conocimiento
- El Certificado

OSSU asume que estás aquí por el conocimiento. Puedes tenerlo gratis. Si lo haces por el conocimiento, no necesitas entregar tu tarea. Solo necesitas hacer la tarea.

Si quieres el reconocimiento de que has hecho la cosa, entonces estás aquí por el certificado. No puedes tener el certificado gratis. Tienes que pagar por él.

No hay razón para que entregues las tareas a menos que lo hagas por el certificado. Si lo estás haciendo, en realidad no puedes obtener un certificado del curso SPD (porque el curso ha expirado), así que estás en el lugar equivocado.

Si quieres un certificado, entonces necesitas tomar "How To Code" y tienes que pagar por él.

Pero no necesitas pagar por nada en OSSU. Te sugerimos que tomes SPD porque el acceso a la información es mejor (porque el curso ha expirado) y es más que suficiente para obtener el conocimiento.

En resumen:

    Si estás aquí por el conocimiento, toma SPD -- es gratis pero inactivo.
    Si estás aquí por el certificado, toma y paga por "How To Code" -- sigue siendo un curso activo.

### ¿Puedo hacer este curso en otro lenguaje de programación?

Este curso está realmente integrado con los lenguajes de programación que utiliza. Te sugerimos que uses el lenguaje especificado por el curso. Aunque los conceptos que aprendes en este curso son aplicables en cualquier lugar, intentar hacer el curso con otro lenguaje no es realmente sensato y solo llevaría a una pérdida de tiempo.

### ¿Puedo usar otro IDE? No me gusta Dr. Racket.

Los programas de este curso incrustan imágenes y bloques de texto enriquecido en el código, lo que significa que los archivos no pueden ser abiertos por otros IDEs. Aunque es posible preparar los archivos de inicio para usarlos con otros IDEs, necesitas Dr. Racket para eso, y el tiempo necesario para hacerlo se puede utilizar mejor en aprender los conceptos que enseña el curso.

### ¿Cómo pruebo funciones que se supone que deben devolver valores aleatorios?

Puedes usar `check-random` para probar esas funciones. Puedes [aprender más sobre ello aquí](https://docs.racket-lang.org/htdp-langs/beginner-abbr.html#(form._((lib._lang%2Fhtdp-beginner-abbr..rkt)._check-random))). Se necesita para el proyecto de Space Invaders.

## Créditos

Los archivos de inicio de los problemas y las instrucciones de Space Invaders fueron tomados del curso ["Systematic Program Design" en edX](https://learning.edx.org/course/course-v1:UBCx+SPD1x+2T2015), licenciado bajo la licencia [CC BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/).
