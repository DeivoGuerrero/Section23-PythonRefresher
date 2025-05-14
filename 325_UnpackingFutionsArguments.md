# Unpacking funtion arguments

Para definir un metodo que pueda recibir multiples argumentos, hacemos uso de `*` antes del argumento, por buenas practicas se recomienda usar `*args`, todos los parametros que le mantemos a la función se almacenaran en una tupla que se guardaran como `args`

Ejemplo función de multiplicación

```python
def multiply(*args):
    total = 1
    for arg in args:
        total = total * arg
    return total

print(multiply(1, 3, 5)) # 15
```

Ejemplo, desempaquetar valores de lista como parametros

```python
def add(x, y):
    return x + y

nums = [3, 5]
# Es necesario tener el mismo numero de valores
# como de parametros, si no retornará error.
print(add(*nums)) # 8
```


Ejemplo, desempaquetar valores de un diccionario como parametros

```python
def add(x, y):
    return x + y

nums = {"x": 3, "y": 5}
# Es necesario que el nombre de los argumentos
# y de las llaves del diccionario sean iguales.
print(add(**nums)) # 8
```

Ejemplo función de multiples argumentos y argumento final necesario

```python
def multiply(*args):
    total = 1
    for arg in args:
        total = total * arg
    return total

# Podemos paras varios argumentos,
# pero el ultimo tiene que ser
# el que define operator
def apply(*args, operator):
    if operator == "*":
        # debemos pasar los argumentos uno por
        # unohaciendo uso de *, caso contrario,
        # pasamos la tupla como un argumento
        # y el metodo recepcionará una tupla
        # de tuplas tipo: ((1, 3, 6, 7), )
        return multiply(*args)
    elif operator == "+":
        return sum(args)
    else:
        return "No valid operator provided to apply()"

# Es importante que se debe definir el nombre 
# del argumento cuando se llame la función, 
# caso contrario se lo tomará como parte de 
# los args y retornará error.
print(apply(1, 3, 6, 7, operator="+")) # 17
print(apply(1, 3, 6, 7, operator="*")) # 15
```