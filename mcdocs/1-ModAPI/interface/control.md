--- 
sidebarDepth: 1 
--- 
# Control 

# Index 

Including related interfaces for screen operations 

--- 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddPickBlacklist](Control.md#addpickblacklist) | <span style="display:inline;color:#7575f9">Client</span> | Add the blacklist when using the camera component to select an entity, that is, the entity will not be selected | 
| [ClearPickBlacklist](Control.md#clearpickblacklist) | <span style="display:inline;color:#7575f9">Client</span> | Clear the blacklist for selecting entities using the camera component | 
| [GetChosen](Control.md#getchosen) | <span style="display:inline;color:#7575f9">Client</span> | Get the entity or block information of the screen click position, usually used in conjunction with GetEntityByCoordEvent | 
| [GetChosenEntity](Control.md#getchosenentity) | <span style="display:inline;color:#7575f9">Client</span> | Get the entity id of the screen click position, usually used in conjunction with GetEntityByCoordEvent | 
| [GetHoldTimeThresholdInMs](Control.md#getholdtimethresholdinms) | <span style="display:inline;color:#7575f9">Client</span> | Get the long press judgment time, that is, how long the screen is pressed to trigger the long press operation | 
| [GetInputVector](Control.md#getinputvector) | <span style="display:inline;color:#7575f9">Client</span> | Get the input of the direction keys (moving the wheel) | 
| [GetTouchPos](control.md#gettouchpos) | <span style="display:inline;color:#7575f9">Client</span> | Get the screen coordinates of the click. You can listen to the TapBeforeClientEvent or TapOrHoldReleaseClientEvent events and call this API to get the click coordinates. | 
| [LockInputVector](Control.md#lockinputvector) | <span style="display:inline;color:#7575f9">Client</span> | Lock the input of the local player's direction keys (movement wheel), allowing the local player to continue moving in the specified direction and no longer be affected by the player's input | 
| [PickFacing](Control.md#pickfacing) | <span style="display:inline;color:#7575f9">Client</span> | Get the entity or block selected by the crosshair | 
| [SetCanAll](Control.md#setcanall) | <span style="display:inline;color:#7575f9">Client</span> | Set SetCanMove, SetCanJump, SetCanAttack, SetCanWalkMode, SetCanPerspective, SetCanPause, SetCanChat, SetCanScreenShot, SetCanOpenInv, SetCanDrag, SetCanInair at the same time | 
| [SetCanAttack](control.md#setcanattack) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to respond to attacks | 
| [SetCanChat](control.md#setcanchat) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to respond to chat buttons | 
| [SetCanDrag](control.md#setcandrag) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to respond to screen dragging | 
| [SetCanInair](control.md#setcaninair) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to respond to the ascend and descend buttons (the three buttons in the lower right corner when flying in the air) | 
| [SetCanJump](Control.md#setcanjump) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to respond to jumping (and floating in water) | 
| [SetCanMove](Control.md#setcanmove) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to respond to movement | 
| [SetCanOpenInv](Control.md#setcanopeninv) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to respond to the open backpack button | 
| [SetCanPause](Control.md#setcanpause) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to respond to the pause button | 
| [SetCanPerspective](control.md#setcanperspective) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to respond to the switch perspective | 
| [SetCanScreenShot](control.md#setcanscreenshot) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to respond to the screenshot button | 
| [SetCanWalkMode](control.md#setcanwalkmode) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to respond to the switch walking mode | 
| [SetDeviceVibrate](control.md#setdevicevibrate) | <span style="display:inline;color:#7575f9">Client</span> | Set device vibration | 
| [SetHoldTimeThreshold](control.md#setholdtimethreshold) | <span style="display:inline;color:#7575f9">Client</span> | Set the long press judgment time, that is, how long you press the screen to trigger a long press operation | 
| [SetMoveLock](control.md#setmovelock) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to lock movement. In fact, it is whether to respond to the cross key and remote sensing operations. | 
| [SetShowRideUI](control.md#setshowrideui) | <span style="display:inline;color:#ff5555">Server</span> | Set whether to display the horse UI interface | 
| [SimulateTouchWithMouse](control.md#simulatetouchwithmouse) | <span style="display:inline;color:#7575f9">Client</span> | Simulate using the mouse to control the UI (PC F11 shortcut key) | 
| [UnlockInputVector](control.md#unlockinputvector) | <span style="display:inline;color:#7575f9">Client</span> | Unlock the input of the local player's direction keys (moving the wheel) | 

## AddPickBlacklist 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Add a blacklist when selecting entities using the camera component, that is, the entity will not be selected.


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
# Add blacklist 
comp.AddPickBlacklist(entityId) 
``` 

## ClearPickBlacklist 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Clear the blacklist of entities selected using the camera component 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
# Clear all entities in the blacklist

comp.ClearPickBlacklist() 
``` 

## GetChosen 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Get the entity or block information of the screen click position, usually used in conjunction with GetEntityByCoordEvent 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Data of the selected target, see the notes of [PickFacing interface](control.md#pickfacing) for details | 

- Notes 
- Currently only in the first-person perspective can it be accurately obtained 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# Get the entityId of the click position when the player clicks the screen 
class MyClientSystem(ClientSystem): 
def __init__(self, namespace, name): 
ClientSystem.__init__(self, namespace, name) 
self.ListenForEvent('Minecraft', 'Engine', 'GetEntityByCoordEvent', self, self.click) 
def click(self, args): 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
pickData = comp.GetChosen() 
``` 

## GetChosenEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 


- Description 

Get the entity id of the screen click position, usually used with GetEntityByCoordEvent 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Entity id | 

- Notes 
- Currently only accurate in the first-person perspective 

- Example 

```python 
# Get the entityId of the click position when the player clicks the screen 
import mod.client.extraClientApi as clientApi 
class MyClientSystem(ClientSystem): 
def __init__(self, namespace, name): 
ClientSystem.__init__(self, namespace, name) 
self.ListenForEvent('Minecraft', 'Engine', 'GetEntityByCoordEvent', self, self.click) 
def click(self, args): 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
entityId = comp.GetChosenEntity() 
``` 

## GetHoldTimeThresholdInMs 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Get the long press judgment time, that is, how long to press the screen to trigger the long press operation 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| int | Time, in milliseconds. Default is 400 | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
timeMs = comp.GetHoldTimeThresholdInMs() 
``` 

## GetInputVector 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorMotionCompClient.ActorMotionComponentClient 

- Description 

Get the input of the arrow keys (movement wheel) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Returns a unit vector, the first term of the vector is the magnitude to the left, the second term is the magnitude to the forward | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateActorMotion(localPlayerId) 
left, up = comp.GetInputVector() 
``` 

## GetTouchPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description


Get the screen coordinates of the click. You can listen to the TapBeforeClientEvent or TapOrHoldReleaseClientEvent event and call this API to get the click coordinates. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Screen coordinates | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
def GetTouchPosTest(): 
touchX, touchY = clientApi.GetTouchPos() 
``` 

## LockInputVector 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorMotionCompClient.ActorMotionComponentClient 

- Description 

Lock the input of the local player's direction keys (movement wheel), so that the local player can continue to move in the specified direction and will no longer be affected by the player's input 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| inputVector | tuple(float,float) | Input vector, the first item controls the size to the left, and the second item controls the size to the front. When (0, 0) is passed in, the player will be forced to stay in place and not allowed to move. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the lock is successful, True: success False: failure | 

- Notes 
- The passed in vector will be converted to a unit vector, so passing in (10, 0) has the same effect as passing in (0.1, 0) 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
# Make the player move forward and left continuously 
localPlayerId = clientApi.GetLocalPlayerId() 
rotComp = clientApi.GetEngineCompFactory().CreateRot(localPlayerId) 
motionComp = clientApi.GetEngineCompFactory().CreateActorMotion(localPlayerId) 
motionComp.LockInputVector((1, 1)) 
``` 

## PickFacing 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Get the entity or block selected by the crosshair 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Data of the selected target, see the notes for details | 

- Notes 
- When the selected target is an entity, the return value is: 
```python 
{ 
"type": "Entity", 
"entityId": entityId 
} 
``` 
- When the selected target is a block, the return value is: 
```python 
{ 
"type": "Block", 
"x": x, 
"y": y, 
"z": z, 
"face": face 
} 
``` 
- When no target is selected, the return value is:

```python 
{ 
"type": "None" 
} 
``` 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
pickData = comp.PickFacing() 
``` 

## SetCanAll 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Sets SetCanMove, SetCanJump, SetCanAttack, SetCanWalkMode, SetCanPerspective, SetCanPause, SetCanChat, SetCanScreenShot, SetCanOpenInv, SetCanDrag, SetCanInair at the same time 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| all | bool | True means all responses | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Set before setting other properties, otherwise the settings before all will be overwritten 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Set all to non-response 
comp.SetCanAll(False) 
``` 




## SetCanAttack 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Set whether to respond to attacks 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| attack | bool | True is attackable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Do not respond to attacks 
comp.SetCanAttack(False) 
``` 
## SetCanChat 
<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Set whether to respond to the chat button 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| chat | bool | True means the chat page can be opened |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Do not respond to the chat button 
comp.SetCanChat(False) 
``` 

## SetCanDrag 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Set whether to respond to screen dragging 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| drag | bool | True means the screen can be dragged | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Do not respond to screen dragging 
comp.SetCanDrag(False) 
``` 




## SetCanInair 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Set whether to respond to the up and down buttons (the three buttons in the lower right corner when flying in the air) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| inair | bool | True is clickable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Do not respond to air control buttons 
comp.SetCanInair(False) 
``` 
## SetCanJump 
<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Set whether to respond to jumping (and floating in water) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| jump | bool | True means jumping | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Do not respond to jump 
comp.SetCanJump(False) 
``` 

## SetCanMove 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Set whether to respond to movement 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| move | bool | True is movable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Difference from SetMoveLock: Calling SetCanMove will clear the current Input Vector. For example, if the player keeps pressing the forward key, calling SetCanMove(False) will stop immediately, but calling SetMoveLock(True) will not. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Do not respond to movement 
comp.SetCanMove(False) 
```



## SetCanOpenInv 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Set whether to respond to the open backpack button 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| open | bool | True means the backpack can be opened | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Do not respond to the backpack opening button 
comp.SetCanOpenInv(False) 
``` 
## SetCanPause 
<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Set whether to respond to the pause button 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| pause | bool | True means you can open the pause page | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Do not respond to the pause button 
comp.SetCanPause(False) 
``` 

## SetCanPerspective 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Set whether to respond to switching perspectives 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| persp | bool | True is switchable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Do not respond to switching perspectives 
comp.SetCanPerspective(False) 
``` 




## SetCanScreenShot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Set whether to respond to the screenshot button 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| shot | bool | True means screenshot can be taken | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Do not respond to the screenshot button 
comp.SetCanScreenShot(False) 
``` 
## SetCanWalkMode 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.operationCompClient.OperationCompClient 

- Description 
Set whether to respond to switching walking mode 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| walkmode | bool | True is switchable |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Do not respond to switching walking mode 
comp.SetCanWalkMode(False) 
``` 

## SetDeviceVibrate 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.deviceCompClient.DeviceCompClient 

- Description 

Set device vibration 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| milliSeconds | int | Vibration time (unit: milliseconds) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Set the time interval to [1,5000] milliseconds. If the milliSeconds parameter is greater than this interval, it will be set to 5000 milliseconds, and if it is less than this interval, it will be set to 1 millisecond. 
- The time from the last vibration to the end of the call cannot be less than 2 seconds. If it is less than 2 seconds, this setting will fail. 
- Possible reasons for failure to set vibration (function returns False): less than 2 seconds from the last vibration, the current state is already vibrating, the device does not support vibration, etc. 
- Even if the function returns True, it may not actually vibrate because of incorrect judgment of whether the device supports vibration, device permissions prohibiting vibration, etc. 
- The current version does not support vibration for IOS devices 

- Example 

```python

import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateDevice(entityId) 
comp.SetDeviceVibrate(1000) 
``` 
## SetHoldTimeThreshold 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.operationCompClient.OperationCompClient 
- Description 
Set the long press judgment time, that is, how long to press the screen to trigger the long press operation 
- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| time | int | Time, in milliseconds. The default value is 400 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
comp.SetHoldTimeThreshold(100) 
``` 

## SetMoveLock 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.operationCompClient.OperationCompClient 

- Description 

Set whether to lock the movement. In fact, it is whether to respond to the operation of the cross key and remote sensing. 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| movelock | bool | True is locked | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Difference from SetCanMove: Calling SetCanMove will clear the current Input Vector. For example, if the player keeps pressing the forward key, calling SetCanMove(False) will stop immediately, but calling SetMoveLock(True) will not. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateOperation(levelId) 
# Lock movement 
comp.SetMoveLock(True) 
``` 

## SetShowRideUI 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.rideCompServer.RideCompServer 

- Description 

Set whether to display the horse UI interface 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| tamedEntityId | str | Rideable creature id | 
| isShowUI | bool | Whether to show UI | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRide(entityId) 
comp.SetShowRideUI(entityId,False) 
``` 

## SimulateTouchWithMouse 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Simulate using the mouse to control the UI (PC F11 shortcut key) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| touch | bool | True: enter mouse mode, False: exit mouse mode | 

- Return value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| bool | Simulation Result | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
comp.SimulateTouchWithMouse(True) 
``` 

## UnlockInputVector 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorMotionCompClient.ActorMotionComponentClient 

- Description 

Unlock the input of the local player's arrow keys (movement wheel) 


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether unlocking is successful, True: success False: failure | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# Unlock the local player's direction key (movement wheel) input locked using LockInputVector 
comp = clientApi.GetEngineCompFactory().CreateActorMotion(localPlayerId) 
motionComp.UnlockInputVector() 
``` 

