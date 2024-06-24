Med klasser som `bpy.types.Panel`, `bpy.types.Menu` och `bpy.types.UIList` kan ni skapa användargränssnitt i samma stil som resterande ytor av Blender.
## Panel
Klassen `bpy.types.Panel` använder ni när ni skapar paneler till ert användargränssnitt

```python
class MY_ADDON_PT_cool_panel(bpy.types.Panel):
	bl_space_type = "VIEW_3D"
	bl_region_type = "UI"
	bl_category = "My Addon"
	bl_label = "Cool Panel"
	bl_context = "objectmode"
	
	def draw(self, context):
		layout = self.layout
```
Med `bl_space_type`, `bl_region_type`, `bl_category`, `bl_label` och `bl_context` beskriver ni vart någonstans panelen ska synas

* `bl_space_type` (Editor-typen panelen hör hemma i) -> [Space Type Items](https://docs.blender.org/api/current/bpy_types_enum_items/space_type_items.html#rna-enum-space-type-items)
* `bl_region_type` (Ytan, inuti editorn, panelen ska placeras på) -> [Region Type Items](https://docs.blender.org/api/current/bpy_types_enum_items/region_type_items.html#rna-enum-region-type-items)
* `bl_category` (Kategorin panelen går under, om applicerbart) -> Valfri text
* `bl_label` (Namnet på panelen) -> Valfri text
* `bl_context` (Kontextläget panelen hör hemma i) -> [Saknar dokumentation](https://docs.blender.org/api/current/bpy.types.Panel.html#bpy.types.Panel.bl_context)

För en komplett lista över alla dess "bl"-attributer se [Panel(bpy_struct)](https://docs.blender.org/api/current/bpy.types.Panel.html#bpy.types.Panel)
Resterande behövs inte inkluderas men vissa kan vara bra att känna till.
## def draw(self, context):

En klass som skapar ett användargränssnitt kommer alltid att kräva en draw-metod. Inuti klassens draw-metod beskrivs alla era UI-element så som inputfält, knappar, listor, ikoner osv.

**Exempelkod**
```python
# Label, Operator och Property

def draw(self, context):
	layout = self.layout
	
	scene = context.scene
	
	layout.label(text="A text label", icon="MONKEY")
	layout.operator("mesh.primitive_monkey_add")
	layout.prop(scene, "use_gravity")
```
```python
# Kolumner - Vol. 1

def draw(self, context):
	layout = self.layout
	
	col = layout.column(align=True)
	col.label(text="Label 1")
	col.operator("mesh.primitive_cone_add")
	
	col.separator()
	col.label(text="Label 2")
	col.operator("mesh.primitive_torus_add")
```
```python
# Kolumner - Vol. 2

def draw(self, context):
	layout = self.layout
	
	row = layout.row()  # Både kolumner placeras horisontellt på samma rad
						# Dvs. bredvid varandra
	
	col = row.column(align=True)
	col.label(text="Column 1")
	col.operator("mesh.primitive_cone_add")
	
	col = row.column(align=True)
	col.label(text="Column 2")
	col.operator("mesh.primitive_torus_add")
```
```python
# Image Preview

def draw(self, context):
	layout = self.layout
	
	icon_id = bpy.data.images["image_name"].preview.icon_id
	layout.template_icon(icon_value=icon_id, scale=10)
```