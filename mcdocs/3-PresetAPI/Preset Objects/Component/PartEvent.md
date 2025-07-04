--- 
sidebarDepth: 1 
--- 
# PartEvent 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [OnTriggerEntityEnter](#ontriggerentityenter) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Triggered when an entity enters the trigger range, only applicable to TriggerPart | 
| [OnTriggerEntityExit](#ontriggerentityexit) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Triggered when an entity leaves the trigger range, only applicable to TriggerPart | 
| [OnTriggerEntityStay](#ontriggerentitystay) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Triggered when an entity stays in the trigger range, only applicable to TriggerPart | 

## OnTriggerEntityEnter 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Parts.PartEvent 

- Description 

Triggered when an entity enters the trigger range, only applicable to TriggerPart 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| TriggerPart | PartBase | The trigger part that emits the event | 
| EnterEntityIds | list(str) | List of entity IDs that enter the trigger scope | 

- Return value 

None 

- Example 

```python 
part = self.GetParent().GetPartByType("TriggerPart") 
if not part: 
return 
self.ListenPartClientEvent(part.id, "OnTriggerEntityEnter", self, self.OnTriggerEntityEnter) 
``` 

## OnTriggerEntityExit 


<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Parts.PartEvent 

- Description 

Triggered when an entity leaves the trigger range, only applicable to TriggerPart 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| TriggerPart | PartBase | Trigger part that emits the event | 
| ExitEntityIds | list(str) | List of entity IDs that leave the trigger range | 

- Return value 

None 

- Example 

```python 
part = self.GetParent().GetPartByType("TriggerPart") 
if not part: 
return 
self.ListenPartClientEvent(part.id, "OnTriggerEntityExit", self, self.OnTriggerEntityExit) 
``` 

## OnTriggerEntityStay 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Parts.PartEvent 

- Description 

Triggered when an entity stays in the trigger range, only applicable to TriggerPart 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| TriggerPart | PartBase | Trigger part that emits the event | 
| StayEntityIds | list(str) | List of entity IDs that stay in the trigger range | 

- Return value 

None


- Example

```python
part = self.GetParent().GetPartByType("TriggerPart")
if not part:
    return
self.ListenPartClientEvent(part.id, "OnTriggerEntityStay", self, self.OnTriggerEntityStay)
```