--- 
sidebarDepth: 1 
--- 
# Blur 

## CheckGaussianBlurEnabled 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Check whether the Gaussian blur effect is enabled. 

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
comp.CheckGaussianBlurEnabled() 
``` 

## SetEnableGaussianBlur 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Set whether to enable the Gaussian blur effect. When enabled, the area around the player's screen is blurred. The effect parameters can be set through other Gaussian blur interfaces. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| enable | bool | Whether to enable the Gaussian blur effect, True means on, False means off. |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
comp.SetEnableGaussianBlur(True) 
``` 

## SetGaussianBlurRadius 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.postProcessControlComp.PostProcessComponent 

- Description 

Set the blur radius of the Gaussian blur effect. The larger the radius, the greater the blur, and vice versa. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| radius | float | Blur radius size, the value range is [0,10], values less than or greater than this range will be truncated to the boundary value 0 or 10 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePostProcess(levelId) 
# Adjust the Gaussian blur radius to 3 
comp.SetGaussianBlurRadius(3) 
``` 

