--- 
sidebarDepth: 1 
--- 
# Model Effects 

## CreateEngineEffectBind 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.system.clientSystem.ClientSystem 

- Description 

Refers to using the editor to save all the special effects of all the edited hanging points in the models/bind/xxx_bind.json in the resource pack. The generated special effects will be automatically hung and played, and the special effects set as invisible in the editor will also be played. And when using the special effects created in this way, the developer does not need to maintain the hanging special effects that are removed due to the entity entering and leaving the field of view. The engine will automatically create all special effects every time the entity enters the field of view. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| path | str | Effect configuration path, needs to contain json suffix | 
| bindEntity | str | Bound entity ID | 
| aniName | str | Select which model action to use for the effect | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int or None | effectEntityId or None | 

- Notes 
- Before creating an effect, you need to replace the entity's skeleton model with the same one in the editor (or other models with the same skeleton), otherwise the attachment will fail. For model replacement, see the model components of the server and client. 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
class MyClientSystem(ClientSystem): 
# Create 
def createEffect(self): 
# Model effect bound to the local player 
effectEntityId = self.CreateEngineEffectBind("models/bind/xuenv_bind.json", clientApi.GetLocalPlayerId(), 'idle') 

# Delete 
def removeEffect(self, effectEntityId): 
self.DestroyEntity(effectEntityId) 
``` 

## Pause


<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.engineEffectBindControlComp.EngineEffectBindControlComp 

- Description 

Pause model effects (i.e. effects created using CreateEngineEffectBind) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreateEngineEffectBindControl(effectEntityId) 
comp.Pause() 
``` 

## Resume 

<span style="display:inline;color:#7575f9">Client</span> 

method in mod.client.component.engineEffectBindControlComp.EngineEffectBindControlComp 

- Description 

Continue playing model effects (i.e. effects created using CreateEngineEffectBind) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the setting is successful | 

- Example


```python
import mod.client.extraClientApi as clientApi
comp = clientApi.GetEngineCompFactory().CreateEngineEffectBindControl(effectEntityId)
comp.Resume()
```