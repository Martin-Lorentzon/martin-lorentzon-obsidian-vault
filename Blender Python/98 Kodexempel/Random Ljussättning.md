```python
import bpy
import random
# Detta skriptet skapar 3 slumpade pointlights

lights  = bpy.data.lights
objects = bpy.data.objects

for i in range(0, 3):
    # Färg
    r = random.random()  # Tal mellan 0 och 1
    g = random.random()
    b = random.random()
    # Position
    pos_x = random.randint(-5, 5)  # Tal mellan -5 och 5
    pos_y = random.randint(-5, 5)
    pos_z = random.randint(-5, 5)
    # Skapa pointlight
    light_data = lights.new("Random Light Data", "POINT")
    light_data.color = (r, g, b)
    light_data.energy = random.randint(20, 500)
    # Skapa objektet
    light_object = objects.new("Random Light Object", light_data)
    light_object.location = (pos_x, pos_y, pos_z)
    # Länka objektet till scenen
    bpy.context.scene.collection.objects.link(light_object)
```
### Förklaring
Med `lights.new("Random Light Data", "POINT")` skapar vi oss ett nytt data-block av typen [light](https://docs.blender.org/api/current/bpy.types.Light.html#bpy.types.Light), och slumpmässigt ändrar på värdet av dess `color` och `energy` attributer med `random`.
För att vår ljuskälla ska synas i scenen tilldelar vi den ett objekt och länkar objektet till den aktiva scenen. Detta upprepas tre gånger.
### Saknar ett användargränssnitt
Detta skriptet saknar ett UI och måste köras genom Blenders text-editor.
> [!todo] Frivillig uppgift
>Om ni vill testa att designa ett användargränssnitt fungerar koden bra som utfyllnad för gränssnittets funktionalitet. Placera koden i en operator och inkludera den i en ny panel. Se till att klasserna registreras.
