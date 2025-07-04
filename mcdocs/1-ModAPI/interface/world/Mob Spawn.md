--- 
sidebarDepth: 1 
--- 
# Mob Spawning 

## GetEntityLimit 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.extraServerApi 

- Description 

Get the maximum number of entities that can be spawned in the world. For the meaning of spawnable entities, see [SetEntityLimit](#setentitylimit) 

- Parameters 

None 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| int | Maximum number of spawnable entities | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
print serverApi.GetEntityLimit() 
``` 

## SetEntityLimit 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.extraServerApi 

- Description 

Set the maximum number of spawnable entities in the world. Spawnable entities refer to entities with spawnrules. When the number of spawnable entities currently loaded in the world exceeds this limit, mobs will no longer be spawned through spawnrules.

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| num | int | Maximum number of entities that can be generated | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Notes 
- This upper limit works together with the population density configured in the organism json file. For example, if the upper limit is 200, but the population density is 10, then the organism will not generate more than 10 randomly. In addition, the upper limit of the organism is also related to the block capacity suitable for generation. If the upper limit is set too high, it may not be reached due to other restrictions. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
print serverApi.SetEntityLimit(300) 
``` 

## SpawnCustomModule 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.mobSpawnCompServer.MobSpawnComponentServer 

- Description 

Set custom spawning 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| biomeType | int | [BiomeType enumeration](../../enumeration value/BiomeType.md) | 
| change | int | [Change enumeration](../../enumeration value/Change.md) | 
| entityType | int | [EntityType enumeration](../../enumeration value/EntityType.md) | 
| probability | int | Spawn weight [1, 10] | 
| minCount | int | Minimum number of spawns [0, 10] | 
| maxCount | int | Maximum number of spawns [0, 10] | 
| environment | int | 1: Spawn on the surface; 2: Spawn in water | 
| minBrightness | int | Minimum light level when spawning this creature [1, 15], use the default value if not set | 
| maxBrightness | int | Maximum light level when spawning this creature [1, 15], use the default value if not set | 
| minHeight | int | Minimum altitude when spawning this creature [0, 256], use the default value if not set | 
| maxHeight | int | Maximum altitude when spawning this creature [0, 256], use the default value if not set | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 


- Example

```python
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateMobSpawn(levelId)
comp.SpawnCustomModule(BiomeType.river,Change.Add,EntityType.Dolphin,10,1,10,2)
```