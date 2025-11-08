## Proyecto 1B

### todo gracias a [palladian](https://github.com/palladian1)

### Instalación en Linux

- Asegúrate de tener una cadena de herramientas de compilación compatible; si estás en Linux, `gcc` debería funcionar perfectamente.
- Instala `qemu-system-x86` (puede llamarse `qemu-system-i386` o `qemu-system-x86_64`; ten en cuenta que en algunas distribuciones, `qemu` es el paquete incorrecto).
- Instala Perl.
- Instala gawk.
- Instala expect.
- Crea un directorio `src/` en el mismo directorio que el script de prueba del proyecto.
- Clona el repositorio de GitHub de xv6 y copia el código fuente en tu directorio `src/`.
- Dentro de `src/`, ejecuta `make qemu-nox` para probar si xv6 está funcionando. Sal de xv6 con `Ctrl-a x`; si olvidas esto, también puedes terminar el proceso de qemu. Vale la pena verificar `top` o `htop` para asegurarte de que qemu ya no se está ejecutando; a veces puede seguir funcionando después de que sales y consumir muchos recursos.
- Modifica el `Makefile` para establecer `CPUS := 1`.
- Ejecuta `make qemu-nox` de nuevo para probar que xv6 todavía funciona.

### Instrucciones

- Tu tarea es crear una nueva llamada al sistema para xv6, `getreadcount()`, que devolverá el número de llamadas al sistema `read` que se han realizado previamente. Ten en cuenta que el contador debe ser global, no un contador por proceso.

### Enfoque Sugerido

- Descarga el PDF del código fuente de xv6 (está mejor organizado allí que en el código que descargaste). Lee el índice para entender cómo se numeran las hojas, páginas y líneas. Luego, echa un vistazo a las referencias cruzadas para saber cómo encontrar partes del código si lo necesitas.
- Echa un vistazo (muy) rápido a las porciones del código fuente de xv6 listadas bajo `processes` y `system calls` en el índice, así como a `usys.S` en la sección de `user-level`. No te preocupes por entenderlo todavía; solo necesitas ver dónde está cada archivo en el PDF para poder seguir el video de discusión más tarde, ya que el código del profesor tiene una estructura de directorios diferente a la tuya.
- Mira el video de la discusión 2 sobre el Proyecto P1B y síguelo con tu copia en PDF del código de xv6. Anótalo mientras el profesor explica qué hace cada parte.
- Lee la sección de antecedentes enlazada en la página de GitHub del proyecto, anotando el PDF del código de xv6.
- Lee el PDF de xv6 una vez más, esta vez para obtener una comprensión general de las secciones `processes` y `system calls`, así como de `usys.S` y `user.h` (NOTA: este último no está incluido en el PDF de xv6, así que tendrás que mirar el código real que descargaste). No te preocupes por entender hasta la última línea de código, solo asegúrate de saber dónde se definen las llamadas al sistema, cómo se invocan, etc.
- Modifica el código fuente de xv6 para añadir la nueva llamada al sistema `getreadcount()`. Necesitarás modificar varios archivos; sugiero marcar tus modificaciones con `// OSTEP project` para que sea fácil encontrarlas más tarde para la depuración.
- Hay otro lugar donde tendrás que añadir código, que no está incluido en el PDF de xv6: `user.h`.
- Una vez que hayas terminado, ejecuta el script de prueba. La prueba 1 ejecuta una función que hará varias llamadas a `read` y luego llama a `getreadcount`. Para que tu código funcione, debes llevar un seguimiento correcto del número total de llamadas `read` realizadas por todos los procesos.
- Si tu código pasa la prueba 1, ¡felicidades! Has terminado por ahora. No te preocupes por la prueba 2 hasta que hayas visto las clases sobre concurrencia.
- Si tu código no pasó la prueba 1, puedes comparar la salida esperada en `tests/1.out` con la salida real de tu prueba en `tests-out/1.out`. También puedes mirar `tests-out/1.err` para verificar si hay mensajes de error.
- También puedes probar tu código cargando xv6 en tu terminal con `make qemu-nox`. Escribe `ls` para ver todos los archivos; deberías ver `test_1` y `test_2`. Ejecuta la prueba 1 con `./test_1` para ver lo que imprime; puedes compararlo manualmente con la salida esperada.
- Una vez que hayas visto las clases sobre hilos, concurrencia y bloqueos: la prueba 2 verifica si tu implementación de `getreadcount` es segura para hilos. Probablemente no lo era antes, así que para solucionarlo, tendrás que añadir un bloqueo. Luego puedes ejecutar el script de prueba de nuevo y verificar que tu código ahora pasa ambas pruebas.
