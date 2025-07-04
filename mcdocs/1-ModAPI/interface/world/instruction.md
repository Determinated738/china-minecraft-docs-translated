--- 
sidebarDepth: 1 
--- 
# Commands 

## GetCommandPermissionLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.commandCompServer.CommandCompServer 

- Description 

Returns the permission level of OP when using the /op command (corresponding to the op-permission-level configuration in server.properties) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Permission level: 1-OP can bypass respawn protection; 2-OP can use all single-player cheat commands; 3-OP can use most multiplayer game-specific commands; 4-OP can use all commands | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateCommand(levelId) 
opLevel = comp.GetCommandPermissionLevel() 
print "GetCommandPermissionLevel oplevel={}".format(opLevel) 
``` 

## GetDefaultPlayerPermissionLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.commandCompServer.CommandCompServer 

- Description 

Returns the permission identity of the new player when joining (corresponding to the default-player-permission-level configuration in server.properties) 

- Parameters 

None 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Permission identity: 0-Visitor; 1-Member; 2-Operator; 3-Custom | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateCommand(levelId) 
opLevel = comp.GetDefaultPlayerPermissionLevel() 
print "GetDefaultPlayerPermissionLevel oplevel={}".format(opLevel) 
``` 

## SetCommand 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.commandCompServer.CommandCompServer 

- Description 

Use in-game commands 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| cmdStr | str | Command | 
| playerId | str | Player id: optional, if playerId is not set, randomly select a player | 
| showOutput | bool | Whether to output to the chat window: optional, default False, if True, when the command is correct, the return information will be output just like the native command entered in the chat box. OnCommandOutputServerEvent and OnCommandOutputClientEvent will be triggered only when this parameter is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the command is executed successfully | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateCommand(levelId) 
comp.SetCommand("/tp @p 100 5 100")#Transmit command 
``` 




## SetCommandPermissionLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.commandCompServer.CommandCompServer 

- Description 

Set the OP's permission level when the player uses the /op command (corresponding to the op-permission-level configuration in server.properties) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| opLevel | int | Permission level: 1-OP can bypass respawn protection; 2-OP can use all single-player cheat commands; 3-OP can use most multiplayer game-specific commands; 4-OP can use all commands | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the command is executed successfully | 

- Notes 
- This API will not modify the permission level of players who have already obtained the op. It only affects players who obtain the op after calling the API. It is recommended to call this API when the game is initialized. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateCommand(levelId) 
opLevel = 4 
suc = comp.SetCommandPermissionLevel(opLevel) 
print "SetCommandPermissionLevel to {} suc={}".format(opLevel, suc) 
``` 

## SetDefaultPlayerPermissionLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.commandCompServer.CommandCompServer 

- Description 

Set the permissions for new players when they join (corresponding to the default-player-permission-level configuration in server.properties) 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| opLevel | int | Permission identity: 0-Visitor; 1-Member; 2-Operator; 3-Custom | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the command is executed successfully | 

- Notes 
- This API will not modify the permissions of players who have already joined the game. It only affects new players who join after calling the API. It is recommended to call this API when the game is initialized 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateCommand(levelId) 
opLevel = 1 
suc = comp.SetDefaultPlayerPermissionLevel(opLevel)
print "SetDefaultPlayerPermissionLevel to {} suc={}".format(opLevel, suc)
```