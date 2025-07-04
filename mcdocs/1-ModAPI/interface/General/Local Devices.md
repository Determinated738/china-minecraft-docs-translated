--- 
sidebarDepth: 1 
--- 
# Local device 

## GetIP 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.extraClientApi 

- Description 

Get the local player's IP address 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Local player's IP address | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.GetIP() 
``` 

## GetPlatform 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.extraServerApi 

- Description 

Get the platform where the script runs 

- Parameters 

None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | 0: Window; 1: IOS; 2: Android; -1: Others, such as online lobby, Apollo and other linux servers | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
serverApi.GetPlatform() 
``` 

### Client interface 

<span id="c0"></span> 
method in mod.client.extraClientApi 

- Description 

Get the platform where the script runs 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | 0: Window; 1: IOS; 2: Android; -1: Other | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
clientApi.GetPlatform() 
``` 

## IsInApollo 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.extraServerApi 


- Description 

Returns whether the current game mod is running in the Apollo network server 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: The current mod is running in the Apollo network service environment<br>False: The current mod is running in the rental service, online lobby or stand-alone environment | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
IsInApollo = serverApi.IsInApollo() 
``` 

## IsInServer 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.extraServerApi 

- Description 

Get whether the current game is running in the server environment 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: In server environment<br>False: Not in server environment | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
isInServer = serverApi.IsInServer() 
``` 
