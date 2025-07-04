--- 
sidebarDepth: 1 
--- 
# Items 

# Index 

Including the interface of item properties. For the generation and acquisition of items, see [Player/Backpack](Player/Index.md#Backpack), [Entity/Backpack](Entity/Index.md#Backpack), [Block/Container](Block/Index.md#Container), and for the generation and acquisition of item entities, see [World/Entity Management](World/Index.md#Entity Management) 

--- 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CancelShearsDestoryBlockSpeed](Item.md#cancelshearsdestoryblockspeed) | <span style="display:inline;color:#ff5555">Server</span> | Cancel the speed setting of shears destroying a block | 
| [CancelShearsDestoryBlockSpeedAll](Item.md#cancelshearsdestoryblockspeedall) | <span style="display:inline;color:#ff5555">Server</span> | Cancel the shears' destruction speed setting for all blocks | 
| [ChangeArmorTextures](Item.md#changearmortextures) | <span style="display:inline;color:#7575f9">Client</span> | Modify the textures of armor displayed in the scene and in the UI | 
| [ChangeItemTexture](Item.md#changeitemtexture) | <span style="display:inline;color:#7575f9">Client</span> | Replace the texture of the item. After the modification, all items using the texture will be changed, and subsequent items of the same type will also be changed. It will also modify the display of the item on the UI interface, the display when holding it and the display when it drops in the scene. | 
| [GetCustomName](Item.md#getcustomname) | <span style="display:inline;color:#ff5555">Server</span> | Get the custom name of the item, which is the same as the name modified by the anvil | 
| [GetItemBasicInfo](Item.md#getitembasicinfo) | <span style="display:inline;color:#ff5555">Server</span> | Get the basic information of the item | 
| [GetItemBasicInfo](Item.md#getitembasicinfo) | <span style="display:inline;color:#7575f9">Client</span> | Get the basic information of the item | 
| [GetItemDefenceAngle](Item.md#getitemdefenceangle) | <span style="display:inline;color:#ff5555">Server</span> | Get the angle range of the shield item | 
| [GetItemDurability](Item.md#getitemdurability) | <span style="display:inline;color:#ff5555">Server</span> | Get the durability of the item in the specified slot | 
| [GetItemEffectName](Item.md#getitemeffectname) | <span style="display:inline;color:#7575f9">Client</span> | Get the item's status description, such as: §7Protection 0§r | 
| [GetItemFormattedHoverText](Item.md#getitemformattedhovertext) | <span style="display:inline;color:#7575f9">Client</span> | Get the item's formatted hover text, such as: §fDisaster Banner§r | 
| [GetItemHoverName](Item.md#getitemhovername) | <span style="display:inline;color:#7575f9">Client</span> | Get the hover name of the item, such as: Disaster Banner§r | 
| [GetItemMaxDurability](Item.md#getitemmaxdurability) | <span style="display:inline;color:#ff5555">Server</span> | Get the maximum durability of the item in the specified slot | 
| [GetUserDataInEvent](Item.md#getuserdatainevent) | <span style="display:inline;color:#ff5555">Server</span> | Make the <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> parameter of item-related server events contain userData. Just call it when the mod is initialized | 
| [GetUserDataInEvent](Item.md#getuserdatainevent) | <span style="display:inline;color:#7575f9">Client</span> | Make the <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> parameter of the item-related client event contain userData. Call it when the mod is initialized | 
| [LookupItemByName](Item.md#lookupitembyname) | <span style="display:inline;color:#ff5555">Server</span> | Determine if the item with the specified identifier exists | 
| [SetAttackDamage](Item.md#setattackdamage) | <span style="display:inline;color:#ff5555">Server</span> | Set the attack damage value of the item | 
| [SetCustomName](Item.md#setcustomname) | <span style="display:inline;color:#ff5555">Server</span> | Set the custom name of the item, which is consistent with renaming with anvil | 
| [SetItemDefenceAngle](Item.md#setitemdefenceangle) | <span style="display:inline;color:#ff5555">Server</span> | Set the shield item's blocking angle range | 
| [SetItemDurability](Item.md#setitemdurability) | <span style="display:inline;color:#ff5555">Server</span> | Set the item's durability | 
| [SetItemMaxDurability](Item.md#setitemmaxdurability) | <span style="display:inline;color:#ff5555">Server</span> | Set the item's maximum durability | 
| [SetItemTierLevel](Item.md#setitemtierlevel) | <span style="display:inline;color:#ff5555">Server</span> | Set the mining level of tool items | 
| [SetItemTierSpeed](Item.md#setitemtierspeed) | <span style="display:inline;color:#ff5555">Server</span> | Set the mining speed of tool items | 
| [SetMaxStackSize](Item.md#setmaxstacksize) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum stacking number of items (archive) | 
| [SetShearsDestoryBlockSpeed](Item.md#setshearsdestoryblockspeed) | <span style="display:inline;color:#ff5555">Server</span> | Set the speed at which shears destroy a block | 

## CancelShearsDestoryBlockSpeed 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Cancel the speed at which shears destroy a block 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block name, including namespace | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(entityId) 
comp.CancelShearsDestoryBlockSpeed("minecraft:obsidian") 
``` 

## CancelShearsDestoryBlockSpeedAll 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Cancel the destruction speed setting of scissors for all blocks 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(entityId) 
comp.CancelShearsDestoryBlockSpeedAll() 
``` 




## ChangeArmorTextures 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Modify the textures displayed in the scene and in the UI 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| armorIdentifier | str | Armor identifier, format [namespace:name:auxvalue], auxvalue defaults to 0 | 
| texturesDict | dict | Mapping table of target textures in the scene, format can refer to "definitions/attachables/diamond_helmet.json" configuration | 
| uiIconTexture | str | Texture of armor UI icon, If it is None or "", it means that the icon on the UI will not be modified | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the modification is successful (because of delayed loading, the return of success here does not mean that the texture path in the parameter is correct. The wrong path will cause the texture to be lost and display abnormally during rendering) | 

- Notes 
- Cannot be used at the same time as the texture animation of the item 
- There is a certain performance consumption, and frequent calls are not recommended 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorRender(levelId) 
# Change the display of diamond helmet to gold helmet 
textureDict = { 
"default": "textures/models/armor/gold_1", 
"enchanted": "textures/misc/enchanted_item_glint"
}
print(comp.ChangeArmorTextures("minecraft:diamond_helmet", textureDict, "textures/items/gold_helmet"))
```



## ChangeItemTexture

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.itemCompClient.ItemCompClient

- Description 

Replace the texture of an item. After the modification, all items using this texture will be changed, and subsequent items of this type created will also be changed. It will also modify the display of the item on the UI interface, the display when holding it, and the display when dropping in the scene. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| identifier | str | Item identifier, format [namespace:name:auxvalue], auxvalue defaults to 0 | 
| texturePath | str | Texture path | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the modification is successful (because of the use of delayed loading, the return success here does not mean that the texture path is correct. The wrong path will cause the texture to be lost and the display to be abnormal during rendering) | 

- Notes 
- Because all items using this texture will be modified at the same time, be as cautious as possible when using it. It is not recommended to modify the original items. It is recommended to only modify items that use new textures defined by yourself. 
- Sequence frame texture items do not support dynamic texture modification 
- Some items have special logic and cannot be modified: boxes, banners, creature heads, shields, tridents, fishing rods 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateItem(levelId) 
print(comp.ChangeItemTexture("mytool:hatchet_1:0", "textures/items/hatchet_1")) 
``` 

## GetCustomName 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the custom name of the item, which is the same as the name modified by the anvil 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>. If it is itemDict obtained by the interface, it should contain userData, that is, getUserData should be True | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Custom name | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
itemDict = comp.GetPlayerItem(serverApi.GetMinecraftEnum().ItemPosType.CARRIED, 0, True) 
name = comp.GetCustomName(itemDict) 
``` 

## GetItemBasicInfo 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get basic information of an item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| itemName | str | Identifier of item | 
| auxValue | int | auxvalue of item, default is 0 | 
| isEnchanted | bool | Whether enchanted, default is False. id_Aux used for return | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Basic information, see notes for details | 

- Notes 
- The default value of auxValue is 0, which can be left unset. If the item does not exist, the return value is None 
| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| itemName | str | Localized item name | 
| maxStackSize |int| Maximum number of item stacks | 
| maxDurability |int| Maximum item durability | 
| id_Aux |int| Mainly used for client ui binding, see client interface for details |

| tierDict |dict| Mining-related properties defined by custom blocks netease:tier, returns None when not set | 
| itemCategory |str| Creative column category | 
| itemType |str| Item type | 
| itemTierLevel |int| Tool level | 
| fuelDuration |float| Fuel duration | 
| foodNutrition |int| Food nutrition value | 
| foodSaturation |float| Food satiety | 
| weaponDamage |int| Weapon attack power | 
| armorDefense |int| Armor defense | 
- Some original items are special and cannot get the return value of some fields 
Block fuel cannot get fuel duration, bow, crossbow, trident cannot get weapon attack power, cake cannot get nutrition value and satiety, horse armor cannot get armor defense, and the corresponding fields of the above items are returned as 0 
- Creative column category description 
| Creative column category | Meaning | 
| --------- | -----| 
| construction | 
| nature | 
| equipment | 
| items | 
| custom | 
| empty string | not in the creation column | 
- Item type, the value is an empty string or one of the following type names: 
| type name | meaning | 
| ----- | ----- | 
| book | 
| sword | 
| shears | 
| axe | 
| clock | 
| bucket | 
| fishing_rod | 
| hoe | 
| shovel | 
| pickaxe | 
| dye | bone meal | 
- Tool level represents different materials. When there is no tool level, the value is -1. The corresponding relationship between tool level and material is as follows 
| tool level | material | 
| ------- | ---- | 
| 0 | Wooden/Gold Tools | 
| 1 | Stone Tools | 
| 2 | Iron Tools | 
| 3 | Diamond Tools | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(levelId) 
comp.GetItemBasicInfo("minecraft:bow") 
``` 




### Client interface 

<span id="c0"></span> 
method in mod.client.component.itemCompClient.ItemCompClient 

- Description 

Get basic information of an item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemName | str | Identifier of item | 
| auxValue | int | auxvalue of item, default is 0 | 
| isEnchanted | bool | Whether enchanted, default is False. id_Aux for return | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Basic information dictionary, see notes | 

- Notes 
- The default value of auxValue is 0, which can be left unset. If the item does not exist, the return value is None 
| Keywords | Data Type | Description | 
| ----------| --------------------- | ---------| 
| itemName | str | Localized item name | 
| maxStackSize |int| Maximum number of stacks of items | 
| maxDurability |int| Maximum durability of items | 
| id_Aux |int| Used to bind the #item_id_aux field to the inventory_item_renderer type control of the UI, see the notes for details | 
| tierDict |dict| Mining-related properties defined by custom blocks netease:tier, returns None when not set | 
| itemCategory |str| Creation column category | 
| itemType |str| Item type | 
| itemTierLevel |int| Tool level | 
| fuelDuration |float| Fuel duration | 
| foodNutrition |int| Food nutrition value | 
| foodSaturation |float| Food satiety | 
| weaponDamage |int| weapon attack power | 
| armorDefense |int| armor defense power | 
- Some original items are special and the return values of individual fields cannot be obtained. 
Block-type fuel cannot obtain fuel duration, bows, crossbows, and tridents cannot obtain weapon attack power, cakes cannot obtain nutritional values and satiety, and horse armor cannot obtain armor defense power. The return value of the corresponding fields of the above items is 0. 
- Example of id_Aux field: 
Add an inventory_item_renderer control and the binding of #item_id_aux in the ui. 
```json 
"my_item_renderer": { 
"type": "custom", 
"renderer": "inventory_item_renderer",

"size": [ 160, 160 ], 
"bindings" : [ 
{ 
"binding_condition" : "always_when_visible", 
"binding_name" : "#GetItemIdAux", 
"binding_name_override" : "#item_id_aux" 
} 
] 
} 
``` 

Then add the binding callback in python 
```python 
@ViewBinder.binding(ViewBinder.BF_BindInt, "#GetItemIdAux") 
def OnStarkGridResize(self): 
comp = clientApi.GetEngineCompFactory().CreateItem(levelId) 
info = comp.GetItemBasicInfo("minecraft:bow", 0, True) 
return info['id_aux'] 
``` 
- Create Column Category Description 
| Creative column category | Meaning | 
| --------- | -----| 
| construction | 
| nature | nature | 
| equipment | 
| items | 
| custom | custom | 
- Item type, the value is an empty string or one of the following type names: 
| Type name | Meaning | 
| ----- | ----- | 
| book | 
| sword | 
| shears | 
| axe | 
| clock | 
| bucket | 
| fishing_rod | 
| hoe | 
| shovel | 
| pickaxe | 
| dye | bone meal | 
- Tool level represents different materials. When there is no tool level, the value is -1. The corresponding relationship between tool level and material is as follows 
| tool level | material | 
| ------- | ---- | 
| 0 | Wooden/Gold Tools | 
| 1 | Stone Tools | 
| 2 | Iron Tools | 
| 3 | Diamond Tools | 

- Example


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateItem(levelId) 
comp.GetItemBasicInfo("minecraft:bow") 
``` 

## GetItemDefenceAngle 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Get the defense angle range of the shield item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posType | int | [ItemPosType enumeration](../enumeration value/ItemPosType.md) | 
| slotPos | int | slot | 

- return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(float) | Angle range | 

- Notes 
- When the player id passed in is incorrect, the player does not hold a shield, or a non-existent slot is passed in, an empty list will be returned 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetItemDefenceAngle(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 0) 
``` 

## GetItemDurability 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer


- Description 

Get the durability of the item in the specified slot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posType | int | [ItemPosType enumeration](../enumeration value/ItemPosType.md) | 
| slotPos | int | Slot, only meaningful when posType is ItemPosType.INVENTORY or ItemPosType.ARMOR | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Durability value of the item | 

- Notes 
- posType is set to serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, which can replace GetInvItemDurability; posType is set to serverApi.GetMinecraftEnum().ItemPosType.ARMOR, which can replace GetEquItemDurability;

- Example

```python
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateItem(playerId)
comp.GetItemDurability(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 1)

#Method to replace GetInvItemDurability
comp.GetItemDurability(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 1) 

#Method to replace GetEquItemDurability 
comp.GetItemDurability(serverApi.GetMinecraftEnum().ItemPosType.ARMOR, 1) 
``` 

## GetItemEffectName 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.itemCompClient.ItemCompClient 

- Description 

Get the item status description, such as: §7 Protection 0§r 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| itemName | str | item identifier | 
| auxValue | int | item additional value auxValue, default is no auxValue (0) | 
| userData | dict | item userData, default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | item status description | 

- Example 

```python 
# Disaster Banner 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateItem(levelId) 
comp.GetItemEffectName("minecraft:banner", 15, {'Type': 1}) 
``` 

## GetItemFormattedHoverText 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.itemCompClient.ItemCompClient 

- Description 

Get the formatted hover text of the item, such as: §fDisaster Banner§r 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemName | str | Item identifier | 
| auxValue | int | Item additional value auxValue, default is no auxValue (0) | 
| showCategory | bool | Whether to include item category information, default is False | 
| userData | dict | Item userData, default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Formatted hover text for the item | 

- Example 

```python

# Disaster Banner 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateItem(levelId) 
comp.GetItemFormattedHoverText("minecraft:banner", 15, True, {'Type': 1}) 
``` 

## GetItemHoverName 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.itemCompClient.ItemCompClient 

- Description 

Get the hover name of the item, such as: Disaster Banner§r 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | :--- | 
| itemName | str | item identifier | 
| auxValue | int | auxValue of the item, default is no auxValue (0) | 
| userData | dict | Item userData, default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Item hover name | 

- Example 

```python 
# Disaster Banner 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateItem(levelId) 
comp.GetItemHoverName("minecraft:banner", 15, {'Type': 1}) 
``` 

## GetItemMaxDurability 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer

- describe


Get the maximum durability of the item in the specified slot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posType | int | [ItemPosType enumeration](../enumeration value/ItemPosType.md) | 
| slotPos | int | Slot, only meaningful when posType is ItemPosType.INVENTORY or ItemPosType.ARMOR | 
| isUserData | bool | If True, only try to get the value of the special setting of the userData of the item, and return 0 if there is no special setting. If False, it will try to get the value in userData first, and if not, get the general value of this type of item. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Maximum durability of the item | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.GetItemMaxDurability(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 1, False) 
``` 

## GetUserDataInEvent 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Make the <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> parameter of item-related server events contain userData. Just call it when the mod is initialized 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| eventName | str | Engine event name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Success | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(levelId) 
# After calling this, the itemDict parameter of the PlayerEatFoodServerEvent event will have the userData field 
comp.GetUserDataInEvent("PlayerEatFoodServerEvent") 
``` 

### Client Interface 

<span id="c0"></span> 
method in mod.client.component.itemCompClient.ItemCompClient 

- Description 

Make the <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> parameter of item-related client events have userData. Just call it when the mod is initialized 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| eventName | str | Engine event name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateItem(levelId) 
# After calling this, the itemDict parameter of the ActorAcquiredItemClientEvent event will have the userData field 
comp.GetUserDataInEvent("ActorAcquiredItemClientEvent") 
``` 

## LookupItemByName

<span style="display:inline;color:#ff5555">Server</span>

method in mod.server.component.gameCompServer.GameComponentServer


- Description 

Check if the item with the specified identifier exists 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemName | str | The identifier of the item. Similar to "minecraft:bed", supports custom items | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | exist True means the corresponding item exists, False means the corresponding item does not exist | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
exist = gameComp.LookupItemByName("minecraft:bed") 
``` 

## SetAttackDamage 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the attack damage value of the item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| attackDamage | int | Attack damage value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
itemDict = comp.GetPlayerItem(serverApi.GetMinecraftEnum().ItemPosType.CARRIED, 0, True) 
success = comp.SetAttackDamage(itemDict, 5) 
if success: 
comp.SpawnItemToPlayerCarried(itemDict, playerId) 
``` 

## SetCustomName 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the custom name of the item, consistent with renaming with anvil 

- Parameters 

| Parameter Name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| name | str | Item name. Support unicode | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
itemDict = comp.GetPlayerItem(serverApi.GetMinecraftEnum().ItemPosType.CARRIED, 0, True) 
comp.SetCustomName(itemDict, 'Steve') 
comp.SpawnItemToPlayerCarried(itemDict, playerId) 
``` 

## SetItemDefenceAngle 


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the blocking angle range of the shield item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posType | int | [ItemPosType enumeration](../enumeration value/ItemPosType.md) | 
| slotPos | int | slot | 
| angleLeft | float | Left range, if you don't want to set the left range, pass None, the value range is [-180,180] | 
| angleRight | float | Right range, if you don't want to set the right range, pass None, the value range is [-180,180], and angleLeft<angleRight | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- When the set item is not a shield item, return False; the native shield will return True but still follow the native logic 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.SetItemDefenceAngle(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 0, -60, 70) 
``` 

## SetItemDurability 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the durability of the item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| posType | int | [ItemPosType Enumeration](../Enumeration Value/ItemPosType.md) | 
| slotPos | int | Slot, only meaningful when posType is ItemPosType.INVENTORY or ItemPosType.ARMOR | 
| durability | int | Durability value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- When the set durability value exceeds the maximum durability value of the item, the maximum durability value is used; the minimum durability value is 0. 
- When posType is set to serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, it can replace SetInvItemDurability; when posType is set to serverApi.GetMinecraftEnum().ItemPosType.ARMOR, it can replace SetEquItemDurability; 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.SetItemDurability(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 0, 5) 

#Method to replace SetInvItemDurability 
comp.SetItemDurability(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 0, 5) 5) 
#Method to replace SetEquItemDurability 
comp.SetItemDurability(serverApi.GetMinecraftEnum().ItemPosType.ARMOR, 0, 5) 
``` 

## SetItemMaxDurability 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the maximum durability of the item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posType | int | [ItemPosType enumeration](../enumeration value/ItemPosType.md) | 
| slotPos | int | Slot, only meaningful when posType is ItemPosType.INVENTORY or ItemPosType.ARMOR | 
| maxDurability | int | Maximum durability, can be set to 0~32767 | 
| isUserData | bool | If True, the setting is only effective for the specified item, if False, it is effective for all items of the same type | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- If the number of items stacked is greater than 1, the durability change will take effect on the entire stack of items. And after the durability is 0, each consumption of durability will reduce the number by one 
- The maximum durability of userData set for the item has the highest priority during calculation, and the userData data is saved. 
- When merging a grindstone or backpack, if two items have userData, only one will be retained. When repairing in an anvil, the maximum durability is the durability of the repaired item. 
- When the maximum durability value is changed, the current durability will also be repaired proportionally. 
- The maximum durability set for all items of the same type is not saved. Each time the world is restarted, it will be reinitialized. The initial maximum durability can be set through the `minecraft:max_damage` component of the corresponding item json 
- If the backpack item is set, when the slot value is -1, set the maximum durability of the left hand item 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.SetItemMaxDurability(serverApi.GetMinecraftEnum().ItemPosType.INVENTORY, 0, 5, False) 
``` 

## SetItemTierLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the mining level of tool items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| level | int | Mining level | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- For blocks that are not always destructible (including blocks with material Stone, Metal, TopSnow, Snow, Web), tools of different mining levels are required to break them and produce drops. 
| level | type | 
| ----- | ---- | 
| 0 | Wood |

| 1 | Stone | 
| 2 | Iron | 
| 3 | Diamond | 
| 4 | Nether | 
- Both swords and scissors can destroy spider webs and produce drops; 
A shovel can destroy snow and top snow and produce drops; 
Whether a pickaxe can be used to destroy or not: 
1) For obsidian, Nether blocks, and ancient debris, a pickaxe of Level 3 or higher is required to destroy and produce drops; 
2) For diamond blocks, diamond ore, emerald blocks, emerald ore, gold blocks, gold ore, redstone ore, and glowing redstone ore, a pickaxe of Level 2 or higher is required to destroy and produce drops; 
3) For iron blocks, iron ore, lapis lazuli blocks, and lapis lazuli ore, a pickaxe of Level 1 or higher is required to destroy and produce drops; 
4) For other Stone and Metal blocks, a pickaxe of Level 0 or higher is required to destroy and produce drops.

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
itemDict = comp.GetPlayerItem(serverApi.GetMinecraftEnum().ItemPosType.CARRIED, 0, True) 
success = comp.SetItemTierLevel(itemDict, 5) 
if success: 
comp.SpawnItemToPlayerCarried(itemDict, playerId) 
``` 

## SetItemTierSpeed 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the mining speed of tool items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| speed | float | Mining speed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
itemDict = comp.GetPlayerItem(serverApi.GetMinecraftEnum().ItemPosType.CARRIED, 0, True) 
success = comp.SetItemTierSpeed(itemDict, 32) 
if success: 
comp.SpawnItemToPlayerCarried(itemDict, playerId) 
``` 

## SetMaxStackSize 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the maximum stack size of an item (save) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| maxStackSize | int | Maximum stack size, cannot exceed 64. If this value is less than the stack size of the item, failure will be returned | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId)
itemDict = comp.GetPlayerItem(serverApi.GetMinecraftEnum().ItemPosType.CARRIED, 0, True)
success = comp.SetMaxStackSize(itemDict, 32)
if success:
    comp.SpawnItemToPlayerCarried(itemDict, playerId)
```



## SetShearsDestoryBlockSpeed

<span style="display:inline;color:#ff5555">Server</span>


method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Set the speed at which scissors destroy a block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| blockName | str | Block name, including namespace | 
| speed | float | Destruction speed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The set speed will eventually be added to the scissors' enchantment: efficiency calculation 
- The original scissors destroy spider webs at a speed of 15 and wool at a speed of 5. This interface can also be used to rewrite the destruction speed of these two blocks 

The set speed must be greater than 1, otherwise the interface returns False 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(entityId) 
comp.SetShearsDestoryBlockSpeed("minecraft:obsidian", 100) 
``` 

