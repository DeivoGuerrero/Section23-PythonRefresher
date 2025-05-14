# Usos de Sets

Tomemos un ejemplo de 2 set definidos, uno de amigos y otro de amigos en el extrangero, en acaso se identificar los amigos que se encuentran localmente podemos hacer uso de una funcion de ser llamada `difference()`. por ejemplo:

```python
friends = {"Bob", "Rolf", "Anne"}
abroad = {"Bob", "Anne"}

local_friends = friends.difference(abroad)
print(local_friends) # {"Rolf"}

# difference tiene un sentido
# y elimina los elemntos del primer
# conjunto en el otro conjunto

example_two = abroad.difference(friends)
print(example_two) # set() # Conotación set vacio
```

---

Tambien existe un metodo de set para calcular el total de dos conjuntos de set con el metodo `union`por ejemplo.

```python
local = {"Rolf"}
abroad = {"Bob", "Anne"}

friends = local.union(abroad)
print(local) # {"Anne", "Bob", "Rolf"}
```

---

Tambien existe otro método para identificar los elementos comunes entre dos conjuntos, llamado `intersection`

```python
art = {"Bob", "Jen", "Rolf", "Charlie"}
science = {"Bob", "Jen", "Adam", "Anne"}

both = art.intersections(science)
print(both) # {"Jen", "Bob"}
```

---
