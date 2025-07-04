--- 
sidebarDepth: 1 
--- 
# Entity Part EntityBasePart 

## Overview 

- Description 

Entity Part 

- Member Variables 

| Variable Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | :--- | 
| engineType | str | Entity Type | 
| autoCreate | str | Whether to automatically create the associated entity when the part is initialized, the default is True | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CreateVirtualEntity](#createvirtualentity) | <span style="display:inline;color:#ff5555">Server</span> | Manually create the associated entity, if it has been created, it will be returned directly | 
| [DestroyVirtualEntity](#destroyvirtualentity) | <span style="display:inline;color:#ff5555">Server</span> | Remove the created associated entity, which will be called by default when the engine exits | 

## CreateVirtualEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Parts.EntityBasePart.EntityBasePart 

- Description 

Manually create an associated entity, and return directly if it has been created 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| str | Returns the created entity ID | 

## DestroyVirtualEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Parts.EntityBasePart.EntityBasePart 

- Description 

Removes the created associated entity, which will be called by default when the engine exits 

- Parameters 

None 

- Return value 

None 

