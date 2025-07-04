--- 
sidebarDepth: 1 
--- 
# UIPreset 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
PresetBase <|-- UIPreset 
link PresetBase "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%A2%84%E8%AE%BE/%E9%A2%84%E8%AE%BE%E5%9F%BA%E7%B1%BBPresetBase.html" 
TransformObject <|-- PresetBase 
link TransformObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E5%8F%98%E6%8D%A2%E5%AF%B9%E8%B1%A1TransformObject.html"
SdkInterface <|-- PresetBase
linkSdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9 %80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html"
GameObject <|-- TransformObject
link GameObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1GameObject.html" 
UIPreset: interface preset 
SdkInterface: SDK interface encapsulation 
SdkInterface: (click to jump) 
PresetBase: preset base class 
PresetBase: (click to jump) 
TransformObject: transformation object 
TransformObject: (click to jump) 
GameObject: game object 
GameObject: (click to jump) 
``` 

- Description 

UIPreset (interface preset) is a kind of preset that binds interface resources. 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| uiNodeScreen | str | UI canvas path, in the string form of "UI file name.UI canvas name" | 
| uiNodeModulePath | str | UI logic file module path inherited from ScreenNode | 
| uiNodeModule | str | UI logic file class name inherited from ScreenNode | 
| uiName | str | UI name, which must be unique in a single addon | 
| autoCreate | bool | Whether to automatically create the UI after the interface preset is created | 
| isHud | bool | Whether the interface blocks game operations | 
| createUIMethod | str | Create interface interface | 
| isBindParent | bool | Whether to bind the parent preset, which is only effective when the parent preset is an entity preset | 
| bindParentOffset | tuple | Takes effect when bound to a parent preset, modifies the offset between the bound entity | 
| bindParentAutoScale | bool | Takes effect when bound to a parent preset, sets whether the bound entity's UI is dynamically scaled based on the distance between the bound entity and the local player |

| showInEditor | bool | Whether to create UI in preset editor | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [SetUiActive](#setuiactive) | <span style="display:inline;color:#7575f9">Client</span> | Set UI activation | 
| [GetUiActive](#getuiactive) | <span style="display:inline;color:#7575f9">Client</span> | Get whether the current UI is active | 
| [SetUiVisible](#setuivisible) | <span style="display:inline;color:#7575f9">Client</span> | Set UI visibility | 
| [GetUiVisible](#getuivisible) | <span style="display:inline;color:#7575f9">Client</span> | Get whether the current UI is displayed | 
| [GetScreenNode](#getscreennode) | <span style="display:inline;color:#7575f9">Client</span> | Get the current ScreenNode instance | 

## SetUiActive 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.UI.UIPreset.UIPreset 

- Description 

Set UI activation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| active | bool | Whether activated | 

- Return value 

None 

## GetUiActive 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.UI.UIPreset.UIPreset 

- Description 

Get whether the current UI is activated 

- Parameters


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | UI activated or not | 

## SetUiVisible 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.UI.UIPreset.UIPreset 

- Description 

Set UI visibility 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| visible | bool | Displayed or not | 

- Return value 

None 

## GetUiVisible 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.UI.UIPreset.UIPreset 

- Description 

Get whether the current UI is displayed 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Whether the UI is displayed | 

## GetScreenNode 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.UI.UIPreset.UIPreset 

- Description 

Get the current ScreenNode instance 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ScreenNode | Current ScreenNode instance | 

