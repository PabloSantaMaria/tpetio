# Guía de referencia rápida de **_Python_**

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
...
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
Un diccionario es un conjunto no ordenado de pares _clave:valor_, con el requerimiento de que las claves sean únicas (dentro de un diccionario en particular). Un par de llaves crean un diccionario vacío: ``{}``. Colocar una lista de pares _clave:valor_ separados por comas entre las llaves añade pares _clave:valor_ iniciales al diccionario; esta también es la forma en que los diccionarios se presentan en la salida.

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

Operador  |  Descripción
--|--
+  |  Suma
-  |  Resta
-  |  Negativo
*  |  Multiplicación
**  |  Exponente
/  |  División
//  |  División entera
%  |  Residuo

#### Reglas de precedencia

1. Paréntesis.
2. Exponente.
3. Multiplicación.
4. División.
5. Suma.
6. Sustracción.  

### Operadores para objetos de tipo str

Operador  |  Descripción
--|--
+  |  Suma
*  |  Repetición

```python
>>> "hola" + "mundo"
'holamundo'
>>> 'hola' * 3
'holaholahola'
```

### Operadores de relación

Los operadores de relación evalúan si dos valores/objetos cumplen con una condición específica. El resultado de esta evaluación es un objeto de tipo bool.

Operador  |  Evalúa
--|--
==  |  a == b ¿a igual a b?
!=  |  a != b ¿a distinta de b?
\> |  a > b ¿a mayor que b?
< |  a < b ¿a menor que b?
\>=  |  a >= b ¿a mayor o igual que b?
<= |  a <= b ¿a menor o igual que b?

#### Operadores lógicos

Operador  |  Evalúa
--|--
or  |  a or b ¿Se cumplen a o b?
and  |  a and b ¿Se comple a y b?
not |  not x Contrario a x

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

Operador  |  Descripción
--|--
=  |  x = y
+=  |  x += y equivale a x = x + y
-=  |  x -= y equivale a x = x - y
\*=  |  x \*= y equivale a x = x * y
\**=  |  x \** = y equivale a x = x ** y
/=  |  x /= y equivale a x = x / y
//=  |  x //= y equivale a x = x // y
%=  |  x %= y equivale a x = x % y

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