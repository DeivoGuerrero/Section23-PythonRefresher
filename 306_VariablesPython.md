# Variables

Es el nombre para un valor en python

Por ejemplo podemos definir la variable `x` y podemos guardar un valor dentro de esta variables como `15`. 
Para definir el valor a una variable usamos `=`

`x = 15`

Ahora tambien podemos reutilizar varias variables para la definición de una nueva variable, por ejemplo.

```python
price = 9.99
discount = 0.2

result = price * (1 - discount)

# Podemos imprimir el valor de una variable con print() que es una función, algo que veremos más adelante
print(result)
```

---

Tabien exite otro tipo de datos llamados `strings` o cadenas de caracteres, podemos definir un string haciendo uso de comillas secillas `'` o comillas dobles `"`

```python
name = "Rolf"

print(name) # Rolf
print(name*2) # RolfRolf
```

---

```python
a = 25
b = a

print(a) # 25
print(b) # 25

b = 17

print(a) # 25
print(b) # 17
```