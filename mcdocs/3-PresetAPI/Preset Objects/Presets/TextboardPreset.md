--- 
sidebarDepth: 1 
--- 
# TextboardPreset 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
PresetBase <|-- TextboardPreset 
link PresetBase "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E9%A2%84%E8%AE%BE%E5%9F%BA%E7%B1%BBPresetBase.html" 
TextboardObject <|-- TextboardPreset 
link TextboardObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8 %AE%BE/%E6%96%87%E5%AD%97%E9%9D%A2%E6%9D%BF%E5%AF%B9%E8%B1%A1TextboardObject.html"
SdkInterface <|-- PresetBase
linkSdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9 %80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html"
TransformObject <|-- PresetBase
linkTransformObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E5%8F%98%E6%8D%A2%E5%AF%B9%E8%B1%A1TransformObject.html"
GameObject <|-- TransformObject
link GameObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1GameObject.html" 
TextboardPreset: Text panel preset 
TextboardObject: Text panel object 
TextboardObject: (Click to jump) 
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

TextboardPreset is bound to the text panel entity and provides an object-oriented interface for modifying text panel related properties. 

- Member variables 

None 

