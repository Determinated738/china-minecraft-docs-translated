--- 
sidebarDepth: 1 
--- 
# Model 

# Index 

Including bone model related interfaces 

--- 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [BindModelToEntity](Model.md#bindmodeltoentity) | <span style="display:inline;color:#7575f9">Client</span> | After the entity replaces the bone model, other bone models are attached. | 
| [BindModelToModel](Model.md#bindmodeltomodel) | <span style="display:inline;color:#7575f9">Client</span> | Attach other bone models to the bone model | 
| [CancelAllBoneMask](Model.md#cancelallbonemask) | <span style="display:inline;color:#7575f9">Client</span> | Cancel all bone masks in the animation. | 
| [CreateFreeModel](Model.md#createfreemodel) | <span style="display:inline;color:#7575f9">Client</span> | Create a free model (no need to bind Entity) | 
| [GetAllBindModelToEntity](Model.md#getallbindmodeltoentity) | <span style="display:inline;color:#7575f9">Client</span> | Get the ids of all bone models attached to a bone on the entity | 
| [GetAnimLength](Model.md#getanimlength) | <span style="display:inline;color:#7575f9">Client</span> | Get the length of a bone animation in seconds | 
| [GetBoneWorldPos](Model.md#getboneworldpos) | <span style="display:inline;color:#7575f9">Client</span> | Get the coordinates of the bone | 
| [GetEntityBoneWorldPos](Model.md#getentityboneworldpos) | <span style="display:inline;color:#7575f9">Client</span> | Get the bone coordinates of the entity with the changed bone model | 
| [GetEntityScale](Model.md#getentityscale) | <span style="display:inline;color:#ff5555">Server</span> | Get the scale ratio of the entity | 
| [GetModelId](Model.md#getmodelid) | <span style="display:inline;color:#7575f9">Client</span> | Get the ID of the bone model, mainly used for special effects binding bone model | 
| [GetModelName](Model.md#getmodelname) | <span style="display:inline;color:#ff5555">Server</span> | Get the model name of the entity | 
| [GetPlayingAnimList](Model.md#getplayinganimlist) | <span style="display:inline;color:#7575f9">Client</span> | Get the name list of the skeleton animations currently being played in the specified skeleton model | 
| [GetTexture](Model.md#gettexture) | <span style="display:inline;color:#7575f9">Client</span> | Get the texture path of the skeleton model | 
| [HideModel](Model.md#hidemodel) | <span style="display:inline;color:#7575f9">Client</span> | Hide pure model | 
| [ModelPlayAni](Model.md#modelplayani) | <span style="display:inline;color:#7575f9">Client</span> | Pure skeleton playback action. Supports skeletal animation blending. Please refer to the description of SetAnimationBoneMask interface and RegisterAnim1DControlParam interface. | 
| [ModelStopAni](Model.md#modelstopani) | <span style="display:inline;color:#7575f9">Client</span> | Pause the specified skeletal animation | 
| [PlayAnim](Model.md#playanim) | <span style="display:inline;color:#7575f9">Client</span> | Play skeletal animation | 
| [RegisterAnim1DControlParam](Model.md#registeranim1dcontrolparam) | <span style="display:inline;color:#7575f9">Client</span> | When playing multiple skeletal animations at the same time, create a new parameter for controlling the animation for 1D linear blending. Currently, linear blending only supports blending of two animations. The value range of the new parameter is [0,1]. The specified bone will linearly blend the two animations according to the value of this parameter. | 
| [RemoveFreeModel](Model.md#removefreemodel) | <span style="display:inline;color:#7575f9">Client</span> | Remove the free model | 
| [ResetModel](Model.md#resetmodel) | <span style="display:inline;color:#7575f9">Client</span> | Restore the entity to the original model | 
| [SetAnim1DControlParam](Model.md#setanim1dcontrolparam) | <span style="display:inline;color:#7575f9">Client</span> | After creating the 1D control parameters of the animation, use this interface to control the corresponding parameters. | 
| [SetAnimLayer](Model.md#setanimlayer) | <span style="display:inline;color:#7575f9">Client</span> | Set the level of the skeleton animation. The higher the animation level, the higher the priority. The skeleton model's bones will play the animation with the highest priority first. The animations of the same level will play the animation that is played first. | 
| [SetAnimSpeed](Model.md#setanimspeed) | <span style="display:inline;color:#7575f9">Client</span> | Set the playback speed of a skeleton animation | 
| [SetAnimationAllBoneMask](Model.md#setanimationallbonemask) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to mask the animation of all bones in the animation. If the bone mask is turned on, the bone will no longer play the actions in the animation. This interface will take effect on all bones in the animation. The parameter ignoreBoneList can be used to specify the names of bones that are not affected. By shielding the animation of the specified bones, the same skeletal model can play different action animations on different bones at the same time, thereby achieving quick action fusion. | 
| [SetAnimationBoneMask](Model.md#setanimationbonemask) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to shield the animation of the specified bones in the animation. If the bone shield is turned on, the bone will no longer play the actions in the animation. By shielding the animation of the specified bones, the same skeletal model can play different action animations on different bones at the same time, thereby achieving quick action fusion. | 
| [SetBrightness](Model.md#setbrightness) | <span style="display:inline;color:#7575f9">Client</span> | Set the brightness of the entity | 
| [SetEntityOpacity](Model.md#setentityopacity) | <span style="display:inline;color:#7575f9">Client</span> | Set the transparency of the skeleton model. It can only be applied to the skeleton model. If the setting is for the original model, the model's shadow will be hidden. | 
| [SetEntityScale](Model.md#setentityscale) | <span style="display:inline;color:#ff5555">Server</span> | Set the scale of the entity. Setting the scale too large will cause game lag. It is recommended to control it within 20 times. | 
| [SetEntityShadowShow](Model.md#setentityshadowshow) | <span style="display:inline;color:#7575f9">Client</span> | Set the entity to turn on/off shadow rendering | 
| [SetExtraUniformValue](Model.md#setextrauniformvalue) | <span style="display:inline;color:#7575f9">Client</span> | Set the value of a specific uniform in the shader | 
| [SetFreeModelAniSpeed](Model.md#setfreemodelanispeed) | <span style="display:inline;color:#7575f9">Client</span> | Set the playback speed of the free model animation | 
| [SetFreeModelBoundingBox](Model.md#setfreemodelboundingbox) | <span style="display:inline;color:#7575f9">Client</span> | Set the bounding box of the free model | 
| [SetFreeModelPos](Model.md#setfreemodelpos) | <span style="display:inline;color:#7575f9">Client</span> | Set the position of the free model | 
| [SetFreeModelRot](Model.md#setfreemodelrot) | <span style="display:inline;color:#7575f9">Client</span> | Set the direction of the free model | 
| [SetFreeModelScale](Model.md#setfreemodelscale) | <span style="display:inline;color:#7575f9">Client</span> | Set the size of the free model | 
| [SetLegacyBindRot](model.md#setlegacybindrot) | <span style="display:inline;color:#7575f9">Client</span> | Used to fix the direction of special effects when attached to the skeleton | 
| [SetModel](model.md#setmodel) | <span style="display:inline;color:#ff5555">Server</span> | Set the skeleton model |

| [SetModel](Model.md#setmodel) | <span style="display:inline;color:#7575f9">Client</span> | Replace the skeletal model of the entity | 
| [SetModelOffset](Model.md#setmodeloffset) | <span style="display:inline;color:#ff5555">Server</span> | Set the offset of the skeletal model relative to the local coordinate system, the initial value is (0, 0, 0) | 
| [SetModelOffset](Model.md#setmodeloffset) | <span style="display:inline;color:#7575f9">Client</span> | Add offset to the model | 
| [SetModelPerspectiveEffect](Model.md#setmodelperspectiveeffect) | <span style="display:inline;color:#7575f9">Client</span> | Set the model perspective effect. Note: Only works for custom skeleton models | 
| [SetModelTexture](Model.md#setmodeltexture) | <span style="display:inline;color:#ff5555">Server</span> | Set the skeleton model texture. This interface has the same function as SetTexture, but belongs to the server interface. | 
| [SetShowArmModel](Model.md#setshowarmmodel) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to display the hand model when switching to the first person view after using the skeleton model. You need to define arm_model for the skeleton model first. The definition of arm_model can refer to the definition of the Daitengu model in resourcePack/models/netease_models.json in the demo example-AwesomeMod | 
| [SetTexture](Model.md#settexture) | <span style="display:inline;color:#7575f9">Client</span> | Set the texture of the skeleton model. This interface has the same function as SetModelTexture, but it belongs to the client interface. | 
| [ShowCommonHurtColor](Model.md#showcommonhurtcolor) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the entity attached to the skeletal model displays the common red hurt effect | 
| [ShowCommonHurtColor](Model.md#showcommonhurtcolor) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the entity attached to the skeletal model displays the common red hurt effect | 
| [ShowModel](Model.md#showmodel) | <span style="display:inline;color:#7575f9">Client</span> | Show pure model | 
| [UnBindModelToEntity](Model.md#unbindmodeltoentity) | <span style="display:inline;color:#7575f9">Client</span> | Unbind a skeletal model attached to an entity. After unbinding, the model with this modelId will be destroyed and cannot be used anymore. If it is temporarily hidden, you can use HideModel | 
| [UnBindModelToModel](Model.md#unbindmodeltomodel) | <span style="display:inline;color:#7575f9">Client</span> | Unbind a skeletal model attached to a skeletal model. After unbinding, the model with this modelId will be destroyed and cannot be used anymore. If it is temporarily hidden, you can use HideModel | 

## BindModelToEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

After the entity replaces the skeletal model, attach other skeletal models upwards. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| boneName | str | Name of the bone to be attached | 
| modelName | str | Name of the bone model to be attached | 
| offset | tuple(float,float,float) | Offset | 
| rot | tuple(float,float,float) | Rotation | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | The ID of the bone model attached to the bone, -1 if failed | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
# Attach the skeleton model named gun to the rightHand skeleton 
gunModelId = comp.BindModelToEntity("rightHand", "gun") 
``` 

## BindModelToModel


<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Attach other bone models to the bone model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| boneName | str | Name of the bone to be attached | 
| modelName | str | Name of the bone model to be attached | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Id of the bone model attached to the bone, return -1 if failed | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(11) 
# Attach the skeleton model named gun to the rightHand skeleton of the model with modelId 11 
gunModelId = comp.BindModelToModel("rightHand", "gun") 
``` 

## CancelAllBoneMask 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Cancel all skeleton masks in the animation. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | Model id that needs to be set, including entity model and free model | 
| aniName | str | Animation name | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.CancelAllBoneMask(modelId, "attack") 
``` 

## CreateFreeModel 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Create a free model (no need to bind Entity) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelName | str | model name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Return modelId if created successfully, 0 if created failed | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
model = comp.CreateFreeModel(modelName) 
``` 

## GetAllBindModelToEntity 


<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Get the ids of all bone models attached to a bone on the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| boneName | str | The name of the bone to be obtained | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(int) | List of bone model ids | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
modelIds = comp.GetAllBindModelToEntity("rightHand") 
``` 

## GetAnimLength 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Get the length of a skeletal animation in seconds 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| aniName | str | Skeletal animation name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| float | Bone animation length | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
# Get the length of the run animation 
animLength = comp.GetAnimLength('run') 
``` 

## GetBoneWorldPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Get the coordinates of the bone 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| boneName | str | Bone name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(int,int,int) | Position coordinates | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
bPos = comp.GetBoneWorldPos(boneName) 
``` 

## GetEntityBoneWorldPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient


- Description 

Get the bone coordinates of the entity with a changed bone model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| boneName | str | Bone name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(int,int,int) | Position coordinates | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
bPos = comp.GetEntityBoneWorldPos(entityId, boneName) 
``` 

## GetEntityScale 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.scaleCompServer.ScaleComponentServer 

- Description 

Get the scale ratio of the entity 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Scale factor | 

- Example 


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateScale(entityId) 
result = comp.GetEntityScale() 
``` 

## GetModelId 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Get the id of the skeleton model, mainly used for binding the skeleton model with special effects 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | The id of the current skeleton model instance | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
modelId = comp.GetModelId() 
``` 

## GetModelName 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.modelCompServer.ModelComponentServer 

- Description 

Get the model name of the entity 

- Parameters 


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Model name | 

- Notes 
- Obtained on the server, not effective on the client 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateModel(entityId) 
modelName = comp.GetModelName() 
``` 

## GetPlayingAnimList 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Get the list of skeletal animation names currently playing in the specified skeletal model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | Skeleton model Id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Skeleton animation name list | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
playingAnimList = comp.GetPlayingAnimList(modelId) 
```



## GetTexture 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Get the texture path of the skeleton model 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Texture path, relative to textures\models | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
texturePath = comp.GetTexture() 
``` 

## HideModel 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Hide pure model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | modelId to be hidden | 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None | No return value | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.HideModel(modelId) 
``` 

## ModelPlayAni 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Pure skeleton playback action. Supports skeleton animation mixing, please refer to the SetAnimationBoneMask interface and RegisterAnim1DControlParam interface description. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | Model id to be set, including entity model and free model. | 
| aniName | str | Animation name to be set | 
| isLoop | bool | Whether to loop playback, default is False | 
| isBlended | bool | Whether to blend with the current animation or terminate the current animation during playback, default is False, that is, terminate the current animation playback. When set to True, the animation to be played will be allowed to blend. Note that animation blending is only performed between animations of the same level. If the currently playing animation and the animation to be played are at different levels, the isBlended parameter is invalid. | 
| layer | int | Set the level of the skeletal animation, ranging from 0 to 255, default is 0. Note that if the animation to be played already exists, the original animation level will be overwritten. The higher the animation level, the higher the priority. The skeleton model's skeleton plays the animation with the highest priority first. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- When the animation levels are the same, the priority order of the animation is determined by: 1. Whether it needs to be mixed with other animations. 2. Whether it is played first. For example, we first use the interface RegisterAnim1DControlParam to register the 1D linear mixing parameter alpha for animation A and animation B, and then use the interface RegisterAnim1DControlParam to register the linear mixing parameter beta for animation A and animation C. Then, play animation A, animation C, animation B, and animation D in sequence. At this time, since animation A and animation C need to be mixed and played first, the skeleton model will first play the mixed animation of animation A and animation C (note that the initial value of the 1D linear mixing parameter is 0, so the performance of the mixed animation is still animation A). If animation C is paused at this time, the mixed animation of animation A and animation B will be played. Then pause animation B, animation A will be played, and finally pause animation A again, and animation D will be played. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.ModelPlayAni(modelId, 'run', True, False, 0)

``` 

## ModelStopAni 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Pause the specified skeleton animation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| modelId | int | Model id to be set, including entity model and free model | 
| aniName | str | Animation name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.ModelStopAni(modelId, "attack") 
``` 

## PlayAnim 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Play skeletal animation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| aniName | str | Animation name | 
| isLoop | bool | Whether to play in a loop | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.PlayAnim("run", True) 
``` 

## RegisterAnim1DControlParam 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

When playing multiple bone animations at the same time, create a new parameter to control the 1D linear blending of animations. Currently, linear blending only supports blending of two animations. The value range of the new parameter is [0,1]. The specified bone will linearly blend the two animations according to the value of this parameter. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | The model id that the bone needs to set, including entity models and free models. | 
| leftAniName | str | The name of the first animation to be blended. When the value of the 1D parameter is 0, the specified bone only plays this animation. | 
| rightAniName | str | The name of the second animation to be blended. When the value of the 1D parameter is 1, the specified bone only plays this animation. | 
| paramName | str | The name of the custom 1D parameter. The initial value of this parameter after creation is 0. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Note that if a bone mask is used for a bone, this 1D linear blend will not take effect on the bone. In addition, if a new parameter name that already exists is created when using this interface, the original parameter will be overwritten. 
- When the animations have the same level, the priority of the animation playback is determined by the following two factors: 1. Whether it needs to be mixed with other animations. 2. Whether it is played first. For example, we first use the interface RegisterAnim1DControlParam to register the 1D linear blend parameter alpha for animation A and animation B, and then use the interface RegisterAnim1DControlParam to register the linear blend parameter beta for animation A and animation C. Then, play animation A, animation C, animation B, and animation D in sequence. At this time, since animation A and animation C need to be mixed and are played first, the skeleton model will first play the mixed animation of animation A and animation C (note that since the initial value of the 1D linear mixing parameter is 0, the performance of the mixed animation is still animation A at this time). If animation C is paused at this time, the mixed animation of animation A and animation B will be played. Then pause animation B, animation A will be played, and finally pause animation A again, and animation D will be played. 
- Another situation that needs attention: If we first use the interface RegisterAnim1DControlParam to register the 1D linear mixing parameter alpha for animation A and animation B, and then use the interface RegisterAnim1DControlParam to register the linear mixing parameter beta for animation A and animation C. Then, play animation A, animation B, and animation C in sequence. At this time, we call the SetAnim1DControlParam interface to set the value of parameter beta to 0.5. At this time, the model is still playing animation A. This is because animation A and animation B have a mixing requirement and are played first, that is, the parameters for mixing the two animations are gathered first. Therefore, at this time, the model is actually mixing animation A and animation B. However, since the alpha value is 0, the model still behaves as animation A. If the SetAnim1DControlParam interface is used to set the parameter alpha value to 0.5, the mixed animation of animation A and animation B can be seen. 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
# Create a new 1D control parameter for linear blending of the attack and walk animations. The parameter name is "arm_control_param". 
comp.RegisterAnim1DControlParam(modelId, "attack", "walk", "arm_control_param") 
# Play the two animations in succession, set isBlend to True, and enable animation blending. 
comp.ModelPlayAni(modelId, "attack", True, True) 
comp.ModelPlayAni(modelId, "walk",True, True) 
# Change the value of the 1D control parameter, and the two animations will be linearly blended according to the value. It can be adjusted dynamically according to the actual situation. 
comp.SetAnim1DControlParam(modelId, "arm_control_param", 0.5) 
``` 

## RemoveFreeModel 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Remove free model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| modelId | int | ModelId to be removed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the removal is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateModel(entityId)
comp.RemoveFreeModel(modelId)
```



## ResetModel

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Restore the entity to the original model 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.ResetModel() 
``` 

## SetAnim1DControlParam 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

After creating a 1D control parameter for an animation, use this interface to control the corresponding parameter. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | Model id to be set, including entity model and free model. | 
| paramName | str | Custom 1D parameter name created using the interface RegisterAnim1DControlParam. The initial value of this parameter after creation is 0. | 
| value | float | Parameter value, in the range [0,1]. When the value of the 1D parameter is 0, only the animation specified by the leftAniName parameter in the interface RegisterAnim1DControlParam will be played; when the value of the 1D parameter is 1, only the animation specified by the rightAniName parameter in the interface RegisterAnim1DControlParam will be played. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the setting is successful | 

- Notes 
- Note that if a bone mask is used for a bone, this 1D linear blend will not take effect on the bone. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
# Create a new 1D control parameter for linear blending of the attack and walk animations. The parameter name is "arm_control_param". 
comp.RegisterAnim1DControlParam(modelId, "attack", "walk", "arm_control_param") 
# Play these two animations in succession, set isBlend to True, and enable animation blending. 
comp.ModelPlayAni(modelId, "attack", True, True) 
comp.ModelPlayAni(modelId, "walk",True, True) 
# Change the value of the 1D control parameter. The two animations will be linearly mixed according to the value. It can be adjusted dynamically according to the actual situation. 
comp.SetAnim1DControlParam(modelId, "arm_control_param", 0.5) 
``` 

## SetAnimLayer 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set the level of the skeleton animation. The larger the animation level, the higher the priority. The skeleton of the skeleton model will play the animation with the highest priority first. The animations of the same level will play the animation that is played first. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | Model id to be set, including entity model and free model | 
| aniName | str | Animation name | 
| layer | int | Animation layer, positive integer, range 0~255 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Note that setting the same layer will not change the current priority playback sequence. For example: There are currently animation A and animation B, animation A's layer is 1, animation B's layer is 0, and the animation played by the skeleton model is animation A. If the level of animation A is set to 0, that is, the levels of animation A and animation B are the same, animation A will still be played, because the current priority playback sequence will not be changed when the levels are the same. In order for the skeleton model to play animation B, the level of animation B needs to be higher than that of animation A. 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetAnimLayer(modelId, "attack", 1) 
``` 

## SetAnimSpeed 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set the playback speed of a skeleton animation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| aniName | str | Skeleton animation name | 
| speed | float | Speed multiplier | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
# run action triple speed 
comp.SetAnimSpeed("run", 3.0) 
``` 

## SetAnimationAllBoneMask 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 


Set whether to block the animation of all bones in the animation. If the bone blocking is turned on, the bone will no longer play the action in the animation. This interface will take effect on all bones in the animation. The parameter ignoreBoneList can be used to specify the name of the bones that are not affected. By blocking the animation of the specified bones, different action animations can be played on different bones of the same bone model at the same time, thereby achieving quick action fusion. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | Model id to be set, including entity model and free model | 
| aniName | str | Animation name | 
| ignoreBonesList | list(str) | List of ignored bone names. Bones in this list will not be affected. When an empty list is entered, this setting is performed on all bones. | 
| enable | bool | Whether to enable the animation of the bone. True means not blocking and starting the animation of the bone. False means blocking, and the animation of the bone is not started. | 
| applyToChild | bool | True means that the child bones of the bones in ignoreBoneList are also effective, False means that it is only effective for the bones in ignoreBoneList, and the default is True. If ignoreBoneList is an empty list, applyToChild has no effect. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- When using this interface to block the animation of the upper and lower body, if there is a root bone in the skeleton, and the child bones of the root bone include the bones of the upper and lower body, the root bone will often control the movement of the entire skeleton model. Pay attention to the influence of the root bone on other bones. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
# Shield the animation of all bones in the attack animation. "l_arm" and "r_arm" are not affected, and their child bones are not affected. 
comp.SetAnimationAllBoneMask(modelId, "attack", ["l_arm", "r_arm"], False, True) 
``` 

## SetAnimationBoneMask 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set whether to shield the animation of the specified bone in the animation. If the bone shield is turned on, the bone will no longer play the action in the animation. By shielding the animation of the specified bone, the same bone model can play different action animations on different bones at the same time, thereby achieving quick action fusion. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | Model id to be set, including entity model and free model | 
| aniName | str | Animation name | 
| boneNamesList | list(str) | Bone name list | 
| enable | bool | Whether to enable the animation of the bone. True means not shielding and starting the animation of the bone. False means shielding and not starting the animation of the bone. |

| applyToChild | bool | True means it applies to the bone and its child bones, False means it applies to only the bone, the default is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- When using this interface to block the animation of the upper and lower body, if there is a root bone in the bone, and the child bones of the root bone include the bones of the upper and lower body, the root bone will often control the movement of the entire bone model. Pay attention to the influence of the root bone on other bones. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
# Mask the animation of bones named "l_arm" and "r_arm" in the attack animation, and also apply to their child bones 
comp.SetAnimationBoneMask(modelId, "attack", ["l_arm", "r_arm"], False, True) 
``` 

## SetBrightness 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.brightnessCompClient.BrightnessCompClient 

- Description 

Set the brightness of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| brightness | float | 0: pure black<br>1: normal brightness<br>1-14: brighter or even pure white<br>More than 14: usually pure white, no obvious change even if the value changes | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: Setting successful False: Setting failed | 

- Notes 
- Currently only supports modifying the brightness of entities that have replaced the skeleton model, and entities using the game's native model are not supported. 

- Example 

```python

import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBrightness(entityId) 
success = comp.SetBrightness(0.5) 
``` 

## SetEntityOpacity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set the transparency of the skeleton model. It can only be applied to the skeleton model. If the original model is set, the shadow of the model will be hidden. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| opacity | float | Transparency value, the range is [0, 1], the smaller the value, the more transparent | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetEntityOpacity(0.2) 
``` 

## SetEntityScale 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.scaleCompServer.ScaleComponentServer 

- Description 

Set the scaling ratio of the entity. Setting the ratio too large will cause game lag. It is recommended to control it within 20 times. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| entityId | str | Entity to set | 
| scale | float | Scale factor | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Return 1 if successful, -1 if failed | 

- Notes 
- This interface supports setting the size of the entity after replacing the skeleton model, as well as the original model affected by the minecraft:scale component (such as minecarts and tridents are invalid) 
- After using this interface to set the size, it is no longer controlled by the minecraft:scale component 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateScale(entityId) 
result = comp.SetEntityScale(entityId, scale) 
``` 

## SetEntityShadowShow 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set entity to open/close shadow rendering 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| flag | bool | True turns on shadow rendering, False turns off shadow rendering | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetEntityShadowShow(False)

``` 

## SetExtraUniformValue 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set the value of a specific uniform in the shader 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | ModelId to set | 
| uniformIndex | int | Uniform index to set, currently supports 4, ranging from 1 to 4. Corresponding to EXTRA_VECTOR1,EXTRA_VECTOR2,EXTRA_VECTOR3,EXTRA_VECTOR4 in Shader | 
| vec4data | tuple(float,float,float,float) | The value of vec4 to be set. The initial value is (0.0, 0.0, 0.0, 0.0) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- If the shader file is modified during the game, you need to call clientApi.ReloadAllShaders() or restart the game to take effect 

- Example 

```python 
# python code: 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
modelId = comp.GetModelId() 
#You can pass rgba to the shader to represent red 
comp.SetExtraUniformValue(modelId, 1, (1.0, 0.0, 0.0, 1.0)) 

// Shader code (in two steps): 
// Step 1, include header file 
#include "uniformExtraVectorConstants.h" 

// Step 2, use the set value directly in the shader 
void main() 
{ 
vec4 pythonColor = EXTRA_VECTOR1; 
...(Irrelevant code omitted here)

} 
``` 

## SetFreeModelAniSpeed 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set the playback speed of the free model animation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| modelId | int | modelId to be set | 
| aniName | str | animation name to be set | 
| speed | float | playback speed, the upper limit of the speed is the number of animation frames, positive and negative numbers have the same effect | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is the setting successful? | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(clientApi.GetLevelId()) 
# Create a free model at the player's feet 
playerId = clientApi.GetLocalPlayerId() 
posComp = clientApi.GetEngineCompFactory().CreatePos(playerId) 
playerPos = posComp.GetPos() 
modelId = comp.CreateFreeModel("alloy_barrier_1_1_set") 
comp.SetFreeModelPos(modelId, playerPos[0], playerPos[1]-3, playerPos[2]) 
# The animation corresponding to the model needs to be played to set the animation speed 
comp.ModelPlayAni(modelId, "recover", True)
comp.SetFreeModelAniSpeed(modelId, "recover", 10)
```



## SetFreeModelBoundingBox

<span style="display:inline;color:#7575f9">Client</span>


method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set the bounding box of the free model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | ModelId to be set | 
| min | tuple(float,float,float) | Minimum point of the bounding box | 
| max | tuple(float,float,float) | Maximum point of the bounding box | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns True if successful, False if failed | 

- Notes 
- The element of min must be smaller than the corresponding element of max. 
- Model bounding box is used to determine rendering culling: To determine whether a model should be rendered, it depends on whether it is within the field of view, that is, whether the frustum of the game camera (the range captured by the camera) and the bounding box intersect. If yes, it means it is within the field of view, otherwise it is not. Then the model can be culled and not rendered. 
For example, if the size of the created free model is 3x3x3 blocks on the display, then the bounding box size needs to be set to 3x3x3. Otherwise, if the bounding box is relatively small, such as using the default 1x1x1 bounding box, then when the model is at the edge of the screen, the model will not be rendered. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(levelId) 
comp.SetFreeModelBoundingBox(modelId, (-1, -0.9, -0.8), (1, 1, 1)) 
``` 

## SetFreeModelPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set the position of the free model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| modelId | int | modelId to be set | 
| x | float | X-axis position parameter to be set | 
| y | float | Y-axis position parameter to be set | 
| z | float | Z-axis position parameter to be set | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetFreeModelPos(modelId, 0, 0, 0) 
``` 

## SetFreeModelRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set the direction of the free model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | ModelId to be set | 
| x | float | Rotation parameter along the X direction | 
| y | float | Rotation parameter along the Y direction | 
| z | float | Rotation parameter along the Z direction | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi

comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetFreeModelRot(modelId, 0, 0, 0) 
``` 
## SetFreeModelScale 
<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set the size of the free model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | modelId to set | 
| x | float | Scale factor along the X direction | 
| y | float | Scale factor along the Y direction | 
| z | float | Scale factor along the Z direction | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether it is set successfully | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetFreeModelScale(modelId, 1, 1, 1) 
``` 

## SetLegacyBindRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Used to fix the direction of the special effect when it is attached to the skeleton


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| enable | bool | When set to False, the special effect can be consistent with the direction of the skeleton | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Call before attaching special effects 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetLegacyBindRot(False) 
``` 

## SetModel 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.modelCompServer.ModelComponentServer 

- Description 

Set the skeleton model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| modelName | str | Model name, reset the model when the value is "" | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result |


- Example 

```python 
#Set name 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetModel("xuenv") 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Replace the skeleton model of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| modelName | str | Name of the skeleton model | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | The id of the replaced skeleton model instance. Return -1 if failed | 

- Notes 
- To restore the original model, please use the ResetModel interface 
- Using the client component to replace the model will not be synchronized or saved, it is only a pure client performance. If synchronization and saving are required, please use the server's model component 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetModel("xuenv") 
``` 

## SetModelOffset 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span>


### Server Interface 

<span id="s0"></span> 
method in mod.server.component.modelCompServer.ModelComponentServer 

- Description 

Set the offset of the skeleton model relative to the local coordinate system, the initial value is (0, 0, 0) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| offset | tuple(float,float,float) | offset | 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetModelOffset((0, 3, 0)) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Add offset to the model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| offset | tuple(float,float,float) | offset vector | 

- Return value 

None 

- Example


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetModelOffset((0, 1, 0)) 
``` 

## SetModelPerspectiveEffect 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set the model perspective effect. Note: Only works for custom skeleton models 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isPerspective | bool | Whether to display perspective color | 
| color | tuple(float,float,float,float) | RGBA value of perspective color, range 0-1 | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetModelPerspectiveEffect(True, (1, 0.9, 0, 0.2)) 
``` 

## SetModelTexture 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.modelCompServer.ModelComponentServer 

- Description 

Set the bone model texture. This interface has the same function as SetTexture, but it belongs to the server interface. 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| texture | str | Texture path, relative to the current path of textures\models | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetModelTexture("Osteve") 
``` 

## SetShowArmModel 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set whether to display the hand model when switching to first person view after using the skeletal model. You need to define arm_model for the skeleton model first. The definition of arm_model can refer to the definition of the Daitengu model in resourcePack/models/netease_models.json in the demo example-AwesomeMod 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | Model id | 
| show | bool | Whether to display | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId)

modelId = comp.SetModel("datiangou") 
# Hide the hand model 
comp.SetShowArmModel(modelId, False) 
``` 
## SetTexture 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.modelCompClient.ModelComponentClient 
- Description 
Set the texture of the skeleton model. This interface has the same function as SetModelTexture, but it belongs to the client interface. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| texture | str | Texture path, relative to the current path of textures\models | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.SetTexture("Osteve") 
``` 

## ShowCommonHurtColor 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.modelCompServer.ModelComponentServer 

- Description 


Set whether the entity attached to the skeleton model displays the common red hurt effect 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| show | bool | Whether to display | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The engine turns on this option by default. If you need to change the hurt effect, you can turn it off and then customize it 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateModel(entityId) 
comp.ShowCommonHurtColor(True) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Set whether the entity attached to the skeleton model displays the general red injury effect 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| show | bool | Whether to display | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The engine turns on this option by default. If you need to change the injury effect, you can turn it off and then customize it.


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.ShowCommonHurtColor(False) 
``` 

## ShowModel 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Show pure model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | modelId to be displayed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None | No return value | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.ShowModel(modelId) 
``` 

## UnBindModelToEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description


Cancel a bone model attached to an entity. After unhooking, the model of this modelId will be destroyed and can no longer be used. If it is temporarily hidden, you can use HideModel 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | The id of the skeleton model to be unhooked | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the unhooking is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(entityId) 
comp.UnBindModelToEntity(gunModelId) 
``` 

## UnBindModelToModel 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modelCompClient.ModelComponentClient 

- Description 

Unbind a bone model from a bone model. After cancelling the attachment, the model with this modelId will be destroyed and cannot be used anymore. If you want to hide it temporarily, you can use HideModel 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | The id of the skeleton model to be canceled | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Successful or not | 

- Example 

```python

import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModel(11) 
# subModelId has been bound to the skeleton model with modelId 11 
comp.UnBindModelToModel(subModelId) 
``` 

