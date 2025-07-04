--- 
sidebarDepth: 1 
--- 
# Transform 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
GameObject <|-- Transform 
link GameObject "../../../../mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1GameObject.html" 
Transform: Transform 
GameObject: GameObject 
GameObject: (Click to jump) 
``` 

- Description 

Transform, including position, rotation and scale 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Position transformation | 
| rotation | tuple(float,float,float) | Rotation transformation | 
| scale | tuple(float,float,float) | Scaling transformation | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddOffset](#addoffset) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add offset to coordinate transformation position | 
| [AddRotation](#addrotation) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add offset to coordinate transformation rotation | 
| [AddScale](#addscale) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add offset to coordinate transformation scaling | 
| [AddTransform](#addtransform) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add offset to coordinate transformation | 
| [GetMatrix](#getmatrix) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get coordinate transformation matrix | 

## AddOffset 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span>


method in Preset.Model.Transform.Transform 

- Description 

Add an offset to the coordinate transformation position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| offset | tuple(float,float,float) | Transform position | 

- Return value 

None 

## AddRotation 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Transform.Transform 

- Description 

Add an offset to the coordinate transformation rotation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rotation | tuple(float,float,float) | Transform rotation | 

- Return value 

None 

## AddScale 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Transform.Transform 

- Description 

Add an offset to the coordinate transformation scaling


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| scale | tuple(float,float,float) | Transform scaling | 

- Return value 

None 

## AddTransform 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Transform.Transform 

- Description 

Add an offset to the coordinate transformation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| transform | Transform | Coordinate transformation | 

- Return value 

None 

## GetMatrix 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.Transform.Transform 

- Description 

Get the coordinate transformation matrix 

- Parameters 

None 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| Matrix | Coordinate transformation matrix | 

