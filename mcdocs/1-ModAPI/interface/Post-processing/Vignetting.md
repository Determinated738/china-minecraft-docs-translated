--- 
sidebarDepth: 1 
--- 
# Vignette 

## CheckVignetteEnabled 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Check whether the screen vignetting effect is enabled. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means enabled, False means disabled. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
comp.CheckVignetteEnabled() 
``` 

## SetEnableVignette 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Set whether to enable the screen vignetting (Vignette) effect. When enabled, vignetting will appear around the player's screen. The effect parameters can be set through other Vignette interfaces. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| enable | bool | Whether to enable the Vignette effect, True means on, False means off. |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
comp.SetEnableVignette(True) 
``` 

## SetVignetteCenter 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Set the vignetting center position of the vignetting (Vignette), which can change the position of the screen vignetting. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| center | tuple(float,float) | The x and y values of the screen position in order. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the vignetting center position to the center of the screen 
comp.SetVignetteCenter((0.5,0.5)) 
``` 



## SetVignetteRGB 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Set the vignetting color of the vignetting (Vignette), which can change the color of the screen vignetting. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| color | tuple(float,float,float) | The RGB values of the color in order, the value range is [0,255]. Values less than or greater than this range will be truncated to the boundary value 0 or 255 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Set the color value to red. 
comp.SetVignetteRGB((255,0,0)) 
``` 

## SetVignetteRadius 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Set the vignetting radius of the vignetting (Vignette). The larger the radius, the smaller the vignetting and the larger the player's field of view. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| radius | float | The vignetting radius size, the value range is [0,1]. Values less than or greater than this range will be truncated to the boundary value 0 or 1 | 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the vignetting radius to 0.5 
comp.SetVignetteRadius(0.5) 
``` 

## SetVignetteSmoothness 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Set the vignetting blur coefficient of the vignetting (Vignette). The larger the blur coefficient, the blurrier the vignetting edge and the larger the blur range 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| radius | float | Vignette blur coefficient, the value range is [0,1], values less than or greater than this range will be truncated to the boundary value 0 or 1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the vignetting blur coefficient to 0.5 
comp.SetVignetteSmoothness(0.5) 
``` 

