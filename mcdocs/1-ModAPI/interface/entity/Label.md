--- 
sidebarDepth: 1 
--- 
# Tags 

## AddEntityTag 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.tagCompServer.TagComponentServer 

- Description 

Add entity tag 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tag | str | Tag name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateTag(entityId) 
comp.AddEntityTag("AAA") 
``` 

## EntityHasTag 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.tagCompServer.TagComponentServer 

- Description 

Determine whether an entity has a specified tag 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| tag | str | tag name | 

- return value 

| <div style="width: 4em">data type</div> | description | 
| :--- | :--- | 
| bool | contains tags | 

- example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateTag(entityId) 
comp.EntityHasTag("AAA") 
``` 

## GetEntityTags 

<span style="display:inline;color:#ff5555">server</span> 

method in mod.server.component.tagCompServer.TagComponentServer 

- description 

Get entity tag list 

- parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Tag list | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateTag(entityId) 
comp.GetEntityTags() 
``` 

## RemoveEntityTag


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.tagCompServer.TagComponentServer 

- Description 

Remove a specified tag from an entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tag | str | Tag name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateTag(entityId)
comp.RemoveEntityTag("AAA")
```