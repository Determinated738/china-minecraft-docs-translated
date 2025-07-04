--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Custom Armor 

## Overview 

It is a special custom item. It supports all the features of custom items and also has armor-related functions. 

## Registration 

1. Same as steps 1-6 for registering custom basic items 

2. custom_item_type is amor 

3. Add the netease:armor component to the json of `behavior/netease_items_beh`. For details on the parameters, see [json component](#json component) 

```json 
{ 
"format_version": "1.10", 
"minecraft:item": { 
"description": { 
"identifier": "customitems:modarmor1", 
"register_to_create_menu":true, 
"custom_item_type": "armor" 
}, 
"components": { 
"netease:armor":{ 
"defense": 10, 
"enchantment":4, 
"armor_slot":0 
} 
} 
} 
} 
``` 

4. Add model textures to `textures\models` in the resource pack 

Consistent with Microsoft's built-in armor textures, custom armor textures also need to be set. 

5. Create a new json in the `resource/netease_item_res` directory to add textures for armor items. For detailed parameters, see the explanation of setting textures in custom item registration 

```json 
{ 
"format_version": "1.10", 
"minecraft:item": {

"description": { 
"identifier": "customitems:modarmor1", 
"category": "Equipment" 
}, 
"components": { 
"minecraft:icon": "customitems:modarmor1" 
} 
} 
} 
``` 

6. Create an `attachables` directory under the resource directory and create a new json description file. For configurable parameters, see [json component](#json component) 

```json 
{ 
"format_version": "1.8.0", 
"minecraft:attachable": { 
"description": { 
"identifier": "customitems:modarmor1", 
"materials": { 
"default": "armor", 
"enchanted": "armor_enchanted" 
}, 
"textures": { 
"default": "textures/models/diamond_1", 
"enchanted": "textures/misc/enchanted_item_glint" 
}, 
"geometry": { 
"default": "geometry.customitems_modarmor1" 
}, 
"scripts": { 
"parent_setup": "variable.chest_layer_visible = 0.0;" 
}, 
"render_controllers": [ "controller.render.armor" ] 
} 
} 
} 
``` 



7. Add the `entity` directory under the `resource/models` directory and add the corresponding geometry description file 

The configurable parameters are mainly the root node descriptor `geometry.modid_modarmor1`, which corresponds to the geometry file value in the previous step. 

```json
   {
       "geometry.customitems_modarmor1": {
           "texturewidth": 64,
           "textureheight": 32,

           "visible_bounds_width": 2,
           "visible_bounds_height": 2,
           "visible_bounds_offset": [ 0, 1, 0 ],
           "bones": [
               {
                   "cubes": [
                       {
                           "origin": [ -4, 24, -4],
                           "uv": [ 0, 0 ],
                           "size": [ 8, 8, 8 ],
                           "inflate": 1.0
                       },
                       {
                           "origin": [4, 30, -1],
                           "size": [2, 2, 2],
                           "uv": [47, 0]
                       },
                       {
                           "origin": [-6, 30, -1],
                           "size": [2, 2, 2],
                           "uv": [47, 0]
                       },                       {
                           "origin": [6, 31, -1],
                           "size": [2, 2, 2],
                           "uv": [42, 8]
                       },
                       {
                           "origin": [-8, 31, -1],
                           "size": [2, 2, 2],
                           "uv": [42, 8]
                       },
                       {
                           "origin": [8, 32, -1],
                           "size": [2, 4, 2],
                           "uv": [41, 0]
                       },
                       {
                           "origin": [-10, 32, -1],
                           "size": [2, 4, 2],
                           "uv": [41, 0]
                       },
                       {
                           "origin": [-8, 36, -1],
                           "size": [16, 2, 2],
                           "uv": [28, 28]
                       }
                   ],
                   "name": "head",
                   "parent": null,

"pivot": [ 
0.0, 
24.0, 
0.0 
] 
} 

] 

} 
} 
``` 


## JSON component 

### `netease_item_beh` file 

**description** 

| key | type | default | explanation | 
| -------- | ---- | --------- | ----------------------------------------- | 
| category | str | Equipment | Unlike ordinary items, the default category of armor is Equipment | 

**NetEase components** 

* netease:armor (beh pack) 

| key | type | default | explanation | 
| ----------- | ---- | ------ | ------------------------------------------------------------ | 
| defense | int | 0 | The defense value of the armor | 
| enchantment | int | 0 | The enchantability of the armor. For an explanation of this value, see the [official wiki](https://minecraft-zh.gamepedia.com/index.php?title=%E6%95%99%E7%A8%8B/%E9%99%84%E9%AD%94%E6%9C%BA%E5%88%B6&variant=zh#.E9.AD.94.E5.92.92.E6.98.AF.E5.A6.82.E4.BD.95.E9.80.89.E6.8B.A9.E5.87.BA.E6.9D.A5.E7.9A.84) | 
| armor_slot | int | | Armor slot, see <a href="../../../../mcdocs/1-ModAPI/Enumeration Value/ArmorSlotType.html" rel="noopenner"> ArmorSlotType </a> | 

### attachables file 

| Key | Type | Description | 
| -------------------- | ---- | ------------------------------------------------------ | 
| identifier | str | Unique descriptor of the armor, consistent with the item descriptor in the previous registration process | 
| textures/default | str | Texture path setting corresponding to the armor | 
| geometry/default | str | Model description file path setting corresponding to the armor | 
| scripts/parent_setup | str | Setting parameters of the corresponding parts of the armor that affect the player rendering | 

**parent_setup** 

The values of the corresponding settings of Microsoft's built-in armor are as follows: 


> variable.helmet_layer_visible Whether the player is displayed 
> 
> variable.chest_layer_visible Whether the player's upper body is displayed 
> 
> variable.leg_layer_visible Whether the player's legs are displayed 
> 
> variable.boot_layer_visible Whether the player's feet are displayed 

Generally speaking, when setting the corresponding part of the armor, you need to set the corresponding variable value in `scripts/parent_setup` to 0 

**geometry/default** 

It needs to be set to the geometry of the corresponding position of the armor, such as `geometry.humanoid.armor.boots`. 

| Key | Description | 
| ---------------------------------- | ---- | 
| geometry.humanoid.armor.boots | Boots | 
| geometry.humanoid.armor.chestplate | Chestplate | 
| geometry.humanoid.armor.helmet | Helmet | 
| geometry.humanoid.armor.leggings | Feet | 

## Additional functions 

In addition to supporting all functions of custom items, it also supports Python events and interfaces for armor, including OnNewArmorExchangeServerEvent events and armorslot components 

## Demo explanation 

[CustomItemsMod](../../13-Module SDK Programming/60-Demo Example.md#CustomItemsMod) defines a custom equipment: 

* customitems:modarmor1 

Custom equipment of helmet type 

## Custom model setting suggestions 

* The basic reference file for the armor model is: **geometry.humanoid** in the `mobs.json` file in the `data\resource_packs\vanilla\models` directory. 

* For model making tools, it is recommended to use BlockBench. The format of the exported model JSON file is close to the required format. 

* After using BlockBench to make the model and export it as a JSON file, adjust it according to the JSON style of the equipment item Demo we provided; 
It should be noted that please try to use the key order in the JSON example to avoid strange bugs. 

* If there are overlapping faces between the Cube and the existing model or Cube, the overlapping part may not be displayed or flicker; this can be avoided by adjusting the `inflate` of each Cube (can be a negative number). The function of inflate is to make the Cube expand a certain value in all directions without affecting the texture coordinates. 


* **Note**: For drowned, you cannot use the `SetArmorNew` interface to equip custom armor, as this will cause the game to crash. 
