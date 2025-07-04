--- 
sidebarDepth: 1 
--- 
# Experience Orb 

## GetOrbExperience 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.expCompServer.ExpComponentServer 

- Description 

Get the experience of the experience orb 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Experience value, a positive integer. Returns -1 if the acquisition fails. | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExp(entityId) 
print(comp.GetOrbExperience()) 
``` 

## SetOrbExperience 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.expCompServer.ExpComponentServer 

- Description 

Set the experience ball experience 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| exp | int | Experience ball experience |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Set the experience of the experience ball. entityId is the entityId of the experience ball. If the experience is less than or equal to 0, no experience will be added after picking it up. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExp(entityId) 
comp.SetOrbExperience(25) 
``` 

