För att Blender ska upptäcka ert add-on behöver ni registrera alla dess Blenderspecifika klasser.
En klass `MyHelpers` som enbart innehåller funktioner, till exempel, behöver ni inte registrera.

Registrera klasser gör ni enklast i slutet på er skriptfil
```python
def register():
	bpy.utils.register_class(MY_ADDON_PT_cool_panel)
	bpy.utils.register_class(MY_ADDON_OT_fancy_tool)

def unregister():
	bpy.utils.unregister_class(MY_ADDON_PT_cool_panel)
	bpy.utils.unregister_class(MY_ADDON_OT_fancy_tool)

if __name__ == "__main__":
    register()
```
## Registrera klasser med for-loop
För att inte behöva specifiera varje klass ni registrerar två gånger kan ni använda er av for-loopen.
Detta görs alltså istället för koden ovan
```python
classes = [
	MY_ADDON_PT_cool_panel,
	MY_ADDON_OT_fancy_tool
]

def register():
	for cls in classes:
        bpy.utils.register_class(cls)

def unregister():
	for cls in reversed(classes):
        bpy.utils.register_class(cls)

if __name__ == "__main__":
    register()

```