# Funtions arguments and parameters

Como le damos datos a nuestras funciones para que estas los usen.

```python
# x, y son Parametros
def add(x, y):
    pass

# 5 y 3 son Argumentos
# C/argumento provee un valor a C/parametro
# 5 valor a x y 3 valor a y
add(5,3)
```

Funciones sin parametros:

```python
def say_hello():
    print("Hello!")

say_hello("Bob") 
# Retorna error, porque la funcion 
# no tiene parametros, por lo tanto,
# no hay que asignar argumentos
# al momento de llamar la funcion
```

En una función tambien podemos hacer uso de argumentos palabras clave, por ejemplo:

```python
def say_hello(name, surnmae):
    print(f"Hello, {name} {surname}")

say_hello(surname="Bob", name="Smith") 
```