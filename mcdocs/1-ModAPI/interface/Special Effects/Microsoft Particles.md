--- 
sidebarDepth: 1 
--- 
# Microsoft Particles 

## BindEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Binds a particle emitter to a specified bone of a specified entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id. A particle emitter that has been created and not destroyed is required | 
| entity_id | str or int | Entity id to be bound | 
| bone_name | str | Bone name to be bound (case insensitive). The default value is "body" | 
| offset | tuple | 3D Indicates the binding offset of the particle emitter. The default value is (0, 0, 0) | 
| rotation | tuple | Indicates the three-dimensional rotation of the particle emitter binding (in degrees, rotated in ZYX order). The default value is (0, 0, 0) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- The calculation of the binding transformation is completed in the local space. 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None)
localId = clientApi.GetLocalPlayerId()

parId = comp.Create("netease:tutorial_particle")
comp.BindEntity(parId, localId, "rightitem", (0, 0, 0), (0, 0, 0))
```



## BindModel

<span style="display:inline;color:#7575f9">Client</span>


method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Binds a particle emitter to a specified bone of a specified bone model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id. A particle emitter that has been created and not destroyed is required | 
| model_id | int | ID of the bound bone model (see GetModelId of the model component) | 
| bone_name | str | Name of the specific bone to bind to (case insensitive). The default value is "root" | 
| offset | tuple(float,float,float) | 3D. Indicates the binding offset of the particle emitter. The default value is (0, 0, 0) | 
| rotation | tuple(float,float,float) | Indicates the three-dimensional rotation of the particle emitter binding (in degrees, rotated in ZYX order). The default value is (0, 0, 0) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- The binding transformation is calculated in local space. If no bone is specified, it is bound to "root" by default. If root does not exist, the particle will not be displayed and will not be destroyed. 
- Switching to another skeletal model causes the model_id to change, so the particle emitter bound to the original model_id will also disappear. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(clientApi.GetLevelId()) 
par_Id = comp.Create("netease:tutorial_particle") 
comp.BindModel(par_Id, model_id, "root", (0, 0, 0), (0, 0, 0)) 
``` 
## Create 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 
- Description 
Create a particle emitter and play it immediately after creation 
- Parameters


    | Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| effect_name | str | Particle emitter name (identifier in particle emitter json file) | 
| offset | tuple | 3D Indicates creating a particle emitter at a certain location. The default value is (0, 0, 0) | 
| rotation | tuple | 3D rotation used after the particle emitter is created (using the angle system, rotating in the ZYX order). The default value is (0, 0, 0) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Particle emitter instance ID. Returning 0 means creation failed. | 

- Notes 
- Particle emitter json files can be created and edited through the official Microsoft editor SnowStorm. 
Developers can visit the online website https://snowstorm.app or search "snowstorm" in the Visual Studio Code extension store to use this editor 
- The particle emitter json file should be stored in the resource package/particles path 
- The particle emitter json file content should not contain Chinese, otherwise it will not be parsed 
- Please note that if the particle emitter appears in the world space (that is, there is no bound entity), 
Even if the particle emitter json file defines the minecraft:emitter_lifetime_looping component, 
It will only play once or for one cycle and then be destroyed 
- Some original particles use the minecraft:emitter_rate_manual component, and the EmitManually function needs to be called additionally to emit particles 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
parId = comp.Create("netease:tutorial_particle", (0, 0, 0), (0, 0, 0)) 
``` 

## CreateBindEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Create a particle emitter and bind it to the specified bone of the specified entity. Play it immediately after creation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| effect_name | str | Particle emitter name (identifier in the particle emitter json file) | 
| entity_id | str or int | Entity id to be bound | 
| bone_name | str | Bone name to be bound (case insensitive) The default value is "body" |

| offset | tuple | 3D Indicates the binding offset of the particle emitter. The default value is (0, 0, 0) | 
| rotation | tuple | Indicates the 3D rotation of the particle emitter binding (using the angle system, rotating in the ZYX order). The default value is (0, 0, 0) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Particle emitter instance id. Returning 0 indicates creation failure | 

- Notes 
- The particle emitter json file can be created and edited through the official Microsoft editor SnowStorm. 
Developers can use this editor by visiting the online website https://snowstorm.app or searching for "snowstorm" in the Visual Studio Code extension store. 
- The particle emitter json file should be stored in the resource package/particles path 
- The particle emitter json file content should not contain Chinese, otherwise it will not be parsed 
- The calculation of the binding transformation is done in local space. 
- Some vanilla particles use the minecraft:emitter_rate_manual component, and need to call the EmitManually function to emit particles 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
``` 
## EmitManually 

<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 
Manually emit particles once 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id. A particle emitter that has been created and not destroyed is required | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful |


- Notes 
- Some original particles use the minecraft:emitter_rate_manual component. After creating the particle emitter, particles will not be automatically emitted. You need to call this function additionally. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("minecraft:water_evaporation_manual", localId, "rightitem") 
comp.EmitManually(parId) # Manually emit particles once 
``` 

## Exist 

<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Check if the specified particle emitter exists 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | When True is returned, it means that the specified particle emitter exists in the scene | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0))
print comp.Exist(parId)
comp.RemoveAll()
print comp.Exist(parId)

``` 

## GetActiveDuration 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Get the activation period of the particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Indicates the activation period of the particle emitter. When the particle emitter is invalid, it will return 0.0 | 

- Notes 
- The activation period of the particle emitter is defined in its corresponding json file (resource package/particles/xxx.json) 
- The play period of the particle emitter is equal to the activation period (active_time) + the sleep period (sleep_time) 
- For a particle emitter without an activation period defined, the return value is a large number (about 1000000) 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
print comp.GetActiveDuration(parId) 
``` 

## GetBindingID

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient

- Description 

Returns the bound target id. If not, returns "0" 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Bound entity id | 

- Notes 
- GetBindingModleID can be used to get the bound skeleton model id 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 

parId = comp.Create("netease:tutorial_particle") 
print comp.GetBindingID(parId) 

comp.BindEntity(parId, localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
print comp.GetBindingID(parId) 
``` 

## GetBindingModleID 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Returns the id of the bound skeleton model. If not, returns -1 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | particle emitter id |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Bound skeleton model id | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(clientApi.GetLevelId()) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.Create("netease:tutorial_particle") 
print comp.GetBindingID(parId) 
comp.BindModel(parId, modID, 'root', (0, 0, 0), (0, 0, 0)) 
print comp.GetBindingModleID(parId) 
``` 

## GetDuration 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Get the play period of the particle emitter (activation + sleep time) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Indicates the play period of the particle emitter. If the particle emitter is invalid, it will return 0.0 | 

- Notes 
- The play cycle of the particle emitter is defined in its corresponding json file (resource package/particles/xxx.json) 
- The play cycle of the particle emitter is equal to the activation cycle (active_time) + the sleep cycle (sleep_time) 
- For particle emitters that do not define a play cycle, the return value is a larger number (approximately 1000000) 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
print comp.GetDuration(parId) 
``` 

## GetFacingMode 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Returns the particle facing mode of the particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Particle orientation mode string Return string "none" means illegal | 

- Notes 
- Orientation mode does not support script settings yet. You can edit this property in the particle editor SnowStorm: https://snowstorm.app 
- Currently supported orientation modes are as follows: 

rotate_xyz Particles face the camera, and the patch is perpendicular to the camera's view 
rotate_y Particles face the camera, but the patch only rotates the world Y axis 
lookat_xyz Particles rotate the XYZ axis to look at the camera position 
lookat_y Particles only rotate the Y axis to look at the camera position 
lookat_direction You can choose to determine the particle patch direction based on the velocity direction or a custom direction 
direction_x The particle patch faces the x-axis of the emitter 
direction_y The particle patch faces the y-axis of the emitter 
direction_z The particle patch faces the z-axis of the emitter 
emitter_transform_xy Follows the xy direction of the particle emitter 
emitter_transform_xz Follows the xz direction of the particle emitter 
emitter_transform_yz Follows the yz direction of the particle emitter


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
print comp.GetFacingMode(parId) 
``` 
## GetLoopAge 

<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Get the time that the particle emitter has played in the current playback cycle 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Indicates the time the particle emitter has played in the current playback cycle. If the particle emitter id is invalid, 0.0 will be returned | 

- Notes 
- 0.0 <= Played time <= Particle emitter playback cycle 
- The playback time in the returned cycle is affected by functions such as SetTimeScale, Replay, and PlayAt. 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None)
localId = clientApi.GetLocalPlayerId()

parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0))
print comp.GetLoopAge(parId)
comp.PlayAt(parId, 0.5)

print comp.GetLoopAge(parId) 
``` 

## GetPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Get the particle emitter position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 
| is_local | bool | Whether to get the local space | Binding offset The default value is True (i.e., get the local space position | Binding offset by default) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| Tuple | A 3D vector representing the position of the particle emitter | 

- Notes 
- If a particle is not bound (i.e. not placed in world space), its local space position is equal to its world space position. 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None)
localId = clientApi.GetLocalPlayerId()

parId0 = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 1, 0), (0, 0, 0))
parId1 = comp.Create("netease:tutorial_particle", (0, 1, 0), (0, 0, 0))
print 'local position:', comp.GetPos(parId0, True)
print 'local position:', comp.GetPos(parId1)

print 'world position:', comp.GetPos(parId0, False)
print 'world position:', comp.GetPos(parId1, False)
```



## GetRot

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Get the local rotation of the particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 
| is_local | bool | Indicates whether to get the local space rotation. The default value is True (that is, the local space rotation is obtained by default) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| Tuple | Particle emitter 3D rotation (using angle system) | 

- Notes 
- If the particle emitter is not bound, its local space rotation is equal to the world space rotation 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (45, 0, 45)) 
print comp.GetRot(parId) # True 
print comp.GetRot(parId, False) 
``` 
## GetSleepDuration 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Get the sleep period of the particle emitter 

- Parameters


    | Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Indicates the sleep period of the particle emitter. When the particle emitter is invalid, it will return 0.0 | 

- Notes 
- The sleep period of the particle emitter is defined in its corresponding json file (resource package/particles/xxx.json) 
- The play period of the particle emitter is equal to the activation period (active_time) + the sleep period (sleep_time) 
- For particle emitters without a defined sleep period, the return value is 0.0 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) print comp.GetSleepDuration(parId) 
``` 
## GetTimeScale 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 
- Description 
Get the playback speed of the particle emitter 
- Parameters 
| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Indicates the playing speed of the particle emitter. It will return 0.0 when the particle emitter is invalid |


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem") 
print comp.GetTimeScale(parId) 
comp.SetTimeScale(parId, 0.2) 
print comp.GetTimeScale(parId) 
``` 

## GetVariable 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Get the Molang variable value of the particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 
| variable_name | str | Molang variable name (e.g. variable.emitter_age) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Indicates the Molang variable value of the particle emitter. If invalid, it will return 0.0 | 

- Notes 
- Molang variables can be defined in the particle emitter json file. 
- In addition, particle emitters and particles have some built-in Molang variables available for use: 

variable.emitter_random_1 Particle emitter random number, ranging from 0.0 to 1.0, only generated once when the particle emitter is created 
variable.emitter_random_2 Particle emitter random number, ranging from 0.0 to 1.0, only generated once when the particle emitter is created 
variable.emitter_random_3 Particle emitter random number, ranging from 0.0 to 1.0, only generated once when the particle emitter is created 
variable.emitter_random_4 Particle emitter random number, ranging from 0.0 to 1.0, only generated once when the particle emitter is created 
variable.emitter_lifetime Particle emitter playback cycle (life cycle) 
variable.emitter_age Particle emitter current playback time 
variable.entity_scale When the particle emitter is bound to an entity, this value indicates the size scale of the bound entity

variable.particle_lifetime particle life cycle 
variable.particle_age time after particle generation 
variable.particle_random_1 particle random number, range is 0.0 to 1.0, only generated once when the particle is generated 
variable.particle_random_2 particle random number, range is 0.0 to 1.0, only generated once when the particle is generated 
variable.particle_random_3 particle random number, range is 0.0 to 1.0, only generated once when the particle is generated 
variable.particle_random_4 particle random number, range is 0.0 to 1.0, only generated once when the particle is generated 
- For the use of Molang expressions, you can refer to Microsoft's official documentation: 
https://docs.microsoft.com/en-us/minecraft/creator/reference/content/molangreference/examples/molangconcepts/molangintroduction 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
print comp.GetVariable(parId, 'variable.custom_size') # variable.custom_size is a custom variable in the particle json file 
``` 
## Hide 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 
- Description 
Hide particle emitter (do not render) 
- Parameters 
| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Remarks 
- Please note that this function does not stop the update of the particle emitter, so the particle emitter will be naturally destroyed when the playback ends if there is no bound entity or it is designed to be played only once. 
- Can be used in conjunction with the Show function. 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
print comp.IsHiding(parId) 
# You can wait for the particle to appear before calling 
comp.Hide(parId) 
print comp.IsHiding(parId) 
``` 
## IsHiding 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 
- Description 
Returns whether the particle emitter is being hidden (not rendered) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the particle emitter is being hidden | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0))
print comp.IsHiding(parId)
comp.Hide(parId)
print comp.IsHiding(parId)
```



## IsPausing 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Returns whether the logic of the particle emitter is being paused 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the particle emitter is paused | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
print comp.IsPausing(parId) 
comp.Pause(parId) 
print comp.IsPausing(parId) 
``` 
## Pause 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 
- Description 
Pause the logic update of the particle emitter, but keep the rendering state 
- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Remarks 
- Can be used with the Resume function to pause the logic of the particle emitter. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
print comp.IsPausing(parId) 
# Wait for a while and call to see the effect of time stopping 
comp.Pause(parId) 
print comp.IsPausing(parId) 
``` 
## Play 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 
- Description 

Play particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- The particle emitter will play immediately when it is created, so there is no need to call this function manually. 
- This function is equivalent to calling Resume and Show. If both functions are needed at the same time, it is recommended to use this function directly. 
- This function is used in conjunction with the Stop function to allow the particle emitter to continue playing at the time it was stopped (resume logic update, start rendering). 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None)
localId = clientApi.GetLocalPlayerId()

parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0))
comp.Stop(parId)
print comp.IsHiding(parId)
print comp.IsPausing(parId)

comp.Play(parId)
print comp.IsHiding(parId)
print comp.IsPausing(parId)
```



## PlayAt

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Set the particle emitter playback time point 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 
| at_second | float | Playback time point | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 


- Notes 
- This function can be used in conjunction with the Stop function (jump to a specified time point, continue logic update and start rendering). 
- This function can make the particle emitter jump to a certain time point for playback. 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None)
localId = clientApi.GetLocalPlayerId()

parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0))
print comp.GetLoopAge(parId)

comp.PlayAt(parId, 0.5)
print comp.GetLoopAge(parId)
```



## Remove

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient

- describe

Destroy the specified particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id No operation will be performed for a non-existent particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- The original rain and other particle emitters cannot be destroyed through similar interfaces at present, probably because they use the old version of Microsoft Particle System 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None)

localId = clientApi.GetLocalPlayerId() 

parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
print comp.Exist(parId) 
comp.Remove(parId) 
print comp.Exist(parId) 
``` 

## RemoveByName 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Destroys all particle emitters with the specified name (identifier in particle emitter json) in the scene 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| effect_name | str | Particle emitter name (identifier in json) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- Original rain and other particle emitters cannot be destroyed through similar interfaces, probably because they use the old version of Microsoft particle system for management 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0))
print comp.Exist(parId)
comp.RemoveByName("netease:tutorial_particle")
print comp.Exist(parId)
```

## Replay 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Replay particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- This function can be used in conjunction with the Stop function (re-update logic and start rendering). 
- This function can return the particle emitter to its time point zero and restart the playback (cannot be used for particle emitters that have been destroyed). 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
# You can wait for a while and call 
comp.Replay(parId) 
``` 
## Resume 

<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 
- Description 
Restore the logical update of the particle emitter without affecting the rendering state


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- Can be used with the Pause function to resume the logical update of the particle emitter. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
comp.Pause(parId) 
print comp.IsPausing(parId) 
# You can wait for a while and then call 
comp.Resume(parId) 
print comp.IsPausing(parId) 
``` 
## SetPos 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Set the particle emitter position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id | 
| pos | Tuple | 3D Indicates the local spatial position of the particle emitter. The default value is (0, 0, 0) |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- When the particle emitter is not bound (i.e. placed in world space), its local space position is the world space position. 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None)
localId = clientApi.GetLocalPlayerId()

parId0 = comp.CreateBindEntity("netease:tutorial_particle", localId, "leftitem", (0, 1, 0), (0, 0, 0))
parId1 = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, -1, 0), (0, 0, 0))

comp.SetPos(parId0, (0, 0.5, 0))
comp.SetPos(parId1) # (0, 0, 0)
```



## SetRelative 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Sets whether particles are calculated in local space 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id Requires particle emitter to be bound to entity | 
| is_relative | bool | Indicates whether particles are calculated in local space. The default parameter value is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes

- This function is invalid for unbound particle emitters 
- The relevant values can be pre-defined in the minecraft:emitter_local_space component in the particle emitter json file. 
If this component is not available, the default transformation is in the world coordinate system (False). 
- When relative is set to False, all calculations related to particle movement are considered to be performed in world space. 
- When relative is set to True, all calculations related to particle movement are considered to be performed in local space. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 

# Developers can compare the difference between the two to understand the two different computing spaces 
parId0 = comp.CreateBindEntity("netease:tutorial_particle", localId, "leftitem", (0, 1.0, 0), (90, 0, 0)) 
comp.SetRelative(parId0, False) 
parId1 = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 1.0, 0), (90, 0, 0)) 
comp.SetRelative(parId1, True) 
``` 

## SetRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Set the local rotation of the particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 
| rot | Tuple | Particle emitter three-dimensional rotation (using angle system, rotate in ZYX order) The default value is (0, 0, 0) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- If a particle emitter is not bound, its local space rotation is the world space rotation 

- Example 


```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None)
localId = clientApi.GetLocalPlayerId()

parId0 = comp.CreateBindEntity("netease:tutorial_particle", localId, "leftitem", (0, 0, 0), (0, 0, 0))
parId1 = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0))
comp.SetRot(parId1, (0, 0, 90))
```



## SetTimeScale

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Set the playback speed of the particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 
| scale | float | Indicates the playback ratio. Can be negative for reverse playback | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- Particles that have disappeared during reverse playback (please note that they are single particles, not particle emitters) will not reappear, and no new particles will be generated 
- If the reverse playback reaches time point 0, particle emitters that are not bound or not looped will be destroyed 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None)
localId = clientApi.GetLocalPlayerId()

parId0 = comp.CreateBindEntity("netease:tutorial_particle", localId, "leftitem")
# comp.SetTimeScale(parId0, 1.0)
parId1 = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem")
comp.SetTimeScale(parId1, 0.2)

``` 

## SetVariable 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Set the Molang variable value of the particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 
| variable_name | str | Molang variable name | 
| value | float | Indicates the Molang variable value of the particle emitter | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- Molang variables can be defined in the particle emitter json file. 
- In addition, some Molang variables are built into the particle emitter and particles for use: 

variable.emitter_random_1 Particle emitter random number, ranging from 0.0 to 1.0, only generated once when the particle emitter is created 
variable.emitter_random_2 Particle emitter random number, ranging from 0.0 to 1.0, only generated once when the particle emitter is created 
variable.emitter_random_3 Particle emitter random number, ranging from 0.0 to 1.0, only generated once when the particle emitter is created 
variable.emitter_random_4 Particle emitter random number, ranging from 0.0 to 1.0, only generated once when the particle emitter is created 
variable.emitter_lifetime Particle emitter playback cycle (lifecycle) 
variable.emitter_age Particle emitter current playback time 
variable.entity_scale When the particle emitter is bound to an entity, this value indicates the size scale of the bound entity 
variable.particle_lifetime Particle life cycle 
variable.particle_age The time that has passed since the particle was generated 
variable.particle_random_1 Particle random number, ranging from 0.0 to 1.0, generated only once when the particle is generated 
variable.particle_random_2 Particle random number, ranging from 0.0 to 1.0, generated only once when the particle is generated 
variable.particle_random_3 Particle random number, ranging from 0.0 to 1.0, generated only once when the particle is generated 
variable.particle_random_4 Particle random number, ranging from 0.0 to 1.0, generated only once when the particle is generated 
Some built-in variables (such as variable.emitter_age) are refreshed every frame, and modifying their values may have no effect. 
- Regarding the use of Molang expressions, you can refer to Microsoft's official documentation: 
https://docs.microsoft.com/en-us/minecraft/creator/reference/content/molangreference/examples/molangconcepts/molangintroduction 

- Example


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId0 = comp.CreateBindEntity("netease:tutorial_particle", localId, "leftitem", (0, 0, 0), (0, 0, 0)) 
parId1 = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
comp.SetVariable(parId1, "variable.custom_size", 0.1) # Modifying the built-in Molang value has little effect or even no effect, so it is recommended to customize the variable name 
``` 
## Show 
<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Display particle emitter (turn on rendering) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- Can be used with the Hide function to restore the display of the particle emitter. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
# You can wait for the particle to appear and then call 
comp.Hide(parId) 
print comp.IsHiding(parId)


# You can wait for the particle to be hidden before calling 
comp.Show(parId) 
print comp.IsHiding(parId) 
``` 

## Stop 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Stop the particle emitter (no rendering and no logic update) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| par_id | int | Particle emitter id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- This function is equivalent to calling Pause and Hide. If both functions are needed at the same time, it is recommended to use this function directly. 
- Because the logic is stopped from updating, the particle emitter will not be destroyed naturally due to the end of playback. 
- You can use the Play, Replay or PlayAt functions to play the stopped particle emitter. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None) 
localId = clientApi.GetLocalPlayerId() 
parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (0, 0, 0), (0, 0, 0)) 
print comp.IsHiding(parId) 
print comp.IsPausing(parId) 
# You can wait for a while and then call 
comp.Stop(parId) 
print comp.IsHiding(parId) 
print comp.IsPausing(parId)

``` 

## Unbind 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleSystemCompClient.ParticleSystemCompClient 

- Description 

Unbind the specified particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| par_id | int | Particle emitter id. Requires a particle emitter that has been created and not destroyed | 
| keep_position | bool | Whether to keep the position of the particle emitter in the world space after unbinding. The default value is True | 
| keep_rotation | bool | Whether to keep the rotation of the particle emitter in the world space after unbinding. The default value is True | 

- Return value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| bool | Indicates whether the call is successful | 

- Notes 
- When keep_position is False, the unbound particle emitter will use the local offset at the time of binding as the world space position (i.e. (6, 6, 6) in the example) 
When keep_rotation is False, the unbound particle emitter will use the local rotation at the time of binding as the world space rotation (i.e. (0, 0, 0) in the example) 
- When keep_position is True, the unbound particle emitter will remain at the world space position before the unbinding moment 
When keep_rotation is True, the unbound particle emitter will maintain the world space rotation before the unbinding moment 
- Please note that if the particle emitter appears in the world space (i.e. there is no bound entity), 
Even if the particle emitter json file defines the minecraft:emitter_lifetime_looping component, 
It will only play once or for one cycle and then be destroyed 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateParticleSystem(None)
localId = clientApi.GetLocalPlayerId()

parId = comp.CreateBindEntity("netease:tutorial_particle", localId, "rightitem", (6, 6, 6), (0, 0, 0))
comp.Unbind(parId)
```