--- 
sidebarDepth: 1 
--- 
# Lens Effects 

## CheckDepthOfFieldEnabled 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Check if the depth of field effect is enabled. 

- Parameters 

None 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| bool | True means enabled, False means disabled. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
comp.CheckDepthOfFieldEnabled() 
``` 

## CheckLensStainEnabled 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Checks whether the lens stain effect is enabled. 

- Parameters 

None 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True is enabled, False is disabled. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
comp.CheckLensStainEnabled() 
``` 

## ResetLensStainTexture 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Resets the texture used by the smudge effect to the system default texture. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
comp.ResetLensStainTexture() 
``` 

## SetDepthOfFieldBlurRadius 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent


- Description 

Adjust the blur radius of the depth of field effect. The larger the blur radius, the greater the blur, and vice versa. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| radius | float | Blur radius value, the value range is [0,5]. Values less than or greater than this range will be truncated to the boundary value 0 or 5 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the blur radius value to 0.3 
comp.SetDepthOfFieldBlurRadius(0.3) 
``` 

## SetDepthOfFieldFarBlurScale 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Adjust the distance blur size of the depth of field effect. The larger the distance blur size, the greater the distance blur, and vice versa. Note that the adjustment of the distance blur depends on the focus distance. If the focus is at a closer distance, the distance is in a clearer state at this time, and the blur adjustment will not be very obvious. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| scale | float | The size of the distant blur. The value range is [0,15]. Values smaller or larger than this range will be truncated to the boundary value 0 or 15 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the far blur size value to 1.0 
comp.SetDepthOfFieldFarBlurScale(1.0) 
``` 

## SetDepthOfFieldFocusDistance 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Adjust the focus distance of the depth of field effect. The smaller the distance, the farther away the blur and the closer the clarity; the larger the distance, the farther away the clarity and the closer the blur. This distance is the actual distance, that is, the world coordinate distance starting from the player's camera. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| distance | float | The focal distance value. The value range is [0,100]. Values smaller or larger than this range will be truncated to the boundary value 0 or 100. When the distance value is close to 100, it will be regarded as an infinitely far view. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- If you want to better confirm the position of the focus plane, you can first use SetDepthOfFieldNearBlurScale and SetDepthOfFieldFarBlurScale to set the near blur size and far blur size to the maximum value. At this time, only the area where the focus plane is located appears clear, so that you can see the position of the focus plane more intuitively, so as to conveniently adjust the focus plane distance. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the focus distance value to 4, that is, focus on the position of 4 blocks away from the player 
comp.SetDepthOfFieldFocusDistance(4) 
``` 

## SetDepthOfFieldNearBlurScale 

<span style="display:inline;color:#7575f9">Client</span>


method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Adjust the near blur size of the depth of field effect. The larger the near blur size, the greater the near blur, and vice versa. Note that the near blur adjustment depends on the focus distance. If the focus is at a closer distance, the near blur is in a clearer state, and the blur adjustment will not be very obvious. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| scale | float | Near blur size, the value range is [0,15]. Values less than or greater than this range will be truncated to the boundary value 0 or 15 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the near blur size value to 1.0 
comp.SetDepthOfFieldNearBlurScale(1.0) 
``` 

## SetDepthOfFieldUseCenterFocus 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Sets whether the depth of field effect turns on the screen center focus mode. When turned on, the focus distance will be automatically set to the distance of the object corresponding to the screen center. In the first-person perspective, the focus distance will be automatically set to the distance between the object corresponding to the screen crosshair and the camera, that is, the object corresponding to the crosshair will be automatically focused. In the third-person perspective, since the screen center always corresponds to the player, the focus distance will be automatically set to the distance between the player and the camera, that is, the player will be automatically focused on himself. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| enable | bool | Whether to enable the depth of field effect screen center focus mode, True is on, False is off. After enabling, the original focus distance setting will no longer be valid, and the interface SetDepthOfFieldFocusDistance will also be invalid. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the setting is successful | 

- Notes 
- Similarly, if you want to better confirm the location of the focus point, you can first use SetDepthOfFieldNearBlurScale and SetDepthOfFieldFarBlurScale to set the near blur size and far blur size to the maximum value. At this time, only the area where the focus plane is located appears clear, so that the location of the focus plane can be seen more intuitively, so as to facilitate the adjustment of the focus plane distance. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Enable screen center focus mode 
comp.SetDepthOfFieldUseCenterFocus(True) 
``` 

## SetEnableDepthOfField 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Set whether to enable the depth of field effect. When enabled, the screen will have a depth of field effect, and the effect of blurring far away and being clear near or blurring near and being clear far away will be presented according to the focus distance. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| enable | bool | Whether to enable the depth of field effect, True is on, False is off. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
comp.SetEnableDepthOfField(True) 
``` 

## SetEnableLensStain 


<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Set whether to enable the lens smudge effect. When enabled, the lens will have a smudge effect. You can change the smudge map and smudge color used. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| enable | bool | Whether to enable the lens smudge effect. True means enabled, False means disabled. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
comp.SetEnableLensStain(True) 
``` 

## SetLensStainColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Adjust the lens smudge color. Adjust the smudge color according to the input color and intensity. When the intensity is greater, the smudge color is more biased towards the input color. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| intensity | float | Color intensity, the value range is [0,1]. Values less than or greater than this range will be truncated to the boundary value 0 or 1 | 
| color | tuple(float,float,float) | Color value, the RGB value of the color in order, the value range is [0,255]. Values less than or greater than this range will be truncated to the boundary value 0 or 255 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the lens smudge color to reddish, with an intensity of 0.3 
comp.SetLensStainColor(0.3, (255,0,0)) 
``` 

## SetLensStainIntensity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Adjust the lens smudge intensity. The greater the intensity, the more obvious the smudge, and vice versa. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| intensity | float | Lens stain intensity value, the value range is [0,1]. Values less than or greater than this range will be truncated to the boundary value 0 or 1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the stain intensity value to 0.4 
comp.SetLensStainIntensity(0.4) 
``` 

## SetLensStainTexture 

<span style="display:inline;color:#7575f9">Client</span>


method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

After the lens smudge effect is turned on, the smudge effect uses the system default texture. This interface can change the texture used for lens smudge. Note that it is best to use a transparent background for the texture, otherwise the screen will be covered by the texture. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| texturePath | str | Relative path of the texture, starting with "textures/", no suffix required | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Change the dirt map to my_dirtiness.png in the textures/postprocess directory. 
comp.SetLensStainTexture("textures/postprocess/my_dirtiness")
```