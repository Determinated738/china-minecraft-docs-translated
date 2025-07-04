--- 
sidebarDepth: 1 
--- 
# Game rules 

## AddBannedItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemBannedCompServer.ItemBannedCompServer 

- Description 

Add banned items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemName | str | Item identifier, format [namespace:name:auxvalue], auxvalue defaults to 0, auxvalue is * when it matches any auxvalue value. For example: minecraft:egg (you can also disable it by filling in the configuration file config/banned_items.json) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItemBanned(levelId) 
comp.AddBannedItem("minecraft:egg") 
``` 

## AddBlockProtectField 

<span style="display:inline;color:#ff5555">Only available in Apollo</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Sets an area where a block cannot be destroyed by players/entities 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| dimensionId | int | Dimension of the indestructible area | 
| startPos | tuple(int,int,int) | Initial position, minimum point of the AABB bounding box of the indestructible area | 
| endPos | tuple(int,int,int) | End position, maximum point of the AABB bounding box of the indestructible area | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Returns the unique ID of the area on success, which can be used to cancel the indestructible area, and returns -1 on failure | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
field = gameComp.AddBlockProtectField(0, (-20, 0, -20), (20, 255, 20)) 
if field > 0: 
print "AddBlockProtectField success field={}".format(field) 
else: 
print "AddBlockProtectField fail" 
``` 

## CleanBlockProtectField 

<span style="display:inline;color:#ff5555">Apollo only</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Cancel all areas where blocks cannot be destroyed by players/entities 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | success True means cancellation is successful, False means cancellation fails | 

- Example

```python
import mod.server.extraServerApi as serverApi
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId)

suc = gameComp.CleanBlockProtectField() 
print "CleanBlockProtectField suc={}".format(suc) 
``` 

## ClearBannedItems 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemBannedCompServer.ItemBannedCompServer 

- Description 

Clear banned items 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether clearing is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItemBanned(levelId) 
comp.ClearBannedItems() 
``` 
## DisableVineBlockSpread 
<span style="display:inline;color:#ff5555">Server</span> 
method in mod.server.component.gameCompServer.GameComponentServer 
- Description 
Set whether to disable vine spreading growth 
- Parameters 
| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| disable | bool | True: disable False: not disabled | 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.DisableBineBlockSpread(disable) 
``` 

## ForbidLiquidFlow 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Disable/allow fluid flow in the map 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| forbid | bool | True means prohibiting fluid flow, False means allowing fluid flow | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | success True means successful setting, False means failed setting | 

- Notes 
- After prohibiting the flow of fluid, after the flow is allowed again, it will not flow around immediately until the block is updated (such as the adjacent block changes) 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
success = gameComp.ForbidLiquidFlow(True) 
``` 




## GetBannedItemList 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemBannedCompServer.ItemBannedCompServer 

- Description 

Get a list of banned items 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) or None | List of banned items or None (abnormal situation), list element is item identifier, format [namespace:name:auxvalue], auxvalue defaults to 0, auxvalue is * when it matches any auxvalue value. | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItemBanned(levelId) 
comp.GetBannedItemList() 
``` 

## GetGameDiffculty 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get the game difficulty 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | GetMinecraftEnum().GameDiffculty.*:Peaceful, Easy, Normal, Hard are 0~3 respectively |


- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(entityId) 
diffculty = comp.GetGameDiffculty() 
``` 

## GetGameRulesInfoServer 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get game rules 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Game rule dictionary | 

- Notes 
- Game rule dictionary gameRule See code comments 

- Example

```python
import mod.server.extraServerApi as serverApi
comp = serverApi.GetEngineCompFactory().CreateGame(levelId)
type = comp.GetGameRulesInfoServer()
#The return value is as follows
{
'option_info': {
    'pvp': bool,
    'show_coordinates': bool,
    'fire_spreads': bool,
    'tnt_explodes': bool,
    'mob_loot': bool,
    'natural_regeneration': bool,
    'tile_drops': bool,

    'experimental_gameplay': bool,
    },
'cheat_info': {
    'enable': bool,
    'always_day': bool,
    'mob_griefing': bool,
    'keep_inventory': bool,
    'weather_cycle': bool,
    'mob_spawn': bool,
    'entities_drop_loot': bool,
    'daylight_cycle': bool,
    'command_blocks_enabled': bool,
    'random_tick_speed': int,
    }
}
```



## GetGameType

<span style="display:inline;color:#ff5555">Server</span>

method in mod.server.component.gameCompServer.GameComponentServer

- Description 

Get the default game mode 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | GetMinecraftEnum().GameType.*: Survival, Creative, Adventure are 0~2 respectively | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(entityId) 
type = comp.GetGameType() 
``` 

## GetLevelGravity


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get the gravity factor 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Gravity factor | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.GetLevelGravity() 
``` 

## GetSeed 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get the archive seed 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Archive seed | 

- Example


```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
seed = comp.GetSeed() 
``` 

## IsDisableCommandMinecart 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get whether the command block minecart built-in logic instructions are currently allowed to run. Currently only available on Apollo network servers 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: currently prohibit the command block minecart built-in logic instructions; False: currently allow the command block minecart built-in logic instructions | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
isDisable = comp.IsDisableCommandMinecart() 
``` 

## IsLockDifficulty 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Get whether the game difficulty of the current world is locked 

- Parameters


    None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | isLock True means locked, False means unlocked | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
isLock = comp.IsLockDifficulty() 
``` 

## LockDifficulty 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Lock the game difficulty of the current world (valid only for this game). After locking, no player can modify the game difficulty through commands or pause menu in the game 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| lock | bool | True: lock False: unlock | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | result Whether the operation is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.LockDifficulty(True) 
``` 




## OpenCityProtect 

<span style="display:inline;color:#ff5555">Only available in Apollo</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Enable city protection, including prohibiting the destruction of blocks, prohibiting the use of items on blocks, prohibiting monsters from attacking players, prohibiting players from attacking each other, prohibiting day and night switching, prohibiting weather changes, and prohibiting monster group refreshes 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | success True means successful setting, False means failed setting | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
success = gameComp.OpenCityProtect() 
``` 

## RemoveBannedItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.itemBannedCompServer.ItemBannedCompServer 

- Description 

Remove banned items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemName | str | Item identifier, format [namespace:name:auxvalue], auxvalue defaults to 0, auxvalue is * when it matches any auxvalue value. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Whether the removal is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateItemBanned(levelId) 
comp.RemoveBannedItem("minecraft:stained_glass:2") 
``` 

## RemoveBlockProtectField 

<span style="display:inline;color:#ff5555">Apollo only</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Remove the area where a block cannot be destroyed by players/entities 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| field | int | Unique ID of the indestructible area, return value of AddBlockProtectField | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | success True means cancellation is successful, False means cancellation is failed | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
field = gameComp.AddBlockProtectField(0, (-20, 0, -20), (20, 255, 20)) 
if field > 0: 
print "AddBlockProtectField success field={}".format(field) 
suc = gameComp.RemoveBlockProtectField(field) 
print "RemoveBlockProtectField field={} suc={}".format(field, suc)
```



## SetCanActorSetOnFireByLightning


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Disable/enable lightning to ignite entities 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| enable | bool | True to enable lightning to ignite entities False to disable lightning to ignite entities | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | success True means setting is successful, False means setting fails | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
success = gameComp.SetCanActorSetOnFireByLightning(False) 
``` 

## SetCanBlockSetOnFireByLightning 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Disable/enable lightning to ignite blocks 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| enable | bool | True means allowing lightning to ignite blocks False means disabling lightning to ignite blocks | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | success True means setting is successful, False means setting is failed | 

- Notes 
- Lightning will only ignite blocks when the game difficulty is normal or above and fire spread is turned on 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
gameComp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
success = gameComp.SetCanBlockSetOnFireByLightning(False) 
``` 

## SetDefaultGameType 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Set the default game mode 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| gameType | int | GetMinecraftEnum().GameType.*: Survival, Creative, Adventure are 0~2 respectively | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(playerId) 
# Set the creative mode as the default game mode 
comp.SetDefaultGameType(1) 
``` 

## SetDisableCommandMinecart


<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Set to stop/start running the command block minecart built-in logic instructions. Currently only available in Apollo network server 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| isDisable | bool | True: stop running the command block minecart built-in logic instructions; False: start running the command block minecart built-in logic instructions | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
suc = comp.SetDisableCommandMinecart(True) 
``` 

## SetDisableContainers 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Disable the opening of all container interfaces, including player backpacks, various container blocks containing backpack interfaces such as workbenches and boxes, and entity interactions containing backpack interfaces such as horse backpacks and villager trading 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isDisable | bool | Whether to disable container interface | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(entityId) 
comp.SetDisableContainers(True) 
``` 

## SetDisableDropItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Set to prohibit dropping items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isDisable | bool | Whether to prohibit dropping items | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# 1. After turning on the switch, all items will disappear when the player dies; if you need to ensure that the items are not dropped, you can use /gamerule keepInventory true 
# 2. Items can still be dropped in creative mode. 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(entityId) 
comp.SetDisableDropItem(True) 
``` 

## SetDisableGravityInLiquid 

<span style="display:inline;color:#ff5555">Server</span>


method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Whether to block the gravity of all entities in liquid (water, lava) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| isDisable | bool | True: Block False: Unblock | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- After setting the gravity of the entity in the liquid, the entity will not be able to float up or dive. **For the player, when the water/magma is submerged to the waist or above (about 0.7 blocks or below the water/magma surface), it will be impossible to go ashore. ** 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.SetDisableGravityInLiquid(True) 
``` 

## SetDisableHunger 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Set whether to block hunger 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| isDisable | bool | Whether to block hunger | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- If you need to hide hunger, please use HideHungerGui of extraClientApi 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(entityId) 
comp.SetDisableHunger(True) 
``` 

## SetGameDifficulty 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Set the game difficulty 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| difficulty | int | GetMinecraftEnum().GameDiffculty.*:Peaceful, Easy, Normal, Hard are 0~3 respectively | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful, True is successful, False is failed | 

- Notes 
- If the game difficulty has been locked, the game difficulty cannot be successfully modified unless the unlock game difficulty is called 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
result = comp.SetGameDifficulty(0)
```



## SetGameRulesInfoServer 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Set the game rules. All parameters are optional. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| gameRuleDict | dict | Game rule dictionary | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Remarks 
- Each item in the game rule dictionary is an optional parameter, but after setting one of the sub-items of option_info or cheat_info, option_info or cheat_info must be added 

- Example 

```python 
###Game rule dictionary description 
gameRuleDict ={ 
'option_info': { 
'pvp': bool, #Player damage 
'show_coordinates': bool, #Show coordinates 
'fire_spreads': bool, #fire spread 
'tnt_explodes': bool, #tnt explosion 
'mob_loot': bool, #biological loot 
'natural_regeneration': bool, #natural life recovery 
'tile_drops': bool, #block drops 
'immediate_respawn':bool #immediate respawn 
}, 
'cheat_info': { 
'enable': bool, #whether to enable cheats 
'always_day': bool, #always day 
'mob_griefing': bool, #biological destruction of blocks 
'keep_inventory': bool, #keep inventory 
'weather_cycle': bool, #weather cycle 
'mob_spawn': bool, #biological generation 
'entities_drop_loot': bool, #Entity drops

'daylight_cycle': bool, #Enable day and night cycle 
'command_blocks_enabled': bool, #Enable block commands 
'random_tick_speed': int,#Random block tick speed 
} 
} 
### 
ruleDict ={ 
'cheat_info': { 
'enable': True, 
'always_day': True, 

} 
} 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.SetGameRulesInfoServer(ruleDict) 
``` 

## SetHurtCD 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Set damage CD 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| cdTime | int | Unit frame number | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.SetHurtCD(1) 
``` 




## SetLevelGravity 

<span style="display:inline;color:#ff5555">Server</span> 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Set the gravity factor 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| data | float | Gravity factor | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
#A creature can set its own gravity factor. When the gravity factor of a creature is not 0, it has its own gravity factor. For details, see the entity gravity component 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.SetLevelGravity(-0.08) 
``` 

