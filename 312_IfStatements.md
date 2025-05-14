# If Statements

Tener en cuenta que para definir una sentencia de comparación, iniciamos con la paralabra reservada `if`, esto compará la evaluación booleana de acontinuación, y finaliza su línea de sentencia de comparación con `:` y en la línea siguiente con una identación, se colocará el código que se ejecutará en caso de que la sentacia sea verdadera.

```
dia_semana = input("Que día de la semana es hoy?: ")

if día_semana == "Lunes":
    print("Ten un buen inicio de semana!")

# Codígo fuera del if statement
print("Mensje que se imprime siempre")
```

Ahora tambien se puyeden anidar los if statements con otras palabras reservadas como lo son `else` `elif`, tienen que tener definido siempre antes un `if`.
La sentencia `else` no define ninguna sentencia de comparación, solo se define y ejecuta en caso que la sentencia anterior no se cumpla.
La sentencia `elif` se cumple cuando la sentencia anterior no se cumple pero se tiene que definir la sentencia que se le defina.

| `if` Siempre tiene que iniciar la sentencia de comparación, `else` siempre tiene que estar al final de las sentencias

```python
dia_semana = input("Que día de la semana es hoy?: ")

if dia_semana == "Lunes":
    print("Ten un buen inicio de semana!")
elif dia_semana == "Martes":
    print("Es Martes!")
else:
    print("Eso fue rápido")

# Codígo fuera del if statement
print("Mensje que se imprime siempre")
```