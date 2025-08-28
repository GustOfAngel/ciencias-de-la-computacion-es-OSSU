# Diseño Sistemático de Programas

Este curso ha sido desarrollado por la Universidad de Columbia Británica (UBC) y está disponible en Edx. Recomendamos realizarlo desde la versión archivada en Edx.

> Este curso de programación tiene un enfoque único, ya que se centra en aprender un método sistemático de programación en lugar de un lenguaje de programación específico. Este enfoque práctico te ayudará a canalizar tu creatividad para que puedas programar bien en cualquier lenguaje.

**Enlace del curso (Recomendado):** <https://learning.edx.org/course/course-v1:UBCx+SPD1x+2T2015>

Enlaces alternativos:

- <https://www.edx.org/learn/coding/university-of-british-columbia-how-to-code-simple-data> (Hasta la Semana 6A)
- <https://www.edx.org/learn/coding/university-of-british-columbia-how-to-code-complex-data> (Desde la Semana 6B en adelante)

## Instrucciones

**Nota:** Estas instrucciones son para la versión archivada del curso en Edx, que recomendamos. No aplican a otras versiones del curso.

- El curso no tiene una página de inicio en Edx, pero no te preocupes por eso. Abre el [enlace](https://learning.edx.org/course/course-v1:UBCx+SPD1x+2T2015) proporcionado anteriormente, inicia sesión (si no has iniciado sesión) y luego inscríbete en el curso.
- Trabaja desde la Semana 1A hasta la Semana 6A según se indica en la descripción general del curso. Mira los videos, realiza los ejercicios y luego resuelve los problemas del banco de problemas.
- Después de completar la Semana 6A, realiza el [problema de Space Invaders](https://github.com/ossu/spd-starters/blob/main/final/space-invaders-starter.rkt). Puedes encontrar instrucciones adicionales aquí: [Instrucciones de Space Invaders](space-invaders-instructions.png). Puedes ver una ejecución de muestra del juego [aquí](https://www.youtube.com/shorts/wUg3psZl7vM).
- Luego, trabaja desde la Semana 6B en adelante. Mira los videos, realiza los ejercicios y luego resuelve los problemas del banco de problemas.
- Después de eso, mira los videos adicionales en [esta lista de reproducción](https://www.youtube.com/playlist?list=PL6NenTZG6KrqdcyTwGf09uBxjI5pbXuT7).
- Después de completar todos los módulos del curso, realiza el [problema del solucionador de asistentes](https://github.com/ossu/spd-starters/blob/main/final/ta-solver-starter.rkt). Encontrarás las instrucciones en el archivo inicial.
- La pestaña del banco de problemas tiene muchos problemas adicionales. Te sugerimos resolver todos para reforzar tu comprensión.
- Algunos enlaces a archivos iniciales del curso ya no funcionan. Puedes descargar los archivos iniciales desde este repositorio de GitHub: <https://github.com/ossu/spd-starters>. Puedes descargar un archivo zip con todos los archivos iniciales usando [este enlace](https://github.com/ossu/spd-starters/archive/refs/heads/main.zip).
- No podrás enviar tus respuestas para los ejercicios, pero puedes ver sus soluciones haciendo clic en "Mostrar respuesta". Verifica tus respuestas honestamente.
- No podrás enviar los problemas del banco de problemas, pero proporcionan soluciones de muestra. Puedes comparar tu solución con ellas.
- Aunque existen formas de realizar este curso en otros IDE, te sugerimos usar Dr. Racket, ya que configurar los archivos iniciales para otros IDE no vale el esfuerzo. 
- Si te quedas atascado en algún lugar, no dudes en hacer preguntas. Puedes unirte al chat de OSSU para este curso aquí:
  - Chat para discusiones hasta la Semana 6A: <https://discord.gg/RfqAmGJ>
  - Chat para discusiones desde la Semana 6B en adelante: <https://discord.gg/kczJzpm>

## Notas

- Dr. Racket usa por defecto la notación más reciente `#true #false '()`. Puedes configurar Dr. Racket para usar la notación utilizada por el curso haciendo clic en la barra de menú en Lenguaje > Elegir lenguaje. Luego elige el lenguaje requerido (BSL, ISL u otras variantes). Después haz clic en "Mostrar detalles" en la parte inferior izquierda de la ventana. Luego elige `true false empty` en el campo "Estilo de constantes". Ejecuta tu archivo nuevamente para asegurarte de que usa la nueva configuración.

<img src="change-dr-racket-notation.png" width="600" alt="El diálogo de elección de lenguaje de Dr. Racket" />

- Puedes habilitar el cierre automático de paréntesis, corchetes y comillas. Haz clic en Editar en la Barra de Menú > Preferencias > Ve a la pestaña Edición > Ve a la subpestaña Edición General > Marca la casilla "Habilitar paréntesis, corchetes y comillas automáticos".

<img src="automatic-parentheses.png" width="600" alt="Habilitar cierre automático de paréntesis" />

- Puedes usar Ctrl + I para reindentar todo el archivo.

- Si estás en Windows o Linux, usa Alt + Retroceso para eliminar palabras completas.

- Si no puedes ver los videos en Edx por alguna razón, puedes verlos en [este canal de YouTube](https://www.youtube.com/@systematicprogramdesign7962/playlists).

## Preguntas Frecuentes

### Este curso es aburrido. ¿Puedo saltármelo?

**No.** Este curso puede parecer aburrido al principio, pero te sugerimos trabajar a través de él. Este es un gran curso y probablemente cambiará la forma en que piensas. Muchos estudiantes que encontraron este curso aburrido al principio se convirtieron en fanáticos del curso para cuando lo completaron. Ten mucho cuidado. Las primeras partes (especialmente las reglas sobre cómo funciona la evaluación) juegan un papel fundamental en la comprensión de cómo funciona y se ejecuta el código para el resto del curso.

### ¿Por qué se enseña este curso usando BSL? ¿No tendría más sentido enseñarlo en un lenguaje estándar de la industria?

Esta es una elección intencional, y estas son las razones:

1. Lisp es la lengua franca de los científicos informáticos -- es decir, investigadores de algoritmos con doctorado. Hay algunas razones buenas y otras meramente históricas para esto, pero es una realidad, por lo que si quieres leer artículos técnicos, vas a querer leer Lisp. BSL es una buena introducción, y francamente, una vez que superes el "infierno de paréntesis" y una vez que conozcas cualquier Lisp, sabrás cómo leerlos todos.

2. Este es el primer curso de ciencias de la computación en el currículo de la mayoría de las personas que no se centra en enseñarte cómo usar un lenguaje. Porque el punto de las ciencias de la computación no es enseñarte un lenguaje. Ni enseñarte a codificar. Ni enseñarte a ser un ingeniero de software fullstack. Las Ciencias de la Computación son una matemática aplicada muy estrecha con usos prácticos de amplio alcance. Pero si quitas todo el lenguaje calificativo, son matemáticas. Lo que significa que tiene ciertas reglas generales que son completamente independientes de tu lenguaje de implementación.

Este curso está construido en un lenguaje estudiantil descartable, específicamente para que no te enfoques en el lenguaje y en su lugar te enfoques en lo que estás haciendo con el lenguaje. No nos importa public static void main ni el estilo PEP8. Queremos ver formas de estructurar un programa en cualquier lenguaje. Así que nos enfocamos no en las cosas que hacen único a Java, y no en las cosas que hacen único a Python, y en su lugar nos enfocamos en las cosas que hacen que el código sea mejor.

Puede parecer difícil aprender un nuevo lenguaje solo para tomar este curso, pero BSL te libera de tener que preocuparte por el linting de estilo o problemas de tiempo de ejecución o compartimentalización de código o compilación o entorno de codificación. Es un regalo. Aceptalo. Los patrones de diseño son lo suficientemente difíciles.

### ¿Por qué hay diferentes versiones del curso, HTC, SPD? ¿Por qué recomiendan la versión archivada?

Hay dos razones por las que las personas realizan estos cursos:

- El Conocimiento
- El Certificado

OSSU asume que estás en ello por el conocimiento. Puedes tener eso gratis. Si estás en ello por el conocimiento, no necesitas enviar tus tareas. Solo necesitas hacer las tareas.

Si quieres el reconocimiento de que has hecho la cosa, entonces estás en ello por el certificado. No puedes tener el certificado gratis. Tienes que pagar por eso.

No hay razón para que envíes conjuntos de tareas a menos que lo hagas por el certificado -- Si estás haciendo eso, en realidad no puedes obtener un certificado del curso SPD (porque el curso está vencido) así que estás en el lugar equivocado.

Si quieres un certificado, entonces necesitas tomar How To Code y necesitas pagar por ello.

Pero no necesitas pagar nada en OSSU. Te sugerimos que tomes SPD porque el acceso a la información es mejor (porque el curso está vencido) y es más que suficiente para obtener el conocimiento.

TL;DR:

    Si estás en ello por el conocimiento, toma SPD -- es gratuito pero inactivo
    Si estás en ello por el certificado, toma y paga por How To Code -- todavía es un curso activo

### ¿Puedo hacer este curso en otro lenguaje de programación?

Este curso está realmente integrado con los lenguajes de programación que utiliza. Te sugerimos usar el lenguaje especificado por el curso. Aunque los conceptos que aprendas de este curso son aplicables en cualquier lugar, intentar hacer el curso con otro lenguaje no es realmente sensato y solo llevaría a un desperdicio de tiempo.

### ¿Puedo usar otro IDE? No me gusta Dr. Racket

Los programas en este curso incrustan imágenes y bloques de texto enriquecido en el código, lo que significa que los archivos no pueden ser abiertos por otros IDE. Aunque es posible preparar los archivos iniciales para su uso con otros IDE, necesitas Dr. Racket para eso, y el tiempo necesario para hacerlo puede ser mejor utilizado en aprender los conceptos enseñados por el curso.

### ¿Cómo pruebo funciones que se supone que producen valores aleatorios?

Puedes usar `check-random` para probar esas funciones. Puedes [obtener más información aquí](https://docs.racket-lang.org/htdp-langs/beginner-abbr.html#(form._((lib._lang%2Fhtdp-beginner-abbr..rkt)._check-random))). Es necesario para el proyecto Space Invaders.

## Créditos

Los archivos iniciales de problemas y las instrucciones de Space Invaders fueron tomados del curso "Diseño Sistemático de Programas" en Edx, licenciado bajo licencia [CC BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/).
