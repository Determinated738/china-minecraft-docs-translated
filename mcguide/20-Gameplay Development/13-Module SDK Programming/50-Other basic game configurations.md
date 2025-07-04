--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# <span id="Other basic game configurations"></span>Other basic game configurations 

<span id="General configuration"></span> 
## General configuration 

Below is the configuration file description document. 

Configurations files are placed in the config folder of the mod behavior folder, that is, the same level directory as config and entities. 

<span id="configuration file"></span> 
### configuration file 

<span id="netease_require"></span> 
#### netease_require 

- Description 

Manage the order of mod loading dependencies 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| modName | str | mod name, this naming field is only used to load dependencies | 
| modRequire | list | list of mods used by dependencies | 

- Path 

behavior/config/netease_require.json 

- File name 

netease_require.json 

- Example 

```json 
{ 
// Indicates that SampleMod depends on RequireMod, so when loading, the RequireMod mod will be loaded first 
"modName":"SampleMod", 
"modRequire":[ 
                "RequireMod"
        ]
}

``` 

<span id="server configuration"></span> 
## server configuration 

The configuration defined in the server configuration file is as follows 

<span id="configuration file"></span> 
### configuration file 

<span id="banned_items"></span> 
#### banned_items 

- description 

banned item configuration file 

- parameters 

| parameter name | data type | description | 
| :--- | :--- | :--- | 
| banned_items | list | identifier of banned items | 

- path 

behavior/config/banned_items.json 

- file name 

banned_items.json 

- example 

```json 
{ 
"banned_items": ["minecraft:egg", "minecraft:snowball"]
}
```