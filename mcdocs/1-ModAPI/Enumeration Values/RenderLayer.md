# RenderLayer 

class in mod.common.minecraftEnum 

- Description 

Material type when rendering blocks 

- Notes 
- Currently, custom blocks only support the use of some materials, see [Custom Block JSON Component][/mc-dev/mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.md] for details 
Because some materials in the online lobby and apollo are missing definitions, the enumeration value in the online lobby and apollo environment is -2 overall 
For example: Blend = 4 becomes Blend = 2; Opaque = 5 becomes Opaque = 3, and so on 

```python 
class RenderLayer(object): 
Blend = 4 # Translucent 
Opaque = 5 # Opaque 
Alpha = 7 # Fully transparent 
SeasonOpaque = 9 # Original version used to render opaque leaves 
SeasonAlpha = 10 # The original version is used to render partially transparent blocks 

``` 

