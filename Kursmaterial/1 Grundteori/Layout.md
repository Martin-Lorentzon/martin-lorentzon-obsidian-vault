Kom ihåg att dessa klasser måste registreras, det är ert sätt att tala om för Blender att era användargränssnitt ska synas för användaren.
# Panel
Klassen `bpy.types.Panel` använder ni när ni skapar paneler till ert användargränssnitt.

```python
class MY_ADDON_PT_some_panel(bpy.types.Panel):
	bl_space_type = "VIEW_3D"
	bl_region_type = "UI"
	bl_category = "My Addon"
	bl_label = "Some Panel"

	def draw(self, context):
		layout = self.layout
```
I panel-klassen med `bl_space_type`, `bl_region_type`, `bl_category` och `bl_label` beskriver ni vart någonstans panelen ska synas

* `bl_space_type` (Editor-typen panelen hör hemma i) -> [Space Type Items](https://docs.blender.org/api/current/bpy_types_enum_items/space_type_items.html#rna-enum-space-type-items)
* `bl_region_type` (Ytan, inuti editorn, panelen ska placeras på) -> [Region Type Items](https://docs.blender.org/api/current/bpy_types_enum_items/region_type_items.html#rna-enum-region-type-items)
* `bl_category` (Kategorin panelen går under, om applicerbart) -> Valfri text
* `bl_label` (Namnet på panelen) -> Valfri text

# def draw(self, context):

