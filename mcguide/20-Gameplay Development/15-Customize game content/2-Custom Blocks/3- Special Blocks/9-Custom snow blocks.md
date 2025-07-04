--- 
front: 
hard: Getting Started 
time: minutes 
--- 
# Custom Snow-Containing Blocks 

## Overview 

Custom Snow-Containing Blocks supports configuring custom blocks with snow-related functions in components, and supports python listening events, interface settings, etc. 

To configure a block to contain snow, you need to set the following two components 

## netease:snow_recover_able 

You can set whether a block can contain snow in the netease:snow_recover_able component. 

| Key | Type | Default | Explanation | 
| ----- | ---- | ------ | -------------------------------- | 
| value | bool | | Required, used to set whether the block can contain snow | 

## netease:can_built_over 

In the netease:can_built_over component, you can set whether other blocks can be placed in this block if there is already a block with netease:can_built_over configuration at that location. 

| Key | Type | Default | Explanation | 
| ----- | ---- | ------ | ------------------------------------------------------------ | 
| value | bool | | Required, used to set whether other blocks can be placed in this block if there is already a block with netease:can_built_over in this position | 

### Example 
```json 
{ 
"format_version": "1.10.0", 
"minecraft:block": { 
"description": { 
"register_to_creative_menu": true, 
"identifier": "customblocks:customblocks_test_ore", 
"is_experimental": false, 
"category": "custom" 
}, 
"components": { 
"minecraft:block_light_absorption": { 
"value": 0 
}, 
"netease:render_layer": { 
        "value": "alpha"
      },
          "netease:snow_recover_able": {
        "value": true
      },

"netease:can_built_over": { 
"value": true 
}, 
"netease:aabb": { 
"collision": { 
"min": [0.0, 0.0, 0.0], 
"max": [0.0, 0.0, 0.0] 
}, 
"clip": { 
"min": [0.0, 0.0, 0.0], 
"max": [1.0, 0.188, 1.0] 
} 
} 
} 
} 
} 
``` 

## Note 
Currently, custom snow-containing blocks and block entities are incompatible (including custom block entities, custom monster spawners, etc.), please do not use them together 
