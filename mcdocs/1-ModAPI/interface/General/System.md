--- 
sidebarDepth: 1 
--- 
# System 

## GetClientSystemCls 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Used to get the client system base class. When implementing a new system, you need to inherit the class returned by this interface 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type(ClientSystem) | Client system class | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
ClientSystem = clientApi.GetClientSystemCls() 
class FpsClientSystem(ClientSystem): 
def __init__(self, namespace, systemName): 
ClientSystem.__init__(self, namespace, systemName) 
``` 

## GetServerSystemCls 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.extraServerApi 

- Description 

Used to get the server system base class. When implementing a new system, you need to inherit the class returned by this interface 

- Parameters 

None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type(ServerSystem) | Server system class | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerSystem = serverApi.GetServerSystemCls() 
class FpsServerSystem(ServerSystem): 
def __init__(self, namespace, systemName): 
ServerSystem.__init__(self, namespace, systemName) 
``` 

## GetSystem 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Get registered systems 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| nameSpace | str | Namespace, mod name is recommended | 
| systemName | str | System name, custom name, English, pinyin and underscore can be used, it is recommended to be as personalized as possible | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ServerSystem | Returns an instance of a specific system | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
serverSystem = serverApi.GetSystem("TutorialMod", "TutorialServerSystem")

``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Used to obtain other system instances 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| nameSpace | str | System registered namespace, usually mod name | 
| systemName | str | System name to be obtained | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ClientSystem | Returns an instance of a specific system, or None if it cannot be obtained | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
ClientSystem = clientApi.GetClientSystemCls()
class FpsClientSystem(ClientSystem):
    def __init__(self, namespace, systemName):
        ClientSystem.__init__(self, namespace, systemName)
        self.tutorialSystem = clientApi.GetSystem("TutorialMod", "TutorialClientSystem")
```



## RegisterSystem

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span>

### Server interface

<span id="s0"></span>
method in mod.server.extraServerApi

- describe


Used to register the system to the engine. The engine will create an instance of the system and recycle it when exiting the game. The system can execute the basic logic given by our engine, such as listening to events, executing Tick functions, communicating with clients, etc. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| nameSpace | str | Namespace, mod name recommended | 
| systemName | str | System name, custom name, English, pinyin and underscores can be used, it is recommended to be personalized as much as possible | 
| clsPath | str | Component class path, the path starts from the first layer of the script | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ServerSystem | Returns an instance of a specific system | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
# The system system is registered in the MOD class of modMain.py 
# Registration method of server system 
@Mod.InitServer() 
def TutorialServerInit(self): 
serverApi.RegisterSystem("TutorialMod", "TutorialServerSystem", "tutorialScripts.tutorialServerSystem.TutorialServerSystem") 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Used to register the system to the engine. The engine will create an instance of the system and recycle it when exiting the game. The system can execute the basic logic given by our engine, such as listening to events, executing Tick functions, communicating with the server, etc. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| nameSpace | str | Namespace, mod name is recommended | 
| systemName | str | System name, custom name, English, pinyin and underscore can be used, it is recommended to be as personalized as possible | 
| clsPath | str | Component class path, the path starts from the first layer of the script | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| ClientSystem | Returns an instance of a specific system | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# The registration of the system is in the MOD class of modMain.py 
# Registration method of the client system 
@Mod.InitClient() 
def TutorialClientInit(self): 
clientApi.RegisterSystem("TutorialMod", "TutorialClientSystem", "tutorialScripts.tutorialClientSystem.TutorialClientSystem") 
``` 

