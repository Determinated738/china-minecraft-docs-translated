--- 
sidebarDepth: 1 
--- 
# Sequence Frame 

## Bind 

<span style="display:inline;color:#7575f9">Client</span> 

<span id="0"></span> 
method in mod.client.component.frameAniEntityBindComp.FrameAniEntityBindComp 

- Description 

Bind entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| bindEntityId | str | ID of the bound entity | 
| offset | tuple(float,float,float) | Offset of the bound entity | 
| rot | tuple(float,float,float) | Rotation angle of the bound entity | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniEntityBind(frameEntityId) 
comp.Bind(entityId, (0, 1, 0), (0, 0, 0)) 
``` 

<span id="1"></span> 
method in mod.client.component.frameAniSkeletonBindComp.FrameAniSkeletonBindComp 

- Description 

Bind skeleton model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| modelId | int | ID of the bound skeleton model (see GetModelId of the model component) | 
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
comp = clientApi.GetEngineCompFactory().CreateFrameAniSkeletonBind(frameEntityId) 
comp.Bind(modelId, "root", (0, 1, 0), (0, 0, 0)) 
``` 

## CreateEngineSfx 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.system.clientSystem.ClientSystem 

- Description 

Create sequence frame special effects 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| path | str | Special effect resource path, no suffix | 
| pos | tuple(float,float,float) | Create position, optional, if not passed, you can use frameAniTrans component settings after creation | 
| rot | tuple(float,float,float) | Angle, optional, if not passed, you can use frameAniTrans component settings after creation | 
| rot | tuple(float,float,float) | Angle, optional, if not passed, you can use frameAniTrans component settings after creation | 
| scale | tuple(float,float,float) | Scaling factor, optional. If not passed, you can use the frameAniTrans component to set it after creation | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int or None | frameEntityId or None | 

- Notes 
- After creating a sequence frame, you can use the returned frameEntityId to create related components in the sequence frame classification and set the required properties to achieve various performance effects 
- After switching dimensions, sequence frames that are not created in this dimension and have no bound entities will be automatically hidden, and will be automatically redisplayed after returning to this dimension

- Please note that after the sequence frame is created, the play function of the frameAniControl component needs to be called before it can be played. If a sequence frame created in a dimension other than the current dimension is played, the creation dimension of the sequence frame will be modified to the current dimension at the same time 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
class MyClientSystem(ClientSystem): 
# Create 
def createSfx(self): 
frameEntityId = self.CreateEngineSfx("textures/sfxs/snow_3") 
frameAniTransComp = clientApi.GetEngineCompFactory().CreateFrameAniTrans(frameEntityId) 
frameAniTransComp.SetPos((10,10,10)) 
frameAniTransComp.SetRot((0,0,0)) 
frameAniTransComp.SetScale((1,1,1)) 
frameAniControlComp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId) 
frameAniControlComp.Play() 

# Delete 
def removeSfx(self, frameEntityId): 
self.DestroyEntity(frameEntityId) 
``` 

## CreateEngineSfxFromEditor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.system.clientSystem.ClientSystem 

- Description 

Refers to using effects/xxx.json in the resource package to create a sequence frame according to the parameters edited in the editor. Supports circular sequence frames 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| path | str | Effect configuration path, needs to be "effects/xxx.json", "xxx" is the name filled in when the editor creates a sequence frame | 
| pos | tuple(float,float,float) | Creation position, optional, if not passed, you can use the frameAniTrans component to set it after creation, generally you need to set the playback position | 
| rot | tuple(float,float,float) | Angle, optional, if not passed, you can use the frameAniTrans component to set it after creation | 
| scale | tuple(float,float,float) | Scaling factor, optional, if not passed, you can use the frameAniTrans component to set it after creation | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int or None | frameEntityId or None | 

- Notes

- After creating a sequence frame, you can use the returned frameEntityId to create related components in the sequence frame classification and set the required properties to achieve various performance effects. 
- It should be noted that after the sequence frame is created, the play function of the frameAniControl component needs to be called to play it. 
- After generating the sequence frame according to the editor configuration, you also need to set the position or binding and play it. 

- Example

```python
import mod.client.extraClientApi as clientApi
class MyClientSystem(ClientSystem):
    # Create
    def createSfxFromEditor(self):
        frameEntityId = self.CreateEngineSfxFromEditor("effects/mySfx.json")
        frameAniTransComp = clientApi.GetEngineCompFactory().CreateFrameAniTrans(frameEntityId)
        frameAniTransComp.SetPos((10,10,10))
        frameAniTransComp.SetRot((0,0,0))
        frameAniTransComp.SetScale((1,1,1))
        frameAniControlComp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId)
        frameAniControlComp.Play()

    # delete
    def removeSfx(self, frameEntityId): 
self.DestroyEntity(frameEntityId) 
``` 

## GetPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniTransComp.FrameAniTransComp 

- Description 

Get the position of the sequence frame effect 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Returns the world coordinate position of the sequence frame effect. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi

comp = clientApi.GetEngineCompFactory().CreateFrameAniTrans(frameEntityId) 
comp.GetPos() 
``` 
## GetRot 
<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniTransComp.FrameAniTransComp 

- Description 

Get the rotation angle of the sequence frame effect 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Returns the rotation angle of the sequence frame effect. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniTrans(frameEntityId) 
comp.GetRot() 
``` 

## GetScale 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniTransComp.FrameAniTransComp 

- Description 

Get the scale value of the sequence frame effect 

- Parameters 

None 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Returns the scaling value of the sequence frame effect. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniTrans(frameEntityId) 
comp.GetScale() 
``` 

## Pause 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniControlComp.FrameAniControlComp 

- Description 

Pause playback, freeze the sequence frame at the current moment, and continue playing when Play is called again 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId)
comp.Pause()
```



## Play

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.frameAniControlComp.FrameAniControlComp 

- Description 

Play sequence frames 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId) 
comp.Play() 
``` 

## SetDeepTest 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniControlComp.FrameAniControlComp 

- Description 

Set whether the sequence frame is perspective, the default is no 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| deepTest | bool | False means perspective, then the sequence frame can still be seen when blocked by objects/blocks | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId) 
# Set to perspective 
comp.SetDeepTest(False) 
``` 

## SetFaceCamera 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniControlComp.FrameAniControlComp 

- Description 

Sets whether the sequence frame is always facing the camera, the default is yes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| face | bool | True means facing the camera | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId) 
# Set to not always face the camera 
comp.SetFaceCamera(False) 
``` 

## SetFadeDistance 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniControlComp.FrameAniControlComp 

- Description 


Set the distance at which the sequence frame starts to automatically adjust the transparency. When the distance between the sequence frame and the camera is less than this value, the transparency of the sequence frame will be automatically adjusted. The closer the distance to the camera, the more transparent the sequence frame is. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| fadeDistance | float | The distance for automatically adjusting the transparency, which should be a positive number. Negative numbers will be treated as zero. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId) 
# Set the sequence frame to automatically adjust the transparency when the distance from the camera is less than 3 
comp.SetFadeDistance(3) 
``` 
## SetLayer 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.frameAniControlComp.FrameAniControlComp 
- Description 
Set the sequence frame rendering level. The default level is 1. When the level is not 1, it means that the special effect has enabled the special effect layered rendering function. When special effects (particles and frame animations) are rendered in layers, the higher the level, the later the rendering. The larger the level, the lower the level will be. And the special effects of the same level will have the correct mutual occlusion relationship according to the relative position of the special effects. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| layer | int | Particle rendering level, including 0-15 levels in total. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- This interface is only set for sequence frames. For particle effects, please use the particleControl component 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId) 
# Set the rendering layer to 2 
comp.SetLayer(2) 
``` 

## SetLoop 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniControlComp.FrameAniControlComp 

- Description 

Set whether the sequence frame is played in a loop, the default is no 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| loop | bool | True means loop playback | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId) 
# Set to loop playback 
comp.SetLoop(True) 
``` 

## SetMixColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniControlComp.FrameAniControlComp 


- Description 

Set the sequence frame mixed color 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| color | tuple(float,float,float,float) | RGBA value of the color, range 0-1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId) 
# Set the color to red semi-transparent 
color = (1, 0, 0, 0.5) 
comp.SetMixColor(color) 
``` 
## SetPos 
<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniTransComp.FrameAniTransComp 

- Description 

Set the position of the sequence frame 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(float,float,float) | World coordinates | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniTrans(frameEntityId) 
comp.SetPos((0, 5, 0)) 
``` 

## SetRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniTransComp.FrameAniTransComp 

- Description 

Set the rotation of the sequence frame 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rot | tuple(float,float,float) | Angle of rotation around the +x, -y, +z axis of the local coordinate system in order | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniTrans(frameEntityId) 
# Rotate 90 degrees around the y axis, then rotate 90 degrees around the z axis 
comp.SetRot((0, 90, 90)) 
``` 

## SetRotUseZXY 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniTransComp.FrameAniTransComp

- describe


Set the rotation of the sequence frame. The rotation order is around the z, x, and y axes. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rot | tuple(float,float,float) | The rotation angle around the +z, +x, and +y axes of the local coordinate system. The rotation order is around the z, x, and y axes. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniTrans(frameEntityId) 
# Rotate 90 degrees around the z axis, then rotate 90 degrees around the y axis 
comp.SetRotUseZXY((0, 90, 90)) 
``` 

## SetScale 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniTransComp.FrameAniTransComp 

- Description 

Set the scale of the sequence frame 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| scale | tuple(float,float,float) | For planar sequence frames, the first parameter is the horizontal scale of the texture, the second parameter is the vertical scale, and the third parameter is useless. For circular sequence frames, it is the scale on three coordinate axes | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniTrans(frameEntityId) 
# Horizontal stretch is 2 times, vertical unchanged 
comp.SetScale((2, 1, 1)) 
``` 

## SetUsePointFiltering 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniControlComp.FrameAniControlComp 

- Description 

Set whether to use point filtering for sequence frames 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| use | bool | True is to use point filtering, False is to use bilinear interpolation (default) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Images using point filtering usually have clear edges and may have a strong sense of aliasing; images using bilinear interpolation are usually smoother and may make the image blurred to a certain extent 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId) 
# Set the sequence frame to use point filtering 
comp.SetUsePointFiltering(True) 
``` 

## Stop 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.frameAniControlComp.FrameAniControlComp


- Description 

Stop sequence frames (not pause) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId) 
comp.Stop() 
``` 

