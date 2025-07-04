--- 
sidebarDepth: 1 
--- 
# Container 

## GetChestBoxSize 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chestContainerCompServer.ChestContainerCompServer 

- Description 

Get the capacity of the box 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | None | This parameter is deprecated | 
| pos | tuple(int,int,int) | Box position | 
| dimensionId | int | The dimension where the box is located. You can get the box capacity in the constant loading block of the corresponding dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Chest size, error value -1 | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChestBlock(levelId) 
comp.GetChestBoxSize(None, (x, y, z), 0) 
``` 

## GetChestPairedPosition 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Get the coordinates of box B that is merged with box A into a large box 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Position coordinates of box A | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(int,int,int) or None | Position coordinates of box B. If the block on the input coordinates of box A is not a box block or is not combined with other box blocks to form a large box, None will be returned | 

- Notes 
- This interface uses the playerId when creating the component to locate the specific dimension, and can only obtain blocks near the player. If the block position is too far away from the player, the correct return information may not be obtained. 

- Example

```python
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId)
pos = (-1, 4, 34)
otherPos = comp.GetChestPairedPosition(pos)
if otherPos:
    print "GetChestPairedPosition success pos=%s otherPos=%s" % (str(pos), str(otherPos))
else:
    print "GetChestPairedPosition failed pos=%s" % (str(pos), )
```



## GetContainerItem

<span style="display:inline;color:#ff5555">Server</span>

method in mod.server.component.itemCompServer.ItemCompServer

- describe

Get items in the container 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Container position | 
| slotPos | int | Container slot | 
| dimensionId | int | Dimension where the block is located | 
| getUserData | bool | Whether to get userData, default is False | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, returns None if there is no item | 

- Notes 
- Specific types of containers include: chests, trapped chests, shulker boxes, hoppers, barrels, droppers, and dispensers 
- This interface does not support ender chests. For the corresponding ender chest interface, please refer to [GetEnderChestItem](#getenderchestitem) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(levelId) 
comp.GetContainerItem((x,y,z), 0, 2) 
``` 

## GetContainerSize 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the container capacity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Box location | 
| dimensionId | int | Dimension of the container | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Box size, error value -1 | 

- Notes 
- This interface does not support ender boxes because the size of ender boxes is fixed to 27. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(levelId) 
comp.GetContainerSize((x, y, z), 0)

``` 

## GetEnderChestItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the items in the ender chest 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str | Player id | 
| slotPos | int | Container slot | 
| getUserData | bool | Whether to get userData, default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, returns None if there is no item | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetEnderChestItem(playerId, 0) 
``` 

## GetInputSlotItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the item in the furnace input bar, support the following parameters to clear a specific slot: itemDict is empty, is {}, Or itemName is minecraft:air, or count is 0 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Container position | 
| dimensionId | int | Dimension of the block | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, returns None if there is no item | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(levelId) 
itemName = comp.GetInputSlotItem((x, y, z), 1) 
``` 

## GetOpenContainerItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the item of the open container 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 
| containerId | int | [Open container Id enumeration](../../enumeration value/OpenContainerId.md) | 
| getUserData | bool | Whether to obtain userData, the default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, if there is no item, return None | 

- Notes 
- You need to listen to the event [CraftItemOutputChangeServerEvent](../../Event/Item.html#CraftItemOutputChangeServerEvent) to get the correct result 
- The open container is a temporary container used to save items during the interaction process, such as anvil input position, grinding wheel input position 

- Example


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetOpenContainerItem(playerId,serverApi.GetMinecraftEnum().OpenContainerId.AnvilInputContainer, True) 
``` 

## GetOutputSlotItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the item in the furnace output slot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Container position | 
| dimensionId | int | The dimension where the block is located | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, returns None if there is no item | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(levelId) 
itemName = comp.GetOutputSlotItem((x, y, z), 1) 
``` 

## GetPlayerUIItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 


Get the item of the synthesis container 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
| slot | int | Container slot, meaning see: [Container type enumeration](../../enumeration value/PlayerUISlot.md) | 
| getUserData | bool | Whether to get userData, default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, returns None if there is no item | 

- Notes 
- Synthesis containers include workbench, anvil, enchantment table, loom, grinding wheel, stonecutter, cartography table, and forging table. 
- All crafting container slots are shared and will not be rearranged according to different containers 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetPlayerUIItem(playerId, slot, True) 
``` 

## SetChestBoxItemExchange 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chestContainerCompServer.ChestContainerCompServer 

- Description 

Exchange the slots of items in the chest 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 
| pos | tuple(int,int,int) | box position | 
| slotPos1 | int | box slot 1 | 
| slotPos2 | int | box slot 2 | 

- return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns True if set successfully, False if failed | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChestBlock(playerId) 
comp.SetChestBoxItemExchange(playerId, (x,y,z), 0, 1) 
``` 

## SetChestBoxItemNum 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chestContainerCompServer.ChestContainerCompServer 

- Description 

Set the number of items in the box slot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | None | This parameter is deprecated | 
| pos | tuple(int,int,int) | Box position | 
| slotPos | int | Box slot | 
| num | int | Number of items | 
| dimensionId | int | The dimension where the block is located. You can set the block in the constant loading block of the corresponding dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChestBlock(levelId)
comp.SetChestBoxItemNum(None, (x,y,z), 0, 10, 0)
```


## SetInputSlotItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the furnace input slot item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| itemDict | dict | Item dictionary information, including three keys: itemName, auxValue, count | 
| pos | tuple(int,int,int) | Container position | 
| dimensionId | int | Dimension where the block is located | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is it set successfully? | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.SetInputSlotItem({"itemName": "minecraft:iron_ore", "auxValue": 0, "count": 1}, (x, y, z), 1) 
``` 

## SetPlayerUIItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the item of the synthesis container 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id |

| slot | int | Container slot, meaning see: [Container Type Enumeration](../../Enumeration Value/PlayerUISlot.md) | 
| itemDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, returns None if there is no item | 
| needBack | bool | Whether to put the existing items in the container slot back to the player's backpack, the default is True. When set to False, the existing items in the container slot will be directly overwritten with the items in itemDict. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Synthetic containers include workbench, anvil, enchantment table, loom, grinding wheel, stonecutter, cartography table, and forging table. 
- If there are items in the original slot, the original items will be put into the player's backpack. If the player's backpack is full, the corresponding item drops will be generated at the player's current position in the world. 
- Note that all synthetic container slots are shared and will not be rearranged according to different containers. If the container is not opened or another container is opened, this interface will return False. 
- The following situations are considered to clear a specific slot: itemDict is None, {}, or itemName is minecraft:air, or count is 0, and the needBack parameter is False 
- Because the creation output item generation position is special, this interface has blocked the situation of slot = 50, that is, it is impossible to set the creation output item. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
itemDict = { 
'itemName': 'minecraft:bow', 
'count': 1, # You can fill in 0 to delete an item in a slot 
'auxValue': 0, 
} 
comp.SetPlayerUIItem(playerId, slot, itemDict) 
# You can also use comp.SetPlayerUIItem(playerId, slot, None, False) to clear items 
``` 

## SpawnItemToContainer 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Generate items to the inventory of the container block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| slotPos | int | Box slot | 
| blockPos | tuple(int,int,int) | Box position |

| dimensionId | int | Dimension of the container | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- This interface does not support ender boxes. For the corresponding ender chest interface, please refer to [SpawnItemToEnderChest](#spawnitemtoenderchest) 
- The following situations are considered to clear a specific slot: itemDict is empty, is {}, or itemName is minecraft:air, or count is 0 
- Currently this interface supports container type blocks: boxes, shulker boxes, hoppers, barrels, droppers, and launchers 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
itemDict = { 
'itemName': 'minecraft:bow', 
'count': 1, # You can fill in 0 to achieve the effect of deleting an item in a slot 
'enchantData': [(serverApi.GetMinecraftEnum().EnchantType.BowDamage, 1),], 
'auxValue': 0, 
'customTips':'§c new item §r', 
'extraId': 'abc', 
'userData': { }, 
} 
# Spawn item to slot 0 of container, container is located at dimension 0, coordinates are (x,y,z) 
comp = serverApi.GetEngineCompFactory().CreateItem(levelId) 
comp.SpawnItemToContainer(itemDict, 0, (x,y,z), 0) 
``` 

## SpawnItemToEnderChest 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Spawn item to ender chest 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| slotPos | int | Ender Chest Slot | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- The following situations are considered to clear a specific slot: itemDict is empty, is {}, or itemName is minecraft:air, or count is 0 

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
    'userData': { },
}
comp = serverApi.GetEngineCompFactory().CreateItem(playerId)
comp.SpawnItemToEnderChest(itemDict, 0)
```