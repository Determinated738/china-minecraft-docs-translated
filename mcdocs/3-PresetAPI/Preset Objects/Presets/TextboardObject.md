--- 
sidebarDepth: 1 
--- 
# TextboardObject 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
SdkInterface <|-- TextboardObject 
link SdkInterface "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/SDK%E6%8E%A5%E5%8F%A3%E5%B0%81%E8%A3%85SdkInterface.html" 
TextboardObject: TextboardObject 
SdkInterface: SDK interface package 
SdkInterface: (click to jump) 
``` 

- Description 

TextboardObject (text panel object) is the base class that encapsulates the text panel object and provides object-oriented methods for the text panel 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| textboardId | int | Associated text panel ID | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [SetBindEntity](#setbindentity) | <span style="display:inline;color:#7575f9">Client</span> | Text panel bound entity object | 
| [SetPos](#setpos) | <span style="display:inline;color:#7575f9">Client</span> | Modify the preset position of the text panel | 
| [SetRot](#setrot) | <span style="display:inline;color:#7575f9">Client</span> | Modify the rotation angle. If the text is set to face the camera, the modification of the rotation angle will not take effect. | 
| [SetScale](#setscale) | <span style="display:inline;color:#7575f9">Client</span> | Scale the content as a whole | 
| [SetText](#settext) | <span style="display:inline;color:#7575f9">Client</span> | Modify the text panel content | 
| [SetColor](#setcolor) | <span style="display:inline;color:#7575f9">Client</span> | Modify the font color | 
| [SetBackgroundColor](#setbackgroundcolor) | <span style="display:inline;color:#7575f9">Client</span> | Modify the background color | 
| [SetFaceCamera](#setfacecamera) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to always face the camera | 
| [SetBoardDepthTest](#setboarddepthtest) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to enable depth test, which is enabled by default | 

## SetBindEntity


<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Textboard.TextboardObject.TextboardObject 

- Description 

Text panel binds entity object 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| bindEntityId | str | Id of bound entity; if None, entity binding is canceled, and the following parameters are world coordinates and rotation | 
| offset | tuple(float,float,float) | Offset relative to entity | 
| rot | tuple(float,float,float) | Offset angle relative to entity | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
self.SetBindEntity(self.GetLocalPlayerId(), (0.0, 1.5, 0.0), (0.0, 0.0, 0.0)) 
``` 

## SetPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Textboard.TextboardObject.TextboardObject 

- Description 

Modify the preset position of the text panel 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Coordinates | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
self.SetPos((0.0, 3.0, 0.0)) 
``` 

## SetRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Textboard.TextboardObject.TextboardObject 

- Description 

Modify the rotation angle. If the text is set to face the camera, the modification of the rotation angle will not take effect 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rot | tuple(float,float,float) | Angle (not radians) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
self.SetRot((45.0, 90.0, 0.0)) 
``` 

## SetScale 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Textboard.TextboardObject.TextboardObject 

- Description 

Content overall scaling


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| scale | tuple(float,float) | Scaling value in x,y direction, the value must be greater than 0, (1.0,1.0) in normal state | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
self.SetScale((2.0, 2.0)) 
``` 

## SetText 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Textboard.TextboardObject.TextboardObject 

- Description 

Modify the content of the text panel 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| text | str | Text content | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the modification is successful | 

- Example 

```python 
self.SetText("Modified text") 
``` 




## SetColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Textboard.TextboardObject.TextboardObject 

- Description 

Modify the font color 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| textColor | tuple(float,float,float,float) | RGBA value of the color, range 0-1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
self.SetColor((1.0, 1.0, 0.0, 0.8)) 
``` 

## SetBackgroundColor 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Textboard.TextboardObject.TextboardObject 

- Description 

Modify the background color 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| backgroundColor | tuple(float,float,float,float) | RGBA value of the color, range 0-1 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
self.SetBackgroundColor((1.0, 1.0, 1.0, 1.0)) 
``` 

## SetFaceCamera 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Textboard.TextboardObject.TextboardObject 

- Description 

Set whether to always face the camera 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| faceCamera | bool | Whether to always face the camera, default is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
self.SetFaceCamera(True) 
``` 

## SetBoardDepthTest 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.Textboard.TextboardObject.TextboardObject 

- Description 

Set whether to enable depth test, which is enabled by default


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| depthTest | bool | True means to enable depth test, False means not to enable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Example 

```python 
self.SetBoardDepthTest(False) 
``` 

