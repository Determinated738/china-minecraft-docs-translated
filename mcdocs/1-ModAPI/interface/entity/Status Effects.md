--- 
sidebarDepth: 1 
--- 
# Status Effects 

## AddEffectToEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.effectCompServer.EffectComponentServer 

- Description 

Adds a specified status effect to the entity. If the added status already exists, the following situations will occur: 1. If the level is greater than the existing one, update the status level and duration; 2. If the status levels are equal and the remaining duration is greater than the existing one, refresh the remaining time; 3. If the level is less than the existing one, do not modify it; 4. The particle effect is based on the new one 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | :--- | 
| effectName | str | Status effect name string, including custom status effects and vanilla status effects. Vanilla status effects can be found on the wiki | 
| duration | int | Duration of the status effect, in seconds | 
| amplifier | int | The additional level of the status effect. Must be between 0 and 255 (inclusive). If not specified, it defaults to 0. Note that the first level of a status effect (such as health regeneration I) corresponds to 0, so the second level of a status effect, such as health regeneration II, should be specified with a strength of 1. Some effects and custom status effects have no intensity difference, such as night vision | 
| showParticles | bool | Whether to display particle effects, True to display, False not to display | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateEffect(entityId) 
res = comp.AddEffectToEntity("speed", 30, 2, True) 
``` 

## GetAllEffects 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.effectCompServer.EffectComponentServer 

- Description 

Get all current state effects of an entity 


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(dict) | List of status effect information dictionaries | 

- Notes 
- Status effect information dictionary effectDict 
| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| effectName | str | Status effect name | 
| duration | int | Status effect remaining duration, in seconds | 
| amplifier | int | Status effect additional level | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateEffect(entityId) 
effectDictList = comp.GetAllEffects() 
``` 

## RemoveEffectFromEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.effectCompServer.EffectComponentServer 

- Description 

Delete the specified status effect for the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| effectName | str | Status effect name string, including custom status effects and original status effects. The original status effects can be queried in the wiki | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the deletion is successful | 


- Example

```python
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateEffect(entityId)
res = comp.RemoveEffectFromEntity("speed")
```