---
layout: post
title:  "Proyecto 3: Procesador"
date:   2017-04-27
category: proyecto
description: >
    Implementar un procesador de MIPS en el simulador Logisim, para unir todos los temas aprendidos en el curso.
permalink: /:categories/:title.html
---

#### Objetivo
En este proyecto va a implementar una version simulada de un procesador MIPS utilizando Logisim. Aqui pondra en práctica todo lo que ha aprendido sobre lenguaje ensamblador y logica de circuitos para poder ejecutar programas compilados. 

#### Background
Para poder realizar el proyecto debe haber entendido codificación de instrucciones; repase el tema antes de comenzar el proyecto si no se siente listo.

Existen tres tipos de instrucciones en MIPS. Las tipo R, las Tipo I, y las tipo J, todas del mismo tamaño, pero con un diferente formato. Recuerde que las instrucciones tipo R tiene un opcode de 0b000000, y solo existen unas cuantas instrucciones tipo J.

Adicionalmente implementaremos la instruccion Syscall: 0x0000000c, que sirve para hacer llamadas al sistema operativo. Especificamente para hacer un Read Char y Print Char en una pantalla.

Por si necesita refrescarse, este es el formato de las instrucciones en MIPS:
* Tipo R: opcode (6 bits), RS (5 bits), RT (5 bits), RD (5 bits), shamt (5 bits), func (6 bits)
* Tipo I: opcode (6 bits), RS (5 bits), RT (5 bits), immediate (16 bits)
* Tipo J: opcode (6 bits), address (26 bits)

### Instrucciones del proyecto
Debe simular un procesador que ejecute instrucciones de MIPS. Trabaje el procesador por módulos, para dividir el trabajo en porciones más pequeñas, y para llevar un mejor control de que falta agregar.

Los módulos principales que debe implementar son:
* Memory: Contendra la memoria RAM para lectura/escritura de instrucciones y datos.
* Register File: Todos los registros entre los cuales se realizaran las operaciones.
* Program Counter: Se encargara de llevar un conteo de la siguientes instruccion que toca ejecutar.
* ALU: Unidad Arimetico Logica: encargada de todos los procesos de este tipo.
* Instruction Fetcher/Decoder: para decodificar el tipo de instruccion que deben ejecutar (Tipo R, Tipo J o Tipo I).
* Jump Controller: Este modulo debe controlar cuando un programa salta a otra instruccion y cuando no.
Para que todos estos módulos trabajen de forma correcta, debera implementar también el Controller visto en clase. Si considera que otro módulo puede ser necesario, impleméntelo.

Esta es una lista de las instrucciones que su procesador debe poder ejecutar:

| Tipo R | Tipo I | Tipo J |
|--------|--------|--------|
| ADD    | BEQ    | J      |
| ADDU   | BNE    | JAL    |
| AND    | ADDI   |        |
| JR     | ADDIU  |        |
| NOR    | SLTI   |        |
| OR     | SLTIU  |        |
| SLT    | ANDI   |        |
| SLTU   | ORI    |        |
| SLL    | XORI   |        |
| SRL    | LUI    |        |
| SUB    | LW     |        |
| SUBU   | SW     |        |
| DIV    |        |        |
| DIVU   |        |        |
| MFHI   |        |        |
| MFLO   |        |        |
| MULT   |        |        |
| MULTU  |        |        |
| XOR    |        |        |
| SRA    |        |        |
| SLLV   |        |        |
| SRLV   |        |        |

Note que la mayoría de instrucciones realizan algún trabajo en el ALU. Los branches solo usan el ALU para calcular la condición, para hacer el salto usan el módulo Jump Controller.

Adicional a estas instrucciones, debe implementar syscall para hacer Read Char y Print Char.

#### Toys
Existe una libreria para logisim llamada CS316 que agrega algunos elementos extra (Pantallas LCD, Teclado, etc) que puede usar para su proyecto. Para instalarla solo deben descargar el archivo .jar e importarlo en Project/Load Library/JAR Library, y cuando solicite el nombre de la clase deben escribir edu.cornell.cs316.Components 

Esta libreria tambien contiene un Register File, tome en cuenta que este componente no lo podra utilizar, usted debe crear su propio Register File. Exceptuando esto, usted es libre de utilizar cualquier otro componente para su proyecto, y esto puede representar puntos extras.

#### Testing
Para probar el proyecto utilice el simulador Mars para codificar algún programa de MIPS. Copie las instrucciones modificadas (hexadecimal) hacia la memoria de su simulación de procesador, y ejecute. El resultado debería ser el mismo que Mars le da.

#### Entrega
El proyecto se trabajará en grupos de una o dos personas únicamente. Envíe un correo a luiscu@galileo.edu para que se le cree su grupo en el GES y pueda entregar. La fecha de entrega es la indicada en el GES.
