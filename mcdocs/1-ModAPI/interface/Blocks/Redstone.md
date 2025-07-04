--- 
sidebarDepth: 1 
--- 
# Redstone 

## GetBlockPoweredState 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.redStoneCompServer.RedStoneComponentServer 

- Description 

Get the power state of a block at a certain coordinate 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(float,float,float) | Block coordinate position | 
| dimensionId | int | Target dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Charging state 0: uncharged; 1: weakly charged; 2: strongly charged | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRedStone(levelId) 
comp.GetBlockPoweredState((1,1,1), 0) 
``` 

## GetStrength 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.redStoneCompServer.RedStoneComponentServer 

- Description 

Get the redstone signal strength of a certain coordinate 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Coordinate position | 
| dimensionId | int | Target dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Redstone signal strength [0, 15] | 

- Notes 
- Get the redstone signal strength in the constant loading block of the corresponding dimension 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateRedStone(levelId) 
comp.GetStrength((1,1,1), 0) 
``` 

