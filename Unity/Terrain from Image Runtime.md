## Goal
To generate a patch of terrain with heights based on the values of an image (a height map) during runtime
## Unity's mesh API vs Terrain component
The requirements for this problem consist of defining a grid size and grid resolution, displacing each point/vertex based on some value, filling the grid with quads, giving the resulting mesh a collider, a material and other details such as grass and trees.

There are two obvious routes one can go down when implementing terrain generation in Unity
* Unity's mesh API
* Terrain component

Unity's mesh API is (in my opinion) a better fit for projects in need of fine control over vertex placement and other implementation details, whereas the Terrain component offers a richer feature set and respectable optimization out of the box.

|                       | Collisions | Vegetation                    | Multiple materials              | Optimization                                           |
| --------------------- | ---------- | ----------------------------- | ------------------------------- | ------------------------------------------------------ |
| **Mesh API**          | Yes        | Do it yourself                | Yes                             | Do it yourself                                         |
| **Terrain Component** | Yes        | Yes, various existing methods | Kinda, using <br>Terrain Layers | Built-in dynamic terrain LODs<br>and detail instancing |
## Final verdict
I ultimately think the Terrain component is the better option here; it requires very little code to get started with as it already contains a lot of the logic for generating an optimized mesh.
## Pitfalls
Using the Terrain component can lead to some frustrating moments out of missing documentation, these are some limitations and important details to be aware of
* Image needs to be square
* Image needs to be a power of two plus one (129x129, 257x257, 513x513 etc.)
  (`heightmapResolution` rounds to the nearest one of these)
* The heights array is indexed as [y,x]
* Heights are defined as 0-1 values where a value of 1 equals the max height defined by the Y-component of `terrainData.size`

>[!note]
>Unity may scale the Texture to the nearest power-of-two dimension size at import time.
>To combat this, set Non Power of 2 to "None" in Import Settings for the Texture 2D asset
## Final code
The final code generates a patch of terrain based on an image where 1px is equal to 1 world unit.

**TerrainGeneration.cs**
```cs
using UnityEngine;

[RequireComponent(typeof(Terrain))]
[RequireComponent(typeof(TerrainCollider))]
public class TerrainGeneration : MonoBehaviour
{
    Terrain terrain;
    TerrainData terrainData;
    TerrainCollider terrainCollider;

    public Texture2D image;
    public Material terrainMaterial;

    void Awake()
    {
        terrain = GetComponent<Terrain>();
        terrain.materialTemplate = terrainMaterial;

        terrainData = new TerrainData();
        int size = image.width;
        float height = 128f;
        terrainData.heightmapResolution = size;
        terrainData.size = new Vector3(size, height, size);

        float[,] heights = new float[size, size];

        for (int x = 0; x < size; x++)
        {
            for (int y = 0; y < size; y++)
            {
                heights[y, x] = image.GetPixel(x, y).r;
            }
        }

        terrainData.SetHeights(0, 0, heights);
        terrain.terrainData = terrainData;

        terrainCollider = GetComponent<TerrainCollider>();
        terrainCollider.terrainData = terrain.terrainData;

        // terrainMaterial.SetTexture("_ImageMap", image);
    }
}
```
TODO:
Provide an example on procedural placement of trees with Terrain component