--- 
sidebarDepth: 1 
--- 
# Permissions 

## GetPlayerAbilities 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get player specific permissions 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Specific permissions, see notes | 

- Notes 
- Specific permission description 
| Permission field | Data type | Description | 
| --------| ---- |------| 
| build | bool | Place blocks | 
| mine | bool | Collect blocks | 
| doorsandswitches | bool | Use doors and switches | 
| opencontainers | bool | Open containers | 
| attackplayers | bool | Attack players | 
| attackmobs | bool | Attack mobs | 
| op | bool | Operator commands | 
| teleport | bool | Use teleport | 
- Return value example 
```python 
{'teleport': True, 'opencontainers': True, 'mine': True, 'build': True, 'op': True, 'attackmobs': True, 'doorsandswitches': True, 'attackplayers': True} 
``` 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
operation = comp.GetPlayerAbilities() 
``` 




## GetPlayerOperation 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get player permission type information 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Permission type, Visitor is 0, Member is 1, Operator is 2, Custom is 3 | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
operation = comp.GetPlayerOperation() 
``` 

