--- 
sidebarDepth: 1 
--- 
# Effect Object EffectObject 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
SdkInterface <|-- EffectObject 
link SdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html" 
EffectObject: Effect Object 
SdkInterface: SDK Interface Encapsulation 
SdkInterface: (Click to Jump) 
``` 

- Description 

EffectObject is the base class that encapsulates special effect objects. It provides an object-oriented way to use special effects. 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| effectId | int | Associated effect ID | 
| effectType | str | Associated effect type, frame/particle | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [Play](#play) | <span style="display:inline;color:#7575f9">Client</span> | Play special effects, only valid for the client | 
| [Stop](#stop) | <span style="display:inline;color:#7575f9">Client</span> | Stop playing special effects, only valid for the client | 
| [BindToEntity](#bindtoentity) | <span style="display:inline;color:#7575f9">Client</span> | Bind to entity | 
| [BindToSkeleton](#bindtoskeleton) | <span style="display:inline;color:#7575f9">Client</span> | Bind to skeleton model | 
| [SetLoop](#setloop) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the special effect is played in a loop, the default is no, only valid for sequence frames | 
| [SetDeepTest](#setdeeptest) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the sequence frame is perspective, the default is no | 
| [SetFaceCamera](#setfacecamera) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the sequence frame is always facing the camera, the default is yes | 

## Play 


<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Effect.EffectObject.EffectObject 

- Description 

Play special effects, only valid for the client 

- Parameters 

None 

- Return value 

None 

## Stop 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Effect.EffectObject.EffectObject 

- Description 

Stop playing special effects, only valid for the client 

- Parameters 

None 

- Return value 

None 

## BindToEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Effect.EffectObject.EffectObject 

- Description 

Bind to entity 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| bindEntityId | str | Bound entity ID | 
| offset | tuple(float,float,float) | Bound offset | 
| rot | tuple(float,float,float) | Bound rotation angle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.BindToEntity(entityId, (0, 1, 0), (0, 0, 0)) 
``` 

## BindToSkeleton 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Effect.EffectObject.EffectObject 

- Description 

Bind bone model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| modelId | int | ID of the bound bone model (see GetModelId of the model component) | 
| boneName | str | Name of the specific bone to bind | 
| offset | tuple(float,float,float) | Binding offset | 
| rot | tuple(float,float,float) | Binding rotation angle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether it is successful | 

- Example 

```python 
self.BindToSkeleton(modelId, "root", (0, 1, 0), (0, 0, 0)) 
```




## SetLoop 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Effect.EffectObject.EffectObject 

- Description 

Set whether the special effect is played in a loop. The default is no. It is only valid for sequence frames. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| loop | bool | True means loop playback | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# Set to loop playback 
self.SetLoop(True) 
``` 

## SetDeepTest 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Effect.EffectObject.EffectObject 

- Description 

Set whether the sequence frame is perspective, the default is no 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| deepTest | bool | False means perspective, then the sequence frame can still be seen when blocked by objects/blocks | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# Set to perspective 
self.SetDeepTest(False) 
``` 

## SetFaceCamera 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Effect.EffectObject.EffectObject 

- Description 

Set whether the sequence frame is always facing the camera, the default is yes 

- Parameter 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| face | bool | True means facing the camera | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# Set to not always face the camera 
self.SetFaceCamera(False) 
``` 

