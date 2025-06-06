
В этом уроке познакомимся с правилами преобразования аргумента и узнаем, как работать с составными выражениями и двойным отрицанием.

## Правила преобразования

Оператор **ИЛИ** работает так, что его выполнение слева направо прерывается и возвращается результат первого аргумента, который можно преобразовать в `True`. Если такого аргумента нет, возвращается последний — правый.

Посмотрите на пример:

```python
print(0 or 1)  ## 1
```

В данном случае, число `0` эквивалентно `False`, а число `1` эквивалентно `True`. Таким образом, оператор **ИЛИ** вернет `1`, так как это первый аргумент, который может быть преобразован в `True`.

Возьмем пример посложнее:

```python
print(0 or False or '' or [] or 42 or "Hello")  ## 42
```

В данном случае:

- Число `0` эквивалентно `False`
- Значение `False` уже является `False`
- Пустая строка (`''`) эквивалентна `False`
- Пустой список (`[]`) эквивалентен `False`
- Число `42` эквивалентно `True`
- Строка `"Hello"` также эквивалентна `True`

Оператор **ИЛИ** будет проверять значения слева направо, и возвращает первый аргумент, который может быть преобразован в `True`. В данном примере это число `42`.

Пример с оператором **И**:

```python
print(0 and 1)  ## 0
```

Оператор **И** работает так, что его выполнение слева направо прерывается и возвращается результат первого аргумента, который можно преобразовать в `False`. Если такого аргумента нет, возвращается последний — правый.

```python
print(42 and "Hello" and [] and 0)  ## []
```
В данном случае:

- Число `42` эквивалентно `True`
- Строка `"Hello"` эквивалентна `True`
- Пустой список (`[]`) эквивалентен `False`
- Число `0` эквивалентно `False`

Оператор **И** будет проверять значения слева направо и возвращать первый аргумент, который может быть преобразован в `False`. В данном примере это пустой список (`[]`).

В Python есть два правила преобразования:

* `0`, `0.0`, `''` и `None` приводятся к `False`. Эти значения называют **falsy**. Сюда входят еще другие типы данных, которые мы  будем изучать на Хекслете
* Все остальное приводится к `True`

Этими правилами пользуются в разработке, например, чтобы определить значение по умолчанию:

```python
value = name or ''
# Примеры
234 or '' # 234
'hexlet' or '' # 'hexlet'
None or '' # ''
```

Если `name` примет одно из falsy-значений, переменной `value` будет присвоена пустая строка. В этом случае в последующем коде мы сможем работать с `value` как со строкой.

Но здесь есть потенциальный баг. Если `name` содержит falsy значение, а переменной `value` можно присвоить значения типа `0`, `False`, `None`, то код выше заработает неверно:

```python
# Значение на самом деле есть,
# но оно Falsy, поэтому не выбирается на условии OR
False or '' # ''
0 or '' # ''
None or '' # ''
```

## Составные выражения

Если соединить логические выражения между собой, можно получать довольно интересные способы решения задач с кодом.

Допустим, нам нужно реализовать код, в котором в переменную записывается:

* Строка `yes`, если число четное
* Строка `no`, если нечетное

Это можно сделать, если использовать знания, полученные выше:

```python
# число четное
result = 10 % 2 == 0 and 'yes' or 'no' # 'yes'
# или сразу печатаем на экран
print(10 % 2 == 0 and 'yes' or 'no') # => 'yes'
# число нечетное
print(11 % 2 == 0 and 'yes' or 'no') # => 'no'
```

Эти выражения работают согласно порядку и приоритетам. Приоритет присваивания самый низкий, поэтому оно происходит в конце. Приоритет сравнения `==` выше, чем приоритет логических операторов `and` и `or`, поэтому сравнение происходит раньше. Дальше код выполняется слева направо, так как приоритет `and` выше, чем приоритет `or`. Рассмотрим по шагам:

```python
# Для четного
# 1 шаг
10 % 2 == 0 # True
# 2 шаг
True and 'yes' # Результат — 'yes'
# Проверка на or выполняется, но правая часть не исполняется, так как сразу возвращается 'yes'

# Для нечетного
# 1 шаг
11 % 2 == 0 # False
# 2 шаг
False and 'yes' # Результат — ложь, проверяем дальше
# 3 шаг
False or 'no' # Выбирается и возвращается 'no'
```

Такую же схему можно использовать с любым выражением в начале:

```python
print(somefunc() and 'yes' or 'no')
```

## Двойное отрицание

Напомним, как выглядит операция отрицания:

```python
answer = True
print(not answer)  # => False
```

При двойном отрицании итоговое значение равно начальному:

```python
answer = True
print(not not answer)  # => True
```

Оператор `not` всегда возвращает булевое значение, независимо от типа переданного аргумента, а не заменяет значение на противоположное. Поэтому двойное отрицание тоже вернет булевое True/False.

```python
answer = 'python'
print(not answer) # => False
print(not not answer) # => True
```

## Ошибка выбора

Представьте, что нам нужно проверить — значение равно одному или другому. Например, переменная `value` должна содержать одно из двух значений: `first` или `second`. Начинающие разработчики иногда записывают это выражение так:

```python
value == ('first' or 'second')
```

Однако такой код приведет к неверному результату. Необходимо вспомнить приоритет выполнения операций. Первым делом вычисляется все, что указано в скобках — `'first' or 'second'`. Если выполнить этот код в Replit, то вывод будет таким:

```bash
python
Python 3.8.2 (default, Apr 12 2020, 15:53:37)
>>> 'first' or 'second'
'first'
>>>
```

Теперь заменим исходное выражение на частично вычисленное:

```python
value == 'first'
```

Совсем не то, что мы ожидали. А теперь вернемся к началу и напишем проверку правильно:

```python
# Скобки ставить не обязательно,
# потому что приоритет == выше чем приоритет or
value == 'first' or value == 'second'
```
