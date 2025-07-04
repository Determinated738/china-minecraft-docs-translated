--- 
sidebarDepth: 1 
--- 
# Block geometry model 

## CombineBlockBetweenPosToGeometry 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockGeometryCompClient.BlockGeometryCompClient 

- Description 

Based on the two input positions, search for all blocks between the two positions, and merge and convert these blocks into a geometry model that can be used for entities. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| startPos | tuple(int,int,int) | Starting position | 
| endPos | tuple(int,int,int) | End position | 
| geometryName | str | The name of the geometry model, used to identify each geometry model, equivalent to the id of the model | 
| unsupportedMode | int | Enumeration of unsupported block processing methods, optional parameter, the input value is 0, 1. The default value is 0. If there are blocks in the block palette that do not support conversion to geometry, they will be processed as follows: 0: Skip the unsupported blocks and continue to generate. 1: Stop generating | 
| useStructureVoid | bool | Whether to use structure voids instead of air blocks, optional parameter, the default value is False. True means using structure voids, False means not using structure voids. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockPaletteComponent | Returns the block palette instance generated during the merge process. If the creation fails, it returns None | 

- Notes 
- If there is already a geometry model with the same name, the merged new model will overwrite the previous model. Therefore, it should be noted that the geometryName should be different each time models with different appearances are merged. 
- If the models merged each time are models with the same appearance, we recommend using the same geometryName to save memory for storing models. Of course, the best case is to reuse the previously created block geometry models as much as possible instead of repeatedly merging new models. 
- The block types that are not currently supported are (will be supported in subsequent versions): 
1. Custom block entity appearance (see Development Guide-Gameplay Development-Custom Game Content-Custom Block-Custom Block Entity Appearance) 
2. Miniature Blocks (see Development Guide-Gameplay Development-Custom Game Content-Miniature Blocks) 
3. Fire Blocks, Water Blocks 
4. Flower Pots 
5. Bells 
6. End Portal, End Warp Gate 
7. Barriers 
8. Tidal Core 
9. Flags 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
blockGeometryComp = clientApi.GetEngineCompFactory().CreateBlockGeometry(levelId)

palette = blockGeometryComp.CombineBlockBetweenPosToGeometry((200,64,200),(201,65,202),"my_block_geometry") 
``` 

## CombineBlockFromPosListToGeometry 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockGeometryCompClient.BlockGeometryCompClient 

- Description 

Based on the input block position list, search for all blocks at these positions, and merge and convert these blocks into geometric models that can be used for entities. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| posList | list(tuple(int,int,int)) | Block position list | 
| geometryName | str | The name of the geometry model, used to identify each geometry model, equivalent to the id of the model | 
| unsupportedMode | int | Enumeration of unsupported block processing methods, optional parameter, the input value is 0, 1. The default value is 0. If there are blocks in the block palette that do not support conversion to geometry, they will be processed as follows: 0: Skip the unsupported blocks and continue to generate. 1: Stop generating | 
| useStructureVoid | bool | Whether to use structure voids instead of air blocks, optional parameter, the default value is False. True means using structure voids, False means not using structure voids. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockPaletteComponent | Returns the block palette instance generated during the merge process. If the creation fails, it returns None | 

- Notes 
- If there is already a geometry model with the same name, the merged new model will overwrite the previous model. Therefore, it should be noted that the geometryName should be different each time models with different appearances are merged. 
- If the models merged each time are models with the same appearance, we recommend using the same geometryName to save memory for storing models. Of course, the best case is to reuse the previously created block geometry models as much as possible instead of repeatedly merging new models. 
- The block types that are not currently supported are (will be supported in subsequent versions): 
1. Custom block entity appearance (see Development Guide-Game Development-Custom Game Content-Custom Block-Custom Block Entity Appearance) 
2. Miniature Block (see Development Guide-Game Development-Custom Game Content-Miniature Block) 
3. Fire Block, Water Block 
4. Flower Pot 
5. Bell 
6. End Portal, End Warp Gate 
7. Barrier 
8. Conduit 
9. Banner 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
blockGeometryComp = clientApi.GetEngineCompFactory().CreateBlockGeometry(levelId) 
palette = blockGeometryComp.CombineBlockFromPosListToGeometry([(200,64,200),(201,65,202)],"my_block_geometry")

``` 

## CombineBlockPaletteToGeometry 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.blockGeometryCompClient.BlockGeometryCompClient 

- Description 

Combine all blocks in BlockPalette and convert them into a geometry model that can be used for entities. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockPalette | BlockPaletteComponent | Block palette, obtained by GetBlockPaletteBetweenPos and GetBlockPaletteFromPosList interfaces | 
| geometryName | str | The name of the geometry model, used to identify each geometry model, equivalent to the id of the model. | 
| unsupportedMode | int | Enumeration of unsupported block processing methods, optional parameter, the input value can be 0 or 1. The default value is 0. If there are blocks in the block palette that do not support conversion to geometry, they will be processed as follows: 0: Skip the unsupported blocks and continue to generate. 1: Stop generating | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Returns the name of the geometry model after successful generation, and None if generation fails. The geometry model name is consistent with the input parameter geometryName. | 

- Notes 
- If there is already a geometry model with the same name, the merged new model will overwrite the previous model. Therefore, it is important to note that geometryName should be different each time models with different appearances are merged. 
- If the models merged each time are models with the same appearance, we recommend using the same geometryName to save memory for storing models. Of course, the best situation is to reuse the previously created block geometry models as much as possible, rather than repeatedly merging new models. 
- Currently unsupported block types are (subsequent versions will support): 
1. Custom block entity appearance (see Development Guide-Game Development-Custom Game Content-Custom Block-Custom Block Entity Appearance) 
2. Miniature Block (see Development Guide-Game Development-Custom Game Content-Miniature Block) 
3. Fire Block, Water Block 
4. Flower Pot 
5. Bell 
6. End Portal, End Warp Gate 
7. Barrier 
8. Tidal Core 
9. Banner 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
blockComp = clientApi.GetEngineCompFactory().CreateBlock(levelId) 
palette = blockComp.GetBlockPaletteBetweenPos((200,64,200),(201,65,202))
blockGeometryComp = clientApi.GetEngineCompFactory().CreateBlockGeometry(levelId)
geometryName = blockGeometryComp.CombineBlockPaletteToGeometry(palette,"my_block_geometry")

print geometryName 
``` 

## EnableActorBlockGeometryTransparent 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Set whether to allow entity block geometry models to generate transparency. If it is enabled, the block geometry model will become transparent by adjusting the transparency of the block geometry. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| geometryName | str | The name of the geometry model, used to identify each geometry model, which is equivalent to the id of the model. | 
| enable | bool | Whether to allow entity block geometry models to generate transparency. True means allowed, False means not allowed. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether the operation is successful. Return True if successful, and False if failed. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
actorRenderComp = clientApi.GetEngineCompFactory().CreateActorRender("-4294967295") 
# Enable transparency of block geometry models 
print actorRenderComp.EnableActorBlockGeometryTransparent("my_block_geometry", True) 
# Adjust the transparency of the block geometry model to 0.5 
print actorRenderComp.SetActorBlockGeometryTransparency("my_block_geometry", 0.5) 
``` 

## SetActorBlockGeometryOffset 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Set the position offset of the entity's block geometry model.


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| geometryName | str | The name of the geometry model, used to identify each geometry model, equivalent to the id of the model | 
| offset | tuple(float,float,float) | The position offset value of the block geometry model relative to the entity, the default is (0, 0, 0). | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether it is successful, return True if successful, and return False if failed. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
actorRenderComp = clientApi.GetEngineCompFactory().CreateActorRender("-4294967295") 
print actorRenderComp.SetActorBlockGeometryOffset("my_block_geometry", (1,1,1)) 
``` 

## SetActorBlockGeometryRotation 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Sets the rotation of the entity's block geometry model. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| geometryName | str | The name of the geometry model, used to identify each geometry model, equivalent to the id of the model | 
| rotation | tuple(float,float,float) | The rotation angle of the block geometry model relative to the entity, the default is (0, 0, 0), which represents the rotation angle around the x, y, and z axes respectively, and the rotation order is z, x, y. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether it is successful, return True if successful, and return False if failed. | 

- Example 

```python

import mod.client.extraClientApi as clientApi 
actorRenderComp = clientApi.GetEngineCompFactory().CreateActorRender("-4294967295") 
print actorRenderComp.SetActorBlockGeometryRotation("my_block_geometry", (90,0,0)) 
``` 

## SetActorBlockGeometryTransparency 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.actorRenderCompClient.ActorRenderCompClient 

- Description 

Sets the transparency of the entity's block geometry model. Note that this interface will only take effect after the interface EnableActorBlockGeometryTransparent is called to enable the transparency of the block geometry model. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| geometryName | str | The name of the geometry model, used to identify each geometry model, equivalent to the id of the model. | 
| transparent | float | The transparency of the block geometry model, the range value is [0,1]. Values exceeding this range will be truncated to 0 or 1. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether it is successful, return True if successful, and return False if failed. | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
actorRenderComp = clientApi.GetEngineCompFactory().CreateActorRender("-4294967295") 
# Enable transparency of block geometry models 
print actorRenderComp.EnableActorBlockGeometryTransparent("my_block_geometry", True) 
# Adjust the transparency of the block geometry model to 0.5 
print actorRenderComp.SetActorBlockGeometryTransparency("my_block_geometry", 0.5) 
``` 

