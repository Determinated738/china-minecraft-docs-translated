--- 
sidebarDepth: 1 
--- 
# World 

# Index 

| Events | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AchievementCompleteEvent](世界.md#achievementcompleteevent) | <span style="display:inline;color:#ff5555">Server</span> | This event is triggered when a player completes a custom achievement | 
| [AddEntityClientEvent](世界.md#addentityclientevent) | <span style="display:inline;color:#7575f9">Client</span> | This event is triggered when a new entity is created on the client side | 
| [AddEntityServerEvent](世界.md#addentityserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when a new entity is created on the server side or when an entity is loaded from a save file | 
| [AddPlayerAOIClientEvent](世界.md#addplayeraoiclientevent) | <span style="display:inline;color:#7575f9">Client</span> | AOI event triggered when a player joins the game or other players enter the block where the current player is located, replacing AddPlayerEvent | 
| [AddPlayerCreatedClientEvent](世界.md#addplayercreatedclientevent) | <span style="display:inline;color:#7575f9">Client</span> | After a player enters the block AOI where the current player is located, the event is triggered after the player skin data is asynchronously loaded | 
| [AddServerPlayerEvent](世界.md#addserverplayerevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: Trigger this event when a player joins. | 
| [ChunkAcquireDiscardedClientEvent](世界.md#chunkacquirediscardedclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Trigger time: When the client chunk is about to be unloaded | 
| [ChunkAcquireDiscardedServerEvent](世界.md#chunkacquirediscardedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger when the server chunk is about to be unloaded | 
| [ChunkGeneratedServerEvent](世界.md#chunkgeneratedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: When the chunk is created | 
| [ChunkLoadedClientEvent](世界.md#chunkloadedclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Trigger time: When the client chunk is loaded | 
| [ChunkLoadedServerEvent](世界.md#chunkloadedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: When the server chunk is loaded | 
| [ClientLoadAddonsFinishServerEvent](世界.md#clientloadaddonsfinishserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: When the client mod is loaded, the server triggers this event. The server can use this event to send data to the client to initialize it. | 
| [CommandEvent](世界.md#commandevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired when a player requests to execute a command | 
| [DelServerPlayerEvent](世界.md#delserverplayerevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired when: This event is fired when a player is deleted. | 
| [EntityRemoveEvent](世界.md#entityremoveevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired when an entity is deleted | 
| [ExplosionServerEvent](世界.md#explosionserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired when an explosion occurs. | 
| [LoadClientAddonScriptsAfter](世界.md#loadclientaddonscriptsafter) | <span style="display:inline;color:#7575f9">Client</span> | Client mod loading complete event | 
| [LoadServerAddonScriptsAfter](世界.md#loadserveraddonscriptsafter) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the server finishes loading the mod | 
| [NewOnEntityAreaEvent](世界.md#newonentityareaevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger timing: After registering the AOI event through RegisterEntityAOIEvent, this event is triggered when an entity enters or leaves the registered sensing area. | 
| [OnCommandOutputClientEvent](世界.md#oncommandoutputclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when command outputs a success message | 
| [OnCommandOutputServerEvent](世界.md#oncommandoutputserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Command execution success event | 
| [OnContainerFillLoottableServerEvent](世界.md#oncontainerfillloottableserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: when a random reward box is opened for the first time and an item is generated based on loottable | 
| [OnLightningLevelChangeServerEvent](世界.md#onlightninglevelchangeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Lightning intensity changes | 
| [OnLocalLightningLevelChangeServerEvent](世界.md#onlocallightninglevelchangeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the intensity of thunder changes in independent dimension weather | 
| [OnLocalPlayerStopLoading](世界.md#onlocalplayerstoploading) | <span style="display:inline;color:#7575f9">Client</span> | Triggering time: When the player enters the save file and the terrain at the spawn point is loaded. When this event is triggered, you can switch dimensions. | 
| [OnLocalRainLevelChangeServerEvent](世界.md#onlocalrainlevelchangeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the rain intensity of the independent dimension weather changes | 
| [OnRainLevelChangeServerEvent](世界.md#onrainlevelchangeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Rain intensity changes | 
| [OnScriptTickClient](世界.md#onscripttickclient) | <span style="display:inline;color:#7575f9">Client</span> | Client tick event, 30 times per second | 
| [OnScriptTickServer](世界.md#onscripttickserver) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the server ticks, 30 ticks per second | 
| [PlaceNeteaseStructureFeatureEvent](世界.md#placeneteasestructurefeatureevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: When the terrain is first generated, the server throws this event when the structure feature is about to be generated. | 
| [PlayerIntendLeaveServerEvent](世界.md#playerintendleaveserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: This event is triggered when the player is about to be deleted. At this time, the current status of the player can be obtained through various APIs. | 
| [PlayerJoinMessageEvent](世界.md#playerjoinmessageevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: The server throws the event when the player login prompt text "xxx joins the game" is about to be displayed. | 
| [PlayerLeftMessageServerEvent](世界.md#playerleftmessageserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: The server throws the event when the player leaves the prompt text "xxx leaves the game" is about to be displayed. | 
| [RemoveEntityClientEvent](世界.md#removeentityclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when the client-side entity is removed | 
| [RemovePlayerAOIClientEvent](世界.md#removeplayeraoiclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when the player leaves the same block as the current player | 
| [ServerChatEvent](世界.md#serverchatevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the player sends a chat message | 
| [ServerPostBlockPatternEvent](世界.md#serverpostblockpatternevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger timing: Generate a creature by combining blocks. This event is triggered after the creature is generated. | 
| [ServerPreBlockPatternEvent](世界.md#serverpreblockpatternevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger timing: Generate a creature by combining blocks. This event is triggered when the last block is placed. | 
| [ServerSpawnMobEvent](世界.md#serverspawnmobevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when creatures are automatically generated in the game, and when creatures are generated using the API | 
| [UnLoadClientAddonScriptsBefore](世界.md#unloadclientaddonscriptsbefore) | <span style="display:inline;color:#7575f9">Client</span> | Triggered before the client uninstalls the mod | 
# World


## AchievementCompleteEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

This event is triggered when the player completes a custom achievement 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
| rootNodeId | str | Root node achievement id of the page to which it belongs | 
| achievementId | str | Achievement id | 
| title | str | Achievement title | 
| description | str | Achievement description | 

- Return value 

None 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## AddEntityClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when a new entity is created on the client side 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 
| posX | float | Position x | 
| posY | float | Position y | 
| posZ | float | Position z | 
| dimensionId | int | Entity dimension | 
| isBaby | bool | Is it a baby | 
| engineTypeStr | str | entity type | 
| itemName | str | item identifier (this field only exists if it is an item entity) | 
| auxValue | int | item additional value (this field only exists if it is an item entity) | 

- return value 


None 

- Notes 
- This event will not be triggered when creating a player 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## AddEntityServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when a new entity is created on the server side or the entity is loaded from the archive 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 
| posX | float | Position x | 
| posY | float | Position y | 
| posZ | float | Position z | 
| dimensionId | int | Entity dimension | 
| isBaby | bool | Is it a baby? | 
| engineTypeStr | str | Entity type, that is, entity identifier | 
| itemName | str | Item identifier (this field only exists when the item is an entity) | 
| auxValue | int | Item additional value (this field only exists when the item is an entity) | 

- Return value 

None 

- Remarks 
- This event will not be triggered when creating a player 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## AddPlayerAOIClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

AOI event triggered when a player joins the game or other players enter the block where the current player is located, replacing AddPlayerEvent 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 

- Return value 

None 

- Notes 
- This event trigger only indicates that a new player has been received in the server data, and does not mean that the player is visible in the client at this time. If you want to call the player rendering related interface immediately after the player enters the AOI, it is recommended to use [AddPlayerCreatedClientEvent](#addplayercreatedclientevent). 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## AddPlayerCreatedClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

After the player enters the block AOI where the current player is located, the event is triggered after the player's skin data is asynchronously loaded 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 

- Return value 

None 

- Remarks 
- Because the player skin is loaded asynchronously, this event is triggered later than [AddPlayerAOIClientEvent](#addplayeraoiclientevent). After triggering this event, the relevant [Player Rendering Interface](../Interface/Player/Rendering.md) can be called for the player. 
- This event will be triggered once each time a player's skin is loaded on the current client. For example, when entering the world, it will be triggered once when the localPlayer is loaded, and once when all the surrounding players are loaded. 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## AddServerPlayerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: Trigger this event when a player joins. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| id | str | Player id | 
| isTransfer | bool | Whether to enter the server when switching servers, only for Apollo. If True, it means joining the server when switching servers, if False, it means logging in to the online game | 
| isReconnect | bool | Whether it is disconnected and reconnected, only for Apollo. If True, it means that this login is disconnected and reconnected, if False, it means that this is a normal login or transfer | 
| isPeUser | bool | Whether to log in from the mobile terminal, only for Apollo. If True, it means that this login is from the mobile terminal, if False, it means that this login is from the PC terminal | 
| transferParam | str | Parameters passed in when switching servers, only for Apollo. The server switching parameters passed in by calling [TransferToOtherServer] or [TransferToOtherServerById] | 
| uid | int/long | Only used for Apollo, the player's netease uid, the player's unique identifier | 
| proxyId | int | Only used for Apollo, the proxy server id of the current client connection | 

- Return value 

None 

- Notes 
- When this event is triggered, the client mod has not been loaded, so the client cannot send events when responding to this event. If you need the server to send events to the client when the player enters the world, please use ClientLoadAddonsFinishServerEvent 
- When this event is triggered, the player's entity has not been loaded yet, so please do not switch dimensions at this time. Please listen to the OnLocalPlayerStopLoading event on the client and send the event to the server before switching dimensions. 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ChunkAcquireDiscardedClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger time: when the client block is about to be unloaded 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension of the block | 
| chunkPosX | int | The x coordinate of the block, the corresponding block x coordinate interval is [x * 16, x * 16 + 15] | 
| chunkPosZ | int | The z coordinate of the chunk, the corresponding chunk z coordinate range is [z * 16, z * 16 + 15] | 

- Return value 

None 

- Notes 
- Chunk unloading: The game will only load chunks around the player. When the player moves to another area, the chunks in the original area will be unloaded. Refer to [Block Introduction](https://minecraft-zh.gamepedia.com/%E5%8C%BA%E5%9D%97) 

## ChunkAcquireDiscardedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description


Triggered when the server-side chunk is about to be unloaded 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension of the chunk | 
| chunkPosX | int | The x coordinate of the chunk, corresponding to the x coordinate interval of the chunk is [x * 16, x * 16 + 15] | 
| chunkPosZ | int | The z coordinate of the chunk, corresponding to the z coordinate interval of the chunk is [z * 16, z * 16 + 15] | 
| entities | list(str) | List of entity ids removed from the world when the chunk is unloaded. Note that the information of these entities cannot be obtained when the event is triggered, and it is only used for script resource recycling. | 
| blockEntities | list(dict) | A list of the coordinates of custom block entities that are removed from the world when the block is unloaded. The list element dict contains three ints, posX, posY, and posZ, representing the coordinates of the custom block entities. Note that the information of these block entities cannot be obtained when the event is triggered, and is only used for script resource recycling. | 

- Return value 

None 

- Notes 
- Chunk unloading: The game will only load the chunks around the player. When the player moves to another area, the chunks in the original area will be unloaded. Refer to [Chunk Introduction](https://minecraft-zh.gamepedia.com/%E5%8C%BA%E5%9D%97) 

## ChunkGeneratedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: Triggered when the chunk is created 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | The dimension where the chunk is located | 
| blockEntityData | [{"blockName":str,"posX":int,"posY":int,"posZ":int}...]/None | List of custom block entities in this chunk, usually custom blocks generated by custom features. If there is no custom block entity, the value is None | 

- Return value 

None 

## ChunkLoadedClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger time: When the client chunk is loaded


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension of the chunk | 
| chunkPosX | int | The x coordinate of the chunk, the corresponding x coordinate interval of the chunk is [x * 16, x * 16 + 15] | 
| chunkPosZ | int | The z coordinate of the chunk, the corresponding z coordinate interval of the chunk is [z * 16, z * 16 + 15] | 

- Return value 

None 

## ChunkLoadedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: When the chunk is loaded on the server 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension of the chunk | 
| chunkPosX | int | The x coordinate of the chunk, the corresponding x coordinate interval of the chunk is [x * 16, x * 16 + 15] | 
| chunkPosZ | int | The z coordinate of the chunk, the corresponding z coordinate interval of the chunk is [z * 16, z * 16 + 15] | 

- Return value 

None 

## ClientLoadAddonsFinishServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: The server triggers this event when the client mod is loaded. The server can use this event to send data to the client to initialize it. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id |


- Return value 

None 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## CommandEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the player requests to execute a command 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Player ID | 
| command | str | Command string | 
| cancel | bool | Cancel | 

- Return value 

None 

- Remarks 
- This event is a Hook triggered when the player requests to execute a command. This event does not respond to the command of the command block and the command called by modSDK. To block the player's command, just set cancel to True 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## DelServerPlayerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: Trigger this event when deleting a player. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Player id | 
| isTransfer | bool | Whether to exit the server when switching servers, only used for Apollo. If True, it means exiting the server when switching servers; if False, it means exiting the online game | 
| uid | int/long | Player's netease uid, the player's unique identifier | 


- Return value 

None 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## EntityRemoveEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the entity is deleted 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 

- Return value 

None 

- Remarks 
- Triggering scenario: Entity is deleted from the scene, for example: mob death, mob is [cleared](https://minecraft.fandom.com/zh/wiki/%E7%94%9F%E6%88%90#.E6.B8.85.E9.99.A4), player quits the game, boat/armor stand is destroyed, dropped items/experience balls are picked up or cleared 
- When the mob is unloaded with the chunk, this event will not be triggered, but the ChunkAcquireDiscardedServerEvent event will be triggered instead 
- Regarding the clearing of mobs: When the mob is greater than the distance from the player as stated in the wiki and is still within the player's simulation distance, it will be cleared. That is to say, if the player teleports to a distant place, the creatures at the original place will leave the simulation distance immediately and will not be cleared. 
- When the player exits the game, EntityRemoveEvent and DelServerPlayerEvent are triggered in sequence. 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ExplosionServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when an explosion occurs. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blocks | list[[x,y,z,cancel],...] | The block coordinates (x,y,z) involved in the explosion, cancel is a bool value | 
| victims | list/None | List of injured entity ids. When the explosion creator id is None, victims is also None | 
| sourceId | str/None | Explosion creator id | 
| explodePos | list | Explosion position [x,y,z] |

| dimensionId | int | dimension id | 

- Return value 

None 

- Notes 
- The explosion of the block can be canceled by setting the bool value of cancel in blocks to True, for example (x,y,z,True) 
- In some cases, the explosion creator id is None, and the injured entity id list is also None, such as the explosion caused by a creeper. 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## LoadClientAddonScriptsAfter 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Event when the client loads the mod 

- Parameters 

None 

- Return value 

None 

## LoadServerAddonScriptsAfter 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the server loads the mod 

- Parameters 

None 

- Return value 

None 

## NewOnEntityAreaEvent


<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: After registering the AOI event through RegisterEntityAOIEvent, this event is triggered when an entity enters or leaves the registered sensing area. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Registered sensing area name | 
| enteredEntities | list[str] | List of entity ids that entered the sensing area | 
| leftEntities | list[str] | List of entity ids that left the sensing area | 

- Return value 

None 

- Remarks 
- This event replaces the original OnEntityAreaEvent event 

- Example 

```python 
# ServerSystem 
import mod.server.extraServerApi as serverApi 
self.ListenForEvent(serverApi.GetEngineNamespace(), 
serverApi.GetEngineSystemName(), 
"NewOnEntityAreaEvent", 
self, self.NewOnEntityAreaEvent) 
def NewOnEntityAreaEvent(self, args): 
name = args['name'] 
``` 

### Related interfaces 

<span id="RegisterEntityAOIEvent"></span> 
### RegisterEntityAOIEvent 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Register the sensing area, and there will be message notifications when an entity enters and leaves 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension id | 
| name | str | Registered sensing area name | 
| aabb | tuple(float,float,float,float,float,float) | Coordinate range of the sensing area, in order of minX, minY, minZ, maxX, maxY, maxZ | 
| ignoredEntities | list(str) | Ignored entity id list | 
| entityType | int | Expected response entity type, if not passed, respond to all entity types [EntityType enumeration](../enumeration value/EntityType.md) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Notes 
- After registering the sensing area, you need to listen to the OnEntityAreaEvent or NewOnEntityAreaEvent event to obtain the sensing event 
- Areas with a length or width greater than 2000 grids are not supported. For large areas, it is recommended to obtain entity coordinates at regular intervals in the script to achieve this. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(levelId) 
comp.RegisterEntityAOIEvent(0, "test", (0, 0, 0, 1, 1, 1), None) 
``` 

<span id="UnRegisterEntityAOIEvent"></span> 
### UnRegisterEntityAOIEvent 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Unregister sensor area 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension id | 
| name | str | Name of the sensor area to be unregistered | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(levelId) 
comp.UnRegisterEntityAOIEvent(0, "test") 
``` 

## OnCommandOutputClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when command outputs a success message 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| command | str | Command name | 
| message | str | Message returned by the command | 

- Return value 

None 

- Notes 
- Some commands do not have a command name when they are returned. The command component needs to set the showOutput parameter to True to return. 

## OnCommandOutputServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Command command execution success event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| command | str | Command name | 
| message | str | Message returned by the command | 

- Return value


None 

- Notes 
- Some commands do not have a command name when they are returned. The command component needs to set the showOutput parameter to True to return. 

## OnContainerFillLoottableServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: When the random reward box is opened for the first time to generate items based on loottable 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| loottable | str | JSON path of the loottable read by the reward box | 
| playerId | str | PlayerId of the player who opened the reward box | 
| itemList | list | Dropped item list, each element is an itemDict, the format can be referred to <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| dirty | bool | Default is False. If you need to modify the drop list, set the value to True | 

- Return Value 

None 

- Remarks 
- Only when dirty is True will the item list be re-read and the corresponding drops generated. If you do not need to modify the drop result, do not modify the dirty value at will 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Events">Part Events</a> 

## OnLightningLevelChangeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

The intensity of thunder has changed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| oldLevel | float | Thunder intensity before change | 
| newLevel | float | Thunder intensity after change | 


- Return value 

None 

## OnLocalLightningLevelChangeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the thunder intensity of independent dimension weather changes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| oldLevel | float | Thunder intensity before change | 
| newLevel | float | Thunder intensity after change | 
| dimensionId | int | Independent weather dimension id | 

- Return value 

None 

## OnLocalPlayerStopLoading 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggering time: When the player enters the archive and the terrain at the birth point is loaded, it is triggered. When this event is triggered, the dimension can be switched. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | The id of the player who has completed loading | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnLocalRainLevelChangeServerEvent


<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the rain intensity of the independent dimension weather changes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| oldLevel | float | Rain intensity before change | 
| newLevel | float | Rain intensity after change | 
| dimensionId | int | Independent weather dimension id | 

- Return value 

None 

## OnRainLevelChangeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Rain intensity changes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| oldLevel | float | Rain intensity before change | 
| newLevel | float | Rain intensity after change | 

- Return value 

None 

## OnScriptTickClient 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Client tick event, 30 times per second 


- Parameters 

None 

- Return value 

None 

## OnScriptTickServer 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the server ticks, 30 ticks per second 

- Parameters 

None 

- Return value 

None 

## PlaceNeteaseStructureFeatureEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: When the terrain is generated for the first time, the server throws this event when the structural feature is about to be generated. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| structureName | str | Structure name | 
| x | int | The x coordinate of the smallest block in the structure coordinates | 
| y | int | The y coordinate of the smallest block in the structure coordinates | 
| z | int | The z coordinate of the smallest block in the structure coordinates | 
| biomeType | int | The biome type of the block where the feature is placed | 
| biomeName | str | The biome name of the block where the feature is placed | 
| dimensionId | int | Dimension id | 
| cancel | bool | Set to True to prevent the placement of the structure | 

- Return value


    None 

- Notes 
- **Need to be used with AddNeteaseFeatureWhiteList interface** 
If other mod SDK interfaces are called in this monitoring event, it will not take effect. It is strongly recommended that this event is only used to set whether the structure is placed or not 

### Related interfaces 

<span id="AddNeteaseFeatureWhiteList"></span> 
### AddNeteaseFeatureWhiteList 

method in mod.server.component.featureCompServer.FeatureCompServer 

- Description 

Add the script layer monitoring of the structure to the PlaceNeteaseStructureFeatureEvent event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| structureName | str | Structure identifier | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateFeature(levelId) 
# Note that the structureName format is floderName:structureName 
comp.AddNeteaseFeatureWhiteList("test:pumpkins") 
``` 

<span id="RemoveNeteaseFeatureWhiteList"></span> 
### RemoveNeteaseFeatureWhiteList 

method in mod.server.component.featureCompServer.FeatureCompServer 

- Description 


Remove the script layer listening of structureName to PlaceNeteaseStructureFeatureEvent event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| structureName | str | Structure name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the removal is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateFeature(levelId) 
# Note that the format of structureName is floderName:structureName 
comp.RemoveNeteaseFeatureWhiteList("test:pumpkins") 
``` 

<span id="ClearAllNeteaseFeatureWhiteList"></span> 
### ClearAllNeteaseFeatureWhiteList 

method in mod.server.component.featureCompServer.FeatureCompServer 

- Description 

Clear all script layer listeners of the PlaceNeteaseStructureFeatureEvent event of the added Netease Structure Feature 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether clearing is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateFeature(levelId) 
comp.ClearAllNeteaseFeatureWhiteList()

``` 

## PlayerIntendLeaveServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: This event is triggered when the player is about to be deleted. At this time, the current status of the player can be obtained through various APIs. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 

- Return value 

None 

- Remarks 
- Different from the [DelServerPlayerEvent] event, the current status of the player can be obtained through various APIs at this time. 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerJoinMessageEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: The event thrown by the server when the player login prompt text "xxx joins the game" is ready to be displayed. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Player entity id | 
| name | str | Player nickname | 
| cancel | bool | Whether to display the prompt text, modification is allowed. True: Do not display prompts | 
| message | str | Prompt text for players joining the game, modification is allowed | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a>



## PlayerLeftMessageServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: The event thrown by the server when the player leaves the game and the prompt text "xxx has left the game" is ready to be displayed. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Player entity id | 
| name | str | Player nickname | 
| cancel | bool | Whether to display the prompt text, and allow modification. True: Do not display prompts | 
| message | str | Prompt text for players leaving the game, editable | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Events">Part Events</a> 

## RemoveEntityClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the client-side entity is removed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Removed entity id | 

- Return value 

None 

- Remarks 
- Triggered when the client receives the AOI event from the server, the original event name is RemoveEntityPacketEvent 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 



## RemovePlayerAOIClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

AOI event is triggered when the player leaves the same block as the current player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ServerChatEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when a player sends a chat message 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| username | str | Player name | 
| playerId | str | Player id | 
| message | str | Content of the chat message sent by the player | 
| cancel | bool | Whether to cancel this chat event. If canceled, it can be set to True | 
| bChatById | bool | Whether to send the chat message to a specified online player instead of broadcasting it to all online players. If only sending it to certain players, it can be set to True | 
| bForbid | bool | Whether to ban or not. Only available in apollo. true: banned, the player chat will prompt "You have been banned by the administrator". | 
| toPlayerIds | list(str) | List of player IDs that receive chat messages, effective when bChatById is True | 

- Return value 

None 

- Example 

```python 
# ServerSystem 
import mod.server.extraServerApi as serverApi

from mod_log import logger as logger 
# Listen to engine events: self refers to the instance of ServerSystem class ServerChatEvent is a system event 
self.ListenForEvent(serverApi.GetEngineNamespace(), 
serverApi.GetEngineSystemName(), 
"ServerChatEvent", 
self, self.OnServerChat) 
def OnServerChat(self, args): 
#You can set the style code of username or message. See mc wiki for details. Style code 
args["username"] = "§rl"+args[username]+"§r" 
args["message"] = "test" 
logger.info("ServerChatEvent %s" % args) 
``` 

Directly declare a function with the same name in the component to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Parts Development.html#Parts Event">Parts Event</a> 

## ServerPostBlockPatternEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: Generate creatures with block combinations, and trigger this event after the creatures are generated. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | The id of the generated creature | 
| entityGenerated | str | The name of the generated creature, such as "minecraft:pig" | 
| x | int | Block x coordinate | 
| y | int | Block y coordinate | 
| z | int | Block z coordinate | 
| dimensionId | int | Dimension id | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Events">Part Events</a> 

## ServerPreBlockPatternEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: Use blocks to combine to generate creatures. This event is triggered when the last block is placed. 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| enable | bool | Whether to allow continued generation. If set to False, it will prevent mobs from spawning | 
| x | int | x coordinate of the block | 
| y | int | y coordinate of the block | 
| z | int | z coordinate of the block | 
| dimensionId | int | dimension id | 
| entityWillBeGenerated | str | name of the mob to be spawned, such as "minecraft:pig" | 

- Return value 

None 

## ServerSpawnMobEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when mobs are automatically spawned in the game and when spawning mobs using the API 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | entity id | 
| identifier | str | Namespace of the generated entity | 
| type | int | Type of the generated entity, refer to [EntityType](../Enumeration Value/EntityType.md) | 
| baby | bool | Whether the generated monster is a baby monster | 
| x | float | Generated entity coordinate x | 
| y | float | Generated entity coordinate y | 
| z | float | Generated entity coordinate z | 
| dimensionId | int | Dimension of the generated entity, the default value is 0 (0 is the main world, 1 is the underworld, and 2 is the end of the world) | 
| realIdentifier | str | Namespace of the generated entity. Creatures generated through the MOD API can also get the real namespace in this parameter, not the one starting with custom | 
| cancel | bool | Whether to cancel the generation of this entity | 

- Return value 

None 

- Notes 
- If generated through the MOD API, the identifier namespace is custom. If you need to block the generation of the original creatures, you can set cancel to True when the identifier namespace is not custom. 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 



## UnLoadClientAddonScriptsBefore 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered before the client uninstalls the mod 

- Parameters 

None 

- Return value 

None 

