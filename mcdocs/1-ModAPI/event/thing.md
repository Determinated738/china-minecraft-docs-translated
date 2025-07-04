--- 
sidebarDepth: 1 
--- 
# Items 

# Index 

| Events | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [ActorAcquiredItemClientEvent](Items.md#actoracquireditemclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggering time: The event thrown by the client when the player obtains the item (some ways of obtaining items will only trigger client events, and some ways of obtaining items will only trigger server events, so pay attention when using them.) | 
| [ActorAcquiredItemServerEvent](Items.md#actoracquireditemserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: The event thrown by the server when the player obtains the item (some ways of obtaining items will only trigger client events, and some ways of obtaining items will only trigger server events, so pay attention when using them.) | 
| [ActorUseItemClientEvent](Item.md#actoruseitemclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggering time: The event thrown by the client when the player uses the item (special examples of not triggering this event: 1) drinking milk; 2) using dye on a cauldron with water; 3) equipping armor on an armor stand) | 
| [ActorUseItemServerEvent](Item.md#actoruseitemserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: The event thrown by the server before the player uses the item (special examples of not firing this event: 1) drinking milk; 2) using dye on a cauldron with water; 3) equipping armor on an armor stand) | 
| [AnvilCreateResultItemAfterClientEvent](Item.md#anvilcreateresultitemafterclientevent) | <span style="display:inline;color:#7575f9">Client</span> | The event thrown when the player clicks on the item synthesized by the anvil. | 
| [ClientItemTryUseEvent](Item.md#clientitemtryuseevent) | <span style="display:inline;color:#7575f9">Client</span> | The event thrown by the client when the player right-clicks and tries to use the item. You can cancel the use of the item by setting cancel to True. Note: If you need to cancel the use of the item, you need to set cancel to True in both ClientItemTryUseEvent and ServerItemTryUseEvent to cancel it correctly. | 
| [ClientItemUseOnEvent](Item.md#clientitemuseonevent) | <span style="display:inline;color:#7575f9">Client</span> | Event thrown by the client when the player uses an item on a block. Note: If you need to cancel the use of an item, you need to set ret to True in both ClientItemUseOnEvent and ServerItemUseOnEvent to cancel it correctly. | 
| [ClientShapedRecipeTriggeredEvent](Item.md#clientshapedrecipetriggeredevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when the player synthesizes an item | 
| [ContainerItemChangedServerEvent](Item.md#containeritemchangedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Container item change event | 
| [CraftItemOutputChangeServerEvent](Item.md#craftitemoutputchangeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the player takes out the generated item from the container | 
| [FurnaceBurnFinishedServerEvent](Item.md#furnaceburnfinishedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Server-side furnace firing trigger event. Triggered when furnace, blast furnace, smoker burns items | 
| [GrindStoneRemovedEnchantClientEvent](Item.md#grindstoneremovedenchantclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Event thrown when the player clicks on the grindstone to synthesize the item | 
| [InventoryItemChangedClientEvent](Item.md#inventoryitemchangedclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Event thrown by the client when the player's backpack items change. | 
| [InventoryItemChangedServerEvent](Item.md#inventoryitemchangedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | The event thrown by the server when the player's inventory items change. | 
| [ItemReleaseUsingClientEvent](Item.md#itemreleaseusingclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Trigger time: releasing the item in use | 
| [ItemReleaseUsingServerEvent](Item.md#itemreleaseusingserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: when releasing the item in use | 
| [ItemUseAfterServerEvent](Item.md#itemuseafterserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Event thrown by the server after the player uses the item. | 
| [ItemUseOnAfterServerEvent](Item.md#itemuseonafterserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Event thrown by the server after the player uses an item on the opponent's block. | 
| [OnCarriedNewItemChangedClientEvent](Item.md#oncarriednewitemchangedclientevent) | <span style="display:inline;color:#7575f9">Client</span> | This event is triggered when the handheld item changes; the quantity change will not be notified | 
| [OnCarriedNewItemChangedServerEvent](Item.md#oncarriednewitemchangedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: when the player switches the main hand item | 
| [OnItemPutInEnchantingModelServerEvent](Item.md#onitemputinenchantingmodelserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: when the player puts the enchantable item on the enchanting table | 
| [OnNewArmorExchangeServerEvent](Item.md#onnewarmorexchangeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger Time: This event is triggered when the player switches armor | 
| [OnOffhandItemChangedServerEvent](Item.md#onoffhanditemchangedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger Time: This event is triggered when the player switches off-hand items | 
| [OnPlayerActiveShieldServerEvent](Item.md#onplayeractiveshieldserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger Time: This event is triggered when the player activates/deactivates the shield. Including the player holding a shield to enter the stealth state, and switching the shield in the stealth state (switching the same shield with different durability will not be triggered) | 
| [OnPlayerBlockedByShieldAfterServerEvent](Item.md#onplayerblockedbyshieldafterserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: Trigger after the player uses the shield to resist damage | 
| [OnPlayerBlockedByShieldBeforeServerEvent](Item.md#onplayerblockedbyshieldbeforeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: Trigger before the player uses the shield to resist damage | 
| [PlayerDropItemServerEvent](Item.md#playerdropitemserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: Trigger when the player drops an item | 
| [PlayerTryDropItemClientEvent](Item.md#playertrydropitemclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Trigger time: Trigger when the player drops an item | 
| [ServerItemTryUseEvent](Item.md#serveritemtryuseevent) | <span style="display:inline;color:#ff5555">Server</span> | Event thrown by the server when the player right-clicks to try to use an item. Note: If you need to cancel the use of an item, you need to set cancel to True in both ClientItemTryUseEvent and ServerItemTryUseEvent to cancel it correctly. | 
| [ServerItemUseOnEvent](Item.md#serveritemuseonevent) | <span style="display:inline;color:#ff5555">Server</span> | The event thrown by the server before the player uses an item on the other block. Note: If you need to cancel the use of an item, you need to set ret to True in both ClientItemUseOnEvent and ServerItemUseOnEvent to cancel it correctly. | 
| [ServerPlayerTryTouchEvent](Item.md#serverplayertrytouchevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the player is about to pick up an item | 
| [ShearsUseToBlockBeforeServerEvent](Item.md#shearsusetoblockbeforeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: When an entity uses scissors on a block, the block with the scissors special effect will trigger this event on the server thread | 
| [StartUsingItemClientEvent](Item.md#startusingitemclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Thrown when a player uses an item (currently only supports Bucket, Trident, RangedWeapon, Medicine, Food, Potion, Crossbow, ChemistryStick) | 
| [StopUsingItemClientEvent](Item.md#stopusingitemclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Thrown when a player stops using an item (currently only supports Bucket, Trident, RangedWeapon, Medicine, Food, Potion, Crossbow, ChemistryStick) | 
| [UIContainerItemChangedServerEvent](Item.md#uicontaineritemchangedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when a synthesis container item changes | 
# Item 

## ActorAcquiredItemClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 


- Description 

Trigger timing: The event thrown by the client when the player obtains an item (some ways of obtaining items will only trigger client events, and some ways of obtaining items will only trigger server events. Please pay attention when using them.) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| actor | str | Entity ID of the player who obtains the item | 
| secondaryActor | str | Entity ID of the player who gave the item. If there is no giver, this is an empty string | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the obtained item | 
| acquireMethod | int | For details on how to obtain items, see [ItemAcquisitionMethod](../Enumeration Value/ItemAcquisitionMethod.md) | 

- Return Value 

None 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ActorAcquiredItemServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: The event thrown by the server when the player obtains the item (some ways to obtain items will only trigger client events, and some ways to obtain items will only trigger server events. Pay attention to this when using them.) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| actor | str | Item player entity ID | 
| secondaryActor | str | Item giver player entity ID, if there is no giver, this is an empty string | 
| itemDict | dict | Item information dictionary of the acquired item | 
| acquireMethod | int | Method for acquiring items, see [ItemAcquisitionMethod Enumeration](../Enumeration Value/ItemAcquisitionMethod.md) for details | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring, for details, refer to <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ActorUseItemClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 


Trigger timing: The event thrown by the client when the player uses an item (special examples where this event is not triggered: 1) drinking milk; 2) using dye on a cauldron with water; 3) equipping armor on an armor stand) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the item used | 
| useMethod | int | Methods for using items, see [ItemUseMethodEnum Enumeration](../Enumeration Value/ItemUseMethodEnum.md) for details | 

- Return value 

None 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ActorUseItemServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: The event thrown by the server before the player uses the item to take effect (special examples of not taking this event: 1) drinking milk; 2) using dye on a cauldron with water; 3) equipping armor on an armor stand) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player entity id | 
| itemDict | dict | Item information dictionary of the item used | 
| useMethod | int | Method of using the item, see [ItemUseMethodEnum enumeration](../enumeration value/ItemUseMethodEnum.md) | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## AnvilCreateResultItemAfterClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Event thrown when the player clicks on the item synthesized by the anvil. 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| itemShowName | str | Display name of the synthesized item | 
| itemDict | dict | Item information dictionary of the synthesized item | 
| oldItemDict | dict | Item information dictionary of the item before synthesis (the first item in the anvil) | 
| materialItemDict | dict | Material information dictionary of the material used for synthesis href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> (the second item in the anvil) | 

- Return Value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ClientItemTryUseEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

The event thrown by the client when the player right-clicks and tries to use an item. You can cancel the use of the item by setting cancel to True. Note: If you need to cancel the use of an item, you need to set cancel to True in both ClientItemTryUseEvent and ServerItemTryUseEvent to cancel correctly. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the item used | 
| cancel | bool | Cancel the use of the item | 

- Return value 

None 

- Notes 
- ServerItemTryUseEvent/ClientItemTryUseEvent cannot cancel the behavior of using items on the block, such as using creature eggs, using buckets to pour/collect, using flint to ignite grass, etc.; if you want to cancel this behavior, please use ClientItemUseOnEvent and ServerItemUseOnEvent 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ClientItemUseOnEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Event thrown by the client when the player uses an item on the block. Note: If you need to cancel the use of the item, you need to set ret to True in both ClientItemUseOnEvent and ServerItemUseOnEvent to cancel it correctly. 

- Parameters


    | Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Player entity id | 
| itemDict | dict | Item information dictionary of the item used | 
| x | int | Block x coordinate value | 
| y | int | Block y coordinate value | 
| z | int | Block z coordinate value | 
| blockName | str | Block identifier | 
| blockAuxValue | int | Block additional value | 
| face | int | Click on the face of the block, refer to [Facing enumeration](../enumeration value/Facing.md) | 
| clickX | float | x-proportional position of the click point | 
| clickY | float | y-proportional position of the click point | 
| clickZ | float | z-proportional position of the click point | 
| ret | bool | Set to True to cancel the use of the item | 

- Return value 

None 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ClientShapedRecipeTriggeredEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the player synthesizes an item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| recipeId | str | recipe id, corresponding to the identifier field in the recipe json file | 

- Return value 

None 

## ContainerItemChangedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Container item change event


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int)/None | Container coordinates | 
| containerType | int | Container type, type meaning see: [Container type enumeration](../enumeration value/ContainerType.md) | 
| slot | int | Container slot | 
| dimensionId | int | Dimension id | 
| oldItemDict | dict | Old item, format reference <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| newItemDict | dict | New item, format reference <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 

- Return Value 

None 

- Notes 
- Changes in items in storage containers (boxes, shulker boxes), furnaces, brewing stands, dispensers, droppers, hoppers, cauldrons, record players, blast furnaces, and smokers will trigger this event 
- Workbenches, anvils, enchantment tables, looms, grinding wheels, stonecutters, cartography tables, and forging tables are synthetic containers and will not trigger this event. Such containers can monitor specific container item changes through UIContainerItemChangedServerEvent 
- The cauldron only triggers this event when dyes are used, and the slot is 2 
- The record player only triggers this event when a record is put into the hopper 

- Example 

```python 
import mod.server.extraServerApi as serverApi
from mod_log import logger as logger
# Listen to engine events
self.ListenForEvent(serverApi.GetEngineNamespace(),
                    serverApi.GetEngineSystemName(),
                    "ContainerItemChangedServerEvent",
                    self, self.OnContainerItemChangedServerEvent)

def OnContainerItemChangedServerEvent(self, args):
    playerId = args['playerId']
    logger.info("OnContainerItemChangedServerEvent args:%s", args)
    if args['containerType'] == serverApi.GetMinecraftEnum().ContainerType.SMOKER:
        print 'The smoker has changed'
```



## CraftItemOutputChangeServerEvent

<span style="display:inline;color:#ff5555">Server</span>

- describe

Triggered when the player takes a spawned item from a container 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| itemDict | dict | Generated items, format reference <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| screenContainerType | int | Current interface type, type meaning see: [Container Type Enumeration](../Enumeration Value/ContainerType.md) | 
| cancel | bool | Whether to cancel the generated item | 

- Return value 

None 

- Remarks 
- Support work blocks such as workbench, anvil, grinding wheel, etc. 
- screenContainerType = serverApi.GetMinecraftEnum().ContainerType.INVENTORY means taking items from the creative inventory or taking crafted items from the crafting bar 
- Cancel the creation of items through the cancel parameter, which can be used to prohibit plug-in item farming 
- Cannot take items from the creative inventory when cancel=True 
- Anvil cannot repair or rename items when cancel=True, but experience points will still be deducted 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
from mod_log import logger as logger 
# Listen for engine events 
self.ListenForEvent(serverApi.GetEngineNamespace(), 
serverApi.GetEngineSystemName(), 
"CraftItemOutputChangeServerEvent", 
self, self.OnCraftItemOutputChangeServerEvent) 

def OnCraftItemOutputChangeServerEvent(self, args): 
playerId = args['playerId'] 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
logger.info("OnCraftItemOutputChangeServerEvent args:%s", args) 
# Anvil trigger 
if args['screenContainerType'] == serverApi.GetMinecraftEnum().ContainerType.ANVIL: 
anvilInputItem = comp.GetOpenContainerItem(playerId,serverApi.GetMinecraftEnum().OpenContainerId.AnvilInputContainer,True) 
if anvilInputItem != None: 
# There is an item in the anvil input position. This event is triggered by taking out the anvil spawn 
if anvilInputItem['itenName'] != args['itemDict']['itemName']: 
# The input item and the spawned item are not of the same type. It may be cheating. Cancel the item spawn 
args['cancel'] = True 

``` 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 



## FurnaceBurnFinishedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Server furnace burning trigger event. Triggered when a furnace, blast furnace, or smoker burns an item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimensionId | int | Dimension id | 
| posX | float | Position x | 
| posY | float | Position y | 
| posZ | float | Position z | 
| itemDict | dict | Item's <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, when the new item is empty, this attribute is None | 

- Return value 

None 

## GrindStoneRemovedEnchantClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Event thrown when the player clicks on the item synthesized by the grinding wheel 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| oldItemDict | dict | Item before synthesis <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> (the first item in the grinding wheel) | 
| additionalItemDict | dict | Items used as synthesis materials <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> (the second item in the grinding wheel) | 
| newItemDict | dict | Synthesized items <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| exp | int | Experience returned for this synthesis | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Events">Part Events</a> 

## InventoryItemChangedClientEvent


<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Event thrown by the client when the player's backpack items change. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| slot | int | Backpack slot | 
| oldItemDict | dict | Items in the slot before the change, format reference <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| newItemDict | dict | Items in the slot after the change, format reference <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 

- Return value 

None 

- Notes 
- If the slot becomes empty, the item in the slot after the change is air 
- When triggered, the item in the slot is still the item before the change 
- The operations of moving, stacking, and unstacking items in the backpack will be triggered by multiple events and the order is uncertain. Please do not rely on the event triggering order when writing logic 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## InventoryItemChangedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Event thrown by the server when the player's backpack items change. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| slot | int | Backpack slot | 
| oldItemDict | dict | Items in the slot before the change, format reference <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| newItemDict | dict | Items in the slot after the change, format reference <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 

- Return value 

None 

- Remark

- If the slot becomes empty, the item in the slot after the change is air 
- When triggered, the item in the slot is still the item before the change 
- When the player enters the game, the items on his body will trigger this event 
- The operations of moving, stacking, and unstacking items in the backpack will be triggered by multiple events and the order is uncertain. Please do not rely on the event triggering order when writing logic 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ItemReleaseUsingClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger time: Release the item in use 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 
| durationLeft | float | remaining charging time (when the item lacks the "minecraft:maxduration" component, the remaining charging time is negative) | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the item used | 
| maxUseDuration | int | maximum charging duration | 
| cancel | bool | set to True to cancel, you need to cancel the server event [ItemReleaseUsingServerEvent](#itemreleaseusingserverevent) at the same time | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring, for details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ItemReleaseUsingServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: when releasing the item in use 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
| durationLeft | float | Remaining time of charging (when the item lacks the "minecraft:maxduration" component, the remaining time of charging is negative) | 
| itemDict | dict | The <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| maxUseDuration | int | Maximum charging time | 
| cancel | bool | Set to True to cancel, and the client event [ItemReleaseUsingClientEvent](#itemreleaseusingclientevent) needs to be canceled at the same time |


- Return value 

None 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ItemUseAfterServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

The event thrown by the server after the player uses the item. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Player entity id | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the item used | 

- Return value 

None 

- Remarks 
- Triggered after the action of using the item is performed. Some item use events (ActorUseItemServerEvent) that require power will be triggered later. For example, if you throw a trident, this event is triggered first, and then ActorUseItemServerEvent is triggered after it is thrown. 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ItemUseOnAfterServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

The event thrown by the server after the player uses an item on the opponent's block. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Player entity id | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the item used | 
| x | int | Block x coordinate value | 
| y | int | Block y coordinate value | 
| z | int | Block z coordinate value |

| face | int | Click on the face of the block, refer to [Facing enumeration](../enumeration value/Facing.md) | 
| clickX | float | x-proportional position of the click point | 
| clickY | float | y-proportional position of the click point | 
| clickZ | float | z-proportional position of the click point | 
| blockName | str | block identifier | 
| blockAuxValue | int | block additional value | 
| dimensionId | int | dimension id | 

- Return value 

None 

- Remarks 
- Triggered after ServerItemUseOnEvent and original item use event 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnCarriedNewItemChangedClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

This event is triggered when the item in hand changes; quantity changes will not be notified 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the item after switching | 

- Return value 

None 

## OnCarriedNewItemChangedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: This event is triggered when the player switches the main hand item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| oldItemDict | dict/None | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the old item. When the old item is empty, this attribute is None | 
| newItemDict | dict/None | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the new item. When the new item is empty, this attribute is None | 
| playerId | str | player entityId | 

- Return value 

None 

- Notes 
- Switching the same item with different durability will not trigger this event 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnItemPutInEnchantingModelServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: When the player puts an enchantable item on the enchantment table 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id, parameter type is str | 
| slotType | int | EnchantSlotType of the item placed by the player | 
| options | list | Enchantment table options | 
| change | bool | When True is passed in, the enchantment table options will be overwritten by the newly passed in options | 

- Return value 

None 

- Notes 
- options is a list containing three dicts. The format of a single dict is {'cost': 1, 'enchantData': [(1,1)], 'modEnchantData': [('custom_enchant, 1')]}, cost is the player level required to unlock the option, enchantData is the original enchantment data contained in the enchantment option, and modEnchantData is the custom enchantment data contained in the option. 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnNewArmorExchangeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: This event is triggered when the player switches armor 

- Parameters


    | Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| slot | int | Slot id | 
| oldArmorDict | dict/None | <a href="../../../mcguide/20-玩法开发/10-基本概念/1-我的世界基础概念.html#件信息辞典#件信息辞典">Item information dictionary</a> of old equipment. When the old item is empty, this attribute is None | 
| newArmorDict | dict/None | <a href="../../../mcguide/20-玩法开发/10-基本概念/1-我的世界基础概念.html#件信息辞典#件信息辞典">Item information dictionary</a> of new equipment. When the new item is empty, this attribute is None | 
| playerId | str | Player entityId | 

- Return value 

None 

- Notes 
- When the player logs in, each armor slot will trigger this event twice, the first time it is None and switches to the equipment on the body, and the second time both old and new are the equipment on the body. If the slot is empty, it triggers the event of switching from None to None twice. 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnOffhandItemChangedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: The event is triggered when the player switches the off-hand item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| oldItemDict | dict/None | The old item's <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a>, when the old item is empty, this attribute is None | 
| newItemDict | dict/None | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the new item, when the new item is empty, this attribute is None | 
| playerId | str | player entityId | 

- Return value 

None 

- Notes 
- When the original item slot is empty, the value of `oldItemName` is 'minecraft:air', and the rest of the fields of `oldItem` do not exist<br>When the original item is switched and the new item is empty, the parameter value is the same 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnPlayerActiveShieldServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 


Trigger timing: Events triggered by the player activating/deactivating the shield. Including the player holding the shield to enter the stealth state, and switching the shield in the stealth state (switching the same shield with different durability will not trigger) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player Id | 
| isActive | bool | True: try to activate, False: try to deactivate | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the shield item | 
| cancelable | bool | Whether it can be canceled. If the player switches the shield in stealth mode, it cannot be canceled | 
| cancel | bool | Whether to cancel this activation | 

- Return value 

None 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnPlayerBlockedByShieldAfterServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: Triggered after the player uses the shield to resist damage 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| sourceId | str | Damage source entity ID, "-1" is returned if there is no entity | 
| itemDict | dict | Shield item dictionary <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| damage | float | Damage value blocked | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Events">Part Events</a> 

## OnPlayerBlockedByShieldBeforeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: before the player uses a shield to block damage


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| sourceId | str | Damage source entity ID, return "-1" if no entity | 
| itemDict | dict | Shield item dictionary <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| damage | float | Damage value | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerDropItemServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: Triggered when the player drops an item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 
| itemEntityId | str | item entityId | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Parts Development.html#Parts Event">Parts Event</a> 

## PlayerTryDropItemClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger timing: Triggered when the player drops an item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| playerId | str | player id | 
| itemDict | dict | item dict | 
| cancel | bool | whether to cancel this operation | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ServerItemTryUseEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

The event thrown by the server when the player right-clicks and tries to use the item. Note: If you need to cancel the use of the item, you need to set cancel to True in both ClientItemTryUseEvent and ServerItemTryUseEvent to cancel it correctly.

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the item used | 
| cancel | bool | Set to True to cancel the use of the item | 

- Return value 

None 

- Notes 
- ServerItemTryUseEvent/ClientItemTryUseEvent cannot cancel the behavior of using items on the block, such as using creature eggs, using buckets to pour/collect, using flint to ignite grass, etc.; if you want to cancel this behavior, please use ClientItemUseOnEvent and ServerItemUseOnEvent 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ServerItemUseOnEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

The event thrown by the server before the player uses an item on the block. Note: If you need to cancel the use of the item, you need to set ret to True in both ClientItemUseOnEvent and ServerItemUseOnEvent to cancel it correctly. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| entityId | str | player entity id | 
| itemDict | dict | item information dictionary of the item used | 
| x | int | x coordinate value of the block | 
| y | int | y coordinate value of the block | 
| z | int | z coordinate value of the block | 
| blockName | str | identifier of the block | 
| blockAuxValue | int | additional value of the block | 
| face | int | face of the clicked block, refer to [Facing enumeration](../enumeration value/Facing.md) | 
| dimensionId | int | dimension id | 
| clickX | float | x proportional position of the clicked point | 
| clickY | float | y proportional position of the clicked point | 
| clickZ | float | z-proportional position of the click point | 
| ret | bool | Set to True to cancel the use of the item | 

- Return value 

None 

- Notes 
- When using native blocks, such as composters and other blocks with the "use" function, this event will not be triggered. When native blocks are added to the listener, ServerBlockUseEvent will be triggered. When you need to get the item used when the trigger is triggered, you can get the item in your hand through the item component, and the corresponding client event is the same. 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ServerPlayerTryTouchEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the player is about to pick up an item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player Id | 
| entityId | str | Item entity Id | 
| itemDict | dict | The touched item's <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| cancel | bool | Set to True to cancel this pickup | 
| pickupDelay | int | Reset the pickup CD of the item after canceling the pickup. Less than 15 frames will be regarded as 15 frames, and greater than or equal to 97813 frames will be regarded as unable to pick up | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ShearsUseToBlockBeforeServerEvent


<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: When an entity uses scissors on a block, the block with the scissors special effect will trigger this event in the server thread 

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
| entityId | str | Entity ID that triggers the shears effect. Currently, only players can trigger it. | 
| dimensionId | int | Dimension ID when the player triggers it | 
| cancelShears | bool | Whether to cancel the shears effect | 

- Return value 

None 

- Notes 
- Blocks that currently trigger this event: pumpkin, beehive 
- This event is triggered after ServerItemUseOnEvent. If the item use is canceled in ServerItemUseOnEvent, this event cannot be triggered 
- Like ServerItemUseOnEvent, this event is judged to be executed in tick, which means that if the shears effect is canceled, this event may be triggered multiple times (depending on how long the player presses the use key) 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## StartUsingItemClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Thrown when a player uses an item (currently only supports Bucket, Trident, RangedWeapon, Medicine, Food, Potion, Crossbow, ChemistryStick) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the item used | 

- Return value


    None 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## StopUsingItemClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Thrown when the player stops using an item (currently only supports Bucket, Trident, RangedWeapon, Medicine, Food, Potion, Crossbow, ChemistryStick) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the item used | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Events">Part Events</a> 

## UIContainerItemChangedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the synthesis container item changes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player entity id | 
| slot | int | container slot, meaning see: [Container Type Enumeration](../Enumeration Value/PlayerUISlot.md) | 
| oldItemDict | dict | old item, format reference <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| newItemDict | dict | generated item, format reference <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 

- Return value 

None 

- Remarks

- Crafting containers include workbenches, anvils, enchantment tables, looms, grinding wheels, stonecutters, cartography tables, and forging tables. This event is triggered when the input items change. 
- Different types of generated containers can be distinguished by container slots. 
- This event is not triggered when the generated slots of the synthesis container generate items. The generated items can be listened to through CraftItemOutputChangeServerEvent. 
- Changes in items in storage containers (boxes, shulker boxes), furnaces, brewing stands, dispensers, droppers, hoppers, cauldrons, record players, blast furnaces, and smokers will not trigger this event. Such containers can be listened to through ContainerItemChangedServerEvent. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
from mod_log import logger as logger 
# Listen for engine events 
self.ListenForEvent(serverApi.GetEngineNamespace(), 
serverApi.GetEngineSystemName(), 
"UIContainerItemChangedServerEvent", 
self, self.OnUIContainerItemChangedServerEvent) 

def OnUIContainerItemChangedServerEvent(self, args): 
playerId = args['playerId'] 
logger.info("OnUIContainerItemChangedServerEvent args:%s", args) 
if args['slot'] == serverApi.GetMinecraftEnum().PlayerUISlot.GrindstoneInput: 
print 'Grindstone input position changed' 
``` 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

