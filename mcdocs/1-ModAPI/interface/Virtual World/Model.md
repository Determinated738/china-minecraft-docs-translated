--- 
sidebarDepth: 1 
--- 
# Model 

## ModelCancelAllBoneMask 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Cancel all bone masks in the animation. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| objId | int | Model object id | 
| animationName | str | Model animation | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.ModelCancelAllBoneMask(objId, "attack") 
``` 

## ModelCreateMinecraftObject 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Creates a Microsoft vanilla model in a virtual world 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| identifier | str | Model identifier | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Returns the id of the model object, returns -1 if failed | 

- Notes 
- After creating the model, you need to use ModelUpdateAnimationMolangVariable to assign values to all variables in the model's json action file, otherwise there will be a large number of non-empty judgments at runtime, which will cause performance degradation 
- When the model is created, the initial default direction is +z, and the position is 10 units in front of the camera. It is recommended to modify the coordinates later 
- If the original model needs to change the playback action, it can only be controlled by modifying the molang variable through the ModelUpdateAnimationMolangVariable interface, which is not compatible with other action interfaces in the component 
- Unsupported Microsoft original models: horse, donkey, mule, skeleton_horse, zombie_horse, llama, tropicalfish, slime, magma_cube, ghast, shulker, ender_dragon, thrown_trident, ender_crystal, boat, tnt 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.ModelCreateMinecraftObject("minecraft:sheep") 
virtualWorldComp.ModelUpdateAnimationMolangVariable(id, {"variable.state": 2, "variable.liedownamount": 0}) 
``` 

## ModelCreateObject 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Create a NetEase skeleton model in a virtual world 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelName | str | Model resources | 
| animationName | str | Animation of the model | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Returns the id of the model object, returns -1 if failed | 


- Notes 
- When the model is created, the initial default orientation is +z direction, and the position is 10 units in front of the camera. It is recommended to modify the coordinates later. 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.ModelCreateObject("datiangou", "run") 
``` 

## ModelGetPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Get the coordinates of the model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | id of the model object | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Coordinates of the model (x, y, z). If the model does not exist, None is returned | 

- Notes 
- If the object is bound to other objects, the return value is meaningless. The parameters at the time of binding shall prevail 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
objId = virtualWorldComp.ModelCreateObject("datiangou", "run")
virtualWorldComp.ModelSetPos(objId, (0.0, 0.0, -10.0))
pos = virtualWorldComp.ModelGetPos(objId)
```

## ModelGetRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Returns the rotation angle of the model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| objId | int | Model object id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Rotation angle (x, y, z), returns None if the model does not exist | 

- Notes 
- If the object is bound to other objects, the return value is meaningless and the binding parameters are used. 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
objId = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelSetRot(objId, (0.0, 90.0, 0.0)) 
rot = virtualWorldComp.ModelGetRot(objId) 
``` 

## ModelIsVisible 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Returns model visibility 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| objId | int | id of the model object | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Visible | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
id = virtualWorldComp.ModelCreateObject("datiangou", "run") 
print(virtualWorldComp.ModelIsVisible(id)) 
``` 

## ModelMoveTo 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set the model translation movement 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | Model object id | 
| pos | tuple(float,float,float) | Coordinate value (x, y, z) | 
| time | float | Unit seconds, movement duration (floating point number greater than 0) | 
| ease | TimeEaseType | Time change function, the default value is clientApi.GetMinecraftEnum().TimeEaseType.linear, the parameter is not in the enumeration value and is also treated as linear | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId())

objId = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelSetPos(objId, (0.0, 0.0, 0.0)) 
virtualWorldComp.ModelMoveTo(objId, (0.0, 0.0, -10.0), 3.0, clientApi.GetMinecraftEnum().TimeEaseType.linear) 
``` 

## ModelPlayAnimation 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Model plays animation, supports action fusion, and its function is the same as the model interface ModelPlayAni. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | Model object id | 
| animationName | str | Model animation | 
| loop | bool | Whether to loop playback | 
| isBlended | bool | Whether to blend with the current animation or terminate the current animation playback. The default is False, which means terminating the current animation playback. When set to True, the animation to be played will be allowed to blend (note that no blending effect will occur if no bone shielding or linear blending parameters are set). In addition, animation blending is only performed between animations of the same level. If the currently playing animation is different from the animation to be played, the isBlended parameter is invalid. | 
| layer | int | Set the level of the skeletal animation, ranging from 0 to 255, and the default is 0. Note that if the animation to be played already exists, the original animation level will be overwritten. The larger the animation level, the higher the priority. The bones of the skeleton model will play the animation with the highest priority first. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
objId = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelPlayAnimation(objId, "fengxi", True) 
``` 

## ModelRegisterAnim1DControlParam 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient

- Description 

When playing multiple skeletal animations at the same time, create a new parameter to control the 1D linear blending of animations. Currently, linear blending only supports blending of two animations. The value range of the new parameter is [0,1]. The specified bone will linearly blend the two animations according to the value of this parameter. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | The id of the model object | 
| leftAniName | str | The name of the first animation to be blended. When the value of the 1D parameter is 0, the specified bone only plays this animation. | 
| rightAniName | str | The name of the second animation to be blended. When the value of the 1D parameter is 1, the specified bone only plays this animation. | 
| paramName | str | The name of the custom 1D parameter. The initial value of this parameter after creation is 0. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Note that if a bone mask is used for a bone, this 1D linear blend will not take effect on the bone. In addition, if a new parameter name that already exists is created when using this interface, the original parameter will be overwritten. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
# Create a new 1D control parameter for linear blending of the attack and walk animations. The parameter name is "arm_control_param". 
virtualWorldComp.ModelRegisterAnim1DControlParam(objId, "attack", "walk", "arm_control_param") 
# Play the two animations in succession, set isBlend to True, and enable animation blending. 
virtualWorldComp.ModelPlayAnimation(objId, "attack", True, True) 
virtualWorldComp.ModelPlayAnimation(objId, "walk",True, True) 
# Change the value of the 1D control parameter, and the two animations will be linearly blended according to this value. It can be adjusted dynamically according to the actual situation. 
virtualWorldComp.ModelSetAnim1DControlParam(objId, "arm_control_param", 0.5) 
``` 

## ModelRemove 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Destroy the model in the virtual world 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | Model object id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the destruction is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
objId = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelRemove(objId) 
``` 

## ModelRotate 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

How many degrees the model rotates around a certain axis 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | Model object id | 
| degreeAngle | float | Rotation angle. To avoid floating point errors due to large values, it is recommended to control the angle range between -360 and 360 degrees | 
| axis | tuple(float,float,float) | Rotation axis (x, y, z) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId())

objId = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelRotate(objId, 90.0, (0.0, 1.0, 0.0)) 
``` 

## ModelRotateTo 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set the model rotation movement 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | Model object id | 
| rot | tuple(float,float,float) | Rotation value (x, y, z) | 
| time | float | Unit: seconds, duration of movement (floating point number greater than 0) | 
| ease | TimeEaseType | Time change function, default value is clientApi.GetMinecraftEnum().TimeEaseType.linear, parameter is also considered linear if it is not in the enumeration value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
objId = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelSetRot(objId, (0.0, 0.0, 0.0))
virtualWorldComp.ModelRotateTo(objId, (0.0, 90.0, 0.0), 3.0, clientApi.GetMinecraftEnum().TimeEaseType.linear)
```



## ModelSetAnim1DControlParam

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient

- describe


After creating a 1D control parameter for the animation, use this interface to control the corresponding parameter. 

- Parameter 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | The id of the model object | 
| paramName | str | The name of the custom 1D parameter created using the RegisterAnim1DControlParam interface. The initial value of this parameter after creation is 0. | 
| value | float | The value of the parameter, in the range [0,1]. When the value of the 1D parameter is 0, only the animation specified by the leftAniName parameter in the interface RegisterAnim1DControlParam is played. When the value of the 1D parameter is 1, only the animation specified by the rightAniName parameter in the interface RegisterAnim1DControlParam is played. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Note that if a bone mask is used for a bone, this 1D linear blend will not take effect on the bone. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
# Create a new 1D control parameter for linear blending of the attack and walk animations. The parameter name is "arm_control_param".
virtualWorldComp.ModelRegisterAnim1DControlParam(objId, "attack", "walk", "arm_control_param") 
# Play the two animations in succession, set isBlend to True, and enable animation blending. 
virtualWorldComp.ModelPlayAnimation(objId, "attack", True, True) 
virtualWorldComp.ModelPlayAnimation(objId, "walk",True, True) 
# Change the value of the 1D control parameter, and the two animations will be linearly blended according to this value. It can be adjusted dynamically according to the actual situation. 
virtualWorldComp.ModelSetAnim1DControlParam(objId, "arm_control_param", 0.5) 
``` 

## ModelSetAnimAllBoneMask 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set whether to block the animation of all bones in the animation. If the bone shielding is turned on, the bone will no longer play the action in the animation. This interface will take effect on all bones in the animation. The parameter ignoreBoneList can be used to specify the name of the bones that are not affected. By shielding the animation of the specified bones, the same bone model can play different action animations on different bones at the same time, thereby achieving quick action fusion. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| objId | int | id of the model object | 
| animationName | str | animation of the model | 
| ignoreBonesList | list(str) | List of ignored bone names. Bones in this list will not be affected. If an empty list is entered, this setting will be performed on all bones. | 
| enable | bool | Whether to enable the animation of this bone. True means not to block and start the animation of this bone. False means to block and not start the animation of this bone. | 
| applyToChild | bool | True means that the child bones of the bones in ignoreBoneList are also effective. False means that it is only effective for the bones in ignoreBoneList. The default is True. If ignoreBoneList is an empty list, applyToChild has no effect. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- When using this interface to block the animation of the upper and lower body, if there is a root bone in the skeleton, and the child bones of the root bone include the bones of the upper and lower body, the root bone will often control the movement of the entire skeleton model. Pay attention to the influence of the root bone on other bones. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
# Mask the animation of all bones in the attack animation. "l_arm" and "r_arm" are not affected, and their child bones are not affected either 
virtualWorldComp.ModelSetAnimAllBoneMask(objId, "attack", ["l_arm", "r_arm"], False, True) 
``` 

## ModelSetAnimBoneMask 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set whether to block the animation of the specified bone in the animation. If the bone blocking is turned on, the bone will no longer play the action in the animation. By blocking the animation of the specified bone, different action animations can be played on different bones of the same bone model at the same time, thereby achieving quick action fusion. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | Model object id | 
| animationName | str | Model animation | 
| boneNamesList | list(str) | Bone name list | 
| enable | bool | Whether to enable the animation of the bone. True means not blocking and starting the animation of the bone. False means blocking and not starting the animation of the bone. | 
| applyToChild | bool | True means it is effective for this bone and its child bones, False means it is effective only for this bone, the default value is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the setting is successful | 

- Notes 
- When using this interface to block the animation of the upper and lower body, if there is a root bone in the skeleton, and the child bones of the root bone include the bones of the upper and lower body, the root bone will often control the movement of the entire skeleton model. Pay attention to the influence of the root bone on other bones. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
# Mask the animation of bones named "l_arm" and "r_arm" in the attack animation, and also apply to their child bones 
virtualWorldComp.ModelSetAnimBoneMask(objId, "attack", ["l_arm", "r_arm"], False, True) 
``` 

## ModelSetAnimLayer 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set the level of skeletal animation. The higher the animation level, the higher the priority. The skeleton of the skeletal model will play the animation with the highest priority first. The animations of the same level will play the animations that are played first. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| objId | int | Model object id | 
| animationName | str | Model animation | 
| layer | int | Animation level, a positive integer ranging from 0 to 255 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Note that setting the same level will not change the current priority playback sequence. For example: There are currently animations A and B, the level of animation A is 1, and the level of animation B is 0. At this time, the animation played by the skeleton model is animation A. If the level of animation A is set to 0, that is, the levels of animation A and animation B are the same, animation A will still be played, because the current priority playback sequence will not be changed when the levels are the same. In order for the skeleton model to play animation B, the level of animation B must be higher than that of animation A. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.ModelSetAnimLayer(objId, "attack", 1) 
```




## ModelSetBoxCollider 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set the bounding box of the model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | ID of the model object | 
| lengths | tuple(float,float,float) | Length of the model bounding box in each direction, (x,y,z) | 
| offset | tuple(float,float,float) | Offset of the center of the model bounding box, (x,y,z), default is (0.0,0.0,0.0) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
objId = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelSetBoxCollider(objId, (2.0, 2.0, 2.0), (0.0, 0.0, 0.0)) 
``` 

## ModelSetPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Sets model coordinates 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | Model object id | 
| pos | tuple(float,float,float) | Coordinates(x, y, z) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- If the object is bound to other objects, the modification will be invalid and the actual position will be based on the parameters at the time of binding 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
objId = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelSetPos(objId, (0.0, 0.0, -10.0)) 
``` 

## ModelSetRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set the rotation angle of the model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | Model object id | 
| rot | tuple(float,float,float) | The initial default value of the rotation angle (x, y, z) is (0, 0, 0), pointing to the negative direction of the z axis. In order to avoid floating point errors caused by large values, it is recommended that the angle control range of each dimension be between -360 degrees and 360 degrees | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- If the object is bound to other objects, the modification will be invalid, and the actual rotation angle is based on the parameters at the time of binding.


- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
objId = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelSetRot(objId, (0.0, 90.0, 0.0)) 
``` 

## ModelSetScale 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set the scale value of the model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | id of the model object | 
| scales | tuple(float,float,float) | scaling value (x, y, z) | 

- return value 

| <div style="width: 4em">data type</div> | description | 
| :--- | :--- | 
| bool | whether the setting is successful | 

- example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
objId = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelSetScale(objId, (2.0, 2.0, 2.0)) 
``` 

## ModelSetVisible 

<span style="display:inline;color:#7575f9">Client</span> 


method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Set model visibility 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| objId | int | Model object id | 
| isVisible | bool | Visible | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
id = virtualWorldComp.ModelCreateObject("datiangou", "run") 
virtualWorldComp.ModelSetVisible(id, False) 
``` 

## ModelStopActions 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Stop the movement and rotation of the model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| objId | int | Model object id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

    | bool | Whether the stop was successful |

- Example

```python
import client.extraClientApi as clientApi
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId())
objId = virtualWorldComp.ModelCreateObject("datiangou", "run")
virtualWorldComp.ModelSetPos(objId, (0.0, 0.0, 0.0))
virtualWorldComp.ModelSetRot(objId, (0.0, 0.0, 0.0))
virtualWorldComp.ModelMoveTo(objId, (0.0, 0.0, -10.0), 3.0, clientApi.GetMinecraftEnum().TimeEaseType.linear)
virtualWorldComp.ModelRotateTo(objId, (0.0, 90.0, 0.0), 3.0, clientApi.GetMinecraftEnum().TimeEaseType.linear) 
virtualWorldComp.ModelStopActions(objId) 
``` 

## ModelStopAnimation 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Stops playing the specified model animation. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| objId | int | Model object id | 
| animationName | str | Model animation | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the pause is successful | 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
virtualWorldComp.ModelStopAnimation(objId, "fengxi") 
``` 



## ModelUpdateAnimationMolangVariable 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.virtualWorldCompClient.VirtualWorldCompClient 

- Description 

Updates the Microsoft original model expression variable to control the change of the action 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| objId | int | Model object id | 
| molangDict | dict | Data in the form of key-value pairs | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- If this interface is called immediately after creating the model in the same frame, the scripts/initialize field in the client entity configuration will no longer be executed. 

- Example 

```python 
import client.extraClientApi as clientApi 
virtualWorldComp = clientApi.GetEngineCompFactory().CreateVirtualWorld(clientApi.GetLevelId()) 
id = virtualWorldComp.ModelCreateMinecraftObject("minecraft:cat") 
virtualWorldComp.ModelUpdateAnimationMolangVariable(id, {"variable.state": 2, "variable.liedownamount": 0}) 
``` 

