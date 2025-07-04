# SpigotMaster API documentation 

com.neteasemc.spigotmaster 

## Class SpigotMaster 

- java.lang.Object 
- org.bukkit.plugin.PluginBase 
- org.bukkit.plugin.java.JavaPlugin 
- com.neteasemc.spigotmaster.SpigotMaster 

- All implemented interfaces: 

org.bukkit.command.CommandExecutor, org.bukkit.command.TabCompleter, org.bukkit.command.TabExecutor, org.bukkit.plugin.Plugin 

------ 

``` 
public class SpigotMaster 
extends org.bukkit.plugin.java.JavaPlugin 
``` 

- ### Constructor Summary 

| Constructor and Description | 
| :-------------- | 
| `SpigotMaster()` | 

- ### Method Summary 

| Qualifiers and Types | Method and Description | 
| :------------------------------- | :----------------------------------------------------------- | 
| `void` | `broadcastToAllClient(org.bukkit.entity.Player except, java.lang.String namespace, java.lang.String system, java.lang.String event, java.util.Map<java.lang.String,java.lang.Object> data)`<br>Sends a server-side event to all players on the server. | 
| `void` | `broadcastToAllClient(org.bukkit.entity.Player except, org.bukkit.World world, java.lang.String namespace, java.lang.String system, java.lang.String event, java.util.Map<java.lang.String,java.lang.Object> data)`<br/>Send server-side events to all players in a world. | 
| `java.lang.String` | `getCustomItemIdentifier(org.bukkit.inventory.ItemStack spigotItemStack)`<br/>Get the identifier of the custom item name | 
| `org.bukkit.Material` | `getCustomItemMaterial(java.lang.String customItemIdentifier)`<br/>Get the java material of the custom item name. In the current implementation, it is fixed to Material.WOOD_SWORD, which means the wooden sword is reskinned | 
| `void` | `listenForEvent(java.lang.String namespace, java.lang.String system, java.lang.String event, com.neteasemc.spigotmaster.PyRpcHandler handler)`<br/>Register client events | 
| `void` | `notifyToClient(org.bukkit.entity.Player player, java.lang.String namespace, java.lang.String system, java.lang.String event, java.util.Map<java.lang.String,java.lang.Object> data)`<br/>Send server events to a specified player | 
| `void` | `notifyToClientsNearby(org.bukkit.entity.Player except, org.bukkit.Location loc, double dist, java.lang.String namespace, java.lang.String system, java.lang.String event, java.util.Map<java.lang.String,java.lang.Object> data)`<br/>Send server events to all players within a certain radius near a location. | 
| `void` | `notifyToMultiClients(java.util.List<org.bukkit.entity.Player> players, java.lang.String namespace, java.lang.String system, java.lang.String event, java.util.Map<java.lang.String,java.lang.Object> data)`<br/>Send server events to multiple players. |
  | `void` | `onDisable()` |
  | `void` | `onEnable()` |
  | `org.bukkit.inventory.ItemStack` | `setCustomItemIdentifier(org.bukkit.inventory.ItemStack spigotItemStack, java.lang.String customIdentifier)`<br/>Set the identifier of the custom item |

- ### Methods inherited from class org.bukkit.plugin.java.JavaPlugin

  ```
  getCommand, getConfig, getDataFolder, getDefaultWorldGenerator, getDescription, getLogger, getPlugin, getPluginLoader, getProvidingPlugin, getResource, getServer, isEnabled, isNaggable, onCommand, onLoad, onTabComplete, reloadConfig, saveConfig, saveDefaultConfig, saveResource, setNaggable, toString
  ```

- ### Methods inherited from class org.bukkit.plugin.PluginBase 

``` 
equals, getName, hashCode 
``` 

- ### Methods inherited from class java.lang.Object 

``` 
getClass, notify, notifyAll, wait, wait, wait 
``` 

- ### Constructor details 



- #### SpigotMaster 

``` 
public SpigotMaster() 
``` 

- ### Method details 



- #### onEnable 

``` 
public void onEnable() 
``` 

- Specified by: 

`onEnable` in interface `org.bukkit.plugin.Plugin` 

- Overrides: 

`onEnable` in class `org.bukkit.plugin.java.JavaPlugin`

  

  - #### onDisable

    ```
    public void onDisable()
    ```

    - Designated by:

`onDisable` in interface `org.bukkit.plugin.Plugin` 

- Override: 

`onDisable` in class `org.bukkit.plugin.java.JavaPlugin` 



- #### getCustomItemMaterial 

``` 
public org.bukkit.Material getCustomItemMaterial(java.lang.String customItemIdentifier) 
``` 

Get the java material of the custom item name. In the current implementation, it is fixed to Material.WOOD_SWORD, which means the wooden sword is reskinned 

- Parameters: 

`customItemIdentifier` - custom item identifier 



- #### getCustomItemIdentifier 

``` 
public java.lang.String getCustomItemIdentifier(org.bukkit.inventory.ItemStack spigotItemStack) 
``` 

Get the identifier of the custom item name 

- Parameters: 

`spigotItemStack` - itemStack 



- #### setCustomItemIdentifier 

``` 
public org.bukkit.inventory.ItemStack setCustomItemIdentifier(org.bukkit.inventory.ItemStack spigotItemStack, 
java.lang.String customIdentifier) 
``` 

Set the identifier of the custom item 

- Parameters: 

`spigotItemStack` - itemStack 

`customIdentifier` - custom item identifier


  

  - #### listenForEvent 

``` 
public void listenForEvent(java.lang.String namespace, 
java.lang.String system, 
java.lang.String event, 
com.neteasemc.spigotmaster.PyRpcHandler handler) 
``` 

Register client events 

- Parameters: 

`namespace` - source client system namespace 

`system` - source client system system name 

`event` - event name 

`handler` - callback function 



- #### notifyToClient 

``` 
public void notifyToClient(org.bukkit.entity.Player player, 
java.lang.String namespace, 
java.lang.String system, 
java.lang.String event, 
java.util.Map<java.lang.String,java.lang.Object> data) 
``` 

Send server-side events to the specified player 

- Parameters: 

`player` - The player who receives the event 

`namespace` - The namespace that is listened to using ListenForEvent in the client system 

`system` - The systemName that is listened to using ListenForEvent in the client system 

`event` - Event name 

`data` - Event parameters. Note that -2 is used to refer to the entityId of the local player. 




- #### notifyToMultiClients 

``` 
public void notifyToMultiClients(java.util.List<org.bukkit.entity.Player> players, 
java.lang.String namespace, 
java.lang.String system, 
java.lang.String event, 
java.util.Map<java.lang.String,java.lang.Object> data) 
``` 

Send server events to multiple players. Because the entityId of -2 refers to the local player for different players, rather than a fixed entity, do not send this information in multicast. 

- Parameters: 

`players` - List of players to receive events 

`namespace` - namespace to listen to using ListenForEvent in the client system 

`system` - systemName to listen to using ListenForEvent in the client system 

`event` - event name 

`data` - event parameters 



- #### notifyToClientsNearby 

``` 
public void notifyToClientsNearby(org.bukkit.entity.Player except, 
org.bukkit.Location loc, 
double dist, 
java.lang.String namespace, 
java.lang.String system, 
java.lang.String event, 
java.util.Map<java.lang.String,java.lang.Object> data) 
``` 

Send server-side events to all players within a certain radius near a location. Because the entityId of -2 refers to the local player for different players, rather than a fixed entity, so do not send this information in multicast. 

- Parameters: 

`except` - exclude this player when sending events, can be null to indicate not excluding 

`loc` - center position of the circle 

`dist` - radius 


`namespace` - namespace to listen to using ListenForEvent in the client system 

`system` - systemName to listen to using ListenForEvent in the client system 

`event` - event name 

`data` - event parameters 



- #### broadcastToAllClient 

``` 
public void broadcastToAllClient(org.bukkit.entity.Player except, 
org.bukkit.World world, 
java.lang.String namespace, 
java.lang.String system, 
java.lang.String event, 
java.util.Map<java.lang.String,java.lang.Object> data) 
``` 

Send server-side events to all players in a world. Because the entityId of -2 refers to the local player for different players, rather than a fixed entity, do not send this information in multicast. 

- Parameters: 

`except` - exclude this player when sending events, can be null to indicate not excluding 

`world` - world 

`namespace` - namespace to listen to using ListenForEvent in the client system 

`system` - systemName to listen to using ListenForEvent in the client system 

`event` - event name 

`data` - event parameters 



- #### broadcastToAllClient 

``` 
public void broadcastToAllClient(org.bukkit.entity.Player except, 
java.lang.String namespace, 
java.lang.String system, 
java.lang.String event, 
java.util.Map<java.lang.String,java.lang.Object> data) 
``` 

Send server-side events to all players in the server. Because the entityId of -2 refers to the local player for different players, rather than a fixed entity, do not send this information in multicast.


- Parameters: 

`except` - exclude this player when sending events, can be null to indicate not excluding 

`namespace` - namespace to be listened to using ListenForEvent in the client system 

`system` - systemName to be listened to using ListenForEvent in the client system 

`event` - event name 

`data` - event parameters