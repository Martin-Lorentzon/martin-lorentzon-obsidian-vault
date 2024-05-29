Blender läser in add-ons från s.k. script directories. Blenders egna script directory hittar ni under
`C:\Users\...\AppData\Roaming\Blender Foundation\Blender\4.2\scripts\`
Det räcker med att skriva `%appdata%` för att komma till `\Roaming\`

Ett script directory kan innehålla flera undermappar med olika syften
`.\addons\...` Standard för add-ons ni vill kunna aktivera i _Edit > Preferences > Add-ons_
`.\startup\...` Add-ons som aktiveras vid start av Blender
För mer info om dessa se [Blender’s Directory Layout - Blender 4.2 Manual](https://docs.blender.org/manual/en/latest/advanced/blender_directory_layout.html#path-layout)

Ni skulle teoretiskt sätt kunna utveckla era add-ons och spara de direkt i Blenders egna script directory för att slippa behöva installera de på nytt genom _Edit > Preferences > Add-ons_ när ni gjort nya ändringar. Men normalt sätt vill ni utveckla och spara era add-ons i ett separat script directory, kanske på avdelningens nätverksdisk eller ett GitHub-repo. Mest för att hålla koll på era egna grejer.
# Skapa ett nytt script directory
När ni skapar ett nytt script directory måsta det efterlikna Blenders egna. Mest troligt behöver ni endast bry er om undermappen `.\addons\...`
Så här skulle det kunna se ut
```
C Drive (lokal disk)
└── GitHub
    └── xyz-in-house-tools (klonat GitHub-repo)
        ├── Blender (script directory)
        │   └── addons
        │       ├── crazy_tool.py
        │       └── other_tool.py
        ├── Maya
        └── Omniverse
```
Eller med nätverksdisk
```
S Drive (nätverksdisk)
└── Tools
    ├── Blender (script directory)
    │   └── addons
    │       ├── crazy_tool.py
    │       └── other_tool.py
    ├── Maya
    └── Omniverse
```
# Lägga till ett script directory i Blender
Innan ert script directory kan användas måste Blender först få reda på att ert script directory existerar och vart någonstans. Ni konfigurerar era script directories i Blender genom
_Edit > Preferences > File Paths > Script Directories_

![[Pasted image 20240529222529.png|600]]


