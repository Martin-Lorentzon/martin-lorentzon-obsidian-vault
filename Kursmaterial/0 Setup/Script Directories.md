---
cssclasses:
  - hide-title
---
# 📁 Script Directories
Blender läser in add-ons från s.k. script directories. Blenders egna script directory hittar ni under
`C:/Users/.../AppData/Roaming/Blender Foundation/Blender/4.2/scripts`
Det räcker med att skriva `%appdata%` för att komma till `./Roaming`

Ett script directory kan innehålla flera undermappar med olika syften
`./addons` -> Standard för add-ons ni vill kunna aktivera i *Edit > Preferences > Add-ons*
`./startup` -> Add-ons som aktiveras vid start av Blender
För mer info om dessa se [Blender’s Directory Layout](https://docs.blender.org/manual/en/latest/advanced/blender_directory_layout.html#path-layout)

Ni skulle teoretiskt sätt kunna utveckla era add-ons och spara de direkt i Blenders egna script directory. Men normalt sätt vill ni utveckla och spara era add-ons i ett separat script directory, kanske på avdelningens nätverksdisk eller ert GitHub-repo.
## Skapa ett nytt script directory
När ni skapar ett nytt script directory måsta ni konstruera det på samma sätt som Blenders egna.
Så här skulle det kunna se ut
```
C Drive (lokal disk)
└── GitHub
    └── xyz-in-house-tools (klonat GitHub-repo)
        ├── Blender (script directory)
        │   └── addons
        │       ├── crazy_addon.py
        │       ├── other_addon.py
        │       └── multi_file_addon
        ├── Maya
        └── Omniverse
```
Eller med nätverksdisk
```
S Drive (nätverksdisk)
└── Tools
    ├── Blender (script directory)
    │   └── addons
    │       ├── crazy_addon.py
    │       ├── other_addon.py
    │       └── multi_file_addon
    ├── Maya
    └── Omniverse
```
## Lägg till ett script directory i Blender
Innan ert script directory kan användas måste Blender få reda på att ert script directory existerar och vart ni har placerat det. Ni konfigurerar era script directories i Blender genom
_Edit > Preferences > File Paths > Script Directories_

![[File Paths.png]]

