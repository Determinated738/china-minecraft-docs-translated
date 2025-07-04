--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Custom Dimensions 

## Declare a New Dimension 

<span id="jump_to_custom_dimension"></span> 

The engine comes with three native dimensions by default: overworld, nether, and the end, as well as custom dimensions numbered 3 to 20, which can be used directly. 

In addition, you can also add new custom dimensions numbered 22 to 2147483647 through configuration: 

1. Add a new `netease_dimension` folder in the `behavior` directory in the addon directory 

2. Add a json file named after the dimension id: 

For example, dm23333.json: 

```json 
{ 
"format_version": "1.14.0", 
"netease:dimension_info": { 
"components": { //This field must be present 
} 
} 
} 
``` 

You can use the following python code to generate a random dimension id: 

```python 
import random, sys 
print random.randint(22, sys.maxint) 
``` 

For the three native dimensions and 18 built-in custom dimensions, you can also configure the json of the corresponding file name (Note: the file names corresponding to the three native dimensions are: overworld.json, nether.json, the end.json, please do not use dimension id naming), write the components field to modify their properties, but some properties cannot be modified for native dimensions, see the following instructions for details. 

## Dimension configuration 

Components that can be configured in components are as follows: 

| Component | Type | Default value | Description | 
| ----------------------------------------------------- | ------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | 
| netease:dimension_type | string | minecraft:overworld | Dimension type, you can choose the following values: <br>minecraft:overworld<br>minecraft:nether<br>minecraft:the_end<br> (Invalid for three native dimensions) | 
| netease:generator_noise | Empty object | | Noise generator, used to generate randomly bumpy ground<br>If no generator is configured, this generator is used by default<br> (Invalid for three native dimensions) | 
| netease:generator_flat | Empty object | | Super flat generator, only available for the main world and the netherworld types<br> (Invalid for three native dimensions) |

| netease:generator_legacy | empty object | | Old world/classic (limited map) generator, only available for the main world type<br> (not valid for the three native dimensions) | 
| netease:ban_vanilla_feature | empty object | | Clear the vanilla feature, which can solve the problem of floating structures in the sky similar to sky island gameplay | 
| netease:spawn_biomes | array(string) | forest, forest_hills, plains, taiga, taiga_hills, jungle, jungle_hills in this dimension | A list of biome names in this dimension where players can spawn. <br> Make sure the listed biomes will be generated in this dimension. | 
| [netease:biome_source](./2-biome-landform.md#7-4.biome-source-node-type) | array(dict) | | The biome source under this dimension, only the main world type is available<br> (invalid for the three native dimensions) | 
| netease:ban_vanilla_mineshaft | empty object | | Shield abandoned mineshaft | 
| netease:ban_vanilla_monument | empty object | | Shield underwater monument | 
| netease:ban_vanilla_mansion | empty object | | Shield woodland mansion | 
| netease:ban_vanilla_temple | empty object | | Shield temple | 
| netease:ban_vanilla_pillageroutpost | empty object | | Shield pillager outpost | 
| netease:ban_vanilla_ruinedportal | empty object | | Shield destroyed portal | 
| netease:ban_vanilla_ruins | empty object | | shield underwater ruins | 
| netease:ban_vanilla_shipwreck | empty object | | shield shipwreck | 
| netease:ban_vanilla_stronghold | empty object | | shield fortress | 
| netease:ban_vanilla_village | empty object | | shield village | 

For example, dm23333.json in CustomBiomesMod: 

```json 
{ 
"format_version": "1.14.0", 
"netease:dimension_info": { 
"components": { 
"netease:dimension_type": "minecraft:overworld", //Type is overworld 
"netease:generator_noise": {}, //Use noise generator 
"netease:spawn_biomes": ["dm23333_ice_plains"] //The player will be born under the ice field 
} 
} 
} 
``` 
Note: 

- It is recommended to configure the custom end in the biome not to generate the ender dragon and related logic (reference: [biome terrain](./2-biome terrain.md#jump_to_no_spawn_dragon)). Even if the ender dragon logic is turned on, the portal will not be generated. If necessary, it can be used with a custom portal. 
- If you have entered a certain dimension and the terrain of the dimension has been saved, then reconfiguring the dimension type may cause the saved terrain and the generated terrain to merge. Before entering the dimension, you can use the UpgradeMapDimensionVersion interface to upgrade the dimension version number and discard the original saved information. 
