--- 
sidebarDepth: 1 
--- 

# <span id="5-Functional Service API"></span>5-Functional Service API 

Here are some interfaces of Service 

<span id="Configuration"></span> 
### Configuration 

<span id="GetCommonConfig"></span> 
#### GetCommonConfig 

- Description 

Get the common configuration of the server, including the configuration of all servers and db, see the notes for details 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| dict | Configuration content | 
- Notes 

The example of the common configuration of the server is as follows, only the core configuration information is shown: 
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
import service.netgameApi as netServiceApi 
conf = netServiceApi.GetCommonConfig() 
serverlist = conf['serverlist'] #Get serverlist configuration 
serverlist = conf['log_debug_level'] #Get log level configuration 
``` 
<span id="GetServerId"></span> 
#### GetServerId 

- Description 

Get server id, server id corresponds to serverid in public configuration, for public configuration, see [GetCommonConfig](#GetCommonConfig) Remarks 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | Server id | 
- Example 

```python 
import service.netgameApi as netServiceApi 
serverId = netServiceApi.GetServerId() 
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
import service.netgameApi as netServiceApi 
#An example returned: ["neteaseAnnounce", "neteaseAuth", "neteaseShop"] 
mods = netServiceApi.GetServerLoadedModsById(4000) 
 ```
<span id="GetServerLoadedModsByType"></span>

#### GetServerLoadedModsByType 

- Description 

Get the server loaded mod list according to the server type. If the same type of server is configured with different mods, one of the corresponding mod lists will be returned. 

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
import service.netgameApi as netServiceApi 
#An example of return: ["neteaseAnnounce", "neteaseAuth", "neteaseShop"] 
mods = netServiceApi.GetServerLoadedModsByType("survivalGame") 
``` 
<span id="GetServiceConfig"></span> 
#### GetServiceConfig 

- Description 

Get service configuration, which corresponds to the configuration of the corresponding service under servicelist in the common configuration. For common configuration, see [GetCommonConfig](#GetCommonConfig) Notes 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| dict | Configuration content | 
- Example 

```python 
import service.netgameApi as netServiceApi 
serviceConf = netServiceApi.GetServiceConfig() 
print serviceConf 
# The result example is as follows: 
# { 
# "app_type": "service", 
# "app_version": "1.15.0.release20191128", 
# "http_port": 8520, 
# "ip": "127.0.0.1", 
# "mods": "service", 
# "module_names": [ 
# "netease_salog_0",

# "netease_salog_1", 
# "netease_uniqueid", 
# "netease_stats_log_0", 
# "netease_stats_log_1", 
# "netease_stats_monitor" 
# ], 
# "serverid": 11, 
# "type": "service" 
# } 
``` 
<span id="General"></span> 
### General 

<span id="StartRecordEvent"></span> 
#### StartRecordEvent 

- Description 

Start the script event packet receiving and sending statistics between the lobby server/game server and the function server. After starting, call [StopRecordEvent()](#StopRecordEvent) to obtain the statistics of the engine packet receiving and sending between the two function calls. 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Execution result | 
- Example 

```python 
import service.netgameApi as netServiceApi 
suc = netServiceApi.StartRecordEvent() 
# Then call StopRecordEvent through a timer or other triggering method 
result = netServiceApi.StopRecordEvent() 
# The value corresponding to sendEvent saves the event statistics that the function server actively sends to the lobby server/game server and even the client 
for eventName, data in result["sendEvent"].iteritems(): 
print "sendEvent event[{}] send={} sendSize={}".format(eventName, data["send_num"], data["send_size"]) 
# The value corresponding to sendRequest saves the event sent by the function server to other function servers, as well as the event of the corresponding function server returning the result 
for eventName, data in result["sendRequest"].iteritems(): 
print "sendRequest event[{}] request={} requestSize={} response={} responseSize={}".format(eventName, data["request_num"], data["request_size"], data["response_num"], data["response_size"]) 
# The value corresponding to recvRequest stores the request received by the function service from other servers, as well as the corresponding return result event 
for eventName, data in result["recvRequest"].iteritems(): 
print "recvRequest event[{}] request={} requestSize={} response={} responseSize={}".format(eventName, data["request_num"], data["request_size"], data["response_num"], data["response_size"]) 
``` 
<span id="StopRecordEvent"></span> 
#### StopRecordEvent 

- Description 

Stop the script event packet sending and receiving statistics between the lobby server/game server and the function server and output the results. Used in conjunction with [StartRecordEvent()](#StartRecordEvent), the output result is a dictionary. See the example for details. 

- Return value


| Data type | Description | 
| :--- | :--- | 
| dict | Packet information, see the example for details. If StartRecordEvent has not been called, it will return None | 
- Example 

```python 
import service.netgameApi as netServiceApi 
suc = netServiceApi.StartRecordEvent() 
# Then call StopRecordEvent through a timer or other triggering method 
result = netServiceApi.StopRecordEvent() 
# The value corresponding to sendEvent saves the event statistics that the function server actively sends to the lobby server/game server and even the client 
for eventName, data in result["sendEvent"].iteritems(): 
print "sendEvent event[{}] send={} sendSize={}".format(eventName, data["send_num"], data["send_size"]) 
# The value corresponding to sendRequest stores the event sent by the function service to other function services, as well as the event returned by the corresponding function service. 
for eventName, data in result["sendRequest"].iteritems(): 
print "sendRequest event[{}] request={} requestSize={} response={} responseSize={}".format(eventName, data["request_num"], data["request_size"], data["response_num"], data["response_size"]) 
# The value corresponding to recvRequest stores the request received by the function service from other servers, as well as the event returned by the corresponding result. 
for eventName, data in result["recvRequest"].iteritems(): 
print "recvRequest event[{}] request={} requestSize={} response={} responseSize={}".format(eventName, data["request_num"], data["request_size"], data["response_num"], data["response_size"]) 
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
| callback | function | Instance function that responds to HTTP requests. There are two parameters. The first parameter, clientId, is of type int. It is the unique identifier of the requester and is used to return the request processing result. The second parameter, requestData, is of type dict and contains the parameters of the HTTP request (requestBody) | 
- Return value 

None 
- Remarks 

When multiple game servers/function servers have registered the same URL, the request will be broadcasted to all servers that have registered this URL by default, and the return result will also integrate the return results of all servers. 

By adding the opUid [type is int] parameter in the request, you can specify that this request is only forwarded to the server with the corresponding uid currently online. 

By adding the opServerIds [type is list(int)] parameter in the request, you can specify that this request is only forwarded to the server whose server ID is in the opServerIds list. 

By adding the opServerType [type is str] parameter in the request, you can specify that this request is only forwarded to the server with the server type of opServerType. 


When the url registered by this API is the same as the url registered by [masterHttp.RegisterMasterHttp], only one of them can be retained. The statement executed later will replace the callback of the statement executed earlier. 


- Example 

```python 
import service.netgameApi as serviceNetgameApi 
class ServiceApiSys(ServiceSystem): 
def __init__(self,namespace,systemName): 
ServiceSystem.__init__(self, namespace, systemName) 
serviceNetgameApi.RegisterOpCommand("/api/game-url-test1", self.OnServiceUrlTest1) 

def OnServiceUrlTest1(self, clientId, requestData): 
print "OnServiceUrlTest1", clientId, requestData 
# Return processing results 
serviceNetgameApi.ResponseOpCommandSuccess(clientId, {"result":"exec success"}) 
``` 
<span id="ResponseOpCommandFail"></span> 
#### ResponseOpCommandFail 

- Description 

Send HTTP failed Response, supports asynchronous return, specifies the clientId passed in the request when returning 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| clientId | int | Request unique ID, identifies the HTTP request. | 
| code | int | Request failure reason code | 
| message | str | Request failure reason text | 
- Return value 

None 
- Example 

```python 
import service.netgameApi as serviceNetgameApi 
class ServiceApiSys(ServiceSystem): 
def __init__(self,namespace,systemName): 
ServiceSystem.__init__(self, namespace, systemName) 
serviceNetgameApi.RegisterOpCommand("/api/game-url-test3", self.OnServiceUrlTest3) 

def OnServiceUrlTest3(self, clientId, requestData): 
print "OnServiceUrlTest3", clientId, requestData 
# Return processing result 
lobbyGameApi.ResponseOpCommandFail(clientId, 1, "exec failed") 
``` 
<span id="ResponseOpCommandSuccess"></span>
#### ResponseOpCommandSuccess


- Description 

Sends a successful HTTP Response, supports asynchronous return, and specifies the clientId passed in the request when returning 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| clientId | int | Request unique ID, identifying HTTP request. | 
| entity | dict | Content to be returned in the request, you can customize the meaning of key/value | 
- Return value 

None 
- Example 

```python 
import service.netgameApi as serviceNetgameApi 
class ServiceApiSys(ServiceSystem): 
def __init__(self,namespace,systemName): 
ServiceSystem.__init__(self, namespace, systemName) 
serviceNetgameApi.RegisterOpCommand("/api/game-url-test1", self.OnServiceUrlTest1) 

def OnServiceUrlTest1(self, clientId, requestData): 
print "OnServiceUrlTest1", clientId, requestData 
# Return processing results 
serviceNetgameApi.ResponseOpCommandSuccess(clientId, {"result":"exec success"}) 
``` 
<span id="UnRegisterOpCommand"></span> 
#### UnRegisterOpCommand 

- Description 

Unregister a registered HTTP interface 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| url | str | Interface url | 
- Return value 

None 
- Example 

```python 
import service.netgameApi as serviceNetgameApi 
class ServiceApiSys(ServiceSystem): 
def __init__(self,namespace,systemName): 
ServiceSystem.__init__(self, namespace, systemName)

serviceNetgameApi.RegisterOpCommand("/api/game-url-test1", self.OnServiceUrlTest1) 

def Destroy(self): 
serviceNetgameApi.UnRegisterOpCommand("/api/game-url-test1") 

def OnServiceUrlTest1(self, clientId, requestData): 
print "OnServiceUrlTest1", clientId, requestData 
# Return processing results 
serviceNetgameApi.ResponseOpCommandSuccess(clientId, {"result":"exec success"}) 
``` 
Here are some HTTP interfaces of the service 

<span id="HTTP server"></span> 
### HTTP server 

<span id="RegisterServiceHttp"></span> 
#### RegisterServiceHttp 

- Description 

Register a new HTTP interface 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| url | string | interface url | 
| binder | instance | Instance of HTTP request response | 
| func | function | Instance function of HTTP request response | 
- Return value 

None 
- Example 

```python 
import service.serviceHttp as serviceHttp 
class HttpHandler(object): 
def __init__(self): 
# Set interface URI and callback 
url = '/kick-user' 
func = self.HttpTest 
# Register 
serviceHttp.RegisterServiceHttp(url, self, func) 
def HttpTest(self, clientId, requestBody): 
# clientId identifies the unique id of the request, which must be carried in send_http_response 
# requestBody is the post body content. If it is in json format, you can load the content in the following way. 
# import ujson as json 
# request = json.loads(requestBody) 
# Return the processing result. The code must be 1 to indicate successful processing, otherwise the master will consider the request failed when requesting. 
response = '{"code":1,"message":"ok"}'

serviceHttp.SendHttpResponse(clientId, response) 
``` 
<span id="SendHttpRequestToMaster"></span> 
#### SendHttpRequestToMaster 

- Description 

Send http request to master 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| requestUrl | string | Request url, for example "/test-reqeust" | 
| message | string | HTTP post body, a json string | 
- Return value 

None 
- Example 

```python 
import service.serviceHttp as serviceHttp 
params = { 
"message":"content", 
"code":1 
} 
url = "/test-reqeust" 
serviceHttp.SendHttpRequestToMaster(url, json.dumps(params)) 
``` 
<span id="SendHttpResponse"></span> 
#### SendHttpResponse 

- Description 

Send HTTP Response. Supports asynchronous return. Specify input clientId when returning. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| clientId | int | Request unique ID, identify HTTP request | 
| message | string | Content of HTTP Response | 
- Return value 

None 
- Example 

```python 
import service.serviceHttp as serviceHttp 
class HttpHandler(object):

def __init__(self): 
# Set interface URI and callback 
url = '/kick-user' 
func = self.HttpTest 
# Register 
serviceHttp.RegisterServiceHttp(url, self, func) 
def HttpTest(self, clientId, requestBody): 
# clientId identifies the unique id of the request, which must be carried in send_http_response 
# requestBody is the post body content. If it is in json format, you can load the content in the following way. 
# import ujson as json 
# request = json.loads(requestBody) 
# return processing result 
response = '{"code":0,"message":"ok"}' 
serviceHttp.SendHttpResponse(clientId, response) 
``` 
Here are some management interfaces of service 

<span id="server"></span> 
### server 

<span id="ResetServer"></span> 
#### ResetServer 

- Description 

Reset server 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | lobby/game server id | 
- Return value 

None 
- Remarks 


Note that for the survival server, if archive A is used, archive A will still be used after the reset, and the map will not be saved during the reset process. 


If you need to reset the game server GameA, use the following method: make sure the player exits the corresponding GameA before resetting, and do not allow the player to enter GameA during the reset process. After GameA is reset, GameA can send a message to inform the master or service that GameA is ready, and then the player can enter GameA. 


- Example 

```python 
import service.serverManager as serverManager 
serverManager.ResetServer(4000) 
```

<span id="Server Management"></span> 
### Server Management 

<span id="GetServerIdsByServerType"></span> 
#### GetServerIdsByServerType 

- Description 

Get a list of server ids by type 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverType | str | Server type | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| list(int) | Server id list. If the server type does not exist, an empty list is returned | 
- Example 

```python 
import service.serverManager as serverManager 
#An example returned: [4000, 4001] 
serverIds = serverManager.GetServerIdsByServerType("lobby") 
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
import service.serverManager as serverManager 
version = serverManager.GetServerProtocolVersion(6000) 
```

<span id="GetServerType"></span> 
#### GetServerType 

- Description 

Get server type 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | master/service/lobby/game server id | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| str | Server type string. If the server does not exist, an empty string is returned | 
- Example 

```python 
import service.serverManager as serverManager 
serverType = serverManager.GetServerType(6000) 
``` 
<span id="GetServersStatus"></span> 
#### GetServersStatus 

- Description 

Get the status of all lobby/game servers. Only status 1 indicates that the server is providing normal services, and other statuses indicate that the server cannot provide external services. 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| dict | key: int, server id, value: int server status. The server status is as follows: <br/>1: Normal status <br/>2: Rolling update shutdown status, the server will be removed from the shelves soon <br/>3: Rolling update new server status, the server will be converted to status 1 when it is ready <br/>4: The server has been put on the shelves, but the connection with the service has not been established (it may be caused by server crash, reset or shutdown, etc.), and it will be converted to status 1 after the connection is established | 
- Example 

```python 
import service.serverManager as serverManager 
statusDict = serverManager.GetServersStatus() 
``` 
<span id="IsConnectedServer"></span> 
#### IsConnectedServer 

- Description 

Whether the service has established a connection with the lobby/game/proxy 

- Parameters 


| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| serverId | int | Server id | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | True, connection established; False, no connection established | 
- Example 

```python 
import service.serverManager as serverManager 
bConnect = serverManager.IsConnectedServer(4000) 
``` 
