--- 
sidebarDepth: 1 
--- 
# Preset.Controller.PresetApi 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CreateTransform](#createtransform) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Construct transformation object | 
| [GetAllPresets](#getallpresets) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get all presets | 
| [GetBlockPresetByPosition](#getblockpresetbyposition) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the first block preset at the specified position | 
| [GetGameObjectByEntityId](#getgameobjectbyentityid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the game object with the specified entity ID | 
| [GetGameObjectById](#getgameobjectbyid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the game object with the specified object ID | 
| [GetGameObjectByTypeName](#getgameobjectbytypename) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the first game object of the specified type and name | 
| [GetGameObjectsByTypeName](#getgameobjectsbytypename) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get all game objects of the specified type and name | 
| [GetPartApi](#getpartapi) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get Parts API | 
| [GetPresetByName](#getpresetbyname) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the first preset of the specified name | 
| [GetPresetByType](#getpresetbytype) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the first preset of the specified type | 
| [GetPresetsByName](#getpresetsbyname) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get all presets of the specified name | 
| [GetPresetsByType](#getpresetsbytype) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get all presets of the specified type | 
| [GetTickCount](#gettickcount) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the current frame count | 
| [LoadPartByModulePath](#loadpartbymodulepath) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Load parts and instantiate by module relative path | 
| [LoadPartByType](#loadpartbytype) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Load parts and instantiate by class name | 
| [SpawnPreset](#spawnpreset) | <span style="display:inline;color:#ff5555">Server</span> | Generate a specified preset at a specified coordinate transformation | 

## CreateTransform 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Constructs a transformation object 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Position transformation | 
| rotation | tuple(float,float,float) | Rotation transformation | 
| scale | tuple(float,float,float) | Scaling transformation | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| Transform | Generated transform object | 

- Example 

```python 
# Create Transform object 
import Preset.Controller.PresetApi as presetApi 
transform = presetApi.CreateTransform((0, 0, 0), (0, 0, 0), (1, 1, 1)) 
``` 

## GetAllPresets 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Get all presets 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(PresetBase) | Preset list | 

- Example 

```python 
import Preset.Controller.PresetApi as presetApi 
presets = presetApi.GetAllPresets() 
``` 

## GetBlockPresetByPosition 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 


Get the first block preset at the specified position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| x | int | X-axis coordinate | 
| y | int | Y-axis coordinate | 
| z | int | Z-axis coordinate | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockPreset | The first block preset at the specified position, returns None if not | 

- Example 

```python 
import Preset.Controller.PresetApi as presetApi 
obj = presetApi.GetBlockPresetByPosition(0, 0, 0) 
``` 

## GetGameObjectByEntityId 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Get the game object of the specified entity ID 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str | Specified entity ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TransformObject | Returns the game object if successful, returns None if failed | 

- Example 

```python

import Preset.Controller.PresetApi as presetApi 
obj = presetApi.GetGameObjectByEntityId(0) 
``` 

## GetGameObjectById 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Get the game object of the specified object ID 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| id | int | Specified object ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TransformObject | Returns the game object if successful, returns None if failed | 

- Example 

```python 
import Preset.Controller.PresetApi as presetApi 
obj = presetApi.GetGameObjectById(0) 
``` 

## GetGameObjectByTypeName 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Get the first game object of the specified type and name 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| classType | str | Specify the type (including preset, part, material data type) | 
| name | str | Specify the name, can be default | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TransformObject | Returns the game object if successful, returns None if failed | 

- Example 

```python 
# Find the first entity preset 
import Preset.Controller.PresetApi as presetApi 
obj = presetApi.GetGameObjectByTypeName("EntityPreset") 
``` 

## GetGameObjectsByTypeName 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Get all game objects of the specified type and name 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| classType | str | Specified type (including preset, part, material data type) | 
| name | str | Specified name, can be default | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(TransformObject) | Transform object list | 

- Example 

```python 
# Find the first entity preset 
import Preset.Controller.PresetApi as presetApi 
objects = presetApi.GetGameObjectsByTypeName("EntityPreset")
```



## GetPartApi 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Get Part API 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PartBase | Empty part, used to call part API | 

- Example 

```python 
import Preset.Controller.PresetApi as presetApi 
partApi = presetApi.GetPartApi() 
partApi.LogDebug("debug") 
``` 

## GetPresetByName 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Get the first preset with the specified name 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Specified name | 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PresetBase | Preset/None | 

- Example 

```python 
import Preset.Controller.PresetApi as presetApi 
obj = presetApi.GetPresetByName("name") 
``` 

## GetPresetByType 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Get the first preset of the specified type 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| classType | str | specified type | 

- return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PresetBase | preset/None | 

- example 

```python 
# Get the first entity preset 
import Preset.Controller.PresetApi as presetApi 
obj = presetApi.GetPresetByType("EntityPreset") 
``` 

## GetPresetsByName 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Controller.PresetApi 

- Description 

Get all presets with a specified name 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Specified name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(PresetBase) | Preset list | 

- Example 

```python 
import Preset.Controller.PresetApi as presetApi 
obj = presetApi.GetPresetsByName("name") 
``` 

## GetPresetsByType 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Get all presets of the specified type 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| classType | str | Specified type | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(PresetBase) | Preset list | 

- Example


```python 
# Get all empty presets 
import Preset.Controller.PresetApi as presetApi 
obj = presetApi.GetPresetsByType("EmptyPreset") 
``` 

## GetTickCount 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Get the current frame number 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Current frame number | 

- Example 

```python 
import Preset.Controller.PresetApi as presetApi 
cnt = presetApi.GetTickCount() 
``` 

## LoadPartByModulePath 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Load parts and instantiate by module relative path 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modulePath | str | Relative path of the part module | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PartBase | The instantiated part, returns None if failed | 

- Example 

```python 
# Load built-in world attribute parts 
import Preset.Controller.PresetApi as presetApi 
obj = presetApi.LoadPartByModulePath("Preset.Parts.WorldPart") 
# Load custom parts, you need to replace Script_xxxxxx, YourPartDir, YourPart with your custom parts 
import Preset.Controller.PresetApi as presetApi 
obj = presetApi.LoadPartByModulePath("Script_xxxxxx.Parts.YourPartDir.YourPart") 
``` 

## LoadPartByType 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Load and instantiate parts by class name 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| partType | str | Part class name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PartBase | The instantiated part, returns None if failed | 

- Example 

```python 
import Preset.Controller.PresetApi as presetApi 
obj = presetApi.LoadPartByType("WorldPart")

``` 

## SpawnPreset 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Controller.PresetApi 

- Description 

Generates a specified preset at a specified coordinate transformation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| presetId | str | Specifies the file ID of the preset, corresponding to the preset object's attribute presetId | 
| transform | Transform | Specified coordinate transformation (preset object->general->coordinate transformationTransform) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PresetBase | Returns the generated preset, returns None if failed | 

- Example 

```python 
# Built-in empty preset, the file IDs of special effect presets are EmptyPreset, EffectPreset 
import Preset.Controller.PresetApi as presetApi 
preset = presetApi.SpawnPreset("EmptyPreset", Transform()) 
``` 

