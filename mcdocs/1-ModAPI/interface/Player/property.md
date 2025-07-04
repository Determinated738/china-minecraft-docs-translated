--- 
sidebarDepth: 1 
--- 
# Properties 

## AddPlayerExperience 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.expCompServer.ExpComponentServer 

- Description 

Add player experience 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| exp | int | Player experience, can be set to negative | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- If the set exp value is a negative number and exceeds the existing experience value of the current level, after calling the interface, the player's level will not decrease but the experience value will be set to the minimum value 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExp(entityId) 
comp.AddPlayerExperience(25) 
``` 

## AddPlayerLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.levelCompServer.LevelComponentServer 

- Description 

Modify the player level 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| level | int | Player level, can be set to a negative number | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateLv(playerId) 
comp.AddPlayerLevel(2) 
``` 

## CollectOnlineClientData 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Collects online player client data to determine whether the player is cheating 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| collectTypes | list(str) | Data type, different types collect different data, see the notes for specific instructions. | 
| callback | function | Callback function, used to analyze data and determine whether the player is cheating, contains two parameters, the first parameter is playerId, type str; the second parameter represents the collected data, dict type, the content is determined by collectTypes, see the notes for details, if data collection fails, it is None (for example, the player is not online) | 
| extraArgs | dict | The default is None, different parameters are passed in according to collectTypes, see the notes for specific instructions. | 

- Return value 

None 

- Remarks 
- The types in collectTypes are explained as follows 
The data dictionary collected by the game type is explained as follows: 
| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| gameType | int | Game mode, meaning: -1: Failed to obtain, 0: Survival mode, 1: Creative mode, 2: Adventure mode, 3: Spectator mode|

| levelGravity | float | World gravity factor| 

The data dictionary collected by player type is explained as follows: 
| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| playerHealth | int | Player health value| 

The data dictionary collected by world type is explained as follows: 
| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| blockName | str | The name of a block at a certain position. The extraArgs parameter is required to include the pos parameter| 
| blockAuxValue | int | The additional value AuxValue of a block at a certain position. The extraArgs parameter dictionary is required to include "pos". If it is missing, there is no data| 

The data dictionary collected by entity type is explained as follows: 
| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| entityPos | tuple(float,float,float) | Entity position, see the GetPos interface description on the client side, extraArgs parameter dictionary must contain "entityId", if missing, no data | 
| entityGravity | float | Get the gravity factor of the entity, when the gravity factor of the creature is 0, the gravity factor of the world is applied, extraArgs parameter dictionary must contain "entityId", if missing, no data | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
def ProcessData(playerId, data): 
#Normal return example: ProcessData 123 {'blockAuxValue': 0, 'blockName': 'minecraft:air', 'blockBoxSize': (-1.0, -1.0), 'gameType': 1, 'entityPos': (123,456,789), 'levelGravity': -0.08, 'playerHealth': 20, 'entityGravity': 0.0} 
#Failed return example: ProcessData 123 None 
print minecraft'ProcessData', playerId, data 
comp.CollectOnlineClientData(['player', 'world', 'entity', 'game'], ProcessData, {'entityId' :'123', 'pos' : (123,456,789))}) 
``` 

## GetPlayerExp 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.expCompServer.ExpComponentServer 

- Description 

Get the player's experience value at the current level 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isPercent | bool | Is it a percentage? | 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Player experience value | 

- Notes 
- If the return percentage is set to False, the absolute value of the player's experience at the current level (not the current player's total experience value) is returned. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExp(entityId) 
print(comp.GetPlayerExp(False)) 
``` 

## GetPlayerHealthLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get the player's health threshold. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural recovery are turned on. The default value of the original version is 18 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Health threshold, -1 means acquisition failure | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
print(comp.GetPlayerHealthLevel()) 
``` 

## GetPlayerHealthTick 


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get the player's natural recovery speed. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural recovery are turned on. The default value of the original version is 80 ticks (i.e., 1 health point is restored every 4 seconds) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Natural recovery speed, -1 means acquisition failed | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
print(comp.GetPlayerHealthTick()) 
``` 

## GetPlayerHunger 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get the player's hunger and display it on the UI hunger progress bar. The initial value is 20, that is, each chicken leg represents 2 hungers. **Saturation**: The player's current saturation, the initial value is 5, and the maximum value is always the player's current hunger. This value directly affects the player's **hunger**. <br>1) Increase method: Eat food. <br>2) Decrease method: Each time a **consumption event** is triggered, the value decreases by 1. If the value is not greater than 0, directly reduce the player's **hunger** by 1. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Player hunger | 

- Example 


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.GetPlayerHunger() 
``` 

## GetPlayerLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.levelCompServer.LevelComponentServer 

- Description 

Get the player level 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Player level | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateLv(playerId) 
comp.GetPlayerLevel() 
``` 
## GetPlayerMaxExhaustionValue 
<span style="display:inline;color:#ff5555">Server</span> 
method in mod.server.component.playerCompServer.PlayerCompServer 
- Description 
Get the zero value of the player's foodExhaustionLevel, a constant value, the default is 4. **Exhaustion** refers to the player's current exhaustion level, the initial value is 0, the value will increase with the player's series of actions (such as jumping), when the value is greater than the maximum exhaustion (maxExhaustion) after zero, and reduce the saturation (saturation) by 1 (in order to illustrate the hunger mechanism, we define this as **consumption event**) 
- Parameters 


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Zero value of player's foodExhaustionLevel | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.GetPlayerMaxExhaustionValue() 
``` 

## GetPlayerStarveLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get the player's hunger threshold. When the hunger value is less than the hunger threshold, the health will be automatically deducted. It is effective when the hunger value and hunger blood loss are turned on. The default value of the original version is 1 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Hunger threshold -1 means acquisition failed | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
print(comp.GetPlayerStarveLevel()) 
``` 

## GetPlayerStarveTick 


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Get the player's blood loss rate due to hunger. When the hunger value is less than the hunger threshold, the blood will be automatically deducted. It is effective when the hunger value and hunger blood loss are enabled. The default value of the original version is 80 ticks (i.e., 1 health point is deducted every 4 seconds) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Hunger blood loss rate, -1 means acquisition failure | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
print(comp.GetPlayerStarveTick()) 
``` 

## GetPlayerTotalExp 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.expCompServer.ExpComponentServer 

- Description 

Get the total experience value of the player 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Total experience value, a positive integer. Returns -1 if the acquisition fails. | 

- Example 


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExp(entityId) 
print(comp.GetPlayerTotalExp()) 
``` 

## IsPlayerNaturalRegen 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Whether to enable the player's natural regeneration. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural regeneration are enabled. The original version is enabled by default 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means enabled, False means disabled, None means failed to obtain | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
print(comp.IsPlayerNaturalRegen()) 
``` 

## IsPlayerNaturalStarve 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Whether to enable the player's blood loss due to hunger. When the hunger value is less than the hunger threshold, the blood volume will be automatically restored. It is effective when the hunger value and hunger blood loss are enabled. The original version is enabled by default 

- Parameters 


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means on, False means off, None means acquisition failed | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
print(comp.IsPlayerNaturalStarve()) 
``` 

## SetPlayerHealthLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set the player's health threshold. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural recovery are turned on. The default value of the original version is 18 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| healthLevel | int | Health threshold | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Note: The health threshold is always greater than or equal to the hunger threshold. If the set health threshold is less than the hunger threshold, the hunger threshold will be set to the current health threshold 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.SetPlayerHealthLevel(16) # If the hunger value is greater than or equal to 16, it will enter the natural recovery state, and the default is to restore 1 health point every 4 seconds 
```



## SetPlayerHealthTick 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set the player's natural recovery speed. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural recovery are turned on. The default value of the original version is 80 ticks (i.e., 1 health point is restored every 4 seconds) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| healthTick | int | Natural recovery speed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Note: The minimum value is 1, which means 20 health points are restored per second 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.SetPlayerHealthTick(40) # Restore 1 health point every 2 (40/20) seconds in natural recovery state 
``` 

## SetPlayerHunger 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set the player's hunger. 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| value | float | Hunger | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.SetPlayerHunger(10) 
``` 

## SetPlayerMaxExhaustionValue 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set the player's **maxExhaustion**. By adjusting the **maxExhaustion**, you can adjust the **hunger** consumption rate. When the **maxExhaustion** is very large, the hunger** may seem to never decrease. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| value | float | **maxExhaustion** | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- For example: When **maxExhaustion** is 4, the player's hunger consumption rate is twice as fast as when **maxExhaustion** is 8 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId)

comp.SetPlayerMaxExhaustionValue(10.0) 
``` 

## SetPlayerNaturalRegen 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set whether to enable natural regeneration of the player. When the hunger value is greater than or equal to the health threshold, the player will automatically recover health. This function is effective when both hunger value and natural regeneration are enabled. The original version is enabled by default 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| value | bool | True to enable, False to disable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is the setting successful? | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.SetPlayerNaturalRegen(False) # Turn off natural recovery. Even if the hunger value is greater than the health threshold, the health will not be restored. 
``` 

## SetPlayerNaturalStarve 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set whether to enable the player's hunger blood loss. When the hunger value is less than the hunger threshold, the blood will be automatically deducted. It is effective when the hunger value and hunger blood loss are enabled. The original version is enabled by default 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| value | bool | True to enable, False to disable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.SetPlayerNaturalStarve(False) # Disable hunger loss. Even if the hunger value is less than the hunger threshold, the health will not be deducted. 
``` 

## SetPlayerPrefixAndSuffixName 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.nameCompServer.NameComponentServer 

- Description 

Set the player prefix and suffix name 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| prefix | str | Prefix content | 
| prefixColor | str | Prefix content color description, you can use the GenerateColor interface to pass in parameters | 
| suffix | str | Suffix content | 
| suffixColor | str | Suffix content color description, you can use the GenerateColor interface to pass in parameters | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateName(playerId)
comp.SetPlayerPrefixAndSuffixName("red team",serverApi.GenerateColor('RED'),'human shield',serverApi.GenerateColor('RED'))

``` 

## SetPlayerStarveLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set the player's hunger threshold. When the hunger value is less than the hunger threshold, the health will be automatically deducted. It is effective when the hunger value and hunger blood loss are turned on. The default value of the original version is 1 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| starveLevel | int | Hunger threshold | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Note: The health threshold is always greater than or equal to the hunger threshold. If the set hunger threshold is greater than the health threshold, it will be set to the current health threshold 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.SetPlayerStarveLevel(2) # If the hunger value is less than or equal to 2, the player will enter the starvation and blood loss state. By default, 1 health point will be lost every 4 seconds 
``` 

## SetPlayerStarveTick 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Set the player's hunger blood loss speed. When the hunger value is less than the hunger threshold, the blood will be automatically deducted. It is effective when the hunger value and hunger blood loss are turned on. The default value of the original version is 80 ticks (i.e., 1 health point is deducted every 4 seconds) 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| starveTick | int | Hunger blood loss speed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Note: The minimum value is 1, which means 20 health points are deducted per second 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.SetPlayerStarveTick(40) # Deduct 1 health point every 2 (40/20) seconds when hungry blood loss 
``` 

## SetPlayerTotalExp 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.expCompServer.ExpComponentServer 

- Description 

Set the total experience value of the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| exp | int | Total experience value, positive integer | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- The level will be recalculated according to the total experience value. This interface can cause changes in the level 
- Internal calculations use floating point numbers, and errors will occur when the value is large 


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExp(entityId) 
comp.SetPlayerTotalExp(25) 
``` 

## Swing 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

The local player plays the original attack action 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayer(clientApi.GetLevelId()) 
comp.Swing() 
``` 
## getUid 
<span style="display:inline;color:#7575f9">Client</span> 
method in mod.client.component.playerCompClient.PlayerCompClient 
- Description 
Get the local player's uid 


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| long or None | Player uid | 

- Notes 
- The uid obtained when it is not a client thread or has not been logged in is None. The value obtained by calling this interface on the current machine is a fixed value and does not depend on the created player 
- The getUid interface cannot be used during the mod loading process. It is recommended that developers use it after the OnLocalPlayerStopLoading event is triggered 

- Example 

```python 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
uid = comp.getUid() 
``` 

