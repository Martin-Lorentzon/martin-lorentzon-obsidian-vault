"Operator" är Blenders ramar för att skapa de actions Blender-användaren ska kunna utföra.
Dessa finns överallt i Blender och körs ofta av knappar, keybinds, gizmos och i skript.
Med operatorn får användaren tillgång till funktionalitet som *Undo*, *Repeat Last* och *Adjust Last Operation*.

>[!quote] dr. Sybren A. Stüvel - Blender Developer
>An operator is the glue between menus, buttons and hotkeys—and the code that should be executed by them.
## Context
Operatorn är designad att följa den aktiva ytans kontextvariabler. Dessa ger oss utvecklare möjlighet att tweaka vår kods beteende efter vad användaren fokuserar på i Blenders användargränssnitt. Detta är nödvändigt när vi skapar funktionalitet som ska respektera användarens intentioner.

![[Context Operator.png]]
## Skelett
```python
class MY_ADDON_OT_fancy_tool(bpy.types.Operator):
	"""The Tooltip"""
	bl_idname = my_addon.fancy_tool
	bl_label = "Fancy Tool"
	
	# prop1: bpy.props.StringProperty(name="Property 1", default="DRINK WATER")
	# prop2: bpy.props.StringProperty(name="Property 2", default="EAT APPLES")
	
	def execute(self, context):
		print("Hello World")
		# print(self.prop1)
		# print(self.prop2)
		return {"FINISHED"}
```
* `bl_idname` — Unikt ID för klassen (Används av menyer för att identifiera operatorn)
* `bl_label` — Display-namnet av operatorn

[Operator (bpy_struct)](https://docs.blender.org/api/current/bpy.types.Operator.html#bpy.types.Operator)
### def execute(self, context):
`execute`-metoden används för att köra operatorns huvudsakliga kod.

När `execute`-metoden anses vara färdig returnerar ni `{"FINISHED"}`, alternativt om `execute`-metoden inte kan slutföra sin uppgift returnerar ni `{"CANCELLED"}`.
## Användning av properties
En operator kan göras mer dynamisk med property-definitioner. Dessa blir till en del av klassen och definieras alltså utanför operatorns `execute`-metod.
* `BoolProperty` ([bpy.props.BoolProperty](https://docs.blender.org/api/current/bpy.props.html#bpy.props.BoolProperty))
* `EnumProperty` ([bpy.props.EnumProperty](https://docs.blender.org/api/current/bpy.props.html#bpy.props.EnumProperty))
* `FloatProperty` ([bpy.props.FloatProperty](https://docs.blender.org/api/current/bpy.props.html#bpy.props.FloatProperty))
* `IntProperty` ([bpy.props.IntProperty](https://docs.blender.org/api/current/bpy.props.html#bpy.props.IntProperty))
* `StringProperty` ([bpy.props.StringProperty](https://docs.blender.org/api/current/bpy.props.html#bpy.props.StringProperty))

[Property Definitions (bpy.props)](https://docs.blender.org/api/current/bpy.props.html#bpy.props.BoolProperty)
### invoke och pop-up menyer
`invoke`-metoden beskriver vad som ska hända när operatorn körs från Blenders användargränssnitt (den ignoreras om operatorn enbart skulle köras i Python).
```python
def invoke(self, context, event):
		print("Operator was used inside the Blender Interface!")
		return
```

```python
class MY_ADDON_OT_fancy_tool(bpy.types.Operator):
	"""The Tooltip"""
	bl_idname = my_addon.fancy_tool
	bl_label = "Fancy Tool"
	
	# prop1: bpy.props.StringProperty(name="Property 1", default="DRINK WATER")
	# prop2: bpy.props.StringProperty(name="Property 2", default="EAT APPLES")
	
	def execute(self, context):
		print("Hello World")
		# print(self.prop1)
		# print(self.prop2)
		return {"FINISHED"}
	
	
```













```python
def invoke(self, context, event):
        wm = context.window_manager
        return wm.invoke_props_dialog(self)
```