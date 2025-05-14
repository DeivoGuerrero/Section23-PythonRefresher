# Lambda funtions

Tipo de función que no tiene un nombre y solo se usa para devolver valores.
Se usan exclusivamente para operar entradas y salidas de retorno.

```python
def add(x, y):
    return x + y

print(add(5, 7)) # 12

# Podemos realizar la misma función con lambda
# podemos guardar la función como variable
add = lambda x, y: x + y
# podemos hacer llamado a la funcion
print(add(5, 7)) # 12

# Pero tambien podemos usarla en la misma 
# linea sin guardarla con un nombre
# Tenemos que enserrarla entre parecntesis
# Y en los siguientes parentesis asignar los
# Parametro x, y definidos, haciendo que
# esta función se ejecute.
print( (lambda x, y: x + y)(5,7) ) # 12
```

```python
def double(x):
    return x*2

sequence = [1, 3, 5, 9]
doubled = [double(x) for x in sequence]
# Tambien podriamos usar
# doubled = [x*2 for x in sequence]
# Pero es en caso que la cunción sea más complicada

# Tenemos un metodo llamado map(), lo que hace es 
# recorrer cada elemento de una lista y aplocar una función
doubled = map(double, sequence)

# Ejemplo con lambda, sin necesidad de crear la función double 
doubled = [(lambda x: x*2)(x) for x in sequence]
# Importante si queremos retornar una lista debemos combertir el
# elemento map
doubled = list(map(lambda x: x*2, sequence))
```
