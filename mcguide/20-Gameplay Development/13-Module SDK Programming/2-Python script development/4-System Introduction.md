--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# <span id="System Introduction"></span>System Introduction 

System is our core class, used to listen to events, use components, update, etc. 

To get a custom System, you need to inherit the engine's system base class ClientSystem/ServerSystem. 
```python 
import client.extraClientApi as clientApi 
ClientSystem = clientApi.GetClientSystemCls() 
import server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
``` 

