---
layout: post
title:  "Proyecto 2: MIPS"
date:   2017-03-17
category: proyecto
description: >
    Demostrar su comprensión de llamadas a funciones, acceso a memoria, y codificación de instrucciones, al implementar un ensamblador para MIPS.
permalink: /:categories/:title.html
---

#### Introducción

Este proyecto está diseñado para que el estudiante comprenda a detalle la función de un ensamblador, cómo es que este traduce código legible por humanos a lenguaje de máquina. Con este proyecto nos acercamos un poco más a los componentes lógicos con los cuales están construídas las computadoras.

Este proyecto nos enseña los detalles de la codificación de instrucciones, y las ventajas de tener una arquitectura estándar, sin muchos casos especiales, pocos formatos de instrucciones, utilización de cualquier registro en operaciones aritmético-lógicas, etc.

#### Descripción del proyecto

Usted debe implementar una función en MIPS llamada *ensamblador*, la cual recibe como primer argumento una dirección de memoria en la cual se encuentra el código a codificar (este código en forma de cadena de caracteres), como segundo argumento la dirección de memoria donde se encuentra su área de .text (un espacio de tamaño fijo que pediremos para guardar las instrucciones codificadas), y como tercer argumento la dirección de su área de .data (un espacio de tamaño fijo para guardar cadenas de caracteres).

La función debe convertir las instrucciones que se le piden de MIPS a lenguaje de máquina, y luego calcular los offsets de los branches y los jumps. Únicamente debe soportar tres directivas, .text, .data, y .asciiz. Todo el input numérico es en formato decimal. Si se reciben números en otros formatos, está permmitido terminar la ejecución sin codificar nada, y sin indicar el error.

La función debe devolver la dirección donde almacenó el código en lenguaje de máquina. Al regresar a la función que la mandó a llamar, debe ser posible saltar a la dirección devuelta por *ensamblador* y su simulador debe ser capaz de ejecutar el código.

#### Archivos base

Descargue los archivos base del siguiente [link](https://drive.google.com/file/d/0Byz-R0iYOs4fV3gyZE1uSGNLeGc/view?usp=sharing).

* punteo.txt: Indica cuales son las instrucciones que debe soportar su ensamblador, y el punteo de cada una.
* ensamblador.s: Archivo que incluye un main funcional, algunas funciones que le serán de ayuda (string compare, ascii to integer, etc.) y un ejemplo con dos instrucciones codificadas (ori y syscall). Puede modificar este código a su discreción. Se le sugiere utilizarlo para ahorrar tiempo, pero puede hacer su propio main.
* testcases: Casos de prueba para su ensamblador.

#### Tabla de símbolos

Su ensamblador debe implementar una tabla de símbolos. Recuerde que los branches necesitan saber a cuántas instrucciones antes o después deben de saltar, y los jumps necesitan conocer hacia qué dirección señala la etiqueta. La tabla de símbolos será quien ayude a realizar este cálculo de direcciones.

Para facilitar la construcción de la tabla de símbolos podemos agregar la limitante que no se tendrán más de 20 etiquetas en el código a ensamblar.

#### Ejecución

Al principio de ensamblador.s usted encontrará un par de comentarios que indican dónde va el programa a ser codificado. Coloque su programa allí, como una cadena de texto.

Luego de esto, ejecute el programa. Este automáticamente debe ensamblar el código, y luego ejecutarlo. Normalmente codificaremos programas que impriman algún valor a pantalla para que sea fácil comparar los resultados.

#### Detalles y ayuda

No es necesario que soporten los comentarios, sin embargo su implementación es trivial y les evitaría tener que estarlos borrando.

La mejor forma de probar su proyecto es haciendo programas en MIPS y probándolos en un simulador como MARS, codificarlos utilizando su ensamblador, luego ejecutar el código que su ensamblador generó y verificar que el output fue el mismo.

La mejor fuente de información que tendrá será el apéndice de Computer Organization and Design. El apéndice tiene todas las instrucciones que soporta MIPS y cual es su codificación. El simulador MARS también le ayudará, pues le muestra cómo quedan las instrucciones ya codificadas.

No es necesario que escriba un código muy robusto, los programas con los que los probaremos no contendrán errores de ningún tipo. Es especialmente importante la forma de codificación, para estandarizar no utilizaremos comas para separar registros, ni mas de un espacio, los registros nunca estarán en forma numérica a excepción de $0. Los labels siempre están en una línea por si mismos. En caso de alguna duda de sintaxis, pregunte o revise los testcases.

#### Entrega

El proyecto se trabaja de forma individual o en parejas, es decir, grupos de una o dos personas únicamente.

Creen un repositorio donde iran actualizando con los avances que realicen. Ambas personas del grupo deben contribuir al repositorio. Deben agregar a cc3-grades como colaborador en el repositorio.

La fecha de entrega del proyecto es la indicada en el GES.
