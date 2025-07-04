--- 
sidebarDepth: 1 
--- 
# Entity Preset 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
PresetBase <|-- EntityPreset 
link PresetBase "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E9%A2%84%E8%AE%BE%E5%9F%BA%E7%B1%BBPresetBase.html" 
EntityObject <|-- EntityPreset 
link EntityObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E5%AE%9E%E4%BD%93%E5%AF%B9%E8%B1%A1EntityObject.html"
SdkInterface <|-- PresetBase
linkSdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9 %80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html"
TransformObject <|-- PresetBase
linkTransformObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E5%8F%98%E6%8D%A2%E5%AF%B9%E8%B1%A1TransformObject.html"
GameObject <|-- TransformObject
link GameObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1GameObject.html" 
EntityPreset: Entity preset 
EntityObject: Entity object 
EntityObject: (Click to jump) 
PresetBase: Preset base class 
PresetBase: (Click to jump) 
GameObject: Game object 
GameObject: (Click to jump) 
TransformObject: Transform object 
TransformObject: (Click to jump) 
SdkInterface: SDK interface encapsulation 
SdkInterface: (Click to jump) 
``` 

- Description 

EntityPreset is a special type of preset. Entity presets are usually bound to a certain type of entity in MC. Entity preset instances are bound to a certain entity in MC. Therefore, entity presets can be used to program some entity-related logic. If the player enables multiple AddOns at the same time, and these AddOns all contain entity presets bound to the same MC original entity, only the first entity preset will be loaded. 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| engineTypeStr | str | Entity type ID | 
| entityId | str | Entity ID | 
| updateTransformInterval | int | Transform update interval of entity preset child nodes, 0 means never update | 

