--- 
sidebarDepth: 1 
--- 
# Backpack 

## GetEntityItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get biological items, support getting backpack, armor bar, off-hand and main hand items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posType | int | [ItemPosType enumeration](../../enumeration value/ItemPosType.md) | 
| slotPos | int | Slot, need to be set when getting INVENTORY and ARMOR, write 0 in other cases | 
| getUserData | bool | Whether to obtain userData, default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Item information dictionary, returns None if there is no item | 

- Notes 
- Left and right hands and equipment can replace the GetPlayerItem interface to obtain the player's items, but backpacks cannot. Get creature backpacks. Currently supports donkeys, mules, alpacas and other custom creatures with backpacks. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(entityId) 
comp.GetEntityItem(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 0) 
``` 

## GetEquItemEnchant 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 


Get the enchantment of the armor in the equipment slot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| slotPos | int | [ArmorSlotType enumeration](../../enumeration value/ArmorSlotType.md)enumeration | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(tuple(int,int)) | Enchantment of armor | 

- Notes 
- If the item does not exist or has no enchantment value, return None. If present, returns an array of tuples, each consisting of the enchantment type ([EnchantType enumeration](../../enumeration value/EnchantType.md)) and the enchantment level 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetEquItemEnchant(serverApi.GetMinecraftEnum().ArmorSlotType.HEAD) 
``` 

## GetEquItemModEnchant 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Gets the custom enchantment for the armor in the equipment slot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| slotPos | int | [ArmorSlotType enumeration](../../enumeration value/ArmorSlotType.md)enumeration | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(tuple(str,int)) | Each tuple in the list consists of a custom enchantment id and an enchantment level. If there is no custom enchantment, an empty list is returned | 

- Example


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetEquItemModEnchant(serverApi.GetMinecraftEnum().ArmorSlotType.HEAD) 
``` 

## SetEntityItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set biological items. It is recommended that developers set them according to the characteristics of the biological. Some biological equipment may not be displayed after setting, but the set equipment will still be dropped after death 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posType | int | [ItemPosType Enumeration](../../Enumeration Value/ItemPosType.md) | 
| itemDict | dict | List of <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> at different positions on the creature. If None is passed in, the item/equipment at the current position will be cleared. | 
| slotPos | int | Container slot. If ItemPosType is left or right hand, it can be omitted. If ItemPosType is backpack, it corresponds to backpack slot. If ItemPosType is armor, it corresponds to equipment position. For details, please see [ArmorSlotType Enumeration](../../Enumeration Value/ArmorSlotType.md) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Return True if set successfully | 

- Notes 
- Setting the creature backpack currently supports donkeys, mules, alpacas, and other custom creatures with backpacks. Compared with the spawnTo series of interfaces, this interface has more slot restrictions. Only equipment and left-hand items in the corresponding slot can be set, and equipment cannot be set for the right hand. Drowned corpses do not currently support setting custom equipment. If the passed itemDict is None or {}, itemName is minecraft:air, and count is 0, the effect of clearing items can be achieved. For the player backpack, please use SpawnItemToPlayerInv to generate items, and use SetInvItemNum to set 0 to clear items. Other parts can also be set using this interface. 
- posType is set to serverApi.GetMinecraftEnum().ItemPosType.OFFHAND, itemDict is set to None to replace ClearPlayerOffHand

- Example

```python
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateItem(entityId)
itemDict = {
    'itemName': 'minecraft:bow',
    'count': 1,
    'enchantData': [(serverApi.GetMinecraftEnum().EnchantType.BowDamage, 1),],
    'auxValue': 0,
    'customTips':'§c new item §r',
    'extraId': 'abc',
    'userData': {},

}
comp.SetEntityItem(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, itemDict, 0)

#Replacement of ClearPlayerOffHand interface
comp.SetEntityItem(serverApi.GetMinecraftEnum().ItemPosType.OFFHAND, None, 0)
```