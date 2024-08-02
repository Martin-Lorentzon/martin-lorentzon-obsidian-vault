```python
import bpy

"""Kopiera modifiers från ert aktiva objekt till de objekt inuti kollektionen"""

collection_name = "My Collection"  # Justera efter namnet på er kollektion

collection = bpy.data.collections.get(collection_name)

active_object = bpy.context.object

for obj in collection.objects:
    if obj.name == active_object.name:
        continue  # Inget behöver ske om loopen itererar över det aktiva objektet
    
    for modifier in active_object.modifiers:
        # Om modifiern finns sedan tidigare återanvänder vi den
        modifier_copy = obj.modifiers.get(modifier.name, None)
        
        # Annars skapar vi en ny
        if not modifier_copy:
            modifier_copy = obj.modifiers.new(modifier.name, modifier.type)
		
        properties = [p.identifier for p in modifier.bl_rna.properties
                      if not p.is_readonly]
		
        for prop in properties:
            setattr(modifier_copy, prop, getattr(modifier, prop))
```
## Beskrivning