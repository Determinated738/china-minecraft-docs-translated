--- 
sidebarDepth: 1 
--- 

# <span id="2-Control Server Event"></span>2-Control Server Event 

Event definition. 

<span id="Server"></span> 
## Server 

<span id="ResetGamesBeginEvent"></span> 
### ResetGamesBeginEvent 

- Description 

Start resetting lobby/game events. For details, please refer to API【ResetServer】 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Server id | 
- Return value 

None 
<span id="ResetGamesEndEvent"></span> 
### ResetGamesEndEvent 

- Description 

Reset lobby/game end events. This event only indicates that the reset is completed, but the server may not have completed initialization. For details, please refer to the API [ResetServer] 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Server id | 
| bSuccess | bool | Whether the reset is successful. true means the reset is successful, otherwise it means failure | 
- Return value 

None 
<span id="RollingCloseServersEndEvent"></span> 
### RollingCloseServersEndEvent 

- Description 

Use RollingCloseServersEndEvent to roll the server shutdown end event. 


- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| request | str | The request parameter for rolling shutdown, which is a string in json format and contains the following attributes: serverlist, serverIds, apolloid, apollo_key | 
| response | str | The return parameter for rolling shutdown, which is a string in json format and contains the following attributes: code error code, message error information, entity removed server information, where the fields are the same as RollingUpdateServersEndEvent | 
| suc | bool | Whether the rolling shutdown is successful | 
- Return value 

None 
<span id="RollingUpdateServersEndEvent"></span> 
### RollingUpdateServersEndEvent 

- Description 

Use RollingUpdateServers to update the server end event. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| request | str | Request parameter for rolling update, a string in json format, containing the following attributes: app_version, ip, server_type, add_num, apolloid, apollo_key | 
| response | str | Return parameter for rolling update, a string in json format, containing the following attributes: code error code, message error information, server information added or removed by entity | 
| suc | bool | Whether the rolling update is successful | 
- Return value 

None 
- Remarks 

entity is a list (dict), each element contains the following fields, corresponding to the server configuration of mcstudio: 
| Field | Type | Description | 
| --- | --- | --- | 
| serverid | int | server id | 
| ip | str | server ip | 
| mods | str | server mod list | 
| app_type | str | game/lobby/proxy | 
| type | str | server type | 
| save | bool | whether to save the map | 
| save_id | int | use the map | 
| gb | int | single process memory | 


<span id="ServerConnectedEvent"></span> 
### ServerConnectedEvent 

- Description 

Triggered when lobby/game/proxy successfully establishes a connection 

- Parameters


    | Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Server id | 
| protocolVersion | int | Protocol version number | 
- Return value 

None 
<span id="ServerDisconnectEvent"></span> 
### ServerDisconnectEvent 

- Description 

Triggered when lobby/game/proxy is disconnected 

- Parameter 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Server id | 
- Return value 

None 
<span id="Configuration"></span> 
## Configuration 

<span id="NetGameCommonConfChangeEvent"></span> 
### NetGameCommonConfChangeEvent 

- Description 

Triggered when public configuration changes, including: adding or deleting servers; server-related configuration changes; log level changes 

- Return value 

None 
<span id="Player"></span> 
## Player 

<span id="PlayerLoginServerEvent"></span> 
### PlayerLoginServerEvent 

- Description 

Player login event, at which time the master starts to assign lobby/game to the player, and can distinguish whether the player is logging in or switching servers 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- |

| serverId | int | The server id that the client is about to log in to | 
| uid | int/long | The uid of the player | 
| protocolVersion | int | Protocol version number | 
| isTransfer | bool | True: Switch server, False: Log in | 
| isReconnect | bool | True: Reconnect after disconnection, False: Normal login | 
| isPeUser | bool | True: The player logs in from the mobile terminal, False: The player logs in from the PC terminal | 
- Return value 

None 
<span id="PlayerLogoutServerEvent"></span> 
### PlayerLogoutServerEvent 

- Description 

Triggered when the player logs out. The player will also trigger this event when he exits the lobby/game during the process of downloading the behavior pack. It can be used to distinguish whether the player logs out or switches servers. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Proxy server ID that the client is connected to | 
| uid | int/long | Player's uid | 
| isTransfer | bool | True: switch server, False: log out | 
- Return value 

None 
<span id="PlayerTransferServerEvent"></span> 
### PlayerTransferServerEvent 

- Description 

Player starts server switch event. At this time, the master starts to prepare the server for the player. The player has not yet completed the server switch, and the subsequent server switch may fail. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Proxy server ID that the client is connected to | 
| uid | int/long | Player's uid | 
| targetServerId | int | Target lobby/game server ID | 
| targetServerType | str | Target server type, such as "game" or "lobby". If targetServerId is 0, a server of the target type will be randomly selected as the target server | 
| protocolVersion | int | protocol version number | 
| transferParam | str | Server switching parameters. The server switching parameters passed in by calling [TransferToOtherServer] or [TransferToOtherServerById]. | 
- Return value 

None 
