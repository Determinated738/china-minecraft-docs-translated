--- 
sidebarDepth: 1 
--- 
# Custom data 

## CleanExtraData 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.exDataCompServer.ExDataCompServer 

- Description 

Clear the custom data of the entity or the world. When clearing entity data, use the corresponding entity id to create the component. When clearing world data, use levelId to create the component. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| key | str | Custom key | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
# Clear entity data 
entitycomp = serverApi.GetEngineCompFactory().CreateExtraData(entityId) 
suc = entitycomp.CleanExtraData("nickname") 
print "CleanExtraData entity=%s suc=%s" % (entityId, suc) 
# Clear global data 
levelcomp = serverApi.GetEngineCompFactory().CreateExtraData(levelId) 
suc = levelcomp.CleanExtraData("globalMsg") 
print "CleanExtraData for level suc=%s" % suc 
``` 

## GetExtraData 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.exDataCompServer.ExDataCompServer

- describe


Get the custom data of the entity or the world, the value corresponding to a key. When getting entity data, use the corresponding entity id to create a component. When getting world data, use levelId to create a component. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| key | str | Custom key | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| any | Value corresponding to key | 

- Example 

```python 
# Get global data 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExtraData(levelId) 
levelExData = comp.GetExtraData("globalMsg") 
# Get 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExtraData(entityId) 
nickName = comp.GetExtraData("nickName") 
``` 

## GetWholeExtraData 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.exDataCompServer.ExDataCompServer 

- Description 

Get the complete entity's custom data or the world's custom data. When getting entity data, use the corresponding entity id to create a component. When getting world data, use levelId to create a component. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict or None | Get the specified entity or global extra storage data dictionary. If there is no extra storage data, return None or an empty dictionary. | 


- Example 

```python 
#Get entity data dictionary 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExtraData(entityId) 
dataDict = comp.GetWholeExtraData() 
if dataDict: 
for key, value in dataDict.iteritems(): 
print "key=%s value=%s" % (key, str(value)) 
#Get global data dictionary 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateExtraData(levelId) 
dataDict = comp.GetWholeExtraData() 
if dataDict: 
for key, value in dataDict.iteritems(): 
print "key=%s value=%s" % (key, str(value)) 
``` 

## SaveExtraData 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.exDataCompServer.ExDataCompServer 

- Description 

Used to save custom data of entities or custom data of the world 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Save result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
# Set custom data of entity 
entitycomp = serverApi.GetEngineCompFactory().CreateExtraData(entityId) 
entitycomp.SetExtraData("nickname", "steve", False) 
entitycomp.SetExtraData("score", 256, False)
# more data to set

entitycomp.SaveExtraData() 
``` 

## SetExtraData 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.exDataCompServer.ExDataCompServer 

- Description 

Used to set custom data of an entity or a world. The data is saved in the form of key-value pairs. When setting entity data, use the corresponding entity id to create a component. When setting world data, use levelId to create a component. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| key | str | Custom key | 
| value | any | The value corresponding to the key, supporting Python basic data types | 
| autoSave | bool | Automatically save by default, the default is True. If you set data in batches, please set this parameter to False, and call the SaveExtraData interface when the data is set | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
# Set custom data for entities 
entitycomp = serverApi.GetEngineCompFactory().CreateExtraData(entityId) 
entitycomp.SetExtraData("nickname","steve") 
entitycomp.SetExtraData("score",256) 
# Set custom data for the world 
levelcomp = serverApi.GetEngineCompFactory().CreateExtraData(levelId) 
levelcomp.SetExtraData("globalMsg","helloWorld") 
``` 

