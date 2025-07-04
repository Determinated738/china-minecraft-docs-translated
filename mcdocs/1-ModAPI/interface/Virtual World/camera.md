--- 
sidebarDepth: 1 
--- 
# Camera 

## CameraGetClickModel 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Get the id of the model the camera is currently pointing to. It will return the one closest to the camera. It is usually used with GetEntityByCoordEvent 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Model id. If the camera is not pointing to the model, it will return -1 | 

- Notes 
- The model needs to set a bounding box to respond to clicks 

- Example 

```python 
# When the player clicks the screen, get the id of the model at the click position 
import mod.client.extraClientApi as clientApi 
class MyClientSystem(ClientSystem): 
def __init__(self, namespace, name): 
ClientSystem.__init__(self, namespace, name) 
self.ListenForEvent('Minecraft', 'Engine', 'GetEntityByCoordEvent', self, self.click) 
self.initModel() 

def initModel(self): 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
id = virtualWorldComp.ModelCreateObject("datiangou", "run") 
# Set the bounding box to respond to clicks 
virtualWorldComp.ModelSetBoxCollider(id, (2.0, 2.0, 2.0), (0.0, 0.0, 0.0)) 

def click(self, args):
        import client.extraClientApi as clientApi
        virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId())
        id = virtualWorldComp.CameraGetClickModel()
        if id > 0:

print("select:", id) 
``` 

## CameraGetFov 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Get the camera's field of view 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Field of view, in degrees, range [30, 110]. Defaults to 45 when not modified. | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
fov = virtualWorldComp.CameraGetFov() 
``` 

## CameraGetPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Returns the camera position 

- Parameters 

None 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Coordinate value (x, y, z), returns None if the virtual world is not created | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
cameraPos = virtualWorldComp.CameraGetPos() 
``` 

## CameraGetZoom 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Get the zoom value of the camera 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Zoom value | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
zoom = virtualWorldComp.CameraGetZoom() 
``` 

## CameraLookAt 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient


- Description 

Modify the camera orientation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| targetPos | tuple(float,float,float) | Target coordinates | 
| upVector | tuple(float,float,float) | Camera upward vector, (x,y,z) initially defaults to (0,1,0) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the modification is successful | 

- Notes 
- The initial default orientation of the camera is -z axis 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.CameraLookAt((0.0, 0.0, -10.0), (0.0, 1.0, 0.0)) 
``` 

## CameraMoveTo 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set the camera movement animation, which will be interpolated and displayed according to the current camera state and the input parameters according to time 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Coordinates of the target point | 
| targetPos | tuple(float,float,float) | Position after reaching the target point | 
| upVector | tuple(float,float,float) | The upward vector of the camera after reaching the target point | 
| zoom | float | Zoom value of the camera when reaching the target point | 
| time | float | Unit is seconds, duration of the action (floating point number greater than 0). For the sake of lens continuity, the movement of the camera is related to the actual frame rate. It is calculated at 60 frames by default, and there will be slight deviations due to fluctuations in the actual frame rate. |

| ease | TimeEaseType | Time change function, the default value is clientApi.GetMinecraftEnum().TimeEaseType.linear, the parameter is also considered linear if it is not in the enumeration value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.CameraMoveTo((0.0, 0.0, -10.0), (1.0, 1.0, -10.0), (0.0,1.0, 0.0), 1.0, 3.0, clientApi.GetMinecraftEnum().TimeEaseType.linear) 
``` 

## CameraSetFov 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set the camera field of view 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fov | float | Field of view, in degrees, range [30, 110]. If fov is less than 30, set it to 30; if fov is greater than 110, set it to 110. The default value is 45 if not modified. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.CameraSetFov(60) 
``` 



## CameraSetPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set the camera position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(float,float,float) | The coordinate value (x,y,z) is initially set to (0,0,0) and faces the negative direction of the z axis | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.CameraSetPos((0.0, 6.0, 0.0)) 
``` 

## CameraSetZoom 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set camera zoom 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| zoom | float | Zoom value, The range is [0.1,100.0]. If it is less than 0.1, it is set to 0.1. If it is greater than 100, it is set to 100. If it is not modified, the default value is 1. | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.CameraSetZoom(2.0) 
``` 

## CameraStopActions 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Stop the camera movement animation 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to stop successfully | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.CameraMoveTo((0.0, 0.0, -10.0), (1.0, 1.0, -10.0), (0.0,1.0, 0.0), 1.0, 3.0, clientApi.GetMinecraftEnum().TimeEaseType.linear) 
virtualWorldComp.CameraStopActions() 
``` 

