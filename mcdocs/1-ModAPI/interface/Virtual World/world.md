--- 
sidebarDepth: 1 
--- 
# World 

## VirtualWorldCreate 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Create a virtual world. Only one virtual world is allowed. Calling this method will be invalid if a virtual world already exists 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the creation is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.VirtualWorldCreate() 
``` 

## VirtualWorldDestroy 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Destroy the virtual world 

- Parameters 

None 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Destruction success? | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.VirtualWorldDestroy() 
``` 

## VirtualWorldSetCollidersVisible 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Sets whether the bounding box of the model in the virtual world is displayed, mainly used for debugging, and is not displayed by default 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isVisible | bool | Display or not | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.VirtualWorldSetCollidersVisible(True) 

id = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelSetBoxCollider(id, (2.0, 2.0, 2.0), (0.0, 0.0, 0.0)) 
``` 



## VirtualWorldSetSkyBgColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set the color of the sky background in the virtual world 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| color | tuple(float,float,float) | The r, g, b values of the color are all floating point values between 0.0 and 1.0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
#Set the sky to red 
virtualWorldComp.VirtualWorldSetSkyBgColor((1.0, 0.0, 0.0)) 
``` 

## VirtualWorldSetSkyTexture 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set the texture of the sky in the virtual world 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| texturePath | str | Texture path | 
| mode | int | Stretching mode, 0 or 1. 0 means that the width and height of the texture are stretched to the full screen, which may cause the texture to deform; 1 means that the height is stretched to the full screen, and the width is scaled accordingly according to the original aspect ratio of the texture, which can keep the texture from being stretched, but will cause the texture to exceed the screen or not completely fill the screen. | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.VirtualWorldSetSkyTexture("textures/virtualWorldSky", 0) 
``` 

## VirtualWorldToggleVisibility 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set whether the virtual world is displayed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isVisible | bool | Display or not | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- It is recommended to use this method when you need to frequently switch between the main world and the virtual world. If you do not need to use the virtual world for a long time in the future, it is recommended to call VirtualWorldDestroy to destroy and release resources 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId())
virtualWorldComp.VirtualWorldToggleVisibility(False)
```