
Los programas que escribimos en el curso se vuelven más complejos y extensos. Aunque todavía están lejos de ser programas reales, ya nos hacen esforzarnos un poco más.

En esta lección, nos adentraremos en uno de los temas básicos más difíciles de la programación: los **ciclos**.

Las aplicaciones de software ayudan a gestionar empleados, finanzas y pueden ser entretenidas. A pesar de las diferencias, todas ellas ejecutan algoritmos incorporados en ellas, que son similares. Un **algoritmo** es una secuencia de acciones que conduce a un resultado esperado.

Imaginemos que tenemos un libro y queremos encontrar una frase específica en él. Recordamos la frase, pero no sabemos en qué página está. Tendremos que revisar las páginas secuencialmente hasta encontrarla. Este proceso se llama algoritmo.

Un algoritmo implica comprobaciones lógicas y recorrer las páginas. No se sabe de antemano cuántas páginas habrá que revisar, pero el proceso de revisión se repite de la misma manera. Para realizar acciones repetitivas, se necesitan ciclos. Cada repetición se llama **iteración**.

Escribamos una función con un ciclo simple que imprima la cadena `'Hello!'` `n` veces en la pantalla:

```python
def print_hello(n):
    counter = 0
    while counter < n:
        print('Hello!')
        counter = counter + 1

print_hello(2)
# => Hello!
# => Hello!
```

Ahora analicemos un ejemplo de una función con un ciclo que imprime los números del 1 al número pasado como argumento:

```python
print_numbers(3)
# => 1
# => 2
# => 3
```

No se puede implementar esta función con los medios que ya hemos aprendido, ya que no se conoce de antemano la cantidad de impresiones en pantalla. Pero con los ciclos no hay problemas:

```python
def print_numbers(last_number):
    # i es una abreviatura de índice
    # se utiliza por convención en muchos lenguajes
    # como contador del ciclo
    i = 1
    while i <= last_number:
        print(i)
        i = i + 1
    print('finished!')

print_numbers(3)
# => 1
# => 2
# => 3
# => finished!
```


El ciclo `while` consta de tres elementos:

* La palabra clave `while`
* El predicado: una condición que se especifica después de `while` y se evalúa en cada iteración
* El bloque de código: el cuerpo del ciclo

Cada ejecución del cuerpo se llama **iteración**. En el ejemplo anterior, `print_numbers(3)` provocó tres iteraciones, en cada una de las cuales se imprimió la variable `i` en la pantalla. La construcción se lee así: "haz lo que se especifica en el cuerpo del ciclo mientras la condición `i <= last_number` sea verdadera".

Analicemos cómo funciona este código para la llamada `print_numbers(3)`:

```python
# Se inicializa i
i = 1

# El predicado es verdadero, por lo que se ejecuta el cuerpo del ciclo
while 1 <= 3
# print(1)
# i = 1 + 1

# Se ha completado el cuerpo del ciclo, por lo que se vuelve al principio
while 2 <= 3
# print(2)
# i = 2 + 1

# Se ha completado el cuerpo del ciclo, por lo que se vuelve al principio
while 3 <= 3
# print(3)
# i = 3 + 1

# El predicado es falso, por lo que la ejecución pasa después del ciclo
while 4 <= 3

# print('¡finished!');
# En este punto, i es igual a 4, pero ya no lo necesitamos
# La función finaliza
```

El proceso que genera el ciclo debe detenerse. Eso es responsabilidad del programador.

Por lo general, la tarea se reduce a introducir una variable: el **contador del ciclo**. Primero se inicializa, es decir, se le asigna un valor inicial. En nuestro ejemplo, esto se hace con la línea `i = 1`. Luego, en la condición del ciclo, se verifica si el contador ha alcanzado su valor límite.

El valor límite en el ejemplo se determina mediante el argumento de la función. Si la condición del ciclo no se cumple, el cuerpo no se ejecuta y el intérprete pasa a trabajar con las instrucciones después del ciclo.

Si la condición del ciclo es verdadera, se ejecuta el cuerpo, que contiene el elemento de parada: el cambio del contador. Por lo general, esto se hace al final del cuerpo y es el lugar donde no se puede prescindir de una variable. En el ejemplo anterior, el cambio se realiza con la línea `i = i + 1`.

En este punto, los principiantes cometen muchos errores. Por ejemplo, se puede olvidar de incrementar el contador o verificarlo incorrectamente en el predicado. Esto conducirá a un bucle infinito, donde el ciclo se ejecutará indefinidamente y el programa nunca se detendrá. En ese caso, es necesario terminarlo forzosamente.

```python
def print_numbers(last_number):
    i = 1
    # Este ciclo nunca se detendrá
    # y siempre imprimirá el mismo valor
    while i <= last_number:
        print(i)
    print('finished!')
```

En algunos casos, los bucles infinitos son útiles. No vamos a considerar tales situaciones, pero mostraremos cómo se ve este código:

```python
while True:
  # Hacer algo
```

Los ciclos son indispensables cuando el algoritmo para resolver un problema requiere repetir ciertas acciones y la cantidad de estas operaciones no se conoce de antemano.
