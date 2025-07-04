--- 
sidebarDepth: 1 
--- 
# Player Preset PlayerPreset 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
EntityPreset <|-- PlayerPreset 
link EntityPreset "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E5%AE%9E%E4%BD%93%E9%A2%84%E8%AE%BEEntityPreset.html" 
PlayerObject <|-- PlayerPreset 
link PlayerObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E7%8E%A9%E5%AE%B6%E5%AF%B9%E8%B1%A1PlayerObject.html"
PresetBase <|-- EntityPreset
link PresetBase "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E9%A2%84%E8%AE%BE%E5%9F%BA%E7%B1%BBPresetBase.html"
EntityObject <|-- EntityPreset
link EntityObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E5%AE%9E%E4%BD%93%E5%AF%B9%E8%B1%A1EntityObject.html"
TransformObject <|-- PresetBase
linkTransformObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E5%8F%98%E6%8D%A2%E5%AF%B9%E8%B1%A1TransformObject.html"
SdkInterface <|-- PresetBase
linkSdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9 %80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html"
GameObject <|-- TransformObject
link GameObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1GameObject.html" 
PlayerPreset: Player preset 
PlayerObject: Player object 
PlayerObject: (Click to jump) 
EntityPreset: Entity preset 
EntityPreset: (Click to jump) 
GameObject: Game object 
GameObject: (Click to jump) 
EntityObject: Entity object 
EntityObject: (Click to jump) 
SdkInterface: SDK interface encapsulation 
SdkInterface: (Click to jump) 
TransformObject: Transform object 
TransformObject: (Click to jump) 
PresetBase: Preset base class 
PresetBase: (Click to jump) 
``` 

- Description 

PlayerPreset is a special type of entity preset, which is bound to the player entity. Each AddOn (editor work) is only allowed to create one player preset. If the player enables multiple AddOns that use player presets at the same time, only the first player preset will be loaded. 

- Member variables 


| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Player ID | 

