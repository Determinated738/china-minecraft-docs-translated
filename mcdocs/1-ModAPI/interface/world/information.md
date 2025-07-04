--- 
sidebarDepth: 1 
--- 
# Message 

## NotifyOneMessage 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.msgCompServer.MsgComponentServer 

- Description 

Send a chat message to a specified player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Specified player id | 
| msg | str | Message content | 
| color | str | Color style code string, refer to wiki [style code] (https://minecraft-zh.gamepedia.com/%E6%A0%B7%E5%BC%8F%E4%BB%A3%E7%A0%81), default is white | 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateMsg(entityId) 
comp.NotifyOneMessage(playerId, "test", "§c") 
``` 

## SendMsg 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.msgCompServer.MsgComponentServer 

- Description 

Simulates a player sending a chat message to everyone 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| name | str | The name of the sender player | 
| msg | str | Message content | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- The name parameter needs to set the player's name (which can be obtained through the name component). If the set player name does not exist, a random player will be found to send the message 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateMsg(entityId) 
comp.SendMsg("playerName","test") 
``` 

## SendMsgToPlayer 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.msgCompServer.MsgComponentServer 

- Description 

Simulates a player sending a chat message to another player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fromEntityId | str | Sender player ID | 
| toEntityId | str | Receiver player ID | 
| msg | str | Message content | 

- Return value 

None 

- Example 

```python 
comp = serverApi.GetEngineCompFactory().CreateMsg(entityId) 
comp.SendMsgToPlayer(fromEntityId, toEntityId, "test")

``` 

## SetLeftCornerNotify 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.textNotifyCompClient.TextNotifyComponet 

- Description 

Set the upper left corner notification information of the client 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| textMsg | str | Notification content | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextNotifyClient(levelId) 
comp.SetLeftCornerNotify("Get ready") 
``` 

## SetNotifyMsg 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Set message notification 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| msg | str | message content | 
| color | str | Color obtained using GenerateColor interface, default is white | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.SetNotifyMsg("Message notification", serverApi.GenerateColor('BLUE')) 
``` 

## SetOnePopupNotice 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Pop up a popup notification above a specific player's inventory, below the tip message. For this function, it is recommended that the client use the corresponding interface SetPopupNotice of the game component. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Specific player ID | 
| message | str | Message content. You can add extraServerApi.GenerateColor("RED") characters to the front of the message to set the color. For specific reference examples | 
| subtitle | str | Message subtitle content. The effect is the same as message. You can also set the color. The position is above the message | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(playerId) 
# Change the playerId variable to the specific player ID 
comp.SetOnePopupNotice(playerId, serverApi.GenerateColor("RED") + "Message notification", "Message subtitle")

``` 

## SetOneTipMessage 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Pop up a tip type notification above the inventory of a specific player, located above the popup type notification. This function is more recommended to use the corresponding interface SetTipMessage of the game component on the client 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Specific player ID | 
| message | str | Message content, you can add extraServerApi.GenerateColor("RED") characters before the message to set the color, refer to the sample for details | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(playerId) 
# Change the playerId variable to a specific player ID 
comp.SetOneTipMessage(playerId, serverApi.GenerateColor("RED") + "tip prompt") 
``` 

## SetPopupNotice 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

A pop-up notification appears above all players' inventories, below the tip message.


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| message | str | Message content. You can add extraServerApi.GenerateColor("RED") characters before the message to set the color. For details, refer to the sample | 
| subtitle | str | Message subtitle content. The effect is the same as message. You can also set the color. The position is above the message | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.SetPopupNotice(serverApi.GenerateColor("RED") + "Message notification", "Message subtitle") 
``` 
### Client interface 
<span id="c0"></span> 
method in mod.client.component.gameCompClient.GameComponentClient 
- Description 

Pop up a popup notification above the local player's inventory, below the tip message 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| message | str | Message content, you can add extraClientApi.GenerateColor("RED") characters before the message to set the color, refer to the sample for details | 
| subtitle | str | Message subtitle content, the effect is the same as message, the color can also be set, the position is above the message | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi

comp = clientApi.GetEngineCompFactory().CreateGame(entityId) 
comp.SetPopupNotice(clientApi.GenerateColor("RED") + "Message notification", "Message subtitle") 
``` 

## SetTipMessage 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Pop up a tip type notification above all player inventory, located above the popup type notification 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| message | str | Message content, you can add extraServerApi.GenerateColor("RED") characters before the message to set the color, refer to the sample for details | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.SetTipMessage(serverApi.GenerateColor("RED") + "tip提示") 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.gameCompClient.GameComponentClient 

- Description 

A tip type notification pops up above the local player's inventory, located above the pop-up type notification 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| message | str | Message content, you can add extraClientApi.GenerateColor("RED") characters before the message to set the color, refer to the sample for details | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateGame(entityId) 
comp.SetTipMessage(clientApi.GenerateColor("RED") + "tip提示") 
``` 

