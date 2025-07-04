--- 
front: 
hard: Getting Started 
time: minutes 
--- 
# Custom Water-Containing Blocks 

## Overview 

Custom Water-Containing Blocks support the configuration of custom block water-containing related functions in the component, and support python listening events, interface settings, etc. 

## netease:water_destory 

You can set whether it cannot be placed in water sources and flowing water blocks in the netease:water_destory component. If set to true, it will be destroyed by flowing water. 

| Key | Type | Default | Explanation | 
| ----- | ---- | ------ | -------------------------------------------- | 
| value | bool | | Required, used to set the block cannot be placed in water source and flowing water blocks | 

- You can set the dropped items after being destroyed by water in the loottable of the block 

### Example 
```json 
{ 
"format_version": "1.10.0", 
"minecraft:block": { 
"description": { 
"register_to_creative_menu": true, 
"identifier": "customblocks:water_destroy_test_block", 
"is_experimental": false, 
"category": "custom" 
}, 
"components": { 
"netease:water_destory": { 
"value": true 
} 
} 
} 
} 
``` 

## netease:water_only 

You can set whether it must be placed in water in the netease:water_only component. 

| Key | Type | Default value | Explanation | 
| ----- | ---- | ------ | ------------------------------------ | 
| value | bool | | Must be set, used to set whether it must be placed in water. | 

### Example

```json 
{ 
"format_version": "1.10.0", 
"minecraft:block": { 
"description": { 
"register_to_creative_menu": true, 
"identifier": "customblocks:water_only_test_block", 
"is_experimental": false, 
"category": "custom" 
}, 
"components": { 
"netease:water_only": { 
"value": true 
} 
} 
} 
} 
``` 

## netease:water_source 

The netease:water_source component can be used to set whether or not water source blocks are represented as containing water. 

| Key | Type | Default | Explanation | 
| ----- | ---- | ------ | -------------------------------------- | 
| value | bool | | Required, whether or not water source blocks are represented as containing water. |

### Example
```json
{
    "format_version": "1.10.0",
    "minecraft:block": {
        "description": {
            "register_to_creative_menu": true,
            "identifier": "customblocks:water_source_test_block",
            "is_experimental": false,
            "category": "custom"
        },
        "components": {
            "netease:water_source": {
              "value": true
            },
            "netease:render_layer": {
              "value": "alpha"
          }
        }
    }
}
```

## netease:water_flow_source 

In the netease:water_flow_source component, you can set whether to display water in water source and water flow blocks. 

| Key | Type | Default | Explanation | 
| ----- | ---- | ------ | -------------------------------------- | 
| value | bool | | Required, whether to display water in water source and water flow blocks. |

### Example
```json
{
    "format_version": "1.10.0",
    "minecraft:block": {
        "description": {
            "register_to_creative_menu": true,
            "identifier": "customblocks:water_flow_source_test_block",
            "is_experimental": false,
            "category": "custom"
        },
        "components": {
            "netease:water_flow_source": {
              "value": true
            },
            "netease:render_layer": {
              "value": "alpha"
          }
        }
    }
}
```