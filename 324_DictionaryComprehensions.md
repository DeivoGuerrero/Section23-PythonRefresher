# Dictionary comprehentions

Muy similares a List comprehensions, pero en retornar un diccionaro.

```python
users = [
    (0, "Bob", "password"),
    (1, "Rolf", "bob123"),
    (2, "Jose", "longp4ssword"),
    (3, "username", "1234"),
]

username_mapping = {user[1]: user for user in users}
print(username_mapping)
# {'Bob': (0, "Bob", "password"), 
# 'Rolf': (1, "Rolf", "bob123"), 
# 'Jose': (2, "Jose", "longp4ssword"), 
# 'username': (3, "username", "1234")}

# Como puede ser util, podemos imprimir los valores de Bob
# en una sola linea
print(username_mapping['Bob'])

# Si no tuvieramos un maping tendriamos algo como:

for user in users:
    if user[1] == 'Bob':
        print(user)

# Un ejemplo de donde podemos tener algo practico
# puede ser en la validación de inicio de sesión

username_input = input("Enter your username: ")
password_input = input("Enter your password: ")

_, username, password = username_mapping[username_input]

if password_input == password:
    print("Log In!")
else:
    print("Wrong credentials")
```

