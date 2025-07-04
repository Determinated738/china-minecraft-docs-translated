--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Mob Spawning 

## Overview 

Developers can use the `spawn_rules` feature of the original addon to control mob spawning in custom dimensions. 

## How to use spawn_rules 

1. Add a spawn_rules folder to the bevavior directory of the addon 

2. Create a json file and name it, such as example.json, example: 

```python 
{ 
"format_version": "1.8.0", 
"minecraft:spawn_rules": { 
"description": { 
"identifier": "minecraft:netease_example", 
"population_control": "ambient" 
}, 
"conditions": [ 
{ 
"minecraft:spawns_underground": {}, 
"minecraft:brightness_filter": { 
"min": 0, 
"max": 4, 
"adjust_for_weather": true 
}, 
"minecraft:height_filter": { 
"min": 0, 
"max": 63 
}, 
"minecraft:weight": { 
"default": 10
        },
        "minecraft:herd": {
          "min_size": 2,
          "max_size": 2
        },
        "minecraft:density_limit": {
          "surface": 5
        },
        "minecraft:biome_filter": {
          "test": "has_biome_tag", "operator":"==", "value": "animal"

} 
} 
] 
} 
} 
``` 

description parameter explanation 

| Parameter | Type | Explanation | 
| --- | --- | --- | 
| identifier | str | The identifier of the spawn rule, in the format of namespace:name | 
| population_control | str | The type of creature to spawn. Each type has a limit on the number of spawns. The optional values are: <br>animal<br>monster<br>water_animal<br>villager<br>ambient<br>cat<br>pillager | 

conditions parameter explanation 

| Name | Description | 
| :-------------------------: | :---------------------: | 
| minecraft:spawns_on_surface | Allow mobs to spawn on the ground | 
| minecraft:spawns_underwater | Allow mobs to spawn in water | 
| minecraft:brightness_filter | The lighting conditions under which mobs are allowed to spawn | 
| minecraft:weight | The weight of mob spawning, default is 0 | 
| minecraft:difficulty_filter | Difficulty mode of mob spawning | 
| minecraft:herd | Size of herd | 
| minecraft:biome_filter | Biomes allowed to be spawned by mobs | 

## Spawn_rules of custom biomes 

Use minecraft:biome_filter in condition to filter tags of custom biomes, such as tags such as dm3 that come with the biome development template, or other custom tags. 

## Demo explanation 

In the example [CustomBiomesMod] (../../13-Module SDK Programming/60-Demo Example.md#CustomBiomesMod), some adjustments were made to the creature spawning of the two custom dimensions dm4 and dm5. 

- dm4 

Make polar bears spawn only in this dimension, and not in ice biomes in other dimensions. 

1. Set polar_bear's spawn_rules to only spawn in biomes with the dm4 tag: 

(see customBiomesBehaviorPack/spawn_rules/polar_bear.json) 

```json 
"minecraft:biome_filter": [ 
..., 
{"test": "has_biome_tag", "operator":"==", "value": "dm4"} 
] 
``` 

- dm5


Rabbits will not spawn on the ice plains, but polar bears 3 times their size will spawn. 

1. Rewrite rabbit's spawn_rules so that it does not spawn in biomes with dm5 tags: 

(see customBiomesBehaviorPack/spawn_rules/rabbit.json) 

```json 
"minecraft:biome_filter": { 
"any_of": [ 
{ 
"all_of": [ 
{ "test": "has_biome_tag", "operator":"==", "value": "taiga"}, 
{ "test": "has_biome_tag", "operator":"!=", "value": "mega"} 
] 
}, 
{ 
"all_of": [ 
{"test": "is_snow_covered", "operator":"==", "value": true}, 
{"test": "has_biome_tag", "operator":"!=", "value": "dm5"} //Add this sentence 
] 
}, 
{"test": "has_biome_tag", "operator":"==", "value":"desert"} 
] 
} 
``` 

2. Create a custom creature called neteasebiomes:dm5_polar_bear, which is the same as the original polar bear except that it is set to 3 times the size 

(see customBiomesBehaviorPack/entities/polar_bear.json, and customBiomesResourcePack/entity/dm5_polar_bear.entity.json) 

```json 
"minecraft:scale": { 
"value": 3.0 
}, 
``` 

Then configure spawn_rules for it so that it only spawns in dm5 

(see customBiomesBehaviorPack/spawn_rules/dm5_polar_bear.json) 

```python 
"minecraft:biome_filter": [ 
			... ,
			{"test": "has_biome_tag", "operator":"==", "value": "dm5"}
		]
		```