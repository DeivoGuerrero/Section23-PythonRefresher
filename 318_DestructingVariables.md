# Destructuring variables

para crear una tupla no necesariamente se requiere hacer uso de los parentesis, solo cuando es necesario para que el código no interprete otra cosa

```python
t = 5, 11 # -> Seria una tupla
# Podemos desestructurar esta variable en 2
x, y = t
print(x, y)
```
---
Ya habiamos echo algo similar anteriormente:

```python
student_attendance = {"Rolf": 96, "Bob": 80, "Anne": 100}

for student, attendance in student_attendance.items():
    print(f"{student}: {attendance}")

for t in student_attendance.items():
    print(t)
    # ('Rolf', 96)
    # ('Bob', 80)
    # ('Anne', 100)
```

Ejemplo de lista de tuplas con 3 elementos

```python
people = [
    ("Bob", 42, "Mechanic"), 
    ("James", 24, "Artist"), 
    ("Harry", 32, "Lecturer")
    ]
# Si una de las tuplas no tiene los 3 campos, retornara un indexerror
for name, age, profession in people:
    print(f"Name: {name}, Age: {age}, Profession: {profession}")
```

Dividir una lista en 2 listas, el primer elemento y el resto
```python
head, *tail = [1, 2, 3, 4, 5]
print(head) # 1
print(tail) # [2, 3, 4, 5]
```