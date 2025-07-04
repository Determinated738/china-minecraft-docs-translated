--- 
sidebarDepth: 1 
--- 
# TransformObject 

## Overview 

- Inheritance 

```mermaid 
classDiagram 
GameObject <|-- TransformObject 
link GameObject "/mcdocs/3-PresetAPI/%E9%A2%84%E8%AE%BE%E5%AF%B9%E8%B1%A1/%E9%80%9A%E7%94%A8/%E6%B8%B8%E6%88%8F%E5%AF%B9%E8%B1%A1GameObject.html" 
TransformObject: Transform Object 
GameObject: Game Object 
GameObject: (Click to jump) 
``` 

- Description 

TransformObject is the base class of GameObjects that have transformation properties. They have exact positions and other information in the game world. 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Object name | 
| transform | Transform | Local coordinate transformation | 
| isBroken | bool | Whether it is available. It is unavailable when the material file is lost or the part code syntax is incorrect | 
| isRemoved | bool | Whether it has been destroyed | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetChildTransformObjects](#getchildtransformobjects) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the child TransformObject list | 
| [GetTransformObjects](#gettransformobjects) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the TransformObject list, including itself | 
| [GetChildGameObjects](#getchildgameobjects) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the child GameObject list | 
| [GetGameObjects](#getgameobjects) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the GameObject list, including itself | 
| [GetGameObjectById](#getgameobjectbyid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get GameObject by ID | 
| [GetGameObjectByEntityId](#getgameobjectbyentityid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get GameObject by entity ID | 
| [GetId](#getid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the ID of the current preset | 
| [GetEntityId](#getentityid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the entity ID of the current preset | 
| [GetDisplayName](#getdisplayname) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the display name of the current preset | 
| [GetDisplayPath](#getdisplaypath) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the display path from the current preset to the root node | 
| [GetLocalTransform](#getlocaltransform) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the local coordinate transformation of the current preset |

| [SetLocalTransform](#setlocaltransform) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the local coordinate transformation of the current preset | 
| [GetLocalPosition](#getlocalposition) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the local coordinate position of the current preset | 
| [SetLocalPosition](#setlocalposition) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the local coordinate position of the current preset | 
| [GetLocalRotation](#getlocalrotation) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the current preset local coordinate rotation | 
| [SetLocalRotation](#setlocalrotation) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the current preset local coordinate rotation | 
| [GetLocalScale](#getlocalscale) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the current preset local coordinate scale | 
| [SetLocalScale](#setlocalscale) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the local coordinate scale of the current preset | 
| [GetWorldTransform](#getworldtransform) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the world coordinate transformation of the current preset | 
| [GetWorldMatrix](#getworldmatrix) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the world coordinate transformation matrix | 
| [GetLocalMatrix](#getlocalmatrix) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the local coordinate transformation matrix | 
| [SetWorldTransform](#setworldtransform) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the current preset world coordinate transformation | 
| [GetWorldPosition](#getworldposition) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the current preset world coordinate position | 
| [SetWorldPosition](#setworldposition) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the current preset world coordinate position | 
| [GetWorldRotation](#getworldrotation) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the current preset world coordinate rotation | 
| [SetWorldRotation](#setworldrotation) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the current preset world coordinate rotation | 
| [GetWorldScale](#getworldscale) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the current preset world scale | 
| [SetWorldScale](#setworldscale) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the current preset world scale | 
| [AddLocalOffset](#addlocaloffset) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add an offset to the local coordinate transformation position | 
| [AddWorldOffset](#addworldoffset) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add offset to world transform position | 
| [AddLocalRotation](#addlocalrotation) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add offset to local transform rotation | 
| [AddWorldRotation](#addworldrotation) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add offset to world transform rotation | 
| [AddLocalScale](#addlocalscale) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Adds an offset to the local coordinate transformation scale | 
| [AddWorldScale](#addworldscale) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Adds an offset to the world coordinate transformation scale | 
| [AddLocalTransform](#addlocaltransform) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Adds an offset to the local coordinate transformation scale | 
| [AddWorldTransform](#addworldtransform) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add an offset to the world transform | 
| [GetRootParent](#getrootparent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the root preset of the current preset | 
| [GetParent](#getparent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the parent preset of the current preset | 
| [SetParent](#setparent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the parent preset of the current preset | 
| [GetManager](#getmanager) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the preset manager where the current preset is located | 
| [Unload](#unload) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Unload the current preset | 
| [Destroy](#destroy) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Destroy current preset | 

## GetChildTransformObjects 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the list of child TransformObjects 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| recursive | bool | Whether to recursively search for all child nodes |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(TransformObject) | TransformObject list | 

## GetTransformObjects 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the TransformObject list, including itself 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| recursive | bool | Whether to recursively search for all child nodes | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(TransformObject) | TransformObject list | 

## GetChildGameObjects 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the child GameObject list 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| recursive | bool | Whether to recursively search for all child nodes | 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(GameObject) | Game object list | 

## GetGameObjects 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the GameObject list, including itself 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| recursive | bool | Whether to recursively search for all child nodes | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(GameObject) | Game object list | 

## GetGameObjectById 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get GameObject by ID 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| GameObject | Game object |



## GetGameObjectByEntityId 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get GameObject by entity ID 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| GameObject | Game object | 

## GetId 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the ID of the current preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | ID | 

## GetEntityId 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span>


method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the entity ID of the current preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Entity ID | 

## GetDisplayName 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the display name of the current preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | name | 

## GetDisplayPath 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the display path from the current preset to the root node


- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Node path | 

## GetLocalTransform 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the local coordinate transformation of the current preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| Transform | Coordinate transformation | 

## SetLocalTransform 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Set the local coordinate transformation of the current preset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| transform | Transform | Coordinate transformation |


- Return value 

None 

## GetLocalPosition 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the local coordinate position of the current preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | (X-axis position, Y-axis position, Z-axis position) | 

## SetLocalPosition 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Set the local coordinate position of the current preset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | (X-axis position, Y-axis position, Z-axis position) | 

- Return value 

None 




## GetLocalRotation 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the local coordinate rotation of the current preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | (X-axis angle, Y-axis angle, Z-axis angle) | 

## SetLocalRotation 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Set the local coordinate rotation of the current preset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rotation | tuple(float,float,float) | (X-axis angle, Y-axis angle, Z-axis angle) | 

- Return value 

None 

## GetLocalScale 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject


- Description 

Get the local coordinate scale of the current preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | (X axis scale, Y axis scale, Z axis scale) | 

## SetLocalScale 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Set the local coordinate scale of the current preset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| scale | tuple(float,float,float) | (X-axis scaling, Y-axis scaling, Z-axis scaling) | 

- Return value 

None 

## GetWorldTransform 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the current preset world coordinate transformation 

- Parameters


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| Transform | Coordinate transformation | 

## GetWorldMatrix 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the world coordinate transformation matrix 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| Matrix | World coordinate transformation matrix | 

## GetLocalMatrix 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the local coordinate transformation matrix 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| Matrix | Local coordinate transformation matrix | 

## SetWorldTransform 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Set the current preset world coordinate transformation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| transform | Transform | Coordinate transformation | 

- Return value 

None 

## GetWorldPosition 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the current preset world coordinate position 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | (X-axis position, Y-axis position, Z-axis position) | 

## SetWorldPosition


<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Set the current preset world coordinate position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | (X-axis position, Y-axis position, Z-axis position) | 

- Return value 

None 

## GetWorldRotation 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the current preset world coordinate rotation 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | (X-axis angle, Y-axis angle, Z-axis angle) | 

## SetWorldRotation 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description


    Set the current preset world coordinate rotation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rotation | tuple(float,float,float) | (X-axis angle, Y-axis angle, Z-axis angle) | 

- Return value 

None 

## GetWorldScale 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the current preset world coordinate scale 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | (X-axis scaling, Y-axis scaling, Z-axis scaling) | 

## SetWorldScale 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Set the world coordinate scaling of the current preset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| scale | tuple(float,float,float) | (X-axis scaling, Y-axis scaling, Z-axis scaling) | 

- Return value 

None 

## AddLocalOffset 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Add an offset to the local coordinate transformation position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| offset | tuple(float,float,float) | Transform position | 

- Return value 

None 

## AddWorldOffset 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Add an offset to the world coordinate transformation position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| offset | tuple(float,float,float) | Transform position | 

- Return value 

None



## AddLocalRotation 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Adds an offset to the local coordinate transformation rotation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rotation | tuple(float,float,float) | Transform rotation | 

- Return value 

None 

## AddWorldRotation 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Add an offset to the world coordinate transformation rotation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| rotation | tuple(float,float,float) | Transform rotation | 

- Return value 

None 

## AddLocalScale 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span>


method in Preset.Model.TransformObject.TransformObject 

- Description 

Add an offset to the local coordinate transformation scale 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| scale | tuple(float,float,float) | Transform scale | 

- Return value 

None 

## AddWorldScale 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Add an offset to the world coordinate transformation scale 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| scale | tuple(float,float,float) | Transform scaling | 

- Return value 

None 

## AddLocalTransform 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Add an offset to the local coordinate transformation


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| transform | Transform | Coordinate transformation | 

- Return value 

None 

## AddWorldTransform 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Add an offset to the world coordinate transformation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| transform | Transform | Coordinate transformation | 

- Return value 

None 

## GetRootParent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the root preset where the current preset is located 

- Parameters 

None 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PresetBase | Preset | 

## GetParent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the parent preset of the current preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PresetBase | Preset | 

## SetParent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Set the parent preset of the current preset 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| parent | PresetBase | Preset | 

- Return value 

None 




## GetManager 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Get the preset manager where the current preset is located 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PresetManager | Preset management | 

## Unload 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description 

Uninstall the current preset 

- Parameters 

None 

- Return value 

None 

## Destroy 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.TransformObject.TransformObject 

- Description


Destroy the current preset 

- Parameters 

None 

- Return value 

None 

