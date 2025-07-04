--- 
sidebarDepth: 1 
--- 
# Block Entity 

## CleanBlockTileEntityCustomData 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Clear the custom data stored in the TileEntity bound to the special block (chest, skull, furnace, flower pot, etc.) at the specified location. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | Position coordinates of the special block bound to TileEntity | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Clear the result. If the block at the corresponding position does not exist or there is no bound TileEntity, it will fail | 

- Notes 
- This interface uses the playerId when creating the component to locate the specific dimension, and can only obtain blocks near the player. If the block position is too far away from the player, the correct return information may not be obtained. 

- Example

```python
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId)
pos = (-1, 4, 34)
suc = comp.CleanBlockTileEntityCustomData(pos)
print "CleanBlockTileEntityCustomData pos=%s suc=%s" % (str(pos), suc)
```



## CreateFrameEffectForBlockEntity

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient

- describe


Create a sequence frame effect on a custom block entity. After creation, this interface returns the ID of the sequence frame effect. With this ID, you can use the interface in the effect/sequence frame to play, set the position, size, and other operations on the sequence frame effect. This is similar to the creation of the entity's sequence frame effect. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block location | 
| path | str | Effect resource path. No suffix is required. The path is the path of the sequence frame resource file in the resource_pack/textures folder or the resource_pack/effects folder. The path name starts with "textures/" or "effects/". When the path name starts with "textures/", the .json suffix is not required. When the path name starts with "effects/", the .json suffix is required. | 
| frameKeyName | str | The custom key value name of the sequence frame effect. After creating the sequence frame effect, you can use this key value name to obtain the id of the sequence frame effect through the GetFrameEffectIdInBlockEntity interface. | 
| effectPos | tuple(float,float,float) | The position of the effect relative to the custom block entity, that is, the coordinate position in the coordinate system with the position of the custom block entity as the origin. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int or None | Returns the ID of the sequence frame effect if the creation is successful, and returns None if the creation fails | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Take the position of the custom block entity as the origin, and use the resources under resource_pack/textures at the coordinates (1.0, 1.0, 1.0) on this origin to create a sequence frame effect 
id1 = comp.CreateFrameEffectForBlockEntity(pos, "textures/sfxs/snow", "my_frame1", (1.0, 1.0, 1.0)) 
# Take the position of the custom block entity as the origin, and use the resources under resource_pack/effects to create a sequence frame effect at the coordinate (1.0, 1.0, 1.0) on this origin 
id2 = comp.CreateFrameEffectForBlockEntity(pos, "effects/sfxs/snow.json", "my_frame2", (1.0, 1.0, 1.0)) 
``` 

## CreateParticleEffectForBlockEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Create a particle effect on the custom block entity. After creation, this interface returns the ID of the particle effect. Using this ID, you can use the interface in the effect/particle to play, set the position, size, and other operations on the particle effect. Similar to the creation of particle effects for entities. If the custom block entity already has an effect with the same key name, a new effect will not be created, and the interface returns the existing effect ID. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block location | 
| path | str | Effect resource path, which needs to be suffixed (usually json). The path is the particle effect json file path under the resource_pack/effects file, and the path name starts with "effects/". | 
| particleKeyName | str | The custom key name of the particle effect. After creating the particle effect, you can use this key name to get the particle effect ID through the GetParticleEffectIdInBlockEntity interface. | 
| effectPos | tuple(float,float,float) | The position of the special effect relative to the custom block entity, that is, the coordinate position in the coordinate system with the position of the custom block entity as the origin. | 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int or None | Returns the particle effect ID if creation succeeds, returns None if creation fails | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Create a particle effect at the coordinate (1.0, 1.0, 1.0) of the custom block entity as the origin 
id = comp.CreateParticleEffectForBlockEntity(pos, "effects/fire.json", "my_particle1", (1.0, 1.0, 1.0)) 
``` 

## GetBlockEntityData 

<span style="display:inline;color:#ff5555">Server</span> 

<span id="0"></span> 
method in mod.server.component.blockEntityExDataCompServer.BlockEntityExDataCompServer 

- Description 

Used to obtain an object that can manipulate a custom block entity data, the operation method is similar to dict 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension | 
| pos | tuple(int,int,int) | Block location | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockEntityData or None | Object that can manipulate the data in the block entity | 

- Notes 
- GetBlockEntityData returns None usually because the block where the block is located is not loaded, the game is exiting, the block is not a custom block, or the netease:block_entity component is not configured in the json of the custom block. <br>Before operating the object returned by GetBlockEntityData, please first determine whether it is empty, otherwise it will cause the error ```'NoneType' object has no attribute '__getitem__'```. 
- Supports python basic data types (int/float/string/bool/dict/list), does not support tuple and **dict's key must be a string** 
- **When storing a list, the data types of each item in the list should be the same, otherwise the storage will fail**. For example, [True, False] can be stored successfully, and [True, 1, 0.5] will fail to store 
- **Although the returned object operation is similar to dict, it does not support nested storage and only allows direct assignment such as blockEntityData['key'] = value. Operations such as blockEntityData["value5"] ["v1"] = 9 or blockEntityData["value6"].append(True) will not be able to store data successfully. ** 
- When storing integers, if the value range exceeds the maximum range that int can represent, it will not be stored successfully. It is recommended to convert such values into strings for storage. 

- Example 

```python

import mod.server.extraServerApi as serverApi 
# Settings 
blockEntitycomp = serverApi.GetEngineCompFactory().CreateBlockEntityData(levelId) 
dimension = 0 
pos = (4, 3, 2) 
# GetBlockEntityData will return None in some cases. Before operating on the returned result, be sure to determine whether it is empty 
blockEntityData = blockEntitycomp.GetBlockEntityData(dimension, pos) 
# Store data 
# Supports storing Python basic data types (int/float/string/bool/dict/list), does not support tuple, and key must be a string 
# When storing a list, the data types of each item in the list should be the same, otherwise the storage will fail 
if blockEntityData: 
blockEntityData['value1'] = 10 
blockEntityData['value2'] = 3.5 
blockEntityData['value3'] = True 
blockEntityData['value4'] = "hello" 
blockEntityData['value5'] = {"v1": 10, "v2": 3.5, "v3": [0,1,2]} 
blockEntityData['value6'] = [True, False] 
# Read data 
if blockEntityData: 
value1 = blockEntityData['value1'] 
value5 = blockEntityData['value5'] 
# Data that does not exist in the block entity will return None 
valueNone = blockEntityData['valueNone'] 
``` 

<span id="1"></span> 
method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Used to get the data of blocks (including custom blocks). The data is read-only and cannot be written. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension | 
| pos | tuple(int,int,int) | Block location | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict or None | Object of data in block entity | 

- Notes 
- **With the update of versions, the data structure contained in the block may be adjusted by the Microsoft team and will not be announced. Developers using this interface should pay attention to testing and compatibility when updating versions. Data encoding is UTF-8 
Applicable to: [Block entity](https://minecraft-zh.gamepedia.com/%E6%96%B9%E5%9D%97%E5%AE%9E%E4%BD%93)

Special case: The item information of the ender chest cannot be obtained through this interface 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
blockEntitycomp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
blockEntityData = blockEntitycomp.GetBlockEntityData(0, (4, 3, 2)) 
``` 

## GetBlockEntityMolangValue 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Get the value of the Molang variable of a custom block entity. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| variableName | str | The name of a molang variable, starting with "variable." and cannot contain more than two "."s. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | The value of the molang variable. If the variable does not exist, it returns None | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.GetBlockEntityMolangValue(pos, "query.mod.idle") 
``` 

## GetBlockTileEntityCustomData 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer


- Description 

Read the custom data stored in the TileEntity bound to the special block (box, skull, furnace, flower pot, etc.) at the specified position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | Position coordinates of the special block bound to TileEntity | 
| key | str | Custom key | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| any | The set value. If the corresponding data does not exist, None will be returned | 

- Notes 
- This interface uses the playerId when creating the component to locate the specific dimension, and can only obtain blocks near the player. If the block is too far away from the player, the correct return information may not be obtained.

- Example

```python
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId)
pos = (-1, 4, 34)
key = "owner"
val = comp.GetBlockTileEntityCustomData(pos, key)
print "GetBlockTileEntityCustomData pos=%s key=%s value=%s" % (str(pos), key, val)
```



## GetBlockTileEntityWholeCustomData

<span style="display:inline;color:#ff5555">Server</span>

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer

- describe

Read the custom data dictionary stored in the TileEntity bound to the special block (box, skull, furnace, flower pot, etc.) at the specified location. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Position coordinates of the special block bound to TileEntity | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict or None | TileEntity custom storage data dictionary. If there is no additional storage data, it returns None or an empty dictionary | 

- Notes 
- This interface uses the playerId when creating the component to locate the specific dimension, and can only obtain blocks near the player. If the block is too far away from the player, the correct return information may not be obtained. 

- Example

```python
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId)
pos = (-1, 4, 34)
data = comp.GetBlockTileEntityWholeCustomData(pos)
if not data:
    print "GetBlockTileEntityWholeCustomData pos=%s return empty" % (str(pos), )
else:
    print "GetBlockTileEntityWholeCustomData pos=%s return success" % (str(pos), )
if data:
    for key, val in data.iteritems():
        print "key=%s val=%s" % (key, str(val))
```



## GetFrameEffectIdInBlockEntity

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Get the ID of the specified sequence frame effect created in the custom block entity. There are two types of created effects: one is the effect defined by "netease_frame_effects" in the entity json file under resource_pack/entity/; the other is the effect created using the interface CreateFrameEffectForBlockEntity. The returned effect ID can be used to play, set the position, size, etc. of the sequence frame effect using the interface in the effect/sequence frame. It is similar to the way to create the entity's sequence frame effect. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| frameKeyName | str | The custom key value name of the sequence frame effect, i.e., "keyName" in netease_frame_effects: { "keyName" : {"path": "textures/sfxs/xxx.json", "pos": [1.0, 1.0, 1.0f]} }, or the frameKeyName parameter filled in when creating an effect through CreateFrameEffectForBlockEntity. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int or None | Returns the ID of the sequence frame special effect. If the key value does not exist, None is returned | 


- Example 

```python 
# Assume that the custom block entity defines the following effects 
# "minecraft:client_entity": { 
# ... 
# "netease_frame_effects":{ 
# "my_frame1" : { "path" : "textures/sfxs/snow.json", "pos": [1.0 , 1.0 , 1.0]}, 
# ... 
# } 
# } 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Get the effect ID of the preset effect named "my_frame1" 
id = comp.GetFrameEffectIdInBlockEntity(pos, "my_frame1") 
``` 

## GetParticleEffectIdInBlockEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Get the ID of the specified particle effect created in the custom block entity. There are two types of created effects: one is the effect defined by "netease_particle_effects" in the entity json file under resource_pack/entity/; the other is the effect created using the interface CreateParticleEffectForBlockEntity. The returned effect ID can be used to play, set the position, size, etc. of the particle effect using the interface in the effect/particle. It is similar to the way the particle effect is created for the entity. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| particleKeyName | str | The custom key name of the particle effect, i.e., "keyName" in netease_particle_effects: { "keyName" : {"path":"effects/xxx.json", "pos": [1.0, 1.0, 1.0f]} }, or the particleKeyName parameter filled in the interface when creating an effect through CreateParticleEffectForBlockEntity. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int or None | Returns the ID of the particle effect. If the key value does not exist, it returns None | 

- Example 

```python 
# The entity.json file that requires a custom block entity has the following definition: 
# "minecraft:client_entity": { 
# ... 
# "netease_particle_effects":{ 
# "my_particle1" : { "path" : "effects/fire.json", "pos": [1.0 , 1.0 , 1.0]},

# ... 
# } 
# } 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Get the effect ID of the preset effect named "my_particle1" 
id = comp.GetParticleEffectIdInBlockEntity(pos, "my_particle1") 
``` 

## RemoveFrameEffectInBlockEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Removes a sequence frame effect created on a custom block entity. The effect ID will be invalid after removal. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| frameKeyName | str | Custom key name for the sequence frame effect. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns True if the removal is successful, and returns False if the key value does not exist | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Remove the special effect with the key value "my_frame1" 
comp.RemoveFrameEffectInBlockEntity(pos, "my_frame1") 
``` 

## RemoveParticleEffectInBlockEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient


- Description 

Removes the particle effect created on the custom block entity. The removed effect ID will be invalid. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| particleKeyName | str | The custom key name of the particle effect. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns True if the removal is successful, and False if the key value does not exist | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Remove the special effect with the key value "my_particle1" 
comp.RemoveParticleEffectInBlockEntity(pos, "my_particle1") 
``` 

## SetBlockEntityMolangValue 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Set the Molang variable of the custom block entity, which has the same function as the entity's molang variable. Currently, it is mainly used to control the animation state transition of the custom entity. The definition method of Molang variables is the same as the definition method of Molang variables of the original entity. For details, please refer to the teaching document of custom block entity animation. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block location | 
| variableName | str | The name of the molang variable, starting with "variable." and cannot contain more than two ".". | 
| value | float | The value of the molang variable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Note that the definition and usage of the Molang variables of the custom block entity are the same as those of the original Microsoft Molang variables. Therefore, there is no need to call the Register interface and UnRegister interface in entity/molang/ to register and unregister. You only need to define and initialize it in entity.json. This is the same as the usage of the original Microsoft entity. You can refer to the entity.json file of the original Microsoft entity. 

- Example 

```python 
# The entity.json file for the custom block entity needs to have the following definition: 
# "minecraft:client_entity": { 
# ... 
# "scripts":{ 
# // Register the molang variable "variable.mod_is_moving" and initialize its value to 1.0 
# "initialize": [ "variable.mod_is_moving = 1.0;" ], 
# ... 
# } 
# } 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
# Set the value of the molang variable to transition the animation state 
comp.SetBlockEntityMolangValue(pos, "variable.mod_is_moving", 2.0) 
``` 

## SetBlockTileEntityCustomData 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Sets the custom data stored in the TileEntity bound to the special block (box, skull, furnace, flower pot, etc.) at the specified location. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Position coordinates of the special block bound to TileEntity | 
| key | str | Custom key | 
| value | any | Supports python basic data types, tuple does not support | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result, if the block at the corresponding position does not exist or there is no bound TileEntity, the setting will fail | 


- Notes 
- This interface uses the playerId when creating the component to locate the specific dimension, and can only obtain blocks near the player. If the block is too far away from the player, the correct return information may not be obtained. 

- Example

```python
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId)
pos = (-1, 4, 34)
suc = comp.SetBlockTileEntityCustomData(pos, "owner", "Jack")
print "SetBlockTileEntityCustomData pos=%s suc=%s" % (str(pos), suc)
```



## SetEnableBlockEntityAnimations

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient

- describe

Set whether to enable the animation effect of the custom block entity. When enabled, the custom entity block will animate according to the animation state machine defined by animation_controller in the entity file. When disabled, all animation playback will be stopped. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | Block location | 
| enable | bool | Whether to enable animation playback of custom block entities | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.SetEnableBlockEntityAnimations(pos, True) 
``` 

