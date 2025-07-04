--- 
sidebarDepth: 1 
--- 
# Block combination 

## CreateMicroBlockResStr 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockCompServer.BlockCompServer 

- Description 

Generates a Json string of microblock resources 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| identifier | str | Microblock unique identifier | 
| start | tuple(int,int,int) | Microblock start coordinates | 
| end | tuple(int,int,int) | Microblock end coordinates | 
| colorMap | dict | Default is None, microblock color correspondence table | 
| isMerge | bool | Default is False, whether to merge blocks of the same type | 
| icon | str | Default is an empty string, a miniature block icon, which needs to be defined in terrain_texture.json | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | The resource string of the generated miniature block | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlock(levelId) 
result = comp.CreateMicroBlockResStr("x", (12, 60, 12), (26, 76, 26), colorMap={'minecraft:grass': [12, 22, 123, 255]}, isMerge=True, icon="micro_block_datiangou") 
with open("micro_block_x.json", "w+") as f: 
f.write(result) 
#In this example, the block will be miniaturized with (12 60 12) as the starting point and (26 76 26) as the end point. The color of all grass blocks in the miniaturized block will be rgba(12,22,123,255). The actual display color will be fine-tuned according to the ambient light. The icon in the inventory is the image corresponding to micro_block_datiangou in terrain_texture.json. 
``` 

## GetBlankBlockPalette 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface


<span id="s0"></span> 
method in mod.server.component.blockCompServer.BlockCompServer 

- Description 

Get a blank block palette. 

- Parameters 

None 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| BlockPaletteComponent | Returns the generated block palette instance, or None if the acquisition fails | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlock(levelId) 
blankPalette = comp.GetBlankBlockPalette() 
``` 

### Client Interface 

<span id="c0"></span> 
method in mod.client.component.blockCompClient.BlockCompClient 

- Description 

Get a blank block palette. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockPaletteComponent | Returns the generated block palette instance, or None if the acquisition fails | 

- Example 

```python

import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlock(levelId) 
blankPalette = comp.GetBlankBlockPalette() 
``` 
## GetBlockPaletteBetweenPos 
<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 
### Server Interface 
<span id="s0"></span> 
method in mod.server.component.blockCompServer.BlockCompServer 

- Description 

Create and get a block palette based on the two input block positions. The block palette is used to describe and record the combination of multiple blocks in the world. This block palette contains all blocks between the two positions and their relative positions. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimensionId | int | Dimension of the block | 
| startBlockPos | tuple(int,int,int) | Start block position | 
| endBlockPos | tuple(int,int,int) | End block position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockPaletteComponent | Returns the generated block palette instance, or None if creation fails | 

- Notes 
- For bed blocks, when the block palette obtains the bed block, only the block at the head of the bed is added, and the block at the end of the bed is ignored. For the door block, only the blocks in the lower half of the door will be added, and the upper half of the door will be ignored. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
# playerId can be None, or the player's id can be passed in. When the passed dimensionId is 0 or a positive value, the area is obtained by relying on the dimensionId; when the passed dimensionId is a negative value, the area is obtained by relying on the passed playerId. 
comp = serverApi.GetEngineCompFactory().CreateBlock(entityId) 
palette = comp.GetBlockPaletteBetweenPos(0, (200,64,200),(201,65,202)) 
``` 

### Client interface 


<span id="c0"></span> 
method in mod.client.component.blockCompClient.BlockCompClient 

- Description 

Create and get a block palette based on the two input positions. This interface searches for all blocks between the two positions to create a block palette. The block palette is used to describe and record the combination of multiple blocks in the world. This block palette contains all blocks between the two positions and their relative positions. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| startPos | tuple(int,int,int) | Starting position | 
| endPos | tuple(int,int,int) | End position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockPaletteComponent | Returns the generated block palette instance. If the creation fails, it returns None | 

- Notes 
- For bed blocks, when the block palette obtains the bed blocks, only the blocks at the head of the bed are added, and the blocks at the end of the bed are ignored. For door blocks, only the blocks in the lower half of the door are added, and the blocks in the upper half of the door are ignored. 
- You need to wait for the blocks in the area to be fully loaded to get the palette correctly 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlock(levelId) 
palette = comp.GetBlockPaletteBetweenPos((200,64,200),(201,65,202)) 
``` 

## GetBlockPaletteFromPosList 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.blockCompServer.BlockCompServer 

- Description 

Create and get a block palette based on the input block position list. The block palette is used to describe and record the combination of multiple blocks in the world. The created block palette contains all the blocks in this position list and their relative positions. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| dimensionId | int | The dimension where the block is located | 
| posList | list(tuple(int,int,int)) | Block position list | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockPaletteComponent | Returns the generated block palette instance. If the creation fails, it returns None | 

- Notes 
- For bed blocks, when the block palette obtains the bed block, only the blocks at the head of the bed are added, and the blocks at the end of the bed are ignored. For door blocks, only the blocks in the lower half of the door are added, and the blocks in the upper half of the door are ignored. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
# playerId can be None, or the player's id can be passed in. When the passed dimensionId is 0 or a positive value, the region is obtained by relying on the dimensionId; when the passed dimensionId is a negative value, the region is obtained by relying on the passed playerId. 
comp = serverApi.GetEngineCompFactory().CreateBlock(entityId) 
palette = comp.GetBlockPaletteFromPosList(0, 
[(200,64,200), 
(201,64,200) 
(202,64,200) 
]) 
``` 

### Client Interface 

<span id="c0"></span> 
method in mod.client.component.blockCompClient.BlockCompClient 

- Description 

Create and get a block palette based on the input block position list. The block palette is used to describe and record the combination of multiple blocks in the world. The created block palette contains all blocks in this position list and their relative positions. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| posList | list(tuple(int,int,int)) | Block position list | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockPaletteComponent | Returns the generated block palette instance, or None if creation fails | 

- Notes

- For bed blocks, when the block palette gets the bed blocks, only the blocks at the head of the bed will be added, and the blocks at the end of the bed will be ignored. For door blocks, only the blocks at the lower half of the door will be added, and the blocks at the upper half of the door will be ignored. 
- You need to wait for the blocks in the list to be fully loaded to get the palette correctly 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateBlock(levelId) 
palette = comp.GetBlockPaletteFromPosList([ 
(200,64,200), 
(201,64,200) 
(202,64,200) 
]) 
``` 

## RegisterBlockPatterns 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockCompServer.BlockCompServer 

- Description 

Register special block combination 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pattern | list(str) | Block combination position | 
| defines | dict | Block combination type | 
| result_actor_name | str | Synthesis result | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Note: This pattern does not limit the direction. As long as it can be successfully combined on any plane, the corresponding entity can be synthesized. 
- As shown in the sample code, the position where the block does not need to be placed needs to be explicitly defined as an air block 
- When the same pattern and defines have been registered in the engine, this interface will not update result_actor_name and return False 

- Example 

```python 
import mod.server.extraServerApi as serverApi

comp = serverApi.GetEngineCompFactory().CreateBlock(levelId) 
pattern = [ 
'A#A', 
'XXX', 
'AXA' 
] 
defines ={ 
'#': 'minecraft:gold_block', 
'X': 'minecraft:iron_block', 
'A': 'minecraft:air', 
} 
comp.RegisterBlockPatterns(pattern,defines,'minecraft:chicken') 
#In this example, iron blocks are placed in the left, middle, right, and bottom, and gold blocks are placed on top, which will generate a chicken 
``` 

## SetBlockByBlockPalette 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockCompServer.BlockCompServer 

- Description 

According to the input block palette content, all blocks recorded in the palette are set to actual blocks. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockPalette | BlockPaletteComponent | Block palette, obtained by GetBlockPaletteBetweenPos and GetBlockPaletteFromPosList interfaces | 
| dimensionId | int | The dimension where the block is located. If the input value is less than 0, entityId is used to obtain the block where the block is set. | 
| pos | tuple(int,int,int) | Set the origin of the block. The block will be set with this position as the origin. | 
| rotation | int | The rotation of the block assembly. The rotation direction is around the y-axis where the origin of the block is set. The rotation angle only supports -270, -180, -90, 0, 90, 180, 270. If the value passed in is not one of these, the value closest to the input value will be taken. | 
| conflictMode | int | Conflict mode enumeration, optional parameter, default is 0. During the generation process, if there are other blocks at the generated location, it will be processed according to the conflict mode. The values that can be entered are: 0, 1, 2, which respectively represent: 0: replace the block in the map, 1: skip this block, 2: abandon the subsequent generation process. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the generation process is successful. If the entire generation process cannot be completed, False is returned. If the entire generation process is completed, True is returned. If the conflict mode is 2, the subsequent generation process is abandoned when a conflicting block is encountered, and the interface will also return False at this time. | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlock(entityId) 
palette = comp.GetBlockPaletteBetweenPos(0, (200,64,200),(201,65,202)) 
# Set the block in the palette with (205,64,200) as the origin, rotate 90 degrees, and set the conflict mode to 0, which means replacing the block in the map.

comp.SetBlockByBlockPalette(palette, 0, (205,64,200),90,0)
```