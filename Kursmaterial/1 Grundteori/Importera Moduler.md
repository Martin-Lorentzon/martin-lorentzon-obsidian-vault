För att överhuvudtaget kunna nyttja Blenders Python API måste ni först importera bpy-modulen, detta gör ni i början av skriptfilen
```python
import bpy
```
I vissa fall kommer ni behöva importera fler moduler för särskild funktionalitet, detta gör ni på samma sätt
```python
import bpy
import os
import json
```
I ett multi-file add-on kommer ni behöva importera kod från närliggande filer, för att importera kod relativ till er init-fil använder ni er utav punkter
```python
import bpy
from . import material_manager
```
*En* punkt antyder att filen ligger i samma mapp som er init-fil, två punkter antyder mappen över.
Om er kod ligger inuti en mapp `managers` på samma nivå som er init-fil använder ni syntaxen
```python
import bpy
from .managers import material_managers
```