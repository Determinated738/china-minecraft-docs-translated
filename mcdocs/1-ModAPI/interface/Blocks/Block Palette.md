--- 
sidebarDepth: 1 
--- 
# Block Palette 

## DeleteBlockInBlockPalette 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.component.blockPaletteComp.BlockPaletteComponent 

- Description 

Delete a block of a certain type in the BlockPalette. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block name. | 
| auxValue | int | Block additional value. Optional parameter, default value is -1. If the block additional value is not filled in, all blocks with this name will be deleted. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Returns the number of blocks successfully deleted | 

- Notes 
- When deleting a door or bed type block, please use the additional value of the head of the bed or the additional value of the lower half of the door to delete. The deletion process will be invalid when using the additional value of the foot of the bed and the upper half of the door. 

- Example

```python
# Client call
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateBlock(levelId)
palette = comp.GetBlockPaletteBetweenPos((200,64,200),(201,65,202))
count = palette.DeleteBlockInBlockPalette("minecraft:grass", 0)
print count
# Server call
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateBlock(levelId)
palette = comp.GetBlockPaletteBetweenPos(0, (200,64,200),(201,65,202))
count = palette.DeleteBlockInBlockPalette("minecraft:grass", 0)
print count
```

## DeserializeBlockPalette 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.component.blockPaletteComp.BlockPaletteComponent 

- Description 

Deserializes the data in the block palette data dictionary, which is used to transmit the block palette event data between the client and the server. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dataDict | dict | Block palette data dictionary. Use the interface SerializeBlockPalette to obtain it. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether deserialization is successful, return True if successful, return False if failed | 

- Example 

```python 
# Client call 
# In event callback function 
def onGetBlockPalette(self, data): 
dataDict = data['data'] 
comp = clientApi.GetEngineCompFactory().CreateBlock(levelId) 
newPalette = comp.GetBlankBlockPalette() 
newPalette.DeserializeBlockPalette(dataDict) 

# Server call 
# In event callback function 
def onGetBlockPalette(self, data): 
dataDict = data['data'] 
comp = serverApi.GetEngineCompFactory().CreateBlock(levelId)
    newPalette = comp.GetBlankBlockPalette()
    newPalette.DeserializeBlockPalette(dataDict)
```



## GetBlockCountInBlockPalette

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span>

method in mod.common.component.blockPaletteComp.BlockPaletteComponent

- Description 

Get the number of blocks of a certain type in the BlockPalette. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block name | 
| auxValue | int | Block additional value. Optional parameter, default value is -1. If the block additional value is not filled in, the number of all blocks that match this name is obtained. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Returns the number of blocks of this type | 

- Example 

```python 
# Client call 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlock(levelId) 
palette = comp.GetBlockPaletteBetweenPos((200,64,200),(201,65,202)) 
count = palette.GetBlockCountInBlockPalette("minecraft:grass", 0) 
print count 
# Server call 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlock(levelId) 
palette = comp.GetBlockPaletteBetweenPos(0, (200,64,200),(201,65,202)) 
count = palette.GetBlockCountInBlockPalette("minecraft:grass", 0) 
print count 
``` 

## GetLocalPosListOfBlocks 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.component.blockPaletteComp.BlockPaletteComponent 

- Description 

Gets a list of the relative positions of a block in a block palette. The block palette records the block combination in a three-dimensional space composed of multiple blocks, and the relative position refers to the relative position of the coordinate axis with the position of the block with the smallest coordinate among these blocks as the origin. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| blockName | str | Block name. | 
| auxValue | int | Block additional value. Optional parameter, default value is -1. If the block additional value is not filled in, the relative position list of all blocks that match this block name is obtained. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(tuple(int,int,int)) | Returns the relative position list occupied by blocks of this type. If the block does not exist, an empty list is returned. |

- Example

```python
# Client call
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateBlock(levelId)
palette = comp.GetBlockPaletteBetweenPos((200,64,200),(201,65,202))
result = palette.GetLocalPosListOfBlocks("minecraft:grass")
print result
# Server call
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateBlock(levelId)
palette = comp.GetBlockPaletteBetweenPos(0, (200,64,200),(201,65,202))
result = palette.GetLocalPosListOfBlocks("minecraft:grass") 
print result 
``` 

## GetVolumeOfBlockPalette 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.component.blockPaletteComp.BlockPaletteComponent 

- Description 

Get the length, width and height of the cuboid occupied by the BlockPalette. The length refers to the length of the x-axis in the world coordinates of the BlockPalette, the width refers to the length of the z-axis, and the height refers to the length of the y-axis. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(int,int,int) | Returns the length, width, and height tuple of the block palette BlockPalette, which are the values of length, width, and height in order. | 

- Example 


```python
# Client call
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateBlock(levelId)
palette = comp.GetBlockPaletteBetweenPos((200,64,200),(201,65,202))
result = palette.GetVolumeOfBlockPalette()
print result
# Server call
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateBlock(levelId)
palette = comp.GetBlockPaletteBetweenPos(0, (200,64,200),(201,65,202))
result = palette.GetVolumeOfBlockPalette()
print result
```



## ReplaceAirByStructureVoid 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.component.blockPaletteComp.BlockPaletteComponent 

- Description 

Sets whether to replace all air blocks in the BlockPalette with structure voids. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| enable | bool | Whether to replace air blocks with structure voids. True means replacing with empty structure, False means using air blocks | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the replacement is successful, True is returned if successful, False is returned if failed | 

- Example 

```python 
# Client call 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlock(levelId) 
palette = comp.GetBlockPaletteBetweenPos((200,64,200),(201,65,202)) 
print palette.ReplaceAirByStructureVoid(True) 
# Server call 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlock(levelId)

palette = comp.GetBlockPaletteBetweenPos(0, (200,64,200),(201,65,202)) 
print palette.ReplaceAirByStructureVoid(True) 
``` 

## ReplaceBlockInBlockPalette 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.component.blockPaletteComp.BlockPaletteComponent 

- Description 

Replace a block of a certain type in the BlockPalette. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| newblockName | str | New block name. | 
| newBlockAux | int | Additional value of the new block. | 
| oldBlockName | str | Name of the block to be replaced. | 
| oldBlockAux | int | Additional value of the block name to be replaced. Optional parameter. If the additional value is not filled in, all blocks matching this name will be replaced. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Returns the number of blocks successfully replaced | 

- Notes 
- Note that when replacing blocks, if the new block uses the additional value of the bed block and the end of the bed, or the additional value of the door block and the upper half of the door block, the replacement process will be ignored. Please use the additional value of the head of the bed or the lower half of the door to replace it. Similarly, the replaced block should also use the additional value of the head of the bed or the upper half of the door. 
- Note that after replacing other blocks with the bed block and the additional value of the bed head, or the door block and the additional value of the lower half of the door, when using the interface SetBlockByBlockPalette to set the palette, if there are blocks from other block palettes at the end of the bed or the upper half of the door, conflicts will occur. The conflict will be handled according to the conflict mode parameters in the interface SetBlockByBlockPalette. 

- Example

```python
# Client call
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateBlock(levelId)
palette = comp.GetBlockPaletteBetweenPos((200,64,200),(201,65,202))
count = palette.ReplaceBlockInBlockPalette("minecraft:vine", 4,"minecraft:grass", 0)
print count
# Server call
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateBlock(levelId)
palette = comp.GetBlockPaletteBetweenPos(0, (200,64,200),(201,65,202))
count = palette.ReplaceBlockInBlockPalette("minecraft:vine", 4,"minecraft:grass", 0)
print count

``` 

## SerializeBlockPalette 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.component.blockPaletteComp.BlockPaletteComponent 

- Description 

Serializes the data in the block palette, which is used to transmit the event data of the block palette between the client and the server. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Serialized data of block palette | 

- Example 

```python 
# Client call 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlock(levelId) 
sourcePalette = comp.GetBlockPaletteBetweenPos((200,64,200),(201,65,202)) 
dataDict = sourcePalette.SerializeBlockPalette() 
# Used to pass block palette data in events 
eventData = self.CreateEventData() 
eventData['data'] = dataDict 
self.NotifyToServer(modConfig.GetBlockPaletteEvent, eventData) 

# Server call 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlock(levelId) 
sourcePalette = comp.GetBlockPaletteBetweenPos((200,64,200),(201,65,202)) 
dataDict = sourcePalette.SerializeBlockPalette() 
# Used to pass block palette data in events 
eventData = self.CreateEventData() 
eventData['data'] = dataDict 
self.NotifyToClient(modConfig.GetBlockPaletteEvent, eventData) 
``` 

