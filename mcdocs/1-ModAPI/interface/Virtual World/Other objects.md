--- 
sidebarDepth: 1 
--- 
# Other objects 

## BindModel 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Binds an object to a model, supports binding sequence frames, particles, text and other models 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| virtualWorldObjectType | int | Object type enumeration, supports VirtualWorldObjectType.Sfx, VirtualWorldObjectType.Textboard and VirtualWorldObjectType.Particle, VirtualWorldObjectType.Model | 
| objId | int | The id of the object to be bound | 
| targetId | int | id of the target object to bind to. When the object is deleted, the object bound to it will also be deleted | 
| posOffset | tuple(float,float,float) | position offset relative to the target after binding | 
| rotOffset | tuple(float,float,float) | rotation angle offset relative to the target after binding | 
| boneName | str | which bone to bind to the target object, the default is root | 

- return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Notes 
- Model binding model does not currently support binding to specific bones 
- Model binding only supports original model binding to original model, or NetEase bone model binding to NetEase bone model, and does not support original model binding to NetEase bone model. This type of staggered binding 
- The life cycle and visibility of sequence frames, texts, and particles need to be managed by the player themselves, and the virtual world does not process them when they are hidden or destroyed. 

- Example

```python
import client.extraClientApi as clientApi
VirtualWorldObjectType = clientApi.GetMinecraftEnum().VirtualWorldObjectType
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId())
objId = virtualWorldComp.ModelCreateObject("datiangou", "run")

# Sequence frame
frameEntityId = self.CreateEngineSfx("textures/sfxs/testSfx")
frameAniTransComp = clientApi.GetEngineCompFactory().CreateFrameAniTrans(frameEntityId)
frameAniControlComp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId)
frameAniControlComp.SetLoop(True)

frameAniControlComp.Play()
virtualWorldComp.BindModel(VirtualWorldObjectType.Sfx, frameEntityId, objId, (0.0, 3.0, 0.0), (0.0, 0.0, 0.0), "root")

# text
textBoardComp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId())
textBoardId = textBoardComp.CreateTextBoardInWorld("Hello", (0.5, 0.4, 0.3, 0.8), (0, 0, 0, 1), True)
virtualWorldComp.BindModel(VirtualWorldObjectType.Textboard, textBoardId, objId, (0.0, 3.0, 0.0), (0.0, 0.0, 0.0), "root")

# particle
particleEntityId = self.CreateEngineParticle("effects/testParticle.json", (0.0, 0.0, 0.0))
parComp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId)
parComp.Play()
virtualWorldComp.BindModel(VirtualWorldObjectType.Particle, particleEntityId, objId, (0.0, 3.0, 0.0), (0.0, 0.0, 0.0), "root")

# Model
childObj = virtualWorldComp.ModelCreateObject("datiangou", "fengxi")
virtualWorldComp.BindModel(VirtualWorldObjectType.Model, childObj, objId, (-1.0, 0.0, 0.0), (0.0, 0.0, 0.0)) 
``` 

## MoveToVirtualWorld 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Move objects from the main world to the virtual world. Non-bound sequence frames, texts, and particles need to call this method before they appear in the virtual world. Bound ones can omit calling this method. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| virtualWorldObjectType | int | Object type enumeration, supports VirtualWorldObjectType.Sfx, VirtualWorldObjectType.Textboard and VirtualWorldObjectType.Particle | 
| objId | int | The id of the object to be moved | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python 
import client.extraClientApi as clientApi 
VirtualWorldObjectType = clientApi.GetMinecraftEnum().VirtualWorldObjectType 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId())


# Sequence frame
frameEntityId = self.CreateEngineSfx("textures/sfxs/testSfx")
frameAniTransComp = clientApi.GetEngineCompFactory().CreateFrameAniTrans(frameEntityId)
frameAniTransComp.SetPos((0.0, 0.0, 0.0))
frameAniControlComp = clientApi.GetEngineCompFactory().CreateFrameAniControl(frameEntityId)
frameAniControlComp.SetLoop(True)
frameAniControlComp.Play()
virtualWorldComp.MoveToVirtualWorld(VirtualWorldObjectType.Sfx, frameEntityId)

# text
textBoardComp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId())
textBoardId = textBoardComp.CreateTextBoardInWorld("Hello", (0.5, 0.4, 0.3, 0.8), (0, 0, 0, 1), True)
virtualWorldComp.MoveToVirtualWorld(VirtualWorldObjectType.Textboard, textBoardId)

# particles
particleEntityId = self.CreateEngineParticle("effects/testParticle.json", (0.0, 0.0, 0.0))
parComp = clientApi.GetEngineCompFactory().CreateParticleControl(particleEntityId)
parComp.Play()
virtualWorldComp.MoveToVirtualWorld(VirtualWorldObjectType.Particle, particleEntityId)
```