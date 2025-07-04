--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# <span id="Event Introduction"></span>Event Introduction 

Events depend on the system. Events need the system to listen and trigger, so you need to have your own system before using events. Events are divided into listening events, anti-listening, publishing events and responding events. 

* Listening events 

Listening events means registering a callback function to an event, and actively calling the callback function when the event occurs. Listening function ListenForEvent 

* Anti-listening events 

Events that no longer need to be listened can be unlistened using the UnListenForEvent function 

* Publishing events 

Publishing events means publishing this event when the event occurs to notify all callback functions that listen to this event. Events defined by the engine will be automatically published when engine events occur; custom events need to be published where needed, and you need to create event data first with CreateEventData. The publishing functions are BroadcastEvent / NotifyToClient / BroadcastToAllClient / NotifyToServer. 

* Response events 

Many of the above-mentioned publishing events are broadcast, but not every message needs to be processed by every system, so the response function will only respond to those who listen to these events and when the message source publishes these events. 

The response function will respond to the callback function in the parameter of ListenForEvent when listening to events. **The callback function must pass in a parameter** (usually of type dict). The parameters of different events are described in the specific events below. Some of the parameters are configurable parameters, and the results of the event can be changed by modifying the value. 

* Example
```python
class MyClientSystem(ClientSystem):
	def __init__(self, namespace, systemName):
		ServerSystem.__init__(self, namespace, systemName)
        # Register for monitoring
		self.ListenForEvent(clientApi.GetEngineNamespace(), clientApi.GetEngineSystemName(), 'AddEntityEvent', self, self.OnAddEntity)
		self.ListenForEvent(clientApi.GetEngineNamespace(), clientApi.GetEngineSystemName(), 'ClientJumpButtonPressDownEvent', self, self.OnClientJumpButtonPressDown)

    # Listening callback function
    def OnAddEntity(self, data):
    	entityId = data["id"]
    	logger.info("AddEntityEvent callback... data: %s" % data)

    def OnClientJumpButtonPressDown(self, data):
    	# continueJump is a configurable parameter that can be used to set whether to execute the jump logic. 
data["continueJump"] = False 

``` 

**Please do not add custom keys to the callback parameters of engine events**. If you need to use the dictionary of callback parameters for other logic, please copy it, for example: 
```python

# A callback function 
def OnAddEntity(self, data): 
myData = { 
"id": data["id"], 
"myKey": "myValue" 
} 
do_something(myData) 
``` 

