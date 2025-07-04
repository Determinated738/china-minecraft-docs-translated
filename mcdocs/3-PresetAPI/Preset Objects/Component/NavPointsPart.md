--- 
sidebarDepth: 1 
--- 
# Navigation path part NavPointsPart 

## Overview 

- Description 

Navigation path part, a series of coordinate points relative to the part can be selected in the editor, and the world coordinate list of these coordinate points can be obtained when the part is running 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| patrolsPath | list(tuple(float,float,float)) | Path point list | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetNavigationPoints](#getnavigationpoints) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the world coordinate list of the waypoints | 
| [GetNavigationRadius](#getnavigationradius) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the random radius list of the waypoints | 

## GetNavigationPoints 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Parts.NavPointsPart.NavPointsPart 

- Description 

Get the world coordinate list of path points 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(tuple(float,float,float)) | World coordinate list of path points |



## GetNavigationRadius 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Parts.NavPointsPart.NavPointsPart 

- Description 

Get a list of random radii for path points 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(float) | List of random radii for path points | 

