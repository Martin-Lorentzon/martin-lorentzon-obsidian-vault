Denna sektionen kommer guida er igenom hur ni installerar Python och BPY för att komma igång med Blender Python inuti en mer kapabel kod-editor som Visual Studio Code eller PyCharm.
# Installera Python
Installera den aktuella versionen av Python som Blender använder.
Versions-numret går att hitta i Blenders Python-konsol under "Scripting"-fliken
![[Python Version.png|360]]
>[!warning] Se till att bocka i "Add Python to PATH" när ni installerar Python

[Download Python | Python.org](https://www.python.org/downloads/)
# Installera BPY
BPY-modulen installeras enklast med hjälp av ``pip install`` i er command prompt (kommandotolken)
```
pip install bpy
```
På samma sätt kommer ni behöva installera ``fake-bpy-module`` för korrekt syntax highlighting
```
pip install fake-bpy-module
```
# Installera valfri kod-editor
Installera en kod-editor ni känner er bekväma i, förslagsvis Visual Studio Code eller PyCharm
[Download Visual Studio Code - Mac, Linux, Windows](https://code.visualstudio.com/download)
https://www.jetbrains.com/pycharm/download (Skrolla ner för Community Edition)
>[!warning] Det finns risk för att ni behöver byta Python interpreter om ni har fler än en aktiv installation av Python, sök i så fall "How to change Python Interpreter (din kod-editor här)"
>
# Något mer djupgående video av Michael Bridges:
### https://www.youtube.com/watch?v=77mMpeoh3OI
Använd videon som hjälp när ni felsöker eventuella problem ifall att ni skulle köra fast.