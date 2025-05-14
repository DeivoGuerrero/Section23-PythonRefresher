# Listas, tuplas y sets

Son colectores que nos permiten guardar varias variables en una variable

## Listas (list)
Se identifican porque las definimos con `[]` y cada uno de sus elementos los separamos con `,`.

```python
lista = ["Bob", "Rolf", "Anne"]
# Para acceder a un valor hacemos uso de un subindice
print(lista[0])
# Para agregar un elemento hacemos uso de append() para agregar al final de la lista
lista.append("Smith")
# Para elminar elementos hacemos uso de remove()
lista.remove("Smith")
```

## Tuplas
Se identifican porque las definimos con `()` y cada uno de sus elementos los separamos con `,`. La diferencia con uan lista es que no se puede agregar o eliminar elementos, solo estan los que se asignan al momento de la creación de la variables
```python
tupla = ("Bob", "Rolf", "Anne")
# Para acceder a un valor hacemos uso de un subindice
print(tupla[0])
```

## Sets
Se identifican porque las definimos con `{}` y cada uno de sus elementos los separamos con `,`. La diferencia es que, al igual que una lista se pueden agregar o eliminar elementos pero estos no pueden estar duplicados. Además estos no guardan un orden, a diferencia de una lista o una tupla, puede cambiar.

```python
mi_set = {"Bob", "Rolf", "Anne"}
# Para agregar un valor hacemos uso de add()
mi_set.add("Smith")
```