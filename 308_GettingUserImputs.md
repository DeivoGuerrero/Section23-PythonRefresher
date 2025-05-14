# User Inputs

lo podemos hacer usando el método input(), por ejemplo:

```python
name = input("Enter your name: ")
print(name)
```

Hay que tener en cuenta que `input`, siempre retornará un `str` (string), importante tener en cuenta cuando querramos trabajar con numeros.

```python
size_input = input("How big is your house (in square feet): ")
square_feet = int(size_input)
square_metres = square_feet / 10.8
print(square_metres)
```

Observar que nuestro input lo convertimos a tipo de dato `int`, y este lo guardamos en una variable llamada `square_feet`, incluso tener en cuenta que cuando usamos esta variable para definir la variable `square_metres`, al dividir el valor este será de tipo de valor `float`

Podemos hacer que la impresión sea más clara y formatear el print de salida de la siguiente forma.
`print(f"{square_feet}" square feet is {square_metres:.2f} square metres.)`
Notando que con `{square_metres:.2f}` definimos que esta variable al ser de tipo float solo imprima 2 decimales.