## todo gracias a [palladian](https://github.com/palladian1)

### Consejos Generales

- Lee el capítulo 9 del libro OSTEP y mira el video de la discusión 5. Los planificadores de lotería de tickets no se discuten en las clases, así que realmente tienes que leer el libro para este tema.

- En general, no puedes usar funciones de la biblioteca estándar de C dentro del kernel, porque el kernel tiene que inicializarse antes de que pueda ejecutar binarios de la biblioteca.

- El kernel de xv6 tiene una "versión de kernel" de `printf`; toma un argumento entero adicional que le indica si debe imprimir en `stdout` o `stderr`. Ten en cuenta que solo puede manejar cadenas de formato básicas como `"%d"` y no otras más complejas como `"%6.3g"`; puedes solucionar esto añadiendo espacios manualmente. También tiene otra función similar, `cprintf`.

- Si quieres usar otras funciones de la biblioteca que no están disponibles dentro del kernel (generadores de números pseudoaleatorios), puedes ver cómo se implementan esas funciones en el libro de P.J. Plauger, *The Standard C Library*, y luego implementarlas tú mismo.

  ### Implementación

  - Tendrás que modificar los mismos archivos que modificaste en el Proyecto 1b para añadir las dos nuevas llamadas al sistema.
  - Para entender cómo se crean los procesos, recuerda que comienzan en el estado `EMBRYO` antes de convertirse en `RUNNABLE`; tendrás que encontrar dónde ocurre eso.
  - Las llamadas al sistema siempre tienen el tipo de argumento `void`, así que echa un vistazo a cómo llamadas al sistema como `kill` y `read` logran sortear esa limitación y obtener argumentos (como enteros y punteros) desde el espacio de usuario. Es posible que tengas que retroceder algunos pasos en la cadena que las ejecuta.
  - Asegúrate de incluir `types.h` y `defs.h` donde necesites acceder a código de otras partes del kernel.
  - Para crear el comando de xv6 `ps`, mira cómo se implementan `cat`, `ls` y `ln`. Asegúrate de modificar el `Makefile` para incluir el código fuente de tu comando `ps`.

## ¡Spoilers a continuación!

### Guía de la solución

- Comienza desde una copia nueva del código fuente de `xv6`.

- `argint` y `argptr` son funciones importantes. Las `syscall`s no toman argumentos, pero en realidad, en el código de usuario, quieres pasarles argumentos.

- La forma de hacerlo es que el kernel llamará a la `syscall`, digamos, `sys_kill()` sin argumentos, luego `sys_kill` usará `argint()` para obtener los argumentos de la pila de llamadas, y luego los pasará a una función `kill(int pid)`.

- Puedes ver que hay un montón de declaraciones de funciones `extern int sys_whatever` más abajo; eso significa que estas funciones están definidas en otro archivo y deben ser importadas desde allí como punteros a funciones.

- Y estas funciones `sys_whatever` son básicamente solo envoltorios (wrappers) para la `syscall` real, que no tiene el `sys_` al principio. Así que necesitas añadir `sys_settickets` y `sys_getpinfo` a esa lista de declaraciones de funciones.

- Luego hay un arreglo de punteros a funciones; está usando esta forma antigua de C para inicializar arreglos donde puedes hacer `int arr[] = { [0] 5, [1] 7}`.

- Y los nombres dentro de los corchetes `SYS_fork`, etc., se definen como macros de preprocesador en otro archivo de cabecera, `syscall.h`.

- Así que necesitas añadir dos entradas más en el arreglo con punteros a funciones para `sys_settickets` y `sys_getpinfo`, y luego necesitas definir `SYS_settickets` y `SYS_getpinfo` en el archivo de cabecera correspondiente.

- Luego, todas estas funciones envoltorio `sys_` se definen en `sysproc.c`.

- Así que allí, necesitas crear `int sys_settickets(void)` e `int sys_getpinfo(void)`.

- La función `settickets` real necesitará un argumento entero, así que necesitas usar `argint` allí para tomarlo de la pila de llamadas y pasárselo a `settickets`; de manera similar, `getpinfo` necesitará un puntero, así que usarás `argptr`.

- Además, hay una condición extra en la declaración `if` para `sys_settickets`; eso es porque no se permite usar un número de tickets inferior a 1.

- Luego, hay algo de código ensamblador que necesita ejecutarse para cada una de las llamadas al sistema; afortunadamente, es solo una macro preescrita, así que no tienes que escribir ningún ensamblador. Eso está en `usys.S`.

- Así que solo añades dos líneas al final para crear macros para `SYSCALL(settickets)` y `SYSCALL(getpinfo)`.

- La última parte para las `syscalls`: necesitas declararlas en un archivo de cabecera para que el código de usuario pueda llamarlas. Eso está en `user.h`.

- `struct pstat` estará definida correctamente en `pstat.h`, pero también necesitas declararla en `user.h` para que el código de usuario no se queje cuando la vea.

- Básicamente, cualquier código de usuario que use `syscalls` o funciones de la biblioteca estándar de C (en realidad, de `xv6`) tendrá que incluir `user.h`.

- Hasta ahora, eso es todo para las dos llamadas al sistema en lo que respecta al SO; ahora solo tenemos que implementarlas realmente con las funciones regulares `settickets` y `getpinfo`, luego implementar el planificador y el programa `ps`.

- `pstat.h` no es para el planificador, sino para el programa `ps`, que funcionará de manera similar al `ps` de Linux. `pstat.h` es solo para definir `struct pstat`, pero no hay un archivo `.c` que lo acompañe.

- El planificador funcionará asignando 1 ticket por defecto a cada proceso cuando se crea; luego los procesos pueden establecer sus propios tickets usando la llamada al sistema `settickets`.

- Así que primero necesitamos asegurarnos de que cada proceso rastree sus propios tickets, luego necesitamos asignar un valor predeterminado de 1 ticket al crearlos, y luego necesitamos escribir `settickets`.

- La primera parte está en `proc.h`: los procesos se representan como una `struct proc`, así que añadimos un nuevo miembro para `int tickets`.

- El miembro `int ticks` es para `ps`; volveré a eso.

- Otra cosa a tener en cuenta en `proc.h` es el `enum procstate`: puedes ver todos los estados posibles de los procesos allí. `EMBRYO` significa que está en proceso de creación; así que lo que hice fue buscar `EMBRYO` con `grep` para encontrar dónde se creaba el proceso para establecer los tickets predeterminados en 1. Resulta que está en `proc.c`.

- Dentro de `proc.c`, hay una función `allocproc`, que inicializa un proceso.

- Hay una tabla de procesos llamada `ptable`, y `allocproc` la recorre para encontrar un proceso no utilizado.

- Luego, cuando lo encuentra, procede a crearlo; añadí `p->tickets = 1;` allí.

- Bien, el siguiente cambio es para cumplir con uno de los requisitos: los procesos hijos deben heredar el número de tickets de su proceso padre.

- Los procesos hijos se crean con `fork`, que está en el mismo archivo.

- En `fork`, `curproc` es el proceso actual, y `np` es el nuevo proceso.

- Así que establecí `np->tickets = curproc->tickets`.

- El planificador necesita generar un número pseudoaleatorio, luego debe iterar a través de la tabla de procesos con un contador inicializado en 0, sumando el número de tickets de cada proceso al contador. Una vez que el contador es mayor que el número pseudoaleatorio, se detiene y ejecuta ese proceso.

- Así que terminé buscando en *The Standard C Library* de P.J. Plauger, que es un libro grande con todo el código fuente de la biblioteca C con comentarios. Es bastante bueno; no sé si todavía se escribe de esa manera, porque el libro es de los años 80.

- Así que simplemente implementé las funciones `rand` y `srand` de C. `srand` establece una semilla aleatoria (no tan aleatoria, como verás más adelante), y luego `rand` la convierte en un entero pseudoaleatorio.

- Hay mucha magia de tipos sucediendo allí entre los cambios de ida y vuelta de enteros a enteros sin signo; eso es para evitar el desbordamiento de enteros con signo, que causa un comportamiento indefinido. El desbordamiento de enteros sin signo está bien, sin embargo.

- Solo hice un cambio para que fuera más rápido, que fue escribir `& 32767` en lugar de `% 32768`.

- Verás la semilla "aleatoria" que usé: el número de `ticks`, que creo que cuenta el número de interrupciones de temporizador hasta el momento.

- Lo cual no es nada aleatorio, ya que la primera vez que se ejecute este programa, será 0, luego 1, luego 2, etc.

- Hay algunas líneas sobre contar `ticks`; eso era para `ps`, no para el planificador.

- El cambio principal para convertirlo en un planificador de lotería es la variable contador.

- Y añadir un bucle `for` para contar el número total de tickets que se han distribuido.

- Al final de este archivo está la implementación de `settickets` y `getpinfo`.

- Después de inicializar `counter` y `totaltickets`, hay un bucle `for` que cuenta el número total de tickets que se han asignado a los procesos.

- Luego obtenemos el ticket ganador.

- Discutamos primero el código fuente original. Primero adquieres el bloqueo (lock). Lo liberarás al final. Pero en el medio, tienes un bucle `for` que itera sobre todos los procesos en `ptable`.

- Específicamente, itera solo sobre los procesos en estado `RUNNABLE`; si un proceso no está `RUNNABLE`, simplemente `continue`a al siguiente. (Esto es para el mecanismo de planificación round-robin que ya está en el código).

- Ahora va a cambiar al primer proceso `RUNNABLE` que encuentre. Es decir, va a empezar a ejecutarlo.

- Primero, `c` representa la CPU actual. Así que establece que la CPU actual ejecute el proceso que encontró con `c->proc = p;`.

- Luego llama a esta función, `switchuvm(p)`, que configura el espacio de direcciones de memoria virtual para `p`. Luego establece el estado del proceso en `RUNNING`.

- Y en `swtch` es donde ocurre la magia: esa función intercambia los contenidos de los registros del SO y del planificador con los contenidos de los registros guardados en memoria del proceso `p`.

- Tan pronto como se ejecuta `swtch`, la CPU continuará ejecutando instrucciones, pero ahora son las instrucciones del proceso. Así que esta función del planificador simplemente se queda en espera.

- Eventualmente, cuando se produzca una interrupción del temporizador, el procesador usará otra llamada `swtch` pero con los argumentos invertidos para intercambiar los contenidos de los registros del planificador desde la memoria a los registros de la CPU y guardar los contenidos de los registros del proceso. En ese momento, la ejecución continuará en este punto exacto.

- Ahora `switchkvm` configurará el espacio de direcciones de memoria virtual del kernel.

- Estas 5 líneas son el cambio de contexto:

  ```c
  c->proc = p;
  switchuvm(p);
  p->state = RUNNING;

  swtch(&(c->scheduler), p->context);
  switchkvm();
  ```

- Luego pasamos a la siguiente iteración del bucle `for` interno, que encuentra el siguiente proceso `RUNNABLE` y se repite.

- Solo una vez que hemos ejecutado todos los procesos `RUNNABLE` salimos del bucle `for` interno y liberamos el bloqueo.

- El código fuente original está estructurado así (esto es pseudocódigo):

  ```python
  while (1) {
    iterar sobre los procesos:
      if no está en estado runnable:
        continue
      ejecutarlo
  ```

- El nuevo código está estructurado así (esto es pseudocódigo):

  ```python
  while (1) {
    contar el total de tickets asignados a todos los procesos // un bucle for aquí
    obtener el número del ticket ganador
    iterar sobre los procesos: // otro bucle for aquí
      if no está en estado runnable:
        continue
      añadir sus tickets al contador
      if el contador <= número del ticket ganador:
        continue
      ejecutarlo
  ```

- Ignoramos los tickets de los procesos que no están en estado `RUNNABLE`.

- Los tickets no están numerados; cada proceso simplemente tiene una cantidad determinada de tickets, y simplemente contamos hasta que hemos pasado `n` tickets, donde `n` es el ganador.

- Por ejemplo, si el proceso A tiene 5 tickets, el proceso B tiene 7 y el proceso C tiene 2. Si el número ganador es 3, entonces se ejecutaría A; si es 8, se ejecutaría B; si es 12, se ejecutaría C.

- Un ganador entre 0 y 4 sería A, entre 5 y 11 sería B, y entre 12 y 13 sería C.

- `settickets` es bastante básico: solo adquieres un bloqueo, estableces los tickets para el proceso y liberas el bloqueo.

- Para `getpinfo`, básicamente funciona así:

- `p` es un puntero a una `struct pstat`, como se define en `pstat.h`. Cada uno de sus miembros es un arreglo, con una entrada por proceso.

- Comprobar si hay un puntero nulo.

- Iterar sobre la tabla de procesos y establecer `proc_i` como el i-ésimo proceso.

- Establecer la i-ésima entrada de cada miembro de `p` con el valor para este proceso.

- Una última tarea administrativa: necesitamos añadir declaraciones para `struct pstat` y las llamadas al sistema `settickets` y `getpinfo` en `defs.h`.

- Y el último archivo es `ps.c`, que implementa el programa `ps`, similar al `ps` de Linux. Simplemente llama a `getpinfo` para rellenar una `struct pstat`, y luego imprime la información de cada proceso en uso.

- Y luego solo modificas el `Makefile` para incluir `ps.c` en la compilación, ¡y hemos terminado!

- Ah, y por esto necesitábamos los ticks en el planificador: `ps` imprimirá cuánto tiempo se ha ejecutado cada proceso.

- Así que necesita cronometrar el número de ticks que realmente se ejecutó.

- FINALMENTE, ejecuta `make qemu` en el directorio `/src` para asegurarte de que todo funciona.
