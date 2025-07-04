# Plugin folder structure 

Based on the previous understanding, there are 4 types of plugins, namely lobbyMod, gameMod, serviceMod, and masterMod. 

Their folder structures are not exactly the same. This section will introduce the contents and functions of the folders. 

## lobbyMod/gameMod 

``` 
xxxMod 
developer_mods —— server mod, will not be transferred to the client 
xxxModDev —— server mod root directory 
mod.json —— plugin configuration file and basic information 
netease_require.json —— plugin dependencies (can be default) 
scripts —— server scripts 
behavior_packs 
xxxModBeh —— client mod root directory 
scripts —— client scripts 
manifest.json —— resource version information 
resource_packs 
xxxModRes —— resource root directory 
manifest.json —— resource version information 
ui —— ui file 
... —— other resource files 
worlds 
level 
db 
level.dat —— map global data 
levelname.txt —— map name 
world_behavior_packs.json —— configure the behavior mods that the client needs to download 
world_resource_packs.json ——Configure the resource mods that the client needs to download 
mod.sql ——SQL statement for creating a data table (optional) 
readme.txt ——Plugin introduction 
``` 

Differences between developer_mods and behavior_packs: 

- developer_mods controls server-side behavior, behavior_packs controls client-side behavior. 
- behavior_packs will be downloaded to the client, but developer_mods will not. 
- developer_mods can use all interfaces of Apollo SDK and server-side related interfaces in MOD SDK, while behavior_packs uses client-side related interfaces in MOD SDK. 
- behavior_packs must contain the manifest.json file, and the pack id and version must be configured in the world_behavior_packs.json file under the map directory. 

world_behavior_packs.json and world_resource_packs.json files do not need to be configured by themselves. When using MCS to deploy plugins, if the files are illegal, they will be automatically repaired. 

### neteaseDaily example 

``` 
neteaseDaily 
developer_mods —— server mod, will not be transferred to the client 
neteaseDailyDev —— server mod root directory

mod.json ——Configuration file and basic information of the plugin 
neteaseDailyScript ——Server script root directory 
behavior_packs 
neteaseDailyBehavior ——Client mod root directory 
neteaseDailyScript ——Client script root directory 
resource_packs 
neteaseDailyRes 
manifest.json ——Resource version information 
ui ——UI file 
textures ——Material file 
worlds 
level 
world_behavior_packs.json ——Configure behavior mods that the client needs to download 
world_resource_packs.json ——Configure resource mods that the client needs to download 
readme.txt ——Plugin introduction 
``` 

## serviceMod/masterMod 

``` 
xxxMod 
developer_mods ——Server mod 
xxxModDev ——Server mod root directory 
mod.json ——Configuration file and basic information of the plugin 
netease_require.json ——Dependencies used by the plugin (optional) 
scripts ——Server scripts 
mod.sql ——SQL statements for creating data tables (optional) 
readme.txt ——Plugin introduction 
``` 

Compared with lobbyMod/gameMod, serviceMod/masterMod lacks behavior_packs, resource_packs and worlds. This plugin can only be run on the server. 

### neteaseDailyService example 

``` 
neteaseDailyService 
developer_mods ——Server mod, will not be transmitted to the client 
neteaseDailyDev ——Server mod root directory 
mod.json ——Plugin configuration file and basic information 
neteaseDailyScript ——Server script 
mod.sql ——SQL statements for creating data tables 
readme.txt ——Plugin introduction 
``` 

### Plugin directory generation tool 


​ According to actual needs, the plug-in consists of several server mods, which can include lobby/game server mods, service server mods, and master server mods. 

​ The directory structure of various server mods has been described in <a href="../../../mcguide/27-网络游戏/课2：Ａpollo基本知识/第3：服务器修改.html" rel="noopenner">第3：服务器修改 </a>. 

​ Developers can download [Generate Plug-in Template Tool](https://g79.gdl.netease.com/template.zip) to quickly generate plug-in directories in actual applications. 

