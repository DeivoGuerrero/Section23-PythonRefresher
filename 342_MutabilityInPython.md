# Mutability in Python

Imaginemos el siguiente código

```python
a = []
b = a

print(id(a)) # 139932162509632
print(id(b)) # 139932162509632
```

Lo que se concluye es que `a` y `b` son nombres para el mismo objeto, el `id` es la posición en memoria.
Incluso si hacemos `a.append(35)`, ambas variables se actualizan por que apuntan a la misma lista.
Caso contrario cuando:

```python
a = []
b = []

print(id(a)) # 139932162509632
print(id(b)) # 139932162511424
```

Esto representa que las listas son mutables, algunos valores son inmutables.
En Python todo es mutable porque todo es un objeto a menos que se le especifique. por ejemplo las tuplas, strings, enteros, floats y booleans

# 343 Mutable default parameters

Porque es importante la mutabilidad en Python.
Observemos el siguiente código:

```python
from typing import List

class Student:
    def __init__(self, name: str, grades: List[int] = []): # This is bad
        self.name = name
        self.grades = grades

    def take_exam(self, result: int):
        self.grades.append(result)

bob = Student("Bob")
rolf = Student("Rolf")
bob.take_exam(90)

print(bob.grades) # [90]
print(rolf.grades) # [90]

```

Aqui vemos el problema cuando creamos el Student rolf, pero este sin ejecutar take_exam ya posee grades.
Es por eso que la mutabilidad es importante en Python.
Los parámetros de la función predeterminados evalúan cuando la función se define, no cuando se la llama (es por eso que es mala idea de definir).
Sucede que cuando esta creando el primer usuario, se crea una lista y se le aplica el nombre `grades`, entonces cuando crea un nuevo Student, el contructor evalua y ve que esa lista creada ya tiene asignado un nombre y hace llamdo a esa misma variable.

```python
from typing import List, Optional

class Student:
    def __init__(self, name: str, grades: Optional[List[int]] = None):
        self.name = name
        self.grades = grades or []

    def take_exam(self, result: int):
        self.grades.append(result)

bob = Student("Bob")
rolf = Student("Rolf")
bob.take_exam(90)

print(bob.grades) # [90]
print(rolf.grades) # []

```