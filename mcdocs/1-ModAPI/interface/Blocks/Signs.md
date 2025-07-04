--- 
sidebarDepth: 1 
--- 
# Signboard 

## GetSignBlockText 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 

Get the text content of the signboard (block) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | Position coordinates of the signboard | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Text content on the signboard | 

- Notes 
- When the block at the input coordinate position is not a sign, None is returned 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId) 
pos = (-1, 4, 34) 
text = comp.GetSignBlockText(pos) 
print "GetSignBlockText text={}".format(text) 
``` 

## SetSignBlockText 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.blockInfoCompServer.BlockInfoComponentServer 

- Description 


Set the text content of the sign (block) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | Coordinates of the sign's location | 
| text | str | Text content to be set | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId) 
pos = (-1, 4, 34) 
suc = comp.SetSignBlockText(pos, "text content") 
print "SetSignBlockText suc={}".format(suc) 
``` 

