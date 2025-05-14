# Custom Error Classes in Python

Tomemos como ejemplo el siguiente código.

```python
class Book:
    def __init__(self, name: str, page_count: int):
        self.name = name
        self.page_count = page_count
        self.pages_read = 0

    def __repr__(self):
        return f"<{self.title!r}, read {self.pages_read } pages out of {self.page_count}>"

    def read(self, pages: int):
        self.pages_read += pages
        print(f"You have now read {self.pages_read} pages out of {self.page_count}.")

python101 = Book("Python 101", 50)
python101.read(35) # You have now read 35 pages out of 50
python101.read(50) # You have now read 85 pages out of 50
```

Vemos que al final que el número de páginas leidas superan el número total de páginas del libro, apliquemos algunas excepciones.

```python
# Creamos la clase de excepcion
# Hacemos que extienda de ValueError
# Tiene que extender de un Error o Excepcion
# si no no interactua con raise
# Es comun extender de un tipo de error y que la clase
# no haga nada más, es solo para cambiar el nombre
# y poder dar más claridad o contexto al código
class TooManyPagesReadError(ValueError):
    pass

class Book:
    def __init__(self, name: str, page_count: int):
        self.name = name
        self.page_count = page_count
        self.pages_read = 0

    def __repr__(self):
        return f"<{self.title!r}, read {self.pages_read } pages out of {self.page_count}>"

    def read(self, pages: int):
        if self.pages_read + pages > self.pages_count:
            raise TooManyPagesReadError(
                f"You tried to read {self.pages_read + pages} pages, but this book only has {self.pages_count} pages."
            )
        self.pages_read += pages
        print(f"You have now read {self.pages_read} pages out of {self.page_count}.")


# Para evitar que se muestre el Trackback
# Cuando llamemos las funciones que posean raise
# ejecutarlos dentro de un try / except
python101 = Book("Python 101", 50)
try:
    python101.read(35) # You have now read 35 pages out of 50.
    python101.read(50) # -- Aqui salta la excepción --
except TooManyPagesReadError as e:
    print(e) # You tried to read 85 but this book only has 50 pages.
```