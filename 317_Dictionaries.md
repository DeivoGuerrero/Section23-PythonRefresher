# Dictionaries

Son otra estructura de Python, que nos permite interactuar con datos, que los identificamos con llaves o keys

```python
# La llave es Rolf y su valor es 24
friend_ages = {"Rolf": 24, "Adam": 30, "Anne": 27}

print(friend_ages["Adam"]) # 30

#Para agregar o editar un elemento,
# hacemos llamado a su llave
# y asignamos su valor
friend_ages["Bob"] = 20

print(friend_ages) # {"Rolf": 24, "Adam": 30, "Anne": 27, "Bob": 20}
```

Es muy util manejar una lista de diccionarios

```python
friends = [
    {"name": "Rolf", "age": 24},
    {"name": "Adam", "age": 30},
    {"name": "Anne", "age": 27},
]

# Tener en cuenta que para acceder a un
# elemento dentro de una lista, debemos
# hacer uso de su indice

print(friends[1]["name"]) # Adam
```

Imprimir llaves y valores de diccionario

```python
student_attendance = {"Rolf": 96, "Bob": 80, "Anne": 100}

for student in student_attendance:
    # student nos devuelve el nombre de la llave
    # student_attendance[student] accediendo a la lista con la llave
    # obtenemos el valor de la llave solicitada.
    print(f"{student}: {student_attendance[student]}")
    # Rolf: 96
    # Bob: 80
    # Anne: 100

# Tambien podemos separar las variables desde un comienzo con items()
for student, attendance in student_attendance.items():
    print(f"{student}: {attendance}")
```

Para chequear si exite una llave en el diccionario lo hacemos con `in`

```python
student_attendance = {"Rolf": 96, "Bob": 80, "Anne": 100}

if "Bob" in student_attendance:
    print(f"Bob: {student_attendance['Bob']}")
else:
    print("Bob is not a student in this class")
```

Obtener los valores de un diccionario con `values()` y obtener promedio

```python
student_attendance = {"Rolf": 96, "Bob": 80, "Anne": 100}

attendance_values = student_attendance.values()
print(sum(attendance_values) / len(attendance_values)) # 92.0
```