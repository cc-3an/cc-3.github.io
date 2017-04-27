---
layout: post
title:  "Laboratorio 10"
date:   2017-04-27
category: lab
description: >
    Uso del módulo de memoria y program counter en Logisim.
---

Descargue el archivo en el que trabajara desde [este link](https://drive.google.com/file/d/0Byz-R0iYOs4fdjJHdXoxVE9nd1k/view?usp=sharing).

#### Ejercicio 1: Memory Manager
El Memory Manager es el encargado de guardar las instrucciones que se irán ejecutando en cada ciclo del reloj. El componente principal del Memory Manager, como se lo pueden imaginar, es la memoria RAM. En el archivo base tienen la memoria RAM que utilizaremos para las instrucciones, es una memoria de 24 bits de selección, cada uno conteniendo una palabra de 32 bits (lo que significa que la unidad mínima direccionable serán 4 bytes). 

Tomen en cuenta que el encargado de llevar el control de la siguiente instrucción a ejecutar será el Program Counter, y el encargado de decodificar parte de la instrucción será el InstructionDecoderPt1, así que el Memory Manager, por ahora, no tendrá mayor dificultad que conectarle inputs y outputs. Adicional a esto, pruebe bien como funciona la RAM en Logisim.

#### Ejercicio 2: Program Counter

El Program Counter (desde ahora PC), es un registro con capacidad de autoincrementarse que mantiene la dirección de la siguiente instrucción a ejecutar. Además de autoincrementarse, el PC también debe tener la capacidad de cambiar a otro valor totalmente diferente (que es lo que sucede cuando ocurre un branch). El PC que nosotros usaremos para este caso es únicamente de 24 bits, porque la memoria RAM de Logisim llega únicamente hasta 24 bits.

Debido a que solo tendremos direcciones de 24 bits, usaremos solo los dígitos menos significativos.

#### Ejercicio 3: 
Esta es la parte más importante del laboratorio.

Deben leer las indicaciones del proyecto e implementar un circuito que, dada la instrucción que reciben de input, encienda uno (y únicamente uno) de los bits de salida R, I o J. Cada uno de estos bits representa un tipo de codificación, y esto les ayudará a determinar como deben partir las instrucciones.

Vean la codificación, los bits que hay en común entre una y otra instrucción, que diferencia las tipo R de las demás, para tratar de simplificar su circuito. Recuerden que también pueden realizar mapas de Karnaugh para encontrar las ecuaciones.
