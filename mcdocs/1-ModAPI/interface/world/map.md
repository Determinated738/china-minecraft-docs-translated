--- 
sidebarDepth: 1 
--- 
# Map 

## CanSee 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Determine whether the starting object can see the target object, based on the object's Head position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fromId | str | Starting object ID | 
| targetId | str | Target object ID | 
| viewRange | float | Field of view distance, default value 8.0 | 
| onlySolid | bool | Only determine if solid blocks are blocking, default True; False means liquid blocks will also block | 
| angleX | float | Field of view X-axis angle, default value 180.0 degrees | 
| angleY | float | Field of view Y-axis angle, default value 180.0 degrees | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Visible or not | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(entityId) 
comp.CanSee(entityId,targetId,20.0,True,180.0,180.0) 
``` 

## CheckBlockToPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer

- describe


Determine whether there is a block between positions 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fromPos | tuple(float,float,float) | Starting position | 
| toPos | tuple(float,float,float) | Ending position | 
| dimensionId | int | Dimension of the position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | result -1: Failed to obtain 0: No block 1: There is a block | 

- Notes 
- Supports determining whether there is a block between positions in the constant loading block of the corresponding dimension 
- Returning -1 is usually because the passed dimension does not exist, the passed parameter is incorrect, the chunk where the passed position is located has not been loaded, etc. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
from mod_log import logger as logger 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
if comp.CheckBlockToPos((0, 0, 0), (1, 1, 1), 0): 
logger.info("There is a block between (0, 0, 0) and (1, 1, 1)") 
``` 

## CheckChunkState 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Determine whether the chunk at the specified position has been loaded 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension where chunk is located | 
| pos | tuple(int,int,int) | Coordinates of the specified position | 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Loading completed | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
comp.CheckChunkState(0, (0, 0, 0)) 
``` 

## CreateDimension 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 

Create a new dimension 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimensionId | int | Dimension, 0/1/2 dimensions do not need to be created. To create a dimension greater than 20, you need to register it in dimension_config.json. Note that dimension 21 is not available. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the creation is successful | 

- Notes 
- It is recommended to call them uniformly when the mod is initialized 
- Interfaces related to dimensions (SetUseLocalTime, SetDimensionUseLocalWeather, etc.) will affect the generation of the birth point. If you want to use the main world terrain to generate the birth point, you need to call CreateDimension(0) once when the mod is initialized. 

- Example 

```python 
comp = serverApi.GetEngineCompFactory().CreateDimension(levelId) 
comp.CreateDimension(3) 
``` 



## CreateExplosion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.explosionCompServer.ExplosionComponentServer 

- Description 

Used to generate explosions 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Explosion position | 
| radius | int | Explosion power. For specific meanings, please refer to the explanation of explosion in [wiki](https://minecraft-zh.gamepedia.com/%E7%88%86%E7%82%B8) | 
| fire | bool | Whether to bring fire | 
| breaks | bool | Whether to destroy blocks | 
| sourceId | str | Entity id of the explosion damage source | 
| playerId | str | Entity id created by the explosion | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExplosion(levelId) 
comp.CreateExplosion((50,50,50),10,True,True,sourceId,playerId) 
``` 

## DeleteAllArea 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Delete all constantly loading areas 

- Parameters 

None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Number of areas to delete, None if error occurs | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
comp.DeleteAllArea() 
``` 

## DeleteArea 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Delete a constantly loaded area 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| key | str | Name of the constantly loaded area | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
comp.DeleteArea('Area0') 
``` 

## DetectStructure


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.portalCompServer.PortalComponentServer 

- Description 

Detect the structure of a custom door 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | None | This parameter is not used, just pass None | 
| pattern | list(str) | Portal shape | 
| defines | dict | Portal definition | 
| touchPos | list(tuple(int,int)) | Portal activatable position (relative to the position defined in the parameter pattern) | 
| pos | tuple(int,int,int) | Use item coordinates | 
| dimensionId | int | Portal dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(bool,tuple(int,int,int),tuple(int,int,int)) | Detection result, portal start position, direction | 

- Example 

```python 
#Portal definition 
defines = { 
'#': 'minecraft:glowstone', 
'*': 'minecraft:air' 
} 
#Portal shape 
pattern = [ 
'####', 
'#**#', 
'#**#', 
'####', 
] 
# Click the two positions at the bottom to activate 
touchPos =[(3,1),(3,2)] 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePortal(levelId) 
ret = comp.DetectStructure(None, pattern, defines, touchPos, (12, 1, 5), 0) 
if ret[0]: 
logger.info('Custom portal built successfully') 
else: 
logger.info('Custom portal built failed')

``` 

## GetAllAreaKeys 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Get a list of all frequently loaded area names 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Name list list | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
comp.GetAllAreaKeys() 
``` 

## GetBiomeName 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.biomeCompServer.BiomeCompServer 

- Description 

Get the biome information of a certain location 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Specified position | 
| dimId | int | Dimension id |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | The name of the biome to which the location belongs | 

- Notes 
- Supports obtaining the biome of unloaded chunks. However, for unloaded chunks, the terrain generator will be used to calculate the biome instead of the biome saved in the archive. Therefore, for maps that have been modified using the map editor, obtaining the biome of unloaded chunks may not match the actual result. It is recommended to confirm that the chunk has been loaded before obtaining it. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBiome(levelId) 
biomeName = comp.GetBiomeName((0, 80, 0), 0) 
``` 

## GetBlockLightLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Get the light level of the block position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| dimensionId | int | Dimension where the block is located | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Light level | 

- Notes 
- Only the light level of the block position in the loaded chunk can be obtained, and the light level in the frequently loaded chunk of the corresponding dimension can be obtained. 

- Example 

```python 
import mod.server.extraServerApi as serverApi

comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
lightlevel = comp.GetBlockLightLevel((x,y,z), 0) 
``` 

## GetChunkEntites 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Get a list of all entity and player IDs in the chunk at the specified location 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension | 
| pos | tuple(int,int,int) | Coordinates of the specified location | 

- Return value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| None or list(str) | List of entity and player IDs. Returns None if the chunk at the specified position does not exist or has not been loaded yet | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
entityList = comp.GetChunkEntites(0, (0, 0, 0)) 
print "GetChunkEntites entityList={}".format(entityList) 
``` 

## GetChunkMaxPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Get the coordinates of the largest point in a block 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| chunkPos | tuple(int,int) | Coordinates of the specified chunk | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None or tuple(int,int,int) | Coordinates of the maximum point of the chunk | 

- Notes 
- When the passed chunkPos type is not tuple or the length is not 2, the return value is None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
maxPos = comp.GetChunkMaxPos((1, 3)) 
``` 

## GetChunkMinPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Get the coordinates of the minimum point of a chunk 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| chunkPos | tuple(int,int) | Coordinates of the specified chunk | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None or tuple(int,int,int) | Coordinates of the minimum point of the chunk | 

- Notes 
- When the passed chunkPos type is not tuple or the length is not 2, the return value is None 


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
minPos = comp.GetChunkMinPos((1, 3)) 
``` 

## GetChunkMobNum 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Get the number of mobs in a chunk (excluding players, but including armor stands) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension of the chunk | 
| chunkPos | tuple(int,int) | Specifies the coordinates of the chunk | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Number of mobs in the chunk | 

- Notes 
- A return value of -1 is usually due to the dimension not being loaded or the chunk not being loaded 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
mobNum = comp.GetChunkMobNum(0, (1, 3)) 
``` 

## GetChunkPosFromBlockPos 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 


### Server interface 

<span id="s0"></span> 
method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Get the block coordinates of the block through the block coordinates 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockPos | tuple(int,int,int) | Block coordinates | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None or tuple(int,int) | Block coordinates | 

- Notes 
- When the passed blockPos type is not tuple or the length is not 3, the return value is None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
chunkPos = comp.GetChunkPosFromBlockPos((90, 40, -4)) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.chunkSourceCompClient.ChunkSourceCompClient 

- Description 

Get the block coordinates of the block through the block coordinates 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockPos | tuple(int,int,int) | Block coordinates | 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None or tuple(int,int) | Coordinates of the block in which the block is located | 

- Notes 
- When the passed blockPos type is not tuple or the length is not 3, the return value is None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateChunkSource(LevelId) 
chunkPos = comp.GetChunkPosFromBlockPos((90, 40, -4)) 
``` 

## GetCurrentDimension 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

Get the current dimension of the client 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Dimension id. Returns -1 when the client has not completed login or is cutting the dimension | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
dimId = comp.GetCurrentDimension() 
``` 

## GetEntitiesAround 


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get the entity list in the area 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str | A certain entityId | 
| radius | int | Cube area radius | 
| filters | dict | Filter settings dictionary | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Returns a list of entityIds | 

- Notes 
- When filtering all entities in the region, the filter sets each entity to other and sets the entity corresponding to entityId to self. For detailed description of filters, users can view the Bedrock Edition wiki: https://bedrock.dev/zh/docs/stable/Entities#Filters 
- In the filter, "subject" indicates the entity type for the filter judgment, "subject"="self" indicates filtering the self set for each entity, and "subject"="other" indicates filtering the other set for each entity 

- Example 

```python 
#Use filters to get the entities around the player 
#The filter in the example indicates the entity that satisfies "is a player" or "does not wear a pumpkin hat" 
filters = { 
"any_of": [ 
{ 
"subject" : "other", 
"test" : "is_family", 
"value" : "player" 
}, 
{ 
"test" : "has_equipment", 
"domain": "head", 
"subject" : "other", 
"operator" : "not", 
"value" : "carved_pumpkin"
        }
    ]
}
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateGame(entityId)
comp.GetEntitiesAround(entityId, 100, filters)

``` 

## GetEntitiesAroundByType 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get a list of entities of a certain type in an area 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | EntityId of the center of the area, such as a player's entityid | 
| radius | int | Area radius | 
| entityType | int | [EntityType enumeration](../../enumeration value/EntityType.md) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Returns a list of entityId | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
# Get the dropped items within 10 grids around you 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.GetEntitiesAroundByType(entityId, 10, serverApi.GetMinecraftEnum().EntityType.ItemEntity) 
``` 

## GetEntitiesInSquareArea 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get a list of entities in an area 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | None | This parameter is deprecated | 
| startPos | tuple(int,int,int) | Initial position | 
| endPos | tuple(int,int,int) | End position | 
| dimensionId | int | The dimension where the region is located. You can get the entity list in the constant loading block of the corresponding dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Returns a list of entityId | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.GetEntitiesInSquareArea(None, (0,0,0), (100,100,100), 0) 
``` 
## GetEntityInArea 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.gameCompClient.GameComponentClient 
- Description 
Returns the entities in the area. You can get the list of entities loaded in the area. 
- Parameters 
| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or None | Entity Id | 
| pos_a | tuple(int,int,int) | Starting point | 
| pos_b | tuple(int,int,int) | End point, the end point should be greater than the start point | 
| exceptEntity | bool | Whether to exclude entityId from the returned result, the default is False, exceptEntity has no effect when the passed entityId is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | List of entityIds loaded within the region | 

- Example


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(levelId) 
entities = comp.GetEntityInArea(entityId, (0,0,0), (1,2,3)) 
``` 

## GetLevelId 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Get levelId. Some components need levelId to create, you can use this interface to get levelId. The level is the game of the current map. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | LevelId of the current map | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def ExtraDataTest(args): 
extraDataComp = serverApi.GetEngineCompFactory().CreateExtraData(serverApi.GetLevelId()) 
extraDataComp.score = 100 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 


- Description 

Get levelId. Some components need levelId to create, you can use this interface to get levelId. The level is the game of the current map. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | LevelId of the current map | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
ClientSystem = clientApi.GetClientSystemCls() 
class FpsClientSystem(ClientSystem): 
def CameraCompTest(args): 
cameraComp = clientApi.GetComponent(clientApi.GetLevelId(), 'Minecraft', 'camera') 
cameraComp.fov = 60 
``` 

## GetLoadedChunks 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Get the coordinate list of all chunks that have been loaded in the specified dimension 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None or list(tuple(int,int)) | List of chunk coordinates (chunk coordinates are (x,z)). When the specified dimension does not exist or has not been created, None is returned | 

- Example


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
result = comp.GetLoadedChunks(0) 
print "dimension {} has chunk {}".format(0, result) 
``` 

## GetSpawnDimension 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get the world spawn dimension 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Dimension id | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
spawnDimension = gameComp.GetSpawnDimension() 
``` 

## GetSpawnPosition 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get the world spawn point coordinates 


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(int,int,int) | Birth point coordinates | 

- Notes 
- The returned coordinates are not necessarily the exact birth point coordinates, nor are they necessarily safe birth points. When the player is born, a coordinate that meets the birth conditions will be randomly selected near the coordinates. 
- When the spawn position is not set using the setworldspawn command, the y-axis of the returned coordinate is 32767 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
spawnPos = gameComp.GetSpawnPosition() 
``` 

## IsChunkGenerated 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Get whether a chunk has been generated. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimensionId | int | Dimension where the chunk is located | 
| chunkPos | tuple(int,int) | Coordinates of the specified chunk | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the chunk has been generated | 

- Notes 
- Chunks that have been explored by the player (chunks within a radius of the player-centered, simulated distance (in the game's settings page)), or chunks near the constantly loaded chunks set using SetAddArea, are all generated chunks. These chunks will be saved in the archive, and will be read from the archive when explored again, and will not be regenerated. 


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
# Get whether the chunk at the coordinates of (10000,0,10000) in the main world has been generated 
result = comp.IsChunkGenerated(0, comp.GetChunkPosFromBlockPos((10000, 0, 10000))) 
``` 

## IsSlimeChunk 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Get whether a chunk is a slime chunk. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimensionId | int | Dimension of the chunk | 
| chunkPos | tuple(int,int) | Coordinates of the specified chunk | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the chunk is a slime chunk | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
result = comp.IsSlimeChunk(0, comp.GetChunkPosFromBlockPos((10000, 0, 10000)))
```



## LocateNeteaseFeatureRule

<span style="display:inline;color:#ff5555">Server</span>

method in mod.server.component.featureCompServer.FeatureCompServer

- Description 

Similar to the [/locate command](https://minecraft-zh.gamepedia.com/%E5%91%BD%E4%BB%A4/locate), used to locate <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/4-Custom Dimensions/4-Custom Features.html#Feature Rules (feature-rules)">NetEase Custom Feature Rules</a> 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | :--- | 
| ruleName | str | Feature rule name, in the form of namespace:featureRuleIdentifier, such as custombiomes:overworld_pumpkins_feature_rule | 
| dimensionId | int | Dimension to search, **requires the dimension to be loaded** | 
| pos | tuple(int,int,int) | Use this location as the center to find coordinates that meet the distribution conditions of NetEase custom feature rules | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) or None | The nearest coordinates that meet the distribution conditions of NetEase custom feature rules. If positioning fails, None is returned | 

- Notes 
- Positioning failure is usually due to the non-existence of the input dimension, the dimension is not loaded, there are no coordinates that meet the distribution conditions of the custom feature rule, the target coordinates are too far from the input location (with this location as the center, it cannot be found within a radius of 100 blocks), etc. 
- If a filter rule other than the judgment dimension is filled in "minecraft:biome_filter" in "conditions" in feature rules, there is a probability that the coordinates that meet the distribution conditions of the custom feature rule cannot be located. It is recommended that developers use query.is_biome instead in "iterations" of "distribution" 
- The positioning principle is to find possible locations based on the distribution conditions of NetEase's custom feature rules, so it is possible to locate the structure location that was canceled in the PlaceNeteaseStructureFeatureEvent event**. Developers should be careful to avoid calling the location function on the feature rule file corresponding to the structure that may be unplaced in the PlaceNeteaseStructureFeatureEvent event 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateFeature(levelId) 
pos = comp.LocateNeteaseFeatureRule("custombiomes:overworld_pumpkins_feature_rule", 0, (0, 64, 0)) 
``` 

## LocateStructureFeature 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.featureCompServer.FeatureCompServer 

- Description 

Similar to the [/locate command](https://minecraft-zh.gamepedia.com/%E5%91%BD%E4%BB%A4/locate), it is used to locate some structures in the original version, such as underwater temples, end cities, etc. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| featureType | int | The structure type of the original version, [StructureFeatureType](../../enumeration value/StructureFeatureType.md) enumeration | 
| dimensionId | int | The dimension where the structure is located, **requires that the dimension has been loaded** | 
| pos | tuple(int,int,int) | Find the nearest structure with this position as the center |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) or None | The block location of the nearest structure (x coordinate, z coordinate), the y coordinate is uncertain, if the location fails, it returns None | 

- Notes 
- Location failure is usually due to the dimension not existing, the dimension not loaded, the structure not existing in the dimension, the structure is too far from the input position, etc. 
- The return value of this interface is the coordinate of the block where the corresponding structure is located, which may be a certain distance away from the actual generated location of the structure 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateFeature(levelId) 
pos = comp.LocateStructureFeature(serverApi.GetMinecraftEnum().StructureFeatureType.Village, 0, (0, 64, 0)) 
``` 

## MayPlace 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Determine whether a block can be placed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| identifier | str | Block identifier, such as minecraft:wheat | 
| blockPos | tuple(int,int,int) | Coordinates where the block will be placed | 
| facing | int | Facing, see [Facing Enumeration](../../Enumeration Values/Facing.md) for details | 
| dimensionId | int | Dimension, default is 0 in the main world | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the block can be placed | 

- Example 

```python 
import mod.server.extraServerApi as serverApi

comp = serverApi.GetEngineCompFactory().CreateBlockInfo(levelId) 
pos = (-1, 4, 34) 
canPlace = comp.MayPlace("minecraft:wheat", pos, serverApi.GetMinecraftEnum().Facing.Up, 0) 
``` 

## MayPlaceOn 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemCompServer.ItemCompServer 

- Description 

Determines whether an item can be placed in a specified location 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| identifier | str | Item identifier, such as minecraft:dye | 
| auxValue | int | Item's additional value | 
| blockPos | tuple(int,int,int) | Position coordinates | 
| facing | int | Direction, see [Facing Enumeration](../../Enumeration Values/Facing.md) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether it can be placed | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItem(playerId) 
comp.MayPlaceOn("minecraft:dye", 3, (1,2,3), serverApi.GetMinecraftEnum().Facing.Up) 
``` 

## MirrorDimension 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.dimensionCompServer.DimensionCompServer 

- Description 


Copy terrain of different dimensions 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| fromId | int | Original dimensionId | 
| toId | int | Target dimensionId | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Only the block information of the source dimension that has been generated is copied to the new dimension. For the source dimension blocks that have not been generated, the generation logic cannot be completely copied, and some of the new dimension's own information may be used. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateDimension(levelId) 
comp.MirrorDimension(0, 1) 
``` 

## PlaceStructure 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Place structure 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | None | This parameter is deprecated | 
| pos | tuple(float,float,float) | Position to place the structure | 
| structureName | str | Structure name | 
| dimensionId | int | The dimension where you want to place the structure. You can place the structure in the constant loading block of the corresponding dimension. The default value is -1. | 
| rotation | int | The rotation angle of the placed structure. The default value is 0 (it can only be rotated 90, 180, and 270 degrees) | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the placement is successful, True means the placement is successful, False means the placement fails | 

- Notes 
- When placing, you need to ensure that all the blocks to be placed have been loaded, otherwise the placement will fail or be partially missing 
- This interface is executed synchronously. Do not place a large number of structures in one frame, which will cause the game to freeze 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.PlaceStructure(None, (100, 70, 100), "test:structureName", 0, 0) 
``` 

## SetAddArea 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.chunkSourceComp.ChunkSourceCompServer 

- Description 

Set the constant loading of chunks 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| key | str | Name of the constant loading area | 
| dimensionId | int | Dimension where the chunk is located | 
| minPos | tuple(int,int,int) | Minimum coordinates of the loading area | 
| maxPos | tuple(int,int,int) | Maximum coordinates of the loading area | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The key must be unique. If the key already exists when adding an area, the addition will fail. 
- The constantly loading area created in this way will not tick, that is, entities, block entities, and random ticks will not be updated. If the area needs to be ticked, please use the original [tickingarea command](https://minecraft-zh.gamepedia.com/%E5%91%BD%E4%BB%A4/tickingarea). 
- When setting the currently unloaded chunk as a constantly loading chunk, creatures will not be loaded from the archive. However, if it is a currently loaded chunk, the entities in the chunk will remain loaded after the player leaves the chunk. 
- In the constantly loading chunk, you can use the api to create entities, place blocks, place structures, and modify block entity data. 
- Due to the characteristics of the chunk loading algorithm, there is no guarantee that the chunks from the minimum to the maximum coordinates are fully loaded and available (i.e. the CheckChunkState interface returns True). It is recommended to set the area extending 80 grids around the operation position to be always loaded. For example, if you need to spawn creatures/place blocks at (0,5,0), you need to set the area from (-80,0,-80) to (80,0,80) to be always loaded. 
- When the chunks added through this interface are not ticked, the fill command cannot be used to fill the chunks.


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateChunkSource(levelId) 
comp.SetAddArea('Area0', 0, (0,0,0), (60,0,60)) 
``` 

## SetMergeSpawnItemRadius 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Sets whether newly generated items are merged 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| radius | int | The radius of the stack detection can be set from 0 to 5, and the initial value is 0. If it is 0, it means no stacking. If it is greater than 0, when an item is generated in the map, it will detect whether there is the same item within this radius. If there is and the stacking limit has not been reached, no new item will be generated, but the number of the item on the map will be increased. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | success True means the setting is successful, False means the setting fails | 

- Remarks 
- This interface is mainly used to optimize the scene where a large number of dropped items are generated at one time. After using this method, the generated result is a pile of items. Multiple items will not be generated first and then stacked. The number of dropped item entities can be greatly reduced and the performance can be greatly improved. 
- This interface will not affect the stack detection logic of each frame of the game itself, and the discarded items in the hand are not affected by the above stacking logic. 

- Example

```python
import mod.server.extraServerApi as serverApi
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId)
gameComp.SetMergeSpawnItemRadius(5)
```



## SetSpawnDimensionAndPosition

<span style="display:inline;color:#ff5555">Server</span>


method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Set the world spawn point dimension and coordinates 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimensionId | int or None | Dimension id | 
| pos | tuple(int,int,int) or None | Birth point coordinates | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Notes 
- When setting dimensionId and pos at the same time, the spawn point is set to the corresponding coordinates of the corresponding dimension. 
When only dimensionId is set and pos is None, the spawn point is set to the corresponding dimension, and the coordinates will be determined by [Bedrock Edition world generation search](https://minecraft.fandom.com/zh/wiki/%E7%94%9F%E6%88%90#.E5.9F.BA.E5.B2.A9.E7.89.88.E4.B8.96.E7.95.8C.E7.94.9F.E6.88.90.E6.90.9C.E7.B4.A2). 
When only pos is set and dimensionId is None, the spawn point is set to the corresponding coordinates of the current spawn dimension, which is the same as the setworldspawn command. 
- Set the y axis of pos to 65535, indicating that the spawn is on the highest solid block of the xz coordinate axis. 
- When the spawn dimension type is the Nether and the End, it will not search for a safe location to spawn like the main world. 
- For the rules of world spawn and personal spawn, please see [Player Generation](https://minecraft.fandom.com/zh/wiki/%E7%94%9F%E6%88%90#.E7.8E.A9.E5.AE.B6.E7.9A.84.E7.94.9F.E6.88.90) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
# Set the world spawn point to a coordinate in the dm3 dimension 
gameComp.SetSpawnDimensionAndPosition(3, (0, 60, 0)) 
``` 

## UpgradeMapDimensionVersion 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Increase the version number of the specified map dimension. If the version number does not match the dimension, the map archive information will be discarded. After use, the archived map version will be upgraded to the latest version. If you want to use this interface to clean up the map archive of the specified dimension, you need to call it when the blocks of the dimension are not loaded. 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension numeric ID, 0 represents the main world | 
| version | int | Dimension map version number, the value range is 1-999 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | success True means successful setting, False means failed setting | 

- Remarks 
- For local games, since the engine is loaded earlier than the mod, it is possible that the chunk loading is earlier than the mod loading. At this time, using this interface to upgrade the current dimension during initialization will fail. It is recommended to move the player out of the dimension that needs to be upgraded in the local game first, and then upgrade the dimension after the chunk is unloaded (CheckChunkState can be used to determine the position before the player leaves). 
- For network games, since the server always loads the mod before the player logs in, you can call this interface to upgrade the specified dimension when the mod is initialized. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
success = gameComp.UpgradeMapDimensionVersion(0, 10) 
``` 

