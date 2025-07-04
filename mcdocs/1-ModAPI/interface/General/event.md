--- 
sidebarDepth: 1 
--- 
# Events 

## BroadcastEvent 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.system.baseSystem.BaseSystem 

- Description 

Local broadcast events. Events broadcast by the client system can only be listened to by the client system. Events broadcast by the server system can only be listened to by the server system. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | Event name | 
| eventData | dict | Event parameter, usually the return value of CreateEventData | 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def BroadCastEventTest(self, args): 
self.BroadcastEvent("bulletShootEvent", args) 
``` 

## BroadcastToAllClient 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.system.serverSystem.ServerSystem 

- Description 

The server broadcasts events to all clients 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | Event name | 
| eventData | dict | Event parameter, usually the return value of CreateEventData | 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def BroadCastEventTest(self, args): 
self.BroadcastToAllClient("bulletShootEvent", args) 

``` 

## CreateEventData 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.system.baseSystem.BaseSystem 

- Description 

Create custom event data, eventData is used to send events. The created eventData can be understood as a dict, which can be nested with dict, list and basic data types, but does not support tuple 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Event data | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def shoot(self): 
shootData = self.CreateEventData()

shootData["id"] = self.mPlayerId 
# Send an event to the client, passing a playerId 
self.NotifyToClient('-12345678910','BulletHit', shootData) 
``` 

## GetEngineNamespace 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Get the namespace of the engine event. When listening to engine events, namespace passes the namespace returned by the interface 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Engine namespace | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), ‘AddServerPlayerEvent’, self, self.OnPlayerAdd) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 


Get the namespace of the engine event. When listening to the engine event, namespace passes the namespace returned by the interface 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Engine namespace | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
ClientSystem = clientApi.GetClientSystemCls() 
class FpsClientSystem(ClientSystem): 
def __init__(self, namespace, systemName): 
ClientSystem.__init__(self, namespace, systemName) 
self.ListenForEvent(clientApi.GetEngineNamespace(), clientApi.GetEngineSystemName(), 'UiInitFinished', self, self.OnUIInitFinished) 
``` 

## GetEngineSystemName 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Get the engine system name. When monitoring engine events, systemName passes the systemName returned by this interface 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Engine systemName | 

- Example 


```python
import mod.server.extraServerApi as serverApi
ServerSystem = serverApi.GetServerSystemCls()
class FpsServerSystem(ServerSystem):
    def __init__(self, namespace, systemName):
        ServerSystem.__init__(self, namespace, systemName)
        self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), ‘AddServerPlayerEvent’, self, self.OnPlayerAdd)
```



### Client interface

<span id="c0"></span>
method in mod.client.extraClientApi

- describe

    Get the engine system name. When listening to engine events, systemName passes the systemName returned by the interface 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Engine systemName | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
ClientSystem = clientApi.GetClientSystemCls() 
class FpsClientSystem(ClientSystem): 
def __init__(self, namespace, systemName): 
ClientSystem.__init__(self, namespace, systemName) 
self.ListenForEvent(clientApi.GetEngineNamespace(), clientApi.GetEngineSystemName(), 'UiInitFinished', self, self.OnUIInitFinished) 
``` 

## ListenForEvent 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.system.baseSystem.BaseSystem 

- Description


Register to listen to events thrown by a certain system. If listening to engine events, namespace and systemName are GetEngineNamespace() and GetEngineSystemName() respectively. For detailed event data of each event, please refer to the content under the "Event" category. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| namespace | str | The namespace of the source system of the monitored event | 
| systemName | str | The systemName of the source system of the monitored event | 
| eventName | str | Event name | 
| instance | any | The instance of the class to which the callback function belongs | 
| func | function | Callback function | 
| priority | int | The priority of this callback function. The default value is 0. The larger the value, the higher the priority of the execution, up to 10. | 

- Return value 

None 

- Notes 
- The callback parameter of the client system event monitored by the server system will have a key called "__id__", and the value is the player id of the corresponding client 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def ListenEvent(self): 
# Listened for the engine event 'ServerChatEvent' 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), 'ServerChatEvent', self, self.OnServerChat) 
# Listen for client system events 
self.ListenForEvent("MyFpsMod", "FpsClientSystem", "MyEvent", self, self.OnMyEvent) 

def OnServerChat(self, args): 
print 'OnServerChat', args

    def OnMyEvent(self, args):
        print 'OnMyEvent', args['__id__'], args
```



## NotifyToClient

<span style="display:inline;color:#ff5555">Server</span>

method in mod.server.system.serverSystem.ServerSystem

- describe


The server sends an event to the specified client 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| targetId | str | The ID corresponding to the client, usually the player ID | 
| eventName | str | Event name | 
| eventData | dict | Event parameters, usually the return value of CreateEventData | 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def NotifyToClientTest(self, args): 
self.NotifyToClient('-1234567890',"bulletShootEvent", args) 
``` 

## NotifyToMultiClients 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.system.serverSystem.ServerSystem 

- Description 

Version 2.0 is only available in Apollo. The server sends events to a specified batch of clients 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| targetIdList | list(str) | The playerId list corresponding to the client. PlayerId is the entityId of the player | 
| eventName | str | Event name | 
| eventData | dict | Event parameters, generally using the return value of CreateEventData | 

- Return value 

None 

- Example 


```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def NotifyToClientTest(self, args): 
self.NotifyToMultiClients(['-1234567890', '-321654987'],"bulletShootEvent", args) 
``` 

## NotifyToServer 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.system.clientSystem.ClientSystem 

- Description 

The client sends an event to the server 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| eventName | str | event name | 
| eventData | dict | event parameters, usually the return value of CreateEventData | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
ClientSystem = clientApi.GetClientSystemCls() 
class FpsClientSystem(ClientSystem): 
def NotifyToServerTest(self, args): 
self.NotifyToServer("bulletShootEvent", args) 
``` 

## UnListenAllEvents 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.system.baseSystem.BaseSystem 

- Description


Unregister to listen to all events thrown by a certain system, that is, no longer listen. 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def ListenEvent(self): 
# The server script customizes 1 event 
self.DefineEvent('BulletHit') 
# The server script listens to 1 engine event 'ServerChatEvent' 
# For detailed event data of each event, please refer to the "MODSDK Documentation" 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), 'ServerChatEvent', self, self.OnServerChat) 
def UnListenEvent(self): 
# Cancel the customized event 
self.UnDefineEvent('BulletHit') 
# Cancel the monitored system event 
self.UnListenAllEvents() 
``` 

## UnListenForEvent 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

method in mod.common.system.baseSystem.BaseSystem 

- Description 

Unregister to listen to events thrown by a certain system, that is, no longer listen. If it is an engine event, namespace and systemName are [GetEngineNamespace](#getenginenamespace) and [GetEngineSystemName](#getenginesystemname) respectively. Corresponds to ListenForEvent. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| namespace | str | The namespace of the source system of the monitored event | 
| systemName | str | The systemName of the source system of the monitored event | 
| eventName | str | Event name | 
| instance | any | The instance of the class to which the callback function belongs |

| func | function | callback function | 
| priority | int | The priority of this callback function. The default value is 0. The larger the value, the higher the priority of the callback function. | 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def ListenEvent(self): 
# The server-side script customizes 1 event 
self.DefineEvent('BulletHit') 
# The server-side script listens to 1 engine event 'ServerChatEvent' 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), 'ServerChatEvent', self, self.OnServerChat) 
def UnListenEvent(self): 
# Cancel the customized event 
self.UnDefineEvent('BulletHit') 
# Cancel the system event being listened 
self.UnListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), 'ServerChatEvent', self, self.OnServerChat)
```