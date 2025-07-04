--- 
sidebarDepth: 1 
--- 
# Trigger Part TriggerPart 

## Overview 

- Description 

Trigger part, triggers OnTriggerEntityEnter when the entity enters, triggers OnTriggerEntityExit when the entity exits, and triggers OnTriggerEntityStay when the entity stays 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isTriggerEnter | bool | Whether to listen to entity entry, the default is True | 
| isTriggerExit | bool | Whether to listen to entity exit, the default is True | 
| isTriggerStay | bool | Whether to listen to entity entry, the default is False | 
| support | int | Supports client (1)/server (2)/dual end (3), default is dual end (3) | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetEntitiesInTrigger](#getentitiesintrigger) | <span style="display:inline;color:#7575f9">client</span>/<span style="display:inline;color:#ff5555">server</span> | Get the list of entities currently in the trigger area | 

## GetEntitiesInTrigger 

<span style="display:inline;color:#7575f9">client</span>/<span style="display:inline;color:#ff5555">server</span> 

method in Preset.Parts.TriggerPart.TriggerPart 

- Description 

Get the list of entities currently in the trigger area 

- Parameters 

None 

- Return value 

None