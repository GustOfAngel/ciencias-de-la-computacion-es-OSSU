## todo gracias a [palladian](https://github.com/palladian1)

### Consejos Generales

- Lee el capítulo 9 del libro OSTEP y mira el video de la discusión 5. Los planificadores de lotería no se discuten en las conferencias, así que realmente tienes que leer el libro para este proyecto.

- En general, no puedes usar funciones de la biblioteca estándar de C dentro del kernel, porque el kernel tiene que inicializarse antes de poder ejecutar binarios de bibliotecas.

- El kernel de xv6 tiene una versión "de kernel" de `printf`; toma un argumento entero adicional que le indica si debe imprimir en `stdout` o `stderr`. Ten en cuenta que solo puede manejar cadenas de formato básicas como `"%d"` y no otras más complejas como `"%6.3g"`; puedes resolver esto agregando espacios manualmente. También tiene otra función similar, `cprintf`.

- Si deseas usar otras funciones de biblioteca que no están disponibles dentro del kernel (generadores de números pseudoaleatorios), puedes ver cómo se implementan esas funciones en el libro de P.J. Plauger, *The Standard C Library*, y luego implementarlas tú mismo.

  ### Implementación

  - Tendrás que modificar los mismos archivos que en el Proyecto 1b para agregar las dos nuevas llamadas al sistema.
  - Para entender cómo se crean los procesos, recuerda que comienzan en el estado `EMBRYO` antes de convertirse en `RUNNABLE`--tendrás que encontrar dónde ocurre eso.
  - Las llamadas al sistema siempre tienen el tipo de argumento `void`, así que mira cómo las llamadas al sistema como `kill` y `read` logran sortear esa limitación y obtener argumentos (como enteros y punteros) desde el espacio de usuario. Es posible que tengas que retroceder algunos pasos en la cadena que las ejecuta.
  - Asegúrate de incluir `types.h` y `defs.h` donde sea necesario acceder a código de otras partes del kernel.
  - Para crear el comando xv6 `ps`, mira cómo están implementados `cat`, `ls` y `ln`. Asegúrate de modificar el Makefile para incluir el código fuente de tu comando `ps`.

## ¡Spoilers a continuación!

### Guía de la solución

- Comienza con una copia nueva del código fuente de `xv6`.

- `argint` y `argptr` son funciones importantes. Las llamadas a sistema (`syscall`) no toman argumentos, pero en realidad, en el código de usuario quieres pasar argumentos a ellas.

- La forma de hacerlo es que el kernel llamará a la `syscall`, digamos, `sys_kill()` sin argumentos, luego `sys_kill` usará `argint()` para obtener los argumentos de la pila de llamadas, y luego pasará eso a una función `kill(int pid)`.

- Así que puedes ver que hay una serie de declaraciones de funciones `extern int sys_whatever` a continuación; eso significa que estas funciones están definidas en otro archivo y deben incluirse desde allí como punteros a funciones.

- Y estas funciones `sys_whatever` son básicamente envolturas (wrappers) para la verdadera llamada al sistema, que no tiene el `sys_` al principio. Así que necesitas agregar `sys_settickets` y `sys_getpinfo` a esa lista de declaraciones de funciones.

- Luego hay un arreglo de punteros a funciones; está usando esta forma antigua de C para inicializar arreglos donde puedes hacer `int arr[] = { [0] 5, [1] 7}`.

- Y los nombres dentro de los corchetes cuadrados `SYS_fork`, etc. están definidos como macros del preprocesador en otro archivo de encabezado `syscall.h`.

- Así que necesitas agregar dos entradas más en el arreglo con punteros a funciones a `sys_settickets` y `sys_getpinfo`, y luego necesitas definir `SYS_settickets` y `SYS_getpinfo` en el archivo de encabezado relevante.

- Entonces todas estas funciones `sys_` están definidas en `sysproc.c`.

- Así que allí, necesitas crear `int sys_settickets(void)` y `int sys_getpinfo(void)`.

- La verdadera función `settickets` necesitará un argumento entero, así que necesitas usar `argint` allí para obtenerlo de la pila de llamadas y pasarlo a `settickets`; de manera similar, `getpinfo` necesitará un puntero, así que usarás `argptr`.

- Además, hay una condición extra en la sentencia if para `sys_settickets`; eso es porque no se permite usar un número de tickets inferior a 1.

- Luego hay código de ensamblador que debe ejecutarse para cada una de las llamadas al sistema; afortunadamente, es solo una macro preescrita, así que no tienes que escribir ningún ensamblador. Eso está en `usys.S`.

- Así que simplemente agregas dos líneas al final para crear macros para `SYSCALL(settickets)` y `SYSCALL(getpinfo)`

- La última parte para las `syscalls`: necesitas declararlas en un archivo de encabezado para que el código de usuario pueda llamarlas. Eso está en `user.h`.

- Así que `struct pstat` se definirá adecuadamente en `pstat.h`, pero necesitas declararla también en `user.h` para que el código de usuario no se queje cuando la vea.

- Básicamente, cualquier código de usuario que use `syscalls` o funciones de la biblioteca estándar de C (realmente, de `xv6`) tendrá que incluir `user.h`.

- Hasta ahora, eso es todo para las dos llamadas al sistema en lo que respecta al sistema operativo; ahora solo tenemos que implementarlas con las funciones regulares `settickets` y `getpinfo`, luego implementar el planificador y el programa `ps`.

- `pstat.h` no es para el planificador, sino para el programa `ps`, que funcionará algo así como el `ps` de Linux. `pstat.h` solo sirve para definir el `struct pstat`, pero no hay un archivo `.c` que lo acompañe.

- Entonces el planificador funcionará asignando 1 ticket por defecto a cada proceso cuando se crea; luego los procesos pueden establecer sus propios tickets usando la llamada al sistema `settickets`.

- así que primero necesitamos asegurarnos de que cada proceso lleve un registro de sus propios tickets, luego necesitamos asignar un valor predeterminado de 1 ticket al crearlos, luego necesitamos escribir `settickets`.

- la primera parte está en `proc.h`: los procesos se representan como un `struct proc`, así que agregamos un nuevo miembro para `int tickets`.

- el miembro `int ticks` es para `ps`; volveré a eso más tarde.

- Otra cosa a tener en cuenta en `proc.h` es el `enum procstate`: puedes ver todos los posibles estados de proceso allí. `EMBRYO` significa que está en proceso de creación; así que lo que hice fue hacer `grep` de `EMBRYO` para encontrar dónde se creaba el proceso para establecer los tickets predeterminados en 1. Resulta que está en `proc.c`.

- Dentro de `proc.c`, hay una función `allocproc`, que inicializa un proceso.

- Hay una tabla de procesos llamada `ptable`, y `allocproc` la recorre para encontrar un proceso no utilizado.

- Luego, cuando lo encuentra, procede a crearlo; agregué `p->tickets = 1;` allí.

- bien, así que el siguiente cambio es para cumplir con uno de los requisitos: los procesos hijos necesitan heredar el número de tickets de su proceso padre.

- Así que los procesos hijos se crean con `fork`, que está en el mismo archivo.

- En `fork`, `curproc` es el proceso actual, y `np` es el nuevo proceso.

- Así que establecí `np->tickets = curproc->tickets`.

- Así que el planificador necesita generar un número pseudoaleatorio, luego debe recorrer la tabla de procesos con un contador inicializado en 0, sumando el número de tickets para cada proceso al contador. Una vez que el contador sea mayor que el número pseudoaleatorio, se detiene y ejecuta ese proceso.

- Así que terminé mirando en *The Standard C Library* de P.J. Plauger, que es simplemente un gran libro con todo el código fuente de la biblioteca C con comentarios. Es bastante bueno; no sé si todavía está escrito de esa manera porque el libro es de los 80.

- Así que simplemente implementé las funciones `rand` y `srand` de C. `srand` establece una semilla aleatoria (no tan aleatoria, como verás más adelante), luego `rand` la convierte en un entero pseudoaleatorio.

- Hay mucha magia de tipos ocurriendo allí entre cambios de enteros a enteros sin signo; eso es para evitar el desbordamiento de enteros con signo, que causa comportamiento indefinido. El desbordamiento de enteros sin signo está bien.

- Solo hice un cambio para hacerlo más rápido, que fue escribir `& 32767` en lugar de `% 32768`.

- Así que verás la semilla "aleatoria" que usé: el número de `ticks`, que creo que cuenta el número de interrupciones de temporizador hasta ahora.

- Lo cual no es aleatorio en absoluto, ya que la primera vez que se ejecuta este programa, será 0, luego 1, luego 2, etc.

- Así que hay algunas líneas sobre contar `ticks`; eso era para `ps`, no para el planificador.

- El cambio principal para hacerlo un planificador de lotería es la variable contador.

- Y agregar un bucle for para contar el número total de tickets que se han distribuido.

- Así que luego, en la parte inferior de este archivo, está la implementación de `settickets` y `getpinfo`.

- Así que después de inicializar `counter` y `totaltickets`, hay un bucle for que cuenta el número total de tickets que se han asignado a los procesos.

- Luego obtenemos el ticket ganador.

- Discutamos primero el código fuente original. Primero adquieres el bloqueo. Lo liberarás al final. Pero entre medias, tienes un bucle for que itera sobre todos los procesos en `ptable`.

- Específicamente, itera solo sobre los procesos en estado `RUNNABLE`; si un proceso no está `RUNNABLE`, simplemente `continue` al siguiente. (Esto es para el mecanismo de planificación round-robin que ya está en el código.)

- Así que ahora va a cambiar al primer proceso `RUNNABLE` que encuentre. Como, cambiando a ejecutarlo.

- Primero, `c` representa la CPU actual. así que establece la CPU actual para ejecutar el proceso que encontró con `c->proc = p;`.

- Luego llama a esta función, `switchuvm(p)`, que configura el espacio de direcciones de memoria virtual para `p`. Luego establece el estado del proceso en `RUNNING`.

- Y luego `swtch` es donde ocurre la magia: eso intercambia el contenido de los registros del sistema operativo y el planificador con el contenido de los registros guardados en memoria del proceso `p`.

- Así que tan pronto como se ejecuta `swtch`, la CPU continuará ejecutando instrucciones, pero ahora son las instrucciones del proceso. Así que esta función del planificador simplemente se queda allí.

- Eventualmente, cuando se active una interrupción de temporizador, el procesador usará otra llamada `swtch` pero con los argumentos invertidos para intercambiar el contenido de los registros del planificador de la memoria en los registros de la CPU y guardar el contenido de los registros del proceso. En ese momento, la ejecución continuará exactamente en este punto.

- Luego `switchkvm` configurará el espacio de direcciones de memoria virtual del kernel.

- Estas 5 líneas son el cambio de contexto:

  ```c
  c->proc = p;
  switchuvm(p);
  p->state = RUNNING;

  swtch(&(c->scheduler), p->context);
  switchkvm();
  ```

- Luego continuamos con la siguiente iteración del bucle for interno, que encuentra el siguiente proceso `RUNNABLE` y repite.

- Solo una vez que hayamos ejecutado todos los procesos `RUNNABLE` salimos del bucle for interno y liberamos el bloqueo.

- El código fuente original está estructurado así (esto es pseudocódigo):

  ```python
  while (1) {
    recorrer procesos:
      si no ejecutable (runnable):
        continuar
      ejecutarlo
  ```

- El nuevo código está estructurado así (esto es pseudocódigo):

  ```python
  while (1) {
    contar los tickets totales asignados a todos los procesos // un bucle for aquí
    obtener el número del ticket ganador
    recorrer procesos: // otro bucle for aquí
      si no ejecutable (runnable):
        continuar
      agregar sus tickets al contador
      si contador <= número del ticket ganador:
        continuar
      ejecutarlo
  ```

- Ignoramos los tickets de los procesos no ejecutables (non-RUNNABLE).

- Los tickets no están numerados; cada proceso simplemente tiene una cantidad fija de tickets, y solo contamos hasta que hayamos superado `n` tickets, donde `n` es el ganador.

- Por ejemplo, si el proceso A tiene 5 tickets y el proceso B tiene 7, el proceso C tiene 2. Si el número ganador es 3, entonces A se ejecutaría; si es 8, entonces B se ejecutaría; si es 12, entonces C se ejecutaría.

- Un ganador en 0-4 sería A, 5-11 sería B, y 12-13 sería C.

- Así que `settickets` es bastante básico: simplemente adquieres un bloqueo, estableces los tickets para el proceso, liberas el bloqueo.

- Para `getpinfo` básicamente funciona así:

- `p` es un puntero a `struct pstat`, como se define en `pstat.h`. Cada uno de sus miembros es un arreglo, con una entrada por proceso.

- Verifica si es un puntero nulo.

- Recorre la tabla de procesos y establece `proc_i` como el i-ésimo proceso.

- Establece la i-ésima entrada de cada miembro de `p` al valor para este proceso.

- Un último detalle administrativo: necesitamos agregar declaraciones para `struct pstat` y las llamadas al sistema `settickets` y `getpinfo` en `defs.h`.

- Y luego el último archivo es `ps.c`, que implementa el programa `ps`, similar al `ps` de Linux. Simplemente llama a `getpinfo` para llenar un `struct pstat`, luego imprime la información para cada proceso en uso.

- Y luego solo modificas el Makefile para incluir `ps.c` en la compilación, ¡y listo!

- Ah, y esto es por qué necesitábamos los ticks en el planificador: `ps` imprimirá cuánto tiempo ha ejecutado cada proceso.

- Así que necesita medir el número de ticks que realmente ejecutó.

- FINALMENTE ejecuta `make qemu` en el directorio `/src` para asegurarte de que todo funcione.
