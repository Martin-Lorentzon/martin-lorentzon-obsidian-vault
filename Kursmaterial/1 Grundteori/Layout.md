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
Med `bl_space_type`, `bl_region_type`, `bl_category` och `bl_label` beskriver ni vart någonstans panelen ska synas

* `bl_space_type` (Editor-typen panelen hör hemma i) -> [Space Type Items](https://docs.blender.org/api/current/bpy_types_enum_items/space_type_items.html#rna-enum-space-type-items)
* `bl_region_type` (Ytan, inuti editorn, panelen ska placeras på) -> [Region Type Items](https://docs.blender.org/api/current/bpy_types_enum_items/region_type_items.html#rna-enum-region-type-items)
* `bl_category` (Kategorin panelen går under, om applicerbart) -> Valfri text
* `bl_label` (Namnet på panelen) -> Valfri text

# def draw(self, context):
En klass som behöver ett användargränssnitt kommer alltid att använda en draw-metod. Inuti draw-metoden beskrivs alla era UI-element så som inputfält, knappar, listor, ikoner osv.

### Variablerna `self` och `context`
* `self` -> Referens till klassen draw-metoden definieras i
* `context` -> Kontextvariablerna för ytan ert UI placeras på
# Exempelkod
```python
# Label, Operator och Property

def draw(self, context):
	layout = self.layout
	
	scene = context.scene
	
	layout.label(text="A text label", icon="MONKEY")
	layout.prop(scene, "use_gravity")
	layout.operator("mesh.primitive_monkey_add")
```
```python
# Kolumner - Vol. 1

def draw(self, context):
	layout = self.layout
	
	col = layout.column(align=True)
	col.label(text="Column 1")
	col.operator("mesh.primitive_cone_add", text="")
	
	col.separator()
	col.label(text="Column 2")
	col.operator("mesh.primitive_torus_add", text="")
```
```python
# Kolumner - Vol. 2

def draw(self, context):
	layout = self.layout
	
	row = layout.row()  # Både kolumner placeras horisontellt på samma rad
						# Dvs. bredvid varandra
	
	col = row.column(align=True)
	col.label(text="Column 1")
	col.operator("mesh.primitive_cone_add", text="")
	
	col = row.column(align=True)
	col.label(text="Column 2")
	col.operator("mesh.primitive_torus_add", text="")
```
```python
# Image Preview (med template_icon, i brist på en bättre metod)

def draw(self, context):
	layout = self.layout
	
	icon_id = bpy.data.images["image_name"].preview.icon_id
	layout.template_icon(icon_value=icon_id, scale=10)
```