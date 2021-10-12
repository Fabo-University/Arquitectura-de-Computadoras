<h1 align="center"> 💻Teoria</h1>

Indice
======
   * [Subrutinas](#Subrutinas)
   * [Pasaje de parámetros](#Pasaje_de_parametros)
     * [Por valor](#Por_Valor)
     * [Por Referencia](#Por_Referencia)
     * [Donde se pasan los Parámetros](#Donde_Pasan_Los_Parametros)
   * [Funcionamiento de la pila](#Funcionamiento_de_la_pila)
   * [PUSH/POP](#Push_Pop)
   * [Interrupciones](#Interrupciones)


Subrutinas
==========

3000H = Ditinta a 2000H (programa principal). La subrutina no debe sobre escribir otras zonas del programa.

Pasaje_de_parametros
====================

- Procedimientos (subrutinas), en general requieren datos de entrada y proveen datos de salida.
- Parametros son estos datos pasados a y desde el procedimiento.
- Estos parámetros pueden ser pasados de dos maneras
  - Por Valor (Cuanto vale)
  - Por Referencia (La dirección)

Por_Valor
--------
- Es eso: Se pasa el valor de una variable al procedimiento
- Son sólo parámetros de entrada.
- Independientemente del uso de este valor por parte del procedimiento, éste no puede ser modificado.

Por_Referencia
--------------
- Aca es pasada la dirección de la variable y no su valor.
- Es necesario cuando hay que modificar el valor del parámetro (Retorno)
- En general menos eficiente que pasar por valor. Tenemos la dir y hay que acceder a memoria para buscar el dato.
- Pero más eficiente cuando hay que transferir un arreglo datos entre proc. Asi se pasa la dir del arreglo.

Donde_Pasan_Los_Parametros
--------------------------
#### Vía Registros
- El número de registros es la principal limitación.
- Es importante documentar que registros se usan

#### Vía Memoria
- Variables definidas en el programa ("Globales")
- Se usa un área definida de memoria (RAM)
- Difícil de estandarizar (En una variable llamada cachito (Casi ni se usa))

#### Vía pila (stack) 
- Es el método más ampliamente usado.
- La pila (o stack) es una zona de memoria (RAM) destinada a este uso específico.
- Lo usa la mayoría de los lenguajes de alto nivel.
- Independientemente de memoria y registros.
- Hay que comprender bien como funciona porque la pila es usada por el usuario y por el sistema
- Aunque es más complicado, en general los registros son recursos muy preciados.

Funcionamiento_de_la_pila
=========================

#### Zona de memoria destinada a un uso específico.
- Uso del sistema: Salva la dirección de retorno cuando es llamada una subrutina o se produce una interrupción de hardware
- Uso del usuario: Pasaje de parámetros

#### Cada vez que se ejecuta un programa, el solo inicializa el registro SP apuntado por la pila.
- El simulador inicia SP = 8000H

Push_Pop
========
- PUSH: Apila datos. El SP apunta al unico dato almacenado, por lo tanto primero se decrementa y luego almacena el dato.
- POP: Desapila datos. Desapila el dato y luego incrementa el SP. Operación inversa a la anterior.
- PUSH y POP apilan y desapilan datos de 16 bits (2 bytes)

Interrupciones
==============
- La funcionalidad dentro de un sistema de cómputo es implementada por hardware que ayuda al procesador
- Cada dispositivo opera a su propio ritmo, pero hay necesidad de sincronizar la operación del procesador con estos dispositivos.