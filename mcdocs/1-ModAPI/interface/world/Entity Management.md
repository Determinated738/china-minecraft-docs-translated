--- 
sidebarDepth: 1 
--- 
# Entity Management 

## CreateEngineEntityByTypeStr 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.system.serverSystem.ServerSystem 

- Description 

Create an entity with the specified identifier 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| engineTypeStr | str | Entity identifier, e.g. 'minecraft:husk' | 
| pos | tuple(float,float,float) | Coordinates to generate | 
| rot | tuple(float,float) | Mob orientation | 
| dimensionId | int | The generated dimension, the default value is 0 (0 is the main world, 1 is the underworld, 2 is the end of the world) | 
| isNpc | bool | Whether it is an NPC, the default value is False. NPCs will not move, turn, or save. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str or None | Entity ID or None | 

- Notes 
- Cannot create in unloaded chunks 
Please use "minecraft:villager_v2" to generate villagers 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class MyServerSystem(ServerSystem): 
def createMob(self): 
# Create a husk facing (0, 0) at the position (0, 5, 0) of the main world 
entityId = self.CreateEngineEntityByTypeStr('minecraft:husk', (0, 5, 0), (0, 0), 0) 
``` 

## CreateEngineItemEntity 


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.system.serverSystem.ServerSystem 

- Description 

Used to create item entities (i.e. drops) and return the entityId of the item entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| dimensionId | int | Set dimension, default is main world | 
| pos | tuple(float,float,float) | Generate coordinates | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str or None | Entity Id or None | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
itemDict = { 
'itemName': 'minecraft:bow', 
'count': 1, 
'enchantData': [(serverApi.GetMinecraftEnum().EnchantType.BowDamage, 1),], 
'auxValue': 0, 
'customTips':'§c new item §r', 
'extraId': 'abc', 
'userData': { 'color': { '__type__':8, '__value__':'gray'} }, 
} 
itemEntityId = self.CreateEngineItemEntity(itemDict, 0, (0, 5, 0)) 
``` 

## CreateExperienceOrb 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.expCompServer.ExpComponentServer 

- Description 

Create a dedicated experience orb 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| exp | int | Experience ball experience | 
| position | tuple(float,float,float) | Creation position | 
| isSpecial | bool | Whether it is a special experience ball | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Set the experience ball experience, entityId is the entityId of the person. Only the person with entityId can pick up the exclusive experience ball 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExp(entityId) 
comp.CreateExperienceOrb(25,(10,10,10),False) 
``` 

## CreateProjectileEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.projectileCompServer.ProjectileComponentServer 

- Description 

Create a projectile (direct launch) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| spawnerId | str | Creator Id | 
| entityIdentifier | str | The identifier of the created projectile, such as minecraft:snowball | 
| param | dict | The default is None, see the notes for detailed description | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | The Id of the created projectile, "-1" if failed |


- Notes 
- The param parameter is explained as follows: 
| Parameter | Type | Explanation | 
| ----------------- | ----- | ------------------------------------------------------------ | 
| position | tuple(float,float,float) | Initial position | 
| direction | tuple(float,float,float) | Initial direction | 
| power | float | Throwing power value | 
| gravity | float | Projectile gravity factor, defaults to the value in the json configuration | 
| damage | float | Projectile damage value, defaults to the value in the json configuration | 
| targetId | str | Projectile target (after specifying the target, it will have the same effect as the projectile of the tracking missile launched by the shulker creature), not specified by default | 
| isDamageOwner | bool | Whether to cause damage to the creator, no damage by default | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateProjectile(levelId) 
param = { 
'position': (1,1,1), 
'direction': (1,1,1) 
} 
comp.CreateProjectileEntity(playerId, "minecraft:snowball", param) 
``` 

## DestroyEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.system.serverSystem.ServerSystem 

- Description 

Destroy entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Destroyed entity ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the destruction is successful | 

- Example


```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def testDestroyEntity(self, entityId): 
self.DestroyEntity(entityId) 
``` 

## GetDroppedItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the item information of the dropped item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemEntityId | str | entityId of the dropped item | 
| getUserData | bool | Whether to get userData, the default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Information | 

- Notes 
- If the dropped object entity does not exist, the return value is None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(levelId) 
comp.GetDroppedItem(entityId) 
``` 

## GetEngineActor 

<span style="display:inline;color:#ff5555">Server</span>


method in mod.server.extraServerApi 

- Description 

Get all entities (excluding players). 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | All entity information in the current map, key: entity id, value: entity dict | 

- Notes 
- Entity information dictionary entityDict 
| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| dimensionId | int | Dimension id | 
| identifier | str | Entity identifier | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
entityDicts = serverApi.GetEngineActor() 
``` 

## GetLocalPlayerId 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Get the local player's id 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| str | Client player ID | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
localId = clientApi.GetLocalPlayerId() 
``` 

## GetPlayerList 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.extraServerApi 

- Description 

Get a list of all player IDs in a level 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Returns a list of player IDs | 

- Notes 
- Since the player IDs in the engine are stored in an unordered manner, the order of the list returned by this interface has no practical significance, and is only for consistent performance on multiple platforms. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
print serverApi.GetPlayerList() 
``` 

## HasEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.gameCompClient.GameComponentClient 


- Description 

Check if entity exists 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | 0 means does not exist, 1 means exists | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
exist = comp.HasEntity(entityId) 
``` 

## IsEntityAlive 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Determine whether a biological entity is alive or a non-biological entity exists 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| entityId | str | Entity ID | 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| bool | false means that the biological entity has died or the non-biological entity has been destroyed, true means that the biological entity is alive or the non-biological entity exists |


- Notes 
- Note that if the chunk where the detected entity is located is unloaded, this interface returns False. Therefore, it is necessary to pay attention to whether the chunk where the entity is located is loaded. 
- Chunk unloading: The game will only load the chunks around the player. When the player moves to another area, the chunks in the original area will be unloaded. Refer to [Block Introduction](https://minecraft-zh.gamepedia.com/%E5%8C%BA%E5%9D%97) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
alive = comp.IsEntityAlive(entityId) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Determine whether a biological entity is alive or a non-biological entity exists 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | false means that the biological entity has died or the non-biological entity has been destroyed, true means that the biological entity is alive or the non-biological entity exists | 

- Notes 
- Note that if the block where the detected entity is located is unloaded, the interface returns False. Therefore, it is necessary to pay attention to whether the block where the entity is located is loaded. 
- Chunk unloading: The game will only load the chunks around the player. When the player moves to another area, the chunks in the original area will be unloaded. Please refer to [Block Introduction](https://minecraft-zh.gamepedia.com/%E5%8C%BA%E5%9D%97) 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
alive = comp.IsEntityAlive(entityId) 
``` 



## KillEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Kill an Entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str | EntityId of the target to be killed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the killing was successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.KillEntity(entityId) 
``` 
## SpawnItemToLevel 
<span style="display:inline;color:#ff5555">Server</span> 
method in mod.server.component.itemCompServer.ItemCompServer 
- Description 
Generates item drops. If you need to get the entityId of the item, you can call the server system interface CreateEngineItemEntity 
- Parameters 
| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| dimensionId | int | Set dimension | 
| pos | tuple(float,float,float) | Generation position | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
itemDict = { 
'itemName': 'minecraft:bow', 
'count': 1, 
'enchantData': [(serverApi.GetMinecraftEnum().EnchantType.BowDamage, 1),], 
'auxValue': 0, 
'customTips':'§c new item §r', 
'extraId': 'abc', 
'userData': {}, 
} 
comp = serverApi.GetEngineCompFactory().CreateItem(levelId) 
comp.SpawnItemToLevel(itemDict, 0, (0,80,20)) 
# When the maximum number of items to be generated is 1, you can continue to call to generate 2 items 
comp.SpawnItemToLevel(itemDict, 0, (0,80,20)) 
``` 

## SpawnLootTable 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorLootCompServer.ActorLootComponentServer 

- Description 

Use the creature type to simulate a random drop. The generated items are related to the probability defined in json 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Drop position | 
| identifier | str | Entity identifier, such as minecraft:guardian | 
| playerKillerId | str | Player killer (can only be a player), default is None | 
| damageCauseEntityId | str | Damage source entity ID (the drop is related to the looting enchantment level of the item held by the entity), default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the drop was generated successfully | 

- Notes 
- Need to be generated near the corresponding player entity, otherwise the generation will fail. For some special creatures, such as minecraft:sheep, you need to use the SpawnLootTableWithActor interface to simulate random drops. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateActorLoot(playerId) 
result = comp.SpawnLootTable((1, 4, 5), 'minecraft:guardian') 
``` 

## SpawnLootTableWithActor 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.actorLootCompServer.ActorLootComponentServer 

- Description 

Use a creature instance to simulate a random drop. The generated items are related to the probability defined in json 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Drop location | 
| entityId | str | Mob ID of simulated mob | 
| playerKillerId | str | Player killer (can only be a player), default is None | 
| damageCauseEntityId | str | Damage source entity ID (drop is related to the looting enchantment level of the item held by the entity), default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the drop was generated successfully | 

- Notes 
- Need to be generated near the corresponding player entity, otherwise the generation will fail 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateActorLoot(playerId) 
result = comp.SpawnLootTableWithActor((1, 4, 5), '-335007449086')
```




## SpawnResources 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Generate random blocks (this method does not apply to entity blocks) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| identifier | str | Block identifier, such as minecraft:wool | 
| pos | tuple(int,int,int) | Drop position | 
| aux | int | Block bonus | 
| probability | float | Drop probability, range is [0, 1], 0 means no drop, 1 means 100% drop | 
| bonusLootLevel | int | [Lucky Level](https://minecraft-zh.gamepedia.com/时运), default is 0 | 
| dimensionId | int | Dimension of dropped blocks, default is -1, when non-negative value is passed, it is used to obtain the dimension where the block is dropped; otherwise, a dimension with players will be randomly selected to drop | 
| allowRandomness | bool | Whether to allow random collection, default is True, if False, the drop probability probability is invalid | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- Lucky level [bonusLootLevel] is only effective for some blocks 
Drop probability [probability] is not effective for some crops and leaves 
- Drops can be generated in the constant loading block of the corresponding dimension 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Gold ore drops 
result = comp.SpawnResources('minecraft:gold_ore', (1,1,1), 7, 1.0, 10) 
# Specified dimension produces drops 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
result = comp.SpawnResources('minecraft:gold_ore', (1,1,1), 7, 1.0, 10, 0) 
``` 



## SpawnResourcesSilkTouched 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Simulates precise capture of blocks 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| identifier | str | Block identifier, such as minecraft:wool | 
| pos | tuple(int,int,int) | Drop position | 
| aux | int | Block additional value | 
| dimensionId | int | Dimension of dropped block, default value is -1, when non-negative value is passed in, it is used to obtain the dimension where the block is dropped; otherwise, a dimension where a player exists will be randomly selected for drop | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- If the specified block is not a Silk Touch block, return False 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
result = comp.SpawnResourcesSilkTouched('minecraft:gold_ore', (1,1,1), 7) 
``` 

