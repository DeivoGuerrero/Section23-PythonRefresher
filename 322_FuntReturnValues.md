# Funtions returning values

Funciones que no retornan ningun valor, retornan `None`

```python
def add(x,y):
    print(x + y)

add(5, 8) # 13
result = add(5, 8) # 13
print(result) # None
```

Algo muy diferente es retornar un valor, lo hacemos con `return`.
Tambien tener en cuenta que cuando se ejecuta `return` hara que se salga de la función y si hay algo posterior del return no se ejecutará

```python
def add(x,y):
    return x + y

add(5, 8) # No imprime nada en pantalla
result = add(5, 8) # No imprime nada en pantalla
print(result) # 13
```

