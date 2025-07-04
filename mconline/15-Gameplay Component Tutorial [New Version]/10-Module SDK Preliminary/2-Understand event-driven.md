--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Advanced 
time: 25 minutes 
--- 
# Understanding event-driven 

Next, we will use the definition of the server system of the TutorialMod demonstration module to understand what is an event-driven system. Let's take a look at the `tutorialServerSystem.py` file in the demonstration module. 

```python 
# -*- coding: utf-8 -*- 

# Get the module of the engine server API 
import mod.server.extraServerApi as serverApi 
# Get the base class of the engine server System. All Systems must inherit from ServerSystem to call related functions 
ServerSystem = serverApi.GetServerSystemCls() 
# Get the component factory to create components 
compFactory = serverApi.GetEngineCompFactory() 

# Server System class registered in modMain 
class TutorialServerSystem(ServerSystem): 

# ServerSystem initialization function 
def __init__(self, namespace, systemName): 
# First call the initialization function of the parent class 
super(TutorialServerSystem, self).__init__(namespace, systemName) 
print "===== TutorialServerSystem init =====" 
# Initially call the listener function to listen to events 
self.ListenEvent() 

# Listening function, used to define and listen to functions. Function names other than those emphasized are self-selected, including this function. 
def ListenEvent(self): 
# Listen to the engine event ServerChatEvent in the custom ServerSystem, the callback function is OnServerChat 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), "ServerChatEvent", self, self.OnServerChat) 
# Listen to the engine event ServerBlockUseEvent, the callback function is OnServerBlockUseEvent 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), "ServerBlockUseEvent", self, self.OnServerBlockUseEvent) 

# Anti-listening function, used for anti-listening events. It is a good programming habit to create and register in the code and destroy and anti-register accordingly. Don't rely on the engine to do these things. 
def UnListenEvent(self): 
self.UnListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), "ServerChatEvent", self, self.OnServerChat) 
self.UnListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), "ServerBlockUseEvent", self, self.OnServerBlockUseEvent) 

# Listen for the callback function of ServerBlockUseEvent 
def OnServerBlockUseEvent(self, args): 
# Replace sdkteam_test:block1 with the namespace and block name of your own custom block 
if args["blockName"] == "sdkteam_test:block1": 
# Call the interface for giving items, similar to OnServerChat 
playerId = args["playerId"] 
comp = compFactory.CreateItem(playerId)

# Fill in the name of the diamond sword here 
comp.SpawnItemToPlayerInv({"itemName": "minecraft:diamond_sword", "count": 1, 'auxValue': 0}, args["playerId"]) 

# Listen for the callback function of ServerChatEvent 
def OnServerChat(self, args): 
print "==== OnServerChat ==== ", args 
# Generate dropped items 
# When the information we input is equal to the value on the right, create the corresponding item 
# Create a Component to complete a specific function, here is to create an Item 
playerId = args["playerId"] 
comp = compFactory.CreateItem(playerId) 
if args["message"] == "Diamond Sword": 
# Call the SpawnItemToPlayerInv interface to generate items to the player's backpack. For parameters, refer to the "MODSDK Document" 
            comp.SpawnItemToPlayerInv({"itemName":"minecraft:diamond_sword", "count":1, 'auxValue': 0}, playerId)
        elif args["message"] == "Diamond Pickaxe":
            comp.SpawnItemToPlayerInv({"itemName":"minecraft:diamond_pickaxe", "count":1, 'auxValue': 0}, playerId)
        elif args["message"] == "Diamond Helmet":
            comp.SpawnItemToPlayerInv({"itemName":"minecraft:diamond_helmet", "count":1, 'auxValue': 0}, playerId)
        elif args["message"] == "Diamond Breastplate":
            comp.SpawnItemToPlayerInv({"itemName":"minecraft:diamond_chestplate", "count":1, 'auxValue': 0}, playerId) 
elif args["message"] == "Diamond Leggings": 
comp.SpawnItemToPlayerInv({"itemName":"minecraft:diamond_leggings", "count":1, 'auxValue': 0}, playerId) 
elif args["message"] == "Diamond Boots": 
comp.SpawnItemToPlayerInv({"itemName":"minecraft:diamond_boots", "count":1, 'auxValue': 0}, playerId) 
else: 
print "==== Sorry man ====" 

# The function name is Destroy and will be called. When this System is recycled by the engine, this function will be called to destroy some content 
def Destroy(self): 
print "===== TutorialServerSystem Destroy =====" 
# Call the above anti-listening function to destroy 
self.UnListenEvent() 

``` 

## Event Driven 

We can see that in order to define our system class, we get a reference to the server-side system class `mod.server.system.serverSystem` inherited from the system base class `mod.common.system.baseSystem` from the `GetServerSystemCls` method under the **Extra API** (the server side is `mod.server.extraServerApi`). The definition of our `TutorialServerSystem` class will inherit from this server-side system class. 

Then, in the `__init__` method of the `TutorialServerSystem` class, we can see that the custom method `ListenEvent` is called immediately after calling the initialization method of the superclass. This is the method used to register various event listeners. 

In the `ListenEvent` method, we register an event listener by calling the `ListenForEvent` method of the system (`self`). The first two parameters are the namespace and name of the system that the event listener is to listen to. If we want to listen to the native events of the module API given by the engine by default, we need to use the `GetEngineNamespace` and `GetEngineSystemName` methods in the additional API to get the namespace and name of the **Engine System**. The engine system is also a system, which is the native system of the module API in the Bedrock engine. If you want to listen to events broadcast by your own or other modules' custom systems, you need to correctly fill in the corresponding namespace and name, so that the two parameters are consistent with the namespace and system name provided when registering the system in `modMain.py`. 

**Event** is an identifier that is sent by the Bedrock engine or user-defined code and is triggered when a certain logic occurs in the game. **Listen** to an event means passing a callback function into the response code of an event and executing the callback function at the same time when the event is triggered. This callback function is often called the **Response** of the event. The behavior of sending this message to the specified client or server when the event is triggered is called **Broadcast** or **Notify**, depending on the number of objects sent and the number of receivers. 

The third parameter of the `ListenEvent` method is the identifier of the event, telling the engine that I have set the listener for "which" event on this system. The fourth parameter is the instance of the system to which the listener is bound. Because our event listener response (i.e. callback function) is defined in the example of this system, we fill in the system itself (`self`). Write the response function of the listener in the fifth parameter. This function will be triggered asynchronously when the event is triggered. 

This series of operations is a simple event-driven logic. By registering an event listener, a callback function is bound to the event as a response. When the event is triggered and broadcast or notified to the end, the callback function is executed asynchronously to run the related logic. 

## Use of component interface

We can get the reference of the server-side **Engine Component Factory** class `mod.server.component.engineCompFactoryServer` from the `GetEngineCompFactory` method under the additional API. The engine component factory is a class used to create **Engine Component**. Engine components are different from components in regular ECS systems. They are not only used to store data, but also to execute logic. Each engine component has a variety of methods, each of which can be used to execute a different logic or complete a different operation. For example, the `KillEntity` method under the engine component `game` (the server is an instance of `mod.server.component.gameCompServer`) can kill an entity with a specified ID. Just use the following example code to kill an entity: 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.KillEntity(entityId) 
``` 

The `comp` variable above is an instance of the `mod.server.component.gameCompServer` engine component. 

Various logics can be achieved through the engine component, and with the event-driven system, various logic occurrence points in the game can be "precisely attacked" and their own logic can be inserted. This operating mode is the basic method of how the module API modifies the game!