# Boolen

Tipo de dato que puede ser True o False, nos ayudaran a definir la lógica de muestro código.

```python
print(5 == 5)
print(5 > 5)
print(10 != 10)

# Comparisons: ==, !=, >, <, >=, <=
```

---

Comparason `is`, realiza una comparación para verificar si es el mismo elemento no si tienen los mismos elementos.

```python
friends = ["Rolf", "Bob"]
abroad = ["Rolf", "Bob"]

print(friends == abroad) # True
print(friends is abroad) # False
```

En este caso son diferentes porque cada variable a creado una nueva lista, esto representa un espcacio de memoria para cada lista creada, ahora si definimos abroad de la siguiente forma.

```python
friends = ["Rolf", "Bob"]
abroad = friends

print(friends == abroad) # True
print(friends is abroad) # True
```
