--- 
sidebarDepth: 1 
--- 
# molang 

## Get 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.queryVariableCompClient.QueryVariableComponentClient 

- Description 

Get the value of a certain entity calculation node. If it does not exist, return the default value when registered 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| variableName | str | Node name, must start with "query.mod." | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Node value | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateQueryVariable(entityId) 
result = comp.Get('query.mod.state') 
``` 

## GetMolangValue 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.queryVariableCompClient.QueryVariableComponentClient 

- Description 

Get the value of the entity molang variable 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| molangName | str | molang variable name, such as query.can_fly | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float or long | Node value, returns None if it does not exist | 

- Notes 
- Because there is no rendering context, some molangs cannot get the correct value in this way, such as query.is_first_person, variable.is_first_person, etc. 
- When molangName is passed to query.get_name or query.owner_identifier, etc., which need to return a string variable value, its hash64 is returned, and the type is an int, which can be used for comparison. query.get_name: returns the name of the creature; query.owner_identifier: returns the identifier of its owner 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateQueryVariable(entityId) 
result = comp.GetMolangValue('query.can_fly') 
``` 

## GetStringHash64 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.queryVariableCompClient.QueryVariableComponentClient 

- Description 

Returns the hash64 of a string variable 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| key | str | String variable to be calculated, such as "steve" | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| long | Result value. If the value passed in is not a string, None is returned | 

- Notes 
- Can be used with GetMolangValue to check whether the hash64 returned by query.get_name or query.owner_identifier is equal to a certain value 

- Example 


```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateQueryVariable(levelId) 
result = comp.GetStringHash64('steve') 
``` 

## Register 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.queryVariableCompClient.QueryVariableComponentClient 

- Description 

Register entity compute node 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| variableName | str | Node name, must start with "query.mod." | 
| defaultValue | float | Default value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Registration success or failure | 

- Notes 
- Note that the node value is stored in single-precision floating point numbers. If used to set integers, there will be errors when the value is greater than 16777216 (or less than -16777216). 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateQueryVariable(levelId) 
result = comp.Register('query.mod.state', 0.0) 
``` 

## Set 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.queryVariableCompClient.QueryVariableComponentClient 


- Description 

Set the value of a certain entity calculation node 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| variableName | str | Node name, must start with "query.mod." | 
| value | float | Calculate the value of the node | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Note that the node value is stored in single-precision floating point numbers. If used to set integers, there will be errors when the value is greater than 16777216 (or less than -16777216) 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateQueryVariable(entityId) 
result = comp.Set('query.mod.state', 1.0) 
``` 

## UnRegister 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.queryVariableCompClient.QueryVariableComponentClient 

- Description 

Unregister entity computing node 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| variableName | str | Node name, must start with "query.mod." | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the deregistration is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateQueryVariable(levelId) 
result = comp.UnRegister('query.mod.state') 
``` 

