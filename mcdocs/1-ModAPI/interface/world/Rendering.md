--- 
sidebarDepth: 1 
--- 
# Rendering 

## GetAmbientBrightness 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Get ambient brightness, affects sky brightness, does not affect entity and block lighting 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Range 0 to 1 | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
ambineBrightness = comp.GetAmbientBrightness() 
``` 

## GetFogColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.fogCompClient.FogCompClient 

- Description 

Get the current fog effect color 

- Parameters 

None 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float,float) | Color rgba | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFog(levelId) 
# Get fog effect color 
fogColor = comp.GetFogColor() 
``` 

## GetFogLength 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.fogCompClient.FogCompClient 

- Description 

Get fog effect range 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Fog effect start value and end value | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFog(levelId) 
start,end = comp.GetFogLength() 
``` 

## GetMoonRot 

<span style="display:inline;color:#7575f9">Client</span> 


method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Get the moon angle 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | The first float represents the north-south offset, the second float represents the moon's rotation angle, and the third float represents the moonrise and moonset. The unit is angle | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
rot = comp.GetMoonRot() 
``` 

## GetSkyColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Get the sky color 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float,float) | Color RGBA, between 0 and 1, the a value is not used at present | 

- Example 

```python 
import mod.client.extraClientApi as clientApi

comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
color = comp.GetSkyColor() 
``` 

## GetSkyTextures 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Get the current dimension skybox texture, the skybox has 6 textures 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) or None | Skybox texture list, the value may be None | 

- Example 

```python 
# The texture list corresponds to the negative Z axis direction of the world coordinate in order, Positive X-axis direction, positive Z-axis direction, negative X-axis direction, positive Y-axis direction, negative Y-axis direction. The positive Y-axis is the top (right-hand coordinate system is used). 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
textureList = comp.GetSkyTextures() 
``` 

## GetStarBrightness 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Get the brightness of the stars 

- Parameters 

None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Range 0 to 1 | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
starBrightness = comp.GetStarBrightness() 
``` 

## GetSunRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Get the sun angle 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | The first float represents the north-south offset, the second float represents the rotation angle of the sun, and the third float represents sunrise and sunset. The unit is angle | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
rot = comp.GetSunRot() 
``` 

## GetUseAmbientBrightness 

<span style="display:inline;color:#7575f9">Client</span>


method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Determine whether the ambient light brightness is set in the mod 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to set | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
useAmbientBrightness = comp.GetUseAmbientBrightness() 
``` 

## GetUseFogColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.fogCompClient.FogCompClient 

- Description 

Determine whether the fog effect color is currently enabled. The default value is False. It is True after using the color value passed in by mod 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to set | 

- Example 

```python

import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFog(levelId) 
# Get whether to enable the fog effect color setting 
useFogColor = comp.GetUseFogColor() 
``` 

## GetUseFogLength 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.fogCompClient.FogCompClient 

- Description 

Determine whether the fog effect range is currently enabled. The default value is False. It is True after using the range value passed in by mod 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to set | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFog(levelId) 
# Get whether to enable the fog effect range 
useFogLength = comp.GetUseFogLength() 
``` 

## GetUseMoonRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Determine whether the moon angle is set in the mod 

- Parameters


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set or not | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
useMoonRot = comp.GetUseMoonRot() 
``` 

## GetUseSkyColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Determine whether the sky color is set in the mod 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| bool | Set or not | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
useSkyColor = comp.GetUseSkyColor() 
``` 

## GetUseStarBrightness


<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Determine whether the star brightness is set in the mod 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to set | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
useStarBrightness = comp.GetUseStarBrightness() 
``` 

## GetUseSunRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Determine whether the sun angle is set in the mod 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to set | 

- Example


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
useSunRot = comp.GetUseSunRot() 
``` 

## HideNameTag 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Hide all names displayed in the scene, including player names, custom names of creatures, floating text of item display frames and command blocks, etc. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isHide | bool | Whether to hide, True is hidden, False is displayed | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.HideNameTag(True) 
``` 

## ResetAmbientBrightness 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Reset ambient brightness 

- Parameters 


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.ResetAmbientBrightness() 
``` 

## ResetFogColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.fogCompClient.FogCompClient 

- Description 

Reset the fog effect color 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFog(levelId) 
comp.ResetFogColor() 
``` 

## ResetFogLength 


<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.fogCompClient.FogCompClient 

- Description 

Reset fog effect range 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFog(levelId) 
comp.ResetFogLength() 
``` 

## ResetMoonRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Reset the moon angle 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.ResetMoonRot() 
``` 

## ResetSkyColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Reset sky color 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.ResetSkyColor() 
``` 
## ResetSkyTextures 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 
- Description 
Reset the current dimension skybox texture. If the texture is configured using addon, the configured texture will be used, otherwise there will be no texture in the game by default 
- Parameters 


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.ResetSkyTextures() 
``` 

## ResetStarBrightness 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Reset star brightness 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.ResetStarBrightness() 
``` 

## ResetSunRot 


<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Reset the sun angle 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.ResetSunRot() 
``` 

## SetAmbientBrightness 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Set the ambient light brightness, affecting the sky brightness, not affecting entity and block lighting 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| brightness | float | Range between 0 and 1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.SetAmbientBrightness(0.1) 
``` 

## SetFogColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.fogCompClient.FogCompClient 

- Description 

Set the fog color 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| color | tuple(float,float,float,float) | Color RGBA, range between 0 and 1, a value is mainly used for underwater effects | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFog(levelId) 
# Set the fog effect to all white 
comp.SetFogColor((1.0,1.0,1.0,1.0)) 
``` 

## SetFogLength 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.fogCompClient.FogCompClient 

- Description


Set fog effect range 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| start | float | Fog effect starting distance | 
| end | float | Fog effect end range | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFog(levelId) 
comp.SetFogLength(10, 50) 
``` 

## SetMoonRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Set the angle of the moon 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rot | tuple(float,float,float) | The first float represents the north-south offset, the second float represents the rotation angle of the moon, and the third float represents the moonrise and moonset. The unit is angle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.SetMoonRot((10, 0, 10)) 
``` 

## SetSkyColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Set the sky color 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| color | tuple(float,float,float,float) | Color RGBA, between 0 and 1, the a value is not used at present | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.SetSkyColor((0.5, 0.5, 0.8, 1.0)) 
``` 

## SetSkyTextures 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Set the current dimension skybox texture, the skybox requires 6 textures 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| textureList | list(str) | Requires the path of 6 textures, which is the absolute path starting from the textures directory. If a certain direction of the skybox does not need to be set, pass an empty string | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The skybox texture will be reset when the game cuts the dimension, so the developer needs to listen to the corresponding dimension switching completion event (DimensionChangeFinishClientEvent) to process the texture. 

- Example 

```python 
# The map list corresponds to the negative Z axis direction, positive X axis direction, positive Z axis direction, negative X axis direction, positive Y axis direction, and negative Y axis direction of the world coordinates in order. The positive Y axis is the top (using the right-hand coordinate system). 
textureList = ['', 'textures/environment/positiveX','textures/environment/positiveZ', '', 'textures/environment/positiveY', ''] 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.SetSkyTextures(textureList) 
``` 

## SetStarBrightness 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Set the star brightness. Stars can also be displayed during the day 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| brightness | float | Range between 0 and 1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.SetStarBrightness(0.1) 
``` 

## SetSunRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Set the sun's angle 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rot | tuple(float,float,float) | The first float represents the north-south offset, the second float represents the sun's rotation angle, and the third float represents sunrise and sunset. The unit is angle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateSkyRender(levelId) 
comp.SetSunRot((10, 0, 10)) 
``` 

## SkyTextures 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.skyRenderCompClient.SkyRenderCompClient 

- Description 

Modify the textures of the sun, moon, cloud distribution, and skybox. Use addon configuration, non-python interface.


- Parameters 

None 

- Return Value 

None 

- Notes 
- The game provides a way to reload textures to modify the textures of the sun, moon, cloud distribution, and skybox. 
**The End and the Nether do not have the sun, moon, or clouds. In addition, the sky in the End uses a texture end_sky.png instead of a skybox texture. end_sky.png should be used in combination with the fog effect color. The Nether does not currently support this feature**. 
The specific path is: 
| Texture | Path | 
| ------------ | ------------------------------------------------------------ | 
| Sun texture | modResource directory/textures/environment/{dimName}_sun.png | 
| Moon texture | modResource directory/textures/environment/{dimName}_moon_phases.png | 
| Cloud distribution texture | modResource directory/textures/environment/{dimName}_clouds.png | 
| Skybox texture | modResource directory/textures/environment/{dimName}_cubemap/cubemap_0.png | 

Among them: the skybox map needs to put 6 pictures, that is, the final needs to include ```cubemap_0.png``` to ```cubemap_5.png```, and ```{dimName}``` represents the name of the dimension. The names of each dimension are as follows: 
| dimension | name | 
| --------------------------- | --------------- | 
| theend | 
| nether | 
| overworld | 
| other copied dimension images | numeric ids from 3 to 20 | 

Example: 
```json 
modResource/textures/environment/4_sun.png 
modResource/textures/environment/overworld_moon_phases.png 
modResource/textures/environment/3_clouds.png 
modResource/textures/environment/overworld_cubemap/cubemap_0.png # -z direction 
modResource/textures/environment/overworld_cubemap/cubemap_1.png # x direction 
modResource/textures/environment/overworld_cubemap/cubemap_2.png # z direction 
modResource/textures/environment/overworld_cubemap/cubemap_3.png # -x direction 
modResource/textures/environment/overworld_cubemap/cubemap_4.png # y direction 
modResource/textures/environment/overworld_cubemap/cubemap_5.png # -y direction 
modResource/textures/environment/end_sky.png #End sky rendering texture 
``` 

