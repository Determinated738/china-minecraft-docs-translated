--- 
sidebarDepth: 1 
--- 
# Blocks 

# Index 

| Event | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [BlockDestroyByLiquidServerEvent](Block.md#blockdestroybyliquidserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger: Event when a block is destroyed by water | 
| [BlockLiquidStateChangeAfterServerEvent](Block.md#blockliquidstatechangeafterserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger: Triggered when a block becomes waterlogged or leaves water (fluid) | 
| [BlockLiquidStateChangeServerEvent](Block.md#blockliquidstatechangeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: When the block becomes water-containing or before it leaves the water-containing (fluid) state | 
| [BlockNeighborChangedServerEvent](Block.md#blockneighborchangedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: When the blocks around the custom block change, you need to configure netease:neighborchanged_sendto_script. For details, please refer to the "Custom Crops" document | 
| [BlockRandomTickServerEvent](Block.md#blockrandomtickserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: Custom block configuration <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html#netease-random-tick">netease:random_tick</a> Random tick | 
| [BlockRemoveServerEvent](Block.md#blockremoveserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: The block listening to this event is triggered when it is destroyed. You can listen through the [ListenOnBlockRemoveEvent](#listenonblockremoveevent) method, or configure it through the json component <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html#netease-listen-block-remove">netease:listen_block_remove</a> | 
| [BlockSnowStateChangeAfterServerEvent](Block.md#blocksnowstatechangeafterserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: After the block turns to contain snow or leaves the snow | 
| [BlockSnowStateChangeServerEvent](Block.md#blocksnowstatechangeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: Before the block turns to contain snow or leaves the snow | 
| [BlockStrengthChangedServerEvent](Block.md#blockstrengthchangedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: When the redstone semaphore of the custom mechanical component block changes | 
| [ChestBlockTryPairWithServerEvent](块.md#chestblocktrypairwithserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: When two small chest blocks side by side are ready to be combined into a large chest block | 
| [ClientBlockUseEvent](块.md#clientblockuseevent) | <span style="display:inline;color:#7575f9">Client</span> | Trigger time: When the player right-clicks the new version of the custom block (or adds the MC native game block to listen through the interface AddBlockItemListenForUseEvent), the client throws this event (this event is ticked, so you need to pay attention to efficiency issues). | 
| [CommandBlockContainerOpenEvent](方块.md#commandblockcontaineropenevent) | <span style="display:inline;color:#ff5555">服务器</span> | Trigger time: When the player clicks the command block and tries to open the command block settings interface | 
| [CommandBlockUpdateEvent](方块.md#commandblockupdateevent) | <span style="display:inline;color:#ff5555">服务器</span> | Trigger time: When the player tries to modify the built-in command of the command block | 
| [DestroyBlockEvent](方块.md#destroyblockevent) | <span style="display:inline;color:#ff5555">服务器</span> | Trigger time: This event is triggered when the block has been destroyed by the player. | 
| [DirtBlockToGrassBlockServerEvent](Block.md#dirtblocktograssblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger Time: When a dirt block turns into a grass block | 
| [EntityPlaceBlockAfterServerEvent](Block.md#entityplaceblockafterserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger Time: When a mob successfully places a block | 
| [FallingBlockBreakServerEvent](Block.md#fallingblockbreakserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger Time: When a falling block entity is destroyed, the server triggers this event | 
| [FallingBlockCauseDamageBeforeClientEvent](Block.md#fallingblockcausedamagebeforeclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggering time: When the falling block starts to calculate the damage of hitting the entity, the client triggers this event | 
| [FallingBlockCauseDamageBeforeServerEvent](Block.md#fallingblockcausedamagebeforeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: When the falling block starts to calculate the damage of hitting the entity, the server triggers this event | 
| [FallingBlockReturnHeavyBlockServerEvent](Block.md#fallingblockreturnheavyblockserverevent) | style="display:inline;color:#ff5555">Server</span> | Trigger Time: When the falling block entity turns back to a normal gravity block, the server triggers this event | 
| [FarmBlockToDirtBlockServerEvent](Block.md#farmblocktodirtblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger Time: Trigger when farmland degenerates into dirt | 
| [GrassBlockToDirtBlockServerEvent](Block.md#grassblocktodirtblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger Time: Trigger when grass blocks turn into dirt blocks | 
| [HeavyBlockStartFallingServerEvent](Block.md#heavyblockstartfallingserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: When the gravity block becomes a falling block entity, the server triggers this event | 
| [HopperTryPullInServerEvent](Block.md#hoppertrypullinserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: When the container is connected to the top of the hopper, it is triggered when the container starts to input items into the hopper. The event is only triggered once | 
| [HopperTryPullOutServerEvent](Block.md#hoppertrypulloutserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: When the hopper is connected to the container in an adjacent way, that is, when the container is connected from the side, it is triggered when the hopper starts to output items to the container. The event is only triggered once | 
| [OnAfterFallOnBlockClientEvent](Block.md#onafterfallonblockclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Trigger timing: The client triggers when the entity lands on the block, mainly used for force calculation | 
| [OnAfterFallOnBlockServerEvent](Block.md#onafterfallonblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger timing: The server triggers when the entity lands on the block, mainly used for force calculation | 
| [OnBeforeFallOnBlockServerEvent](Block.md#onbeforefallonblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger timing: The server triggers when the entity just lands on the block, mainly used for damage calculation | 
| [OnEntityInsideBlockClientEvent](Block.md#onentityinsideblockclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Trigger timing: When there is a block in the area where the entity collision box is located, the client will continue to trigger | 
| [OnEntityInsideBlockServerEvent](Block.md#onentityinsideblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger timing: When there is a block in the area where the entity collision box is located, the server will continue to trigger | 
| [OnModBlockNeteaseEffectCreatedClientEvent](Block.md#onmodblockneteaseeffectcreatedclientevent) | <span style="display:inline;color:#7575f9">Client</span> | The special effect bound to the custom block entity is created successfully. It is triggered when the special effect bound to the custom block entity is created successfully and when the interface CreateFrameEffectForBlockEntity or CreateParticleEffectForBlockEntity is used to successfully add special effects to the custom block entity. | 
| [OnStandOnBlockClientEvent](Block.md#onstandonblockclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Trigger time: Client continues to trigger when the entity stands on the block | 
| [OnStandOnBlockServerEvent](Block.md#onstandonblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: Server continues to trigger when the entity stands on the block | 
| [PistonActionServerEvent](Block.md#pistonactionserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: When a piston or sticky piston pushes/retracts to affect nearby blocks | 
| [PlayerTryDestroyBlockClientEvent](Block.md#playertrydestroyblockclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Fired by the client thread when the player is about to destroy a block. Mainly used for blocks such as beds, flags, and boxes that are rendered based on block entity data. In general, please use ServerPlayerTryDestroyBlockEvent | 
| [ServerBlockEntityTickEvent](块.md#serverblockentitytickevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: The custom block is configured with the netease:block_entity component and tick is set to true. The block is within the player's simulation distance (which can be set when creating a new archive, the default is 4 blocks) or within the tickingarea. Triggering | 
| [ServerBlockUseEvent](块.md#serverblockuseevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: When the player right-clicks the new version of the custom block (or adds the MC native game block to listen through the interface AddBlockItemListenForUseEvent), the server throws this event (this event is ticked, so you need to pay attention to efficiency issues). | 
| [ServerEntityTryPlaceBlockEvent](Block.md#serverentitytryplaceblockevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: This event is triggered when a creature tries to place a block. | 
| [ServerPlaceBlockEntityEvent](块.md#serverplaceblockentityevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: Triggered when a block with a custom block entity is manually placed or created through the interface. At this time, data can be stored in the block entity. | 
| [ServerPlayerTryDestroyBlockEvent](块.md#serverplayertrydestroyblockevent) | <span style="display:inline;color:#ff5555">Server</span> | The server thread triggers this event when the player is about to destroy the block. | 
| [ShearsDestoryBlockBeforeClientEvent](块.md#shearsdestoryblockbeforeclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggering time: When the player holds scissors to destroy blocks, blocks with scissors special effects will trigger this event in the client thread |

| [ShearsDestoryBlockBeforeServerEvent](Cube.md#shearsdestoryblockbeforeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: When a player destroys a block with scissors, the block with the scissors special effect will trigger this event in the server thread | 
| [StartDestroyBlockClientEvent](Cube.md#startdestroyblockclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when the player starts to dig a block. Not triggered in creative mode. | 
| [StartDestroyBlockServerEvent](Cube.md#startdestroyblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the player starts to dig a block. Not triggered in creative mode. | 
| [StepOffBlockClientEvent](Block.md#stepoffblockclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when: the entity moves off a solid block | 
| [StepOffBlockServerEvent](Block.md#stepoffblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when: the entity moves off a solid block | 
| [StepOnBlockClientEvent](Block.md#steponblockclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when: the entity just moves to a new solid block. | 
| [StepOnBlockServerEvent](Block.md#steponblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when: When an entity just moves to a new solid block. | 
# Block 

## BlockDestroyByLiquidServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: Event when a block is destroyed by water 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| liquidName | str | Fluid block id | 
| blockName | str | Block id | 
| auxValue | int | Block additional value | 

- Return value 

None 

- Notes 
- The setting of command or interface will not trigger this event 

## BlockLiquidStateChangeAfterServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: Triggered after the block becomes water-containing or leaves water-containing (fluid) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, including namespace and name |

| auxValue | int | Block additional value | 
| dimension | int | Block dimension | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| turnLiquid | bool | Whether to turn to water, true to turn to water, false to leave water | 

- Return value 

None 

## BlockLiquidStateChangeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: Triggered before the block turns to water or leaves water (fluid) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | The identifier of the block, including the namespace and name | 
| auxValue | int | Block additional value | 
| dimension | int | Block dimension | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| turnLiquid | bool | Whether to turn to water, true to turn to water, false to turn out of water | 

- Return value 

None 

## BlockNeighborChangedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: When the blocks around the custom block change, you need to configure netease:neighborchanged_sendto_script. For details, please refer to the "Custom Crops" document 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| dimensionId | int | Dimension | 
| posX | int | Block x coordinate | 
| posY | int | Block y coordinate | 
| posZ | int | Block z coordinate | 
| blockName | str | Block identifier, including namespace and name | 
| auxValue | int | Block additional value | 
| neighborPosX | int | Changed block x coordinate | 
| neighborPosY | int | Changed block y coordinate | 
| neighborPosZ | int | Changed block z coordinate | 
| fromBlockName | str | Block identifier before change, including namespace and name | 
| fromBlockAuxValue | int | Block additional value before change | 
| toBlockName | str | Block identifier after change, including namespace and name | 
| toAuxValue | int | Additional value after the block changes | 

- Return value 

None 

## BlockRandomTickServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: Custom block configuration <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html#netease-random-tick">netease:random_tick</a> Random tick 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posX | int | Block x coordinate | 
| posY | int | Block y coordinate | 
| posZ | int | Block z coordinate | 
| blockName | str | Block name | 
| fullName | str | Block identifier, including namespace and name | 
| auxValue | int | Block additional value | 
| dimensionId | int | Entity dimension | 

- Return value 

None 

## BlockRemoveServerEvent 

<span style="display:inline;color:#ff5555">Server</span>


- Description 

Triggering time: The block listening to this event is triggered when it is destroyed. You can listen through the [ListenOnBlockRemoveEvent](#listenonblockremoveevent) method, or configure it through the json component <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html#netease-listen-block-remove">netease:listen_block_remove</a> 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| x | int | Block position x | 
| y | int | Block position y | 
| z | int | Block position z | 
| fullName | str | Block identifier, including namespace and name | 
| auxValue | int | Additional value of the block | 
| dimension | int | The dimension where the block is located | 

- Return value 

None 

### Related interfaces 

<span id="ListenOnBlockRemoveEvent"></span> 
### ListenOnBlockRemoveEvent 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Whether to listen to the block BlockRemoveServerEvent event, you can dynamically modify the value of the json component <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Components.html#netease-listen-block-remove">netease:listen_block_remove</a> 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| identifier | str | Block identifier, such as minecraft:wheat | 
| listen | bool | Whether to listen | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- For some special blocks, pay attention to using the corresponding block ID parameter (such as brick stairs, the block ID to be listened should be minecraft:brick_block) 

- Example


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.ListenOnBlockRemoveEvent("minecraft:wheat", True) 
``` 

## BlockSnowStateChangeAfterServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: Trigger after the block turns to contain snow or leaves the snow 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Block dimension | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| turnSnow | bool | Whether to turn to snow, true to turn to snow, false to leave snow | 
| setBlockType | int | Reasons for the block to enter or leave snow, refer to [SetBlockType](../enumeration value/SetBlockType.md) | 

- Return value 

None 

## BlockSnowStateChangeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: Triggered before the block turns to snow or leaves snow 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Block dimension | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate |

| turnSnow | bool | Whether to turn to snow, true to turn to snow, false to leave snow | 
| setBlockType | int | Reasons for the block to enter and leave snow, refer to [SetBlockType](../enumeration value/SetBlockType.md) | 

- Return value 

None 

## BlockStrengthChangedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: Triggered when the redstone semaphore of the custom mechanical component block changes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posX | int | Block x coordinate | 
| posY | int | Block y coordinate | 
| posZ | int | Block z coordinate | 
| blockName | str | Block identifier, including namespace and name | 
| auxValue | int | Block additional value | 
| newStrength | int | Redstone semaphore after change | 
| dimensionId | int | Dimension | 

- Return value 

None 

## ChestBlockTryPairWithServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: When two small chest blocks side by side are ready to be combined into a large chest block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| cancel | bool | Whether to allow triggering, the default is False, if set to True, it can prevent small chests from combining into a large chest | 
| blockX | int | x coordinate of the small box block | 
| blockY | int | y coordinate of the small box block |

| blockZ | int | z coordinate of the small box block | 
| otherBlockX | int | x coordinate of another small box block to be combined with it | 
| otherBlockY | int | y coordinate of another small box block to be combined with it | 
| otherBlockZ | int | z coordinate of another small box block to be combined with it | 
| dimensionId | int | dimension id | 

- Return value 

None 

## ClientBlockUseEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger timing: When the player right-clicks the new version of the custom block (or adds the MC native game block to listen through the interface AddBlockItemListenForUseEvent), the client throws this event (this event is ticked, so you need to pay attention to efficiency issues). 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| blockName | str | Block identifier, including namespace and name | 
| aux | int | Block additional value | 
| cancel | bool | Set to True to intercept the logic of interacting with the block. | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 

- Return value 

None 

- Remarks 
- Some blocks are effective when cancel is set in ServerBlockUseEvent, but some blocks are effective only when cancel is set in ClientBlockUseEvent. If necessary, it is recommended to set cancel in both events to ensure effectiveness. 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

### Related Interfaces 

<span id="AddBlockItemListenForUseEvent"></span> 
### AddBlockItemListenForUseEvent 

method in mod.client.component.blockUseEventWhiteListCompClient.BlockUseEventWhiteListComponentClient 

- Description


Add script layer monitoring of ClientBlockUseEvent event to blockName 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block name, format: namespace:name:auxvalue, where namespace:name:* matches all auxvalue | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockUseEventWhiteList(clientApi.GetLevelId()) 
comp.AddBlockItemListenForUseEvent("minecraft:nether_brick_stairs:2") 
# Note that the format of blockName is namespace:name:auxvalue. If auxvalue is not filled in, it defaults to 0 
# For detailed values of auxValue, please refer to the official wiki, such as 'Block Data Value' in https://minecraft-zh.gamepedia.com/梯 
``` 

<span id="RemoveBlockItemListenForUseEvent"></span> 
### RemoveBlockItemListenForUseEvent 

method in mod.client.component.blockUseEventWhiteListCompClient.BlockUseEventWhiteListComponentClient 

- Description 

Remove the script layer listening of the blockName block to the ClientBlockUseEvent event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block name, format: namespace:name:auxvalue, where namespace:name:* matches all auxvalue | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the removal is successful | 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockUseEventWhiteList(clientApi.GetLevelId()) 
comp.RemoveBlockItemListenForUseEvent("minecraft:nether_brick_stairs:2") 
# Note that the format of blockName is namespace:name:auxvalue. If auxvalue is not filled in, it defaults to 0 
# For detailed values of auxValue, please refer to the official wiki, such as 'Block Data Value' in https://minecraft-zh.gamepedia.com/梯 
``` 

<span id="ClearAllListenForBlockUseEventItems"></span> 
### ClearAllListenForBlockUseEventItems 

method in mod.client.component.blockUseEventWhiteListCompClient.BlockUseEventWhiteListComponentClient 

- Description 

Clear all script-level listeners for ClientBlockUseEvent events for added blocks 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether clearing is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockUseEventWhiteList(clientApi.GetLevelId()) 
comp.ClearAllListenForBlockUseEventItems() 
``` 

## CommandBlockContainerOpenEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: The player clicks the command block and tries to open the command block settings interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| playerId | str | player entity id | 
| isBlock | bool | whether to locate the command block in the form of block coordinates, when True, the following blockX/blockY/blockZ are meaningful, when False, the following victimId is meaningful | 
| blockX | int | command block position x, valid when isBlock is True | 
| blockY | int | command block position y, valid when isBlock is True | 
| blockZ | int | command block position z, valid when isBlock is True | 
| victimId | str | unique id of the logical entity corresponding to the command block, valid when isBlock is False | 
| cancel | bool | when changed to True, it can prevent players from opening the command block setting interface | 

- return value 

None 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## CommandBlockUpdateEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: When the player attempts to modify the built-in command of the command block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| playerUid | int/long | Player's uid | 
| command | str | Command content string in the command block to be modified | 
| isBlock | bool | Whether to locate the command block in the form of block coordinates. When True, the following blockX/blockY/blockZ are meaningful. When False, the following victimId is meaningful. | 
| blockX | int | Command block position x, valid when isBlock is True | 
| blockY | int | Command block position y, valid when isBlock is True | 
| blockZ | int | Command block position z, valid when isBlock is True | 
| victimId | str | The unique id of the logical entity corresponding to the command block, valid when isBlock is False | 
| cancel | bool | When changed to True, it can prevent players from modifying the built-in commands of the command block | 

- Return value 

None 

- Notes 
- When the target of modification is the command block minecart (isBlock is False at this time), setting cancel to True can still prevent the modification of the internal instructions of the command block minecart, but the client can see that the internal instructions of the command block minecart have changed, but this is just an illusion. Re-login or open the setting interface of the command block minecart with other clients, and you will find that the internal instructions have not changed. 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## DestroyBlockEvent 


<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: This event is triggered when the block has been destroyed by the player. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| face | int | Block facing id, see [Facing enumeration](../enumeration value/Facing.md) | 
| fullName | str | Block identifier, including namespace and name | 
| auxData | int | Block additional value | 
| playerId | str | ID of the player who destroyed the block | 
| dimensionId | int | Dimension id | 

- Return value 

None 

- Notes 
- Triggered in both survival mode and creative mode 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## DirtBlockToGrassBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: Triggered when the dirt block turns into a grass block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Block dimension | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 

- Return value 

None 


- Notes 
- Commands or interface settings will not trigger this event 

## EntityPlaceBlockAfterServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: When the creature successfully places a block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| fullName | str | Block identifier, including namespace and name | 
| auxData | int | Block additional value | 
| entityId | str | ID of the creature trying to place the block | 
| dimensionId | int | Dimension id | 
| face | int | Click the face of the block, refer to [Facing enumeration](../enumeration value/Facing.md) | 

- Return value 

None 

- Notes 
- Some blocks that will generate entities, operable blocks, and blocks with special logic after placement will not trigger this event, including but not limited to beds, doors, signs, flower pots, redstone repeaters, ships, cauldrons, head models, cakes, brewing stands, armor stands, etc. 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## FallingBlockBreakServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: When the falling block entity is destroyed, the server triggers this event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fallingBlockId | str | Falling block entity id | 
| fallingBlockX | float | Falling block entity position x |

| fallingBlockY | float | The y position of the falling block entity | 
| fallingBlockZ | float | The z position of the falling block entity | 
| blockName | str | The identifier of the gravity block, including the namespace and name | 
| fallTickAmount | int | How many ticks the falling block entity has been falling | 
| dimensionId | int | The dimension id of the falling block entity | 
| cancelDrop | bool | Whether to cancel the block item drop, which can be set in the script layer | 

- Return value 

None 

- Notes 
- Not all falling blocks will trigger this event, you need to configure the trigger switch in json first (for details, refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/3-Special Blocks/6-Custom Gravity Blocks.html">Custom Gravity Blocks</a>） 

## FallingBlockCauseDamageBeforeClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggering time: When the falling block starts to calculate the damage of hitting the entity, the client triggers this event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fallingBlockId | int | Falling block entity id | 
| fallingBlockX | float | Falling block entity position x | 
| fallingBlockY | float | The y position of the falling block entity | 
| fallingBlockZ | float | The z position of the falling block entity | 
| blockName | str | The identifier of the gravity block, including the namespace and name | 
| dimensionId | int | The dimension id of the falling block entity | 
| collidingEntitys | list(str) | The id of the entity currently colliding (client can only get the player), or None if there is none | 
| fallTickAmount | int | How many ticks the falling block entity has been falling | 
| fallDistance | float | How far the falling block entity has been falling | 
| isHarmful | bool | Always false on the client side, because the client does not calculate the damage value | 
| fallDamage | int | The damage to the entity | 

- Return Value 

None 

- Notes 
- Not all falling blocks will trigger this event. You need to configure the trigger switch in json first (for details, please refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/3-Special Blocks/6-Custom Gravity Blocks.html">Custom Gravity Blocks</a>) 
- When the parameter data of this event (fallTickAmount, fallDistance, collidingEntitys, fallDamage) differs from the server-side event FallingBlockCauseDamageBeforeServerEvent data, please refer to the server-side event data. 



## FallingBlockCauseDamageBeforeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: When the falling block starts calculating the damage of hitting the entity, the server triggers this event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fallingBlockId | str | Falling block entity id | 
| fallingBlockX | float | Falling block entity position x | 
| fallingBlockY | float | Falling block entity position y | 
| fallingBlockZ | float | Falling block entity position z | 
| blockName | str | Gravity block identifier, including namespace and name | 
| dimensionId | int | Dimension id of the falling block entity | 
| collidingEntitys | list(str) | List ids of the entities currently colliding, or None if none | 
| fallTickAmount | int | How many ticks the falling block entity has been falling | 
| fallDistance | float | How far the falling block entity has been falling | 
| isHarmful | bool | Whether to calculate damage to the entity. The value sent by the engine is determined by the json configuration and whether the damage is greater than 0. It can be modified and returned to the engine at the script level. | 
| fallDamage | int | Damage to the entity. The value sent by the engine is determined by the distance and json configuration. It can be modified and returned to the engine at the script level. | 

- Return value 

None 

- Notes 
- Not all falling blocks will trigger this event. You need to configure the trigger switch in json first (for details, please refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/3-Special Blocks/6-Custom Gravity Blocks.html">Custom Gravity Blocks</a>) 
- The server is usually triggered after the client, and sometimes there is a difference of one tick, which means that the following phenomenon may occur: the fallTickAmount of the server is 1 tick longer than the configured forced destruction time, and the calculated falling distance and falling damage are 1 tick longer than the client time. 

## FallingBlockReturnHeavyBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: When the falling block entity turns back into a normal gravity block, the server triggers this event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fallingBlockId | int | Falling block entity id | 
| blockX | int | Block position x | 
| blockY | int | Block position y | 
| blockZ | int | Block position z |

| heavyBlockName | str | The identifier of the gravity block, including namespace and name | 
| prevHereBlockName | str | The identifier of the original block position when it turns back to a gravity block, including namespace and name | 
| dimensionId | int | The dimension id of the falling block entity | 
| fallTickAmount | int | How many ticks the falling block entity has been falling | 

- Return value 

None 

- Notes 
- Not all falling blocks will trigger this event, you need to configure the trigger switch in json first (for details, please refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/3-Special Blocks/6-Custom Gravity Blocks.html">Custom Gravity Blocks</a>) 

## FarmBlockToDirtBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: Triggered when farmland degenerates into soil 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Block dimension | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| setBlockType | int | Reasons for farmland degenerating into soil, refer to [SetBlockType](../enumeration value/SetBlockType.md) | 

- Return value 

None 

- Remarks 
- Command or interface settings will not trigger this event 

## GrassBlockToDirtBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: When the grass block turns into a dirt block 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Block dimension | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 

- Return value 

None 

- Remarks 
- Command or interface settings will not trigger this event 

## HeavyBlockStartFallingServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: When the gravity block becomes a falling block entity, the server triggers this event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fallingBlockId | str | Entity ID of the falling block | 
| blockX | int | Block position x | 
| blockY | int | Block position y | 
| blockZ | int | Block position z | 
| blockName | str | Gravity block identifier, including namespace and name | 
| dimensionId | int | Dimension ID of the falling block entity | 

- Return value 

None 

- Notes 
- Not all falling blocks will trigger this event, you need to configure the trigger switch in json first (for details, please refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/3-Special Blocks/6-Custom Gravity Blocks.html">Custom Gravity Blocks</a>) 

## HopperTryPullInServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description


Trigger timing: When a container is connected above the hopper, it is triggered when the container starts to input items into the hopper. The event is triggered only once. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| x | int | Hopper position x | 
| y | int | Hopper position y | 
| z | int | Hopper position z | 
| abovePosX | int | Interactive container position x | 
| abovePosY | int | Interactive container position y | 
| abovePosZ | int | Interactive container position z | 
| dimensionId | int | Dimension id | 
| canHopper | bool | Whether to allow the container to add things to the hopper (to turn off this interaction, you need to listen to this event before placing the container) | 

- Return value 

None 

## HopperTryPullOutServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: When the hopper is connected to the container in an adjacent way, that is, when the container is connected from the side, the hopper starts to output items to the container. The event is triggered only once. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| x | int | Hopper position x | 
| y | int | Hopper position y | 
| z | int | Hopper position z | 
| attachedPosX | int | Interactive container position x | 
| attachedPosY | int | Interactive container position y | 
| attachedPosZ | int | Interactive container position z | 
| dimensionId | int | Dimension id | 
| canHopper | bool | Whether to allow the hopper to add things to the container (to turn off this interaction, you need to listen to this event before placing the container) | 

- Return value 

None 

## OnAfterFallOnBlockClientEvent


<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger timing: The client triggers when the entity lands on the block, mainly used for force calculation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| posX | float | Entity position x | 
| posY | float | Entity position y | 
| posZ | float | Entity position z | 
| motionX | float | Instantaneous movement force in the X direction | 
| motionY | float | Instantaneous movement force in the Y direction | 
| motionZ | float | Instantaneous movement force in the Z direction | 
| blockName | str | Block identifier, including namespace and name | 
| calculate | bool | Whether to calculate force according to the value passed in the script layer | 

- Return value 

None 

- Remarks 
- Not all blocks will trigger this event, you need to configure the trigger switch in json first (for details, please refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html">Custom Block JSON Component</a>) 
- If you want to modify motion in the script layer, the return value needs to be a floating point type, for example, you need to assign 0.0 instead of 0 
- If you need to modify the force of the entity, it is best to synchronize the modification with the server event to avoid unexpected phenomena 
- Because the engine will definitely calculate the force according to the original block rules (normal blocks are set to 0, beds, slime blocks, etc. rebound), so if the script layer wants to directly modify the current force, you need to set calculate to true to cancel the original calculation and calculate according to the returned value 
- The engine will always trigger OnAfterFallOnBlockClientEvent after landing, so please make corresponding logical judgments in the script layer. 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnAfterFallOnBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: The server is triggered when the entity lands on the block, mainly used for force calculation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| posX | float | entity position x | 
| posY | float | entity position y |

| posZ | float | Entity position z | 
| motionX | float | Instantaneous force in the X direction | 
| motionY | float | Instantaneous force in the Y direction | 
| motionZ | float | Instantaneous force in the Z direction | 
| blockName | str | Block identifier, including namespace and name | 
| calculate | bool | Whether to calculate force according to the value passed at the script layer | 

- Return value 

None 

- Notes 
- Not all blocks will trigger this event. You need to configure the trigger switch in json first (for details, please refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html">Custom Block JSON Component</a>) 
- If you want to modify motion at the script layer, the return value needs to be a floating point type, for example, you need to assign 0.0 instead of 0 
- If you need to modify the force of the entity, it is best to synchronize the modification with the client event to avoid unexpected phenomena. 
- Because the engine will eventually calculate the force according to the original block rules (normal blocks are set to 0, beds, slime blocks, etc. rebound), so if the script layer wants to directly modify the current force, you need to set calculate to true to cancel the original calculation and calculate according to the returned value. 
- After the engine lands, OnAfterFallOnBlockServerEvent will always trigger, so please make corresponding logical judgments in the script layer. 

Directly declare a function of the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnBeforeFallOnBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: server-side trigger when the entity just lands on the block, mainly used for damage calculation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| blockX | int | Block position x | 
| blockY | int | Block position y | 
| blockZ | int | Block position z | 
| blockName | str | Block identifier, including namespace and name | 
| fallDistance | float | Entity fall distance, can be passed to the engine at the script level | 
| cancel | bool | Whether to cancel the engine's calculation of entity fall damage | 

- Return value 

None 

- Notes 
- Not all blocks will trigger this event, you need to configure the trigger switch in json first (for details, refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html">Custom Block JSON Component</a>) 
- If you want to modify fallDistance at the script level, the return value must be a floating point type, for example, you need to assign 0.0 instead of 0 
- It may be triggered multiple times due to slight rebounds, and the value of fallDistance can be judged at the script level 


Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnEntityInsideBlockClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger timing: When there is a block in the area where the entity collision box is located, the client continues to trigger 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| dimensionId | int | Dimension id of the entity | 
| slowdownMultiX | float | Slowdown ratio of the entity's movement speed in the X direction | 
| slowdownMultiY | float | Slowdown ratio of entity speed in Y direction | 
| slowdownMultiZ | float | Slowdown ratio of entity speed in Z direction | 
| blockX | int | Block position x | 
| blockY | int | Block position y | 
| blockZ | int | Block position z | 
| blockName | str | Block identifier, including namespace and name | 
| cancel | bool | True can be returned to the engine by the script layer to prevent subsequent original logic from being triggered | 

- Return value 

None 

- Notes 
- Not all blocks will trigger this event, and the trigger switch needs to be configured in json first (for details, please refer to <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html">Custom Block JSON Component</a>) 
, the original block needs to be registered through the RegisterOnEntityInside interface before it can be triggered 
- If you need to modify slowdownMulti/cancel, it is strongly recommended to modify it synchronously with the server event to avoid unexpected phenomena such as correction by the server. 
- If you want to modify slowdownMulti at the script level, the return must be a floating point type, for example, you need to assign 1.0 instead of 1 
- The slowdown ratio takes effect when any slowdownMulti parameter is returned with a non-zero value 
- The slowdownMulti parameter is more like a Buff, for example, it is not calculated immediately, but first saved in the entity attributes for delayed calculation, the lowest value will be taken if there is already a slowdownMulti attribute, and it is immune to falling damage, etc., which is basically consistent with the logic of the original spider web. 

Simply declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

### Related Interfaces 

<span id="RegisterOnEntityInside"></span> 
### RegisterOnEntityInside 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 


Can dynamically register and modify netease:on_entity_inside components 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 
| sendPythonEvent | bool | Whether to send Python events, True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Notes 
- Currently, only netease:on_entity_inside components of original blocks can be dynamically added and modified 
- Can call to modify the value of the original component multiple times, please use the UnRegisterOnEntityInside interface to delete the component 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.RegisterOnEntityInside("minecraft:redstone_ore", True) 
``` 

<span id="UnRegisterOnEntityInside"></span> 
### UnRegisterOnEntityInside 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

You can dynamically delete the netease:on_entity_inside component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 


- Notes 
- Currently only the netease:on_entity_inside component of the original block can be dynamically deleted 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.UnRegisterOnEntityInside("minecraft:redstone_ore") 
``` 

## OnEntityInsideBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: When there is a block in the area where the entity collision box is located, the server continues to trigger 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| slowdownMultiX | float | The slowdown ratio of the entity's speed in the X direction, which can be modified at the script level | 
| slowdownMultiY | float | The slowdown ratio of the entity's speed in the Y direction, which can be modified at the script level | 
| slowdownMultiZ | float | The slowdown ratio of the entity's speed in the Z direction, which can be modified at the script level | 
| blockX | int | Block position x | 
| blockY | int | Block position y | 
| blockZ | int | Block position z | 
| blockName | str | Block identifier, including namespace and name | 
| cancel | bool | True can be returned to the engine by the script level to prevent subsequent original logic from being triggered | 

- Return value 

None 

- Notes 
- Not all blocks will trigger this event, and the trigger switch needs to be configured in json first (for details, refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html">Custom Block JSON Component</a>) 
, the original block needs to be registered through the RegisterOnEntityInside interface before it can be triggered 
- If you need to modify slowdownMulti/cancel, it is strongly recommended to modify it synchronously with the client event to avoid unexpected phenomena such as inconsistent client performance. 
- If you want to modify slowdownMulti at the script level, the return must be a floating point type, for example, you need to assign 1.0 instead of 1 
- The slowdown ratio takes effect when any slowdownMulti parameter is returned with a non-zero value 
- The slowdownMulti parameter is more like a Buff, for example, it is not calculated immediately, but first saved in the entity attributes for delayed calculation, the lowest value will be taken if there is already a slowdownMulti attribute, and it is immune to falling damage, which is basically the same as the original spider web logic. 

Simply declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 



### Related interfaces 

<span id="RegisterOnEntityInside"></span> 
### RegisterOnEntityInside 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Can dynamically register and modify netease:on_entity_inside components 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 
| sendPythonEvent | bool | Whether to send Python events, True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Notes 
- Currently only the netease:on_entity_inside component of the original block can be dynamically added and modified 
- (Non-rental server online) Using the server-side interface to register will affect the host client component 
- You can call multiple times to modify the value of the original component. To delete the component, please use the UnRegisterOnEntityInside interface 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.RegisterOnEntityInside("minecraft:redstone_ore", True) 
``` 

<span id="UnRegisterOnEntityInside"></span> 
### UnRegisterOnEntityInside 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

The netease:on_entity_inside component can be deleted dynamically 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Notes 
- Currently, only the netease:on_entity_inside component of the original block can be dynamically deleted 
- (Non-rental service online) Using the server-side interface to register will affect the host client component 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.UnRegisterOnEntityInside("minecraft:redstone_ore") 
``` 
## OnModBlockNeteaseEffectCreatedClientEvent 
<span style="display:inline;color:#7575f9">Client</span> 
- Description 
The event of successful creation of special effects bound to custom block entities. It is triggered when the special effects bound to the custom block entity are successfully created and when the interface CreateFrameEffectForBlockEntity or CreateParticleEffectForBlockEntity is used to successfully add special effects to the custom block entity. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| effectName | str | Custom key value name of the successfully created special effect | 
| id | int | The id of the special effect | 
| effectType | int | The type of the special effect, 0 is a particle special effect, 1 is a sequence frame special effect | 
| blockPos | tuple(float,float,float) | The world coordinates of the custom block entity bound to the special effect | 

- Return value 

None 

Directly declare a function of the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnStandOnBlockClientEvent 


<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger timing: The client continues to trigger when the entity stands on the block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| dimensionId | int | Dimension id of the entity | 
| posX | float | Entity position x | 
| posY | float | Entity position y | 
| posZ | float | Entity position z | 
| motionX | float | Instantaneous movement force in the X direction | 
| motionY | float | Instantaneous movement force in the Y direction | 
| motionZ | float | Instantaneous movement force in the Z direction | 
| blockX | int | Block position x | 
| blockY | int | Block position y | 
| blockZ | int | Block position z | 
| blockName | str | Block identifier, including namespace and name | 
| cancel | bool | True can be returned to the engine by the script layer to prevent the subsequent original logic from being triggered | 

- Return value 

None 

- Notes 
- Not all blocks will trigger this event. You need to configure the trigger switch in json first (for details, please refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html">Custom Block JSON Component</a>) 
, the original block needs to be registered through the RegisterOnStandOn interface before it can be triggered 
- If you want to modify motion/cancel at the script layer, it is strongly recommended to synchronize the modification with the OnStandOnBlockServerEvent server event to avoid unexpected phenomena such as correction by the server 
- If you want to modify motion at the script level, the returned value must be a floating point type, for example, you need to assign 0.0 instead of 0 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

### Related Interfaces 

<span id="RegisterOnStandOn"></span> 
### RegisterOnStandOn 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Can dynamically register and modify netease:on_stand_on components 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 
| sendPythonEvent | bool | Whether to send Python events, True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Notes 
- Currently, only the netease:on_stand_on component of the original block can be dynamically added and modified 
- The original logic of the game will not run the OnStandOn related logic of the block client. If the interface is used to add a client component to the original block, regardless of whether the Python event is sent, the original block will run more client-related logic, 
For example, blocks like slime blocks that have certain physical calculations will feel different after running the calculations one more time on the client. 
- You can call multiple times to modify the value of the original component. To delete the component, please use the UnRegisterOnStandOn interface 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.RegisterOnStandOn("minecraft:redstone_ore", True) 
``` 

<span id="UnRegisterOnStandOn"></span> 
### UnRegisterOnStandOn 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

You can dynamically delete the netease:on_stand_on component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Notes 
- Currently, only the netease:on_stand_on component of the original block can be dynamically deleted.


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.UnRegisterOnStandOn("minecraft:redstone_ore") 
``` 

## OnStandOnBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: Server continues to trigger when the entity stands on the block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| dimensionId | int | Dimension id of the entity | 
| posX | float | Entity position x | 
| posY | float | entity position y | 
| posZ | float | entity position z | 
| motionX | float | instantaneous movement force in the X direction | 
| motionY | float | instantaneous movement force in the Y direction | 
| motionZ | float | instantaneous movement force in the Z direction | 
| blockX | int | block position x | 
| blockY | int | block position y | 
| blockZ | int | block position z | 
| blockName | str | block identifier, including namespace and name | 
| cancel | bool | True can be returned to the engine by the script layer to prevent subsequent original logic from being triggered | 

- Return value 

None 

- Notes 
- Not all blocks will trigger this event, you need to configure the trigger switch in json first (for details, refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html">Custom Block JSON Component</a>) 
, the original block needs to be registered through the RegisterOnStandOn interface before it can be triggered 
- If you need to modify motion/cancel, it is strongly recommended to modify it synchronously with the client event to avoid inconsistent client performance, etc. 
- If you want to modify motion at the script level, the return must be a floating point type, for example, you need to assign 0.0 instead of 0 

Declare a function of the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 



### Related interfaces 

<span id="RegisterOnStandOn"></span> 
### RegisterOnStandOn 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Can dynamically register and modify netease:on_stand_on components 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 
| sendPythonEvent | bool | Whether to send Python events, True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Notes 
- Currently, only the netease:on_stand_on component of the original block can be dynamically added and modified 
- (Non-rental server online) Using the server-side interface to register will affect the host client component 
- The original logic of the game will not run the block client OnStandOn related logic. If you use the interface to add a client component to the original block, regardless of whether the python event is sent, the original block will run more client-related logic. 
For example, a block such as a slime block that has certain physical calculations will have a different feel after running the calculation once more on the client. 
- You can call multiple times to modify the value of the original component. To delete a component, please use the UnRegisterOnStandOn interface 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.RegisterOnStandOn("minecraft:redstone_ore", True) 
``` 

<span id="UnRegisterOnStandOn"></span> 
### UnRegisterOnStandOn 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

You can dynamically delete the netease:on_stand_on component 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Notes 
- Currently, only the netease:on_stand_on component of the original block can be dynamically deleted 
- (Non-rental service online) Using the server-side interface to register will affect the host client component 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.UnRegisterOnStandOn("minecraft:redstone_ore") 
``` 
## PistonActionServerEvent 
<span style="display:inline;color:#ff5555">Server</span> 
- Description 

Trigger time: When a piston or sticky piston pushes/retracts to affect nearby blocks 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| cancel | bool | Whether to allow triggering, the default is False, if set to True, it can prevent subsequent events from being triggered | 
| action | str | When pushing = expanding; when retracting = retracting | 
| pistonFacing | int | The direction of the piston, refer to [Facing enumeration](../enumeration value/Facing.md) | 
| pistonMoveFacing | int | The direction of the piston's movement, refer to [Facing enumeration](../enumeration value/Facing.md) | 
| dimensionId | int | The dimension where the piston block is located | 
| pistonX | int | The x coordinate of the piston block | 
| pistonY | int | The y coordinate of the piston block | 
| pistonZ | int | The z coordinate of the piston block | 
| blockList | list[(x,y,z),...] | The coordinates of the blocks that are moved by the piston (x,y,z), all of int type | 
| breakBlockList | list[(x,y,z),...] | The coordinates of the blocks that are destroyed by the piston (x,y,z), all of int type | 
| entityList | list[string,...] | List of IDs of entities that are affected by piston movement and are moved or destroyed | 


- Return value 

None 

## PlayerTryDestroyBlockClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

This event is triggered by the client thread when the player is about to destroy a block. Mainly used for blocks such as beds, flags, and boxes that are rendered based on block entity data. In general, please use ServerPlayerTryDestroyBlockEvent 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| face | int | The facing id of the block being hit, refer to [Facing enumeration](../enumeration value/Facing.md) | 
| blockName | str | Block identifier, including namespace and name | 
| auxData | int | Block additional value | 
| playerId | str | Player ID trying to destroy the block | 
| cancel | bool | The default value is False. Setting it to True at the script level will cancel the destruction of the block. | 

- Return value 

None 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ServerBlockEntityTickEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: The custom block is configured with the netease:block_entity component and tick is set to true. The block is triggered when it is within the player's simulation distance (which can be set when creating a new archive, the default is 4 blocks) or within the tickingarea 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | The name of the block | 
| dimension | int | The dimension of the block | 
| posX | int | The x-coordinate of the block | 
| posY | int | The y-coordinate of the block |

| posZ | int | z coordinate of the block | 

- Return value 

None 

- Notes 
- **The tick event frequency of the block entity is 20 times per second** 
- When this event is triggered, if you are exiting the game, you will not be able to obtain the block entity data that threw this event (GetBlockEntityData function returns None), and you will not be able to operate it. 

## ServerBlockUseEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: When the player right-clicks the new version of the custom block (or adds the MC native game block to listen through the interface AddBlockItemListenForUseEvent), the server throws this event (this event is ticked, so you need to pay attention to efficiency issues). 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player Id | 
| blockName | str | Block identifier, including namespace and name | 
| aux | int | Block additional value | 
| cancel | bool | Set to True to intercept logic that interacts with blocks. | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| dimensionId | int | Dimension id | 

- Return value 

None 

- Notes 
- When using native blocks, such as composters and other blocks with the "use" function, this event will be triggered, while ServerItemUseOnEvent will not be triggered. When you need to obtain the items used when triggered, you can obtain the items in your hand through the item component. The corresponding client events are the same. 
- Some blocks are effective when cancel is set in ServerBlockUseEvent, but some blocks are effective only when cancel is set in ClientBlockUseEvent. If necessary, it is recommended to set cancel in both events to ensure effectiveness. 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

### Related Interfaces 

<span id="AddBlockItemListenForUseEvent"></span> 
### AddBlockItemListenForUseEvent 

method in mod.server.component.blockUseEventWhiteListCompServer.BlockUseEventWhiteListComponentServer


- Description 

Add script layer monitoring of ServerBlockUseEvent event for blockName block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block name, format: namespace:name:auxvalue, where namespace:name:* matches all auxvalue | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockUseEventWhiteList(levelId) 
comp.AddBlockItemListenForUseEvent("minecraft:nether_brick_stairs:2") 
# Note that the format of blockName is namespace:name:auxvalue. If auxvalue is not filled in, it defaults to 0 
# For detailed values of auxValue, please refer to the official wiki, such as 'Block Data Value' in https://minecraft-zh.gamepedia.com/梯 
``` 

<span id="RemoveBlockItemListenForUseEvent"></span> 
### RemoveBlockItemListenForUseEvent 

method in mod.server.component.blockUseEventWhiteListCompServer.BlockUseEventWhiteListComponentServer 

- Description 

Remove the script layer listening of the blockName block to the ServerBlockUseEvent event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block name, format: namespace:name:auxvalue, where namespace:name:* matches all auxvalue | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the removal is successful | 


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockUseEventWhiteList(levelId) 
comp.RemoveBlockItemListenForUseEvent("minecraft:nether_brick_stairs:2") 
# Note that the format of blockName is namespace:name:auxvalue. If auxvalue is not filled in, it defaults to 0 
# For detailed values of auxValue, please refer to the official wiki, such as 'Block Data Value' in https://minecraft-zh.gamepedia.com/Stairs 
``` 

<span id="ClearAllListenForBlockUseEventItems"></span> 
### ClearAllListenForBlockUseEventItems 

method in mod.server.component.blockUseEventWhiteListCompServer.BlockUseEventWhiteListComponentServer 

- Description 

Clear all script-level listeners for ServerBlockUseEvent events for added blocks 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether clearing is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockUseEventWhiteList(levelId) 
comp.ClearAllListenForBlockUseEventItems() 
``` 

## ServerEntityTryPlaceBlockEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: This event is triggered when a creature tries to place a block. 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| fullName | str | Block identifier, including namespace and name | 
| auxData | int | Block additional value | 
| entityId | str | The ID of the creature trying to place the block | 
| dimensionId | int | Dimension id | 
| face | int | Click on the face of the block, refer to [Facing enumeration](../enumeration value/Facing.md) | 
| cancel | bool | Defaults to False, set to True at the script level to cancel the placement of the block | 

- Return value 

None 

- Notes 
- Some blocks that will generate entities, operable blocks, or blocks with special logic after being placed will not trigger this event, including but not limited to beds, doors, signs, flower pots, redstone repeaters, boats, cauldrons, head models, cakes, brewing stands, armor stands, etc. 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ServerPlaceBlockEntityEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: Triggered when a block with a custom block entity is placed manually or created through the interface. At this time, data can be stored in the block entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | The name of the block | 
| dimension | int | The dimension where the block is located | 
| posX | int | The x coordinate of the block | 
| posY | int | The y coordinate of the block | 
| posZ | int | The z coordinate of the block | 

- Return value 

None 

## ServerPlayerTryDestroyBlockEvent 

<span style="display:inline;color:#ff5555">Server</span>


- Description 

When the player is about to destroy a block, the server thread triggers this event. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| face | int | The face id of the block being hit, refer to [Facing enumeration](../enumeration value/Facing.md) | 
| fullName | str | Block identifier, including namespace and name | 
| auxData | int | Block additional value | 
| playerId | str | ID of the player trying to destroy the block | 
| dimensionId | int | Dimension id | 
| cancel | bool | Defaults to False, set to True at the script level to cancel the destruction of the block | 
| spawnResources | bool | Whether to generate drops, the default is True, set to False at the script level to cancel the generation of drops | 

- Return value 

None 

- Notes 
- If you need to prohibit the destruction of some special blocks, you need to use it with PlayerTryDestroyBlockClientEvent, such as beds, flags, boxes, and other blocks that are rendered according to block entity data 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ShearsDestoryBlockBeforeClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger timing: When the player holds a scissors to destroy a block, the block with the scissors special effect will trigger this event in the client thread 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockX | int | Block position x | 
| blockY | int | Block position y | 
| blockZ | int | Block position z | 
| blockName | str | Block identifier, including namespace and name | 
| auxData | int | Block additional value | 
| dropName | str | Drop identifier that triggers the scissors effect, including namespace and name | 
| dropCount | int | Number of drops that trigger the scissors effect | 
| playerId | str | Player id that triggers the scissors effect |

| dimensionId | int | Dimension id when the player triggers | 
| cancelShears | bool | Whether to cancel the shears effect | 

- Return value 

None 

- Notes 
- Currently only the tripwire will trigger. If you need to cancel the shears effect, you must use it together with ShearsDestoryBlockBeforeServerEvent 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ShearsDestoryBlockBeforeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: When the player holds a scissors to destroy a block, the block with the scissors special effect will trigger this event in the server thread 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockX | int | Block position x | 
| blockY | int | Block position y | 
| blockZ | int | Block position z | 
| blockName | str | Block identifier, including namespace and name | 
| auxData | int | Block additional value | 
| dropName | str | Identifier of the drop that triggers the shears effect, including namespace and name | 
| dropCount | int | Number of drops that trigger the shears effect | 
| playerId | str | Player id that triggers the shears effect | 
| dimensionId | int | Dimension id when the player triggers | 
| cancelShears | bool | Whether to cancel the shears effect | 

- Return value 

None 

- Notes 
- This event is triggered after ServerPlayerTryDestroyBlockEvent. If you set the cancellation of Destory or cancellation of dropped objects in the ServerPlayerTryDestroyBlockEvent event, this event will not be triggered. 
- Block types that do not drop anything after canceling the scissors effect: spider webs, withered bushes, grass, nether seedlings, leaves, seaweed, vines 
- The tripwire needs to be used with ShearsDestoryBlockBeforeClientEvent to cancel the scissors effect, otherwise the performance may still show the effect of scissors cutting. The tripwire will still fall into a line after canceling the scissors effect. 

Directly declare a function of the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## StartDestroyBlockClientEvent 


<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the player starts to dig a block. Not triggered in creative mode. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Coordinates of the block | 
| blockName | str | Block identifier, including namespace and name | 
| auxValue | int | Additional value of the block | 
| playerId | str | Player id | 
| cancel | bool | When modified to True, it can prevent the player from entering the state of digging blocks. Need to be modified together with StartDestroyBlockServerEvent. | 

- Return value 

None 

- Notes 
- If you are digging a block across a flame, the flame will be extinguished even if you cancel the event. If you want to prevent the flame from being extinguished, you need to use ExtinguishFireClientEvent 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## StartDestroyBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the player starts digging a block. Not triggered in creative mode. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Coordinates of the block | 
| blockName | str | Block identifier, including namespace and name | 
| auxValue | int | Additional value of the block | 
| playerId | str | Player id | 
| dimensionId | int | Dimension id | 
| cancel | bool | When modified to True, it can prevent the player from entering the state of digging blocks. Need to be modified together with StartDestroyBlockClientEvent. | 

- Return value 

None 

- Notes

- If you dig a block across a flame, the flame will be extinguished even if you cancel the event. If you want to prevent the flame from being extinguished, you need to use ExtinguishFireServerEvent 

Declare a function with the same name in the part directly to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## StepOffBlockClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger timing: Triggered when the entity moves away from a solid block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockX | int | Block x coordinate | 
| blockY | int | Block y coordinate | 
| blockZ | int | Block z coordinate | 
| entityId | str | Triggering entity's unique ID | 
| blockName | str | Block identifier, including namespace and name | 
| dimensionId | int | Dimension id | 

- Return value 

None 

- Notes 
- Not all blocks will trigger this event. Custom blocks need to configure the trigger switch in json first (for details, refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html">Custom Block JSON Component</a>), 
The original blocks need to be registered through the RegisterOnStepOff interface before they can be triggered 
- Non-solid blocks such as pressure plates and tripwire hooks will not be triggered 

Directly declare a function with the same name in the parts to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

### Related Interfaces 

<span id="RegisterOnStepOff"></span> 

### RegisterOnStepOff 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Can dynamically register and modify netease:on_step_off components 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 
| sendPythonEvent | bool | Whether to send Python events, True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Notes 
- Currently only the netease:on_step_off component of the original block can be dynamically added and modified 
- The value of the original component can be modified multiple times. To delete the component, please use the UnRegisterOnStepOff interface 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.RegisterOnStepOff("minecraft:redstone_ore", True) 
``` 

<span id="UnRegisterOnStepOff"></span> 
### UnRegisterOnStepOff 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Can dynamically delete netease:on_step_off component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Notes 
- Currently, only the netease:on_step_off component of the original block can be dynamically deleted 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.UnRegisterOnStepOff("minecraft:redstone_ore") 
``` 

## StepOffBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger: When an entity moves away from a solid block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockX | int | Block x coordinate | 
| blockY | int | Block y coordinate | 
| blockZ | int | Block z coordinate | 
| entityId | str | The unique ID of the entity that triggers | 
| blockName | str | The identifier of the block, including the namespace and name | 
| dimensionId | int | Dimension id | 

- Return value 

None 

- Notes 
- Not all blocks will trigger this event. Custom blocks need to configure the trigger switch in json first (for details, refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html">Custom Block JSON Component</a>), 
The original blocks need to be registered through the RegisterOnStepOff interface before they can be triggered 
- Non-solid blocks such as pressure plates and tripwire hooks will not be triggered 

Directly declare a function with the same name in the parts to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

### Related Interfaces 

<span id="RegisterOnStepOff"></span> 
### RegisterOnStepOff 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Can dynamically register and modify netease:on_step_off components 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 
| sendPythonEvent | bool | Whether to send Python events, True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Notes 
- Currently, only the netease:on_step_off component of the original block can be dynamically added and modified 
- (Non-rental service online) Using the server-side interface to register will affect the host client component 
- You can call multiple times to modify the value of the original component. To delete the component, please use the UnRegisterOnStepOff interface 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.RegisterOnStepOff("minecraft:redstone_ore", True) 
``` 

<span id="UnRegisterOnStepOff"></span> 
### UnRegisterOnStepOff 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Can dynamically delete netease:on_step_off component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Notes

- Currently only the netease:on_step_off component of the original block can be dynamically deleted 
- (Non-rental server online) Using the server-side interface registration will affect the host client component 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.UnRegisterOnStepOff("minecraft:redstone_ore") 
``` 

## StepOnBlockClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger time: Triggered when the entity just moves to a new solid block. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| cancel | bool | Whether to allow triggering, default is False, if set to True, it can prevent the subsequent original logic from being triggered | 
| blockX | int | Block x coordinate | 
| blockY | int | Block y coordinate | 
| blockZ | int | Block z coordinate | 
| entityId | str | Unique ID of the triggered entity | 
| blockName | str | Block identifier, including namespace and name | 
| dimensionId | int | Dimension id | 

- Return value 

None 

- Notes 
- After merging the Microsoft update, the triggering timing of this event is consistent with the Microsoft molang experimental gameplay component "minecraft:on_step_on" 
- The events of pressure plates and tripwire hooks can be triggered in the past versions, but after the update, these non-solid blocks will not be triggered. If necessary, you can use the OnEntityInsideBlockClientEvent event. 
- Not all blocks will trigger this event. Custom blocks need to configure the trigger switch in json first (for details, refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Components.html">Custom Block JSON Components</a>), 
The original blocks need to be registered through the RegisterOnStepOn interface before they can be triggered. The original redstone mine is registered by default, but the deep redstone mine is not registered by default. 
- If you need to modify the cancel, it is strongly recommended to modify it synchronously with the server event to avoid unexpected phenomena such as correction by the server. 

Simply declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

### Related Interfaces 

<span id="RegisterOnStepOn"></span>

### RegisterOnStepOn 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Can dynamically register and modify netease:on_step_on components 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 
| sendPythonEvent | bool | Whether to send Python events, True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Notes 
- Currently, only netease:on_step_on components of the original blocks can be dynamically added and modified 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.RegisterOnStepOn("minecraft:redstone_ore", True) 
``` 

<span id="UnRegisterOnStepOn"></span> 
### UnRegisterOnStepOn 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

You can dynamically delete the netease:on_step_on component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Notes 
- Currently, only the netease:on_step_on component of the original block can be dynamically deleted 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.UnRegisterOnStepOn("minecraft:redstone_ore") 
``` 

## StepOnBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: Triggered when the entity just moves to a new solid block. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| cancel | bool | Whether to allow triggering, the default is False, if set to True, subsequent physical interaction events can be prevented from being triggered | 
| blockX | int | Block x coordinate | 
| blockY | int | Block y coordinate | 
| blockZ | int | Block z coordinate | 
| entityId | str | Unique ID of the entity that triggered | 
| blockName | str | Block identifier, including namespace and name | 
| dimensionId | int | Dimension id | 

- Return value 

None 

- Notes 
- After merging the Microsoft update, the triggering timing of this event is consistent with the Microsoft molang experimental gameplay component "minecraft:on_step_on" 
- The events of pressure plates and tripwire hooks can be triggered in previous versions, but after the update, these non-solid blocks will not be triggered. If necessary, you can use the OnEntityInsideBlockServerEvent event. 
- Not all blocks will trigger this event. Custom blocks need to configure the trigger switch in json first (for details, please refer to: <a href="../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Components.html">Custom Block JSON Components</a>), 
The original blocks need to be registered through the RegisterOnStepOn interface before they can be triggered. The original redstone mine is registered by default, but the deep redstone mine is not registered by default. 
- If you need to modify cancel, it is strongly recommended to modify it synchronously with the client event to avoid unexpected phenomena such as inconsistent client performance. 

Simply declare a function with the same name in the part to complete the monitoring. For details, please refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a>



### Related interfaces 

<span id="RegisterOnStepOn"></span> 
### RegisterOnStepOn 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Can dynamically register and modify netease:on_step_on components 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 
| sendPythonEvent | bool | Whether to send Python events, True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Notes 
- Currently, only the netease:on_step_on component of the original block can be dynamically added and modified. 
- (Non-rental server online) Using the server-side interface to register will affect the host client component 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.RegisterOnStepOn("minecraft:redstone_ore", True) 
``` 

<span id="UnRegisterOnStepOn"></span> 
### UnRegisterOnStepOn 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

The netease:on_step_on component can be dynamically deleted 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, including namespace, such as minecraft:grass | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Notes 
- Currently, only the netease:on_step_on component of the original block can be dynamically deleted 
- (Non-rental service online) Using the server-side interface to register will affect the host client component 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId)
comp.UnRegisterOnStepOn("minecraft:redstone_ore")
```