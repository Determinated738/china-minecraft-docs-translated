--- 
sidebarDepth: 1 
--- 
# Math 

## GetDirFromRot 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Get the orientation by the rotation angle 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rot | tuple(float,float) | Pitch angle and angle around the vertical direction, unit is degree | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Unit vector of the player's direction | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
direction = serverApi.GetDirFromRot((0, 0)) 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Get the direction by the rotation angle 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rot | tuple(float,float) | Pitch angle and angle around the vertical direction, the unit is degree | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Unit vector of the player's direction | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
direction = clientApi.GetDirFromRot((0, 0)) 
``` 

## GetRotFromDir 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server Interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Get the rotation angle by orientation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dir | tuple(float,float,float) | Unit vector of the player's orientation | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Pitch angle and angle around the vertical direction, the unit is degree | 

- Example

```python
import mod.server.extraServerApi as serverApi
rot = serverApi.GetRotFromDir((1, 0, 1))
```



### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Get the rotation angle by heading 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dir | tuple(float,float,float) | Unit vector of the player's heading | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Pitch angle and angle around the vertical direction, the unit is degree | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
rot = clientApi.GetRotFromDir((1, 0, 1))
```