# Lis Comprehensions

Nos permiten crear nuevas listas sobre la marcha a partir de listas

```python
numbers = [1, 3, 5]
doubled = []

for num in numbers:
    doubled.append(num * 2)

# Podemos usar un lis comprehension
# para crear lo mismo

doubled = [num * 2 for num in numbers]
```

Otro ejemplo a partir de una lista de amigos, crear una lista de amigos que su nombre comience con "S"

```python
friends = ["Rolf", "Sam", "Samantha", "Sauraph", "Jen"]
starts_s = [friend for friend in friends if friend.startswith("S")]
```

