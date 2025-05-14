# Unpacking keyword arguments

Es cuando pasamos como argumento un diccionario, para recibir los datos es buena practica usar `**kwargs` haciendo referencia que los argumentos se los recibe en formato llave valor.

```python
def named(**kwargs):
    print(kwargs)

named(name="Bob", age=25) # {'name': 'Bob', 'age': 25}

# -------- inverso -----------

def named(name, age):
    print(name, age)

details = {'name': 'Bob', 'age': 25}
named(**details) # Bob 25
```

Ejemplo:

```python
def named(**kwargs):
    print(kwargs)

def print_nicely(**kwargs):
    named(**kwargs)
    for arg, value in kwargs.items():
        print(f"{arg}: {value}")

print_nicely(name="Bob", age=25)
# {'name': 'Bob', 'age': 25}
# name: Bob
# age: 25
```
---

Usar `*args` y `**kwargs` al mismo timepo

```python
def both(*args, **kwargs):
    print(args)
    print(kwargs)

both(1, 3, 5, name="Bob", age=25)
# (1, 3, 5)
# {'name': 'Bob', 'age': 25}
```

--- 

Ejemplo uso

```python
def post(url, data=None, json=None, **kwargs):
    # Podemos ver que icluso agrega otro parametro, y hace
    # llamado a otro metodo llamado request
    return request('post', url, data=data, json=json, **kwargs)

# -----------------------------------------------------


```