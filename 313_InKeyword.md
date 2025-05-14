# In Keyword

Palabra reservada `in` que nos sirve para saber si exite un elemento en una conjunto, su retorno es True o False dependiendo si se encuentra o nl el elemento a buscar.

```python
primos = [1,2,3,5,7,11]
print(3 in primos) # True
```

---

Tambien podemos combianr el uso de `in` con un `if` statement, por ejemplo.

```python
primos = [1,2,3,5,7,11]
if 13 in primos:
    primos.append(13)
    print("Se agregó 13 a primos")
else:
    print("13 Ya existe")
```


