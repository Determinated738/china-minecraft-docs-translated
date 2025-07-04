--- 
sidebarDepth: 1 
--- 
# PartBase 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
SdkInterface <|-- PartBase 
link SdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html" 
TransformObject <|-- PartBase 
link TransformObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E5%8F%98%E6%8D%A2%E5%AF%B9%E8%B1%A1TransformObject.html"
GameObject <|-- TransformObject
link GameObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1GameObject.html" 
PartBase: Parts 
SdkInterface: SDK interface package 
SdkInterface: (click to jump) 
TransformObject: Transform object 
TransformObject: (click to jump) 
GameObject: Game object 
GameObject: (click to jump) 
``` 

- Description 

PartBase (part base class) can be bound to parts, and parts can be attached to presets to realize the assembly of presets with logic. All custom parts need to inherit PartBase, and most of the code under the preset system needs to be written in custom parts. Note that custom parts can only take effect if they are attached to the preset and instantiated in the game. 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| tickEnable | str | Whether to enable part tick | 
| replicated | list | List of fields to enable network replication | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [InitClient](#initclient) | <span style="display:inline;color:#7575f9">Client</span> | Part object initialization entry of the client | 
| [InitServer](#initserver) | <span style="display:inline;color:#ff5555">Server</span> | Part object initialization entry of the server | 
| [TickClient](#tickclient) | <span style="display:inline;color:#7575f9">Client</span> | Logical driver entry of the client's part object | 
| [TickServer](#tickserver) | <span style="display:inline;color:#ff5555">Server</span> | Logical driver entry of the server's part object | 
| [UnloadClient](#unloadclient) | <span style="display:inline;color:#7575f9">Client</span> | Logical unloading entry of the client's part object |

| [UnloadServer](#unloadserver) | <span style="display:inline;color:#ff5555">Server</span> | Server-side part object unloading logic entry | 
| [DestroyClient](#destroyclient) | <span style="display:inline;color:#7575f9">Client</span> | Client-side part object destruction logic entry | 
| [DestroyServer](#destroyserver) | <span style="display:inline;color:#ff5555">Server</span> | Server-side part object destruction logic entry | 
| [CanAdd](#canadd) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Determine whether the part can be attached to the specified parent node | 
| [GetTickCount](#gettickcount) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the current frame number | 
| [LogDebug](#logdebug) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Print msg % args debug log, only valid for PC development kit | 
| [LogInfo](#loginfo) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Print msg % args message log | 
| [LogError](#logerror) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Print msg % args error log | 
| [GetGameObjectById](#getgameobjectbyid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the game object with the specified object ID | 
| [GetGameObjectByEntityId](#getgameobjectbyentityid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the game object with the specified entity ID | 
| [GetLoadedPlayers](#getloadedplayers) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the ID list of all players on the server | 
| [GetPlayerObject](#getplayerobject) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the player object | 
| [GetEntityObject](#getentityobject) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the entity object | 
| [GetEffectObject](#geteffectobject) | <span style="display:inline;color:#7575f9">Client</span> | Get the special effect object | 
| [CreateEffectPreset](#createeffectpreset) | <span style="display:inline;color:#7575f9">Client</span> | Create the special effect object | 
| [CreateTextboardPreset](#createtextboardpreset) | <span style="display:inline;color:#7575f9">Client</span> | Create the text panel preset object | 
| [ListenForEvent](#listenforevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Listen for the specified event | 
| [UnListenForEvent](#unlistenforevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Unlisten for specified events | 
| [ListenForEngineEvent](#listenforengineevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Unlisten for specified engine events | 
| [UnListenForEngineEvent](#unlistenforengineevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Unlisten for specified engine events | 
| [CreateEventData](#createeventdata) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create custom event data. eventData is used to send events. The created eventData can be understood as a dict, which can be nested with dict, list and basic data types, but does not support tuple | 
| [BroadcastEvent](#broadcastevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Broadcast events, universal to both ends | 
| [BroadcastPresetSystemEvent](#broadcastpresetsystemevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Broadcast to preset system | 
| [NotifyToServer](#notifytoserver) | <span style="display:inline;color:#7575f9">Client</span> | Notify the server to trigger the event | 
| [NotifyToClient](#notifytoclient) | <span style="display:inline;color:#ff5555">Server</span> | Notify the specified client to trigger the event | 
| [BroadcastToAllClient](#broadcasttoallclient) | <span style="display:inline;color:#ff5555">Server</span> | Notify all clients to trigger the event | 
| [ListenSelfEvent](#listenselfevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Listen for events from yourself | 
| [UnListenSelfEvent](#unlistenselfevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Unlisten events from own | 
| [ListenPartEvent](#listenpartevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Unlisten events from specified parts | 
| [UnListenPartEvent](#unlistenpartevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Unlisten events from specified parts | 
| [ListenPresetSystemEvent](#listenpresetsystemevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Listen to events from the preset system | 
| [UnListenPresetSystemEvent](#unlistenpresetsystemevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Unlisten to events from the preset system | 
| [DestroyStoryLines](#destroystorylines) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Manually destroy part blueprints | 
| [GetSelf](#getself) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the part itself | 
| [GetApi](#getapi) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Returns the SDK API modules that the current object can use | 
| [IsPlayerSneaking](#isplayersneaking) | <span style="display:inline;color:#ff5555">Server</span> | Whether to sneak | 
| [GetPlayerHunger](#getplayerhunger) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's hunger and display it on the UI hunger progress bar. The initial value is 20, that is, each drumstick represents 2 hunger points. **Saturation**: The player's current saturation, the initial value is 5, and the maximum value is always the player's current hunger. This value directly affects the player's **hunger**. <br>1) Increase method: Eat food. <br>2) Decrease method: Each time a **consumption event** is triggered, the value decreases by 1. If the value is not greater than 0, directly reduce the player's **hunger** by 1. | 
| [SetPlayerHunger](#setplayerhunger) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's hunger. | 

## InitClient 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.PartBase.PartBase 

- Description 


Part object initialization entry of the client 

- Parameters 

None 

- Return value 

None 

## InitServer 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Part object initialization entry of the server 

- Parameters 

None 

- Return value 

None 

## TickClient 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Part object logic driver entry of the client 

- Parameters 

None 

- Return value 

None 




## TickServer 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Logical driver entry of part object on server 

- Parameters 

None 

- Return value 

None 

## UnloadClient 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Logical entry of part object unloading on client 

- Parameters 

None 

- Return value 

None 

## UnloadServer 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 


The logical entry point for unloading part objects on the server side 

- Parameters 

None 

- Return value 

None 

## DestroyClient 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

The logical entry point for destroying part objects on the client side 

- Parameters 

None 

- Return value 

None 

## DestroyServer 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

The logical entry point for destroying part objects on the server side 

- Parameters 

None 

- Return value 

None 




## CanAdd 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Determine whether a part can be attached to a specified parent node 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| parent | PresetBase | Parent preset to be attached | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | When attachment is not allowed, return the corresponding error prompt | 

## GetTickCount 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Get the current frame number 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Current frame number | 

## LogDebug 


<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Print msg % args debug log, only valid for PC development kit 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| msg | str | Format string to print | 
| *args | list(object) | Format parameter list | 

- Return value 

None 

- Example 

```python 
self.LogDebug(“self.isClient: %s”, self.isClient) 
``` 

## LogInfo 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Print msg % args message log 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| msg | str | Format string to print | 
| *args | list(object) | Format parameter list | 

- Return value 

None 

- Example 


```python 
self.LogInfo("self.isClient: %s", self.isClient) 
``` 

## LogError 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Print msg % args error log 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| msg | str | Format string to print | 
| *args | list(object) | Format parameter list | 

- Return value 

None 

- Example 

```python 
self.LogError(“self.isClient: %s”, self.isClient) 
``` 

## GetGameObjectById 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Get the game object of the specified object ID 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | int | Specified object ID |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TransformObject | Returns the game object if successful, returns None if failed | 

- Example 

```python 
obj = self.GetGameObjectById(0) 
``` 

## GetGameObjectByEntityId 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Get the game object of the specified entity ID 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Specified entity ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TransformObject | Returns the game object if successful, returns None if failed | 

- Example 

```python 
obj = self.GetGameObjectByEntityId(0) 
``` 

## GetLoadedPlayers 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase


- Description 

Get the ID list of all players on the server 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | List of all player IDs | 

## GetPlayerObject 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Get player object 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PlayerObject | Returns the player object if successful, returns None if failed | 

- Example 

```python 
player = self.GetPlayerObject(playerId) 
``` 

## GetEntityObject 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span>


method in Preset.Model.PartBase.PartBase 

- Description 

Get entity object 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str | Specified entity ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| EntityObject | Returns entity object if successful, None if failed | 

- Example 

```python 
entity = self.GetEntityObject(entityId) 
``` 

## GetEffectObject 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Get the special effect object 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| effectId | int | Special effect ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| EffectObject | Returns the special effect object if successful, and None if failed | 

- Example


```python 
effect = self.GetEffectObject(effectId) 
``` 

## CreateEffectPreset 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Create special effect object 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| resource | str | Special effect resource json | 
| pos | tuple(float,float,float) | Special effect position | 
| rotation | tuple(float,float,float) | Special effect rotation | 
| scale | tuple(float,float,float) | Special effect scaling | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| EffectPreset | Returns the effect object if successful, and None if failed | 

- Example 

```python 
# Play the specified effect at a certain entity position 
effect = self.CreateEffectPreset("effects/xxx", self.GetEntityPos(entityId)) 
``` 

## CreateTextboardPreset 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Create a text panel preset object


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| text | str | Text display content | 
| textColor | tuple(float,float,float,float) | RGBA value of text color, range 0-1 | 
| boardColor | tuple(float,float,float,float) | Optional parameter, default None, set to black, RGBA value of board color, range 0-1 | 
| pos | tuple(float,float,float) | Optional parameter, default (0, 0, 0) Generate text panel position | 
| faceCamera | bool | Whether to always face the camera, default is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TextboardPreset | Returns the text panel object if successful, and None if failed | 

- Example 

```python 
# Generate a text panel preset at a certain location 
textboard = self.CreateTextboardPreset('Hello', (0.5, 0.4, 0.3, 0.8)) 
``` 

## ListenForEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Listen for the specified event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| namespace | str | namespace | 
| systemName | str | event system name | 
| eventName | str | event name | 
| instance | object | instance | 
| func | object | function | 
| priority | str | priority | 

- return value 

none




## UnListenForEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Unlisten for the specified event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| namespace | str | Namespace | 
| systemName | str | Event system name | 
| eventName | str | Event name | 
| instance | object | Instance | 
| func | object | Function | 
| priority | str | Priority | 

- Return value 

None 

## ListenForEngineEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Listen to the specified engine event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | Event name | 
| instance | object | Instance | 
| func | object | Function | 
| priority | str | Priority | 

- Return value


None 

## UnListenForEngineEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Unlisten for the specified engine event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | Event name | 
| instance | object | Instance | 
| func | object | Function | 
| priority | str | Priority | 

- Return value 

None 

## CreateEventData 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Create custom event data, eventData is used to send events. The created eventData can be understood as a dict, which can be nested with dict, list and basic data types, but does not support tuple 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Event data | 




## BroadcastEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Broadcast event, common to both ends 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | Event name | 
| eventData | object | Event data | 

- Return value 

None 

## BroadcastPresetSystemEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Broadcast to preset system 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | Event name | 
| eventData | object | Event data | 

- Return value 

None 

## NotifyToServer 


<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Notify the server to trigger an event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | Event name | 
| eventData | object | Event data | 

- Return value 

None 

## NotifyToClient 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Notify the specified client to trigger an event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player ID | 
| eventName | str | event name | 
| eventData | object | event data | 

- Return value 

None 

## BroadcastToAllClient 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase


- Description 

Notification refers to all client trigger events 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | Event name | 
| eventData | object | Event data | 

- Return value 

None 

## ListenSelfEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Listen for events from yourself 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | event name | 
| target | object | target | 
| func | object | callback function | 

- return value 

none 

## UnListenSelfEvent 

<span style="display:inline;color:#7575f9">client</span>/<span style="display:inline;color:#ff5555">server</span> 

method in Preset.Model.PartBase.PartBase 

- description 


Unlisten to events from itself 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | Event name | 
| target | object | Target | 
| func | object | Callback function | 

- Return value 

None 

## ListenPartEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Listen to events from specified parts 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| partId | int | ID of the specified part | 
| eventName | str | event name | 
| target | object | target | 
| func | object | callback function | 

- Return value 

None 

## UnListenPartEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Unlisten events from the specified part


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| partId | int | ID of the specified part | 
| eventName | str | Event name | 
| target | object | Target | 
| func | object | Callback function | 

- Return value 

None 

## ListenPresetSystemEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Listen for events from the preset system 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | event name | 
| target | object | target | 
| func | object | callback function | 

- Return value 

None 

## UnListenPresetSystemEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Unlisten events from the preset system 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | Event name | 
| target | object | Target | 
| func | object | Callback function | 

- Return value 

None 

## DestroyStoryLines 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Manually destroy part blueprint 

- Parameters 

None 

- Return value 

None 

## GetSelf 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PartBase.PartBase 

- Description 

Get the part itself 

- Parameters 

None 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PartBase | Part itself | 

## GetApi 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Returns the SDK API module that can be used by the current object 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| extraClientApi or extraServerApi | Returns the SDK API module that can be used by the current object | 

## IsPlayerSneaking 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Whether sneaking 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether sneaking | 


- Example 

```python 
self.IsPlayerSneaking(playerId) 
``` 

## GetPlayerHunger 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the player's hunger and display it on the UI hunger progress bar. The initial value is 20, that is, each chicken leg represents 2 hungers. **Saturation**: The player's current saturation, the initial value is 5, and the maximum value is always the player's current hunger. This value directly affects the player's **hunger**. <br>1) Increase method: Eat food. <br>2) Decrease method: Every time a **consumption event** is triggered, the value decreases by 1. If the value is not greater than 0, directly reduce the player's **hunger** by 1. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Player id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Player hunger | 

- Example 

```python 
self.GetPlayerHunger(playerId) 
``` 

## SetPlayerHunger 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the player's hunger. 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Player ID | 
| value | float | Hunger | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetPlayerHunger(playerId, 10) 
``` 

