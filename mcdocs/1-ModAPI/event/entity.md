--- 
sidebarDepth: 1 
--- 
# Entity 

# Index 

| Event | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [ActorHurtServerEvent](Entity.md#actorhurtserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger: Trigger when a creature (including the player) is hurt | 
| [ActuallyHurtServerEvent](Entity.md#actuallyhurtserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger when the entity is actually hurt. Compared to DamageEvent, this damage is the actual amount of health lost after armor and buff calculations | 
| [AddEffectServerEvent](Entity.md#addeffectserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when: Entity gains status effect | 
| [ApproachEntityClientEvent](Entity.md#approachentityclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when the player approaches the mob | 
| [ChangeSwimStateServerEvent](Entity.md#changeswimstateserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when: Entity starts or ends swimming | 
| [DamageEvent](Entity.md#damageevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the entity takes damage | 
| [EntityChangeDimensionServerEvent](Entity.md#entitychangedimensionserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Thrown by the server when the entity dimension changes | 
| [EntityDefinitionsEventServerEvent](entity.md#entitydefinitionseventserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: Triggered at the same time as the event set in the creature definition json file is triggered. Mob behavior change event | 
| [EntityDieLoottableServerEvent](Entity.md#entitydieloottableserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: When a mob dies and drops an item | 
| [EntityDroppedItemServerEvent](Entity.md#entitydroppeditemserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: When a mob throws an item | 
| [EntityEffectDamageServerEvent](Entity.md#entityeffectdamageserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Mob status damage/recovery event. | 
| [EntityLoadScriptEvent](Entity.md#entityloadscriptevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the database loads entity custom data | 
| [EntityModelChangedClientEvent](Entity.md#entitymodelchangedclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Trigger time: Triggered when the entity model is switched | 
| [EntityMotionStartServerEvent](Entity.md#entitymotionstartserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Entity motion start event. After an entity (including the player) adds a motion machine, it is triggered when the motion machine starts running. | 
| [EntityMotionStopServerEvent](Entity.md#entitymotionstopserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Entity motion machine stop event. After an entity (including the player) adds a motion machine and starts running, the motion machine automatically stops. | 
| [EntityPickupItemServerEvent](Entity.md#entitypickupitemserverevent) | <span style="display:inline;color:#ff5555">Server</span> | This event is triggered when a mob with the minecraft:behavior.pickup_items behavior picks up an item, such as a villager picking up bread or a piglin picking up a gold ingot. | 
| [EntityStartRidingEvent](Entity.md#entitystartridingevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when an entity rides another entity | 
| [EntityStopRidingEvent](Entity.md#entitystopridingevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: when the entity stops riding | 
| [EntityStopRidingEvent](Entity.md#entitystopridingevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when: When the entity stops riding | 
| [EntityTickServerEvent](Entity.md#entitytickserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when the entity ticks. This event is 20 frames per second. You need to use AddEntityTickEventWhiteList to add a whitelist of entity types that trigger this event. | 
| [HealthChangeBeforeServerEvent](entity.md#healthchangebeforeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired before the creature's health value changes | 
| [HealthChangeClientEvent](entity.md#healthchangeclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Fired when the creature's health value changes | 
| [HealthChangeServerEvent](entity.md#healthchangeserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Fired when the creature's health value changes | 
| [LeaveEntityClientEvent](entity.md#leaveentityclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Fired when the player leaves the creature | 
| [MobDieEvent](entity.md#mobdieevent) | <span style="display:inline;color:#ff5555">Server</span> | Fires when the entity is killed by the player | 
| [MobGriefingBlockServerEvent](entity.md#mobgriefingblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Fires when an ambient mob changes blocks. The timing of the trigger is the same as the behavior affected by the mobgriefing game rule | 
| [OnFireHurtEvent](entity.md#onfirehurtevent) | <span style="display:inline;color:#ff5555">Server</span> | Fires when a mob takes fire damage | 
| [OnGroundClientEvent](entity.md#ongroundclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Entity landing event. Triggered when a player, sand, anvil, dropped items, or ignited TNT falls to the ground. Other entities landing do not trigger. | 
| [OnGroundServerEvent](entity.md#ongroundserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Entity landing event. Entity, dropped items, or lit TNT hitting the ground | 
| [OnKnockBackServerEvent](Entity.md#onknockbackserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Entity is knocked back | 
| [OnMobHitBlockServerEvent](Entity.md#onmobhitblockserverevent) | <span style="display:inline;color:#ff5555">Server</span> | When: After OpenMobHitBlockDetection is enabled, this event is triggered when a mob (not including the player) collides with a block. | 
| [OnMobHitMobClientEvent](Entity.md#onmobhitmobclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggering time: After OpenPlayerHitMobDetection is used to turn on creature collision detection, this event is triggered when creatures (including players) collide with each other. Note: The client and server perform collision detection separately, and the two events may return slightly different results. | 
| [OnMobHitMobServerEvent](Entity.md#onmobhitmobserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: After OpenPlayerHitMobDetection is used to turn on creature collision detection, this event is triggered when creatures (including players) collide with each other. Note: The client and server perform collision detection separately, and the two events may return slightly different results. | 
| [ProjectileCritHitEvent](Entity.md#projectilecrithitevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: This event is triggered when the projectile collides with the head. Note: This event can only be triggered after calling OpenPlayerCritBox to enable the player's headshot. | 
| [ProjectileDoHitEffectEvent](entity.md#projectiledohiteffectevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: This event is triggered when the projectile collides | 
| [RefreshEffectServerEvent](entity.md#refresheffectserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: Triggered when the status effect on the entity is updated. Update conditions 1. The level of the newly added status is high, and the status level and time are updated; 2. The level of the newly added status remains unchanged, and the time is long, so the status duration is updated | 
| [RemoveEffectServerEvent](entity.md#removeeffectserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger time: When the status effect on the entity is removed | 
| [SpawnProjectileServerEvent](entity.md#spawnprojectileserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when: projectile spawns | 
| [StartRidingClientEvent](entity.md#startridingclientevent) | <span style="display:inline;color:#7575f9">Client</span> | Triggered when: an entity is about to ride another entity | 
| [StartRidingServerEvent](entity.md#startridingserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggered when: an entity is about to ride another entity | 
| [WillAddEffectServerEvent](entity.md#willaddeffectserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Triggering time: Before the entity gains a status effect |

| [WillTeleportToServerEvent](entity.md#willteleporttoserverevent) | <span style="display:inline;color:#ff5555">Server</span> | Entity is about to teleport or switch dimensions | 
# Entity 

## ActorHurtServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: Triggered when a creature (including the player) is injured 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Creature Id | 
| cause | str | Damage source, see [ActorDamageCause](../enumeration/ActorDamageCause.md) in the Minecraft enumeration document for details | 
| damage | int | Damage value (value after damage absorption), cannot be modified | 
| absorbedDamage | int | Damage value absorbed by damage absorption effect | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ActuallyHurtServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the entity actually receives damage. Compared with DamageEvent, this damage is the actual amount of health deduction after armor and buff calculation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| srcId | str | Damage source id | 
| projectileId | str | Projectile id | 
| entityId | str | Damaged id | 
| damage | int | Damage value (value after damage absorption), modification is allowed, if set to 0, the damage caused this time is 0 | 
| cause | str | Damage source, see [ActorDamageCause](../enumeration value/ActorDamageCause.md) in the Minecraft enumeration value document for details | 

- Return value 

None 

- Remarks

- Damage caused by potions and status effects is not triggered, you can use ActorHurtServerEvent 

Declare a function with the same name in the part directly to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## AddEffectServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: when the entity obtains a status effect 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| effectName | str | Name of the entity's status effect | 
| effectDuration | int | Duration of the status effect, in seconds | 
| effectAmplifier | int | The amplification factor of the status effect | 
| damage | int | The damage value caused by the status (the actual amount of health deducted). Only useful when the duration is 0 | 

- Return value 

None 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## ApproachEntityClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the player approaches the creature 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player entity id | 
| entityId | str | Approaching creature entity id | 

- Return value 

None 

Just declare a function with the same name in the part to complete the monitoring. For details, please refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a>



## ChangeSwimStateServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: When the entity starts or ends swimming 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Unique ID of the entity | 
| formState | bool | Whether the entity is in the swimming state before the event is triggered | 
| toState | bool | Whether the entity is in the swimming state after the event is triggered | 

- Return value 

None 

- Remarks 
- When the state of the entity does not change, this event will not be triggered, that is, formState and toState must be one true and one false 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## DamageEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the entity is damaged 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| srcId | str | Damage source id | 
| projectileId | str | Projectile id | 
| entityId | str | Damage id | 
| damage | int | Damage value (value before damage absorption), modification is allowed, if set to 0, the damage caused this time is 0 | 
| absorption | int | Damage absorbs health, see ABSORPTION in [AttrType enumeration](../enumeration value/AttrType.md) for details | 
| cause | str | Damage source, see [ActorDamageCause](../enumeration value/ActorDamageCause.md) in Minecraft enumeration value document | 
| knock | bool | Whether to knock back the attacker, modification is allowed, setting this value to False will not produce knockback | 
| ignite | bool | Whether to ignite the victim, modification is allowed, setting this value to True will produce ignition effect, and vice versa | 

- Return value


None 

- Notes 
- The damage value will be absorbed by armor and absorption, and is not necessarily the final amount of health lost. Setting this damage value can cancel damage, but it will not cancel damage caused by knockback or ignition effects. 
- This event is triggered before the entity is injured. Since some damage is processed in the tick, the event will be triggered every frame when the injury is continuously triggered (such as standing in fire) (you can use ActorHurtServerEvent to avoid this). 
- The damage here is the attack damage value of the damage source, not the actual amount of health lost by the entity. If you need to get the real damage, you can use the ActuallyHurtServerEvent event. 
- When the target cannot be knocked back, the knock value is invalid 
- Damage caused by potions and status effects is not triggered, you can use ActorHurtServerEvent 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## EntityChangeDimensionServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Thrown by the server when the entity dimension changes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
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

- Remarks 
- When an entity transfers a dimension, if the chunk at the corresponding position of the corresponding dimension has not been loaded, the entity will be cached in the buffer of the dimension itself until the corresponding chunk is loaded. The throwing of this event only means that the entity disappears from the original dimension, not that it will definitely appear in the corresponding dimension 
- Note that this event is not triggered when the player dimension changes, but the DimensionChangeServerEvent event will be triggered 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Parts Development.html#Parts Event">Parts Event</a> 

## EntityDefinitionsEventServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 


- Description 

Trigger timing: Triggered at the same time as the event set in the creature definition json file. Biological behavior change event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Biological id | 
| eventName | str | Triggered event name | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## EntityDieLoottableServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: When the creature dies and drops items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dieEntityId | str | entityId of the dead entity | 
| attacker | str | entityId of the source of damage | 
| itemList | list(dict) | Dropped item list, each element is an itemDict, the format can refer to <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> | 
| dirty | bool | Defaults to False, if you need to modify the drop list, set the value to True | 

- Return value 

None 

- Notes 
- Only when dirty is True will the item list be re-read and the corresponding dropped items generated. If you do not need to modify the drop result, please do not modify the dirty value at will. 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## EntityDroppedItemServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description


Trigger timing: Triggered when the creature throws an item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Creature ID | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">Item Information Dictionary</a> of the thrown item | 
| itemEntityId | str | Item Entity ID | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Parts Development.html#Parts Event">Parts Event</a> 

## EntityEffectDamageServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Event in which the creature receives status damage/recovery. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| damage | int | Damage value (actual amount of health deducted after damage absorption), negative number indicates life recovery | 
| attributeBuffType | int | Status type, refer to [AttributeBuffType](../enumeration value/AttributeBuffType.md) | 
| duration | float | Status duration, unit seconds (s) | 
| lifeTimer | float | Status life time, unit seconds (s) | 
| isInstantaneous | bool | Whether it is an immediate effective state | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Parts Development.html#Parts Event">Parts Event</a> 

## EntityLoadScriptEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 


Triggered when the database loads entity custom data 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| args | list | The parameter of this event is a list of length 2, not a dict, where the first element of the list is the entity id | 

- Return value 

None 

- Remarks 
- Only entities that have used the extraData component have this event. When triggered, the custom data of the entity can be obtained through the extraData component 

## EntityModelChangedClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Trigger time: Triggered when the entity model is switched 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | entity id | 
| newModel | str | new model name | 
| oldModel | str | original model name | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## EntityMotionStartServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Entity motion start event. After the entity (including the player) adds the motion machine, the motion machine starts running. Triggered 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| motionId | int | Motion device id | 
| entityId | str | Entity id | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## EntityMotionStopServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Entity motion stop event. After an entity (including the player) adds a motion machine and starts running, it is triggered when the motion machine stops automatically. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| motionId | int | Motion machine id | 
| entityId | str | Entity id | 
| remove | bool | Whether to remove the motion machine. If set to False, it will be retained. The default is True, which means that the motion machine will be automatically removed after it stops. This parameter setting is only valid for non-player entities | 

- Return value 

None 

- Notes 
- Note: The triggering of this event indicates that the motion device playback is completed successfully. Manually calling [StopEntityMotion](../Interface/Entity/Behavior.md#StopEntityMotion), [RemoveEntityMotion](../Interface/Entity/Behavior.md#RemoveEntityMotion) and the motion device stopping caused by the entity being destroyed will not trigger this event. 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## EntityPickupItemServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

This event is triggered when a creature with the minecraft:behavior.pickup_items behavior picks up an item, such as a villager picking up bread and a piglin picking up a gold ingot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| entityId | str | creature id | 
| itemDict | dict | <a href="../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary">item information dictionary</a> of the picked up item | 
| secondaryActor | str | item giver id (usually the player), if there is no giver, this is an empty string | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## EntityStartRidingEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when an entity rides on another entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Rider entity id | 
| rideId | str | Rider entity id | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## EntityStopRidingEvent 

<span style="display:inline;color:#ff5555">Server</span><span style="display:inline;color:#7575f9">Client</span> 

<span id="server"></span> 
### Server-side events 

- Description 

Trigger time: When the entity stops riding 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 
| rideId | str | Mount id |

| exitFromRider | bool | Whether to dismount | 
| entityIsBeingDestroyed | bool | Whether the mount is about to be destroyed | 
| switchingRides | bool | Whether to switch mounts | 
| cancel | bool | Set to True to cancel (need to cancel together with client events) | 

- Return value 

None 

- Notes 
- Cancellation is not allowed in the following situations 
1. Ride component StopEntityRiding interface 
2. When the player teleports 
3. When the mount dies 
4. When the player sleeps 
5. When the player dies 
6. Untamed horses 
7. The mount of a water-afraid creature enters the water 
8. Switching dimensions 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

<span id="client"></span> 
### Client Event 

- Description 

Triggering time: When the entity stops riding 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 
| rideId | str | Mount id | 
| exitFromRider | bool | Whether to get off the mount | 
| entityIsBeingDestroyed | bool | Whether the mount is about to be destroyed | 
| switchingRides | bool | Whether to switch the mount | 
| cancel | bool | Set to True to cancel (need to be canceled together with the server event) | 

- Return value 

None 

- Notes 
- Cancellation is not allowed in the following situations 
1. Ride component StopEntityRiding interface 
2. When the player teleports 
3. When the mount dies

4. When the player is sleeping 
5. When the player dies 
6. Untamed horses 
7. When a water-afraid creature mounts into the water 
8. Switching dimensions 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## EntityTickServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the entity ticks. This event is 20 frames per second. You need to use AddEntityTickEventWhiteList to add a whitelist of entity types that trigger this event. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| identifier | str | Entity identifier | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

### Related interfaces 

<span id="AddEntityTickEventWhiteList"></span> 
### AddEntityTickEventWhiteList 

method in mod.server.extraServerApi 

- Description 

Add entity types to the trigger whitelist of EntityTickServerEvent events.

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| identifier | str | Entity type name, the original entity needs to add the minecraft namespace | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
# Let the cow trigger the EntityTickServerEvent event 
serverApi.AddEntityTickEventWhiteList('minecraft:cow') 
``` 

## HealthChangeBeforeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered before the creature's health value changes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| from | float | Health value before change | 
| to | float | Health value to be changed. Set cancel to True to cancel the change, but this parameter remains unchanged | 
| byScript | bool | Whether the change is generated by calling SetAttrValue or SetAttrMaxValue | 
| cancel | bool | Whether to cancel the change | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## HealthChangeClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the biological health value changes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| entityId | str | entity id | 
| from | float | health value before change | 
| to | float | health value after change | 

- Return value 

None 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## HealthChangeServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the biological health value changes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | entity id | 
| from | float | health value before change | 
| to | float | health value after change | 
| byScript | bool | whether the change is generated by calling SetAttrValue or SetAttrMaxValue | 

- Return value 

None 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## LeaveEntityClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggered when the player moves away from the creature 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player entity id | 
| entityId | str | mob entity id to move away from |


- Return value 

None 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## MobDieEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the entity is killed by the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 
| attacker | str | Damage source id | 

- Return value 

None 

- Remarks 
- Note: The player's handheld items cannot be modified in this event callback, such as [SpawnItemToPlayerCarried](../Interface/Player/Backpack.md#spawnitemtoplayercarried), [ChangePlayerItemTipsAndExtraId](../Interface/Player/Backpack.md#changeplayeritemtipsandextraId) and other interfaces 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## MobGriefingBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the environmental creature changes the block. The triggering timing is the same as the behavior affected by the mobgriefing game rules 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| cancel | bool | Whether to allow triggering, the default is False, if set to True, it can prevent the subsequent physical interaction events from being triggered | 
| blockX | int | Block x coordinate | 
| blockY | int | Block y coordinate | 
| blockZ | int | Block z coordinate | 
| entityId | str | The unique ID of the triggered entity |

| blockName | str | block identifier, including namespace and name | 
| dimensionId | int | dimension id | 

- Return value 

None 

- Notes 
- Triggering times include: creatures trampling farmland, destroying a single block, breaking a door, fire arrows igniting blocks, wither boss destroying blocks, ender dragon destroying blocks, enderman picking up blocks, silverfish destroying infested blocks, silverfish turning blocks into infested blocks, wither killing creatures to generate wither roses, creatures trampling turtle eggs. 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnFireHurtEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when the creature is damaged by fire 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| victim | str | Injured entity id | 
| src | str | Flame creator id | 
| fireTime | float | Ignition time, in seconds | 
| cancel | bool | Whether to cancel the fire damage here | 

- Return value 

None 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnGroundClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Entity landing event. It is triggered when the player, sand, anvil, dropped items, and ignited TNT fall to the ground. Other entities landing will not trigger. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id |


- Return value 

None 

You can complete the monitoring by directly declaring a function with the same name in the part. For details, please refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnGroundServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Entity landing event. Triggered when an entity, dropped item, or ignited TNT falls to the ground 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## OnKnockBackServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggered when an entity is knocked back 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Entity id | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 



## OnMobHitBlockServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Triggering time: After opening block collision detection through OpenMobHitBlockDetection, this event is triggered when a creature (excluding players) collides with a block. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Id of the creature that collides with the block | 
| posX | int | x coordinate of the collision block | 
| posY | int | y coordinate of the collision block | 
| posZ | int | z coordinate of the collision block | 
| blockId | str | identifier of the collision block | 
| auxValue | int | additional value of the collision block | 
| dimensionId | int | dimension id | 

- Return value 

None 

You can complete the monitoring by directly declaring a function of the same name in the part. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

### Related Interfaces 

<span id="OpenMobHitBlockDetection"></span> 
### OpenMobHitBlockDetection 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Enable collision block detection. When enabled, the OnMobHitBlockServerEvent event will be triggered when the creature (excluding the player) collides with the block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity ID of the creature | 
| precision | float | Collision detection accuracy, the parameter needs to be in the interval [0, 1) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful |


- Notes 
- Note: This collision detection will block grass, air, fire, and tall grass. 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.OpenMobHitBlockDetection("-123456",0.0001) 
``` 

<span id="CloseMobHitBlockDetection"></span> 
### CloseMobHitBlockDetection 

method in mod.server.component.gameCompServer.GameComponentServer 

- Description 

Turn off the detection of collision blocks. After turning it off, the OnMobHitBlockServerEvent event will not be triggered when creatures (excluding players) collide with blocks. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity ID of the creature | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreateGame(levelId) 
comp.CloseMobHitBlockDetection("-123456") 
``` 

## OnMobHitMobClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description


Triggering time: After opening the creature collision detection through OpenPlayerHitMobDetection, this event is triggered when creatures (including players) collide with each other. Note: The client and server perform collision detection separately, and the two events may return slightly different results. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| mobId | str | The id of the current mob | 
| hittedMobList | list[str] | The list of all other mob ids that the current mob has collided with | 

- Return value 

None 

- Remarks 
- This event replaces the original OnPlayerHitMobClientEvent event 

- Example 

```python 
# ClientSystem 
import mod.client.extraClientApi as clientApi 
self.ListenForEvent(clientApi.GetEngineNamespace(), 
clientApi.GetEngineSystemName(), 
"OnMobHitMobClientEvent", 
self, self.OnMobHitMobClientEvent) 
def OnMobHitMobClientEvent(self, args): 
mobId = args.get('mobId', '') 
hittedMobs = args.get('hittedMobList', []) 
``` 

### Related interfaces 

<span id="OpenPlayerHitMobDetection"></span> 
### OpenPlayerHitMobDetection 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Enable collision detection for other creatures. When it is enabled, the OnMobHitMobClientEvent event will be triggered when a collision occurs with a creature. (This interface is also valid for creatures) 

- Parameters 

None 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether it is opened successfully | 

- Notes 
- This interface is also valid for creatures 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.OpenPlayerHitMobDetection() 
``` 

<span id="ClosePlayerHitMobDetection"></span> 
### ClosePlayerHitMobDetection 

method in mod.client.component.playerCompClient.PlayerCompClient 

- Description 

Close the detection of collision creatures. After closing, the OnMobHitMobClientEvent event will not be triggered. (This interface is also valid for creatures) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the closure is successful | 

- Notes 
- This interface is also valid for creatures 

- Example 

```python 
import mod.client.extraClientApi as clientApi 
comp = clientApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.ClosePlayerHitMobDetection() 
``` 

## OnMobHitMobServerEvent


<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: After opening the creature collision detection through OpenPlayerHitMobDetection, this event is triggered when creatures (including players) collide with each other. Note: The client and server perform collision detection separately, and the two events may return slightly different results. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| mobId | str | The id of the current mob | 
| hittedMobList | list[str] | The list of all other mob ids that the current mob has collided with | 

- Return value 

None 

- Remarks 
- This event replaces the original OnPlayerHitMobServerEvent event 

- Example 

```python 
# ServerSystem 
import mod.server.extraServerApi as serverApi 
self.ListenForEvent(serverApi.GetEngineNamespace(), 
serverApi.GetEngineSystemName(), 
"OnMobHitMobServerEvent", 
self, self.OnMobHitMobServerEvent) 
def OnMobHitMobServerEvent(self, args): 
mobId = args.get('mobId', '') 
hittedMobs = args.get('hittedMobList', []) 
``` 

### Related interfaces 

<span id="OpenPlayerHitMobDetection"></span> 
### OpenPlayerHitMobDetection 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Enable collision detection for other creatures. When it is enabled, the OnMobHitMobServerEvent event will be triggered when a collision occurs with a creature. (This interface is also valid for creatures) 

- Parameters 


None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether it is opened successfully | 

- Notes 
- This interface is also valid for creatures 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.OpenPlayerHitMobDetection() 
``` 

<span id="ClosePlayerHitMobDetection"></span> 
### ClosePlayerHitMobDetection 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Close the detection of collision creatures. After closing, the OnMobHitMobServerEvent event will not be triggered. 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the closure is successful | 

- Notes 
- This interface is also valid for creatures 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.ClosePlayerHitMobDetection() 
```



## ProjectileCritHitEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: This event is triggered when the projectile collides with the head. Note: This event can only be triggered after calling OpenPlayerCritBox to enable the player's headshot. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Bullet id | 
| targetId | str | Collision target id | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

### Related interfaces 

<span id="OpenPlayerCritBox"></span> 
### OpenPlayerCritBox 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Enable player headshots. When enabled, ProjectileCritHitEvent will be triggered when the player's head is hit. 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.OpenPlayerCritBox()

``` 

<span id="ClosePlayerCritBox"></span> 
### ClosePlayerCritBox 

method in mod.server.component.playerCompServer.PlayerCompServer 

- Description 

Close the player's headshot. After closing, the ProjectileCritHitEvent event will not be triggered. 

- Parameters 

None 

- Return value 

None 

- Example 

```python 
import mod.server.extraServerApi as serverApi 
comp = serverApi.GetEngineCompFactory().CreatePlayer(playerId) 
comp.ClosePlayerCritBox() 
``` 

## ProjectileDoHitEffectEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: This event is triggered when the projectile collides 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| id | str | Bullet id | 
| hitTargetType | str | Collision target type, 'ENTITY' or 'BLOCK' | 
| targetId | str | collision target id | 
| hitFace | int | face id that hits the block, refer to [Facing enumeration](../enumeration value/Facing.md) | 
| x | float | collision x coordinate | 
| y | float | collision y coordinate | 
| z | float | collision z coordinate |

| blockPosX | int | x coordinate of the block when the collision is a block | 
| blockPosY | int | y coordinate of the block when the collision is a block | 
| blockPosZ | int | z coordinate of the block when the collision is a block | 
| srcId | str | creator id | 
| cancel | bool | whether to cancel this collision event, if canceled, it can be set to True | 

- Return value 

None 

- Example 

```python 
# ServerSystem 
import mod.server.extraServerApi as serverApi 
# Listen for engine events: self refers to an instance of the ServerSystem class ProjectileDoHitEffectEvent is a system event 
self.ListenForEvent(serverApi.GetEngineNamespace(), serverApi.GetEngineSystemName(), 
"ProjectileDoHitEffectEvent", self, self.OnProjectileDoHitEffectEvent) 
def OnProjectileDoHitEffectEvent(self, args): 
# Set to True to cancel the projectile collision event 
args["cancel"] = True 
``` 

Declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## RefreshEffectServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: Triggered when the status effect on the entity is updated. Update conditions 1. The newly added status level is higher, and the status level and time are updated; 2. The newly added status level remains unchanged, the time is longer, and the status duration is updated 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| effectName | str | Name of the updated status effect | 
| effectDuration | int | Remaining duration of the status effect after update, in seconds | 
| effectAmplifier | int | Amplification factor of the updated status effect | 
| damage | int | Damage value caused by the status, such as potion | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 



## RemoveEffectServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: when the status effect on the entity is removed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| effectName | str | Name of the removed status effect | 
| effectDuration | int | Remaining duration of the removed status effect, in seconds | 
| effectAmplifier | int | Amplification factor of the removed status effect | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## SpawnProjectileServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: Trigger when the projectile is generated 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| projectileId | str | Projectile entity id | 
| projectileIdentifier | str | Projectile identifier | 
| spawnerId | str | Launcher entity id, -1 when there is no launcher | 

- Return value 

None 

- Notes 
- The auxvalue of the projectile entity cannot be obtained in this event. If necessary, you can delay the acquisition by one frame, or obtain it in ProjectileDoHitEffectEvent 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 



## StartRidingClientEvent 

<span style="display:inline;color:#7575f9">Client</span> 

- Description 

Triggering time: an entity is about to ride another entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| actorId | str | The unique ID of the rider | 
| victimId | str | The unique ID of the ridden entity | 

- Return value 

None 

- Remarks 
- If you need to modify cancel, please modify it synchronously through the server event StartRidingServerEvent. When the client triggers this event, the entity has already ridden successfully. 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## StartRidingServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger timing: an entity is about to ride another entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| cancel | bool | Whether to allow triggering, the default is False. If set to True, subsequent entity interaction events can be prevented from being triggered | 
| actorId | str | The unique ID of the rider | 
| victimId | str | The unique ID of the ridden entity | 

- Return value 

None 

Directly declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## WillAddEffectServerEvent


<span style="display:inline;color:#ff5555">Server</span> 

- Description 

Trigger time: before the entity gets the status effect 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 
| effectName | str | Name of the status effect the entity gets | 
| effectDuration | int | Duration of the status effect, in seconds | 
| effectAmplifier | int | Amplification factor of the status effect | 
| cancel | bool | Set to True to cancel | 
| damage | int | The damage value that the status will cause, such as potion; Note that this value is not necessarily the final damage value, for example, it is deducted by the damage absorption effect. Only useful when the duration is 0 | 

- Return value 

None 

Declare a function with the same name directly in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Part Development.html#Part Event">Part Event</a> 

## WillTeleportToServerEvent 

<span style="display:inline;color:#ff5555">Server</span> 

- Description 

The entity is about to teleport or switch dimensions 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| cancel | bool | Whether to allow triggering, the default is False, if set to True, it can prevent the subsequent transmission from being triggered | 
| entityId | str | Unique ID of the entity | 
| fromDimensionId | int | Dimension before teleporting | 
| toDimensionId | int | Target dimension after teleporting | 
| fromX | int | x-coordinate before teleporting | 
| fromY | int | y-coordinate before teleporting | 
| fromZ | int | z-coordinate before teleporting | 
| toX | int | x-coordinate of the target location after teleporting | 
| toY | int | y-coordinate of the target location after teleporting | 
| toZ | int | z-coordinate of the target location after teleporting | 
| cause | str | Reason for teleporting, see MinecraftEnum.EntityTeleportCause for details | 

- Return value


None 

- Notes 
- If the target dimension has not been created in memory (i.e., no player has entered this dimension after the server is started and before the transmission), then the target location coordinates returned in the event are generated by the algorithm and cannot be guaranteed to be correct. 

Simply declare a function with the same name in the part to complete the monitoring. For details, refer to <a href="../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/0-Parts Development.html#Parts Event">Parts Event</a> 

