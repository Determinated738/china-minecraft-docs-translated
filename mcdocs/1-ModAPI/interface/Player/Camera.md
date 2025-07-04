--- 
sidebarDepth: 1 
--- 
# Camera 

## DepartCamera 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Detach the player from the camera 

- Parameters 

None 

- Return value 

None 

- Notes 
- After detaching, you can see the player's surroundings, and the direction the player is facing no longer changes with the camera rotation when rotating the camera. Note that when riding a boat after detaching the camera, the lock_rider_rotation field in the boat component minecraft:rideable will lose its effect. In addition, when riding a horse or other creature, after detaching the camera, the player's direction no longer rotates with the camera, so you cannot turn while riding, so please note this. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# Third person lock perspective example 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.DepartCamera() 
comp.LockModCameraYaw(1) # Lock left and right perspectives 
comp.LockModCameraPitch(1) # Lock up and down perspectives 
comp.SetCameraOffset((0, 0, 15)) 
comp.SetCameraRot((45.0, 0.0)) 
``` 

## GetCameraAnchor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Get the camera anchor point


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Anchor offset | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.GetCameraAnchor() 
``` 

## GetCameraOffset 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Get the camera offset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | offset | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.GetCameraOffset() 
``` 




## GetCameraPitchLimit 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Get the camera's upper and lower angle limit values 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Upper and lower angle limit values | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.GetCameraPitchLimit() 
``` 

## GetCameraRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Get the camera's rotation direction 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Rotation direction |


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
rot = comp.GetCameraRot() 
``` 

## GetForward 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Returns the camera's forward direction 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Forward direction | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.GetForward() 
``` 
## GetFov 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.cameraCompClient.CameraComponentClient 
- Description 
Get the field of view size


- Parameters 

None 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| float | The field of view in the video settings, in degrees | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
fov = comp.GetFov() 
``` 

## GetFpHeight 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Get the camera height offset in the first-person perspective of the local player in the current state. It will be different when swimming, gliding and in normal state 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Height offset | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
heightOffset = comp.GetFpHeight() 
``` 




## GetPerspective 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerViewCompClient.PlayerViewCompClient 

- Description 

Get the current perspective mode 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | 0: first-person perspective; 1: third-person perspective; 2: front-view third-person perspective | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayerView(entityId) 
persp = comp.GetPerspective() 
``` 

## GetPosition 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Returns the center of the camera 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Camera center position |


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.GetPosition() 
``` 

## IsModCameraLockPitch 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Whether to lock the up and down angle of the camera 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to lock | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.IsModCameraLockPitch() 
``` 
## IsModCameraLockYaw 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.cameraCompClient.CameraComponentClient 
- Description 
Whether to lock the left and right angles of the camera


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Locked or not | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.IsModCameraLockYaw() 
``` 

## LockCamera 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Lock the camera 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| lockPos | tuple(float,float,float) | World coordinates | 
| lockRot | tuple(float,float) | Camera angle (pitch and yaw) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- When locking the camera, only the screen angle is locked, and the player can still move 

- Example 

```python

import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
# Fix the camera at (0, 6, 0) and look down 30 degrees, facing the positive direction of the world z-axis 
comp.LockCamera((0, 6, 0), (30, 0)) 
``` 

## LockModCameraPitch 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Lock the up and down angle of the camera (effective in third-person view, the view angle cannot be adjusted up and down after locking) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| enable | int | 1: lock 0: unlock | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.LockModCameraPitch(1) 
``` 

## LockModCameraYaw 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Lock the left and right angles of the camera (effective in third-person perspective, the viewing angle cannot be adjusted left and right with the mouse after locking) 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| enable | int | 1: lock 0: unlock | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.LockModCameraYaw(1) 
``` 

## LockPerspective 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerViewCompClient.PlayerViewCompClient 

- Description 

Lock the player's perspective mode 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| lock | int | 0: first-person perspective; 1: third-person perspective; 2: front-view third-person perspective Other values: unlock | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the lock is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayerView(entityId)
comp.LockPerspective(1)

``` 

## ResetCameraBindActorId 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Rebind the camera back to the protagonist 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.ResetCameraBindActorId() 
``` 

## SetCameraAnchor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Set the camera anchor point. Currently only supports height. Other dimensions are invalid 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| offset | tuple(float,float,float) | Anchor point offset | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Unlike SetCameraOffset, this interface changes the center position of the camera's orbit. It is effective for both first-person and third-person modes. 
- Note that the effect after setting will not be saved 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.SetCameraAnchor((0,1,0)) 
``` 

## SetCameraBindActorId 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Bind the camera to the target entity (the caller and the target must be in the same dimension and within the loading range. If the target leaves the range or dies after binding, it will be automatically unbound) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| targetId | str | target entity id | 

- return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.SetCameraBindActorId('1234') 
``` 




## SetCameraOffset 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Set the camera offset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| offset | tuple(float,float,float) | offset | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Note that this interface only changes the offset of the third-person camera (including front-view third-person and rear-view third-person), and is invalid for the camera in first-person mode. 
- Unlike SetCameraAnchor, this interface changes the position offset value of the camera, and does not change the center position of the camera track. 
- Note that the effect after setting will not be saved 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.SetCameraOffset((1, 1, 1)) 
``` 

## SetCameraPitchLimit 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Set the upper and lower angle limits of the camera, the default is (-90, 90) 

- Parameters


    | Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| limit | tuple(float,float) | Upper and lower angle limit | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- Note that the effect after setting will not be saved 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.DepartCamera() 
comp.SetCameraPitchLimit((-30, 30)) 
``` 

## SetCameraPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Set the position of the camera center 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(float,float,float) | Position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Note that the effect after setting will not be saved 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.SetCameraPos((1, 1, 1)) 
``` 

## SetCameraRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Set the camera rotation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rot | tuple(float,float) | rotation | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.SetCameraRot((1, 1)) 
``` 

## SetFov 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 


Set the field of view size 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| fov | float | The unit is angle, the range is [30, 110]. If fov is less than 30, it is set to 30. If fov is greater than 110, it is set to 110. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.SetFov(60) 
``` 

## SetPerspective 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerViewCompClient.PlayerViewCompClient 

- Description 

Set the perspective mode 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| persp | int | 0: first-person perspective; 1: third-person perspective; 2: front-view third-person perspective | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi

comp = clientApi.GetEngineCompFactory().CreatePlayerView(entityId) 
comp.SetPerspective(1) 
``` 
## SetSpeedFovLock 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.cameraCompClient.CameraComponentClient 
- Description 
Whether to lock the camera's field of view fov. After locking, it will not change with the speed. 
- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isLocked | bool | Whether locked | 
- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.SetSpeedFovLock(True) 
``` 
## UnDepartCamera 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.cameraCompClient.CameraComponentClient 
- Description 

Bind the player to the camera 

- Parameters 

None 


- Return value 

None 

- Notes 
- After binding, you can only see the back of the player 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId) 
comp.UnDepartCamera() 
``` 

## UnLockCamera 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.cameraCompClient.CameraComponentClient 

- Description 

Unlock the camera 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateCamera(levelId)
comp.UnLockCamera()
```