--- 
sidebarDepth: 1 
--- 
# UI 

# Index 

| Event | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [ClientChestCloseEvent](UI.md#clientchestcloseevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when the chest interface is closed, including small chests, merged large chests and ender dragon chests | 
| [ClientChestOpenEvent](UI.md#clientchestopenevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when the chest interface is opened, including small chests, merged large chests and ender dragon chests | 
| [ClientPlayerInventoryCloseEvent](UI.md#clientplayerinventorycloseevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when closing the inventory interface | 
| [ClientPlayerInventoryOpenEvent](UI.md#clientplayerinventoryopenevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when opening the inventory interface | 
| [GridComponentSizeChangedClientEvent](UI.md#gridcomponentsizechangedclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Trigger timing: Triggered when the number of grids in the UI grid component changes | 
| [OnItemSlotButtonClickedEvent](UI.md#onitemslotbuttonclickedevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when clicking the item slots in the shortcut bar and backpack bar | 
| [PlayerChatButtonClickClientEvent](UI.md#playerchatbuttonclickclientevent) | <span style="display:inline;color:#7575f9">Client</span> | The event thrown by the client when the player clicks the chat button or the Enter key to trigger the call-out chat window | 
| [PlayerInventoryOpenScriptServerEvent](UI.md#playerinventoryopenscriptserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when a client opens the inventory interface | 
| [PopScreenEvent](UI.md#popscreenevent) | <span style="display:inline;color:#7575f9">Client</span> | Screen removal trigger | 
| [PushScreenEvent](UI.md#pushscreenevent) | <span style="display:inline;color:#7575f9">Client</span> | Screen creation trigger | 
| [UiInitFinished](UI.md#uiinitfinished) | <span style="display:inline;color:#7575f9">Client</span> | UI initialization framework is completed, you can create UI at this time | 
| [UrgeShipEvent](UI.md#urgeshipevent) | <span style="display:inline;color:#ff5555">Server</span> | This event is triggered when the player clicks the mall urges shipment button | 
# UI 

## ClientChestCloseEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the box interface is closed, including small boxes, merged large boxes and ender dragon boxes 

- Parameters 

None 

- Return value 

None 

## ClientChestOpenEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the chest interface is opened, including small chests, merged large chests and ender dragon chests 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| x | int | Box position x value | 
| y | int | Box position y value | 
| z | int | Box position z value | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ClientPlayerInventoryCloseEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when closing the inventory interface 

- Parameters 

None 

- Return value 

None 

## ClientPlayerInventoryOpenEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when opening the inventory interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isCreative | bool | Is it the creative mode inventory interface | 
| cancel | bool | Cancel opening the inventory interface | 

- Return value 


None 

## GridComponentSizeChangedClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger time: Triggered when the number of grids in the UI grid component changes 

- Parameters 

None 

- Return value 

None 

## OnItemSlotButtonClickedEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when clicking the item slots in the shortcut bar and backpack bar 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| slotIndex | int | Number of the item slot clicked | 

- Return value 

None 

## PlayerChatButtonClickClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

The event thrown by the client when the player clicks the chat button or the Enter key to trigger the call-out chat window 


- Parameters 

None 

- Return value 

None 

## PlayerInventoryOpenScriptServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when a client opens the inventory interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Unique ID of the player entity corresponding to the client | 
| isCreative | bool | Whether it is the creative mode backpack interface | 

- Return value 

None 

- Remarks 
- You can listen to this event to determine whether the client has opened the creative backpack 

Directly declare a function with the same name in the part to complete the listening. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PopScreenEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Screen removal trigger 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| screenName | str | UI name | 

- Return value


None 

## PushScreenEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Screen creation trigger 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| screenName | str | UI name | 

- Return value 

None 

## UiInitFinished 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

UI initialization framework is completed, you can create UI at this time 

- Parameters 

None 

- Return value 

None 

- Notes 
- After switching dimensions, the UI will be reinitialized and the event will be triggered 

## UrgeShipEvent 

<span style="display:inline;color:#ff5555">Server</span> 


- Description 

This event is triggered when the player clicks the button to urge delivery in the mall 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 

- Return value 

None 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Parts Development.html#Parts Event">Parts Event</a> 

