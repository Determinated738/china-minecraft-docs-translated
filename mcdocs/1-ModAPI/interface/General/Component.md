--- 
sidebarDepth: 1 
--- 
# Component 

## CreateComponent 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Create a server component for an entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity ID of the owner of the component | 
| nameSpace | str | Component namespace, registerComponent namespace | 
| name | str | Component name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BaseComponent | Component instance | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.CreateComponent(entityId, "Minecraft", "item") 
# After getting comp, you can do some logic content, similar to GetComponent, if it has been created, it will automatically get it directly 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Create a client component for the entity


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity ID of the component owner | 
| nameSpace | str | Component namespace, registerComponent namespace | 
| name | str | Component name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BaseComponent | Component instance | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.CreateComponent(clientApi.GetLocalPlayerId(), "Minecraft", "item") 
# After getting comp, you can do some logic content, similar to GetComponent. If it has been created, it will be automatically Get directly. 
``` 

## DestroyComponent 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Delete the server component of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | The entity id of the owner of the component | 
| nameSpace | str | The namespace of the component, the namespace of registerComponent | 
| name | str | The name of the component | 

- Return value 

None 


- Example 

```python 
import mod.server.extraServerApi as serverApi 
# entityId is obtained according to the actual game ID, here '-12345678910' is just a random 
comp = serverApi.DestroyComponent('-12345678910', "Minecraft", "item") 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Delete the client component of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | The entity id of the owner of the component | 
| nameSpace | str | The namespace of the component, the namespace of registerComponent | 
| name | str | component name | 

- Return value 

None 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.DestroyComponent(clientApi.GetLocalPlayerId(), "Minecraft", "item") 
``` 

## GetComponent 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description


Get the server-side component of the entity. Generally used to determine whether a component has been created. In other cases, please use CreateComponent 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity ID of the owner of the component | 
| nameSpace | str | Namespace of the component, namespace of registerComponent | 
| name | str | Name of the component | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BaseComponent | Component instance or None | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetComponent(entityId, "Minecraft", "item") 
# After getting comp, you can do some logic. If it has not been created, it will return None 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Get the client component of the entity. Generally used to determine whether a component has been created. In other cases, please use CreateComponent 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity ID of the owner of the component | 
| nameSpace | str | Namespace of the component, namespace of registerComponent | 
| name | str | Name of the component | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BaseComponent | Component instance or None | 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetComponent(clientApi.GetLocalPlayerId(), "Minecraft", "item") 
# After getting comp, you can do some logic. If it has not been created, it will return None 
``` 

## GetComponentCls 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Used to get the server component base class. When implementing a new component, you need to inherit the class returned by this interface 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type(BaseComponent) | Component base class | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
ServerComponentCls = serverApi.GetComponentCls() 
# Component must inherit from the base class to take effect 
class ShootComponentServer(ServerComponentCls): 
def __init__(self, entityId): 
ServerComponentCls.__init__(self, entityId) 
# A switch is set here to switch on and off the update of shooting 
self.mShoot = False 
``` 

### Client interface 


<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Used to obtain the client component base class. When implementing a new component, you need to inherit the class returned by this interface 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type(BaseComponent) | Component base class | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
ClientComponentCls = clientApi.GetComponentCls() 
# Component must inherit from the base class to take effect 
class ShootComponentClient(ClientComponentCls): 
def __init__(self, entityId): 
ClientComponentCls.__init__(self, entityId) 
# Here is a switch to switch the update shooting 
self.mShoot = False 
``` 

## GetEngineCompFactory 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Get the factory of the engine component, through which the server engine component can be created 

- Parameters 

None 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| EngineCompFactoryServer | Server-side engine component factory | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
compFactory = serverApi.GetEngineCompFactory() 
gameComp = compFactory.CreateGame(serverApi.GetLevelId()) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Get the factory of the engine component, through which you can create the client's engine component 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| EngineCompFactoryClient | Client Engine Component Factory | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
compFactory = clientApi.GetEngineCompFactory() 
gameComp = compFactory.CreateGame(clientApi.GetLevelId()) 
``` 

## RegisterComponent 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 


<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Used to register components in the engine 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| nameSpace | str | Namespace, mod name is recommended | 
| name | str | Component name | 
| clsPath | str | Component class path, the path starts from the first layer of the script | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Registration success or failure | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
@Mod.InitServer() 
def TutorialServerInit(self): 
# Register a custom server-side Component 
serverApi.RegisterComponent("TutorialMod", "ServerShoot", "tutorialScripts.modServer.serverComponent.shootComponentServer.ShootComponentServer") 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Used to register components to the engine 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| nameSpace | str | Namespace, mod name is recommended | 
| name | str | Component name | 
| clsPath | str | Component class path, the path starts from the first level of the script | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Registration success or failure | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
@Mod.InitClient() 
def TutorialClientInit(self): 
# Register a custom client component 
clientApi.RegisterComponent("TutorialMod", "ClientShoot", "tutorialScripts.modClient.clientComponent.shootComponentClient.ShootComponentClient") 
``` 

