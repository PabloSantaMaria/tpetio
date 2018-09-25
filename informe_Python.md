# Guía de referencia rápida de **_Python_**

# Índice principal

* [Generalidades](#generalidades)
* [Indentación](#indentación)
* [Palabras reservadas](#palabras-reservadas)
* [El espacio de nombres](#el-espacio-de-nombres)
* [El operador de asignación =](#el-operador-de-asignación-=)
* [La función id()](#la-función-id())
* [Expresiones y declaraciones](#expresiones-y-declaraciones)
  * [Expresiones](#expresiones)
  * [Declaraciones (Statements)](#declaraciones-(statements))
* [Expresiones en el entorno interactivo.](#expresiones-en-el-entorno-interactivo.)
* [Salida estándar](#salida-estándar)
* [Despliegue con formato](#despliegue-con-formato)
* [Caracteres de escape](#caracteres-de-escape)
* [Despliegue con formato](#despliegue-con-formato)
* [Entrada estándar con input()](#entrada-estándar-con-input())
* [Tipos de datos](#tipos-de-datos)
  * [Números enteros (int)](#números-enteros-(int))
  * [Números de punto flotante (float)](#números-de-punto-flotante-(float))
  * [Números complejos (complex)](#números-complejos-(complex))
  * [Valores booleanos (bool)](#valores-booleanos-(bool))
  * [Cadenas de caracteres (str)](#cadenas-de-caracteres-(str))
  * [Listas](#listas)
  * [Conjuntos](#conjuntos)
  * [Diccionarios](#diccionarios)
* [Operadores](#operadores)
* [Control de flujo](#control-de-flujo)
  * [Sentencia if](#sentencia-if)
  * [Sentencia while](#sentencia-while)
  * [Sentencia for](#sentencia-for)
  * [Sentencia range()](#sentencia-range())
* [Funciones](#funciones)

## Generalidades

* Una declaración debe estar toda en una sola línea. Para romper una declaración en múltiples líneas debe usarse `\` al final de cada una de ellas (salvo la última).  

_Excepción_: siempre se puede romper dentro de cualquier par `()`, `[]` o `{}`, o en una cadena delimitada por triple comillas.

* En una línea pueden aparecer más de una declaración separándolas por `;`.

* Los comentarios comienzan con `#` y continúan hasta el final de la línea.

* Python también permite incluir comentarios de varias líneas. Éstos deben de estar encerrados entre triples comillas `"""` o apóstrofes `' ' '`. Este tipo de comentarios son conocidos como "_docstrings_" y son utilizados para generar documentación que se desplegaría mediante la función `help()`.

* Un identificador está formado por una letra o símbolo `_` seguido de más letras, números o símbolos `_`.

* Python distingue mayúsculas de minúsculas.

## Indentación

> _En Python la indentación forma parte de la sintaxis._

La indentación se utiliza para delimitar bloques de código dentro de un condicional, ciclo, función, etc., sin necesidad de utilizar caracteres delimitadores como ocurre en otros lenguajes de programación.

La indentación es la forma que usa Python para agrupar declaraciones. En el intérprete interactivo se debe teclear un tab o espacio(s) para cada línea indentada. Todos los editores de texto tienen la facilidad de agregar la indentación automáticamente.

Al ingresar una declaración compuesta en forma interactiva, se debe finalizar con una línea en blanco para indicar que está completa (ya que el analizador no puede adivinar cuándo se tecleó la última línea). Cada línea de un bloque básico debe estar indentada de la misma forma.

## Palabras reservadas

Las palabras reservadas (keywords) corresponden a los nombres de las declaraciones que el intérprete de Python incluye por defecto. No se deben utilizar dichas palabras para asignar nombres a otros objetos.
El listado de palabras reservadas puede ser consultado ingresando ``help('keywords')`` desde la interfaz interactiva.

```python
* False
* def
* if
* raise
* None
* del
* import
* return
* True
* elif
* in
* try
* and
* else
* is
* while
* as
* except
* lambda
* with
* assert
* finally
* nonlocal
* yield
* break
* for
* not
* class
* from
* or
* continue
* global
* pass
```

El intérprete utiliza otros elementos por defecto los cuales aún cuando son parte fundamental del lenguaje y  no son palabras reservadas, no se recomienda utilizarlos como nombres.
El módulo `__buitlins__` contiene al resto de estos elementos.

## El espacio de nombres (namespace)

* Python es un lenguaje de muy alto nivel, en el que todos sus elementos son objetos, incluyendo los tipos de datos básicos.
* La gestión del uso de la memoria es automático en Python, tanto para la asignación de memoria al crear un objeto, como para la recuperación de memoria al desecharlo.
* El espacio de nombres (namespace) contiene un listado de los objetos existentes en la memoria del sistema y los nombres a los que están ligados.
* Un objeto puede tener más de un nombre.
* Si un objeto no está ligado al menos a un nombre, dicho objeto es desechado.
* El intérprete de Python tiene un espacio de nombres principal, pero cada función, módulo y objeto tiene su propio espacio de nombres. A ésto se le conoce como "Ámbito" (Scope).

## El operador de asignación `=`

Para asignar un nombre a un objeto, se utiliza el operador de asignación `=` con la siguiente sintaxis:

```python
<identificador> = <objeto>

saludo = 'Hola'
matriz = [["autobús", "diesel", True], ["automóvil", "gasolina", True]]
numero = 23.45
```

Es posible asignar a varios nombres un número igual de objetos usando un sólo operador de asignación mediante la siguiente sintaxis:

```python
<nombre 1>, <nombre 2>, <nombre 3>, ..., <nombre n> = <objeto 1>, <objeto 2>, <objeto 3>, ..., <objeto n>
entero, flotante, complejo, booleano = 12, 4.5, (12.3 + 23j), True
```

## Sintaxis para la elaboración de nombres

* Python 3 acepta el uso de _unicode_, por lo que es posible utilizar cualquier caracter alfabético, incluso aquellos distintos al alfabeto occidental, para la elaboración de nombres.
* Los nombres pueden empezar con un guión bajo `_` o un caracter alfabético.
* Después del primer caracter, se pueden utilizar caracteres alfabéticos, números y/o guiones bajos.
* No se permiten caracteres distintos a los alfabéticos o que pudieran confundirse con operadores como `|` , `~` , `#` , `-` , etc.
* Se pueden utilizar mayúsculas, pero cabe señalar que **Python es sensible a mayúsculas.**

```python
_saludo = 'Hola'
número = 23
Numero = 45.32
```

## La función `id()`

Cada objeto cuenta con una "identidad", la cual corresponde a la posición en la que se encuentra almacenado en la memoria. La función `id()` permite conocer esta identidad por medio del nombre.

```python
>>> numero = 45
>>> otro_numero = 45
>>> id(numero)
139900019112480
>>> id(otro_numero)
139900019112480
>>> otro_numero = 25
>>> id(otro_numero)
139900019111840
>>> id(numero)
139900019112480
>>> numero
45
```

## Expresiones y declaraciones

### Expresiones

Una expresión es una combinación de valores, operadores, funciones y métodos que da por resultado un valor en una sola línea.

```python
>>> 1 + 1
2
>>> 45 >= 11
True
>>> "carro".upper()
'CARRO'
```

### Declaraciones (Statements)

Las declaraciones son unidades de código que el interprete de Python puede ejecutar. En realidad una declaración es un tipo de expresión.

```python
>>> y = 0
>>> for x in range(25):
>>>    y += x
>>> print(y)
300
```

El intérprete de Python permite ejecutar múltiples expresiones en una sola, separándolas por punto y comas `;`. En este caso, sólo se desplegará el resultado de la última expresión ejecutada.

```python
>>> a = 3; b = a * 4.5; b; a + 5
8
```

_Advertencia_: No se recomienda usar este recurso ya que se corre el riesgo de ofuscar el código innecesariamente.

### Expresiones en el entorno interactivo

La interfaz interactiva evalúa las expresiones tan pronto como son ingresadas y en su caso, despliega el resultado.

```python
>>> 4 * 3
12
>>> 15 == 25
False
>>> 'hola' + ' mundo'
'hola mundo'
```

## Salida estándar

La instrucción para desplegar información en la teminal de texto es `print`.
`print()` es una función, por lo que el contenido a desplegar siempre debe estar expresado como un parámetro dentro de la función, es decir, que debe estar entre paréntesis.

Cuando `print()` incluye una expresión, ésta es evaluada antes de ser desplegada. Del mismo modo, `print()` puede desplegar varias expresiones separadas por comas.

Ejemplos:

```python
>>> a = 2
>>> print(a)
2
>>> 2 + 2
4
>>> print("Hola")
Hola
>>> print("Hola", "Mundo")
Hola Mundo
>>> print("Hola" + "Mundo")
HolaMundo
>>> print("Tienes", a, "buenos amigos.")
Tienes 2 buenos amigos.
>>> print("Tienes" + a + "buenos amigos.")
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-8-e72a50cbaac8> in <module>()
----> 1 print("Tienes" + a + "buenos amigos.")

TypeError: must be str, not int
```

Todas las funciones, incluyendo a `print()`, regresan un valor. El valor que `print` regresa es `None`, pero este valor no es desplegado por el intérprete.

```python
>>> nulo = print("Hola")
>>> Hola
nulo
```

Sin embargo, la función `print()` sí puede desplegar el valor `None`.

```python
>>> print(nulo)
None
```

### Despliegue con formato

Para intercalar valores dentro de un formato específico de texto se utiliza el carácter sobre-escritura `%` seguido de uno de los siguientes caracteres.

Caracter de escape|Modo de despliegue
------------------|------------------
s                 |cadena de texto
d                 |entero
o                 |octal
x                 |hexadecimal
f                 |punto flotante
e                 |punto flotante en formato exponencial

El uso de `%s`, equivale a aplicar la función `str()` al valor a desplegar.
Después del texto, se añade otro signo `%` y las expresiones o nombres correspondientes entre paréntesis y separados por comas. Si sólo es una expresión o nombre, no es necesario utilizar el paréntesis.

Ejemplo:

```python
>>> pi = 3.141592
>>> radio = 2
>>> print("El perímetro de un circulo de radio %d es %f." % (radio, 2 * radio * pi))
El perímetro de un circulo de radio 2 es 12.566368.
>>> print("El perímetro de un circulo de radio %d es %d." % (radio, 2 * radio * pi))
El perímetro de un circulo de radio 2 es 12.
>>> print("El perímetro de un circulo de radio %s es %s." % (radio, 2 * radio * pi))
El perímetro de un circulo de radio 2 es 12.566368.
>>> print("El valor de pi es %f." % (pi))
El valor de pi es 3.141592.
>>> print("El valor de pi es %e." % pi)
El valor de pi es 3.141592e+00.  
```

>Para desplegar el signo de porcentaje "%" se utiliza `%%`.

### Caracteres de escape

Existen algunos caracteres que por su función o por la sintaxis de Python -tales como los apóstrofes, las comillas, los retornos de línea, etc.- que deben utilizar un "caracter de escape", para que puedan ser desplegados. Los caracteres de escape pueden ser introducidos después de una diagonal invertida `\`.

Secuencia|Despliegue
---------|----------
\n       |Retorno de línea
\t       |Tabulador
\\"      |Comillas
\\'      |Apóstrofe
\\\      |Diagonal invertida
\xNN     |Caracter que corresponde al número hexadecimal NN en ASCII
\uNN     |Caracter que corresponde al número hexadecimal NN en Unicode

## Entrada estándar con `input()`

La función `input()` captura los caracteres provenientes de entrada estándar (el teclado) hasta que se introduce un [Enter] y el contenido capturado es devuelto al intérprete como una cadena de texto.
La cadena de caracteres resultante puede ser almacenada como un objeto de tipo _str_ mediante la asignación de un nombre.
La función permite desplegar un mensaje de tipo _str_ como parámetro.

La sintaxis es la siguiente:

> `input(<objeto tipo str>)`

Ejemplos:

```python
>>> input()
[Hola]
'Hola'
>>> texto = input()
[Hola]
>>> type(texto)
str
>>> texto
'Hola'
>>> print(texto)
Hola
>>> nombre = input("Escribe un nombre: ")
>>> print(nombre)
Escribe un nombre: [Juan]
Juan
```

## Tipos de datos

* **Tipado dinámico**

Python es un lenguaje que no requiere que se defina el tipo de un objeto. El intérprete "infiere" el tipo de dato del que se trata.

* **Fuertemente tipado**

Existen operaciones que no están permitidas entre tipos que no sean compatibles.

* **Los tipos son clases**

En Python todos sus elementos son objetos y los datos una vez identificados, se convierten en objetos instanciados del tipo al que pertenecen.

### Números enteros (int)

Python identifica a los número enteros como un tipo de dato el cual puede ser expresado de la siguiente manera.

>**_Decimal:_**
>
> 24, 60
>
>**_Binario:_**
>
>0b010011, 0b1101
>
>**_Hexadecimal:_**
>
>0x18, 0x3cf4
>
>**_Octal:_**
>
>030, 074

### Números de punto flotante (float)

Los objetos tipo float corresponden al conjunto de los números reales.

```python
3.141595
12.0
-45.3556
```

Hay que tomar en cuenta de que la precisión de los números dependen en gran medida de la capacidad del equipo de cómputo, por lo que en ocasiones una operación con números de tipo float no dará el resultado exacto, sino una aproximación.

### Números complejos (complex)

Los objetos de tipo complex corresponden al conjunto de los números complejos.

Siempre que el componente en los números reales sea distinto de 0, los objetos de tipo complex se expresarán como un par de números de tipo float separados por el operador de adición `+`, en el que el primer número corresponde al componente en los números reales y el componente en los números imaginarios es identificado añadiéndole la letra `j` al final.

```python
6.32 + 45j
0.117j
(2 + 0j)
1j
```

### Valores booleanos (bool)

El tipo booleano es una especie de tipo numérico que es utilizado para evaluar expresiones lógicas.

Si la expresión lógica es cierta, el resultado es **True** (con mayúscula al principio).
Si la expresión lógica NO es cierta, el resultado es **False** (con mayúscula al principio).
`False` equivale numéricamente a `0`. Cualquier otro número equivale a `True` y su valor por defecto es `1`.

### Cadenas de caracteres (str)

Las cadenas de caracteres son secuencias de caracteres encerradas entre comillas `" "` o apóstrofes `' '` indistintamente.

```python
'Hola Mundo'
"Vamos al McDonald's"
None
```

El tipo None representa un valor "vacío"

### Funciones relativas a tipos de datos

* `type()`

Entre otras cosas, type regresa el tipo de dato de una variable.

* `str()`

Transforma a un objeto compatible en una cadena de caracteres.

* `int()`

Transforma un objeto compatible a un objeto tipo int.

* `float()`

Transforma a un objeto compatible a uno de tipo float.

* `complex()`

Transforma a un objeto compatible a uno de tipo complex.

* `bool()`

Transforma en booleano a un objeto.

### Listas

Python tiene varios tipos de datos compuestos, usados para agrupar otros valores. El más versátil es la **_lista_**, la cual puede ser escrita como una lista de valores separados por coma (ítems) entre corchetes. Las listas pueden contener ítems de diferentes tipos.

```python
>>> cuadrados = [1, 4, 9, 16, 25]
>>> cuadrados
[1, 4, 9, 16, 25]
```

Las listas pueden ser indexadas y rebanadas:

```python
>>> cuadrados[0]  # índices retornan un ítem
1
>>> cuadrados[-1]
25
>>> cuadrados[-3:]  # rebanadas retornan una nueva lista
[9, 16, 25]
```

Todas las operaciones de rebanado devuelven una nueva lista conteniendo los elementos pedidos. Esto significa que la siguiente rebanada devuelve una copia superficial de la lista:

```python
>>> cuadrados[:]
[1, 4, 9, 16, 25]
```

Las listas también soportan operaciones como concatenación:

```python
>>> cuadrados + [36, 49, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

A diferencia de las cadenas de texto, que son inmutables, las listas son un tipo mutable y es posible cambiar un su contenido.

```python
>>> letras = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> letras
['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> # reemplazar algunos valores
>>> letras[2:5] = ['C', 'D', 'E']
>>> letras
['a', 'b', 'C', 'D', 'E', 'f', 'g']
>>> # ahora borrarlas
>>> letras[2:5] = []
>>> letras
['a', 'b', 'f', 'g']
>>> # borrar la lista reemplazando todos los elementos por una lista vacía
>>> letras[:] = []
>>> letras
[]
```

Es posible anidar listas (crear listas que contengan otras listas), por ejemplo:

```python
>>> a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]
>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'
```

#### Métodos de los objetos _lista_

* `list.append(x)`

Agrega un ítem al final de la lista. Equivale a `a[len(a):] = [x]`.

* `list.extend(iterable)`

Extiende la lista agregándole todos los ítems del iterable. Equivale a `a[len(a):] = iterable`.

* `list.insert(i, x)`

Inserta un ítem en una posición dada. El primer argumento es el índice del ítem delante del cual se insertará, por lo tanto `a.insert(0, x)` inserta al principio de la lista, y `a.insert(len(a), x)` equivale a `a.append(x)`.

* `list.remove(x)`

Quita el primer ítem de la lista cuyo valor sea x. Da un error si no existe tal ítem.

* `list.pop([i])`

Quita el ítem en la posición dada de la lista, y lo devuelve. Si no se especifica un índice, `a.pop()` quita y devuelve el último ítem de la lista.

* `list.clear()`

Quita todos los elementos de la lista. Equivalente a `del a[:]`.

* `list.index(x[, start[, end]])`

Devuelve un índice basado en cero en la lista del primer ítem cuyo valor sea x. Levanta una excepción `ValueError` si no existe tal ítem.
Los argumentos opcionales `start` y `end` son interpretados como la notación de rebanadas y se usan para limitar la búsqueda a una subsecuencia particular de la lista. El `index` retornado se calcula de manera relativa al inicio de la secuencia completa en lugar de con respecto al argumento `start`.

* `list.count(x)`

Devuelve el número de veces que `x` aparece en la lista.

* `list.sort(key=None, reverse=False)`

Ordena los ítems de la lista in situ (los argumentos pueden ser usados para personalizar el orden de la lista, ver `sorted()` para su explicación).

* `list.reverse()`

Invierte los elementos de la lista in situ.

* `list.copy()`

Devuelve una copia superficial de la lista. Equivalente a `a[:]`.

### Conjuntos

Python también incluye un tipo de dato para conjuntos. Un conjunto es una colección no ordenada y sin elementos repetidos. Los usos básicos de éstos incluyen verificación de pertenencia y eliminación de entradas duplicadas. Los conjuntos también soportan operaciones matemáticas como la unión, intersección, diferencia, y diferencia simétrica.

Las llaves o la función `set()` pueden usarse para crear conjuntos. Para crear un conjunto vacío hay que usar `set()`, no `{}`; esto último crea un _diccionario_ vacío.

Ejemplo:

```python
>>> canasta = {'manzana', 'naranja', 'manzana', 'pera', 'naranja', 'banana'}
>>> print fruta                  # muestra que se removieron los duplicados
{'pera', 'manzana', 'banana', 'naranja'}
>>> 'naranja' in canasta         # verificación de pertenencia rápida
True
>>> 'yerba' in canasta
False

>>> # veamos las operaciones para las letras únicas de dos palabras

>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a                                  # letras únicas en a
{a', 'r', 'b', 'c', 'd'}
>>> a - b                              # letras en a pero no en b
{'r', 'b', 'd'}
>>> a | b                              # letras en a o en b o en ambas
{'a', 'c', 'b', 'd', 'm', 'l', 'r', 'z'}
>>> a & b                              # letras en a y en b
{'a', 'c'}
>>> a ^ b                              # letras en a o b pero no en ambos
{'b', 'd', 'm', 'l', 'r', 'z'}
```

### Diccionarios

Los diccionarios se encuentran a veces en otros lenguajes como “memorias asociativas” o “arreglos asociativos”. Los diccionarios se indexan con claves, que pueden ser cualquier tipo inmutable; las cadenas y números siempre pueden ser claves. No es posible usar listas como claves, ya que las listas pueden modificarse usando asignación por índice, asignación por sección, o métodos como `append()` y `extend()`.
Un diccionario es un conjunto no ordenado de pares _clave:valor_, con el requerimiento de que las claves sean únicas (dentro de un diccionario en particular). Un par de llaves crean un diccionario vacío: `{}`. Colocar una lista de pares _clave:valor_ separados por comas entre las llaves añade pares _clave:valor_ iniciales al diccionario; esta también es la forma en que los diccionarios se presentan en la salida.

Las operaciones principales sobre un diccionario son guardar un valor con una clave y extraer ese valor dada la clave. También es posible borrar un par _clave:valor_ con `del`. Si se usa una clave que ya está en uso para guardar un valor, el valor que estaba asociado con esa clave se pierde. Es un error extraer un valor usando una clave no existente.

El método `list(d.keys())` en un diccionario devuelve una lista de todas las claves usadas en el diccionario, en un orden arbitrario, y `sorted(d.keys())` las devuelve ordenadas. Para controlar si una clave está en el diccionario, se una `in`.

Ejemplo:

```python
>>> tel = {'jack': 4098, 'sape': 4139}
>>> tel['guido'] = 4127
>>> tel
{'sape': 4139, 'jack': 4098, 'guido': 4127}
>>> tel['jack']
4098
>>> del tel['sape']
>>> tel['irv'] = 4127
>>> tel
{'jack': 4098, 'irv': 4127, 'guido': 4127}
>>> list(tel.keys())
['irv', 'guido', 'jack']
>>> sorted(tel.keys())
['guido', 'irv', 'jack']
>>> 'guido' in tel
True
>>> 'jack' not in tel
False

# El constructor dict() crea un diccionario directamente desde secuencias de pares clave-valor:
>>> dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])
{'sape': 4139, 'jack': 4098, 'guido': 4127}
```

## Operadores

### Operadores aritméticos

Operador|Descripción
--------|-----------
+       |Suma
-       |Resta
-       |Negativo
*       |Multiplicación
**      |Exponente
/       |División
//      |División entera
%       |Residuo

#### Reglas de precedencia

1. Paréntesis.
2. Exponente.
3. Multiplicación.
4. División.
5. Suma.
6. Sustracción.  

### Operadores para objetos de tipo str

Operador|Descripción
--------|-----------
+       |Suma
*       |Repetición

```python
>>> "hola" + "mundo"
'holamundo'
>>> 'hola' * 3
'holaholahola'
```

### Operadores de relación

Los operadores de relación evalúan si dos valores/objetos cumplen con una condición específica. El resultado de esta evaluación es un objeto de tipo bool.

Operador|Evalúa
--------|------
==      |a == b ¿a igual a b?
!=      |a != b ¿a distinta de b?
\>      |a > b ¿a mayor que b?
<       |a < b ¿a menor que b?
\>=     |a >= b ¿a mayor o igual que b?
<=      |a <= b ¿a menor o igual que b?

#### Operadores lógicos

Operador|Evalúa
--------|------
or      |a or b ¿Se cumplen a o b?
and     |a and b ¿Se comple a y b?
not     |not x Contrario a x

#### Operadores de pertenencia

Los operadores `in` y `not in` evalúan si un objeto se encuentra dentro de otro.

```python
>>> 'a' in 'Hola'
True
>>> 'z' in 'Hola'
False
>>> 'la' not in 'Hola'
False
>>> 'z' not in 'Hola'
True
```

### Operadores de asignación

Los operadores de asignación se utilizan para enlazar un objeto/valor con un nombre.

Operador|Descripción
--------|-----------
=       |x = y
+=      |x += y equivale a x = x + y
-=      |x -= y equivale a x = x - y
\*=     |x \*= y equivale a x = x * y
\**=    |x \** = y equivale a x = x ** y
/=      |x /= y equivale a x = x / y
//=     |x //= y equivale a x = x // y
%=      |x %= y equivale a x = x % y

## Control de flujo

### Condicionales

#### Sentencia `if`

La palabra clave if siempre evalúa una expresión lógica y en caso de que dicha expresión de por resultado el valor `True`, se ejecutará el código indentado justo por debajo del `if`. En caso de que la declaración resulte en el valor `False`, el intérprete ignorará el bloque de código indentado y éste continuará con la instrucción siguiente inmediata a la indentación.
Es posible evaluar más de una expresión lógica mediante el uso de `elif`. En el caso de que exista más de una expresión lógica que de por resultado `True`, Python ejecutará solamente el código delimitado por la primera que ocurra.
En caso de que ninguna de las condiciones de por resultado `True` se puede utilizar `else` al final de la estructura.

```python
<flujo principal>
...
...
if <expresión lógica>:
     <bloque inscrito a if>
<flujo principal>
```

Ejemplo:

```python
>>> x = int(input("Ingresa un entero, por favor: "))
Ingresa un entero, por favor: 42
>>> if x < 0:
...      x = 0
...      print('Negativo cambiado a cero')
... elif x == 0:
...      print('Cero')
... elif x == 1:
...      print('Simple')
... else:
...      print('Más')
...
'Mas'
```

### Iteraciones

#### Sentencia `while`

Python cuenta con la palabra reservada `while` para ejecutar un bloque de código recursivamente mientras se cumpla una condición determinada. Cuando la expresión lógica evaluada por `while` sea `False` , el flujo de ejecución continuará sin ejecutar el bloque dentro de `while`.

```pyton
<flujo principal>
...
...
while <expresión lógica>:
     <bloque inscrito a while>
<flujo principal>
```

El bucle while se ejecuta mientras la condición sea verdadera. En Python, como en C, cualquier entero distinto de cero es verdadero; cero es falso. La condición también puede ser una cadena de texto o una lista, de hecho cualquier secuencia; cualquier cosa con longitud distinta de cero es verdadero, las secuencias vacías son falsas.

```pyton
>>> # Series de Fibonacci:
... # la suma de dos elementos define el siguiente
... a, b = 0, 1
>>> while b < 10:
...     print(b)
...     a, b = b, a+b
...
1
1
2
3
5
8
```

#### Interrupciones de ejecución de un bloque

En ciertas circunstancias es necesario interrumpir el flujo lógico de un programa. Python cuenta con los siguientes recursos para hacerlo.

* La palabra reservada `continue`

Termina de forma prematura la ejecución de un bloque dentro de un ciclo.

* La palabra reservada `break`

Termina prematuramente la ejecución del bloque de código en el que se encuentra y restablece el flujo de ejecución al bloque de código que lo precede.

* La función `exit()`

Termina la ejecución de un programa y cierra el intérprete de Python.

#### Sentencia `for`

Una de las grandes fortalezas de Python es su capacidad de realizar iteraciones de forma dinámica a partir de diversos tipos de objetos con la capacidad de ser iterables.

Para iterar un objeto iterable se utiliza la siguiente sintaxis:

>`for <contador> in <objeto iterable>:`

```pyton
>>> # Midiendo cadenas de texto
... palabras = ['gato', 'ventana', 'defenestrado']
>>> for p in palabras:
...     print(p, len(p))
...
gato 4
ventana 7
defenestrado 12
```

Si se necesita iterar sobre una secuencia de números, es apropiado utilizar la función `range()`

#### Sentencia `range()`

Genera progresiones aritméticas

```pyton
>>> for i in range(5):
...     print(i)
...
0
1
2
3
4
```

Para definir rangos numéricos:

* `range(n, m, s)`

    cumple: rango `>= n` and rango `< m` en incrementos de `s`.

* `range(n, m)`

    cumple: rango `>= n` and rango `< m` en incrementos de 1.

* `range(m)`

    cumple: rango `>= 0` and rango `< m` en incrementos de 1.

```pyton
for contador in range(26, 10, -4):
... print(contador)
26
22
18
14
```

## Funciones

### Definición de una función

En Python, las funciones son objetos. De forma general, las funciones en Python se definen de la siguiente manera:  
La palabra reservada `def` se usa para definir funciones. Debe seguirle el nombre de la función y la lista de parámetros formales entre paréntesis.

```pyton
def <nombre>(<parámetros>):
    <código>
```

Las funciones se invocan de la siguiente manera:

```python
<nombre>(<argumentos>)
```

Ejemplo:

```python
>>> def fib(n):  # escribe la serie de Fibonacci hasta n
...     """Escribe la serie de Fibonacci hasta n."""
...     a, b = 0, 1
...     while a < n:
...         print(a, end=' ')
...         a, b = b, a+b
...     print()
...
... fib(2000)
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

La sentencia `return` devuelve un valor en una función.  
`return` sin una expresión como argumento retorna `None`. Si se alcanza el final de una función, también se retorna `None`.

La _ejecución_ de una función introduce una nueva tabla de símbolos usada para las variables locales de la función. Más precisamente, todas las asignaciones de variables en la función almacenan el valor en la tabla de símbolos local; así mismo la referencia a variables primero mira la tabla de símbolos local, luego en la tabla de símbolos local de las funciones externas, luego la tabla de símbolos global, y finalmente la tabla de nombres predefinidos. Así, no se les puede asignar directamente un valor a las variables globales dentro de una función (a menos se las nombre en la sentencia global), aunque si pueden ser referenciadas.

Los parámetros reales (argumentos) de una función se introducen en la tabla de símbolos local de la función llamada cuando esta es ejecutada; así, los argumentos son pasados por valor (dónde el valor es siempre una referencia a un objeto, no el valor del objeto). Cuando una función llama a otra función, una nueva tabla de símbolos local es creada para esa llamada.

La definición de una función introduce el nombre de la función en la tabla de símbolos actual. El valor del nombre de la función tiene un tipo que es reconocido por el interprete como una función definida por el usuario.