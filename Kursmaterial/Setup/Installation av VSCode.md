Denna sektionen kommer guida er igenom att konfigurera Blender och Visual Studio Code för att komma igång med Blender Python inuti en mer kapabel kod-editor.
# Konfigurera Blender
Börja med att konfigurera Blender
1. Edit > Preferences > Interface
	1. Bocka i "Developer Extras"
	2. Bocka i "Python Tooltips"
# Installera Python
Installera den aktuella versionen av Python som Blender använder.
Versions-numret går att hitta i Blenders Python-konsol under "Scripting"-fliken
![[Python Version.png|360]]

>[!warning] Se till att bocka i "Add Python to PATH" under er installation

[Download Python | Python.org](https://www.python.org/downloads/)
# Installera BPY
För att använda BPY-modulen inuti VSCode måste ni installera BPY, detta görs enklast genom er Command Prompt (Kommandotolken)
```
pip install bpy
```
# Installera VSCode
Slutligen installera Visual Studio Code
[Download Visual Studio Code - Mac, Linux, Windows](https://code.visualstudio.com/download)