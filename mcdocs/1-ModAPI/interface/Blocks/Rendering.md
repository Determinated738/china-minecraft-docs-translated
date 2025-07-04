--- 
sidebarDepth: 1 
--- 
# Rendering 

## ChangeBlockTextures 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Replace block texture 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, format [namespace:name:auxvalue], auxvalue defaults to 0; only supports ordinary square blocks without special rendering logic, otherwise it may display abnormally | 
| tileName | str | The name of the original texture in the atlas, corresponding to the configuration in terrain_texture.json | 
| texturePath | str | The path of the texture to be replaced | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful (because of delayed loading, the return success here does not mean that the texture path is correct. The wrong path will cause the texture to be lost and display abnormally during rendering) | 

- Notes 
- Invalid for blocks with dynamically changing textures 
- After calling this interface, tileName will not change. If you want to restore the setting later, you still need to use this tileName 
- The resolution height of the texture needs to be an integer multiple of the width 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
#Set the texture of the upward surface to work_block_other 
print(comp.ChangeBlockTextures("myblock:work_block:0", "myblock:work_block_faceup", "textures/blocks/work_block_other")) 
#Restore the texture of the upward surface 
#print(comp.ChangeBlockTextures("myblock:work_block:0", "myblock:work_block_faceup", "textures/blocks/work_block_faceup")) 
``` 

## GetBlockTextures 

<span style="display:inline;color:#7575f9">Client</span>


method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Get the initial texture information of the block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, format [namespace:name] | 
| face | int | The face of the block to be obtained, refer to [Facing enumeration](../../enumeration value/Facing.md), the default value of face is 6, and the texture information of all faces of the block is obtained | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | The texture information of the block is textureInfoDict. If an error occurs (such as special blocks: doors, beds, etc.), None is returned | 

- Notes 
- name is the name of the texture in the atlas. The texture name used by the block can be found in blocks.json 
- Each texture name may have multiple paths in terrain_texture.json, so this interface will also return the same number of paths. 
- This interface is only used for verification. The texture information obtained is the initial information after the game is loaded. After ChangeBlockTextures is modified, the interface still returns the initial information. 

- Example

```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId)
textureInfoDict = comp.GetBlockTextures("customblocks:customblocks_test_ore")
# textureInfoDict information is as follows
# {
# 'North': {'paths': ['textures/blocks/customblocks_ore'], 'name': 'customblocks:customblocks_test_ore'},
# 'West': {'paths': ['textures/blocks/customblocks_ore'],'name': 'customblocks:customblocks_test_ore'},
# 'Up': {'paths': ['textures/blocks/customblocks_ore'], 'name': 'customblocks:customblocks_test_ore'},
# 'Down': {'paths': ['textures/blocks/customblocks_ore'], 'name': 'customblocks:customblocks_test_ore'},
# 'East': {'paths': ['textures/blocks/customblocks_ore'], 'name': 'customblocks:customblocks_test_ore'},
# 'South': {'paths': ['textures/blocks/customblocks_ore'], 'name': 'customblocks:customblocks_test_ore'}
# }
```



## SetBlockEntityFramePosOffset

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient

- Description 

Sets the offset value of the sequence frame effect position in the custom block entity, which is used to adjust the offset of the sequence frame effect relative to the block position. Unlike the effect/sequence frame/SetPos interface, this interface adjusts the position offset value relative to the block position, not the world coordinates. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| frameKeyName | str | The custom key value name of the sequence frame effect. | 
| effectPosOffset | tuple(int,int,int) | The offset values of the sequence frame effect in the x, y, and z directions relative to the block position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Adjust the position of the sequence frame effect, offset 1 in the +x axis direction, 2 in the +y axis direction, and 1 in the +z axis direction on the block position 
comp.SetBlockEntityFramePosOffset(pos, "my_frame1", (1,2,1)) 
``` 

## SetBlockEntityModelPosOffset 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Set the entity model position offset value of the custom block entity, which is used to adjust the offset of the entity model relative to the block position. This interface can be used to adjust the position of the entity model of the custom block entity. Only when the custom block entity defines the entity model will it take effect. The entity model is defined under resource_pack/entity/. For details, please refer to the teaching document of custom block entity animation. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| modelPosOffset | tuple(int,int,int) | Offset value of the entity model in the x, y, z directions relative to the block position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the setting is successful | 

- Notes 
- When adjusting the position of the entity model, be careful not to set the model position too far from the position of the block entity. If it is set too far, when the player moves the screen to another place and can no longer see the block entity, the entity model will stop rendering because the block entity does not exist on the player's screen. In this case, whenever the position of the block entity is not visible on the player's screen, the entity model will disappear. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Adjust the position of the model, the offset value is 1 to the +x axis, 2 to the +y axis, and 1 to the +z axis 
comp.SetBlockEntityModelPosOffset(pos, (1,2,1)) 
``` 

## SetBlockEntityModelRotation 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Set the rotation value of the entity model of the custom block entity on each axis. This interface can be used to adjust the rotation of the entity model of the custom block entity. Only when the entity model is defined by a custom block entity will it take effect. The entity model is defined under resource_pack/entity/. For details, please refer to the tutorial document of custom block entity animation. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| angles | float | Rotation angle, range is [-360,360]. | 
| rotateAxis | str | Rotation axis, rotate around this axis. This parameter only supports one of the following three values: "x", "y", "z", uppercase and lowercase. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- When adjusting the rotation angle, pay attention to the rotation order and angle setting to avoid the problem of universal lock. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Adjust the model rotation and rotate 30 degrees around the x-axis 
comp.SetBlockEntityModelRotation(pos, 30, "x")

# Adjust the model rotation, rotate 30 degrees around the y axis 
comp.SetBlockEntityModelRotation(pos, 30, "y") 
# Adjust the model rotation, rotate 30 degrees around the z axis 
comp.SetBlockEntityModelRotation(pos, 30, "z") 
``` 

## SetBlockEntityModelScale 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Set the scale value of the entity model size of the custom block entity. This interface can be used to adjust the size of the entity model of the custom block entity. Only when the entity model is defined by the custom block entity will it take effect. The entity model is defined under resource_pack/entity/. For details, please refer to the teaching document of the custom block entity animation. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| scale | tuple(int,int,int) | Scaling value of the entity model on the x, y, and z axes. Negative values are supported. When the scaling value of an axis is negative, it means that the model will be mirrored on this axis with the other two axes as the symmetry plane. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The size of the model can be adjusted in two ways: 
(1) Define scale under the scripts field in entity.json, as shown below 
"minecraft:client_entity": { 
... 
"scripts":{ 
// Overall model size scaling value. After defining "scale", scalex, scaley, and scalez will be invalid 
"scale" : "0.9375", 
// Scaling value for the three axis directions. Comment out the "scale" above, and the following three scaling values will take effect. 
"scalex": "0.9375", 
"scaley": "0.9375", 
"scalez": "0.9375", 
... 
} 
} 
(2) Use this interface SetBlockEntityModelScale to set the model scaling value. 
The above two methods, the first method is effective for all block entities using this model, and the second method is effective for the model of the specified block entity. If the first and second methods are used to adjust the model size at the same time, the model will be scaled according to the first method first, and then scaled according to the second method. 

- Example


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Adjust the model size to 2 times the original in the x-axis direction, 2 times the original in the y-axis direction, and 0.5 times the original in the z-axis direction 
comp.SetBlockEntityModelScale(pos, (2,2,0.5)) 
``` 

## SetBlockEntityParticlePosOffset 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Set the particle effect position offset value in the custom block entity, which is used to adjust the offset of the particle effect relative to the block position. Unlike the Effect/Particle/SetPos interface, this interface adjusts the position offset value relative to the block position, not the world coordinates. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| particleKeyName | str | The custom key value name of the particle effect. | 
| effectPosOffset | tuple(int,int,int) | The offset values of the particle effect in the x, y, and z directions relative to the block position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Adjust the position of the particle effect, offset 1 in the +x direction, 2 in the +y direction, and 1 in the +z direction on the block position 
comp.SetBlockEntityParticlePosOffset(pos, "my_particle1", (1,2,1)) 
``` 

