--- 
sidebarDepth: 1 
--- 
# Official partner 

## Disable 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.petCompServer.PetComponentServer 

- Description 

Disable the official partner function. Single-player games and local online games do not support this interface 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Disable result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePet(levelId) 
comp.Disable() 
``` 

## Enable 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.petCompServer.PetComponentServer 

- Description 

Enable the official partner function. Single-player games and local online games do not support this interface 

- Parameters 

None 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Enable result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePet(levelId) 
comp.Enable() 
``` 

