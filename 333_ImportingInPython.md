# Importing in Python

Como ejemplo trabajaremos con 2 archivos de python, y vamos hacer la importación de uno dentro de otro para ver el funcionamiento.

```python
""" mymodule.py """
def divide(dividend, divisor):
    return dividend / divisor

print("mymodule.py:", __name__) # mymodule.py: __main__
```

De donde se ejecute el archivo python, su variable `__name__` será `__main__`
Ahora importemos este archivo en otro archivo python

```python
""" code.py """
#Importamos la divide de mymodule
from mymodule import divide
# Podemos importar todo el contenido con:
# import mymodule
# Luego podemos usar sun propiedades
# mymodule.divide()

print(divide(10, 2)) 
# mymodule.py: mymodule
# 5.0
print(__name__)
# __main__
```

Entonces, ¿Cómo sabe Pyhton donde está mymodule.py?
Para entender mejor importaremos sys.

```python
import sys

print(sys.path)

"""
[
    '/home/deivo/Documentos/Develop/examples', 
    '/usr/lib/python312.zip', 
    '/usr/lib/python3.12', 
    '/usr/lib/python3.12/lib-dynload', 
    '/usr/local/lib/python3.12/dist-packages', 
    '/usr/lib/python3/dist-packages'
]
"""
# Retorna una lista de directorios.
# El primero es donde se encuentra ubicado el archivo que estamos ejecutando,
# El segundo es la ruta donde se encuentra la variable de entorno de python que estemos corriendo
# Y a continuación los diferentes directorios que tenga importados python

```

En Unix/Linux podemos agregar más directorios la path de python con `export PYTHONPATH=/Users` por ejemplo o la ruta que deseemos.
---

Para continuar con el ejemplo, crearemos una estructura como esta:

```
333_ImportPython/
├── mymodule.py
├── code.py
└── libs/
    └── mylib.py
```
```python
# libs/mylib.py
print("mylib.py", __name__)
```

```python
# mymodule.py
def divide(dividend, divisor):
    return dividend / divisor

print("mymodule.py:", __name__)

import libs.mylib
```

```python
# code.py 
import mymodule

```

Entonce desde `code.py` imporrtamos `mymodule.py` y este hace un import de `lib/mylib.py`.
Si ejecutamos `code.py` nos retorna algo como:

```bash
mymodule.py: mymodule
mylib.py libs/mylib
```

> Si se esta usando Python2 es necesario crerar dentro de cada directorio nuevo, en este caso `lib` un archivo llamado `__init__.py` para que se pueda realizar un import de algun archio dentro de este directorio.

# 334. Relative imports in Python 

Supongamos que a nuestro proyecto anterior, agregamos un nievo directorio y archivo en libs, similar a la siguiente estructura:

~~~
333_ImportPython/
├── mymodule.py
├── code.py
└── libs/
    ├── mylib.py
    └── operations/
        └── operator.py
~~~

Entonces haciendo las importaciones quedaria algo como

```python
# libs/operations/operator.py
print("operator.py: ", __name__)
```

```python
# libs/mylib.py
from libs.operations import operator
print("mylib.py: ", __name__)
```

```python
# mymodule.py
from libs import mylib
print("mymodule.py: ", __name__)
```

```python
# code.py 
import mymodule
print("code.py: ", __name__)
```

Si ejecutamos de nuevo desde `code.py` nos imprimirá algo como:

```bash
operator.py: libs.operations.operator
mylib.py: libs.mylib
mymodule.py: mymodule
code.py: __main__
```

Como vemos, se ejecuta primero operator.py, porque al momento de hacer un import, carga primero el import antes de continuar con el código. A esto anterior se le llama Importaciones Absolutas.

Hablemos de Importaciones relativas: Son aquellas que pueden importar desde la carpeta actual en la que se encunetra el archivo, pero no puede importar a menos que el nombre de carpeta en la ruta de importacion en la ruta del módulo, la caracteristeca es que tenemos que indicar el directorio de donde queremos partir con la etiqueta `from`

```python
# code.py 
import mymodule
print("code.py: ", __name__)

from libs.operations import operator
```

```python
# libs/operations/operator.py
print("operator.py: ", __name__)
## Regresamos 2 niveles con ..
## Importamos todo el contenido de mylib con *
from ..mylib import *
```

> Tener en cuenta que cuando realicemos un DEBUG, este tipo de importaciones no funcionarian, porque su funcionamiento esta condicionada a que se ejecute desde el archivo `__main__` definido al momento de hacer los imports.