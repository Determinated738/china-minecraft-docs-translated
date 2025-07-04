--- 
sidebarDepth: 1 
--- 
# GameObject GameObject 

## Overview 

- Description 

GameObject is the base class of all preset objects, that is, all classes under Preset API - Preset Object in the API document inherit from GameObject. 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | int | Object ID | 
| classType | str | Object class name | 
| isClient | bool | Whether the object runs on the client or the server | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [LoadFile](#loadfile) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Load the contents of a non-python script file in a specified path, such as a configuration file | 
| [fromDict](#fromdict) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Convert the dictionary to an object of the corresponding type according to the classType field. The type must be decorated with @registerGenericClass | 

## LoadFile 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.GameObject.GameObject 

- Description 

Load the contents of a non-python script file at a specified path, such as a configuration file 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| path | str | Specify a relative path | 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | File content | 

## fromDict 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.GameObject.type 

- Description 

Convert the dictionary to an object of the corresponding type according to the classType field. The type must be decorated with @registerGenericClass 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| data | dict | Dictionary to convert | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| GameObject or dict | Returns the object if the conversion is successful, otherwise returns the dictionary itself | 

