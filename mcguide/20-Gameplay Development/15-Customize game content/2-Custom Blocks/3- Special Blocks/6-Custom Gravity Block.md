--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Custom Gravity Block 

## Overview 

Custom Gravity Block can simulate [falling blocks](https://minecraft.fandom.com/zh/wiki/%E4%B8%8B%E8%90%BD%E7%9A%84%E6%96%B9%E5%9D%97), and supports modifying configuration in components and listening to events in Python. 

## base_block settings 

- Custom gravity blocks need to have base_block set to `custom_heavy_block` 

## netease:fall 

| Key | Type | Default | Explanation | 
| ------------ | ----- | -------------------- | ------------------------------------------------------------ | 
| send_python_event | bool | false | Optional, whether to send gravity block/falling block entity related events to python | 
| fall_acceleration | float | 0.04 | Optional, the vertical acceleration increment of the falling block entity each tick | 
| adjust_percentage | float | 0.98 | Optional, the adjustment value of the falling block entity's movement speed multiplied by each tick | 
| hurt_entity | bool | false | Optional, whether to calculate the damage to the collision entity after the falling block entity stops falling | 
| fall_damage_amount | float | 2.0 | Optional, the multiplier of the vanilla fall damage after calculation | 
| max_fall_damage | int | 40 | Optional, the fall damage will be limited to this value after multiplying the multiplier | 
| min_height_remove_tick | int | 100 | Optional, when the falling block entity is below the minimum height of the block, it will be forcibly deleted after a certain number of ticks | 
| force_break_tick | int | 600 | Optional, when the falling block entity is forcibly destroyed after a certain number of ticks | 
| cancel_drop | bool | false | Optional, whether to cancel the drop of the block item when the falling block entity is destroyed | 

- `send_python_event` mainly affects HeavyBlockStartFallingServerEvent, FallingBlockCauseDamageBeforeServerEvent, FallingBlockBreakServerEvent, FallingBlockReturnHeavyBlockServerEvent, FallingBlockCauseDamageBeforeClientEvent. 
- If there is no need to monitor in the mod program, you can set `send_python_event` not to true to optimize performance (you can also configure other values of the component without sending python events). 
- The original version uses Python pseudocode to express the falling process of the falling block entity as follows 
```python 
while Tick: 
falling_block.move_vector.y -= fall_acceleration # The current moving vector adds a downward force 
move(falling_block) # Adjust the entity position according to the current moving vector 
falling_block.move_vector *= adjust_percentage # After moving, multiply the current moving speed (moving vector) by a numerical value 
``` 
- The original falling block entity does not have real-time collision detection for entities, which means that there may be two problems when adjusting the moving speed of the falling block: 
- If the speeds of the two falling blocks are inconsistent, you will see that one block entity passes through the other block entity without a collision effect. 
- The calculation of the damage caused by the falling block to the entity is not when it just touches the entity, but when it lands, it detects whether there is an entity in the range. It is easier to observe this phenomenon by adjusting the moving speed slowly. 
## Sample configuration 
Please refer to customblocks:customblocks_test_heavy.json in [CustomBlocksMod](../../../13-Module SDK Programming/60-Demo Example.md#CustomBlocksMod). 
```json 
{ 
"format_version": "1.10.0",

    "minecraft:block": {
        "description": {
            "identifier": "customblocks:customblocks_test_heavy",
            "register_to_creative_menu": true,
            "is_experimental": false,
            "base_block": "custom_heavy_block",
            "category": "custom"
        },
        "components": {
            "netease:fall": {
                "send_python_event":true,
                "fall_acceleration":0.04,
                "adjust_percentage":0.98,
                "hurt_entity":true,
                "min_height_remove_tick":100,
                "force_break_tick":600,
                "fall_damage_amount":2.0,
                "max_fall_damage":40
            }
        }
    }
}
```