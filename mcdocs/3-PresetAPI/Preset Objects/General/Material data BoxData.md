--- 
sidebarDepth: 1 
--- 
# Material data BoxData 

## Overview 

- Inheritance relationship 

```mermaid 
classDiagram 
TransformObject <|-- BoxData 
link TransformObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E5%8F%98%E6%8D%A2%E5%AF%B9%E8%B1%A1TransformObject.html" 
GameObject <|-- TransformObject 
link GameObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1GameObject.html" 
BoxData: Material data 
GameObject: Game object 
GameObject: (click to jump) 
TransformObject: Transform object 
TransformObject: (click to jump) 
``` 

- Description 

BoxData (material data) is similar to material and can be used under presets. BoxData will not be actually generated in the editor and can be placed overlappingly. 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| filePath | str | Relative path of the material relative to the BoxData directory | 

