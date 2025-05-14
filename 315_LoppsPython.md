# Loops in Python

Hay dos tipos de bucles uno que nos permite repetir un cierto numero de código un cierto numero de veces. y otro que nos permite repetir el codigo mientras la condición sea verdadera.

## while loop

```python
number = 7

# Ciclo infinito
while True:
    user_input = input("Would you like to play? (Y/n)")
    if user_input == "n":
        break # Rompe el ciclo
    user_number = int(input("Guess our number: "))
    if user_number == number:
        print("You guessed correcly!")
    elif abs(number - user_number) == 1:
        print("You were off by one.")
    else:
        print("Sorry, it's wrong!")

```

## for loop

```python
friends = ["Rolf", "Jen", "Bob", "Anne"]

# Imprimir cada elemento de una lista
for friend in friends:
    print(f"{friend} is my friend.")
```

Calcular el promedio de los valores de una lista

```python
grades = [35, 67, 98, 100, 100]
total = 0
amount = len(grades)

for grade in grades:
    total += grade

#Puedes usar metodo sum y evitar usar el ciclo for
total = sum(grades)

print(total / amount)
```