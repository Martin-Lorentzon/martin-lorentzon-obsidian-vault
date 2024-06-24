Vid namngivning av klasser är det viktigt att ni förhåller er till genomtänkta benämningar. Dels för att Blender har vissa krav på dessa benämningar, men också för att bevara en bra struktur i er kod.
>[!info] Inkludera namn
>Att inkludera namnet på ert add-on hjälper i att undvika kolliderande benämningar från andra add-ons

Nedanför är en lista på de exempel Blenders dokumentation använder sig av

**Header ->** `_HT_`
**Menu ->** `_MT_`
**Operator ->** `_OT_`
**Panel ->** `_PT_`
**UIList ->** `_UL_`
## Exempel på korrekt namngivning
* `MY_ADDON_OT_fancy_tool` (`bl_idname = "my_addon.fancy_tool"`)
* `MY_ADDON_PT_cool_panel`
* `UPPER_CASE_HT_lower_case`

**Klasser som inte ärver från `bpy` bör använda PascalCase**
`MyHelpers`
`BakeManager`
`FBXImportHelper`
## bl_idname
Att matcha `bl_idname` med klassens namn är valfritt förutom hos operator där dess `bl_idname` används för att kalla på operatorn -> `bpy.ops.my_addon.fancy_tool()`, då föredras lower case.
>[!info] Default-värde
>`bl_idname` använder klassens namn som default-värde, och behövs många gånger inte definieras