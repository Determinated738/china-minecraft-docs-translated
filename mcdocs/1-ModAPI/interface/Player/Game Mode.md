--- 
sidebarDepth: 1 
--- 
# Game Mode 

## GetPlayerGameType 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get the game mode of the specified player 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| playerId | str | Player id | 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| int | [GameType Enumeration](../../Enumeration Value/GameType.md) | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
gameType = comp.GetPlayerGameType(playerId) 
``` 

## SetPlayerGameType 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set the player's personal game mode 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| gameType | int | GetMinecraftEnum().GameType.*: Survival, Creative, Adventure are 0~2 respectively | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.SetPlayerGameType(serverApi.GetMinecraftEnum().GameType.Survival) 
``` 

