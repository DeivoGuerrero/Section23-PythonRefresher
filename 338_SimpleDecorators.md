# Simple decorators in Python

Nos permite modificar funciones. Por ejemplo:

```python
user = {"username": "jose", "access_level": "guest"}

def get_admin_password():
    return "1234"

def secure_get_admin():
    if user["access_level"] == "admin":
        return "1234"

print(secure_get_admin()) # None
print(get_admin_password()) # 1234
```

Como vemos con la función secure_get_admin no nos permite impprimir la contraseña de admin, pero entonces si queremos agregar esta seguridad, tendremos que agregar las validaciones de seguridad en todos los metodos que la requieran.
Para evitar esto o mejor dicho para agregar cierta funcionalidad o caracteristicas a una función.
Para este caso, lo que buscamos es dar seguridad a la funcion cuando se la llama, no cuando se la define.


```python
user = {"username": "jose", "access_level": "guest"}

def get_admin_password():
    return "1234"

# Le especificamos que va a recibir como parametro una funcion
def make_secure(func):
    def secure_function():
        if user["access_level"] == "admin":
            return func
        # Podemos agregar más funcionalidad como
        else:
            return f"No admin permissions for {user['username']}."
    # Aqui loque hacemos es hacer un llamado a la funcion secure_function
    return secure_funtion

# Mi primera funcion get_admin_password se volverá segura
# pasandola por la función make_secure
# make_secure define una función interna secure_function()
# secure_function() verifica si el acces_level == admin
# Si es así retorna la función que se le paso a make_secure
# es decir la función get_admin_password
get_admin_password = make_secure(get_admin_password)
print(get_admin_password()) # None

# Si cambiamos el access_level a admin, retorna 1234
```

De esa forma podemos crear una función en este caso más segura que remplaza la función inicial. 

---

# 339 'at' @ Sintax for decorators

Quizas puede resultar un poco extraño de ver que se reemplaza la función, pero podemos expresarlo de una forma más ordenada, tomando el ejemplo anterior:


```python
user = {"username": "jose", "access_level": "guest"}

def make_secure(func):
    def secure_function():
        if user["access_level"] == "admin":
            return func
        else:
            return f"No admin permissions for {user['username']}."
    return secure_funtion

# Pero si tiene que estar definida despues de el decorador a usar
# @make_secure reemplaza a `get_admin_password = make_secure(get_admin_password)`
@make_secure
def get_admin_password():
    return "1234"

print(get_admin_password()) # No admin permissions for jose.

user = {"username": "jose", "access_level": "admin"}
print(get_admin_password()) # 1234
```

Hay un problema que sucede con los decoradores, es que si bien la función `get_admin_password` la podemos usar dentro de nuestro código y no existe conflico, pero imprimiento `__name__` de la funcion vemos que ya no hace llamado a la función con el mismo nombre.
Un conflicto haciendo DEBUG y en realizr la documentación del código.

```python
print(get_admin_password.__name__) # secure_funtion
```

Para solucionar esto lo que podemos hacer es hacer uso de otro decarador de la libreria `functools`

```python
import functools
#...
def make_secure(func):
    @functools.wraps(func)
    def secure_function():
        if user["access_level"] == "admin":
            return func
        else:
            return f"No admin permissions for {user['username']}."
    return secure_funtion
#...
print(get_admin_password.__name__) # get_admin_password
```
---

# 340 Decorating funtions with parameters

Ahora, que pasa si tenemos una función que posea parametros, por ejemplo nuestra funcion `get_admin_password()` modificarla y que ahora nos estregue la contraseña de un panel recibido como parámetro, llamando a la función ahora `get_password(panel)`.

```python
@makesecure
def get_password(panel):
    if panel == "admin":
        return "1234"
    elif panel == "billing":
        return "super_secure_passwrod"

```

Ahora podriamos hacer que `secure_function` reciba el parametro y retorne la función con el parámetro.
```python

def make_secure(func):
    @functools.wraps(func)
    def secure_function(panel):
        if user["access_level"] == "admin":
            return func(panel)
        else:
            return f"No admin permissions for {user['username']}."
    return secure_funtion

```

Pero esto lo que haria es que este decorator `make_secure` solo funcione especificamente para la funcion `get_password(panel)`, o almenos nos limitará al uso de metodo especificamente con 1 parametro.
Aqui podemos aplicar el desempaquetado de argumentos de función ![Unpacking Funtions Arguments](325_UnpackingFutionsArguments.md)

```python

def make_secure(func):
    @functools.wraps(func)
    def secure_function(*args, **kwargs):
        if user["access_level"] == "admin":
            return func(*args, **kwargs)
        else:
            return f"No admin permissions for {user['username']}."
    return secure_funtion

```
---

# 341 Decorators with parameters

Para hacer que un decorador reciba parametros, debemos encapsularlo en otra función que reciba esos parametros, luego ese parámetro debe actuar dentro de la función segura que la requiera. Ejemplo.

```python
user = {"username": "jose", "access_level": "guest"}

def make_secure(access_level):
    def decorator(func):
        def secure_function():
            if user["access_level"] == access_level:
                return func
            else:
                return f"No {access_level} permissions for {user['username']}."
        return secure_funtion
    # Debemos hacer llamado a decorador inicial.
    return decorator

# Ahora podemos pasar el acces_level requerido para cada funcion
@make_secure("admin")
def get_admin_password():
    return "1234"

@make_secure("guest")
def get_dashboard_password():
    return "user: user_password"

print(get_admin_password())# No admin permissions for jose.
print(get_dashboard_password()) # user: user_password

user = {"username": "anna", "access_level": "admin"}

print(get_admin_password())# 1234
print(get_dashboard_password()) # No guest permissions for anna.

```