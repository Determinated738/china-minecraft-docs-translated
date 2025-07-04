--- 
sidebarDepth: 1 
--- 
# Backpack 

## AddEnchantToInvItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Add enchantment information to items in the inventory 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| slotPos | int | Inventory slot | 
| enchantType | int | Enchant type, you can view the enumeration value document | 
| level | int | Enchant level | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.AddEnchantToInvItem(0, serverApi.GetMinecraftEnum().EnchantType.BowDamage, 2) 
``` 

## AddModEnchantToInvItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Add custom enchantment information to items in the inventory 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| slotPos | int | Inventory slot | 
| modEnchantId | str | Custom enchantment identifier | 
| level | int | Custom enchantment level | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.AddModEnchantToInvItem(0, "customenchant", 2) 
``` 

## ChangePlayerItemTipsAndExtraId 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Modify the custom tips and custom identifiers of player items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posType | int | [ItemPosType enumeration](../../enumeration value/ItemPosType.md) | 
| slotPos | int | Inventory slot | 
| customTips | str | Custom tips for the item | 
| extraId | str | Custom identifier for the item | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.ChangePlayerItemTipsAndExtraId(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 0, "custom tips", "custom identifier") 
``` 

## ChangeSelectSlot 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Sets the index of the player's currently selected quickbar item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| slot | int | The index of the quick bar item, starting from 0, the maximum is 8 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
success = comp.ChangeSelectSlot(0) 
``` 

## GetCarriedItem 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.itemCompClient.ItemCompClient 

- Description 

Get the information of the right hand item 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| getUserData | bool | Whether to get the userData of the item, the default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, returns None if there is no item | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateItem(entityId) 
carriedData = comp.GetCarriedItem() 
``` 

## GetInvItemEnchantData 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the enchantment information of the item in the inventory 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| slotPos | int | Inventory slot | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(tuple(int,int)) | Each tuple in the list consists of an enchantment type ([EnchantType enumeration](../../enumeration value/EnchantType.md)) and an enchantment level. If there is no enchantment, it will be an empty list | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetInvItemEnchantData(0)

``` 

## GetInvItemModEnchantData 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the custom enchantment information of items in the inventory 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| slotPos | int | Inventory slot | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(tuple(str,int)) | Each tuple in the list consists of a custom enchantment id and an enchantment level. If there is no custom enchantment, it is an empty list | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetInvItemModEnchantData(0) 
``` 

## GetOffhandItem 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.itemCompClient.ItemCompClient 

- Description 

Get the information of the left-hand item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| getUserData | bool | Whether to get the userData of the item, the default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, returns None if there is no item | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateItem(entityId) 
offhandData = comp.GetOffhandItem() 
``` 

## GetPlayerAllItems 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the batch item information of the slot specified by the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posType | int | [ItemPosType enumeration](../../enumeration value/ItemPosType.md) | 
| getUserData | bool | Whether to get userData, the default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(dict) | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> array, the position without an item is None | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetPlayerAllItems(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY) 
``` 




## GetPlayerItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get player items, support backpack, armor bar, off-hand and main-hand items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posType | int | [ItemPosType enumeration](../../enumeration value/ItemPosType.md) | 
| slotPos | int | Slot, need to be set when getting INVENTORY and ARMOR, write 0 in other cases | 
| getUserData | bool | Whether to get userData, default is False | 

- Return value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, returns None if there is no item | 

- Notes 
- Left and right hands and equipment can replace the GetEntityItem interface to obtain items of creatures, but backpacks cannot. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetPlayerItem(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 0) 
``` 

## GetSelectSlotId 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the player's currently selected slot 

- Parameters 


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Current slot, returns -1 on error | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetSelectSlotId() 
``` 

## GetSlotId 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.itemCompClient.ItemCompClient 

- Description 

Get the slot id of the currently held shortcut bar 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| int | 0 to 8 | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateItem(entityId) 
slotId = comp.GetSlotId() 
``` 

## RemoveEnchantToInvItem 


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Remove enchantment information from items in the inventory 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| slotPos | int | Inventory slot | 
| enchantType | int | Enchantment type, see enumeration value documentation | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Removal result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.RemoveEnchantToInvItem(0, serverApi.GetMinecraftEnum().EnchantType.BowDamage) 
``` 

## RemoveModEnchantToInvItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Remove custom enchantment information from items in the inventory 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| slotPos | int | Inventory slot | 
| modEnchantId | str | Custom enchantment identifier | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Removal result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.RemoveModEnchantToInvItem(0, "customenchant") 
``` 

## SetInvItemExchange 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Exchange player backpack items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos1 | int | item position | 
| pos2 | int | item position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.SetInvItemExchange(0, 2) 
``` 

## SetInvItemNum 

<span style="display:inline;color:#ff5555">Server</span>


method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the number of items in the player's backpack 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| slotPos | int | Inventory slot | 
| num | int | Number of items. You can clear the backpack items by setting the number to 0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.SetInvItemNum(0, 10) 
``` 
## SetPlayerAllItems 
<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Add batch item information to the specified slot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemsDictMap | dict | Dictionary of items to be added, the key of the dictionary is tuple([ItemPosType](../../Enumeration value/ItemPosType.md), slotPos), and the value is the item to be added. href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- |

| dict | Setting result, the key of the dictionary is tuple(ItemPosType, slot), and the value is bool, indicating whether the slot setting is successful. | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
itemsDict = { 
'itemName': 'minecraft:bow', 
'count': 1, 
'enchantData': [(serverApi.GetMinecraftEnum().EnchantType.BowDamage, 1),], 
'auxValue': 0, 
'customTips':'§c new item §r', 
'extraId': 'abc', 
'userData': { }, 
} 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
itemsDictMap = {} 
for i in xrange(36): 
if i % 3 == 0: 
itemsDictMap[(minecraftEnum.ItemPosType.INVENTORY, i)] = itemsDict 
itemsDictMap[(minecraftEnum.ItemPosType.CARRIED, 0)] = itemsDict 
itemsDictMap[(minecraftEnum.ItemPosType.OFFHAND, 0)] = itemsDict 
comp.SetPlayerAllItems(itemsDictMap) 
``` 

## SpawnItemToPlayerCarried 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Spawns items to the player's right hand 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| playerId | str | Player id | 

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
    'userData': { },
}
comp = serverApi.GetEngineCompFactory().CreateItem(playerId)
comp.SpawnItemToPlayerCarried(itemDict, playerId)
```



## SpawnItemToPlayerInv

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Generate items to player backpack 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| playerId | str | Player id | 
| slotPos | int | Backpack slot (optional) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- When slotPos is not set, when the set number exceeds the upper limit of a single slot stack, the excess items will be set to other free slots. If the generated items are the same as the items in the slots in the backpack, the interface will also add the items to these slots. Note: If the sum of the number of remaining items in the backpack and the number of added items is greater than 64, the number of items will be generated to 64, but the interface returns failure. 

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
comp.SpawnItemToPlayerInv(itemDict, playerId, 0)
```