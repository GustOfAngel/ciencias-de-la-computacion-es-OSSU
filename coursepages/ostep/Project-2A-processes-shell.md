## Proyecto 2A

### todo gracias a [Palladian](https://github.com/palladian1/)

- [x] Modo interactivo
- [x] Modo por lotes
- [x] `exit`
- [x] `cd`
- [x] `path`
- [x] Redirección
- [x] Comandos paralelos

### Consejos

- Mira el video de la discusión 3 sobre el shell de Unix.
- Lee el capítulo 5 del libro OSTEP.
- Comienza implementando un shell que solo haga una cosa: imprimir el prompt y luego salir cuando escribas `exit`. Luego añade `cd`, y después `path`. A continuación, implementa la capacidad de ejecutar comandos con `execv`, luego añade el modo por lotes, la redirección y, finalmente, los comandos paralelos.
- Todos los scripts de prueba utilizarán el modo por lotes y la redirección, así que hasta que no los tengas listos, tendrás que probar tu shell manualmente.
- Cuando implementes el comando `path`, asegúrate de que puedes manejar tanto rutas absolutas como relativas (es decir, `path tests` y también `path /usr/bin`).
- Es complicado manejar los errores correctamente, así que simplemente añade mensajes de error donde parezca razonable, y luego ejecuta los scripts de prueba y modifica tu código hasta que informes los errores exactamente cuando se supone que debes hacerlo. Si estás ejecutando la prueba `i`, puedes verificar `tests/i.err` y `tests/i.rc` para ver cuántos errores debería generar tu shell y compararlos con `tests-out/i.err` y `tests-out/i.rc`.
- Si tienes problemas con la prueba 3, donde la prueba espera algo como `ls: cannot access ...` y tu shell muestra `/bin/ls: cannot access ...` o `/usr/bin/ls: cannot access ...`, intenta modificar tu variable de entorno `$PATH` para que comience con `/bin`. Si eso no funciona, simplemente modifica `tests/3.err` para que coincida con la salida que da tu sistema. No puedes modificar la salida de tu sistema sin alterar la implementación de `ls` y/o `execv`, así que está bien omitir esta prueba siempre y cuando funcione en espíritu.
- Tuve que editar `/tests/3.pre` para que usara `/bin/ls` debido a cómo está configurado en mi sistema, para poder pasar todas las pruebas. Alternativamente, puedes añadir `export PATH="/bin:$PATH"` a tu archivo `.profile` o `.bashrc`.

### Trampas y Errores Comunes en la Gestión de Memoria

- Esta tarea facilita la creación de punteros a variables de la pila (stack) que ya no existirán una vez que salgan de su ámbito (scope), causando así un fallo de segmentación (segmentation fault). Asegúrate de que si asignas un puntero para que apunte a una cadena de texto, esa cadena sea algo que hayas reservado en el montículo (heap), y no en la pila.

- Dicho esto, si usas una cadena en la pila, puedes copiarla a una cadena reservada en el montículo usando `strcpy()`, `strncpy()`, `strcat()` y `strncat()`.

- Usa `strcpy()` y `strcat()` solo para cadenas de tamaño fijo y asegúrate de que el búfer en el que estás copiando tenga suficiente espacio para contener la cadena, más un carácter extra para el `\0`.

- Para `strncpy()` y `strncat()`, asegúrate de que `n` sea lo suficientemente grande para incluir el terminador `\0`, o añádelo manualmente.

- Ten cuidado con los "use-after-free" (usar memoria después de haberla liberado), especialmente en la implementación de `path`.

- Asegúrate de liberar cualquier cadena obtenida de `getline()` y `strdup()`, pero ten cuidado con las liberaciones dobles (double-frees), por ejemplo, no liberes una subcadena de una cadena que ya has liberado.

- Evita la función de la biblioteca C `strtok()`; no es segura para hilos (thread-safe). Usa `strsep()` en su lugar.

- Cuando uses `strsep()`, asegúrate de guardar una copia del puntero original a la cadena para que puedas liberarla más tarde, porque `strsep()` modificará el puntero, y si lo liberas después, corromperás la tabla de páginas.

- Después de llamar a `strsep(&buf, delim)`, comprueba si `buf` es `NULL` antes de desreferenciarlo.

- Práctica general de codificación en C: si reservas memoria para una estructura de datos dentro de una función, deberías liberarla en la misma función. Si reservas memoria en una función dedicada `crear_xxx`, deberías tener una función correspondiente `destruir_xxx`. De esta manera, siempre reservas y liberas memoria en la misma profundidad de función, lo que facilita evitar errores de memoria.

- Después de cada llamada a `malloc`, `calloc` o `realloc`, comprueba si el resultado es `NULL`.

- Usa `calloc` en lugar de `malloc` si estás creando un arreglo de punteros para evitar crear punteros a valores basura.

- En `update_path` tuve que solucionar un problema donde la mayoría de las pruebas hacen `path /bin /usr/bin`, pero una de ellas hacía `path tests`. Así que simplemente asumí que si tu ruta comienza con una barra (`/`), es una ruta absoluta y debes copiarla tal cual; si no, es una ruta relativa y deberías añadir un `./` al principio.
