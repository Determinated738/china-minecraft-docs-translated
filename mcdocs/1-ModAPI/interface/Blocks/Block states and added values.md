--- 
sidebarDepth: 1 
--- 
# Block state and additional value 

## GetBlockAuxValueFromStates 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockStateCompServer.BlockStateComponentServer 

- Description 

Get the block additional value AuxValue according to the block name and <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State">Block State</a> 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block name | 
| states | dict | Block state | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Block additional value AuxValue, -1 in case of exception | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockState(levelId) 
states = comp.GetBlockAuxValueFromStates("minecraft:hopper", {"facing_direction": 0, "toggle_bit": 0}) 
``` 

## GetBlockStates 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockStateCompServer.BlockStateComponentServer 

- Description 

Get <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block Status">Block Status</a> 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Block position | 
| dimensionId | int | Block dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Block status, None in case of exception | 

- Notes 
- Only the block status in the loaded chunks can be obtained, and the block status in the normally loaded chunks of the corresponding dimension can be obtained 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockState(levelId) 
comp.GetBlockStates((4,4,3), 0) 
``` 
## GetBlockStatesFromAuxValue 
<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockStateCompServer.BlockStateComponentServer 

- Description 

Get <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State">Block State</a> according to the block name and block additional value AuxValue 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block name | 
| auxValue | int | Block additional value AuxValue | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Block status, None in case of exception | 

- Example 

```python

import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockState(levelId) 
states = comp.GetBlockStatesFromAuxValue('minecraft:sapling', 9) 
``` 

## SetBlockStates 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockStateCompServer.BlockStateComponentServer 

- Description 

Sets <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State">Block State</a> 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Block position | 
| data | dict | Block state | 
| dimensionId | int | Block dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Only block states in loaded chunks can be set. Block states in frequently loaded chunks of the corresponding dimension can be set. 

- Example 

```python 
# Set white wool to orange wool 
pos = (4,4,3) 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockState(levelId) 
state = comp.GetBlockStates(pos, 0) # state = { 'color': 'white' }
state['color'] = 'orange'
comp.SetBlockStates(pos, state, 0)
```