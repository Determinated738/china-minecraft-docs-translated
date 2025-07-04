--- 
sidebarDepth: 1 
--- 
# Online lobby 

# Index 

| Event | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [lobbyGoodBuySucServerEvent](Online lobby.md#lobbygoodbuysucserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when a player logs in to the online lobby server or purchases an item in the online lobby game. If the player logs in, the player client has already triggered the UiInitFinished event when the event is triggered | 
# Online lobby 

## lobbyGoodBuySucServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when a player logs in to the online lobby server or purchases an item in the online lobby game. If the player logs in, the UiInitFinished event has already been triggered by the player client when it is triggered 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eid | str | Entity ID of the player who purchased the item | 
| buyItem | bool | False when the player logs in, True when the player purchases the item | 

- Return value 

None 

