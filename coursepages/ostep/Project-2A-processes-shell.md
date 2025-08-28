## Proyecto 2A

### todo gracias a [Palladian](https://github.com/palladian1/)

- [x] Modo interactivo
- [x] Modo por lotes
- [x] exit
- [x] cd
- [x] path
- [x] Redirección
- [x] Comandos paralelos

### Consejos

- Mira el video de la discusión 3 sobre el shell de Unix.
- Lee el capítulo 5 en el libro OSTEP.
- Comienza implementando un shell que solo haga una cosa: imprima el prompt y luego salga cuando escribas `exit`. Luego añade `cd`, luego `path`. Después implementa la capacidad de ejecutar comandos con `execv`, luego añade el modo por lotes, después la redirección y finalmente los comandos paralelos.
- Todos los scripts de prueba usarán el modo por lotes y la redirección, por lo que hasta que no los hayas implementado, tendrás que probar tu shell manualmente.
- Cuando implementes el comando `path`, asegúrate de poder manejar tanto rutas absolutas como relativas (es decir, `path tests` así como `path /usr/bin`).
- Es complicado obtener los errores correctamente, así que simplemente añade mensajes de error donde parezca razonable, luego ejecuta los scripts de prueba y modifica tu código hasta que estés reportando errores exactamente cuando se supone que debes hacerlo. Si estás ejecutando la prueba `i`, puedes verificar `tests/i.err` y `tests/i.rc` para ver cuántos errores debe generar tu shell y comparar con `tests-out/i.err` y `tests-out/i.rc`.
- Si tienes problemas con la prueba 3 donde la prueba espera algo como `ls: cannot access ...` y tu shell muestra `/bin/ls: cannot access ...` o `/usr/bin/ls: cannot access ...`, intenta modificar tu variable de entorno $PATH para que comience con `/bin`. Si eso no funciona, simplemente modifica `tests/3.err` para que coincida con la salida que da tu sistema. No puedes modificar la salida de tu sistema sin alterar la implementación de `ls` y/o `execv`, por lo que está bien omitir esta prueba siempre que funcione en esencia.
- Tuve que editar `/tests/3.pre` para usar `/bin/ls` debido a cómo está configurado en mi sistema, para poder pasar todas las pruebas. Alternativamente, puedes añadir `export PATH="/bin:$PATH"` a tu archivo `.profile` o `.bashrc`.

### Trampas y problemas comunes en la gestión de memoria

- Esta asignación hace muy fácil crear punteros a variables de pila que ya no existirán una vez que salgan de su ámbito, causando así una violación de segmento. Asegúrate de que si estableces un puntero para que apunte a una cadena, esa cadena sea algo que hayas asignado en el heap, y no en la pila.

- Dicho esto, si usas una cadena en la pila, puedes copiarla en una cadena asignada en el heap usando `strcpy()`, `strncpy()`, `strcat()` y `strncat()`.

- Solo usa `strcpy()` y `strcat()` para cadenas de tamaño fijo y asegúrate de que el buffer al que estás copiando tenga suficiente espacio para contener la cadena, más un carácter extra para `\0`.

- Para `strncpy()` y `strncat()`, asegúrate de que `n` sea lo suficientemente grande para incluir el terminador `\0`, o añádelo manualmente.

- Ten cuidado con los usos posteriores a liberar memoria (use-after-frees), especialmente en la implementación de `path`.

- Asegúrate de liberar cualquier cadena de `getline()` y `strdup()`, pero ten cuidado con las liberaciones dobles, por ejemplo, no liberes una subcadena de una cadena que ya hayas liberado.

- Evita la función de la biblioteca C `strtok()`; no es segura para hilos. Usa `strsep()` en su lugar.

- Cuando uses `strsep()`, asegúrate de mantener una copia del puntero original a la cadena para poder liberarla después, porque `strsep()` modificará el puntero, por lo que si lo liberas más tarde, corromperás la tabla de páginas.

- Después de llamar a `strsep(&buf, delim)`, verifica si `buf` es `NULL` antes de desreferenciarlo.
- Práctica general de programación en C: si asignas memoria para una estructura de datos dentro de una función, deberías liberarla en la misma función. Si asignas memoria en una función `create_xxx` dedicada, deberías tener una función `destroy_xxx` correspondiente. De esta manera, siempre asignarás y liberarás memoria en el mismo nivel de profundidad de función, lo que facilita evitar errores de memoria.
- Después de cada llamada a `malloc`, `calloc` o `realloc`, verifica si el resultado es `NULL`.
- Usa `calloc` en lugar de `malloc` si estás creando un arreglo de punteros para evitar crear punteros a valores basura.
- En `update_path` tuve que solucionar ese problema donde la mayoría de las pruebas hacen `path /bin /usr/bin`, pero una de ellas hizo `path tests`. Así que simplemente asumí que si tu ruta comienza con una barra, es una ruta absoluta y debes copiarla tal cual; si no, es una ruta relativa y debes añadir un ./ al principio.
