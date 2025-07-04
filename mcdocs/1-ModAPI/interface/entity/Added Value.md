--- 
sidebarDepth: 1 
--- 
# Additional value 

## GetAuxValue 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

### Server interface 

<span id="s0"></span> 
method in mod.server.component.auxValueCompServer.AuxValueComponentServer 

- Description 

Get the additional value of the arrow shot or the potion thrown 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | auxValue | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateAuxValue(entityId) 
comp.GetAuxValue() 
``` 
### Client interface 
<span id="c0"></span> 
method in mod.client.component.auxValueCompClient.AuxValueComponentClient 

- Description 

Get the additional value of the shot arrow or thrown potion 

- Parameters 

None


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | For specific values, see the "Arrow" and "Potion" pages of the wiki | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateAuxValue(entityId) 
auxValue = comp.GetAuxValue() 
``` 

