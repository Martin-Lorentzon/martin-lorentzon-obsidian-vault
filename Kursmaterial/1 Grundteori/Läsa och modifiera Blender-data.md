Attributen ``bpy.data`` använder ni för att komma åt och skapa ny Blender-data som sparas med blend-filen. Med `bpy.data` kan ni få ut lite allt möjligt som objekt, meshar, material, nod-grupper och mer. Såhär kan ni exempelvis uppdatera namnet på alla material med ett prefix
```python
import bpy

materials = bpy.data.materials  # Skapa en referens till alla material

for mat in materials:         # För varje material...
	name = mat.name           # Läs av namnet
	new_name = f"XYZ_{name}"  # Lägg till prefixen "XYZ_"
	mat.name = new_name       # Uppdatera namnet av materialet
```
För en överblick av vad ``bpy.data`` innehåller se [BlendData(bpy_struct) - Blender Python API](https://docs.blender.org/api/current/bpy.types.BlendData.html#bpy.types.BlendData)
## Kodexempel - Random ljussättning
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
    # Skapa pointlight data-block
    light_data = lights.new("Light Data", "POINT")
    light_data.color = (r, g, b)
    light_data.energy = random.randint(20, 500)
    # Skapa objektet
    light_object = objects.new("Light", light_data)
    light_object.location = (pos_x, pos_y, pos_z)
    # Länka objektet till scenen
    bpy.context.scene.collection.objects.link(light_object)
```
Med `lights.new("Light", "POINT")` skapar vi oss ett nytt data-block av typen [light](https://docs.blender.org/api/current/bpy.types.Light.html#bpy.types.Light)
Och slumpmässigt modifierar värdet av dess `color` och `energy` attributer.
För att vår pointlight ska existera i scenen ger vi den ett objekt och länkar objektet till scenen - detta kan kännas invecklat till en början, men ni vänjer er strax.
# bpy.context