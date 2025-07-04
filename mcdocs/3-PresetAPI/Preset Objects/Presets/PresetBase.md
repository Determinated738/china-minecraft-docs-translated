--- 
sidebarDepth: 1 
--- 
# PresetBase 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
SdkInterface <|-- PresetBase 
link SdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html" 
TransformObject <|-- PresetBase 
link TransformObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E5%8F%98%E6%8D%A2%E5%AF%B9%E8%B1%A1TransformObject.html"
GameObject <|-- TransformObject
link GameObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1GameObject.html" 
PresetBase: Preset base class 
SdkInterface: SDK interface encapsulation 
SdkInterface: (click to jump) 
TransformObject: Transform object 
TransformObject: (click to jump) 
GameObject: Game object 
GameObject: (click to jump) 
``` 

- Description 

PresetBase (preset base class) is the base class of all presets. A preset is a type of TransformObject that can be directly placed in the scene, and other TransformObjects can be attached to the preset, which can be used to simply encapsulate the game logic. When placing a preset in the editor, a virtual instance of the preset will be generated, and when generating a preset in the game, an instance will be generated. 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| presetId | str | Preset file ID | 
| preLoad | bool | Whether to preload | 
| forceLoad | bool | Whether to load frequently | 
| childPresetInstances | list(PresetBase) | Child preset list | 
| childPartInstances | list(PartBase) | Child parts list | 
| dimension | int | Dimension of the preset | 
| isAlive | bool | Whether the preset is alive | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- |

| [GetIsAlive](#getisalive) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the preset survival status | 
| [GetGameObjectById](#getgameobjectbyid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the game object with the specified ID under the current preset node | 
| [GetGameObjectByEntityId](#getgameobjectbyentityid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the game object of the specified entity ID under the current preset node | 
| [GetChildPresets](#getchildpresets) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get all child presets of the current preset | 
| [GetChildPresetsByName](#getchildpresetsbyname) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get all child presets of the specified name | 
| [GetChildPresetsByType](#getchildpresetsbytype) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get all child presets of the specified type | 
| [GetChildObjectByTypeName](#getchildobjectbytypename) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the game object of the specified entity ID | 
| [GetChildObjectsByTypeName](#getchildobjectsbytypename) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the game object of the specified entity ID | 
| [SetBlockProtect](#setblockprotect) | style="display:inline;color:#ff5555">Server</span> | Set the block protection status of all material areas in the preset | 
| [Replicate](#replicate) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Copy the current preset at the specified position coordinates | 
| [RemoveChild](#removechild) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Remove the specified child node object | 
| [AddBoxData](#addboxdata) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add specified material data | 
| [RemoveBoxData](#removeboxdata) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Remove specified material data | 
| [AddPreset](#addpreset) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add specified preset as sub-preset | 
| [RemovePreset](#removepreset) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Remove the specified sub-preset | 
| [AddPart](#addpart) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add the specified part as a sub-part | 
| [RemovePart](#removepart) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Remove the specified sub-part | 
| [GetPartsByName](#getpartsbyname) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get all sub-parts of the specified name | 
| [GetPartByName](#getpartbyname) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the first sub-part of the specified name | 
| [GetPartsByType](#getpartsbytype) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get all sub-parts of the specified type | 
| [GetPartByType](#getpartbytype) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the first subpart of the specified type | 
| [RemovePartsByType](#removepartsbytype) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Remove all subparts of the specified type | 

## GetIsAlive 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Get the survival status of the preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether alive | 

## GetGameObjectById 


<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Get the game object with the specified ID under the current preset node 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| id | int | Object ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| GameObject | Returns the game object if successful, or None if failed | 

## GetGameObjectByEntityId 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Get the game object of the specified entity ID under the current preset node 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str | Entity ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| GameObject | Returns the game object if successful, returns None if failed | 

## GetChildPresets 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.PresetBase.PresetBase 

- Description 

Get all sub-presets of the current preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(PresetBase) | Sub-preset list | 

## GetChildPresetsByName 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Get all sub-presets of the specified name 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | name | 
| recursive | bool | whether to search recursively, the default is yes | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(PresetBase) | Child preset list | 

## GetChildPresetsByType 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description


    Get all sub-presets of the specified type 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| classType | str | Type | 
| recursive | bool | Whether to search recursively, the default is yes | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(PresetBase) | Sub-preset list | 

## GetChildObjectByTypeName 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Get the game object of the specified entity ID 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| classType | str | Specify the type | 
| name | str | Specify the name, which can be defaulted | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TransformObject | Returns the game object if successful, or None if failed | 

- Example 

```python 
self.GetChildObjectByTypeName("PresetDebugPart") 
``` 

## GetChildObjectsByTypeName


<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Get the game object of the specified entity ID 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| classType | str | Specify the type | 
| name | str | Specify the name, which can be left blank | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TransformObject | Returns the game object if successful, or None if failed | 

- Example 

```python 
self.GetChildObjectsByTypeName("PresetDebugPart") 
``` 

## SetBlockProtect 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Set the block protection status of all material areas in the preset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| protect | bool | Protect/Unprotect | 

- Return value 

None 




## Replicate 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Copy the current preset at the specified position coordinates 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(float,float,float) | Position coordinates | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PresetBase | Returns the copied preset, returns None if failed | 

## RemoveChild 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Remove the specified child node object 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| child | TransformObject | Child object to be removed | 

- Return value 

None 

## AddBoxData 


<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Add the specified material data 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| boxData | BoxData | Material data to be added | 

- Return value 

None 

## RemoveBoxData 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Remove the specified material data 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| boxData | BoxData | Material data to be removed | 

- Return value 

None 

## AddPreset 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 


Add the specified preset as a sub-preset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| preset | PresetBase | Preset to be added | 

- Return value 

None 

## RemovePreset 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Remove the specified sub-preset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| preset | PresetBase | Sub-preset to be removed | 

- Return value 

None 

## AddPart 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Add the specified part as a sub-part 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| part | PartBase | Parts to be added | 

- Return value 

None 

## RemovePart 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Remove the specified subpart 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| part | PartBase | Parts to be removed | 

- Return value 

None 

## GetPartsByName 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Get all sub-parts of the specified name 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Part name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| list(PartBase) | Parts list | 

## GetPartByName 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Get the first child part of the specified name 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| name | str | Part name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PartBase | Part/None | 

## GetPartsByType 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Get all sub-parts of the specified type 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type | str | Part class name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(PartBase) | Parts list | 




## GetPartByType 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Get the first child part of the specified type 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| type | str | Part class name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PartBase | Part/None | 

## RemovePartsByType 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.PresetBase.PresetBase 

- Description 

Remove all sub-parts of the specified type 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| type | str | Part class name | 

- Return value 

None 

