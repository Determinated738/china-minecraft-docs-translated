--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Custom Redstone Block 

Custom Redstone Block is a special custom block, including signal source block and redstone mechanical component block, supporting all block-related events and interfaces. 

## Custom Redstone Signal Source Block 

When a custom redstone signal source block is placed on the map, it will emit a redstone signal, and the initial value of the signal can be configured. 

Where type is producer, and strength is the initial redstone signal quantity. 

```json 
{ 
"format_version": "1.10.0", 
"minecraft:block": { 
"description": { 
"identifier": "customblocks:customblocks_redstone", 
"register_to_creative_menu": true, 
"is_experimental": false, 
}, 
"components": { 
"minecraft:map_color": { 
"color": "#408080" 
}, 
"netease:redstone": { 
"type": "producer", 
"strength": 10 
} 
} 
} 
} 
``` 

## Custom Redstone Mechanism Component Block 

Custom Redstone Mechanism Component Blocks placed on the map will receive redstone signals and can be activated. 

For custom redstone mechanical component blocks, the event <a href="../../../../../mcdocs/1-ModAPI/事件/方块.html#blockstrengthchangedserverevent" rel="noopenner"> BlockStrengthChangedServerEvent </a> is triggered when its redstone signal changes. 

Among them, type is consumer, the initial redstone semaphore is 0 (unactivated state), and it cannot be configured through the strength field of netease:redstone. 


```json
{
	"format_version": "1.10.0",
	"minecraft:block": {
		"description": {
			"identifier": "customblocks:customblocks_redstone_consumer",
			"register_to_creative_menu": true,
			"is_experimental": false,
		},
		"components": {
			"netease:redstone": {
                "type": "consumer"
			}
		}
	}
}
```