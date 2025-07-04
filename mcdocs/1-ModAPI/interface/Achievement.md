--- 
sidebarDepth: 1 
--- 
# Achievements 

# Index 

--- 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [LobbyGetAchievementStorage](Achievements.md#lobbygetachievementstorage) | <span style="display:inline;color:#ff5555">Server</span> | Get the storage data of the achievement node. Only available in online lobbies | 
| [LobbySetAchievementStorage](Achievements.md#lobbysetachievementstorage) | <span style="display:inline;color:#ff5555">Server</span> | Add the progress of the achievement node. Only available in online lobby | 

## LobbyGetAchievementStorage 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.achievementCompServer.AchievementCompServer 

- Description 

Get the storage data of the achievement node. Only available in online lobby 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callback | function | Request callback function | 
| playerId | int | Player playerId | 

- Return value 

None 

- Notes 
- callback needs to accept a parameter, 
When the request **failed**, the parameter returns None. 
When the request is **successful**, the parameter is a dict, including the return code, the latest data and other information. 
- When the code is 0, it means the setting is successful. 
- When the code is 5, it means the data conflict. 
The callback parameters are as follows 
```python 
{ 
"code": 0, 
"message": "Normal return", 
"details": "", 
"entity": [ 
{ 
"achievement_id": "Node2",

"completed_at": 1652950659, 
"extra": "", 
"max_progress": 10, 
"progress": 10, 
"version": 4 
} 
] 
} 
``` 
- "completed_at" can be used to determine whether the achievement is completed. Non-zero indicates completion. Do not use "max_progress" to compare with "progress" to determine whether it is completed. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAchievement(levelId) 
def cb(data): 
if data: 
print { {}.format(data["entity"]) } 
else: 
print "Failed to obtain data" 
comp.LobbyGetAchievementStorage(cb, playerId) 
``` 

## LobbySetAchievementStorage 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.achievementCompServer.AchievementCompServer 

- Description 

Add the progress of the achievement node. Only available in the online lobby 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callback | function | Request callback function | 
| playerId | int | Player playerId | 
| nodeId | str | Achievement node ID | 
| delta | int | Set progress value | 
| getExtraData | function | Function used to return the updated data stored, the return value must be str type, optional | 

- Return value 

None 


- Notes 
- callback needs to accept a parameter. 
When the request **failed**, the parameter returns None. 
When the request **succeeded**, the parameter is a dict, which contains the return code and the data information before setting the progress. 
- When code is 0, it means the setting is successful. 
- When code is 5, it means data conflict. At this time, the system will not store the uploaded data. When the developer handles the conflict through callback, a Bool value must be returned. When the callback return value is True, the system will automatically call getExtra again to obtain the latest extra data, and automatically store the progress and extra. If you don't want the system to call it automatically again, set the callback return value to False, and the system will not store the progress again. 
The callback parameters are as follows 
```python 
{ 
"code": 5, 
"message": "Operation conflict", 
"details": "", 
"entity": { 
"completed_at": 0, 
"extra": "", 
"progress": 1, 
"version": 1 
} 
} 
``` 
- You can use "completed_at" to determine whether the achievement is completed. Non-zero means completed. Do not use "max_progress" to compare with "progress" to determine whether it is completed. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAchievement(levelId) 
def cb(data): 
if data: 
print { {}.format(data["entity"]) } 
else: 
print "Failed to obtain data" 
comp.LobbySetAchievementStorage(cb, playerId, nodeId, delta) 
``` 

