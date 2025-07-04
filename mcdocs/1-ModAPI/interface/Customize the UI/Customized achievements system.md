--- 
sidebarDepth: 1 
--- 
# Custom Achievement System 

## AddNodeProgress 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.achievementCompServer.AchievementCompServer 

- Description 

Increase the achievement progress of the corresponding achievement node of the corresponding player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| nodeId | str | Node ID | 
| delta | int | Increase the value of the node progress, only positive integers greater than 0 can be filled in | 
| callback | function | Request callback function. If the node's json is configured as a cloud node, this parameter must be filled in when calling this interface, otherwise it cannot be transmitted to the cloud. | 
| getExtra | function | Function used to return the updated data for storage, used for cloud achievement nodes, the return value must be of str type, optional | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful. When reporting for cloud achievements, True means reporting. For specific circumstances, please refer to the parameter information of the callback function. False means no reporting | 

- Notes 
- callback needs to accept a parameter 
When the request **failed**, the parameter returns None. 
When the request **successfully**, the parameter is a dict containing return code, latest data and other information. 
- When code is 0, it means the setting is successful. 
- When code is 5, it means data conflict. At this time, the system will not store the uploaded data. When the developer handles the conflict through callback, a Bool value must be returned. When the callback return value is True, the system will automatically call getExtra again to obtain the latest extra data, and automatically store the progress and extra. If you don't want the system to call automatically again, set the callback return value to False, and the system will not store the progress again. Optional 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
def cb(data): 
if data: 
print { {}.format(data["entity"]) } 
else: 
print "Failed to get data" 
def get(): 
return extraData 
comp = serverApi.GetEngineCompFactory().CreateAchievement(levelId)

#Add the player's achievement progress: 
comp.AddNodeProgress(playerId, nodeId, delta, callback = cb, getExtra = get) 
``` 

## GetChildrenNode 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.achievementCompServer.AchievementCompServer 

- Description 

Get the list of all child nodes of the next level of the achievement node 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| nodeId | str | Node ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | The return value is whether the setting is successful. If successful, it is a list of all child nodes of the next level of the node. If failed, it is None | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAchievement(levelId) 
#Get the list of all child nodes of the next level of the achievement node: 
NodeChildren = comp.GetChildrenNode(nodeId) 
``` 

## GetNodeDetailInfo 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.achievementCompServer.AchievementCompServer 

- Description 

Get the corresponding node information of the corresponding player 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| nodeId | str | Node ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Successfully obtains all information of the corresponding node of the corresponding player, including all information in json, plus a "progress" attribute to store the progress of the player's node, and fails to obtain None | 

- Remarks 
- The information obtained by this interface is only the information configured in json. If the optional content is not matched, the interface cannot obtain the optional content information that is not matched 
- This interface cannot be called in the "AddServerPlayerEvent" and "ClientLoadAddonsFinishServerEvent" events 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAchievement(levelId) 
#Get information: 
NodeDetail = comp.GetNodeDetailInfo(playerId, nodeId) 
``` 

## SetNodeFinish 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.achievementCompServer.AchievementCompServer 

- Description 

Set the corresponding achievement node of the corresponding player to complete 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| nodeId | str | Node ID | 
| callback | function | Request callback function, if the node's json is configured as a cloud node, this parameter must be filled in when calling this interface, otherwise it cannot be transmitted to the cloud | 
| getExtra | function | Function used to return the updated data stored, used for cloud achievement nodes, the return value must be str type, optional | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the setting is successful. When reporting for cloud achievements, True means reporting. For specific situations, please refer to the parameter information of the callback function. False means no reporting. | 

- Notes 
- callback needs to accept a parameter 
When the request **failed**, the parameter returns None. 
When the request **successful**, the parameter is a dict containing information such as the return code and the latest data. 
- When code is 0, it means the setting is successful. 
- When code is 5, it means data conflict. At this time, the system will not store the uploaded data. When the developer handles the conflict through callback, a Bool value must be returned. When the callback return value is True, the system will automatically call getExtra again to obtain the latest extra data, and automatically store the progress and extra. If you don't want the system to call automatically again, set the callback value to False, the system will not store the progress again, optional 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
def cb(data): 
if data: 
print { {}.format(data["entity"]) } 
else: 
print "Failed to get data" 
def get(): 
return extraData 
comp = serverApi.GetEngineCompFactory().CreateAchievement(levelId) 
#Set the achievement to complete: 
comp.SetNodeFinish(playerId, nodeId, callback = cb, getExtra = get) 
``` 

