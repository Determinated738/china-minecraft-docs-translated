--- 
sidebarDepth: 1 
--- 

# <span id="1-Lobby and Game Server Events"></span>1-Lobby and Game Server Events 

Event definition. 

<span id="Server"></span> 
## Server 

<span id="MasterConnectStatusEvent"></span> 
### MasterConnectStatusEvent 

- Description 

Master successfully connected to the current server event 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| isConnect | int | 1 represents connection establishment, 0 represents connection interruption | 
| serverId | int | Current lobby/game server id | 
- Return value 

None 
<span id="MasterForceShutDownEvent"></span> 
### MasterForceShutDownEvent 

- Description 

Not recommended for developers to use, this event will be triggered when the current server is forcibly closed 

- Return value 

None 
<span id="MasterGraceShutDownEvent"></span> 
### MasterGraceShutDownEvent 

- Description 

Developers are not recommended to use this event. This event will be triggered when the current server is gracefully shut down. 

- Return value 

None 
<span id="ServerWillShutDownEvent"></span> 
### ServerWillShutDownEvent


- Description 

Developers are not recommended to use this event. The game will be forced to close and trigger this event. The event callback function needs to be cleaned up and archived, and terminate or force join all asynchronous threads. 

- Return value 

None 
<span id="ServiceConnectEvent"></span> 
### ServiceConnectEvent 

- Description 

Event of successful connection between service and lobby/game 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Service server id | 
| serviceType | str | Service server type | 
- Return value 

None 
<span id="ServiceDisconnectEvent"></span> 
### ServiceDisconnectEvent 

- Description 

Event of disconnection between service and lobby/game 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | server id of service | 
- Return value 

None 
<span id="ServiceRegisterModuleEvent"></span> 
### ServiceRegisterModuleEvent 

- Description 

Not recommended for developers to use, service registers module to lobby/game 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- |

| serverId | int | service server id | 
| moduleName | str | module name, which is a module in module_names in the common configuration | 
- Return value 

None 
<span id="Configuration"></span> 
## Configuration 

<span id="ReloadCommonConfigEvent"></span> 
### ReloadCommonConfigEvent 

- Description 

Developers are not recommended to use this event. This event is triggered when the common configuration changes. Note that this event is only triggered when the configuration related to this server changes, such as the log level. 

- Return value 

None 
<span id="Player"></span> 
## Player 

<span id="MasterResponseTransferFailServerEvent"></span> 
### MasterResponseTransferFailServerEvent 

- Description 

Server transfer failure event. When a player attempts to transfer servers, this event is thrown when there is no target server that meets the conditions. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player uid, unique identifier of the player | 
| reason | int | Error code of failure, serverApi.GetMinecraftEnum().TransferServerFailReason | 
- Return value 

None 
<span id="MasterResponseTransferSucServerEvent"></span> 
### MasterResponseTransferSucServerEvent 

- Description 

Successful server transfer event. When a player attempts to transfer servers, this event is thrown when the target server to which the transfer can be made is successfully located. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player uid, unique identifier of the player | 
- Return value


None 
<span id="ServerGetPlayerLockEvent"></span> 
### ServerGetPlayerLockEvent 

- Description 

Get the player's online lock event when the player logs in to the lobby/game. When the event is triggered, the player is still in the initial login stage, 
has not downloaded the behavior pack, and has not been born in the map. The online lock is actually the player's online information recorded in redis. The redis key format is "user:online: + netease uid". It is a hash table containing two hash keys: serverid, proxyid. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player's netease uid, player's unique identifier | 
| serverId | int | Current server id | 
| proxyId | int | Proxy server id to which the current client is connected | 
- Return value 

None 
<span id="ServerPlayerBornPosEvent"></span> 
### ServerPlayerBornPosEvent 

- Description 

This event is triggered when the player's birth position is set during the creation of the player object 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| userId | int | Player's netease uid | 
| dimensionId | int | Player's birth dimension, supports modification | 
| posx | int | Player's birth position, supports modification | 
| posy | int | Player's birth position, supports modification | 
| posz | int | Player's birth position, supports modification | 
| deltax | int | Player's motion position, the initial value is the data in the archive. If posx/posy/posz is modified, it is recommended to set it to 0. | 
| deltay | int | Player's motion position, the initial value is the data in the archive. If posx/posy/posz is modified, it is recommended to set it to 0. | 
| deltaz | int | Player's motion position, the initial value is the data in the archive. If posx/posy/posz is modified, it is recommended to set it to 0. | 
| rotx | int | Player's rot, initial value is the data in the archive, supports modification | 
| roty | int | Player's rot, initial value is the data in the archive, supports modification | 
| ret | bool | Whether to modify the player's initial position, other data modifications will take effect only after setting to True | 
- Return value 

None 
<span id="ServerReleasePlayerLockEvent"></span> 
### ServerReleasePlayerLockEvent 

- Description


When the player is offline, the player online lock event in redis is released. When the event is triggered, the client is disconnected from the server, the player data has been saved to the map, and the player no longer exists in the MC world. The online lock is actually the player's online information recorded in redis. 
The redis key format is "user:online: + netease uid". It is a hash table containing two hash keys: serverid, proxyid 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player's netease uid, the player's unique identifier | 
- Return value 

None 
<span id="ServerReleasePlayerLockOnShutDownEvent"></span> 
### ServerReleasePlayerLockOnShutDownEvent 

- Description 

It is not recommended for developers to use. This event is triggered when the player is forced offline during the game's forced shutdown process. The event callback function needs to release the player's online lock in redis 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| idx | int | Event unique id, returned when callback | 
| uid | int/long | Player's netease uid, player's unique identifier | 
- Return value 

None 
<span id="StoreBuySuccServerEvent"></span> 
### StoreBuySuccServerEvent 

- Description 

Event thrown by the server when the player purchases goods in the game 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
- Return value 

None 
<span id="queryPlayerDataEvent"></span>
### queryPlayerDataEvent

- describe


It is not recommended for developers to use. When the player goes online, the engine triggers this event when reading the player entity archive data. 
This event is only valid after [SetUseDatabaseSave] is set to use database archive. 
To trigger this event, developers need to read the player entity data from the archive, and then set the modified player entity data back to the engine through [SavePlayerDataResult] 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| idx | int | Event unique id, [QueryPlayerDataResult] will use this id | 
| playerKey | str | Player uid string, player's unique identifier | 
| dbName | str | Database archive prefix, dbname can be set through [SetUseDatabaseSave] | 
- Return value 

None 
<span id="savePlayerDataEvent"></span> 
### savePlayerDataEvent 

- Description 

Save player data event, which will also be triggered when the player goes offline. This event will only take effect when [SetUseDatabaseSave] sets 
useDatabase to True. The callback function of this event 
Must call the [SavePlayerDataResult] function to inform the engine of the archive status 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| idx | int | Engine callback function id, [SavePlayerDataResult] will use this id | 
| playerKey | str | Player uid string, player's unique identifier | 
- Return value 

None 
<span id="savePlayerDataOnShutDownEvent"></span> 
### savePlayerDataOnShutDownEvent 

- Description 

This event is triggered when the player goes offline during the game forced shutdown process. In addition, this event is only effective when [SetUseDatabaseSave] sets 
useDatabase to True. The callback function of this event must call the 
【SavePlayerDataResult】function to inform the engine of the archive status 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| idx | int | Engine callback function id, the 【SavePlayerDataResult】function will use this id | 
| playerKey | str | Player uid string, the player's unique identifier | 
- Return value 


    none
