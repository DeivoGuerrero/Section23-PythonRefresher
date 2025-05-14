# Class composition

Hace que las clases sean más simples y reduce la complejidad del código en general
Por ejemplo un caso de Estanteria (BookShlef) y Libros (Book)

```python
class Bookshelf:
    def __init__(self, quantity):
        self.quantity = quantity

    def __str__(self):
        return f"Bookshlef with {self.quantity} books"

shelf = Bookshelf(300)
print(shelf) # Bookshlef with 300 books

# --------- Si intentamos realizar herencia --------------

class Book(Bookshlef):
    def __init__(self, name, quantity):
        super().__init__(quantity)
        self.name = name

    def __str__(self):
        return f"Book {self.name}"

book = Book("Harry Poter", 120)
print(book) # Book Harry Poter
```

Pero hay dos problemas en realizar herencia en este caso
1. Conceptual: Cuando se realiza una herencia se tiene un concepto evolutivo cuando tenemos Book(Bookshlef) decimos Book es una Bookshlef y algo más. y Book es algo completamente diferente a una Bookshlef. Estanteria contiene libro pero , un libro no es una estanteria
2. La razon técnica es que Book esta heredando de Bookshlef pero no esta usando nada dentro de Bookshlef, además no tiene sentido definir la cantidad de un Bookshlef en la creación de Book

Aqui es donde entra la Composición, es cuando quieres decir una clase esta compuesta por varios objetos.

```python
class Bookshelf:
    def __init__(self, *books):
        self.books = books

    def __str__(self):
        return f"Bookshlef with {len(self.books)} books"

class Book():
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"Book {self.name}"

book = Book("Harry Poter")
book2 = Book("Python 101")
shelf = Bookshelf(book, book2)

print(shelf) # Bookshlef with 2 books
```