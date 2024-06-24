För att ta användning av Blenders Python API behöver ni först importera `bpy`-modulen, detta gör ni i början av skriptfilen
```python
import bpy
```
I många fall kommer ni vilja importera fler moduler för annan funktionalitet, detta gör ni på samma sätt
```python
import bpy
import os
import json
```
## Importera kod i ett multi-file add-on
Med ett multi-file add-on kommer ni behöva importera kod från närliggande filer. För att importera kod relativ till er skriptfil använder ni er utav punkter
```python
import bpy
from . import material_manager
```
*En* punkt antyder att filen ligger i samma mapp som er skriptfil, två punkter antyder mappen över.
Om er kod ligger inuti en mapp *managers* på samma nivå som er skriptfil använder ni syntaxen-
```python
import bpy
from .managers import material_managers
```