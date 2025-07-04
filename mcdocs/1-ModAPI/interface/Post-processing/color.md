--- 
sidebarDepth: 1 
--- 
# Color 

## CheckColorAdjustmentEnabled 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Checks whether the color correction effect is enabled. 

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
comp.CheckColorAdjustmentEnabled() 
``` 

## SetColorAdjustmentBrightness 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Adjust the screen color brightness. The larger the brightness value, the brighter the screen, and vice versa. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| brightness | float | Brightness value, the value range is [0,5]. Values less than or greater than this range will be truncated to the boundary value 0 or 5 |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the brightness value to 3 
comp.SetColorAdjustmentBrightness(3) 
``` 

## SetColorAdjustmentContrast 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Adjust the screen color contrast. The larger the screen contrast value, the more obvious the color difference. Conversely, the smaller the color difference. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| contrast | float | Contrast value, the value range is [0,5]. Values less than or greater than this range will be truncated to the boundary value 0 or 5 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the contrast value to 3 
comp.SetColorAdjustmentContrast(3) 
``` 




## SetColorAdjustmentSaturation 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Adjust the screen color saturation. The larger the screen saturation value, the more obvious the color, and vice versa. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| saturation | float | Saturation value, the value range is [0,5]. Values less than or greater than this range will be truncated to the boundary value 0 or 5 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the saturation value to 3 
comp.SetColorAdjustmentSaturation(3) 
``` 

## SetColorAdjustmentTint 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Adjust the tint of the screen color. Adjust the screen color according to the input tint and intensity. When the intensity is greater, the overall color of the screen is more inclined to the input tint. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| intensity | float | Hue intensity, the value range is [0,1]. Values less than or greater than this range will be truncated to the boundary value 0 or 1. | 
| color | tuple(float,float,float) | Hue value, the RGB value of the color in order, the value range is [0,255]. Values less than or greater than this range will be truncated to the boundary value 0 or 255. |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the screen color to red, the intensity is 0.3 
comp.SetColorAdjustmentTint(0.3, (255,0,0)) 
``` 

## SetEnableColorAdjustment 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Set whether to enable the color correction effect. After enabling, the screen color can be adjusted. The effect parameters can be set through other interfaces of the color correction effect. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| enable | bool | Whether to enable the color correction effect. True means enabled and False means disabled. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
comp.SetEnableColorAdjustment(True) 
``` 

