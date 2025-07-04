--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# JSON Components 

## format_version 

The json structure of Bedrock Edition custom blocks has been adjusted many times. When filling in format_version, you need to write components according to the json structure of the corresponding version. 

You can choose between the following two versions: 

- 1.16.0 

For details on the components structure of this version, see [bedrock.dev](https://bedrock.dev/zh/docs/1.16.0.0/1.16.0.66/Blocks). 

- 1.10.0 

For details on the components structure of this version, see [bedrock.dev](https://bedrock.dev/zh/docs/1.12.0.0/1.12.0.28/Blocks). Compared to 1.16.0, the value of component in this version is a JSON Object, for example, `minecraft:destroy_time`, in 1.10.0 it is 

```json 
"minecraft:destroy_time": { 
"value": 4.0 
} 
``` 

and in higher versions it is 

```json 
"minecraft:destroy_time": 4.0 
``` 



## description 

| Key | Type | Default | Explanation | 
| ----------------------- | ---- | ------ | ------------------------------------------------------------ | 
| identifier | str | | Includes namespace and item name. Must be globally unique. <br>It is recommended to use the mod name as the namespace | 
| register_to_create_menu | bool | false | Whether to register to the creation column | 
| category | str | Nature | The category registered to the creation column, the optional values are: <br>Construction<br>Nature<br>Equipment<br>Items | 

## components 

Currently, the components supported in the custom block json in the behavior pack include original components and NetEase's unique components. The ones starting with minecraft are original components, and the ones starting with netease are NetEase's unique components. 

For the original components, you can find more parameters and explanations in the format_version explanation above. 


<span id="minecraft_loot"></span> 

### minecraft:loot 

Can be used to control the loot table 

Please refer to the customblocks:customblocks_test_ore block in [CustomBlocksMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBlocksMod) 

<span id="minecraft_destroy_time"></span> 

### minecraft:destroy_time 

Can be used to control the time required for mining. The meaning of this value is consistent with the "hardness" in the [official wiki](https://minecraft-zh.gamepedia.com/%E6%8C%96%E6%8E%98#.E6.96.B9.E5.9D.97.E7.A1.AC.E5.BA.A6) 

Mainly used for [mining](./2-功能.md#wajue) function 

<span id="minecraft_block_light_emission"></span> 

### minecraft:block_light_emission 

Can be used to set the brightness of the block. For information about brightness and block light sources, please refer to the [official wiki](https://minecraft-zh.gamepedia.com/%E4%BA%AE%E5%BA%A6) 

Mainly used for [brightness](./2-功能.md#liangdu) function 

<span id="minecraft_explosion_resistance"></span> 

### minecraft:explosion_resistance 

Can be used to set explosion resistance. For the explosion resistance of the original block, see [Official Wiki](https://minecraft-zh.gamepedia.com/%E7%88%86%E7%82%B8#.E7.88.86.E7.82.B8.E6.8A.97.E6.80.A7) 

<span id="minecraft_block_light_absorption"></span> 

### minecraft:block_light_absorption 

Can be used to set the light transmittance of the block. For details, please refer to [Official Wiki](https://minecraft-zh.gamepedia.com/%E4%BA%AE%E5%BA%A6#.E9.98.BB.E7.A2.8D.E5.85.89.E7.85.A7.E7.9A.84.E6.96.B9.E5.9D.97) 

Default is opaque.

Mainly used for [brightness](./2-function.md#liangdu) function 

<span id="minecraft_map_color"></span> 

### minecraft:map_color 

Can be used to set the color of the block displayed on the map 

<span id="netease_tier"></span> 

### netease:tier 


Used to set properties related to mining 

Mainly used for [mining](./2-function.md#wajue) functions 

| Key | Type | Default value | Explanation | 
| :-------------: | :----: | :----: | :----------------------------------------------------------- | 
| digger | string | | Required. Indicates that the block has a speed bonus when mined with this tool. <br>Optional values are: <br> shovel: shovel <br> pickaxe: pickaxe <br> hatchet: hatchet | 
| destroy_special | bool | false | Optional. <br>When set to true, it means that only when the tool set by digger is used for mining will drops be generated. | 
| level | int | 0 | Optional. <br>Only effective when destroy_special is true. Indicates the tool level required for mining. If the handheld tool level is less than this value, no drops will be generated. <br>Original tool level:<br> Barehand/other non-tool items: 0<br> Wooden/gold tools: 0<br> Stone tools: 1<br> Iron tools: 2<br> Diamond tools: 3 | 

<span id="netease_aabb"></span> 

### netease:aabb 

Used to set the collision box of the block 

**Notes:** 

1. For blocks without collision boxes, please set each item of collision to 0 
2. For blocks with collision boxes, the range of clip needs to be less than or equal to the range of collision, otherwise the projectile will be abnormal when hitting 
3. The min of aabb should not be less than [-1, -1, -1], and the max should not be greater than [2, 2, 2] 

Please refer to the customblocks_model_flower and customblocks_model_wire blocks in [CustomBlocksMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBlocksMod). 

| Key | Type | Default Value | Explanation | 
| --------- | ------------- | ------ | ------------------------------------------------------------ | 
| collision | object or array | | Calculates the collision box used when colliding with objects | 
| clip | object or array | | Calculates the collision box used when raycasting. Such as crosshair selection and projectile collision. <br> (Then when the AABB has no volume, the crosshairs and projectiles will ignore this block) | 

When collision or clip is object, it is used to represent a single collision box of constant size. The structure is: 

| Key | Type | Default value | Explanation | 
| ---- | ------------ | --------- | ---------------------------------- | 
| min | array(float) | [0, 0, 0] | The three values of min must be less than or equal to the three values of max | 
| max | array(float) | [1, 1, 1] | | 

When collision or clip is array, it is used for a combination of multiple collision boxes that can be changed, usually for a custom block model that can be changed. The structure of the element is: 

| | Type | Default value | Explanation | 
| ------ | ------------ | --------- | ------------------------------------------------------------ | 
| enable | molang | true | Controls whether to enable the collision box<br/>Currently only supports is_connect query, see [netease:connection](#netease_connection) for details | 
| min | array(float) | [0, 0, 0] | The three values of min must be less than or equal to the three values of max | 
| max | array(float) | [1, 1, 1] | | 

<span id="netease_face_directional"></span> 

### netease:face_directional 

Used to set the multi-facetedness of the block 


Mainly used for [multi-facing](./2-function.md#duomianxiang) function 

| key | type | default value | explanation | 
| ---- | ------ | ------ | ----------------------------------------------------- | 
| type | string | | direction: four-facing block<br>facing_direction: six-facing block | 

<span id="netease_render_layer"></span> 

### netease:render_layer 

Used to set the material used when rendering blocks 

Please refer to the customblocks:customblocks_model_flower block in [CustomBlocksMod](../../13-module SDK programming/60-Demo example.md#CustomBlocksMod). 

| Key | Type | Default | Explanation | 
| ----- | ------ | ------ | ------------------------------------------------------------ | 
| value | string | | Currently supported materials are: <br>opaque: opaque, i.e. "terrain_opaque" material. This is the default <br>alpha: fully transparent, i.e. "terrain_alpha" material, such as flames and leaves. <br>blend: semi-transparent, i.e. "terrain_blend" material, such as stained glass | 

<span id="netease_solid"></span> 

### netease:solid 

Used to set whether the block is a solid block, which is mainly related to whether the creature is suffocated when in the block. 

Please refer to the customblocks:customblocks_model_flower block in [CustomBlocksMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBlocksMod). 

| Key | Type | Default | Explanation | 
| ----- | ---- | ------ | ------------------------------------------------------------ | 
| value | bool | true | When true, creatures will take suffocation damage in the block<br>When false, creatures will not take suffocation damage in the block | 

<span id="netease_pathable"></span> 

### netease:pathable 

Used to set whether the block is considered an obstacle when the game AI is pathfinding. 

Please refer to the customblocks:customblocks_model_flower block in [CustomBlocksMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBlocksMod). 

| Key | Type | Default | Explanation | 
| ----- | ---- | ------ | ------------------------------------------------------------ | 
| value | bool | false | When true, it is treated as air during pathfinding<br>When false, it is treated as an obstacle during pathfinding and can be walked on | 

<span id="netease_block_entity"></span> 
### netease:block_entity 

Used to add [custom block entity](./4-custom block entity.md) to custom blocks. 

Please refer to the customblocks:customblocks_test_block_entity block in [CustomBlocksMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBlocksMod). 

| Key | Type | Default | Explanation |

| ------- | ---- | ------ | ------------------------------------------------------------ | 
| tick | bool | false | When true, when the player enters the tick range of the block, the block will send **20** ServerBlockEntityTickEvent events per second<br>When false, the block will not send ServerBlockEntityTickEvent events | 
| movable | bool | true | When true, the block can be pulled back by a sticky piston<br>When false, the block cannot be pulled back by a sticky piston | 

<span id="netease_random_tick"></span> 

### netease:random_tick 

Used to define whether a custom block can be randomly ticked, and set whether the tick event is sent to the script layer. 

| Key | Type | Default | Explanation | 
| -------------- | ---- | ------ | ------------------------------------------------------------ | 
| enable | bool | false | Whether the block is ticked randomly | 
| tick_to_script | bool | false | Whether to send the event <a href="../../../../mcdocs/1-ModAPI/事件/方块.html#blockrandomtickserverevent" rel="noopenner"> BlockRandomTickServerEvent </a> to the python script | 

### netease:redstone_property 

Used to set redstone properties for custom blocks 

| Key | Type | Default | Explanation | 
| ----- | ---- | ------ | ------------------------------------------------------------ | 
| value | str | None | Currently only support break_on_push, after setting, the block can be broken by the piston and become a drop, otherwise, the block will be pushed by the piston without being broken | 

### netease:neighborchanged_sendto_script 

| Key | Type | Default | Explanation | 
| ----- | ---- | ------ | ------------------------------------------------------------ | 
| value | bool | false | Whether to send events <a href="../../../../mcdocs/1-ModAPI/Event/Block.html#blockneighborchangedserverevent#blockneighborchangedserverevent" rel="noopenner"> BlockNeighborChangedServerEvent </a> to the script layer when the surrounding environment of the block changes | 

<span id="netease_connection"></span> 

### netease:connection 

Used to define the "connection" attribute for custom blocks 

Use enumeration to configure which blocks this block has the "connection" attribute with, and this attribute is one-way. Additional values are not supported. 

Due to the characteristics of block updates, when "Bed" and "Flag" blocks are placed at the edge of a block, they will fail to connect to other blocks. 

Please refer to the customblocks_model_wire block in [CustomBlocksMod](../../13-Module SDK Programming/60-Demo Example.md#CustomBlocksMod). 

| Key | Type | Explanation | 
| ------ | ------------- | -------------------------- | 
| blocks | array(string) | Array elements are block identifiers | 

Currently, this property is only used for is_connect queries in [netease:aabb](#netease_aabb) and [custom block model](./5-custom block model.md): 

| Name | Explanation | 
| ---------------- | ------------------------------------------------------------ | 
| query.is_connect | Pass in a parameter and return whether the block has a connection attribute with the block on the corresponding adjacent surface<br/>Parameter values and corresponding surfaces:<br>0-down surface, 1-up surface, 2-north surface, 3-south surface, 4-west surface, 5-east surface. |


<span id="netease_redstone"></span> 

### netease:redstone 

Used to configure custom redstone source and custom redstone mechanical components; 

You can configure the type of custom redstone, such as redstone source or redstone mechanical components; 

You can configure the initial signal strength, the default is 15. 

| Key | Type | Default | Description | 
| -------- | ---- | ------ | ---------------------------------------------- | 
| type | str | | Redstone type: <br/>producer: redstone source <br/>consumer: redstone mechanism component | 
| strength | int | 15 | Redstone signal value, range [0,15] | 

<span id="listen_block_remove"></span> 

### netease:listen_block_remove 

Used to configure whether the custom block listens to the <a href="../../../../mcdocs/1-ModAPI/Events/Blocks.html#blockremoveserverevent" rel="noopenner"> BlockRemoveServerEvent </a> event of the block 

| Key | Type | Default | Description | 
| ----- | ---- | ------ | ------------ | 
| value | bool | false | Whether to listen to events | 

<span id="netease_may_place_on"></span> 

### netease:may_place_on 

Used to configure which blocks a custom block can be placed on. 

It will take effect when the player right-clicks to place a block; and when the block below an existing block changes. 

Please refer to customblocks_model_flower in the CustomBlocksMod example 

| Key | Type | Default value | Description | 
| --------------- | ------------ | ------ | ------------------------------------------------------------ | 
| block | list(str) | | List of block identifiers. All [block states](../../10-Basic concepts/1-My world basic concepts.md#Block states) of these blocks can be placed | 
| block_state | list(object) | | List of [block states](../../10-Basic concepts/1-My world basic concepts.md#Block states). <br>Each element corresponds to only one specific block state. If a block has multiple types of states, all permutations and combinations need to be considered<br>The blocks that can be placed on it are the union of the block field and the block_state field | 
| spawn_resources | bool | true | Whether to generate drops when an existing block is destroyed due to changes in the blocks below | 

<span id="netease_fire_resistant"></span> 

### netease:fire_resistant 

Used to configure whether a custom block is fireproof. 


When set to fireproof, the blocks' drops will be like netherite, not destroyed by fire, and will bounce away when dropped into lava. 

Please refer to customblocks_test_ore in the CustomBlocksMod example 

| Key | Type | Default value | Description | 
| ----- | ---- | ------ | -------- | 
| value | bool | | Fireproof or not | 

### netease:block_properties 

Used to configure the block properties of custom blocks 

These block properties can be superimposed, mainly used for the engine to judge the logic of some block characteristics 

Please refer to customblocks_slime and customblocks_flower_extend in the CustomBlocksMod example 

| Key | Type | Default value | Description | 
| ----- | ---- | ------ | -------- | 
| properties | array | | All property strings | 

Among them, the properties array currently supports the following string filling 

| Key | Description | 
| ----- |-------- | 
| piston_block_grabber | Whether to drive the adjacent blocks when being pushed by the piston | 
| slime | Mainly used to modify the calculation of entity force when it becomes a moving block (such as being pushed by a piston) | 
|breaks_when_fallen_on_by_heavy| When the gravity block stops falling on the block position, whether it is destroyed| 

If the block collision box volume is reduced using netease:aabb or minecraft:entity_collision, it may not be triggered (the current reference range is that it will not be triggered if the side length is less than 0.4). 

### netease:on_stand_on 

Used to trigger the event of the entity standing on the block 

Please refer to customblocks_slime in the CustomBlocksMod example, which uses this event combination to create an effect that simulates the original slime block. 

| Key | Type | Default value | Description | 
| ----- | ---- | ------ | -------- | 
| send_python_event | bool | | Send event to python | 

When send_python_event is true, the block will trigger OnStandOnBlockClientEvent and OnStandOnBlockServerEvent events. 

If the block collision box volume is reduced using netease:aabb or minecraft:entity_collision, it may not be triggered (the current reference range is that it will not be triggered if the side length is less than 0.4). 

### netease:on_before_fall_on 

It is used to trigger the event when the entity just falls to the block, mainly used for damage calculation 

You can refer to customblocks_slime in the CustomBlocksMod example, which uses this event combination to create an effect that simulates the original slime block. 


| Key | Type | Default | Description | 
| ----- | ---- | ------ | -------- | 
| send_python_event | bool | | Send event to python | 

When send_python_event is true, the block will trigger the OnBeforeFallOnBlockServerEvent event. 

If the collision box of the block is reduced using netease:aabb or minecraft:entity_collision, it may not be triggered (the current reference range is that it will not be triggered if the side length is less than 0.4). 

### netease:on_after_fall_on 

It is used to trigger the event after the entity falls to the block, mainly used for force calculation 

You can refer to customblocks_slime in the CustomBlocksMod example, which uses this event combination to create an effect that simulates the original slime block. 

| Key | Type | Default | Description | 
| ----- | ---- | ------ | -------- | 
| send_python_event | bool | | Send event to python | 

When send_python_event is true, the block will trigger OnAfterFallOnBlockClientEvent and OnAfterFallOnBlockServerEvent events. 

If the size of the block collision box is reduced using netease:aabb or minecraft:entity_collision, it may not be triggered (the current reference range is that it will not be triggered if the side length is less than 0.4). 

### netease:on_entity_inside 

It is used to trigger the event when there is a block at the location of the entity collision box (the logic of judging whether there is a block at the location has nothing to do with the size of the block collision box). 

You can refer to customblocks_flower_extend in the CustomBlocksMod example, which uses this event to simulate the deceleration effect when passing through the original spider web. 

| Key | Type | Default | Description | 
| ----- | ---- | ------ | -------- | 
| send_python_event | bool | | Send event to python | 

When send_python_event is true, the block will trigger OnEntityInsideClientEvent and OnEntityInsideServerEvent events. 

### netease:on_step_on 

Used to trigger the event when the entity just moves onto a solid block 

Please refer to customblocks_slime in the CustomBlocksMod example, which prints logs when the event is triggered 

| Key | Type | Default | Description | 
| ----- | ---- | ------ | -------- | 
| send_python_event | bool | | Send event to python | 

When send_python_event is true, the block will trigger StepOnBlockServerEvent and StepOnBlockClientEvent events. 

### netease:on_step_off 

Used to trigger the event when the entity just leaves a solid block


Please refer to customblocks_slime in the CustomBlocksMod example, where logs are printed when this event is triggered. 

| Key | Type | Default | Description | 
| ----- | ---- | ------ | -------- | 
| send_python_event | bool | | Whether to send events to python | 

When send_python_event is true, this block will trigger StepOffBlockServerEvent and StepOffBlockClientEvent events. 

