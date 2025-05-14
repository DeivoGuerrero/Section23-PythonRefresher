# Class methods and static methods

Primero un ejemplo de metodos de instancia que son los que hemos visto normalmente.

```python
class ClassTest:
    # Todos los metodos que usen self como parametro
    # Se los denomina metodos de instancia.
    # Si desea usar el objeto
    def instance_method(self):
        print(f"Called instance_method of {self}")

    # Posee como parametro una clase, si no se le asigna nada
    # toma por defecto la clase donde fue creado
    # Para utilizar la clase
    @classmethod
    def class_method(cls):
        print(f"Called class_method of {cls}")

    # Este metodo no requiere de parametros
    # Una funci[on que no tiene relacion con la clase pero vive en ella
    # Para que no utilice ni la clase ni los valores de esta
    @staticmethod
    def static_method():
        print("Called static_method")


test = ClassTest()
test.instance_method() # Called instance_method of <__main__.ClassTest object at ...>
# o Tambien
ClassTest.instance_method(test) # Called instance_method of <__main__.ClassTest object at ...>

# ------- para llamar a class_method --------
ClassTest.class_method() # Called class_method of <class '__main__.ClassTest'>

# ------- para llamar a static_method --------
ClassTest.static_method() # Called static_method
```

---

Realicemos un ejemplo de Factory para ejemplificar mejor estos tipos de metodos.

```python
class Book:
    TYPES = ("hardcover", "paperback")

    def __init__(self, name, book_type, weight):
        self.name = name
        self.boo_type = book_type
        self.weight = weight

    def __repr__(self):
        return f"<Book {self.name}, {self.book_type}, weighting {self.wight}g>"

book = Book("Harry Potter", "hardcover", 1500)
print(book) #<Book Harry Potter, hardcover, weighting 1500g>
```

Queremos evitar que al momento de crear un libro este no se cree con un tipo de libro diferente a los definidos en TYPES. Para ello podemos hacer uso de los `@classmethod`

```python
class Book:
    TYPES = ("hardcover", "paperback")

    def __init__(self, name, book_type, weight):
        self.name = name
        self.boo_type = book_type
        self.weight = weight

    def __repr__(self):
        return f"<Book {self.name}, {self.book_type}, weighting {self.wight}g>"

    @classmethod
    def hardcover(cls, name, page_weight):
        return cls(name, cls.TYPES[0], page_weight + 100)

    @classmethod
    def paperback(cls, name, page_weight):
        return cls(name, cls.TYPES[1], page_weight)

book = Book.hardcover("Harry Potter", 1500)
light = Book.paperback("Python 101", 200)
print(book) #<Book Harry Potter, hardcover, weighting 1600g>
print(light) #<Book Python 101, paperback, weighting 200g>

```