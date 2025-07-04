--- 
sidebarDepth: 1 
--- 
# Local storage 

## GetConfigData 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.configCompClient.ConfigCompClient 

- Description 

Get the data stored in the local configuration file 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| configName | str | Configuration name, can only contain letters, numbers and underscore characters. In addition, to avoid conflicts between addons, it is recommended to add the addon namespace as a prefix | 
| isGlobal | bool | Archive configuration or global configuration, default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Returns local storage data | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateConfigClient(clientApi.GetLevelId()) 
configDict = comp.GetConfigData("addon_namespace_global_config_name", True) 
``` 

## SetConfigData 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.configCompClient.ConfigCompClient 

- Description 

Store data in a local configuration file 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| configName | str | Configuration name, can only contain letters, numbers and underscore characters. In addition, to avoid conflicts between addons, it is recommended to add the addon namespace as a prefix | 
| value | dict | data | 
| isGlobal | bool | When True, it is a global configuration, otherwise it is an archive configuration, the default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateConfigClient(clientApi.GetLevelId()) 
data = {}
data["key"] = "value"
comp.SetConfigData("addon_namespace_global_config_name", data, True)
```