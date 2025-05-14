# Magic methods: __str__ and __repr__

Los metodos con doble `__` al comienzo y al final son metodos especiales en python, tambien llamados metodos mágicos.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

bob = Person("Bob", 35)
print(bob) 
# <__main__.Person object at 0x106f9bc70>
# Cadena que representa el objeto bob
```

La información de un objeto puede ser de utilidad para los programadores, pero podemos configurar esta salida y poder dar más detalles o una cadena más acorde, por ejemplo.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    # Debe imprimir algo facil de leer para usuarios
    def __str__(self):
        return f"Person {self.name}, {self.age} years old."

    # Debe imprimir algo de utilidad para los desarrolladores
    def __repr__(self):
        return f"<Person('{self.name}', {self.age})>"

bob = Person("Bob", 35)
print(bob) # Person Bob, 35 years old.

# Para imprimir el repr, podemos hacer
# imprime por defecto en modo Debug
# Comentando el metodo __str__ , o
print(bob.__repr__()) # <Person('Bob', 35)>
```