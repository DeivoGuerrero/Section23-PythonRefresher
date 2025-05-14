# String Formating in Python

```python
name = "Bob"
greeting = f"Hello, {name}"

print(greeting) # Hello, Bob

name = "Rolf"

print(greeting) # Hello, Bob
```
Cuando se usa f"" en una variables, imprime sus variables obtenidas es ese momento, no las obtiene dinamicamente, pero si usamos print(), vemos que obtenemos ahora el nombre de Rolf porque hacemos de llamada a la variable, entonces vuelve a obtener el valor que tenga la variable en ese momento

```python
name = "Bob"
print(f"Hello, {name}") # Hello, Bob

name = "Rolf"

print(f"Hello, {name}") # Hello, Rolf
```

Hay una forma de definir una plantilla.

```python
name = "Bob"
greeting = "Hello, {}"
with_name = greeting.format(name)
with_name_two = greeting.format("Rolf")

print(with_name) # Hello, Bob
print(with_name_two) # Hello, Rolf
```

Se puede crear plantillas más largas, donde podemos manejar más variables, dependiento del orden que asignemos las variables estas rempazaran cada uno de los `{}` que tengamos en la plantilla.

```python
longer_phrase = "Hello, {}. Today is {}"
formatted = longer_phrase("Rolf", "Monday")

print(formatted) # Hello, Rolf. Today is Monday
```
