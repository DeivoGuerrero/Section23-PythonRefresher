# Default funtion parameter values

Podemos asignar valores por defecto al momento que definamos una función, la funcion tomará este valor por defecto cuando no se le pase como argumento algún valor

```python
def say_hello(name="World"):
    print(f"Hello {name}!")

say_hello() # Hello Wolrd!
```

Tener en cuenta que cambiar el valor de un parametro que se esta usando por defecto, no modificará la funcion, porque el valor que adquiere es cuando se define la fución

```python
default_x = 3
def add(x=default_x, y):
    sum = x + y
    print(sum)

add(2) # 5

default_x = 4

add(2) # 5
```