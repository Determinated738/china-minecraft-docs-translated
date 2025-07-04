--- 
front: 
hard: Advanced 
time: 15 minutes 
--- 

# Customize special blocks 

#### Author: Boundary 

Some blocks in the original version have special functions. The Flower Group provides developers with a form of block inheritance to inherit the capabilities of these special blocks. This chapter will teach developers how to customize redstone component blocks and monster spawner blocks. Since McStudio currently does not support the function of fully customizing these two special blocks, JSON syntax will be used here for demonstration. 

#### Custom redstone component blocks

```
{
	"format_version": "1.16.0",
	"minecraft:block": {
		"description": {
			"identifier": "design:redstone_consumer",
			"register_to_creative_menu": true
		},
		"components": {
			"minecraft:destroy_time": 2.0,
            "minecraft:map_color": "#ffffff",
			"netease:tier": {
                "digger": "pickaxe",
				"level": 0
            },
			"netease:redstone": {
                "type": "consumer"
			}
		} } 
} 
``` 

1) 1.16.0 is the custom block content format for the current Nether update, so we fill in 1.16.0 in format_version 

2) identifier is the name field of the custom block, which can be defined by the developer. register_to_creative_menu manages whether the block is registered in the creative backpack. 

3) The parameters under components will store the various functions of the block. Let's mainly look at the netease:redstone component, which can pass in two types. Here we pass in consumer, so that the block can receive redstone signals and become a redstone component block.


``` 
{ 
"format_version": [ 
1, 
1, 
0 
], 
"design:redstone_producer": { 
"textures": "gold_block", 
"sound": "metal" 
}, 
"design:redstone_consumer": { 
"textures": "gold_block", 
"sound": "metal" 
} 
} 
``` 

4) Finally, the following configuration should be made under blocks.json. In the example figure, the block texture is set to the gold block texture, then all 6 faces are gold block faces, and the sound effect type produced when walking on the block and destroying the block is a metal sound effect. 

#### Custom redstone signal source block

```
{
	"format_version": "1.16.0",
	"minecraft:block": {
		"description": {
			"identifier": "design:redstone_producer",
			"register_to_creative_menu": true
		},
		"components": {
			"minecraft:destroy_time": 2.0,
            "minecraft:map_color": "#ffffff",
			"netease:tier": {
                "digger": "pickaxe",
				"level": 0
            },
			"netease:redstone": {
				"type": "producer",
				"strength": 10
			}
		}
	}
}
```



1) 1.16.0 is the custom block content format for the current Nether update, so we fill in 1.16.0 in format_version 

2) identifier is the name field of the custom block, which can be defined by the developer. register_to_creative_menu manages whether the block is registered in the creative backpack. 

3) The parameters under components will store the various functions of the block. Let's mainly look at the netease:redstone component, which can pass in two types. Here we pass in producer, so that the block can receive and send redstone signals, and strength controls the strength of the redstone signal, that is, the strength will decrease by 1 point for each grid of the signal. 

4) Finally, the following configuration should be made under blocks.json. In the example figure, the block texture is set to the gold block texture, then all 6 faces are gold block faces, and the sound effect type produced when walking on the block and destroying the block is a metal sound effect. 

#### Custom monster spawner blocks

```
{
    "format_version": "1.16.0",
    "minecraft:block": {
        "description": {
            "identifier": "design:chicken_mob_spawner",
            "register_to_creative_menu": true,
			"base_block": "mob_spawner"
        },
        "components": {
            "minecraft:block_light_absorption": 0,
            "netease:tier": {
                "digger": "pickaxe",
				"level": 0
            },
			"netease:render_layer": {
				"value": "alpha"
			},
			"netease:mob_spawner": {
				"type": "minecraft:chicken"
			},
            "minecraft:block_light_emission": 1.0, "minecraft:destroy_time": 2.0, 
"minecraft:map_color": "#ffffff" 
} 
} 
} 
``` 

1) 1.16.0 is the custom block content format of the current Nether update, so we fill in 1.16.0 in format_version 

2) identifier is the name field of the custom block, which can be defined by the developer. register_to_creative_menu manages whether the block is registered in the creative backpack. Here, the base_block key pair must be additionally specified to make the block inherit the monster spawner, that is, "mob_spawner". 


3) The parameters under components will store the various functions of the block. Let's mainly look at the netease:mob_spawner component. The key type in it will point to a creature name domain. This component function supports both custom creatures and MC original creatures. 

``` 
{ 
"format_version": [ 
1, 
1, 
0 
], 
"design:chicken_mob_spawner": { 
"textures": "mob_spawner", 
"sound": "metal" 
} 
} 
``` 

4) Finally, the following configuration should be made under blocks.json. In the example picture, the block texture is set to the original monster spawner texture. Then all 6 sides are monster spawner textures, and the sound effect type produced when walking on the block and destroying the block is metal sound effect.