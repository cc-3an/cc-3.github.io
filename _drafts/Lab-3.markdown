---
layout: post
title:  "Laboratorio 3"
date:   2017-01-04
category: lab
description: >
    El objetivo de este lab es que aprendan a utilizar un debugger como lo es gdb y cgdb. Arreglar unos bugs en C con la ayuda de ese debugger y comprender que es útil este tipo de herramientas en un entorno de trabajo.
---

#### Ejercicio 1: Debugger

Para este ejercicio, ustedes van a encontrar útil usar el GDB reference card. Compilen hello.c con la bandera “-g”:

```shell
$ gcc -g -o hello hello.c
```

Esto hace que gcc guarde información en el archivo ejecutable para el gdb. Ahora comiencen el debugger, en este caso vamos a usar cgdb:

```shell
$ cgdb hello
```

**Si cgdb no funciona, pueden probar usar gdb para completar los ejercicios (solo tienen que utilizar gdb hello).**

Atraviesen todo el programa utilizando lo siguiente:

1. Poniendo un breakpoint en el main
2. Usando el comando run de gdb
3. Usando el comando single-step de gdb

escriban help con gdb para encontrar los comandos que hacen estas cosas, o usan la reference card.

**CGDB vs GDB**

En este ejercicio, usamos cgdb para verificar nuestros programas. Cgdb es idéntico a gdb, excepto que cgdb provee unas cosas extra, que hacen que su uso sea mas placentero y por ende utilizado en la practica. Todos los comandos que están en el reference sheet funcionan en gdb. En cgdb, pueden presionar ESC para ir a la ventana del código (lo que esta arriba) y presionar I para retornar a la ventana de comandos (lo que esta abajo) – similar a vim. En la parte de abajo que es la ventana de comandos, es donde tienen que ingresar los comandos.

**Mas comandos de GDB**

aprender estos comandos, va a ser útil para lo que falta de este lab, y en general en su carrera como programadores de C. Creen un archivo de texto y respondan las siguientes preguntas:


1. ¿Cómo pasan argumentos desde el command line hacia un programa utilizando gdb?
2. ¿Cómo ponen un breakpoint, que se cumpla solo cuando ciertas condiciones son verdaderas? (ejemplo: cuando ciertas variables tienen algún valor en especifico)
3. ¿Cómo ejecutan la siguiente linea de codigo de C en el programa, después haber parado en un breakpoint?
4. ¿Cómo resumen un programa después de un breakpoint?
5. ¿Cómo pueden ver el valor de una variable (inclusive una expresión como 1 + 2) en gdb?
6. ¿Cómo pueden configurar gdb para que imprima los valores de las variables cada step?
7. ¿Cómo pueden imprimir una lista de todas las variables y sus valores en la función actual?
8. ¿Cómo se salen de gdb?

***

#### Ejercicio 2: Debugging a buggy C program

Ahora van a usar su nuevo conocimiento en gdb, para hacer un debug en un programa pequeño hecho en C. Consideren el programa ll_equal.c. Compilen y corran el programa, y experimenten con el. Les dará el siguiente resultado:

```shell
$ gcc -g -o ll_equal ll_equal.c
$ ./ll_equal
equal test 1 result = 1
Segmentation fault
```

Ahora, comiencen gdb en el programa, utilizando las instrucciones en el ejercicio 1. Creen un breakpoint en la función ll_equal(), y corran el programa. Cuando el debugger regrese al breakpoint, hagan un step a través de las instrucciones en la función linea por linea, y examinen los valores de las variables. Pongan atención a los punteros de a y b en la función. ¿Siempre están apuntando a la dirección correcta? Encuentren el bug y arréglenlo.

**Respondan**

En un archivo de texto respondan:

1. ¿Qué hicieron para arreglar el error?

***

#### Ejercicio 3: Punteros y Estructuras en C

En ll_cycle.c completen la funcion ll_has_cycle() para implementar el siguiente algoritmo que verifica si una simple linked-list tiene un ciclo.

1. Comienzen con 2 punteros en el head de la lista. Al primero le vamos a llamar tortoise y al segundo hare
2. Avancen hare 2 nodos. Si no es posible porque hay un null-pointer, es porque es el final de la lista, y entonces la lista es aciclica.
3. Avancen tortoise 1 nodo. (¿Es necesaria una verificación de null-pointer?, ¿Por qué?)
4. Si tortoise y hare apuntan hacia el mismo nodo, la lista es cíclica. Sino, volver al paso 2.

Después de haber implementado ll_has_cycle() correctamente, el programa cuando compilan ll_cycle.c les va a decir si ll_has_cycle() saca la salida esperada.

***

#### Ejercicio 4: Linear feedback shift register

En este ejercicio, van a implementar una función lfsr_calculate() que determina la siguiente iteración de un linear feedback shift register (LFSR). Las aplicaciones que usan un LFSR son: Las TV Digitales, celulares CDMA, Ethernet, USB 3.0 y muchas mas. Esta función va a generar números random, utilizando bitwise operators. Para mayor información, lean el articulo de Wikipedia de los LSFR. En lfsr.c completen la funcion lfsr_calculate() para que haga lo siguiente:

![figura1](/assets/img/labs/LFSR-F16.gif)

**Explicación del diagrama de arriba:**

* En cada llamada a lfsr_calculate, ustedes le van a hacer un shift al registro 1 bit a la derecha
* Este no es un shift lógico o aritmético. En el lado izquierdo, ustedes van hacer shift sobre un único bit, igual al un XOR de los bits originales en la posición 11, 13, 14 y 16
* Las figuras que miran debajo del numero binario son XOR's, que toman 2 entradas a y b, y devuelven como salida a ^ b
* Si implementan lfsr_calculate() correctamente, el programa debería de sacar todos los 65535 números positivos enteros de 16-bits, antes de volver a empezar de nuevo con el número que empezó.

Si implementaron correctamente lfsr_calculate(), compilen y corran lfsr. Su salida debería de ser similar a esta:

```shell
$ make
$ ./lfsr
My number is: 1
My number is: 5185
My number is: 38801
My number is: 52819
My number is: 21116
My number is: 54726
My number is: 26552
My number is: 46916
My number is: 41728
My number is: 26004
My number is: 62850
My number is: 40625
My number is: 647
My number is: 12837
My number is: 7043
My number is: 26003
My number is: 35845
My number is: 61398
My number is: 42863
My number is: 57133
My number is: 59156
My number is: 13312
My number is: 16285
 ... etc etc ...
Got 65535 numbers before cycling!
Congratulations! It works!
```
