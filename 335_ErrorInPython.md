# Errors in Python

Empecemos con un ejemplo 

```python
def divide(dividend, divisor):
    if divisor == 0:
        print("Divisor canot be 0.")
        return
    return dividend / divisor

grades = []
print("Welcome to the average grade program.")
average = divide(sum(grades), len(grades))

print(f"The average grade is {average}.")
# Ejemplo que mostraria si la lista de grades esta vacia
#----------
# Welcome to the average grade program.
# Divisor canot be 0.
# The average grade is None.
```

Los errores a menudo se usan para el control de flujo de manera muy similar a las declaraciones. Permite a las funciones generen errores y capturarlos en el código (En Python Excepciones y Errores se refieren a lo mismo). Podemos declarar un Error o Excepción con `raise` Y podemos manejar estas exceciones en un bloque `try / except`

Empecemos con un ejemplo 

```python
def divide(dividend, divisor):
    if divisor == 0:
        raise ZeroDivisionError("Divisor cannot be 0.")
    return dividend / divisor

grades = []
print("Welcome to the average grade program.")

try:
    average = divide(sum(grades), len(grades))
    print(f"The average grade is {average}.")
except ZeroDivisionError as e:
    print("There are no grades yet in your list.")

# Si ejecutamos 
# Welcome to the average grade program.
# There are no grades yet in your list.
# --------------- imprimir error ------------
# podemos hacer un print(e) en except y 
# obtendriamos el mensaje: Divisor cannot be 0.
```

Ya hay clases de Errores defidas o creadas como ZeroDivisionError, TypeError, ValueError, RunTimeError, o tambien podemos crear nuestros propias clases para gestionar los errores.

Ahora podemos estar propensos a obtener otro tipo de errores que no estemos manejando, en este caso podemos hacer uso de `else`, lo que se ejecute en este bloque es porque se ejecuto correctamente el `try` y no salto la excepción en `except`, Es decir cuando no oobtuvimos errores.
Incluso podemos ejecutar una un bloque de código independientemente que se haya ejecutrado o no cualquier bloque anterior, definienfo `finally`, veamos un ejemplo.

```python
def divide(dividend, divisor):
    if divisor == 0:
        raise ZeroDivisionError("Divisor cannot be 0.")
    return dividend / divisor

students = [
    {"name": "Bob", "grades": [75, 90]},
    {"name": "Rolf", "grades": []},
    {"name": "Jen", "grades": [100, 90]},
]

try:
    for student in students:
        name = student["name"]
        grades = student["grades"]
        average = divide(sum(grades), len(grades))
        print(f"{name} averaged {average}.")
except ZeroDivisionError:
    print(f"ERROR: {name} has no grades!")
else:
    print("-- All student averages calculated --")
finally:
    print("-- End of student average calculation --")

# Si ejecutamos:
# Bob averaged 82.5.
# ERROR: Rolf has no grades!
# -- End of student average calculation --
```