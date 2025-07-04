--- 
sidebarDepth: 1 
--- 
# Online lobby 

# Index 

--- 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetPlayerUid](Online lobby.md#getplayeruid) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's uid. Only online players can get it | 
| [LobbyGetStorage](Online lobby.md#lobbygetstorage) | <span style="display:inline;color:#ff5555">Server</span> | Get the stored data. Only available in the online lobby | 
| [LobbyGetStorageBySort](Online lobby.md#lobbygetstoragebysort) | <span style="display:inline;color:#ff5555">Server</span> | Sort and get the stored data. Only available in the online lobby | 
| [LobbySetStorageAndUserItem](Online lobby.md#lobbysetstorageanduseritem) | <span style="display:inline;color:#ff5555">Server</span> | Set the order to be shipped or store data. Only available in the online lobby | 
| [QueryLobbyUserItem](Online lobby.md#querylobbyuseritem) | <span style="display:inline;color:#ff5555">Server</span> | Query the orders that have not been shipped. Only available in online lobby | 

## GetPlayerUid 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.httpToWebServerCompServer.HttpToWebServerCompServer 

- Description 

Get the player's uid. Only available to online players 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Player uid | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateHttp(levelId) 
uid = comp.GetPlayerUid(playerId) 
``` 

## LobbyGetStorage


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.httpToWebServerCompServer.HttpToWebServerCompServer 

- Description 

Get the stored data. Only available in the online lobby 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callback | function | Request callback function | 
| uid | int | Player uid, if 0 is passed, it means to obtain global data | 
| keys | list(str) | Key list for querying data, both sorted keys and non-sorted keys can be obtained | 

- Return value 

None 

- Remarks 
- You can use uid as 0 and key as op_config to obtain the json configured in the operation management configuration of the developer platform 
- callback needs to accept a parameter 
When the request fails, the parameter returns None, when the request succeeds, the parameter is a dict, the format is as follows. (If the key obtained has not been set, it will not appear in the latest data returned) 
```python 
{ 
"entity": { 
"data": [ 
{ 
"key": str, # data key 
"value": int/float/str # data value 
}, 
... 
] 
} 
} 
``` 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateHttp(levelId) 
def cb(data): 
if data: 
print { i["key"]: i["value"] for i in data["entity"]["data"] } 
else: 
print "Failed to obtain data" 
keys = ["money"]

comp.LobbyGetStorage(cb, uid, keys) 
``` 

## LobbyGetStorageBySort 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.httpToWebServerCompServer.HttpToWebServerCompServer 

- Description 

Sort and get the stored data. Only available in the online lobby 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callback | function | Request callback function | 
| key | str | The key of the query data. Only the sortable keys configured on the developer platform can be queried | 
| ascend | bool | ascending order | 
| offset | int | from which data after sorting to return (starting from 0) | 
| length | int | how many data to return, the upper limit is 50 | 

- Return value 

None 

- Remarks 
- Global data (i.e. uid is 0) does not participate in sorting 
- The returned result is not necessarily the latest data. It is recommended to use it only for client display. To obtain the data required by business logic, please use [LobbyGetStorage](#lobbygetstorage) 
- callback needs to accept a parameter 
When the request fails, the parameter returns None. When the request succeeds, the parameter is a dict with the following format. (If the key obtained has not been set, it will not appear in the latest data returned) 
```python 
{ 
"entity": { 
"data": [ 
{ 
"uid": int, # player uid 
"nickname": str # player username 
"value": int/float/str, # data value 
}, 
... 
] 
} 
} 
``` 

- Example


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateHttp(levelId) 
def cb(data): 
if data: 
print data["entity"]["data"] 
else: 
print "Failed to get data" 
# Get the data of money from 1st to 50th in descending order 
comp.LobbyGetStorageBySort(cb, 'money', False, 0, 50) 
# Get the data of money from 51st to 100th in descending order 
comp.LobbyGetStorageBySort(cb, 'money', False, 50, 50) 
``` 

## LobbySetStorageAndUserItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.httpToWebServerCompServer.HttpToWebServerCompServer 

- Description 

Set the order to be shipped or save the data. Only available in the online lobby 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callback | function | Request callback function | 
| uid | int | Player uid, if 0 is passed, it means setting global data | 
| orderId | int or None | Order ID, optional | 
| entitiesGetter | function or None | Function used to return stored data, optional | 

- Return value 

None 

- Remarks 
- uid is 0, key is the json configured in the operation management configuration of the developer platform corresponding to op_config, please avoid overwriting it when using this interface 
- callback needs to accept a parameter 
When the request **failed**, the parameter returns None. 
When the request **successfully**, the parameter is a dict containing information such as the return code and the latest data. 
- When the code is 0, it indicates that the setting is successful. 
- When the code is 2, it indicates data conflicts, such as multiple rooms setting the data of the same player or global data at the same time. 
- When the code is 5, it indicates order conflicts, such as the order has been marked as shipped. 

When the request is successful, no matter what the return code is, the local data should be updated with the latest data returned.

When data conflicts, entitiesGetter will be automatically called again to obtain data and retry after the callback ends. 
When orders conflict, there will be no retry after the callback ends. 
(When a conflict occurs, if the set key has not been set before, it will not appear in the latest data returned)) 
The specific format is as follows: 
```python 
{ 
"code": int, # Return code 
"message": str # Return information 
"entity": { 
"data": [ # Latest value of the database 
{ 
"key": str, # Data key 
"value": object # Data value 
}, 
... 
] 
} 
} 
``` 
- entitiesGetter needs to return a list (dict) in the following format: 
```python 
[ 
{ 
"key": str, # Data key, maximum length is 64 characters 
# UID is 0, key is the json configured in the operation and management configuration of the developer platform corresponding to op_config, please be careful to avoid overwriting 
"value": object # Data value 
# 1. If it is a sorted key, value can only be int or long, ranging from -2^63 to 2^63-1 
# 2. If it is a non-sorted key, value needs to be an object that can be serialized by json, such as int/float/str/list/dict, etc. 
# After the object is serialized into a json string, the maximum cannot exceed 1024*1024 characters 
# Chinese strings need to be utf8 encoded, do not use unicode 
# Please pay attention to the difference between json and dict, for example, the key of json must be a string, json does not have tuple, etc. 
}, 
... 
] 
``` 
- **This interface has a call frequency limit. The request frequency of all online lobby rooms of the same component is up to 50 times per second. If the request exceeds this frequency, it will cause blocking and the response time of the request will be longer. ** 
- LobbyGetStorage and LobbySetStorageAndUserItem calls with the same uid will be guaranteed to be executed in sequence 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateHttp(levelId) 
playerId = "12345" 
orderId = 12345 
money = { playerId: 100 } 
def cb(data): 
if data: 
# Update local data 
newData = { i["key"]: i["value"] for i in data["entity"]["data"] }

money[playerId] = newData["money"] 
else: 
print "Shipping/data setting failed" 
def getter(): 
return [ 
{ 
"key": "money", 
value": money[playerId] + 100 
} 
] 
comp.LobbySetStorageAndUserItem(cb, uid, orderId, getter) 
``` 

## QueryLobbyUserItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.httpToWebServerCompServer.HttpToWebServerCompServer 

- Description 

Query orders that have not been shipped. Only available in the online lobby 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| callback | function | request callback function | 
| uid | int | player uid | 

- return value 

none 

- notes 
- callback needs to accept a parameter 
When the request fails, the parameter returns None, when the request succeeds, the parameter is a dict, the format is: 
```python 
{ 
"entity": { 
"orders": [ 
{ 
"order_id": int, # order id 
"timestamp": int, # purchase time 
"cmd": str # implementation command 
"product_count": int # purchase quantity. Currently, multiple purchases are not allowed at a time, so the return is 1 
}, 
...

] 
} 
} 
``` 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateHttp(levelId) 
def cb(data): 
if data: 
print data["entity"]["orders"] 
else: 
print "Query order failed" 
comp.QueryLobbyUserItem(cb, uid) 
``` 

