--- 
sidebarDepth: 1 
--- 
# Custom attributes 

## GetAttr 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.modAttrCompServer.ModAttrComponentServer 

- Description 

Get attribute value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| paramName | str | Attribute name. It is recommended to prefix str with mod to avoid conflicts between multiple mods | 
| defaultValue | any | Default value of the attribute. When the attribute does not exist, the default value is returned. In this case, the attribute value is still not set | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| any | Return attribute value | 

- Notes 
- When defaultValue is not passed, the default is None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateModAttr(entityId) 
comp.GetAttr('health') 
# If you modify the collection type obtained by GetAttr directly, you need to call SetAttr again to ensure that it is updated 
testDict = comp.GetAttr('testDict') 
testDict['key'] = 'newValue' 
comp.SetAttr('testDict', testDict) 
``` 

### Client interface 


<span id="c0"></span> 
method in mod.client.component.modAttrCompClient.ModAttrComponentClient 

- Description 

Get attribute value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| paramName | str | Attribute name. It is recommended to prefix str with mod to avoid conflicts between multiple mods | 
| defaultValue | any | Attribute default value. When the attribute does not exist, the default value is returned. At this time, the attribute value is still not set | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| any | Return attribute value | 

- Notes 
- Default is None when defaultValue is not passed 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModAttr(entityId) 
comp.GetAttr('health') 
``` 

## RegisterUpdateFunc 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modAttrCompClient.ModAttrComponentClient 

- Description 

Register the callback function when the attribute value changes. The function will be called when the attribute changes. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| paramName | str | Attribute name to be monitored | 
| func | function | Callback function to be monitored | 


- Return value 

None 

- Notes 
- The callback function needs to accept a parameter, which is a dict. The specific data example is: {'oldValue': 0, 'newValue': 1, 'entityId': ’-433231231231‘} 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
# This entityId is the ID of the object to be monitored 
comp = clientApi.GetEngineCompFactory().CreateModAttr(entityId) 
comp.RegisterUpdateFunc('health', self.jumpingText) 
# When the health attribute of the script layer changes, self.jumpingText will be called 
def jumpingText(self, data): 
entityId = data['entityId'] 
oldValue = data['oldValue'] 
newValue = data['newValue'] 
``` 

## SetAttr 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.component.modAttrCompServer.ModAttrComponentServer 

- Description 

Set attribute value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| paramName | str | Attribute name. It is recommended to prefix str with mod to avoid conflicts between multiple mods | 
| paramValue | any | Attribute value, supports Python basic data | 

- Return value 

None 

- Notes 
- Note: tuple and set will be converted into list during synchronization. It is recommended to use non-collection types such as numbers and strings first. 


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateModAttr(entityId) 
comp.SetAttr('health', 1) 
comp.SetAttr('testDict', {'key':'value'}) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.component.modAttrCompClient.ModAttrComponentClient 

- Description 

Set client attribute value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| paramName | str | Attribute name. It is recommended to prefix str with mod to avoid conflicts between multiple mods | 
| paramValue | any | attribute value, supports python basic data | 

- Return value 

None 

- Remarks 
- Note: The setting here is only valid locally and will not be synchronized to the server and other clients 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModAttr(entityId) 
comp.SetAttr('health', 1) 
``` 

## UnRegisterUpdateFunc 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.modAttrCompClient.ModAttrComponentClient 


- Description 

Callback function when unregistering attribute value change 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| paramName | str | Attribute name to be monitored | 
| func | function | Callback function to be monitored | 

- Return value 

None 

- Remarks 
- The same function as that used during registration needs to be passed as a parameter 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateModAttr(entityId) 
comp.UnRegisterUpdateFunc('health', self.jumpingText) 
``` 

