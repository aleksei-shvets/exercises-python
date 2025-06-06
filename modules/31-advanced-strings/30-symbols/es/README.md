
A veces es necesario obtener un solo carácter de una cadena. Por ejemplo, si un sitio web conoce el nombre y apellido del usuario, y en algún momento se requiere mostrar esta información en el formato *A. Ivanov*. Para lograr esto, la computadora necesita tomar el primer carácter del nombre. En Python, hay una operación adecuada que estudiaremos hoy.

Supongamos que queremos mostrar en pantalla solo la primera letra del nombre "Alexander". Se vería así:

```python
first_name = 'Alexander'

print(first_name[0])  # => A
```

La operación con corchetes y un número extrae el elemento por su **índice** - la posición del carácter dentro de la cadena. Los índices comienzan en 0 en casi todos los lenguajes de programación. Por lo tanto, para obtener el primer carácter, debemos especificar el índice `0`. El índice del último elemento es igual a la longitud de la cadena menos uno. Acceder a un índice fuera de los límites de la cadena resultará en un error:

```python
# La longitud de la cadena es 9, por lo que el último índice es 8
first_name = 'Alexander'

print(first_name[8])  # => r

print(first_name[9])
IndexError: string index out of range
```

Para reforzar los nuevos conocimientos, eche un vistazo al siguiente código y piense en qué imprimirá:

```python
magic = '\nyou'
print(magic[1])  # => ?
```

También hay situaciones que no son estándares o comunes. Por ejemplo, es posible que necesitemos mostrar un elemento desde el final, y además, desde una expresión con un gran número de caracteres. En este caso, podemos usar un índice negativo, que facilitará el trabajo del programador.

Se pueden usar índices negativos. En este caso, se accede a los caracteres desde el final de la cadena. `-1` es el índice del último carácter, `-2` es el penúltimo, y así sucesivamente. A diferencia de la indexación directa, el recuento inverso comienza desde `-1`:

```python
first_name = 'Alexander'

print(first_name[-1])  # => r
```

El índice puede ser no solo un número específico, sino también el valor de una variable. Mire el siguiente ejemplo. Aquí hemos escrito el índice dentro de los corchetes como una variable. Este código dará el mismo resultado, es decir, mostrará en pantalla el carácter *A*:

```python
first_name = 'Alexander'
index = 0

print(first_name[index])  # => A
```


Para mostrar solamente algunos caracteres de una expresión, no es necesario escribir una gran cantidad de líneas de código, simplemente extraiga el elemento utilizando un índice. También puede usar un índice negativo para facilitar la extracción de caracteres desde el final de la expresión. A continuación, veremos cómo usar estos conocimientos para extraer subcadenas de una cadena.
