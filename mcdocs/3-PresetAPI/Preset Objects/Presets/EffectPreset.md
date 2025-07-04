--- 
sidebarDepth: 1 
--- 
# EffectPreset 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
PresetBase <|-- EffectPreset 
link PresetBase "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E9%A2%84%E8%AE%BE%E5%9F%BA%E7%B1%BBPresetBase.html" 
EffectObject <|-- EffectPreset 
link EffectObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E7%89%B9%E6%95%88%E5%AF%B9%E8%B1%A1EffectObject.html"
SdkInterface <|-- PresetBase
linkSdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9 %80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html"
TransformObject <|-- PresetBase
linkTransformObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E5%8F%98%E6%8D%A2%E5%AF%B9%E8%B1%A1TransformObject.html"
GameObject <|-- TransformObject
link GameObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1GameObject.html" 
EffectPreset: Special effect preset 
SdkInterface: SDK interface encapsulation 
SdkInterface: (click to jump) 
PresetBase: Preset base class 
PresetBase: (click to jump) 
TransformObject: Transform object 
TransformObject: (click to jump) 
EffectObject: Special effect object 
EffectObject: (click to jump) 
GameObject: Game object 
GameObject: (click to jump) 
``` 

- Description 

EffectPreset is a type of preset that binds special effect resources. 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| resource | str | Relative path of special effect json, without suffix .json | 
| effectType | str | Special effect type, frame/particle | 
| effectId | int | Special effect ID | 
| auto | bool | Whether to play automatically | 




## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetResource](#getresource) | <span style="display:inline;color:#7575f9">Client</span> | Get bound json resources | 
| [SetResource](#setresource) | <span style="display:inline;color:#7575f9">Client</span> | Set bound json resources | 

## GetResource 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Effect.EffectPreset.EffectPreset 

- Description 

Get bound json resources 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | json resource relative path, without .json suffix | 

## SetResource 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Effect.EffectPreset.EffectPreset 

- Description 

Set the bound json resource 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| resource | str | json resource relative path, without .json suffix | 

- Return value


    none



