--- 
sidebarDepth: 1 
--- 
# Block Management 

## GetBlock 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Get the block at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(float,float,float) | Block position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(str,int) | Parameter 1: the name of the block, parameter 2: the additional value of the block AuxValue | 

- Notes 
- Only loaded terrain can set and obtain block information 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.GetBlock((x,y,z)) 
``` 

## GetBlockClip 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description


Get the current <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html#netease-aabb">clip's aabb</a> of a block at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| dimensionId | int | Block's dimension, defaults to -1 when not filled | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Block clip's aabb dictionary | 

- Notes 
- Only loaded terrain can get block information, and support getting block information in the constantly loaded block of the corresponding dimension 
- Since the collision box of a block can change with the change of adjacent blocks, this interface returns the aabb of the block clip when calling 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
blockDict = comp.GetBlockClip((0, 5, 0), 0) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Get the aabb of the current clip of the block at the specified position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Block aabb dictionary |


- Notes 
- Since the collision box of a block can change with the adjacent blocks, this interface returns the aabb of the block clip when it is called 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.GetBlockClip((x,y,z)) 
``` 

## GetBlockCollision 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Get the aabb of the current collision of a block at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| dimensionId | int | Block dimension, defaults to -1 when not filled | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Block aabb dictionary | 

- Notes 
- Block information can only be obtained from loaded terrain, and block information in the corresponding dimension of the constantly loaded block can be obtained 
- Since the collision box of a block can change with the change of adjacent blocks, this interface returns the aabb of the block collision when called 

- Example

```python
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId)
blockDict = comp.GetBlockCollision((0, 5, 0), 0)

``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Get the aabb of the current collision of the block at the specified position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Block aabb dictionary | 

- Notes 
- Since the collision box of a block can change with the adjacent blocks, this interface returns the aabb of the block collision when it is called 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.GetBlockCollision((x,y,z)) 
``` 

## GetBlockNew 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Get the block at a certain position 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| dimensionId | int | Block dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Block Information Dictionary">Block Information Dictionary</a> | 

- Notes 
- Block information can only be obtained from terrain that has been loaded. It supports obtaining block information in the corresponding dimension's frequently loaded blocks 
- For blocks with multiple states, aux calculations are more complicated. It is recommended to use GetBlockStates to obtain the block state dictionary 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
blockDict = comp.GetBlockNew((0, 5, 0), 0) 
``` 

## GetDestroyTotalTime 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Get the time required to destroy a block using an item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, format [namespace:name:auxvalue], auxvalue defaults to 0 | 
| itemName | str | Item identifier, format [namespace:name:auxvalue], auxvalue defaults to 0, defaults to None (no item used) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Time required |


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.GetDestroyTotalTime("minecraft:diamond_block", "minecraft:stone_pickaxe") 
``` 

### Client Interface 

<span id="c0"></span> 
method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Get the time required to destroy a block using an item 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, format [namespace:name:auxvalue], auxvalue defaults to 0 | 
| itemName | str | Item identifier, format [namespace:name:auxvalue], auxvalue defaults to 0, defaults to None (no item used) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Time required | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.GetDestroyTotalTime("minecraft:diamond_block", "minecraft:stone_pickaxe") 
``` 

## GetLiquidBlock 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer

- describe


    Get the fluid information interface of a block at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| dimensionId | int | Block dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Block Information Dictionary">Block Information Dictionary</a> | 

- Notes 
- Block information can only be obtained from loaded terrain, and block information in the corresponding dimension of the frequently loaded block can be obtained 
- For blocks that do not contain water or are not fluids, None is returned. For a water-containing block, such as a water-containing oak fence, GetLiquidBlock will return the information of the fluid it contains (including custom fluids), and GetBlockNew will return the information of the oak fence. For general water blocks (including custom fluids), GetLiquidBlock and GetBlockNew will both return water information (including custom fluids). Therefore, GetLiquidBlock and GetBlockNew can be used to determine whether a block is liquid. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
liquidBlockDict = comp.GetLiquidBlock((0, 5, 0), 0) 
``` 

## GetTopBlockHeight 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Get the height of the highest non-air block at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int) | x-axis and z-axis position | 
| dimension | int | Dimension id, default is 0, can be used to get the highest non-air block height in the constantly loaded chunk | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int or None | Height. Returns None if the block is not loaded | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
height = comp.GetTopBlockHeight((5, 5), 0) 
``` 

### Client Interface 

<span id="c0"></span> 
method in mod.client.component.blockInfoCompClient.BlockInfoComponentClient 

- Description 

Get the height of the highest non-air block at a certain position in the current dimension 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int) | x-axis and z-axis position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int or None | Height. Returns None if the block is not loaded | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
height = comp.GetTopBlockHeight((5, 5)) 
``` 

## SetBlockNew 

<span style="display:inline;color:#ff5555">Server</span>


method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Set the block at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| blockDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Block Information Dictionary">Block Information Dictionary</a> | 
| oldBlockHandling | int | 0: Replace, 1: Destroy, 2: Keep, default is 0 | 
| dimensionId | int | Dimension where the block is located, required parameter | 
| isLegacy | bool | Whether to set to traditional aux, it is recommended to set to True, that is, the state corresponding to aux does not change with version iteration. The default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- Blocks can only be set on terrain that has been loaded, and blocks can be set in the constant loading block of the corresponding dimension. 
- **If the SetBlockNew interface is used to replace a block containing a block entity, except for a custom block entity, when the block entity type before and after the replacement is the same, the data in the block entity will not change. ** 
For example, if an item is placed in a box, and the SetBlockNew interface is used to replace the box block with a box block, the new box still retains the items in the old box. <br> 
To avoid this situation, add a block replacement with a different block entity type (or without a block entity) in the middle. For example, replace the box with air first, and then replace the air with a box. 
- As the version is updated, the block state corresponding to the aux value will change. For blocks with multiple states, the aux calculation method is more complicated. It is recommended to get the traditional aux value through GetBlockAuxValueFromStates before setting it. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 

comp = serverApi.GetEngineCompFactory().CreateBlockState(levelId) 
# GetBlockAuxValueFromStates only needs to be called once, and the auxValue obtained can be cached for subsequent use 
auxValue = comp.GetBlockAuxValueFromStates("minecraft:wool", { 'color': 'orange' }) 

blockDict = { 
'name': 'minecraft:wool', 
'aux': auxValue 
} 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
comp.SetBlockNew((0, 5, 0), blockDict, 0, 0, True) 
``` 

## SetLiquidBlock


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Set the extraBlock of a block at a certain position. You can set the water content of the block here, etc. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| blockDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Block Information Dictionary">Block Information Dictionary</a> | 
| dimensionId | int | Dimension where the block is located, required parameter | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- Blocks can only be set on terrain that has been loaded. Blocks can be set in the constant loading block of the corresponding dimension. 
- dimensionId needs to be the dimension where the playerId corresponds to the player; if dimensionId is -1, the dimension where the playerId corresponds to the player is used by default 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
blockDict = { 
'name': 'minecraft:water', 
'aux': 5 
} 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId) 
comp.SetLiquidBlock((0, 5, 0), blockDict, 0) 
``` 

## SetSnowBlock 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Set the block at a certain location to contain snow


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| dimensionId | int | Block dimension, required parameter | 
| height | int | Snow block height, default is 1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- Blocks can only be set on loaded terrains. Blocks can be set in the constantly loaded chunks of the corresponding dimension. 
- dimensionId needs to be the dimension of the player corresponding to playerId; if dimensionId is -1, the dimension of the player corresponding to playerId is used by default 

- Example 

```python 
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId)
comp.SetSnowBlock((0, 5, 0), 0, 1)
```