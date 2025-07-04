--- 
sidebarDepth: 1 
--- 
# Particle 

## Bind 

<span style="display:inline;color:#7575f9">Client</span> 

<span id="0"></span> 
method in mod.client.component.particleEntityBindComp.ParticleEntityBindComp 

- Description 

Bind entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| bindEntityId | str | ID of the bound entity | 
| offset | tuple(float,float,float) | Binding offset, relative to the center of the bound entity's foot | 
| rot | tuple(float,float,float) | Binding rotation angle | 
| correction | bool | Not enabled by default. When enabled, the rotation angle of the special effect can be accurately set to the relative angle of the reference player | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleEntityBind(particleEntityId) 
comp.Bind(entityId, (0, 1, 0), (0, 0, 0)) 
``` 

<span id="1"></span> 
method in mod.client.component.particleSkeletonBindComp.ParticleSkeletonBindComp 

- Description 

Bind the skeleton model 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | ID of the bound bone model (see GetModelId of the model component) | 
| boneName | str | Name of the specific bone to be bound | 
| offset | tuple(float,float,float) | Binding offset | 
| rot | tuple(float,float,float) | Binding rotation angle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleSkeletonBind(particleEntityId) 
comp.Bind(modelId, "root", (0, 1, 0), (0, 0, 0)) 
``` 

## CreateEngineParticle 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.system.clientSystem.ClientSystem 

- Description 

Used to create particle effects 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| path | str | Effect resource path, need to add suffix (usually json) | 
| pos | tuple(float,float,float) | Create position coordinates | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int or None | particleEntityId or None | 

- Notes 
- After creating particles, you can use the returned particleEntityId to create related components in the client particle classification and set the required properties to achieve various performance effects. 
- After switching dimensions, particles that are not created in this dimension and have no bound entities will be automatically hidden, and will automatically redisplay after returning to this dimension. 
- After particles are created, the Play function of the particleControl component needs to be called to play. If particles that are not created in this dimension are played, the creation dimension of the particle will be modified to the current dimension at the same time.


- Example

```python
import mod.client.extraClientApi as clientApi
class MyClientSystem(ClientSystem):
    # Create
    def createParticle(self):
        particleEntityId = self.CreateEngineParticle("effects/fire.json", (0,5,0))
        particleControlComp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId)
        particleControlComp.Play()

    # delete
    def removeParticle(self, particleEntityId):
        self.DestroyEntity(particleEntityId)
```



## GetParticleEmissionRate

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.particleControlComp.ParticleControlComp

- describe

Get the frequency of the particle emitter emitting particles per frame. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | The frequency of the particle emitter emitting particles per frame. | 

- Notes 
- The value obtained by this interface corresponds to the value of "emissionrate" in the particle effect json file 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
comp.GetParticleEmissionRate() 
``` 




## GetParticleMaxNum 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Get the maximum number of particles contained in the particle emitter. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | The maximum number of particles contained in the particle emitter. | 

- Notes 
- The value obtained by this interface corresponds to the value of "numparticles" in the particle effect json file 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
comp.GetParticleMaxNum() 
``` 

## GetParticleMaxSize 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Get the maximum size of particles in particle effects. 

- Parameters 

None 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Maximum value of particle size | 

- Notes 
- The value obtained by this interface corresponds to the "max" value of "particlesize" in the particle effect json file. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
comp.GetParticleMaxSize() 
``` 

## GetParticleMinSize 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Get the minimum size of particles in particle effects. 

- Parameters 

None 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Minimum size of particles. | 

- Notes 
- The value obtained by this interface corresponds to the "min" value of "particlesize" in the particle effect json file. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
comp.GetParticleMinSize() 
``` 




## GetParticleVolumeSize 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Get the volume size scaling value of the particle emitter. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Volume size scaling value of the particle emitter. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
comp.GetParticleVolumeSize() 
``` 

## GetPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleTransComp.ParticleTransComp 

- Description 

Get the world coordinate position of the particle emitter 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Returns the world coordinate position of the particle emitter |


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleTrans(particleEntityId) 
comp.GetPos() 
``` 

## GetRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleTransComp.ParticleTransComp 

- Description 

Get the rotation angle of the particle emitter 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Returns the rotation angle of the particle emitter | 

- Notes 
- Note that when using SetRotation to set the rotation angle, the rotation of the x-axis direction is close to 90 degrees or -90 degrees. At this time, due to the singularity of the rotation, there will be a division by 0 problem when calculating the rotation angle. Therefore, in order to avoid this situation, the calculation formula for the singular case will be used for calculation. In this case, the interface returns the rotation angle equivalent to the value set by the SetRotUseZXY interface. 
- The rotation value obtained by this interface corresponds to the rotation value set by the interface SetRotUseZXY. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleTrans(particleEntityId) 
comp.GetRot() 
``` 

## Pause 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp


- Description 

Pause playback, freeze the particles at the current moment, and continue playing when Play is called again 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
comp.Pause() 
``` 

## Play 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Play particle effects 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId)

comp.Play() 
``` 

## SetFadeDistance 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Sets the distance at which particles start to automatically adjust transparency. When the distance between the particle and the camera is less than this value, the transparency of the particle will be automatically adjusted. The closer the distance to the camera, the more transparent the particle. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| fadeDistance | float | The distance for automatically adjusting transparency. It should be a positive number. Negative numbers will be treated as zero. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
# Set the particle to automatically adjust transparency when the distance from the camera is less than 3 
comp.SetFadeDistance(3) 
``` 

## SetLayer 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

The default level of particles is 1. When the level is not 1, it means that the special effect has enabled the special effect layered rendering function. When special effects (particles and frame animations) are rendered in layers, the higher the level, the later the rendering. The larger the level, the lower the level will be. And the special effects at the same level will have the correct mutual occlusion relationship according to the relative position of the special effects. 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| layer | int | Particle rendering level, including 0-15 levels in total. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- This interface is only used for particle settings. For sequence frame effects, please use the frameAniControl component 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
# Set the rendering level to 2 
comp.SetLayer(2) 
``` 

## SetParticleEmissionRate 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Set the frequency of particle emission per frame. The higher the frequency, the more particles are emitted per frame, but the number of particles will not exceed the particle capacity of the particle emitter. At the same time, due to performance considerations, the number of particles emitted per frame will not exceed 100. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| minRate | float | The minimum frequency of particle emission per frame. The frequency of particle emission per frame will be interpolated between the minimum frequency and the maximum frequency. When this value is set to a negative value, the setting will fail, and the value cannot be greater than the maximum particle frequency. | 
| maxRate | float | The maximum frequency of particle emission per frame. The frequency of particle emission per frame will be interpolated between the minimum frequency and the maximum frequency. When this value is set to a negative value, the setting will fail, and the value cannot be less than the minimum particle frequency. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The value set by this interface corresponds to the value of "emissionrate" in the particle effect json file 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
# Expand the particle capacity of the particle emitter 
comp.SetParticleMaxNum(1000) 
# Increase the frequency of particle emission 
comp.SetParticleEmissionRate(15,20) 
``` 

## SetParticleMaxNum 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Set the particle capacity of the particle emitter, that is, the maximum number of particles contained in the particle emitter. This number does not represent the number of particles currently emitted by the particle emitter. If you need to increase the number of emitted particles, you need to change the particle emission frequency at the same time. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| num | int | The maximum number of particles contained in the particle emitter. It cannot be a negative value. The maximum number of particles does not exceed 100,000. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- For performance reasons, please be careful not to set the number of particles too large. The value set by this interface corresponds to the value of "numparticles" in the particle effect json file 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
comp.SetParticleMaxNum(1000) 
``` 

## SetParticleSize 


<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Set the minimum and maximum values of the particle size in the particle effect. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| minSize | tuple(float,float) | The minimum value of the particle size (x,y). The x value affects the degree of stretching of the particle to the left and right, and the y value affects the degree of stretching of the particle to the top and bottom. The particle size in the particle effect will be determined by taking a random value between the minimum and maximum values. When this value is set to a negative value, the setting will fail, and this value cannot be greater than the maximum particle size. | 
| maxSize | tuple(float,float) | The maximum value of the particle size (x,y). The x value affects the left and right stretching of the particle, and the y value affects the up and down stretching of the particle. The particle size in the particle effect is determined by taking a random value between the minimum and maximum values. When the value is set to a negative value, the setting will fail, and the value cannot be smaller than the minimum value of the particle size. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The value set by this interface corresponds to the value of "particlesize" in the particle effect json file. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
comp.SetParticleSize((0.5,0.5),(0.6,0.6)) 
``` 

## SetParticleVolumeSize 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Set the volume size of the particle emitter, without affecting the size of individual particles. The larger the volume of the particle emitter, the larger the emission range of the particles. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| scale | tuple(float,float,float) | Volume scaling value of the particle emitter (x,y,z), x,y,z are the scaling values of each coordinate axis direction respectively, the larger the value, the larger the range of particles emitted in that direction. | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- This setting is invalid when the particle is bound to an entity 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
comp.SetParticleVolumeSize((1,0,0)) 
``` 

## SetPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleTransComp.ParticleTransComp 

- Description 

Set the world coordinate position of the particle emitter 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | World coordinates | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleTrans(particleEntityId) 
comp.SetPos((0, 5, 0)) 
``` 




## SetRelative 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

When particles are bound to an entity or a skeleton model, the emitted particles use the entity coordinate system or the world coordinate system. This is the same as the "Relative Hanging Point Movement" option for particles in the mcstudio special effects editor. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| relative | bool | True indicates relative coordinate system, False indicates world coordinate system | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
# Use world coordinate system 
comp.SetRelative(False) 
``` 

## SetRotUseZXY 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleTransComp.ParticleTransComp 

- Description 

Set the rotation of the particle emitter. The rotation order is around the z, x, and y axes. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rot | tuple(float,float,float) | The angle of rotation around the +z, +x, and +y axes of the local coordinate system. The rotation order is around the z, x, and y axes. | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleTrans(particleEntityId) 
# Rotate 90 degrees around the z axis, then rotate 90 degrees around the y axis 
comp.SetRotUseZXY((0, 90, 90)) 
``` 

## SetUsePointFiltering 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Sets whether the texture filtering of the particle material uses the point filtering method. The default is to use bilinear filtering 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| enable | bool | true is to use the point filtering method, false is to use the default bilinear filtering | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Images using point filtering usually have clear edges and may have a strong sense of aliasing; images using bilinear interpolation are usually smoother and may make the image blurred to a certain extent 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
# Set point filtering 
comp.SetUsePointFiltering(True) 
comp.Play()

``` 

## Stop 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.particleControlComp.ParticleControlComp 

- Description 

Stop particle playback 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId) 
comp.Stop() 
``` 

