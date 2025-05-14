# First class funtions
# Funciones de primera clase

Significa que las funciones solo son variables y pueden pasarse como argumentos a las funciones y usarlas de las misma manera que usaria cualquier otra variables.

```python
def divide(dividend, divisor):
    if divisor == 0:
        raise ZeroDivisionError("Divisor cannot be 0.")
    return dividend / divisor

def calculate(*values, operator):
    return operator(*values)

result = calculate(20, 4, operator=divide)
print(result) # 5.0
```

Como vemos podemos paras la funcion `divide` como parametro, lo importante es no pasarla con `()` porque eso lo que hace es llamar a la función y se estaría ejecutando, en casos asi lo que estarimamos pasando es el resltado de dicha función.

```python
def search(sequence, expected, finder):
    for elem in sequence:
        if finder(elem) == expected:
            return elem
    raise RuntimeError(f"Could not find an element with {expected}")

friends = [
    {"name": "Rolf Smith", "age": 24},
    {"name": "Adam wool", "age": 30},
    {"name": "Anne Pun", "age": 27},
]

def get_friend_name(friend):
    return friend["name"]

print(search(friends, "Rolf Smith", get_friend_name))
# {"name": "Rolf Smith", "age": 24}
```

Este es un ejemplo de donde podemos aplicar tambien un lambda funtion por ejemplo:

```python
def search(sequence, expected, finder):
    for elem in sequence:
        if finder(elem) == expected:
            return elem
    raise RuntimeError(f"Could not find an element with {expected}")

friends = [
    {"name": "Rolf Smith", "age": 24},
    {"name": "Adam wool", "age": 30},
    {"name": "Anne Pun", "age": 27},
]

print(search(friends, "Rolf Smith", lambda friend: friend["name"]))
# {"name": "Rolf Smith", "age": 24}
```

Tambien existe una libreria para realizar lo mismo `itemgetter`.

```python
from operator import itemgetter

def search(sequence, expected, finder):
    for elem in sequence:
        if finder(elem) == expected:
            return elem
    raise RuntimeError(f"Could not find an element with {expected}")

friends = [
    {"name": "Rolf Smith", "age": 24},
    {"name": "Adam wool", "age": 30},
    {"name": "Anne Pun", "age": 27},
]

print(search(friends, "Rolf Smith", itemgetter("name")))
# {"name": "Rolf Smith", "age": 24}
```