# Server Communication 

Information exchange between servers is a very important part of server development. This section will explain some communication-related interfaces. 

All interfaces used in this section can be found in the developer documentation. 

Address: http://mc.163.com/dev/mcmanual/mc-dev/mcdocs/2-Apollo/4-SDK/8-%E6%9C%8D%E5%8A%A1%E5%99%A8%E9%80%9A%E4%BF%A1.html 

### Example 

#### Requirements 

Make a daily sign-in system 

#### Communication process 

- After the player logs in, Game/Lobby sends the player's uid to Service. After receiving the request, Service queries whether the player has logged in today and returns the data to Game/Lobby. 
- After receiving the data, Game/Lobby sends an event to open the UI to the Client, and the data is sent as a parameter. 
- The Client receives the event to open the UI, parses the parameters, and calls ScreenNode to create the UI, which is displayed on the player's client. 
- The player clicks the sign-in button on the UI, and the Client sends a sign-in event to Game/Lobby. 
- Game/Lobby receives the sign-in event and sends the player sign-in event to the Service. 
- The Service receives the request, confirms that the player has not signed in that day, updates the sign-in status, and responds to Game/Lobby whether the sign-in is successful. 
- After receiving the request, Game/Lobby calls the callback to determine whether the sign-in is successful based on the parameters. If successful, the sign-in reward is sent to the player. 

## Client UI 

The sample code related to the client UI will intercept part of the code of the neteaseDaily plug-in for example. You can download it yourself and find the corresponding code in the plug-in for learning. 

The client first needs to use the following code to listen to the open interface request sent by Game/Lobby during initialization. 

Then provide the event parameters to ScreenNode for relevant analysis. 

dailyClientSystem.py 

```python 
# -*- coding: utf-8 -*- 

import neteaseDailyScript.dailyConst as dailyConst 
import client.extraClientApi as clientApi 

ClientSystem = clientApi.GetClientSystemCls() 

class DailyClientSystem(ClientSystem): 
""" 
The client class of this mod 
Communicate with the server class 
Display the status of daily login rewards 
""" 


	def __init__(self, namespace, systemName):
		ClientSystem.__init__(self, namespace, systemName)
		self.mPlayerId = clientApi.GetLocalPlayerId()
		self.mDailyUINode = None

		self.ListenForEvent(clientApi.GetEngineNamespace(), clientApi.GetEngineSystemName(), dailyConst.UiInitFinishedEvent, self, self.OnUiInitFinished)
		self.ListenForEvent(dailyConst.ModName, dailyConst.ServerSystemName, dailyConst.DisplayDailyRewardEvent, self, self.OnDisplayDailyReward) # The server calls the interface to open the daily login reward interface
		self.ListenForEvent(dailyConst.ModName, dailyConst.ServerSystemName, dailyConst.PlayerRecvEvent, self, self.OnPlayerRecv) # After the player receives the reward normally, update the daily login reward interface 

def Destroy(self): 
self.mDailyUINode = None 
self.UnListenForEvent(clientApi.GetEngineNamespace(), clientApi.GetEngineSystemName(), dailyConst.UiInitFinishedEvent, self, self.OnUiInitFinished) 
self.UnListenForEvent(dailyConst.ModName, dailyConst.ServerSystemName, dailyConst.DisplayDailyRewardEvent, self, self.OnDisplayDailyReward) 
self.UnListenForEvent(dailyConst.ModName, dailyConst.ServerSystemName, dailyConst.PlayerRecvEvent, self, self.OnPlayerRecv) 

def OnUiInitFinished(self, *args): 
# Register UI For detailed explanation, refer to "UI API" 
clientApi.RegisterUI(dailyConst.ModName, dailyConst.dailyUIName, dailyConst.dailyUIClsPath, dailyConst.dailyUIScreenDef)
		# Create UI. For detailed explanation, please refer to "UI API"
		clientApi.CreateUI(dailyConst.ModName, dailyConst.dailyUIName, {"isHud": 1})
		self.mDailyUINode = clientApi.GetUI(dailyConst.ModName, dailyConst.dailyUIName)
		if self.mDailyUINode:
			self.mDailyUINode.InitScreen()
		else:
			print '==== %s ====' % 'create UI: %s failed' % dailyConst.dailyUIScreenDef

	def OnDisplayDailyReward(self, data):
		print 'OnDisplayDailyReward', data
		if self.mDailyUINode: self.mDailyUINode.open(data) 
#Receive a request from the server to open the client UI, call ScreenNode and transmit data data, open the interface 

def OnPlayerRecv(self, data): 
print 'OnPlayerRecv', data 
if self.mDailyUINode: 
self.mDailyUINode.refresh(data) 

``` 

In the UI logic code, write the relevant logic code for clicking the receive button. The code below is the most critical code to determine the receive and send the request to the server. 

As you can see, the most important thing is to use the ClientSystem#NotifyToServer function to transmit the request to the server. 

dailyClientUI.py 

```python 
def recv(self): 
print 'recv', self.m_valid_date 
clientApi.GetSystem(dailyConst.ModName, dailyConst.ClientSystemName).NotifyToServer( 
dailyConst.PlayerRecvEvent,

{'playerId': clientApi.GetLocalPlayerId(), 'valid': self.m_valid_date} # Pass the date sent by the server for verification, indicating that the daily login reward is collected on the same day 
) 
``` 

## Client and Game/Lobby Communication 

This communication interface is the same as the interface used for mod development, and readers should be familiar with this interface. 

Using this interface, messages can be sent bidirectionally between the client and the server. The specific usage is as follows. 

```python 
#Example of server sending message to client 
#client mod 
class testClient(ClientSystem): 
def __init__(self,namespace,systemName): 
ClientSystem.__init__(self, namespace, systemName) 
self.ListenForEvent('serverNamespace', 'serverSystem', 'PlayerJoinOKEvent', self, self.OnPlayerJoinOK) 
def OnPlayerJoinOK(self, args): 
#args result is: {'uid':123, 'name':'nickname'} 
print 'OnPlayerJoinOK', args 
#game/lobby mod 
class testServer(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 
def testNotifyClient(self): 
player = {} 
player['uid'] = 123 
                player['name'] = 'nickname'
                playerId = '456'
                self.NotifyToClient(playerId, "PlayerJoinOKEvent", player)
```

```python
#Example of client sending message to server
#client mod
class testClient(ClientSystem):
        def __init__(self,namespace,systemName):
                ClientSystem.__init__(self, namespace, systemName)
        def testNotifyServer(self):
                player = {}
                player['uid'] = 123
                player['name'] = 'nickname'
                self.NotifyToServer("PlayerJoinEvent", data)
#game/lobby mod
class testServer(ServerSystem):
        def __init__(self, namespace, systemName):
                ServerSystem.__init__(self, namespace, systemName)
                self.ListenForEvent('clientNamespace', 'clientSystem', 'PlayerJoinEvent', self, self.OnPlayerJoin)

def OnPlayerJoin(self, args): 
#args result is: {'uid':123, 'name':'nickname'} 
print 'OnPlayerJoin', args 
``` 

## Service and Service/Master communication 

This type of communication is usually used for data transmission between different server nodes. The specific usage is as follows. 

```python 
#service communication example with master. Service communication with service is similar to this, so I won't repeat it here 
#service mod 
class testService(ServiceSystem): 
def __init__(self,namespace,systemName): 
ServiceSystem.__init__(self, namespace, systemName) 
#Register service method. Note that an event can only be registered once, otherwise the subsequent listening function will overwrite the previous listening function 
self.RegisterRpcMethodForMod('PlayerJoinOKEvent', self.OnPlayerJoinOK) 
def OnPlayerJoinOK(self, serverId, callbackId, args): 
#args result is: {'uid':123, 'name':'nickname'} 
print 'OnPlayerJoinOK', args 
response = {} 
response['result'] = 1 
self.ResponseToServer(serverId, callbackId, response) 
#master mod 
class masterServer(MasterSystem): 
def __init__(self, namespace, systemName): 
MasterSystem.__init__(self, namespace, systemName) 
def OnCallback(self, suc, args): 
#If successful: suc=True, args= {'result' : 1} 
#If timeout, suc is False 
if not suc: 
print 'OnCallback timeout' 
return 
print 'OnCallback success', args 
def testNotifyService(self): 
player = {} 
player['uid'] = 123 
player['name'] = 'nickname' 
self.RequestToServiceMod("idv_service", "PlayerJoinOKEvent", data, self.OnCallback, 2) 
``` 
In the sample code above, three related interfaces are called. The following will explain the specific usage of these three interfaces.

### RegisterRpcMethodForMod 

The service interface is used to listen to the request sent by the master and pass the request parameters to the callback function. 

As shown in the code above, after receiving the **PlayerJoinOKEvent**, the service will trigger the **OnPlayerJoinOK** function. 

### ResponseToServer


The service interface is used to respond to the master's communication request. 

In the above code, after the service server receives the request and processes it, it will send the result of the successful operation back to the master server again, and call the master's callback function **OnCallback**. 

If the request is not completed within 2 seconds, it will be judged as timed out. 

The timeout seconds can be configured in the master function and can be adjusted according to your needs. 

### RequestToServiceMod 

The master interface is used to send data to the specified service server. 

The first parameter is module, and module_names needs to be configured in the service's mod.json in advance. 

There is nothing special to pay attention to for other parameters. You can refer to the official documentation to query the specific meaning of the relevant parameters. Link at the top of this page. 

## Service and Lobby/Game Communication 

The communication method between **Service and Lobby/Game** is basically the same as **Service and Service/Master Communication**. All of them use the three interfaces mentioned above: ```RegisterRpcMethodForMod```, ```ResponseToServer```, and ```RequestToServiceMod```. The demo is basically the same, and the code below is for reference. 

```python
#service communicates with game/lobby example
#service mod
class testService(ServiceSystem):
        def __init__(self,namespace,systemName):
                ServiceSystem.__init__(self, namespace, systemName)
                self.RegisterRpcMethodForMod("idv_service", 'PlayerJoinOKEvent', self.OnPlayerJoinOK)
        def OnPlayerJoinOK(self, serverId, callbackId, args):
                The result of #args is: {'uid':123, 'name':'nickname'}
                print 'OnPlayerJoinOK', args
#lobby mod
class lobbyServer(ServerSystem):
        def __init__(self, namespace, systemName):
                ServerSystem.__init__(self, namespace, systemName)
        def testNotifyService(self):
                player = {}
                player['uid'] = 123 
player['name'] = 'nickname' 
self.RequestToServiceMod("idv_service", "PlayerJoinOKEvent", args) 
``` 

In addition, there are more interfaces available for calling between Service and Lobby/Game. 

For details, please click <a href="../../../mcdocs/2-Apollo/4-SDK/8-服务器通讯.html#service和game/lobby通讯" rel="noopenner"> here </a> to view. 

