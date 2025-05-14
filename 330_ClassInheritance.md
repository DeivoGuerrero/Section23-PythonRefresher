# Class inheritance

La herencia permite que una clase tome algunos métodos y propiedades de otra clase

```python
class Device:
    def __init__(self, name, connected_by):
        self.name = name
        self.connected_by = connected_by
        self.connected = True

    def __str__(self):
        # {self.name!r} hace que se imprima entre ''
        return f"Device {self.name!r} ({self.connected_by})"

    def disconnect(self):
        self.connected = False
        print("Disconnected.")

printer = Device("Printer", "USB")
print(printer) # Device 'Printer' (USB)
printer.disconnect() # Disconnected.
```

Tenemos una clase que nos permite crear dispositivos, como primer ejemplo tenemos una impresora, pero digamos que tambien queremos agregarle funcionalidades a esta impresora, como imprimir hojas.

```python
class Device:
    def __init__(self, name, connected_by):
        self.name = name
        self.connected_by = connected_by
        self.connected = True

    def __str__(self):
        # {self.name!r} hace que se imprima entre ''
        return f"Device {self.name!r} ({self.connected_by})"

    def disconnect(self):
        self.connected = False
        print("Disconnected.")

# De esta forma decimos que la clase Printer hereda de la clase Device
# quiere decir que en esencia tendrá los mismos métodos
class Printer(Device):
    # Para crear una impresora, tendrá que tener los mismos parametros
    # para crear un Device, pero le podemos decir que además tenga
    # un atributo "capacity" que dirá cuantas hojas le quedan
    def __init__(self, name, connected_by, capacity):
        # En vez de crear asignar cada variable con self,
        # ej: self.name = name... lo que haremos es llamar
        # el constructor de la clase Device
        super().__init__(name, connected_by)
        # Ahora ya podemos definir las propiedades de la clase Printer
        self.capacity = capacity # Capacidad total
        self.remaining_pages = capacity # Capacidad restante actual
        
        def __str__(self):
            return f"{super().__str__()} ({self.remaining_pages} pages remaining)"

        def print(self, pages):
            if not self.connected:
                print("Your printer is not connected!")
                return
            print(f"Printing {pages} pages.")
            self.remainig_pages -= pages

printer = Printer("Printer", "USB", 500)
printer.print(20) # Printing 20 pages.
print(printer) # Device 'Printer' (USB) (480 pages remainig)
# Además Printer puede hacer uso de los metodos de Device como disconnect
printer.disconnect() # Disconnected.
# Si intentamos imprimir de nuevo
printer.print(30) # Your printer is not connected!
```