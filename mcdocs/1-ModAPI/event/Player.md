--- 
sidebarDepth: 1 
--- 
# Player 

# Index 

| Event | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddExpEvent](player.md#addexpevent) | <span style="display:inline;color:#ff5555">server</span> | Trigger Time: This event is triggered when the player gains experience. | 
| [AddLevelEvent](player.md#addlevelevent) | <span style="display:inline;color:#ff5555">server</span> | Trigger Time: This event is triggered when the player levels up. | 
| [ChangeLevelUpCostServerEvent](player.md#changelevelupcostserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: When obtaining the player's next level upgrade experience, it is used to reload the player's upgrade experience. Each level will only be triggered once before it is reset. | 
| [DimensionChangeClientEvent](player.md#dimensionchangeclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Thrown by the client when the player's dimension changes | 
| [DimensionChangeFinishClientEvent](player.md#dimensionchangefinishclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Thrown by the client after the player's dimension change is completed | 
| [DimensionChangeFinishServerEvent](player.md#dimensionchangefinishserverevent) | style="display:inline;color:#ff5555">Server</span> | Thrown by the server after the player dimension change is completed | 
| [DimensionChangeServerEvent](player.md#dimensionchangeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Thrown by the server when the player dimension changes | 
| [ExtinguishFireClientEvent](player.md#extinguishfireclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when the player extinguishes the fire. Rain, pouring water, etc. will not trigger. | 
| [ExtinguishFireServerEvent](player.md#extinguishfireserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the player extinguishes the fire. Rain, pouring water, etc. will not trigger. | 
| [GameTypeChangedClientEvent](player.md#gametypechangedclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Fired on the client side when the individual game mode changes. | 
| [GameTypeChangedServerEvent](player.md#gametypechangedserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired on the server side when the individual game mode changes. | 
| [OnPlayerHitBlockClientEvent](player.md#onplayerhitblockclientevent) | <span style="display:inline;color:#7575f9">Client</span> | When to trigger: After opening block collision detection through OpenPlayerHitBlockDetection, this event is triggered when the player collides with a block. When the player lands, OnGroundClientEvent is triggered instead of this event. The client and server perform collision detection separately, and the results returned by the two events may be slightly different. | 
| [OnPlayerHitBlockServerEvent](player.md#onplayerhitblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: After opening block collision detection through OpenPlayerHitBlockDetection, this event is triggered when the player collides with a block. To monitor the player's grounding, please use the client's OnGroundClientEvent. The client and server perform collision detection separately, and the results returned by the two events may be slightly different. | 
| [PerspChangeClientEvent](玩家.md#perspchangeclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Event triggered when the perspective switches | 
| [PlayerAttackEntityEvent](玩家.md#playerattackentityevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: This event is triggered when the player attacks. | 
| [PlayerCheatSpinAttackServerEvent](player.md#playercheatspinattackserverevent) | <span style="display:inline;color:#ff5555">Apollo</span> | When: When the player starts/ends a quick spin attack and does not meet the conditions for sending a quick spin attack (equipped with a trident enchanted with Riptide, in water or rain, and not mounted) | 
| [PlayerDieEvent](player.md#playerdieevent) | <span style="display:inline;color:#ff5555">Server</span> | When: When the player dies. | 
| [PlayerDoInteractServerEvent](玩家.md#playerdointeractserverevent) | <span style="display:inline;color:#ff5555">服务器</span> | This event is triggered when the player interacts with a creature with the minecraft:interact component, such as a player holding an empty bucket to milk a cow, or a player holding a flint and steel to ignite a creeper | 
| [PlayerEatFoodServerEvent](玩家.md#playereatfoodserverevent) | <span style="display:inline;color:#ff5555">服务器</span> | When to trigger: when the player eats food | 
| [PlayerHurtEvent](玩家.md#playerhurtevent) | <span style="display:inline;color:#ff5555">服务器</span> | When to trigger: before the player is hurt. | 
| [PlayerInteractServerEvent](player.md#playerinteractserverevent) | <span style="display:inline;color:#ff5555">server</span> | Triggered when: the player can interact with the entity. If in mouse control mode, it is triggered when the crosshair is facing the entity. If in touch mode, it is triggered at the same time as the interaction button at the bottom of the screen is displayed. For events where the player actually interacts with the entity, see [PlayerDoInteractServerEvent](#playerdointeractserverevent) | 
| [PlayerRespawnEvent](player.md#playerrespawnevent) | <span style="display:inline;color:#ff5555">server</span> | Triggered when: the player is resurrected. | 
| [PlayerRespawnFinishServerEvent](player.md#playerrespawnfinishserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: Trigger when the player finishes resurrecting | 
| [PlayerSleepServerEvent](player.md#playersleepserverevent) | <span style="display:inline;color:#ff5555">Server</span> | The player successfully sleeps on the bed | 
| [PlayerSpinAttackServerEvent](player.md#playerspinattackserverevent) | <span style="display:inline;color:#ff5555">Apollo</span> | Trigger time: Trigger when the player starts/ends a fast spinning attack | 
| [PlayerStopSleepServerEvent](player.md#playerstopsleepserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Player stops sleeping | 
| [PlayerTeleportEvent](Player.md#playerteleportevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: This event is triggered when the player teleports, such as when the player uses an ender pearl or tp command. | 
| [PlayerTrySleepServerEvent](player.md#playertrysleepserverevent) | <span style="display:inline;color:#ff5555">server</span> | The player tries to sleep on the bed | 
| [ServerPlayerGetExperienceOrbEvent](player.md#serverplayergetexperienceorbevent) | <span style="display:inline;color:#ff5555">server</span> | Trigger time: The event triggered when the player obtains experience balls | 
| [StoreBuySuccServerEvent](player.md#storebuysuccserverevent) | <span style="display:inline;color:#ff5555">server</span> | Trigger time: The event thrown by the server when the player purchases goods in the game | 
# player 

## AddExpEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: This event is triggered when the player gains experience. 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Player id | 
| addExp | int | Added experience points | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## AddLevelEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: This event is triggered when the player upgrades. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Player id | 
| addLevel | int | Added level value | 
| newLevel | int | New level | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ChangeLevelUpCostServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: When obtaining the player's next level upgrade experience, it is used to reload the player's upgrade experience. Each level will only be triggered once before being reset. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| level | int | Player's current level | 
| levelUpCostExp | int | The experience value required to upgrade from the current level to the next level. When the upgrade experience is set to less than 1, it will be forcibly adjusted to 1 |

| changed | bool | Set to True, reloading the player's upgrade experience will take effect | 

- Return value 

None 

### Related interfaces 

<span id="ClearDefinedLevelUpCost"></span> 
### ClearDefinedLevelUpCost 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

The interface is used to reset the upgrade experience. After using the ChangeLevelUpCostServerEvent event to set the upgrade experience, the upgrade experience cannot be adjusted. When you need to adjust the upgrade experience, you can use this interface. The steps are as follows: 1. Use ClearDefineLevelUpconst, 2. Reset the experience after the upgrade throws the ChangeLevelUpCostServerEvent event. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| level | int | Specifies the level to be cleaned. If the value passed in is less than 0, the upgrade experience value cache of all levels will be cleaned | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the cleanup was successful. | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
suc = comp.ClearDefinedLevelUpCost(1) 
``` 

## DimensionChangeClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Thrown by the client when the player dimension changes 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| fromDimensionId | int | Dimension before dimension change | 
| toDimensionId | int | Dimension after dimension change | 
| fromX | float | Position x before change | 
| fromY | float | Position Y before change | 
| fromZ | float | Position Z before change | 
| toX | float | Position x after change | 
| toY | float | Position Y after change | 
| toZ | float | Position Z after change | 

- Return value 

None 

- Notes 
- When returning to the main world from the End through the portal, the toY value is 32767. In other cases, it is generally 1.62 higher than the set value. 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Events">Part Events</a> 

## DimensionChangeFinishClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Thrown by the client after the player dimension change is completed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| fromDimensionId | int | Dimension before dimension change | 
| toDimensionId | int | Dimension after dimension change | 
| toPos | tuple(float,float,float) | Changed position x,y,z, where the y value is the sum of the height of the character and the sole of the foot | 

- Return value 

None 

- Notes 
- When returning to the main world from the End through the portal, the y value of toPos is 32767, and in other cases it is generally 1.62 higher than the set value 

Declare a function of the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 



## DimensionChangeFinishServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Thrown by the server after the player dimension change is completed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| fromDimensionId | int | Dimension before dimension change | 
| toDimensionId | int | Dimension after dimension change | 
| toPos | tuple(float,float,float) | Changed position x,y,z, where y is the value of the sole plus the height of the character | 

- Return value 

None 

- Notes 
- When returning to the main world from the End through the portal, the y value of toPos is 32767. In other cases, it is generally 1.62 higher than the set value. 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## DimensionChangeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Thrown by the server when the player dimension changes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| fromDimensionId | int | Dimension before dimension change | 
| toDimensionId | int | Dimension after dimension change | 
| fromX | float | Position x before change | 
| fromY | float | Position Y before change | 
| fromZ | float | Position Z before change | 
| toX | float | Position x after change | 
| toY | float | Position Y after change | 
| toZ | float | Position Z after change | 

- Return value


None

- Notes
- When returning to the main world from the End through the portal, the toY value is 32767, and in other cases it is generally 1.62 higher than the set value

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a>

## ExtinguishFireClientEvent

<span style="display:inline;color:#7575f9">Client</span>

- Description

Triggered when the player extinguishes the fire. It will not be triggered by extinguishing the fire by rain, pouring water, etc.

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Coordinates of the fire block | 
| playerId | str | Player id | 
| cancel | bool | When modified to True, it prevents the player from extinguishing the fire. Need to be modified together with ExtinguishFireServerEvent. | 

- Return value 

None 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ExtinguishFireServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the player extinguishes the fire. It will not be triggered by extinguishing the fire by rain, pouring water, etc. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Coordinates of the fire block | 
| playerId | str | Player id | 
| cancel | bool | When modified to True, it can prevent the player from extinguishing the fire. Need to be modified together with ExtinguishFireClientEvent. | 

- Return value 


None 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## GameTypeChangedClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered by the client when the personal game mode changes. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player Id | 
| oldGameType | int | Game mode before switching | 
| newGameType | int | Game mode after switching | 

- Return value 

None 

- Remarks 
- Game mode: GetMinecraftEnum().GameType.*: Survival, Creative, Adventure are 0~2 respectively 
When the default game mode changes, it is finally reflected in the personal game mode. 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## GameTypeChangedServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

The server is triggered when the personal game mode changes. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID, this parameter is an empty string when the [SetDefaultGameType](../Interface/World/Game rules.md#SetDefaultGameType) interface changes the game mode | 
| oldGameType | int | Game mode before switching | 
| newGameType | int | Game mode after switching | 

- Return value 


None 

- Notes 
- Game mode: GetMinecraftEnum().GameType.*:Survival, Creative, Adventure are 0~2 respectively 
When the default game mode changes, it is finally reflected in the personal game mode. 

Simply declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnPlayerHitBlockClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger timing: After opening the block collision detection through OpenPlayerHitBlockDetection, this event is triggered when the player collides with the block. When the player lands, OnGroundClientEvent is triggered instead of this event. The client and server perform collision detection separately, and the results returned by the two events may be slightly different. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Id of the player that collides with the block | 
| posX | int | x coordinate of the colliding block | 
| posY | int | y coordinate of the colliding block | 
| posZ | int | z coordinate of the colliding block | 
| blockId | str | identifier of the colliding block | 
| auxValue | int | additional value of the colliding block | 

- Return value 

None 

You can complete the monitoring by directly declaring a function of the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Events">Part Events</a> 

### Related interfaces 

<span id="OpenPlayerHitBlockDetection"></span> 
### OpenPlayerHitBlockDetection 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Enable collision block detection. When enabled, the OnPlayerHitBlockClientEvent event will be triggered when a collision occurs 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| precision | float | Collision detection precision, the parameter needs to be in the interval [0, 1) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Note: This collision detection will block four types of blocks: grass, air, fire, and tall grass 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.OpenPlayerHitBlockDetection(0.0001) 
``` 

<span id="ClosePlayerHitBlockDetection"></span> 
### ClosePlayerHitBlockDetection 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Turn off the detection of collision blocks. After turning it off, the OnPlayerHitBlockClientEvent event will not be triggered 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayer(entityId) 
comp.ClosePlayerHitBlockDetection() 
``` 



## OnPlayerHitBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: After opening block collision detection via OpenPlayerHitBlockDetection, this event is triggered when the player collides with a block. To monitor the player's landing, use the client's OnGroundClientEvent. The client and server perform collision detection separately, and the two events may return slightly different results. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Id of the player that collides with the block | 
| posX | int | x coordinate of the colliding block | 
| posY | int | y coordinate of the colliding block | 
| posZ | int | z coordinate of the colliding block | 
| blockId | str | identifier of the colliding block | 
| auxValue | int | additional value of the colliding block | 
| dimensionId | int | dimension id | 

- Return value 

None 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

### Related Interfaces 

<span id="OpenPlayerHitBlockDetection"></span> 
### OpenPlayerHitBlockDetection 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Enable collision block detection. When enabled, the OnPlayerHitBlockServerEvent event will be triggered 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| precision | float | Collision detection precision. The parameter needs to be in the interval [0, 1) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 


- Notes 
- Note: This collision detection will block grass, air, fire, and tall grass 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.OpenPlayerHitBlockDetection(0.0001) 
``` 

<span id="ClosePlayerHitBlockDetection"></span> 
### ClosePlayerHitBlockDetection 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Turn off collision detection. After turning it off, the OnPlayerHitBlockServerEvent event will not be triggered 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.ClosePlayerHitBlockDetection() 
``` 

## PerspChangeClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Events triggered when the perspective is switched 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| from | int | Perspective before switching | 
| to | int | Perspective after switching | 

- Return value 

None 

- Remarks 
- Perspective number represents meaning 
0: First person 
1: Third person back 
2: Third person front 

## PlayerAttackEntityEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: This event is triggered when the player attacks. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
| victimId | str | Victim id | 
| damage | int | Damage value: The value passed by the engine is 0. The script layer can be modified to other numbers | 
| isValid | int | Whether the script sets the damage value: 1 means yes; 0 means no | 
| cancel | bool | Whether to cancel the attack, not canceled by default | 
| isKnockBack | bool | Whether to support the knockback effect, supported by default, and the weapon knockback enchantment effect will be blocked if not supported | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerCheatSpinAttackServerEvent 

<span style="display:inline;color:#ff5555">Only available in Apollo</span> 

- Description


Trigger timing: When the player starts/ends a fast spin attack and does not meet the conditions for sending a fast spin attack (equipped with a trident enchanted with Riptide, in water or rain, and not riding) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player's entityId | 
| isStart | bool | True means starting a fast spin attack; False means ending a fast spin attack | 

- Return value 

None 

- Remarks 
- If there is no custom item like a trident/Riptide enchantment, then triggering this event means that this player is likely to use the [Killing Aura] plug-in 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Parts Development.html#Parts Event">Parts Event</a> 

## PlayerDieEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: This event is triggered when the player dies. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Player id | 
| attacker | str | Damage source id | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerDoInteractServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

This event is triggered when a player interacts with a creature with a minecraft:interact component, such as a player holding an empty bucket to milk a cow, or a player holding a flint and steel to ignite a creeper.

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
| itemDict | dict | Item information dictionary for items used during interaction | 
| interactEntityId | str | Interacting creature entityId | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerEatFoodServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: Triggered when the player eats food 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of food items | 
| hunger | int | Hunger value added by food, modifiable | 
| nutrition | float | Nutritional value of food, saturation recovery = Hunger value added by food * Nutritional value of food * 2. The maximum saturation does not exceed the current hunger value and can be modified | 

- Return value 

None 

- Notes 
- Eating cake and drinking milk will not trigger this event 

Simply declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerHurtEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: This event is triggered before the player is hurt. 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Target player id | 
| attacker | str | Entity id of the source of damage. If there is no entity attack, such as falling from a high altitude, the id is -1 | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerInteractServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: When the player can interact with the entity. If in mouse control mode, it is triggered when the crosshair is facing an entity. If in touch mode, it is triggered when the interaction button at the bottom of the screen is displayed. For events where the player actually interacts with an entity, see [PlayerDoInteractServerEvent](#playerdointeractserverevent) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| cancel | bool | Whether to cancel the trigger, the default is False, if set to True, it can prevent the subsequent entity interaction events from being triggered | 
| playerId | str | The unique ID of the player who actively interacts with the entity | 
| itemDict | dict | The current player's holding item's <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| victimId | str | The unique ID of the passive entity | 

- Return value 

None 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerRespawnEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: The event is triggered when the player is resurrected. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| id | str | player id | 

- Return value 

None 

- Remarks 

This event is triggered when the player clicks the respawn button, but the player may not have completed the resurrection when it is triggered. At this time, please do not perform operations such as cutting dimensions or setting health points on the player. 
In general, it is recommended to use PlayerRespawnFinishServerEvent 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerRespawnFinishServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: Trigger when the player is resurrected 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 

- Return value 

None 

- Notes 
- When this event is triggered, the player has already reborn and can safely use operations such as cutting dimensions 
- Returning to the main world through the end portal is also considered rebirth, and this event will also be triggered 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerSleepServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

The player successfully sleeps on the bed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| playerId | str | player id | 

- Return value 

None 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerSpinAttackServerEvent 

<span style="display:inline;color:#ff5555">Apollo only</span> 

- Description 

Trigger timing: Triggered when the player starts/ends a fast spin attack 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player's entityId | 
| isInWaterOrRain | bool | Is it in water or rain? | 
| isRiding | bool | Is it riding? | 
| isStart | bool | True means starting a fast spinning attack; False means ending a fast spinning attack | 

- Return value 

None 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerStopSleepServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Player stops sleeping 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 

- Return value 

None


Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerTeleportEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: This event is triggered when the player teleports, such as when the player uses the ender pearl or tp command. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Player id | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## PlayerTrySleepServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

The player tries to use the bed to sleep 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 
| cancel | bool | cancel (passed in by the developer) | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ServerPlayerGetExperienceOrbEvent 

<span style="display:inline;color:#ff5555">Server</span>


- Description 

Triggering time: The event is triggered when the player obtains the experience ball 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 
| experienceValue | int | Experience value of experience ball | 
| cancel | bool | Whether to cancel (input by the developer) | 

- Return value 

None 

- Notes 
- When the `cancel` value is set to True, the picked up experience ball will not increase the experience value, but the experience ball will disappear. 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## StoreBuySuccServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: Event thrown by the server when the player purchases goods in the game 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id who purchased the goods | 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi
self.ListenForEvent(serverApi.GetEngineNamespace(),serverApi.GetEngineSystemName(),
    "StoreBuySuccServerEvent",
    self, self.OnStoreBuySucc)
def OnStoreBuySucc(self, args):
    entityId = args['playerId']

print 'Ship Item.EntityId:', playerId 
``` 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

