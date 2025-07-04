--- 
sidebarDepth: 1 
--- 
# Properties 

## GetBlockBasicInfo 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Get basic information about a block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| blockName | str | Block identifier | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Block Basic Information Dictionary#Block Basic Information Dictionary">Block Basic Information Dictionary</a> | 

- Notes 
- Some fields in the basic information dictionary will only get data when adding specified components when customizing blocks. For details, see <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Block Basic Information Dictionary#Block Basic Information Dictionary">Block Basic Information Dictionary</a> 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
blockDict = comp.GetBlockBasicInfo("minecraft:stone") 
``` 

## SetBlockBasicInfo 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Set basic information of blocks 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier | 
| infoDict | dict | Block's <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Block Basic Information Dictionary#Block Basic Information Dictionary">Block Basic Information Dictionary</a> | 
| auxValue | int | Block additional value, default is 0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Currently the attributes supported by this interface are destroyTime: hardness; explosionResistance: explosion resistance; loot: drop attribute; tier: mining attribute; solid: solid or not; can only be modified when there is a corresponding component in the block json configuration 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
blockDict = comp.SetBlockBasicInfo("minecraft:stone", {"blockLightEmission":1, 
"blockLightAbsorption":1, 
"solid":False, 
"tier":{"level":3}}) 
``` 

