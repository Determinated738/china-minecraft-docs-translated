--- 
sidebarDepth: 1 
--- 
# BlockPreset 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
PresetBase <|-- BlockPreset 
link PresetBase "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E9%A2%84%E8%AE%BE%E5%9F%BA%E7%B1%BBPresetBase.html" 
SdkInterface <|-- PresetBase 
link SdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9 %80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html"
TransformObject <|-- PresetBase
linkTransformObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E5%8F%98%E6%8D%A2%E5%AF%B9%E8%B1%A1TransformObject.html"
GameObject <|-- TransformObject
link GameObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1GameObject.html" 
BlockPreset: Block preset 
SdkInterface: SDK interface package 
SdkInterface: (click to jump) 
PresetBase: Preset base class 
PresetBase: (click to jump) 
TransformObject: Transform object 
TransformObject: (click to jump) 
GameObject: Game object 
GameObject: (click to jump) 
``` 

- Description 

BlockPreset (block preset) is a type of preset bound to blocks. Due to the huge number of blocks in MC, binding block presets with MC's native blocks, especially native blocks commonly found in maps, may have a significant impact on performance. 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| engineTypeStr | str | Block type ID | 
| blockId | str | Block type digital ID | 
| auxValue | int | Additional value | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- |

| [GetEngineTypeStr](#getenginetypestr) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the block type ID of the block preset | 

## GetEngineTypeStr 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Block.BlockPreset.BlockPreset 

- Description 

Get the block type ID of the block preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Block type ID | 

