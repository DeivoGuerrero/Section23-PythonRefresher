# Type hinting

Nos permite indicar el tipo de variables y retornos que tendrán nuestras funciones.

Por ejemplo, una función que calcula el promedio de una lista, nada nos impide hacer llamado y pasarle un entero, y esto resultando en un mensaje de error
```python
def list_avg(sequence):
    return sum(sequence) / len(sequence)

list_abg(123) # TypeErrpr: 'int' object is not iterable 
```

Entonces como le decimos a una función que lo que debe recibir es una lista, aqui entra el `Type hinting`

```python
def list_avg(sequence: list) -> float:
    return sum(sequence) / len(sequence)

list_abg(123) # TypeErrpr: 'int' object is not iterable 
```

Como vemos podemos identificar el tipo de dato de los argumentos con `:` seguido del tipo de dato que esperamos. Para el ejemplo usamos `list`, aunque se recomienda como buena practica hacer lllamado a la libretia `typing`.
Para definir el tipo de dato de retorno de la función, despues de los parentesis `()` de los argumentos de la función agregar `->` y luego el tipo de dato que retornara, en este caso `float`
Algunos IDEs te pueden mostrar algunos errores para informarte que estas pasando un tipo de dato que no espera una función.

---

Ejemplo de como quedaría código anterior de la libreria con type hinting.

```python
from typing import List
class Bookshelf:
    def __init__(self, *books: List[Book]):
        self.books = books

    def __str__(self) -> str:
        return f"Bookshlef with {len(self.books)} books"

class Book:
    TYPES = ("hardcover", "paperback")

    def __init__(self, name: str, book_type: str, weight: int):
        self.name = name
        self.boo_type = book_type
        self.weight = weight

    def __repr__(self) -> str:
        return f"<Book {self.name}, {self.book_type}, weighting {self.wight}g>"

    @classmethod
    # Para retornar la clase misma donde esta implementado la funcion
    # representar con el nombre de la clase entre comillas
    # es un objeto que se esta llamando mientras se crea
    def hardcover(cls, name: str, page_weight: int) -> "Book":
        return cls(name, cls.TYPES[0], page_weight + 100)

    @classmethod
    def paperback(cls, name: str, page_weight: int) -> "Book":
        return cls(name, cls.TYPES[1], page_weight)
```