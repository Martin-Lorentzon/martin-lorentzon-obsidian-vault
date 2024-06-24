Attributen ``bpy.data`` använder ni för att komma åt och skapa ny Blender-data som sparas med blend-filen. Med `bpy.data` kan ni få ut lite allt möjligt som objekt, meshar, material, nod-grupper etc. Såhär kan ni exempelvis uppdatera namnen på alla material med ett prefix
```python
import bpy

materials = bpy.data.materials  # Skapa en referens till alla material

for material in materials:      # För varje material...
	name = material.name        # Spara namnet
	new_name = f"XYZ_{name}"    # Lägg till prefixet "XYZ_"
	material.name = new_name    # Uppdatera namnet av materialet


# Notera att "material" och "materials" är två olika variabler
```
[Data Access (bpy.data)](https://docs.blender.org/api/current/bpy.data.html#module-bpy.data)
# bpy.context
`bpy.context` innehåller variabler som baseras på den aktiva ytan av Blender. Dessa inkluderar b.a:
* `bpy.context.mode` (Det aktiva vyport-läget) -> [Context Mode Items](https://docs.blender.org/api/current/bpy_types_enum_items/context_mode_items.html#rna-enum-context-mode-items)
* `bpy.context.active_object` (Det aktiva objektet)
* `bpy.context.selected_objects` (De markerade objekten)
* `bpy.context.material` (Det aktiva materialet)
* `bpy.context.collection` (Den aktiva kollektionen)

Alla kontextvariabler är read-only och går därmed inte att ändra värdena av.

[Context Access (bpy.context)](https://docs.blender.org/api/current/bpy.context.html#module-bpy.context)