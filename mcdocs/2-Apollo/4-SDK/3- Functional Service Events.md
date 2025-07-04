--- 
sidebarDepth: 1 
--- 

# <span id="3-Functional Service Event"></span>3-Functional Service Event 

Event definition. 

<span id="Server"></span> 
## Server 

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

Triggered when lobby/game/proxy disconnects 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Server id | 
- Return value 

None 
<span id="UpdateServerStatusEvent"></span> 
### UpdateServerStatusEvent 

- Description 

Triggered when lobby/game/proxy status changes 


- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dict type, key: str, server id string, value: str, server status string. The server status is as follows: '1' | ready state, '2' | stopped state, '3' ready state. The server is available only when the server status is '1', and the server is unavailable in other states. | 
- Return value 

None 
- Example 

```python 
class TestService(ServiceSystem): 
def __init__(self, namespace, systemName): 
ServiceSystem.__init__(self, namespace, systemName) 
self.ListenForEvent( 
serviceApi.GetEngineNamespace(), 
serviceApi.GetEngineSystemName(), 
"UpdateServerStatusEvent", 
self, 
self.OnUpdateServerStatusEvent) 
def OnUpdateServerStatusEvent(self, args): 
print args 
# An example of the result: {'1000000':'1', '2000000':'3'} 
# Meaning: The server with server id 1000000 is running normally, and the server with server id 2000000 is in the ready state. 
``` 
<span id="Configuration"></span> 
## Configuration 

<span id="NetGameCommonConfChangeEvent"></span> 
### NetGameCommonConfChangeEvent 

- Description 

Triggered when the server configuration changes, including: adding or deleting a server; server-related configuration changes; log level changes 

- Return value 

None 
