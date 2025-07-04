--- 
sidebarDepth: 1 
--- 

# <span id="4-Control Server API"></span>4-Control Server API 

Here are some basic API interfaces of Master. 

<span id="Configuration"></span> 
### Configuration 

<span id="GetCommonConfig"></span> 
#### GetCommonConfig 

- Description 

Get the server common configuration, including the configuration of all servers and db, see the notes for details 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| dict | Configuration content | 
- Notes 

The example of server common configuration is as follows, only the core configuration information is shown: 
``` 
{ 
"apolloid":111, 
"extra_redis":{ 
}, 
"game_id":0, 
"game_key":"game_key", 
"gas_server_url":"http://127.0.0.1:111", 
"log_debug_level":true, 
"master":{ 
    "app_type":"master",
    "app_version":"1.21.0.release20210401",
    "gb":8,
    "ip":"127.0.0.1",
    "keep_alive_period":30,
    "master_port":0,
    "mods":"",
    "port":8000,
    "serverid":0,
    "type":"master"
    },
    "mongo":null,
    "mysql":{
    "database":"test_db",

    "host":"127.0.0.1",
    "password":"test_password",
    "port":3306,
    "user":"test_user"
    },
    "redis":{
    "host":"127.0.0.1",
    "password":"",
    "port":6379
    },
    "review_stage":0,
    "serverlist":[
    {
    "app_type":"proxy",
    "app_version":"1.21.0.release20210401",
    "gb":8,
    "ip":"127.0.0.1",
    "log_debug_level":false,
    "master_port":11003,
    "max_players":0,
    "mods":"",
    "optimum_players":0,
    "port":11002,    "save":false,
    "serverid":2000,
    "type":"proxy"
    },
    {
    "app_type":"lobby",
    "app_version":"1.21.0.release20210401",
    "gb":8,
    "ip":"127.0.0.1",
    "log_debug_level":false,
    "master_port":13003,
    "max_players":200,
    "mods":"neteaseRound",
    "optimum_players":0,
    "port":13002,
    "save":false,
    "serverid":4000,
    "type":"lobby"
    }
    ],
    "servicelist":[
    ],
    }
    ```
    
    
- Example


```python 
import master.netgameApi as netMasterApi 
conf = netMasterApi.GetCommonConfig() 
serverlist = conf['serverlist'] #Get serverlist configuration 
bDebugLevel = conf['log_debug_level'] #Get log level configuration 
``` 
<span id="GetGameTypeByServerId"></span> 
#### GetGameTypeByServerId 

- Description 

Get the type of the server with the specified ID 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Server ID | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| None or str | The type of the server with the specified ID. If there is no server that meets the conditions, None is returned | 
- Example 

```python 
import master.netgameApi as netMasterApi 
gameType = netMasterApi.GetGameTypeByServerId(6000) 
``` 
<span id="GetServerIdsByGameType"></span> 
#### GetServerIdsByGameType 

- Description 

Get a list of server ids of a specified type 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| gameType | str | Server type name | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| list(int) | A list of server IDs of a specified type. If no server meets the criteria, an empty list is returned | 
- Example 

```python

import master.netgameApi as netMasterApi 
idList = netMasterApi.GetServerIdsByGameType("gameA") 
``` 
<span id="GetServerLoadedModsById"></span> 
#### GetServerLoadedModsById 

- Description 

Get the server loaded mod list according to the server id 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Server id, id 0 means master | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| list(str) | Server mod list | 
- Example 

```python 
import master.netgameApi as netMasterApi 
#An example returned: ["neteaseAnnounce", "neteaseAuth", "neteaseShop"] 
mods = netMasterApi.GetServerLoadedModsById(4000) 
``` 
<span id="GetServerLoadedModsByType"></span> 
#### GetServerLoadedModsByType 

- Description 

Get the server loaded mod list according to the server type. If the same type of server is configured with different mods, return one of the corresponding mod lists. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverType | str | Server type | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| list(str) | Server mod list | 
- Example 

```python 
import master.netgameApi as netMasterApi 
#An example of return: ["neteaseAnnounce", "neteaseAuth", "neteaseShop"] 
mods = netMasterApi.GetServerLoadedModsByType("survivalGame")

``` 
<span id="IsService"></span> 
#### IsService 

- Description 

Is the server a service server? 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | server id | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | True means it is a service, False means it is not a service | 
- Notes 

This api replaces [masterConf.isService], and [masterConf.isService] is obsolete. 


- Example 

```python 
import master.netgameApi as netMasterApi 
bService = netMasterApi.IsService(10) 
``` 
<span id="player"></span> 
### player 

<span id="BanUser"></span> 
#### BanUser 

- Description 

Ban a player 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player uid | 
| banTime | int | Ban time, in seconds, -1 means permanent ban | 
| reason | str | Ban reason, encoded in utf8 | 
| bCombineReason | bool | Whether to combine and display ban reasons. If True, handle according to the notes, otherwise the banned player will be prompted with [reason] when logging in | 
- Return value 

| Data type | Description |

| :--- | :--- | 
| bool | True indicates successful setting, False indicates failure. Please delay one frame and try again after failure | 
- Notes 

The effect description is as follows: 

If banTime>0, the banned player will be prompted when logging in: Your account has been banned, the remaining ban time: x days y hours z minutes, ban reason: [reason]. If you have any questions, please go to the customer service area for feedback 

If banTime=-1, the banned player will be prompted when logging in: Your account has been permanently banned, ban reason: [reason]. If you have any questions, please go to the customer service area to give feedback 


- Example 

```python 
import master.netgameApi as netMasterApi 
#Player 123456, banned for 86400 seconds, login chain prompt: Your account has been banned, remaining ban time: 1 day 0 hours 0 minutes, ban reason: cheating was banned for one day 
netMasterApi.BanUser(123456, 86400, 'Banned for one day for cheating', True) 
#Player 123457, banned for 86400 seconds, login chain prompt: cheating was banned for one day 
netMasterApi.BanUser(123457, 86400, 'Banned for one day for cheating', False) 
``` 
<span id="GetBanUserInfo"></span> 
#### GetBanUserInfo 

- Description 

Get the ban information of the player 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player uid | 
| callback | function | Callback function, containing two parameters: the first parameter is uid; the second parameter is the ban information, if the acquisition fails, it is None, if it is not banned, it is "{}", if it is banned, it is dict, see the explanation in the remarks | 
- Return value 

None 
- Remarks 

The second dict parameter content in callback is explained as follows: 

| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| banTime | int | Ban duration, in seconds, -1 means permanent ban | 
| banTimestamp | int | Timestamp of the start of the ban, if it is not a permanent ban, the end time is: banTimestamp + banTime | 
| reason | str | ban reason | 




- Example


```python 
import master.netgameApi as netMasterApi 
def cb(uid, info): 
#If banned, return example: result 123456 {banTime: 10, banTimestamp: 1623325971, reason: "cheating"} 
#If not banned, return example: result 123456 {} 
print 'result', uid, info 
netMasterApi.GetBanUserInfo(123456, cb) 
``` 
<span id="GetOnlineUidList"></span> 
#### GetOnlineUidList 

- Description 

Get the uid list of all online players 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| list(int) | Uid list of online players. When no player is online, an empty list is returned. | 
- Notes 

The uid list of online players is cached in memory. After the Master is accidentally dumped and restarted, only the uids of players who log in after the restart can be obtained. 

The uid list returned by this interface may be very large. It is not recommended to use it in a formal environment. 


- Example 

```python 
import master.netgameApi as netMasterApi 
uidList = netMasterApi.GetOnlineUidList() 
``` 
<span id="GetProtocolVersionByUID"></span> 
#### GetProtocolVersionByUID 

- Description 

Get the client protocol version number of online players. In a multi-protocol version engine (for example, supporting both 1.14 and 1.15 clients), the client needs to be assigned to the lobby/game of the same protocol version. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player's UID | 
- Return value 

| Data type | Description | 
| :--- | :--- |

| None or int | When the player is online, returns the client protocol version number of this player, and returns None when the player is not online | 
- Example 

```python 
import master.netgameApi as netMasterApi 
protocolVersion = netMasterApi.GetProtocolVersionByUID(123456) 
``` 
<span id="GetServerIdByUid"></span> 
#### GetServerIdByUid 

- Description 

Get the ID of the server where the online player is located. The information returned is the information in the memory cache of the current control server. The player is likely to go offline or transfer servers soon. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | UID of the player to be obtained | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| None or int | When the player is online, returns the server ID of the player, and returns None when the player is not online | 
- Notes 

The mapping relationship between the player and the current server ID is cached in the memory. When the Master is accidentally dumped and restarted, only the server ID of the player who logged in after the restart can be obtained. 


- Example 

```python 
import master.netgameApi as netMasterApi 
serverId = netMasterApi.GetServerIdByUid(123456) 
``` 
<span id="GetUserSilentInfo"></span> 
#### GetUserSilentInfo 

- Description 

Get the player's mute information 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | player uid | 
| callback | function | callback function, contains two parameters: the first parameter is uid; the second parameter is the ban information, if the acquisition fails, it is None, if not banned, it is "{}", if banned, it is dict, the explanation is as follows: | 
- Return value 


None 
- Notes 

The second dict parameter in callback is explained as follows: 

| Keywords | Data Type | Description | 
| ----------| --------------------- | ---------| 
| banTime | int | Ban duration, in seconds, -1 means permanent ban | 
| banTimestamp | int | Timestamp of ban start, if not permanent ban, the end time is: banTimestamp + banTime | 
| reason | str | Ban reason | 




- Example 

```python 
import master.netgameApi as netMasterApi 
def cb(uid, info): 
#If banned, return example: result 123456 {banTime: 10, banTimestamp: 1623325971, reason: "talking about sensitive topics"} 
#If not banned, return example: result 123456 {} 
print 'result', uid, info 
netMasterApi.GetUserSilentInfo(123456, cb) 
``` 
<span id="SetLoginStratege"></span> 
#### SetLoginStratege 

- Description 

Set the player login server selection strategy, requiring the server to be set when loading the mod after startup 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| func | function | Calculate the player login server, including two parameters: the first parameter is the player uid; the second parameter is the callback function, which executes the subsequent login logic. Regardless of whether the login is successful, it must be executed. The callback function has only one parameter, which is the target server. | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | True means successful setting, False means failure. Please delay one frame and try again after failure | 
- Notes 

The example provides two methods for setting login strategies. Example 1 is for developers to understand the interface and is best not to be used in production environments. Example 2 is a method for using in production environments. 

After calling this API to modify the server selection strategy, the configured maximum number of people on a single server will become invalid. The server selection strategy needs to consider the balance between the carrying capacity of a single server and the number of players, but the configured maximum number of people on all servers will not become invalid. 


- Example 


```python 
#Example 1, do not consider rolling updates, set a fixed target server 
def loginStratege(uid, callback): 
targetId = 20000 #Login to the server with id 20000 
callback(targetId) #Must execute, perform subsequent operations after login 
import master.netgameApi as netMasterApi 
netMasterApi.SetLoginStratege(loginStratege) 
#Example 2, consider rolling updates, the server id will change during the rolling update, so a mechanism is needed to ensure the validity of the target server 
#master mod 
class testMaster(MasterSystem): 
def __init__(self,namespace,systemName): 
MasterSystem.__init__(self, namespace, systemName) 
self.mTargetServerIds = [] #Contains a list of valid target server ids 
def loginStratege(uid, callback): 
targetId = random.choice(self.mTargetServerIds) #Select a target server 
if not serverManager.IsValidServer(targetId):#Check whether the target server is valid. Because during the rolling update process, the server will slowly go offline and become invalid 
#If an invalid server is found, filter out all invalid servers and then reselect the target server 
self.mTargetServerIds = [server for server in self.mTargetServerIds if serverManager.IsValidServer(server)] 
targetId = random.choice(self.mTargetServerIds) 
callback(targetId) #Must be executed to perform subsequent login operations 
netMasterApi.SetLoginStratege(loginStratege) 
self.ListenForEvent('lobbyNameaspace', 'lobbySystem', 'NewLoginServerEvent', self, self.OnNewLoginServer) 

def OnNewLoginServer(self, args): 
# Record the valid target server 
serverId = args['serverId] 
if serverId not in self.mTargetServerIds: 
                        self.mTargetServerIds.append(serverId)
#lobby mod
class lobbyServer(ServerSystem):
        def __init__(self, namespace, systemName):
                ServerSystem.__init__(self, namespace, systemName)
                self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), 'MasterConnectStatusEvent', self,
                        self.OnMasterConnectStatus)
        def OnMasterConnectStatus(self, args):
                # After establishing a connection with the master, immediately register with the master as a valid server
                if args['isConnect']:
                        data = {'serverId' : lobbyGameApi.GetServerId()}
                        self.NotifyToMaster('NewLoginServerEvent', data)
 ```
<span id="SilentByUID"></span>
#### SilentByUID

- Description 

Mute a player 

- Parameters 

| Parameter name | Data type | Description |

| :--- | :--- | :--- | 
| uid | int/long | Player uid | 
| banTime | int | Ban time, in seconds, -1 means permanent ban | 
| reason | str | Ban reason, encoded in utf8 | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | True means successful setting, False means failure. Please delay one frame and try again after failure | 
- Example 

```python 
import master.netgameApi as netMasterApi 
#Player 123456 was banned for 86400 seconds. The reason for banning was "said sensitive content and was banned for one day" 
netMasterApi.SilentByUID(123456, 86400, 'said sensitive content and was banned for one day') 
``` 
<span id="UnBanUser"></span> 
#### UnBanUser 

- Description 

Unban a player 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player uid | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | True means setting is successful, False means failure. Please delay one frame and try again after failure | 
- Example 

```python 
import master.netgameApi as netMasterApi 
#Unban player 123456 
netMasterApi.UnBanUser(123456) 
``` 
<span id="UnSilentByUID"></span> 
#### UnSilentByUID 

- Description 

Unban a player 

- Parameters 

| Parameter name | Data type | Description |

| :--- | :--- | :--- | 
| uid | int/long | player uid | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | True means successful setting, False means failure. Please delay one frame and try again after failure | 
- Example 

```python 
import master.netgameApi as netMasterApi 
#Player 123456 is unbanned 
netMasterApi.UnSilentByUID(123456) 
``` 
Here is the Master's Http interface 

<span id="HTTP server"></span> 
### HTTP server 

<span id="RegisterMasterHttp"></span> 
#### RegisterMasterHttp 

- Description 

Register a new HTTP interface 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| url | str | Interface url | 
| binder | instance | Instance that responds to HTTP requests | 
| func | function | Instance function that responds to HTTP requests | 
- Return value 

None 
- Example 

```python 
import json 
import master.masterHttp as masterHttp 
class HttpHandler(object): 
def __init__(self): 
# Set interface URI and callback 
url = '/kick-user' 
func = self.HttpTest 
# Register 
masterHttp.RegisterMasterHttp(url, self, func) 
def HttpTest(self, clientId, requestBody): 
# clientId identifies the unique id of the request, and this parameter must be carried in SendHttpResponse

# requestBody is the post body content. If it is in json format, you can load the content in the following way. 
# import ujson as json 
# request = json.loads(requestBody) 
# Return the processing result. code must be 1 to indicate successful processing, otherwise the service request will be considered a failure. 
response = '{"code":1,"message":"ok"}' 
masterHttp.SendHttpResponse(clientId, response) 
``` 
<span id="SendHttpRequestToService"></span> 
#### SendHttpRequestToService 

- Description 

Send an http request to the service 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Service server id | 
| requestUrl | str | Request url, such as "/test-reqeust" | 
| body | str | HTTP post body, a json string | 
- Return value 

None 
- Example 

```python 
import json 
import master.masterHttp as masterHttp 
params = { 
"message":"content", 
"code":1 
} 
url = "/test-reqeust" 
masterHttp.SendHttpRequestToService(8000, url, json.dumps(params)) 
``` 
<span id="SendHttpResponse"></span> 
#### SendHttpResponse 

- Description 

Send HTTP Response, supports asynchronous return, specifies the clientId passed in the request when returning 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| clientId | int | Request unique id, identify HTTP request. | 
| message | str | Content of HTTP Response | 
- Return value


None 
- Example 

```python 
import json 
import master.masterHttp as masterHttp 
class HttpHandler(object): 
def __init__(self): 
# Set interface URI and callback 
url = '/kick-user' 
func = self.HttpTest 
# Register 
masterHttp.RegisterMasterHttp(url, self, func) 
def HttpTest(self, clientId, requestBody): 
# clientId identifies the unique id of the request, which must be carried in SendHttpResponse 
# requestBody is the post body content. If it is in json format, you can load the content in the following way. 
# import ujson as json 
# request = json.loads(requestBody) 
# return processing result 
response = '{"code":0,"message":"ok"}' 
masterHttp.SendHttpResponse(clientId, response) 
``` 
Here are some interfaces of the master about server management 

<span id="Server Management"></span> 
### Server Management 

<span id="GetAllResetingServers"></span> 
#### GetAllResetingServers 

- Description 

Get the id list of all resetting servers 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| list(int) | Server id list | 
- Example 

```python 
import master.serverManager as serverManager 
servers = serverManager.GetAllResetingServers() 
 ```
<span id="GetAllServerStatus"></span>
#### GetAllServerStatus

- describe


Get the status of all servers. Only status 2 indicates that the server is in normal service, and other status indicates that the server cannot be used. 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| dict | key: int type, server id, value: int type, server status. The server status is as follows: <br/> 1: Disconnected status <br/> 2: Connected status <br/> 3: Shutdown status <br/> 4: Graceful shutdown status <br/> 6, rolling update intermediate status, about to switch to status 7 <br/> 7 is also a rolling update intermediate status, about to switch to status 1 or 2 | 
- Notes 

In the server status, 2 indicates normal service, and others indicate that the service cannot be used normally. 


- Example 

```python 
import master.serverManager as serverManager 
statusDict = serverManager.GetAllServerStatus() 
``` 
<span id="GetAllServersOnlineNum"></span> 
#### GetAllServersOnlineNum 

- Description 

Get the number of online users of all servers 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| dict | key, int type, indicating server id, value, int type, indicating the number of online users of the server | 
- Example 

```python 
import master.serverManager as serverManager 
onlineDict = serverManager.GetAllServersOnlineNum() 
``` 
<span id="GetConnectedLobbyAndGameIds"></span> 
#### GetConnectedLobbyAndGameIds 

- Description 

Get the server id list of all connected lobby/games 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| list | Server id list, server id is int type. | 
- Example


```python 
import master.serverManager as serverManager 
idList = serverManager.GetConnectedLobbyAndGameIds() 
``` 
<span id="GetOneServerStatus"></span> 
#### GetOneServerStatus 

- Description 

Get the server status. Only status 2 indicates that the server is in normal service, and other statuses indicate that the server cannot be used. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | server id | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | Server status. The server status is as follows:<br/> 1: disconnected status<br/> 2: connected status<br/> 3: shutdown status<br/> 4: graceful shutdown status<br/> 6, rolling update intermediate status, about to switch to status 7<br/> 7 is also a rolling update intermediate status, about to switch to status 1 or 2 | 
- Example 

```python 
import master.serverManager as serverManager 
status = serverManager.GetOneServerStatus(6000) 
``` 
<span id="GetOnlineNumByServerId"></span> 
#### GetOnlineNumByServerId 

- Description 

Get the number of online users of a server (lobby/game/proxy) 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | server id | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | Number of online users | 
- Example 

```python 
import master.serverManager as serverManager 
num = serverManager.GetOnlineNumByServerId(4000)

``` 
<span id="GetOnlineNumByServerType"></span> 
#### GetOnlineNumByServerType 

- Description 

Get the number of online users of a certain type of server 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverType | str | Server type, supports game types such as proxy server/lobby server/game server (see the "Type" configuration in the studio game configuration for details) | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | Number of online users | 
- Example 

```python 
import master.serverManager as serverManager 
num = serverManager.GetOnlineNumByServerType("lobby") 
``` 
<span id="GetServerProtocolVersion"></span> 
#### GetServerProtocolVersion 

- Description 

Get the protocol version number of the server. In a multi-protocol version engine (for example, supporting both 1.14 and 1.15 clients), you need to assign clients to lobby/game with the same protocol version. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | lobby/game server id | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | Protocol version | 
- Example 

```python 
import master.serverManager as serverManager 
version = serverManager.GetServerProtocolVersion(4000) 
``` 
<span id="GetTotalOnlineNum"></span> 
#### GetTotalOnlineNum 


- Description 

Get the total number of online users 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | Number of online users | 
- Example 

```python 
import master.serverManager as serverManager 
num = serverManager.GetTotalOnlineNum() 
``` 
<span id="IsConnectedServer"></span> 
#### IsConnectedServer 

- Description 

Whether the master is connected to the lobby/game/proxy 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Server id | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | True, connection has been established; False, connection has not been established | 
- Example 

```python 
import master.serverManager as serverManager 
bConnect = serverManager.IsConnectedServer(4000) 
``` 
<span id="IsValidServer"></span> 
#### IsValidServer 

- Description 

Whether the server is valid. One use: before the master assigns players to a server, it will check whether the server is valid to avoid assigning players to a server that is about to be closed. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | server id |

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | True, the master has established a connection with the server, and the server is providing services, not about to be shut down. | 
- Example 

```python 
import master.serverManager as serverManager 
bValid = serverManager.IsValidServer(4000) 
``` 
<span id="ResetServer"></span> 
#### ResetServer 

- Description 

Reset a lobby/game. It will restore the server map to the state at startup and restart the server. The ResetGamesBeginEvent event is triggered when the reset starts, and the ResetGamesEndEvent event is triggered when the reset ends 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | lobby/game's server id | 
- Return value 

None 
- Remarks 


Note that for survival servers, if archive A is used, archive A will still be used after the reset, and the map will not be saved during the reset process. 


If you need to reset the game server GameA, use the following method: before resetting, make sure the player exits the corresponding GameA. Players are not allowed to enter GameA during the reset process. After GameA is reset, GameA can send a message to inform the master or service that GameA is ready, and then players can enter GameA. 


- Example 

```python 
import master.serverManager as serverManager 
serverManager.ResetServer(4000) 
``` 
<span id="RollingCloseServers"></span> 
#### RollingCloseServers 

- Description 

Rolling server shutdown 

- Parameters 


| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverIds | list(int) | Server id list | 
- Return value 

None 
- Example 

```python 
import master.serverManager as serverManager 
serverManager.RollingCloseServers([6000]) 
``` 
<span id="RollingUpdateServers"></span> 
#### RollingUpdateServers 

- Description 

Rolling update server, requires the network server to use this ip, requires at least one server with server type serverType and engine version appVersion running, can only roll update proxy server/lobby server/game server 

- Parameter 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverType | str | Server type, game types that support proxy servers/lobby servers/game servers (see the "Type" configuration in the studio game configuration for details) | 
| appVersion | str | engine app_verion | 
| ip | str | server ip | 
| addNum | int | number of new additions, can be negative | 
- Return value 

None 
- Example 

```python 
import master.serverManager as serverManager 
serverManager.RollingUpdateServers('lobby', '2.0.0.release20220120', '10.0.0.1', 1) 
``` 
<span id="StopServerByServerid"></span> 
#### StopServerByServerid 

- Description 

Shut down a server. If "Automatically restart on crash" is set when MCStudio configures the online game, the server will be automatically restarted after it is shut down to achieve the restart function. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | proxy/lobby/game server id | 
| actType | int | 1: Forcefully kick out all players and then shut down the server; 2: Wait for all players to exit before shutting down the server | 
- Return value


    none
- Example

```python
import master.serverManager as serverManager
serverManager.StopServerByServerid(4000, 2)
 ```