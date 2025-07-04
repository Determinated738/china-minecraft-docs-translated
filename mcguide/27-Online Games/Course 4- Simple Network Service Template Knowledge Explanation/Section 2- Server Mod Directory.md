--- 
front: 
hard: Getting Started 
time: 10 minutes 
--- 

# Server Mod Directory 

## Mod Type 

Server Mods are usually composed of control server Mods, function server Mods, lobby server Mods and game server Mods. The concepts of various types of Mods are as follows: 

- Control server Mods: Contains all mods in the developer_mods directory of the control server (master). 

- Function server Mods: Contains all mods in the developer_mods directory of the function server (service). 

- Lobby server Mods: Contains all mods and worlds (map archives) in the behavior_packs, resource_packs, and developer_mods directories of the lobby server. 

- Game server Mods: Contains all mods and worlds (map archives) in the behavior_packs, resource_packs, and developer_mods directories of the game server. 

The **standard directory format** of a game server mod is as follows: 

![](./images/image071.png) 

## developer_mods 

The mod directory loaded by the server will not be transmitted to the client. 
The following takes neteaseAnnounce as an example to introduce its directory structure: 

neteaseAnnounceDev 
netease_require.json 
neteaseAnnounceScript 
__init__.py 
announceConsts.py 
announceServerSystem.py 
modMain.py 
timermanager.py 
mod.json 

|File/Folder|Explanation| 
|--------|----------| 
|neteaseAnnounceDev| The top-level neteaseAnnounceDev indicates the name of the mod; the second-level neteaseAnnounceScript indicates the directory of the behavior pack. Developers start importing modules from this directory, such as import neteaseAnnounceScript.announceConsts as announceConsts | 
|`__init__.py`| is the identifier of the python module, indicating that this is a module that can be imported and can also perform some initialization operations. The content can be empty, but the file must exist. | 
|announceConsts.py| Some macro definitions in mod| 
|announceServerSystem.py|mod business logic| 
|modMain.py|The name of this file cannot be changed. It is used to initialize our Mod. For specific usage, please refer to <a href="../../20-Gameplay Development/13-Module SDK Programming/2-Python Script Development/0-Script Development Introduction.html#What is modmain-py" target="_blank">Introduction to Mod Development</a>| 
|timermanager.py|Implements a timer, providing a one-time timer and a loop timer (there are already components that implement the same function in the current ModSDK, so you don’t need to implement it yourself)| 
|netease_require.json| A configuration file used to control the loading order of server Mods. It is not required. For details, see "1-9 Methods for Controlling the Loading Order of Server Mods"| 
|mod.json| A configuration file used to configure the specific functional implementation details of the mod. It is not required| 


The difference between developer_mods and behavior_packs: 

- developer_mods controls server-side behavior, behavior_packs controls client-side behavior. 
- behavior_packs will be downloaded to the client, but developer_mods will not. 
- developer_mods can use all interfaces of Server Mod SDK and server-side related interfaces in MOD SDK, while behavior_packs use client-side related interfaces in MOD SDK. 
- behavior_packs must contain the manifest.json file, and the pack id and version must be configured in the world_behavior_packs.json file in the map directory. 

developer_mods supports multiple mods, each mod corresponds to a directory. The following is the directory structure of neteaseAnnounce and neteaseAlert mods: 

neteaseAnnounceDev 
netease_require.json 
neteaseAnnounceScript 
__init__.py 
announceConsts.py 
announceServerSystem.py 
modMain.py 
timermanager.py 
mod.json 
neteaseAlertDev 
neteaseAlertScript 
__init__.py 
alertConst.py 
alertServerSystem.py 
modMain.py 
mod.json 

## resource_packs 
- Store client resources 

- Resource version information is stored in manifest.json: 

```json 
{ 
"format_version": 1, 
"header": { 
"description": "By tnm", 
"name": "tnm_glove_pve", 
		"uuid": "1c850d23-64f4-46be-aec0-16c8e4618072",
		"version": [0, 0, 1]
	},
	"modules": [
		{
			"description": "By tnm",
			"type": "resources",
			"uuid": "637ff742-7003-4a8b-8d99-722a1b704f12",
			"version": [0, 0, 1]
		}
	]
}
```



​ 
- Not all resource_packs will be downloaded by the client 

- You need to configure the uuid in the `manifest.json` configuration header to worlds/level/`world_resource_packs.json` before it will be downloaded by the client 

- The content of `world_resource_packs.json` is as follows: 
```python 
[ 
{ 
"pack_id" : "1c850d23-64f4-46be-aec0-16c8e4618072", 
"version" : [ 0, 0, 1 ] 
} 
] 
``` 

​ 

## behavior_packs 
- Store client MODs 
- The configuration of manifest.json & world_behavior_packs.json is similar to resource_packs 
- Only one directory is allowed in behavior_packs. If there are multiple, only the first one will be used. Please name it in the *behavior format. It is case insensitive. 
- Scripts in the `*behavior` directory need to be stored in the *scripts directory, and only one is allowed. 
- The `*behavior` directory must contain version information configuration `manifest.json` 

## worlds 
- Only one subdirectory is allowed, such as level in the demo 
- The directory name is used as the map name, and Chinese characters are not allowed 
- Don't forget to configure two jsons such as `world_behavior_packs.json` 

An example directory structure is as follows: 

worlds 
level 
db 
level.dat 
levelname.txt 
world_behavior_packs.json 
world_resource_packs.json 

|File/Folder|Explanation| 
|--------|----------| 
|worlds| The directory for storing server maps. The name cannot be changed| 
|level| Store a map archive directory, the directory name is the map name| 
| db| Map archive directory| 
| level.dat| Store global information about the map| 
|levelname.txt|Name of the map| 
|world_behavior_packs.json|Configure the behavior mods that the client needs to download|

|world_resource_packs.json|Configure the resource mods that the client needs to download| 
