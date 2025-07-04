--- 
sidebarDepth: 1 
--- 

# <span id="6-Lobby and Game Server API"></span>6-Lobby and Game Server API 

Here are some common interfaces of lobbygame 

<span id="Archive"></span> 
### Archive 

<span id="QueryPlayerDataResult"></span> 
#### QueryPlayerDataResult 

- Description 

Not recommended for developers to use, inform the engine of the player archive string in the mc map. This api needs to be called in the listener function of the queryPlayerDataEvent event 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbCallIndex | int | Corresponding unique ID of the queryPlayerDataEvent event | 
| success | bool | Success | 
| dataStr | str | Player archive string in the mc map. | 
- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.QueryPlayerDataResult(dbCallIndex, success, dataStr) 
``` 
<span id="SavePlayerDataResult"></span> 
#### SavePlayerDataResult 

- Description 

It is not recommended for developers to use. It informs the engine of the player data archive status. In the mod, player data needs to be saved to mysql/mongo. Call this api in the listener function of the savePlayerDataOnShutDownEvent/savePlayerDataEvent event 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbCallIndex | int | Unique ID passed in the [savePlayerDataEvent/savePlayerDataOnShutDownEvent] event | 
| success | bool | Whether the archive is successful | 
- Return value 

None

- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.SavePlayerDataResult(dbCallIndex, success) 
``` 
<span id="SetUseDatabaseSave"></span> 
#### SetUseDatabaseSave 

- Description 

Set whether to use database scheduled archive. Scheduled archive will trigger savePlayerDataEvent event regularly 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| bUseDatabase | bool | Whether to use database | 
| dbName | str | English string within 30 characters, it is recommended to use the English name of the project | 
| internalSaveSecond | int | The time interval for triggering scheduled archive, in seconds | 
- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.SetUseDatabaseSave(True, 'test', 30) 
``` 
<span id="Configuration"></span> 
### Configuration 

<span id="GetCommonConfig"></span> 
#### GetCommonConfig 

- Description 

Get the server public configuration, including the configuration of this server, all dbs and all functional servers. Please refer to the notes for details. Note that it may not include other lobby servers and game server configurations, and the configuration of all servers cannot be obtained. 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| dict | Configuration content | 
- Notes 

The example of the server public configuration is as follows, which only shows the core configuration information. Note that it may not include other game servers and lobby server configurations. 
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
    "host":"127.0.0.1",    "password":"test_password",
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
    "save":false,    "serverid":4000,
    "type":"lobby"
    }
    ],
    "servicelist":[

], 
} 
``` 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
conf = lobbyGameApi.GetCommonConfig() 
bDebugLevel = conf['log_debug_level'] #Get log level configuration 
``` 
<span id="GetMongoConfig"></span> 
#### GetMongoConfig 

- Description 

Get the connection parameters of the mongo database, corresponding to the mongo configuration in the common configuration. For common configuration, see [GetCommonConfig](#GetCommonConfig) Notes 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| tuple | (exist, host, user, password, database, port).exist: bool, whether there is a mongo database configuration; host: str, The address of the mongo database; user: str, the user who accesses the mongo database; port: int, the port of the mongo database; password: str, the password for accessing the mongo database; database: str, the database name of the mongo database | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
exist, host, user, password, database, port = lobbyGameApi.GetMongoConfig() 
``` 
<span id="GetMysqlConfig"></span> 
#### GetMysqlConfig 

- Description 

Get the connection parameters of the mysql database, corresponding to the mysql configuration in the common configuration, for common configuration, see [GetCommonConfig](#GetCommonConfig) Remarks 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| tuple | (exist, host, user, password, database, port).exist: bool, whether there is a mysql database configuration; host: string, mysql database address; user: string, mysql database access user; port: int, mysql database port; password: string, mysql database access password; database: string, mysql database database name | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
exist, host, user, password, database, port = lobbyGameApi.GetMysqlConfig() 
``` 
<span id="GetRedisConfig"></span> 
#### GetRedisConfig


- Description 

Get the connection parameters of the redis database, corresponding to the redis configuration in the common configuration. For common configuration, see [GetCommonConfig](#GetCommonConfig) Notes 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| tuple | (exist, host, port, password).exist: bool, whether there is redis configuration; host: str, address of redis database; port: int, port of redis database; password: str, access password of redis database | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
exist, host, port, password = lobbyGameApi.GetRedisConfig() 
``` 
<span id="GetServerId"></span> 
#### GetServerId 

- Description 

Get the server id of this server. The server id corresponds to the serverid in the public configuration. For public configuration, see [GetCommonConfig](#GetCommonConfig) Remarks 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | Server id | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
serverId = lobbyGameApi.GetServerId() 
``` 
<span id="Map"></span> 
### Map 

<span id="DelForbidDragonEggTeleportField"></span> 
#### DelForbidDragonEggTeleportField 

- Description 

Delete the map area where dragon egg teleportation is prohibited 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| fid | int | The unique ID of the area, must be greater than or equal to 0 | 
- Return value


| Data type | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful (if the corresponding fid cannot be found, the deletion fails) | 
- Notes 

For specific usage, please refer to the territory plug-in 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
suc = lobbyGameApi.DelForbidDragonEggTeleportField(1) 
``` 
<span id="DelForbidFlowField"></span> 
#### DelForbidFlowField 

- Description 

Delete the map area. The boundaries of areas with different IDs will block the flow of fluids 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| fid | int | The unique ID of the area, must be greater than or equal to 0 | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful (if the corresponding fid cannot be found, the deletion fails) | 
- Notes 

For specific usage, please refer to the territory plug-in 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
suc = lobbyGameApi.DelForbidFlowField(1) 
``` 
<span id="SetEnableLimitArea"></span> 
#### SetEnableLimitArea 

- Description 

Set the maximum area of the map. Terrain exceeding the area will no longer be generated 


- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| limit | bool | Whether to enable regional restrictions | 
| x | int | Center point of the map area | 
| y | int | Center point of the map area | 
| z | int | Center point of the map area | 
| offsetX | int | Maximum offset of the map area in the x and z directions | 
| offsetZ | int | Maximum offset of the map area in the x and z directions | 
- Return value 

None 
- Remarks 

In real applications, please enclose the area with walls. 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.SetEnableLimitArea(limit, x, y, z, offsetX, offsetZ) 
``` 
<span id="SetForbidDragonEggTeleportField"></span> 
#### SetForbidDragonEggTeleportField 

- Description 

Set the map area where dragon egg teleportation is prohibited 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| fid | int | The unique ID of the area, must be greater than or equal to 0 | 
| dimensionId | int | The dimension of the area | 
| minPos | tuple(int) | The point with the smallest x, y, z values in the rectangular area. x, y, z are the coordinates of the block, not the pixel coordinates | 
| maxPos | tuple(int) | The point with the largest x, y, z values in the rectangular area. x, y, z are the coordinates of the block, not the pixel coordinates. | 
| priority | int | The priority of the area. The default value is 0 when missing. When a point is surrounded by multiple areas, the area with the highest priority will be used. | 
| isForbid | bool | Whether to prohibit dragon egg teleportation. In order to handle the authority conflict between nested areas, all independent areas need to set whether to prohibit dragon egg teleportation. | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether to set successfully | 
- Notes 

For specific usage, please refer to the territory plug-in 



- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
suc = lobbyGameApi.SetForbidDragonEggTeleportField(1, 0, (-5, -5, -5), (5, 5, 5), 0, True) 
``` 
<span id="SetForbidFlowField"></span> 
#### SetForbidFlowField 

- Description 

Set the map area. The boundaries of different ID areas will block the flow of fluid 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| fid | int | The unique ID of the area, must be greater than or equal to 0 | 
| dimensionId | int | The dimension where the area is located | 
| minPos | tuple(int) | The point with the smallest x, y, and z values in the rectangular area. x, y, and z are block coordinates, not pixel coordinates. | 
| maxPos | tuple(int) | The point with the largest x, y, and z values in the rectangular area. x, y, and z are block coordinates, not pixel coordinates. | 
| priority | int | The priority of the area. The default value is 0 when missing. When a point is surrounded by multiple areas, the area with the highest priority will be used. | 
| isForbid | bool | Whether to prohibit fluid flow. In order to handle the authority conflict between nested areas, all independent areas need to set whether to prohibit fluid flow. | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 
- Remarks 

For specific usage, please refer to the territory plugin 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
suc = lobbyGameApi.SetForbidFlowField(1, 0, (-5, -5, -5), (5, 5, 5), 0, True) 
``` 
<span id="SetLevelGameType"></span> 
#### SetLevelGameType 

- Description 

Force the game play mode 

- Parameters 

| Parameter name | Data type | Description |

| :--- | :--- | :--- | 
| mode | int | 0 survival mode, 1 creative mode, 2 adventure mode | 
- Return value 

None 
- Remarks 

In real applications, please call this function when the server Mod is initialized 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.SetLevelGameType(2) 
``` 
<span id="SetShowFakeSeed"></span> 
#### SetShowFakeSeed 

- Description 

In the client [Settings], display a fake game map seed 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| fakeSeed | int | The fake map seed you want to display on the client must be a positive integer. It can be missing. If missing, a random number will be automatically generated. | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Execution result | 
- Notes 

This API only affects players who log in after the call, so it is strongly recommended to call this API when the Mod is initialized. 

The effect of this API call will be persisted and saved in the map file 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
suc = lobbyGameApi.SetShowFakeSeed(123456789) 
print "SetShowFakeSeed suc={}".format(suc) 
``` 
<span id="StopShowFakeSeed"></span> 
#### StopShowFakeSeed 


- Description 

In the client [Settings], display the real game map seed 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Execution result | 
- Notes 

This API only affects players who log in after the call, so it is strongly recommended to call this API when the Mod is initialized 

The effect of this API call will be persisted and saved in the map file 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
suc = lobbyGameApi.StopShowFakeSeed() 
print "StopShowFakeSeed suc={}".format(suc) 
``` 
<span id="Player"></span> 
### Player 

<span id="GetConnectingProxyIdOfPlayer"></span> 
#### GetConnectingProxyIdOfPlayer 

- Description 

Get the proxy server id that the player client is connected to 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | proxy server id | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
nickname = lobbyGameApi.GetConnectingProxyIdOfPlayer(playerId) 
``` 
<span id="GetPlatformUid"></span>

#### GetPlatformUid 

- Description 

Get the uid of the player's login terminal. If the player logs in from the mobile terminal, the uid of the mobile terminal is returned, otherwise the uid of the PC terminal is returned. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| int/long/None | Returns None when the player is not online. If the player logs in from the mobile terminal when online, the uid of the mobile terminal is returned, otherwise the uid of the PC terminal is returned | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
platformUid = lobbyGameApi.GetPlatformUid(playerId) 
``` 
<span id="GetPlayerIdByUid"></span> 
#### GetPlayerIdByUid 

- Description 

Get the player ID (also known as playerId) based on the player uid. If the player is not in this lobby/game, an empty string is returned 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| str | Player id, that is, the player's playerId | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
playerId = lobbyGameApi.GetPlayerIdByUid(123) 
``` 
<span id="GetPlayerLockResult"></span> 
#### GetPlayerLockResult 

- Description 

It is not recommended for developers to use. Inform the engine layer of the result of obtaining the player's online lock 

- Parameters 

| Parameter name | Data type | Description |

| :--- | :--- | :--- | 
| id | int | Corresponding to the unique ID of the [ServerGetPlayerLockEvent] event | 
| success | bool | Success | 
- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.GetPlayerLockResult(id, suc) 
``` 
<span id="GetPlayerNickname"></span> 
#### GetPlayerNickname 

- Description 

Get the player's nickname. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| str | nickname | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
nickname = lobbyGameApi.GetPlayerNickname(playerId) 
``` 
<span id="GetPlayerUid"></span> 
#### GetPlayerUid 

- Description 

Get the player's uid 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 
- Return value 

| Data type | Description |

| :--- | :--- | 
| int/long | Player's uid; unique identifier of the player | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
uid = lobbyGameApi.GetPlayerUid(playerId) 
``` 
<span id="GetUidIsSilent"></span> 
#### GetUidIsSilent 

- Description 

Get whether the player is muted based on the player's uid 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | 0: global muting, 1: normal muting, 2: not muted | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
isSilent = lobbyGameApi.GetUidIsSilent(123) 
``` 
<span id="HidePlayerFootprint"></span> 
#### HidePlayerFootprint 

- Description 

Hide the appearance of a player's member footprints 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| str | playerId | Player id | 
| hide | bool | Whether to hide, True to hide the footprints, False to restore the footprints display | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | True: Setting success<br>False: Setting failure | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
# Hide the player's member footprint appearance 
result = lobbyGameApi.HidePlayerFootprint(playerId, True)

``` 
<span id="HidePlayerMagicCircle"></span> 
#### HidePlayerMagicCircle 

- Description 

Hide the appearance of a player's member magic circle 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| str | playerId | Player id | 
| hide | bool | Whether to hide, True is to hide the magic circle, False is to restore the magic circle display | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | True: Setting success<br>False: Setting failure | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
# Hide the appearance of the player's member magic circle 
result = lobbyGameApi.HidePlayerMagicCircle(playerId, True) 
``` 
<span id="IsPlayerPeUser"></span> 
#### IsPlayerPeUser 

- Description 

Get whether the player is logged in from the mobile phone 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool/None | Returns None when the player is not online, returns True when online, indicating that the player is logged in from the mobile phone, and returns False, indicating that the player is logged in from the PC | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
isPeUser = lobbyGameApi.IsPlayerPeUser(playerId)
 ```
<span id="ReleasePlayerLockResult"></span>

#### ReleasePlayerLockResult 

- Description 

Not recommended for developers to use, inform the engine layer of the result of releasing the player's online lock 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| id | int | Corresponding to the unique ID passed in by the [ServerReleasePlayerLockEvent/ServerReleasePlayerLockOnShutDownEvent] event | 
| success | bool | Success | 
- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.ReleasePlayerLockResult(id, suc) 
``` 
<span id="SetAutoRespawn"></span> 
#### SetAutoRespawn 

- Description 

Set whether to enable the automatic respawn logic 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| autoRespawn | bool | Whether to enable the auto-respawn logic | 
| internalSeconds | int | How many seconds to check whether the auto-respawn conditions are met | 
| minY | int | The height below which the auto-respawn logic is triggered | 
| x | int | The coordinates of the respawn point after the auto-respawn logic is triggered | 
| y | int | The coordinates of the respawn point after the auto-respawn logic is triggered | 
| z | int | The coordinates of the respawn point after the auto-respawn logic is triggered | 
- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.SetAutoRespawn(autoRespawn, internalSeconds, minY, x, y, z) 
 ```
<span id="ShieldPlayerJoinText"></span>
#### ShieldPlayerJoinText

- Description 

Whether to block the prompt "xxx joined the game" in the upper left corner of the client 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| bShield | bool | True, no prompt; False, display prompt | 
- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.ShieldPlayerJoinText(True) 
``` 
<span id="TryToKickoutPlayer"></span> 
#### TryToKickoutPlayer 

- Description 

Kick the player offline, the text in the message will be displayed in the disconnection prompt of the client 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| playerId | str | entityId of the player object | 
| message | str | Reason for kicking out the player, empty by default | 
- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.TryToKickoutPlayer(playerId, "GM kicks you off the line") 
``` 
<span id="debug"></span> 
### debug 

<span id="StartChunkProfile"></span> 
#### StartChunkProfile 

- Description 

Start the server-side block read and write performance statistics. After starting, call [StopChunkProfile](#StopChunkProfile) to obtain the recent server-side block read and write information 


- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Execution result | 
- Notes 

Starting block read and write information records consumes a lot of resources, so it is not recommended to enable it for a long time. 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
suc = lobbyGameApi.StartChunkProfile() 
print "StartChunkProfile suc={}".format(suc) 
# Then call StopChunkProfile through a timer or other triggering method 
data = lobbyGameApi.StopChunkProfile() 
for singleData in data: 
print "time is {}".format(time.strftime("%H:%M:%S", time.localtime(singleData["timestamp"]))) 
print "saveChunks is {}".format(singleData["saveChunks"]) 
print "loadChunks is {}".format(singleData["loadChunks"]) 
``` 
<span id="StopChunkProfile"></span> 
#### StopChunkProfile 

- Description 

End the server-side block read and write performance statistics, and return the recent block read and write information, used with [StartChunkProfile](#StartChunkProfile) 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| list(dict) | Each dictionary is the block read and write information within 1 second, sorted by timeline, timestamp: type is int, the specific time (seconds) of statistics; saveChunks: type is list(dict), the coordinates and dimensions of the chunk written within 1 second; loadChunks: type is list(dict), the coordinates and dimensions of the chunk read within 1 second | 
- Notes 

Starting block read and write information recording has a relatively large consumption, and it is not recommended to enable it for a long time 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
suc = lobbyGameApi.StartChunkProfile() 
print "StartChunkProfile suc={}".format(suc) 
# Then call StopChunkProfile through a timer or other trigger method 
data = lobbyGameApi.StopChunkProfile() 
for singleData in data: 
print "time is {}".format(time.strftime("%H:%M:%S", time.localtime(singleData["timestamp"])))

print "saveChunks is {}".format(singleData["saveChunks"]) 
print "loadChunks is {}".format(singleData["loadChunks"]) 
``` 
<span id="Shutdown"></span> 
### Shutdown 

<span id="SetGracefulShutdownOk"></span> 
#### SetGracefulShutdownOk 

- Description 

Not recommended for developers. The graceful shutdown logic of the script layer has been executed and the engine can start graceful shutdown. 

- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.SetGracefulShutdownOk() 
``` 
<span id="SetShutdownOk"></span> 
#### SetShutdownOk 

- Description 

It is not recommended for developers to use. The forced shutdown logic of the script layer has been executed, and the engine can start forced shutdown. 

- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.SetShutdownOk() 
``` 
<span id="ShutdownServer"></span> 
#### ShutdownServer 

- Description 

Forced shutdown 

- Return value 

None 
- Example 


```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.ShutdownServer() 
``` 
<span id="Server"></span> 
### Server 

<span id="CheckMasterExist"></span> 
#### CheckMasterExist 

- Description 

Check whether the server is connected to the master 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether to establish a connection with the master | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
exist = lobbyGameApi.CheckMasterExist() 
``` 
<span id="GetLastFrameTime"></span> 
#### GetLastFrameTime 

- Description 

Get the last frame running time of the server script 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | The last frame running time of the server script, in nanoseconds | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lastFrameTime = lobbyGameApi.GetLastFrameTime() 
``` 
<span id="GetOnlinePlayerNum"></span> 
#### GetOnlinePlayerNum 

- Description 

Get the number of online players on the current server 


- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | Current number of online players on the server | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
num = lobbyGameApi.GetOnlinePlayerNum() 
``` 
<span id="GetServerProtocolVersion"></span> 
#### GetServerProtocolVersion 

- Description 

Get the protocol version number of the server 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | The protocol version number of the server | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
protocolVersion = lobbyGameApi.GetServerProtocolVersion() 
``` 
<span id="IsServiceConnected"></span> 
#### IsServiceConnected 

- Description 

Check if the server is connected to a service 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether to establish a connection with the service | 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
bConnected = lobbyGameApi.IsServiceConnected(8000) 
``` 
<span id="IsShowDebugLog"></span> 
#### IsShowDebugLog 


- Description 

Whether the current server prints debug-level logs 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | True, print debug log, otherwise do not print debug log | 
- Remarks 

Basically no need to pay attention 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
bDebug = lobbyGameApi.IsShowDebugLog() 
``` 
<span id="ResetServer"></span> 
#### ResetServer 

- Description 

Reset server 

- Return value 

None 
- Remarks 


Note that for survival servers, if archive A is used, archive A will still be used after reset, and the map will not be saved during the reset process. 


Method to reset this server: Make sure players exit this server before resetting. Players are not allowed to enter this server during the reset process. After starting this server, you can send a message to the master or service to inform that the server is ready, and then players can enter this server. 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.ResetServer() 
``` 
<span id="切服"></span> 
### 切服 

<span id="TransferToOtherServer"></span> 
#### TransferToOtherServer


- Description 

The player is transferred to a server of the specified type. If there are multiple servers of the same type, one server is selected based on load balancing. 
- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
| typeName | str | Type of target server, corresponding to the configuration in MCStudio: Server Configuration->Game Configuration->Type | 
| transferParam | str | Parameters passed in when switching servers, empty string by default. When the player jumps to the target server and triggers the AddServerPlayerEvent event, the AddServerPlayerEvent event will carry this parameter | 
| callback | function | callback function, returns the result of the server transfer API after the master's logical judgment, with three parameters, isSuc(bool), reasonCode(int), message(str), isSuc returns whether it is successful; reasonCode represents the error code of failure, and message is the Chinese description of the reason for failure | 
- Return value 

None 
- Remarks 

The player will only switch to an available service, which means that the target server is required to be in normal working state, and cannot be in abnormal states such as disconnection, rolling shutdown, and shutdown. If the target server is not available, the server transfer fails. 


- Example 

```python 
import json 
import lobbyGame.netgameApi as lobbyGameApi 
transData = {'position' : [1,2,3]} 
def cbFunc(isSuc, reasonCode, message): 
print "TransferToOtherServer callback, isSuc={} reason={}".format(isSuc, message) 
lobbyGameApi.TransferToOtherServer('123', 'game', json.dumps(transData), cbFunc) 
``` 
<span id="TransferToOtherServerById"></span> 
#### TransferToOtherServerById 

- Description 

Players migrate to the server with the specified server id 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
| serverId | str | Target server id, server id corresponds to serverid in public configuration, public configuration see [GetCommonConfig](#GetCommonConfig) Notes | 
| transferParam | str | Server switching parameter, default empty string. When the player jumps to the target server and triggers the AddServerPlayerEvent event, the AddServerPlayerEvent event will carry this parameter | 
| callback | function | callback function, which returns the result of the server transfer API after the master's logical judgment. There are three parameters, isSuc (bool), reasonCode (int), message (str), isSuc returns whether it is successful; reasonCode represents the error code of failure, and message is the Chinese description of the reason for failure | 
- Return value 

None 
- Remarks


    For usage details, see the example Mod sample 

The target server is required to be in normal working state, and cannot be in abnormal state such as disconnected, rolling shutdown, and shutdown. If the target server is not available, the server switching fails. 


- Example 

```python 
import json 
import lobbyGame.netgameApi as lobbyGameApi 
transData = {'position' : [1,2,3]} 
def cbFunc(isSuc, reasonCode, message): 
print "TransferToOtherServerById callback, isSuc={} reason={}".format(isSuc, message) 
lobbyGameApi.TransferToOtherServerById('123', 2000000, json.dumps(transData), cbFunc) 
``` 
<span id="Main City Mode"></span> 
### Main City Mode 

<span id="SetCityMode"></span> 
#### SetCityMode 

- Description 

Set the game to main city mode: including restrictions such as unable to change terrain, not switching between day and night, not changing weather, not refreshing creatures, etc. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| isCityMode | bool | Whether it is main city mode | 
- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.SetCityMode(isCityMode) 
``` 
<span id="HTTP server"></span> 
### HTTP server 

<span id="RegisterOpCommand"></span> 
#### RegisterOpCommand 

- Description 

Register a new HTTP interface 


- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| url | str | Interface url | 
| callback | function | Instance function that responds to HTTP requests. There are two parameters. The first parameter, clientId, is of type int and is the unique identifier of the requester, used to return the request processing result; the second parameter, requestData, is of type dict and contains the parameters of the HTTP request (requestBody) | 
- Return value 

None 
- Remarks 

When multiple game servers/function servers register the same url, the request will be broadcasted to all servers that have registered this url by default, and the return result will also combine the return results of all servers 

By adding the opUid [type int] parameter in the request, you can specify that this request is only forwarded to the server with the corresponding uid currently online 

By adding the opServerIds [type is list(int)] parameter in the request, you can specify that this request is only forwarded to the server whose server ID is in the opServerIds list. 

By adding the opServerType [type is str] parameter in the request, you can specify that this request is only forwarded to the server whose server type is opServerType. 

When the url registered by this API is the same as the url registered by [masterHttp.RegisterMasterHttp], only one of them can be retained, and the later executed statement will replace the callback of the earlier executed statement. 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
class GameExtraApiSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 
lobbyGameApi.RegisterOpCommand("/api/game-url-test1", self.OnGameUrlTest1) 
def OnGameUrlTest1(self, clientId, requestData): 
print "OnGameUrlTest1", clientId, requestData 
# Return processing results 
lobbyGameApi.ResponseOpCommandSuccess(clientId, {"result":"exec success"}) 
``` 
<span id="ResponseOpCommandFail"></span> 
#### ResponseOpCommandFail 

- Description 

Send HTTP failed Response, support asynchronous return, specify the clientId passed in the request when returning 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| clientId | int | Request unique ID, identify HTTP request. | 
| code | int | Request failure reason code | 
| message | str | Request failure reason text | 
- Return value


    none
- Example

```python
import lobbyGame.netgameApi as lobbyGameApi
class GameExtraApiSystem(ServerSystem):
        def __init__(self, namespace, systemName):
                ServerSystem.__init__(self, namespace, systemName)
                lobbyGameApi.RegisterOpCommand("/api/game-url-test2", self.OnServiceUrlTest2)
        
        def OnServiceUrlTest2(self, clientId, requestData):
                print "OnServiceUrlTest2", clientId, requestData
                #Return processing results
                lobbyGameApi.ResponseOpCommandFail(clientId, 1, "exec failed")
 ```
<span id="ResponseOpCommandSuccess"></span>
#### ResponseOpCommandSuccess

- describe

Send HTTP successful Response, support asynchronous return, specify the clientId passed in the request when returning 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| clientId | int | Request unique ID, identify HTTP request. | 
| entity | dict | Content to be returned in the request, you can customize the meaning of key/value | 
- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
class GameExtraApiSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 
lobbyGameApi.RegisterOpCommand("/api/game-url-test1", self.OnGameUrlTest1) 
def OnGameUrlTest1(self, clientId, requestData): 
print "OnGameUrlTest1", clientId, requestData 
# Return processing results 
lobbyGameApi.ResponseOpCommandSuccess(clientId, {"result":"exec success"}) 
``` 
<span id="UnRegisterOpCommand"></span>
#### UnRegisterOpCommand

- describe


Unregister a registered HTTP interface 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| url | str | Interface url | 
- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
class GameExtraApiSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 
lobbyGameApi.RegisterOpCommand("/api/game-url-test1", self.OnGameUrlTest1) 

def Destroy(self): 
lobbyGameApi.UnRegisterOpCommand("/api/game-url-test1") 

def OnGameUrlTest1(self, clientId, requestData): 
print "OnGameUrlTest1", clientId, requestData 
# Return processing results 
lobbyGameApi.ResponseOpCommandSuccess(clientId, {"result":"exec success"}) 
``` 
<span id="Shop"></span> 
### Shop 

<span id="NotifyClientToOpenShopUi"></span> 
#### NotifyClientToOpenShopUi 

- Description 

Notify the client to open the shop interface 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
- Return value 

None 
- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi
lobbyGameApi.NotifyClientToOpenShopUi('123456')

``` 
<span id="Performance switch"></span> 
### Performance switch 

<span id="ChangeAllPerformanceSwitch"></span> 
#### ChangeAllPerformanceSwitch 

- Description 

Turn off/on the predefined game native logic as a whole. The default state of all logics is [on] (that is, is_disable=False). 
Only when this interface is called to turn it off will it enter the [off] state. Turning off this type of native logic can improve the performance of the server and support a higher number of simultaneous online users. At the same time, it will also invalidate the gameplay of some survival servers. In addition, it is strongly recommended to call this interface when the server is initialized, and do not modify it while the server is running. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| is_disable | bool | True represents [off], False represents [on] | 
| extra | list | An enumeration value list that excludes specific functions that do not need to change the switch state. Default is empty | 
- Return value 

None 
- Remarks 

When the value of extra is None, the default affected switch does not include [LoadSavedEntityFromChunk]. 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
lobbyGameApi.ChangeAllPerformanceSwitch(True) 
``` 
<span id="ChangePerformanceSwitch"></span> 
#### ChangePerformanceSwitch 

- Description 

Turn off/on a game's native logic. All logics are in the default state of [on] (that is, is_disable=False). 
Only when this interface is called to turn it off will it enter the [off] state. Turning off this type of native logic can improve the performance of the server, 
and support a higher number of simultaneous online users. At the same time, it will also invalidate some survival server gameplay. In addition, it is strongly recommended to call this interface when the server is initialized, and do not modify it during server operation. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| key | int | Enumeration value of specific function, see notes for details | 
| isDisable | bool | True means [off], False means [on] | 
- Return value


None 
- Notes 

Enumeration values and meanings of all switches 
```python 
class DisableSwitch(object): 
''' 
-------------------ChunkLoadUsePriority------------------- 
Switch introduction: When loading a chunk, whether to calculate the weighted priority based on the chunk's coordinates and the coordinates of the current online player (lower performance). After disable, all chunks have the same loading priority 
Applicable situations: Provide a specific map, no server generation required 
Impact on mod sdk: No impact on mod sdk 
''' 
ChunkLoadUsePriority = 1 
''' 
-------------------RedstoneOnTick------------------- 
Switch introduction: Shield redstone circuit logic, redstone-related logic will not take effect after disable 
Applicable situations: No redstone and circuit-related functions are used 
Impact on mod sdk: 
1. Customizable redstone 
2. Server-side events: BlockStrengthChangedServerEvent is not triggered 
3. Server-side component: redStone is not effective 
''' 
RedstoneOnTick = 2 
''' 
-------------------ChunkSaveOnTick------------------- 
Switch description: Whether to save chunks. After disable, changes to map chunks will no longer be saved to the map file 
Applicable situations: The map will not change 
Scope of impact on mod sdk: 
1. Server-side events are not affected 
2. Affected APIs: 
(1) SetBlockTileEntityCustomData settings will not be saved to the map 
(2) SetBlockStates block states will not be saved to the map 
(3) SetBlockNew can set blocks, but the settings are not saved to the map 
''' 
ChunkSaveOnTick = 3 
''' 
-------------------WalkAnimPostEvent------------------- 
Switch introduction: whether to turn off the server's move start/move end events (low performance). After disable, the server engine layer will no longer dispatch the above two events. 
Applicable situations: no listening of WalkAnimBeginServerEvent and WalkAnimEndServerEvent (generally, the client's WalkAnimBeginClientEvent and WalkAnimEndClientEvent can be used instead) 
Impact on mod sdk: Do not trigger WalkAnimBeginServerEvent and WalkAnimEndServerEvent 
''' 
WalkAnimPostEvent = 4 
''' 
-------------------RecipesSyncOnLogin------------------- 
Switch introduction: whether to send the server recipe list after login. After disable, the client cannot receive the recipe list after login, and the client cannot synthesize, smelt, or refine medicine. 
Applicable situations: Players do not synthesize, smelt, or refine medicine. 
Impact on mod sdk: Does not affect sdk 
''' 
RecipesSyncOnLogin = 5

''' 
-------------------UpdateGlidingOnTick------------------- 
Switch description: Whether to block the player's gliding function. Once disabled, once the gliding state is entered, the state update will be abnormal. 
Applicable situation: the player does not perform gliding operations 
Affecting the scope of mod sdk: does not affect sdk 
''' 
UpdateGlidingOnTick = 6 
''' 
-------------------UpdateContainerOnTick------------------- 
Switch description: Whether to execute the refresh logic of each frame of the container. After disable, the furnace, cauldron, blast furnace, smoker, and brewing stand cannot be used 
Applicable situation: furnace, cauldron, blast furnace, smoker, and brewing stand are not used 
Affecting the scope of mod sdk: does not affect sdk 
''' 
UpdateContainerOnTick = 7 
''' 
-------------------PushEntitiesOnTick------------------- 
Switch description: Whether to execute the logic of players pushing items/entities. After disable, players cannot push items/entities on the map. Applicable situations: Player pushing function is not considered. Affecting the scope of mod sdk: Server-side events: OnPlayerHitMobServerEvent is not triggered. Server-side components: Component actorPushable is not effective. ''' PushEntitiesOnTick = 8 ''' -------------------UpdateInsideBlockOnTick------------------- Switch description: Whether to execute the special judgment logic of each frame of the entity in the block. After disable, the portal cannot start the transmission. In addition, there will be no blood loss on the side of the cactus and on the sweet berry bush. Applicable situations: Do not consider the above special logic. Affecting the scope of mod sdk: Server-side events: WillTeleportToServerEvent, DimensionChangeFinishServerEvent, DimensionChangeServerEvent are not triggered. Server-side components: Not affected. ''' UpdateInsideBlockOnTick = 9 
''' 
-------------------BlockDamageOnTick------------------- 
Switch description: Whether to execute the special judgment logic of the entity on special terrain every frame. After disabling, standing on the magma block and the lit campfire will not be injured. 
Applicable situations: Do not consider the special logic above. 
Impact on mod sdk range: Does not affect sdk. 
''' 
BlockDamageOnTick = 10 
''' 
-------------------SendDirtyActorPerTick------------------- 
Switch description: Whether to check the entity attribute changes and synchronize them every frame. After disabling, the detection frequency is reduced from every frame to every second. It will cause the player to delay one second to synchronize to the local after losing blood. 
Applicable situations: Allow delayed synchronization of biological attributes 
Affecting the scope of mod sdk: SyncModDataServerEvent event will be triggered with delay 
''' 
SendDirtyActorPerTick = 13 
''' 
-------------------ApplyExhaustionOnTick------------------- 
Switch introduction: Whether to execute the hunger logic when the player moves. After disabling, the player's walking, running, swimming will not consume hunger, and jumping, hunger effects, etc. will not reduce the hunger value. 
Applicable situations: The hunger value remains unchanged, or the SetDisableHunger interface is used to block the player's hunger.

Affecting mod sdk scope: does not affect sdk 
''' 
ApplyExhaustionOnTick = 14 
''' 
-------------------UpdateInteractionOnTick------------------- 
Switch description: whether to check character interaction every frame. After disable, the interaction button will not be displayed when the crosshair points to the interactive entity, but long press can still trigger the interaction 
Applicable situation: text prompts for interaction are not considered 
Affecting mod sdk scope: does not trigger OnCarriedNewItemChangedServerEvent event 
''' 
UpdateInteractionOnTick = 15 
''' 
-------------------UpdateOffhandItemOnTick------------------- 
Switch description: whether to check the changes in the character's off-hand equipment attributes every frame and synchronize them. After disable, the off-hand holding the map position will not be updated 
Applicable situation: the off-hand does not use the map 
Affecting mod sdk scope: does not affect sdk 
''' 
UpdateOffhandItemOnTick = 16 
''' 
-------------------PickEntityOnTick------------------- 
Switch description: whether to check nearby pick-up items every frame, and no items will be picked up after disable 
Applicable situations: players do not pick up nearby items 
Impact on mod sdk range: 
1. Server-side event: ServerPlayerTryTouchEvent is not triggered 
2. Server-side component: SetPickUpArea in player component is useless 
''' 
PickEntityOnTick = 17 
''' 
-------------------SyncComplexItemOnTick------------------- 
Switch description: whether to synchronize the player's map (Map) or empty map (Empty Map) content every frame, and do not synchronize the map or blank map after disable 
Applicable situations: do not use map (Map) or empty map (Empty Map) 
Impact on mod sdk range: does not affect sdk 
''' 
SyncComplexItemOnTick = 18 
''' 
-------------------UpdateChunkPerTick------------------- 
Switch description: whether to execute the tick logic of the chunk every frame, after disable, the execution frequency will be reduced from every frame to once every 4 frames 
Applicable situations: there is a delay in the update of the entity logic on the map, the block entity logic, and the random tick of the block 
Impact on the scope of mod sdk: does not affect the sdk 
''' 
UpdateChunkPerTick = 19 
''' 
-------------------SpawnMobsOnTick------------------- 
Switch description: whether to automatically generate monsters, after disable, monsters will not be automatically generated in the game 
Applicable situations: monsters are not automatically generated in the game, and creatures will not be generated with structures (for example, villages will not generate villagers) 
Impact on the scope of mod sdk: ServerSpawnMobEvent server-side events are not triggered 
''' 
SpawnMobsOnTick = 20 
''' 
-------------------UpdateBlocksOnTick------------------- 
Switch introduction: whether to refresh the block logic every frame. After disable, lightning and skeleton traps will no longer refresh, the block will not be affected by weather, and random ticks will not be executed.

Applicable situations: Applicable to scenes where the map and weather remain unchanged 
Impact on mod sdk: BlockRandomTickServerEvent server-side events are not triggered 
''' 
UpdateBlocksOnTick = 22 
''' 
-------------------UpdateWeatherOnTick------------------- 
Switch description: Whether to execute weather refresh logic every frame. After disable, the weather will no longer refresh (thunder and rain), and the season will not change 
Applicable situations: Weather and season remain unchanged 
Impact on mod sdk: No impact on sdk 
''' 
UpdateWeatherOnTick = 23 
''' 
-------------------LoadSavedEntityFromChunk------------------- 
Switch description: Whether to not load entities in chunk archives. After disable, the entity archive will be invalid 
Applicable situations: Do not load entities from the map, do not archive entities 
Impact on mod sdk: No impact on sdk 
''' 
LoadSavedEntityFromChunk = 27 
``` 


- Example 

```python 
import lobbyGame.netgameApi as lobbyGameApi 
import lobbyGame.netgameConsts as netgameConsts 
lobbyGameApi.ChangePerformanceSwitch(netgameConsts.DisableSwitch.ChunkLoadUsePriority, True) 
``` 
Here are some interfaces of lobby 

<span id="Main City Mode"></span> 
### Main City Mode 

<span id="SetCityMode"></span> 
#### SetCityMode 

- Description 

[Abandoned] Set the game to main city mode: including restrictions such as unable to change terrain, not switching day and night, not changing weather, not refreshing creatures, etc. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| isCityMode | bool | Whether it is the main city mode | 
- Return value 

None 
- Example 


```python
import lobby.netgameApi as lobbyApi
lobbyApi.SetCityMode(isCityMode)
 ```