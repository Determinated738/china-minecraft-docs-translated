--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Miniature Blocks 

Miniature blocks are used to shrink the block shapes of certain areas in the game into several single small blocks for display. Currently, only pre-miniature blocks are available in the game. 

1. Pre-miniature blocks, generate the corresponding miniature block information by using the modsdk interface and save it as a miniature block file by the developer, then put the file into the mod. After re-entering the game, the miniature blocks are similar to the native blocks of the game and can be found and used in the item list 

## Demo explanation 

MicroBlocksMod defines three different miniature blocks: 

1. number_9, a 2x2x2 miniature block with an icon 

2. number_9_2, a 1x1x1 miniature block 

3. number_9_3, the same as number_9_2, but the block color is changed. 

## Pre-miniature block registration 

Note: The following files can be found in MicroBlocksMod 

First, you need to create miniature block information in the `MicroBlocksMod_behavior/netease_micro_blocks/` folder, and then you need to create miniature block image information in the `MicroBlocksMod_resource/models/netease_micro_block/` folder. Here we take the creation of number_9_2.json as an example: 

1. Create a number_9_2.json file in the MicroBlocksMod_behavior/netease_micro_blocks/ folder 

2. Write the following information to number_9_2.json, where: 

- `identifier` is used to represent the unique identifier of the miniature block. For miniature blocks, it must start with `micro_block:`, otherwise it cannot be recognized as a miniature block in the game. The recommended identifier is micro_block: namespace_block name. The namespace is recommended to be consistent with the mod name. The block name after the colon must be globally unique. To avoid duplication with the original block and other mods, please add namespace_ as a prefix to ensure uniqueness. 
- `register_to_creative_menu` is used to control whether the miniature model is displayed in the item list. By setting it to `true`, it can be found in the item list like the original block. 
- `micro_size` is used to indicate the size of the grid occupied by the current miniature block. For example, `"1 1 2"` means that the miniature block occupies a grid of 1x1x2 (Note: the original grass block occupies a grid of 1x1x1). It must be an integer when configured and separated by spaces. Note that the current maximum supported size of the miniature block is 4x4x4. Even if the configuration exceeds 4, it cannot occupy more grids. 
- Note: Miniature blocks do not support the json components of the original and NetEase versions. 

```
{
    "format_version": "1.13.0",
    "minecraft:block": {
        "description": {
            "identifier": "micro_block:number_9_2",
            "register_to_creative_menu": true,
            "micro_size": "1 1 1"
        },
        "components": {
        }
    }
}
```


3. Create a new number_9_2.json file in the folder `MicroBlocksMod_resource/models/netease_micro_block/`. The content of the file can be obtained through `CreateMicroBlockResStr` under `blockCompServer`. The prototype of the function is as follows: 

`CreateMicroBlockResStr(self, identifier, start, end, colorMap=None, isMerge=False, icon="")` 

- identifier, str, the unique identifier of the miniature block. Since `micro_block:` will be automatically added, only `x` needs to be filled in here 
- start, (int, int, int), the starting coordinates of the miniature, such as (30, 65, 78) 
- end, (int, int, int), the ending coordinates of the miniature, such as (44, 77, 90) 
- colorMap, Dict, used to specify the color of a certain type of block after miniaturization, such as colorMap={"minecraft:grass": [12, 12, 12, 255], "minecraft:stone": [12, 233, 24]}, will change the color of all blocks that match the type 
- isMerge, Bool, used to indicate whether to merge blocks of the same type (this can reduce performance consumption) 
- icon, str, used to specify the icon of the miniature block. Note that the icon cannot directly use the relative path where the icon is located, but needs to be added to terrain_texture.json first, and then reference the registered name of the icon. For specific usage methods, please refer to [Custom Block Registration](https://mc.163.com/mcstudio/mc-dev/MCDocs/2-ModSDK%E6%A8%A1%E7%BB%84%E5%BC%80%E5%8F%91/03-%E8%87%AA%E5%AE%9A%E4%B9%89%E6%B8%B8%E6%88%8F %E5%86%85%E5%AE%B9/05-%E8%87%AA%E5%AE%9A%E4%B9%89%E6%96%B9%E5%9D%97/0 -%E8%87%AA%E5%AE%9A%E4%B9%89%E6%96%B9%E5%9D%97%E6%A6%82%E8%BF%B0.html)

use `CreateMicroBlockResStr` returns a string, which needs to be saved by the developer 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlock(levelId) 
result = comp.CreateMicroBlockResStr("x", (12, 60, 12), (26, 76, 26), colorMap={'minecraft:grass': [12, 22, 123, 255]}, isMerge=True, icon="micro_block_datiangou") 
with open("micro_block_x.json", "w+") as f: 
f.write(result) 
#In this example, the block will start at (12 60 12) and end at (26 76 26) Miniaturize the end point. The color of all grass blocks in the final miniaturized block is rgba(12,22,123,255). The actual display color will be fine-tuned according to the ambient light. The icon in the inventory is the image corresponding to micro_block_datiangou in terrain_texture.json. 
``` 

- When the area selected by start and end is used, only the block data (including custom blocks) will be generated. The entity data such as creatures will not be included. When the selected area is not loaded, no data will be generated. When the selected area contains loaded and unloaded areas, only the data of the loaded area will be generated. 
- Reverse start and end, and the rendering direction will be opposite. 

## Microblock resource data description 

Let's check out the number_9_2 microblock resource data that comes with MicroBlocksMod 

``` 
{ 
"netease:micro_block": { 
"data": { 
"11": [[], [], [0, 0, 0, 1], [0, 0, 0, 1], [], [], [], [], [], [0, 0, 0, 1], [0, 0, 0, 1]], 
"10": [[], [], [0, 0, 0, 1], [], [], [], [], [], [], [0, 0, 0, 1]], 
"13": [[], [], [], [], [0, 0, 0, 1], [0, 0, 0, 1], [], [0, 0, 0, 1], [0, 0, 0, 1]], 
"12": [[], [], [], [0, 0, 0, 1], [0, 0, 0, 1], [], [], [], [0, 0, 0, 1], [0, 0, 0, 1]], 
"14": [[], [], [], [], [], [0, 0, 0, 1], [0, 0, 0, 2]], 
"1": [[], [], [], [], [], [0, 0, 0, 1], [0, 0, 0, 1], [0, 0, 0, 1]], 
"3": [[], [], [], [0, 0, 0, 1], [0, 0, 0, 1], [], [], [], [0, 0, 0, 1], [0, 0, 0, 1]], 
"2": [[], [], [], [], [0, 0, 0, 1], [0, 0, 0, 1], [], [0, 0, 0, 1], [0, 0, 0, 1]], 
"5": [[], [], [0, 0, 0, 1], [0, 0, 0, 1], [], [], [], [], [0, 0, 0, 1]], 
"4": [[], [], [0, 0, 0, 1], [0, 0, 0, 1], [], [], [], [], [], [0, 0, 0, 1], [0, 0, 0, 1]], 
"7": [[], [], [0, 0, 0, 1], [0, 0, 0, 1], [0, 0, 0, 1], [0, 0, 0, 1], [], [0, 0, 0, 1], [0, 0, 0, 1]], 
"6": [[], [], [0, 0, 0, 1], [0, 0, 0, 1], [], [0, 0, 0, 1], [0, 0, 0, 1]], 
"9": [[], [], [0, 0, 0, 1], [0, 0, 0, 1], [], [], [], [], [], [0, 0, 0, 1], [0, 0, 0, 1]],
            "8": [[], [], [0, 0, 0, 1], [0, 0, 0, 1], [0, 0, 0, 1], [], [], [], [0, 0, 0, 1], [0, 0, 0, 1]]
        },
        "description": {

"identifier": "micro_block:number_9_2", 
"blocks": { 
"1": { 
"aux": 0, 
"name": "minecraft:grass", 
"color": [254, 46, 45, 255] 
}, 
"2": { 
"aux": 1, 
"name": "minecraft:grass", 
"color": [254, 46, 45, 255] 
} 
} 
"icon": "", 
"size": [11, 15, 6] 
} 
}, 
"format_version": "1.13.0" 
} 
``` 

For a basic microblock resource data, there are 6 main data to focus on: 

1. identifier, need to have the same matching block identifier under behavior 
2. icon, the icon corresponding to the miniature block 
3. block_size, used to identify the size of the miniature block rendering graphics. For a 1x1x1 grid, its rendering size is [16, 16, 16], that is, the game will use 16x16x16 block data to render a miniature model with a volume of the game's native grid size. From the perspective of game performance, the current maximum support is [64, 64, 64], that is, the maximum range generated by a miniature block set is a grid of `4*4*4` (note that the size here needs to match the block micro_size under behavior) 
4. blocks, all block information contained in the miniature block, and the information of the serial block corresponding to each string serial number 
5. data, the specific composition data of the miniature block. 
- For data with block_size less than or equal to [16, 16, 16] (i.e. the entire model only occupies the position of one vanilla block), its data consists of a single dictionary, and the identifier under each dictionary, for example, `"3"` in the data is used to identify the composition data of the third layer, and then for the data corresponding to `"3"`, each row of rendering data from north to south is rendered in turn, and for a specific row of data, it will be rendered from east to west in turn. In the rendering data, 0 represents an air block, indicating that there is no block here, 1 represents this is the first block in "blocks", and so on. 
- For data with block_size greater than [16, 16, 16], that is, containing more miniature blocks, such as [32, 32, 32] data (the model needs to occupy `(32 / 16) x (32 / 16) x (32 / 16) = 8` grids), the data under data consists of a list, corresponding to the list data in the order of `x + z*x + y*z*x`. 
6. light_factor, default value [1.0, 1.0, 1.0, 1.0, 1.0, 1.0], each value ranges from 0 to 1.0, used to adjust the light intensity of each face of the miniature block 

Note: For the PE side, if the miniature block data is too large, it will cause the initial loading time of the game to be extended. If it contains too many miniature blocks and each data is particularly large, it will cause the initial loading time of the game to be greatly extended. 

