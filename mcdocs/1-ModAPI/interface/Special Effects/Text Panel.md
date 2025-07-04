--- 
sidebarDepth: 1 
--- 
# Text panel 

## CreateTextBoardInWorld 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.textBoardCompClient.TextBoardComponentClient 

- Description 

Create a text panel 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| text | str | Text display content | 
| textColor | tuple(float,float,float,float) | RGBA value of text color, range 0-1 | 
| boardColor | tuple(float,float,float,float) | Optional parameter, default is None, set to black, RGBA value of panel color, range 0-1 | 
| faceCamera | bool | Whether to always face the camera, default is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Returns the generated id, if the generation fails, returns None | 

- Notes 
- After switching dimensions, text panels that are not created in this dimension and have no bound entities will be automatically hidden, and will be automatically redisplayed after returning to this dimension 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId()) 
comp.CreateTextBoardInWorld("I display in the world coordinate position",(0.5, 0.4, 0.3, 0.8),(0, 0, 0, 1), True)
```



## RemoveTextBoard

<span style="display:inline;color:#7575f9">Client</span>

method in mod.client.component.textBoardCompClient.TextBoardComponentClient

- describe


    Delete text panel 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| boardId | int | ID returned when creating | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId()) 
boardId = comp.CreateTextBoardInWorld("I display in the world coordinate position",(0.5, 0.4, 0.3, 0.8),(0, 0, 0, 1), True) 
if boardId: 
comp.RemoveTextBoard(boardId) 
``` 

## SetBoardBackgroundColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.textBoardCompClient.TextBoardComponentClient 

- Description 

Change the background color 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| boardId | int | Text panel ID | 
| backgroundColor | tuple(float,float,float,float) | RGBA value of the color, range 0-1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 


- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId()) 
boardId = comp.CreateTextBoardInWorld("I am displayed above the player's head",(0.5, 0.4, 0.3, 0.8),(0, 0, 0, 1),True) 
if boardId: 
comp.SetBoardBindEntity(boardId, clientApi.GetLocalPlayerId(), (0.0, 1.5, 0.0), (0.0, 0.0, 0.0)) 
comp.SetBoardBackgroundColor(boardId, (1.0, 1.0, 1.0, 1.0)) 
``` 

## SetBoardBindEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.textBoardCompClient.TextBoardComponentClient 

- Description 

Text panel binds entity object 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| boardId | int | ID of the text panel | 
| bindEntityId | str | ID of the bound entity; if None, the entity binding is canceled, and the following parameters are world coordinates and rotation | 
| offset | tuple(float,float,float) | Offset relative to the entity | 
| rot | tuple(float,float,float) | Offset angle relative to the entity | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId()) 
boardId = comp.CreateTextBoardInWorld("I am displayed above the player's head",(0.5, 0.4, 0.3, 0.8),(0, 0, 0, 1),True) 
if boardId: 
comp.SetBoardBindEntity(boardId, clientApi.GetLocalPlayerId(), (0.0, 1.5, 0.0), (0.0, 0.0, 0.0)) 
``` 



## SetBoardDepthTest 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.textBoardCompClient.TextBoardComponentClient 

- Description 

Set whether to enable depth test. It is enabled by default 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| boardId | int | ID of the text panel | 
| depthTest | bool | True to enable depth test, False to disable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Return whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId()) 
boardId = comp.CreateTextBoardInWorld("I am displayed above the player's head",(0.5, 0.4, 0.3, 0.8),(0, 0, 0, 1),True) 
if boardId: 
comp.SetBoardBindEntity(boardId, clientApi.GetLocalPlayerId(), (0.0, 1.5, 0.0), (0.0, 0.0, 0.0)) 
comp.SetBoardDepthTest(boardId, False) 
``` 

## SetBoardFaceCamera 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.textBoardCompClient.TextBoardComponentClient 

- Description 

Set the orientation of the text panel 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| boardId | int | id of the text panel | 
| faceCamera | bool | whether to always face the camera, default is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Return whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId()) 
boardId = comp.CreateTextBoardInWorld("I am displayed above the player's head",(0.5, 0.4, 0.3, 0.8),(0, 0, 0, 1),True) 
if boardId: 
comp.SetBoardBindEntity(boardId, clientApi.GetLocalPlayerId(), (0.0, 1.5, 0.0), (0.0, 0.0, 0.0)) 
comp.SetBoardFaceCamera(boardId, True) 
``` 

## SetBoardPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.textBoardCompClient.TextBoardComponentClient 

- Description 

Modify position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| boardId | int | Text panel id | 
| pos | tuple(float,float,float) | Coordinates | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId())

boardId = comp.CreateTextBoardInWorld("I am displayed above the player's head",(0.5, 0.4, 0.3, 0.8),(0, 0, 0, 1),True) 
if boardId: 
comp.SetBoardBindEntity(boardId, clientApi.GetLocalPlayerId(), (0.0, 1.5, 0.0), (0.0, 0.0, 0.0)) 
comp.SetBoardPos(boardId, (0.0, 3.0, 0.0)) 
``` 

## SetBoardRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.textBoardCompClient.TextBoardComponentClient 

- Description 

Modify the rotation angle, If the text is set to face the camera, the change of the rotation angle will not take effect 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| boardId | int | ID of the text panel | 
| rot | tuple(float,float,float) | Angle (not radians) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId()) 
boardId = comp.CreateTextBoardInWorld("I am displayed above the player's head",(0.5, 0.4, 0.3, 0.8),(0, 0, 0, 1),True) 
if boardId: 
comp.SetBoardBindEntity(boardId, clientApi.GetLocalPlayerId(), (0.0, 1.5, 0.0), (0.0, 0.0, 0.0)) 
comp.SetBoardRot(boardId, (45.0, 90.0, 0.0)) 
``` 

## SetBoardScale 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.textBoardCompClient.TextBoardComponentClient 


- Description 

Content overall scaling 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| boardId | int | Text panel ID | 
| scale | tuple(float,float) | Scaling value in x,y direction, required value greater than 0, (1.0,1.0) in normal state | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId()) 
boardId = comp.CreateTextBoardInWorld("I am displayed above the player's head",(0.5, 0.4, 0.3, 0.8),(0, 0, 0, 1),True) 
if boardId: 
comp.SetBoardBindEntity(boardId, clientApi.GetLocalPlayerId(), (0.0, 1.5, 0.0), (0.0, 0.0, 0.0)) 
comp.SetBoardScale(boardId, (2.0, 2.0)) 
``` 

## SetBoardTextColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.textBoardCompClient.TextBoardComponentClient 

- Description 

Modify the font color 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| boardId | int | ID of the text panel | 
| textColor | tuple(float,float,float,float) | RGBA value of the color, range 0-1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId()) 
boardId = comp.CreateTextBoardInWorld("I am displayed above the player's head",(0.5, 0.4, 0.3, 0.8),(0, 0, 0, 1),True) 
if boardId: 
comp.SetBoardBindEntity(boardId, clientApi.GetLocalPlayerId(), (0.0, 1.5, 0.0), (0.0, 0.0, 0.0)) 
comp.SetBoardTextColor(boardId, (1.0, 1.0, 0.0, 0.8)) 
``` 

## SetText 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.textBoardCompClient.TextBoardComponentClient 

- Description 

Modify the text panel content 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| boardId | int | Text panel id | 
| text | str | Text content | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the modification is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateTextBoard(clientApi.GetLevelId()) 
boardId = comp.CreateTextBoardInWorld("initial text",(0.5, 0.4, 0.3, 0.8),(0, 0, 0, 1),True) 
if boardId: 
comp.SetText(boardId, "modified text") 
``` 

