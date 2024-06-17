För att Blender ska upptäcka ert add-on måste ni registrera dess Blenderspecifika klasser.
Detta gör ni enklast i slutet på er skriptfil
```python
def register():
	bpy.utils.register_class(CRAZY_TOOL_PT_crazy_panel)
	bpy.utils.register_class(CRAZY_TOOL_OT_do_crazy_things)

def unregister():
	bpy.utils.unregister_class(CRAZY_TOOL_PT_crazy_panel)
	bpy.utils.unregister_class(CRAZY_TOOL_OT_do_crazy_things)

if __name__ == "__main__":
    register()
```
### Registrera klasser med for-loop
För att inte behöva specifiera varje klass ni registrerar två gånger kan ni använda er av for-loopen.
Detta görs alltså istället för koden ovan
```python
classes = [
	CRAZY_TOOL_PT_crazy_panel,
	CRAZY_TOOL_OT_do_crazy_things,
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