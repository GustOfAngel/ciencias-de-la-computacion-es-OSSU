## Créditos para [palladian](https://github.com/palladian1)

## Introducción a la Memoria Virtual de xv6

### ADVERTENCIA:

***¡El proyecto no coincide con el código fuente de xv6 disponible actualmente, que ya tiene este proyecto implementado!***

[palladian](https://github.com/palladian1) encontró un código fuente xv6 diferente en la página de GitHub de un estudiante de la Universidad de Wisconsin. Tuvo que editar el `Makefile` para encontrar correctamente el ejecutable de QEMU. Agregó `null.c` a la carpeta `user` (también editó `makefile.mk` allí), lo cual demuestra la falta de seguridad en la memoria.

Comienza con el código en [`start.zip`](https://github.com/spamegg1/reviews/raw/master/courses/OSTEP/ostep-projects/vm-xv6-intro/start.zip). Extráelo y ejecuta `make clean` y `make qemu-nox`. Luego, dentro del sistema xv6 ejecuta `null` para ver la falta de seguridad. Si deseas comparar los resultados de `null` con el código de máquina real, puedes ejecutar `objdump -d user/null.o`.

Es posible que tengas que ejecutar manualmente `make clean` y `make qemu-nox` cada vez que realices un cambio en el código.
