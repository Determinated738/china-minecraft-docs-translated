--- 
sidebarDepth: 1 
--- 
# SDK interface encapsulation SdkInterface 

## Overview 

- Description 

SdkInterface is the base class for SDK interface encapsulation. 

- Member variables 

| Variable name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Associated entity ID | 
| isClient | bool | Whether client | 

## Index 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetEntityId](#getentityid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get object entity ID | 
| [ToPlayerPreset](#toplayerpreset) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Force type conversion to player preset | 
| [ToEntityPreset](#toentitypreset) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Force type conversion to entity preset | 
| [ToEffectPreset](#toeffectpreset) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Force type conversion to effect preset | 
| [ToBlockPreset](#toblockpreset) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Force type conversion to block preset | 
| [ToUIPreset](#touipreset) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Force type conversion to UI preset | 
| [GetServerSystem](#getserversystem) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Returns the server system available to the current object | 
| [GetClientSystem](#getclientsystem) | style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Returns the client system that the current object can use | 
| [GetSystem](#getsystem) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Returns the system that the current object can use | 
| [GetLevelId](#getlevelid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Gets the level_id of the current object | 
| [CreateComponent](#createcomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create a component for an entity | 
| [GetMinecraftEnum](#getminecraftenum) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Used to get the enumeration value in the enumeration value document | 
| [DestroyEntity](#destroyentity) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Destroy an entity | 
| [CreateActionComponent](#createactioncomponent) | style="display:inline;color:#ff5555">Server</span> | Create action component | 
| [SetEntityAttackTarget](#setentityattacktarget) | <span style="display:inline;color:#ff5555">Server</span> | Set the target of hatred | 
| [ResetEntityAttackTarget](#resetentityattacktarget) | <span style="display:inline;color:#ff5555">Server</span> | Clear the target of hatred | 
| [GetEntityAttackTarget](#getentityattacktarget) | <span style="display:inline;color:#ff5555">Server</span> | Get the target of hatred | 
| [SetMobKnockback](#setmobknockback) | <span style="display:inline;color:#ff5555">Server</span> | Set the initial speed of the knockback, and consider the influence of resistance | 
| [CreateActorLootComponent](#createactorlootcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create actorLoot component | 
| [SpawnLootTable](#spawnloottable) | <span style="display:inline;color:#ff5555">Server</span> | Use the creature type to simulate a random drop, and the generated items are related to the probability defined in json | 
| [SpawnLootTableWithActor](#spawnloottablewithactor) | <span style="display:inline;color:#ff5555">Server</span> | Use the creature instance to simulate a random drop, and the generated items are related to the probability defined in json | 
| [CreateActorMotionComponent](#createactormotioncomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create actorMotion component | 
| [GetDirFromRot](#getdirfromrot) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the orientation by the rotation angle | 
| [SetEntityMotion](#setentitymotion) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the instantaneous movement direction vector of the creature. The server can only be used for non-players, and the client can only be used for local players |

| [GetEntityMotion](#getentitymotion) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the instantaneous moving direction vector of the creature (including the player) | 
| [GetInputVector](#getinputvector) | <span style="display:inline;color:#7575f9">Client</span> | Get the input of the local player's direction keys (movement wheel) | 
| [LockInputVector](#lockinputvector) | <span style="display:inline;color:#7575f9">Client</span> | Lock the input of the local player's direction keys (movement wheel), which allows the local player to continue to move in the specified direction and will no longer be affected by the player's input | 
| [UnlockInputVector](#unlockinputvector) | <span style="display:inline;color:#7575f9">Client</span> | Unlock the input of the local player's arrow keys (moving the wheel) | 
| [CreateActorOwnerComponent](#createactorownercomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create actorOwner component | 
| [SetEntityOwner](#setentityowner) | <span style="display:inline;color:#ff5555">Server</span> | Set the owner of the entity | 
| [GetEntityOwner](#getentityowner) | <span style="display:inline;color:#ff5555">Server</span> | Get the owner of the entity | 
| [CreateActorPushableComponent](#createactorpushablecomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create actorPushable component | 
| [SetActorPushable](#setactorpushable) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the entity is pushable | 
| [CreateAttrComponent](#createattrcomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create attr component | 
| [IsEntityOnFire](#isentityonfire) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the entity is on fire | 
| [SetEntityOnFire](#setentityonfire) | <span style="display:inline;color:#ff5555">Server</span> | Set entity on fire | 
| [GetEntityAttrValue](#getentityattrvalue) | <span style="display:inline;color:#ff5555">Server</span> | Get attribute values, including health, hunger, and speed | 
| [GetEntityAttrMaxValue](#getentityattrmaxvalue) | <span style="display:inline;color:#ff5555">Server</span> | Get the maximum value of attributes, including health, hunger, and speed | 
| [SetEntityAttrValue](#setentityattrvalue) | <span style="display:inline;color:#ff5555">Server</span> | Set attribute values, including health, hunger, and speed | 
| [SetEntityAttrMaxValue](#setentityattrmaxvalue) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum value of attributes, including health, hunger, and movement speed | 
| [SetPlayerStepHeight](#setplayerstepheight) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum step height that the player can climb when moving forward without jumping. The default value is 0.5625. 1 means that the player can climb one step | 
| [GetPlayerStepHeight](#getplayerstepheight) | <span style="display:inline;color:#ff5555">Server</span> | Returns the maximum step height that the player can climb when moving forward without jumping | 
| [ResetPlayerStepHeight](#resetplayerstepheight) | <span style="display:inline;color:#ff5555">Server</span> | Restore the engine default maximum step height that the player can climb when moving forward without jumping | 
| [IsEntityInLava](#isentityinlava) | <span style="display:inline;color:#7575f9">Client</span> | Whether the entity is in lava | 
| [IsEntityOnGround](#isentityonground) | <span style="display:inline;color:#7575f9">Client</span> | Whether the entity is touching the ground | 
| [CreateAuxValueComponent](#createauxvaluecomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create auxValue component | 
| [GetEntityAuxValue](#getentityauxvalue) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the additional value of the arrow shot or the potion thrown | 
| [CreateBiomeComponent](#createbiomecomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create biome component | 
| [GetBiomeName](#getbiomename) | <span style="display:inline;color:#ff5555">Server</span> | Get the biome information of a certain location | 
| [CreateBlockComponent](#createblockcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create block component | 
| [RegisterBlockPatterns](#registerblockpatterns) | <span style="display:inline;color:#ff5555">Server</span> | Register special block combination | 
| [CreateMicroBlockResStr](#createmicroblockresstr) | <span style="display:inline;color:#ff5555">Server</span> | Generate miniature block resource Json string | 
| [CreateBlockEntityData](#createblockentitydata) | <span style="display:inline;color:#ff5555">Server</span> | Create blockEntityData component | 
| [GetCustomBlockEntityData](#getcustomblockentitydata) | <span style="display:inline;color:#ff5555">Server</span> | Used to obtain an object that can operate a custom block entity data, the operation method is similar to dict | 
| [CreateBlockInfoComponent](#createblockinfocomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create blockInfo component | 
| [GetBlock](#getblock) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the block at a certain position | 
| [SetBlock](#setblock) | <span style="display:inline;color:#ff5555">Server</span> | Set the block at a certain position | 
| [GetTopBlockHeight](#gettopblockheight) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the height of the highest non-air block at a certain position in the current dimension | 
| [GetBlockDestroyTime](#getblockdestroytime) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the time required to destroy a block with an item | 
| [GetBlockEntityData](#getblockentitydata) | <span style="display:inline;color:#ff5555">Server</span> | Used to get the data of a block (including custom blocks). The data is read-only and not writable | 
| [CreateBlockStateComponent](#createblockstatecomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create a blockState component | 
| [GetBlockStates](#getblockstates) | <span style="display:inline;color:#ff5555">Server</span> | Get <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State" rel="noopenner">Block State</a> | 
| [SetBlockStates](#setblockstates) | <span style="display:inline;color:#ff5555">Server</span> | Set <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State" rel="noopenner">Block State</a> | 
| [GetBlockAuxValueFromStates](#getblockauxvaluefromstates) | <span style="display:inline;color:#ff5555">Server</span> | According to the block name and <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State" rel="noopenner"> Block State </a>Get Block Added Value AuxValue | 
| [GetBlockStatesFromAuxValue](#getblockstatesfromauxvalue) | <span style="display:inline;color:#ff5555">Server</span> | Get <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State" rel="noopenner"> Block State </a> according to the block name and block added value AuxValue | 
| [CreateBlockUseEventWhiteList](#createblockuseeventwhitelist) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create blockUseEventWhiteList component | 
| [AddBlockItemListenForUseEvent](#addblockitemlistenforuseevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add script layer listening of blockName block to ServerBlockUseEvent event | 
| [RemoveBlockItemListenForUseEvent](#removeblockitemlistenforuseevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Remove the script layer listening of the blockName block to the ServerBlockUseEvent event | 
| [ClearAllListenForBlockUseEventItems](#clearalllistenforblockuseeventitems) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Clear all the script layer listening of the ServerBlockUseEvent event of the added blocks | 
| [CreateBreathComponent](#createbreathcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create breath component | 
| [GetUnitBubbleAirSupply](#getunitbubbleairsupply) | style="display:inline;color:#ff5555">Server</span> | Oxygen reserve value corresponding to the number of bubbles | 
| [GetEntityCurrentAirSupply](#getentitycurrentairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Current oxygen reserve value of organisms | 
| [GetEntityMaxAirSupply](#getentitymaxairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Get the maximum oxygen reserve value of organisms | 
| [SetEntityCurrentAirSupply](#setentitycurrentairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Set the oxygen reserve value of organisms |

| [SetEntityMaxAirSupply](#setentitymaxairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum oxygen reserve value of the organism | 
| [IsEntityConsumingAirSupply](#isentityconsumingairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the organism is currently consuming oxygen | 
| [SetEntityRecoverTotalAirSupplyTime](#setentityrecovertotalairsupplytime) | <span style="display:inline;color:#ff5555">Server</span> | Set the time to restore the maximum oxygen, in seconds | 
| [CreateBulletAttributesComponent](#createbulletattributescomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create bulletAttributes component | 
| [GetEntitySourceId](#getentitysourceid) | <span style="display:inline;color:#ff5555">Server</span> | Get the projectile launcher entity id | 
| [CreateChestBlockComponent](#createchestblockcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create chestBlock component | 
| [GetChestBoxSize](#getchestboxsize) | <span style="display:inline;color:#ff5555">Server</span> | Get the box capacity | 
| [SetChestBoxItemNum](#setchestboxitemnum) | <span style="display:inline;color:#ff5555">Server</span> | Set the number of items in the box slot | 
| [SetChestBoxItemExchange](#setchestboxitemexchange) | <span style="display:inline;color:#ff5555">Server</span> | Exchange the slots of items in the chest | 
| [CreateChunkSourceComponent](#createchunksourcecomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create chunkSource component | 
| [SetAddArea](#setaddarea) | <span style="display:inline;color:#ff5555">Server</span> | Set the constant loading of the chunk | 
| [DeleteArea](#deletearea) | <span style="display:inline;color:#ff5555">Server</span> | Delete a constant loading area | 
| [DeleteAllArea](#deleteallarea) | <span style="display:inline;color:#ff5555">Server</span> | Delete all constantly loaded areas | 
| [GetAllAreaKeys](#getallareakeys) | <span style="display:inline;color:#ff5555">Server</span> | Get a list of all constantly loaded area names | 
| [CheckChunkState](#checkchunkstate) | <span style="display:inline;color:#ff5555">Server</span> | Determine whether the chunk at the specified location has been loaded | 
| [GetLoadedChunks](#getloadedchunks) | <span style="display:inline;color:#ff5555">Server</span> | Get a list of coordinates of all chunks that have been loaded in the specified dimension | 
| [GetChunkEntities](#getchunkentities) | <span style="display:inline;color:#ff5555">Server</span> | Get a list of all entity and player IDs in the chunk at the specified location | 
| [GetChunkMobNum](#getchunkmobnum) | <span style="display:inline;color:#ff5555">Server</span> | Get the number of mobs in a chunk (excluding players, but including armor stands) | 
| [IsChunkGenerated](#ischunkgenerated) | <span style="display:inline;color:#ff5555">Server</span> | Get whether a chunk has been generated. | 
| [CreateCollisionBoxComponent](#createcollisionboxcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create collisionBox component | 
| [SetEntityCollisionBoxSize](#setentitycollisionboxsize) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity's bounding box | 
| [GetEntityCollisionBoxSize](#getentitycollisionboxsize) | <span style="display:inline;color:#ff5555">Server</span> | Get the entity's bounding box | 
| [CreateCommandComponent](#createcommandcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create command component | 
| [SetCommand](#setcommand) | <span style="display:inline;color:#ff5555">Server</span> | Use in-game commands | 
| [GetCommandPermissionLevel](#getcommandpermissionlevel) | <span style="display:inline;color:#ff5555">Server</span> | Returns the OP permission level when using the /op command (corresponding to the op-permission-level configuration in server.properties) | 
| [SetCommandPermissionLevel](#setcommandpermissionlevel) | <span style="display:inline;color:#ff5555">Server</span> | Sets the OP permission level when the player uses the /op command (corresponding to the op-permission-level configuration in server.properties) | 
| [GetDefaultPlayerPermissionLevel](#getdefaultplayerpermissionlevel) | <span style="display:inline;color:#ff5555">Server</span> | Returns the permission identity of the new player when joining (corresponding to the default-player-permission-level configuration in server.properties) | 
| [SetDefaultPlayerPermissionLevel](#setdefaultplayerpermissionlevel) | <span style="display:inline;color:#ff5555">Server</span> | Set the permission identity of the new player when joining (corresponding to the default-player-permission-level configuration in server.properties) | 
| [CreateControlAiComponent](#createcontrolaicomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create controlAi component | 
| [SetEntityBlockControlAi](#setentityblockcontrolai) | <span style="display:inline;color:#ff5555">Server</span> | Set to block the native AI of creatures | 
| [CreateDimensionComponent](#createdimensioncomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create dimension component | 
| [GetEntityDimensionId](#getentitydimensionid) | <span style="display:inline;color:#ff5555">Server</span> | Get the dimension of the entity | 
| [ChangeEntityDimension](#changeentitydimension) | <span style="display:inline;color:#ff5555">Server</span> | Teleport entities other than players | 
| [ChangePlayerDimension](#changeplayerdimension) | <span style="display:inline;color:#ff5555">Server</span> | Teleport players | 
| [MirrorDimension](#mirrordimension) | <span style="display:inline;color:#ff5555">Server</span> | Copy terrain of different dimensions | 
| [CreateDimension](#createdimension) | <span style="display:inline;color:#ff5555">Server</span> | Create a new dimension | 
| [RegisterEntityAOIEvent](#registerentityaoievent) | <span style="display:inline;color:#ff5555">Server</span> | Register the sensing area, and there will be a message notification when an entity enters and leaves | 
| [UnRegisterEntityAOIEvent](#unregisterentityaoievent) | <span style="display:inline;color:#ff5555">Server</span> | Unregister the sensing area | 
| [SetUseLocalTime](#setuselocaltime) | <span style="display:inline;color:#ff5555">Server</span> | Allow a dimension to have its own local time rules. After turning it on, the dimension can have different time and day and night rules from other dimensions. | 
| [GetUseLocalTime](#getuselocaltime) | <span style="display:inline;color:#ff5555">Server</span> | Get whether a dimension is set to use local time rules | 
| [SetLocalTime](#setlocaltime) | <span style="display:inline;color:#ff5555">Server</span> | Set the time of the dimension using local time rules | 
| [SetLocalTimeOfDay](#setlocaltimeofday) | <span style="display:inline;color:#ff5555">Server</span> | Set the time of the dimension using local time rules in a day | 
| [GetLocalTime](#getlocaltime) | <span style="display:inline;color:#ff5555">Server</span> | Get the time of the dimension | 
| [SetLocalDoDayNightCycle](#setlocaldodaynightcycle) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the dimension using the local time rule has day and night changes turned on | 
| [GetLocalDoDayNightCycle](#getlocaldodaynightcycle) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the dimension has day and night changes turned on | 
| [CreateEffectComponent](#createeffectcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create effect component | 
| [RemoveEffectFromEntity](#removeeffectfromentity) | <span style="display:inline;color:#ff5555">Server</span> | Delete the specified status effect for the entity | 
| [AddEffectToEntity](#addeffecttoentity) | <span style="display:inline;color:#ff5555">Server</span> | Add the specified status effect to the entity. If the added status already exists, the following situations will occur: 1. If the level is greater than the existing one, update the status level and duration; 2. If the status levels are equal and the remaining duration is greater than the existing one, refresh the remaining time; 3. If the level is less than the existing one, do not modify it; 4. The particle effect is based on the new one | 
| [GetEntityEffects](#getentityeffects) | <span style="display:inline;color:#ff5555">Server</span> | Get all current status effects of the entity | 
| [CreateEngineTypeComponent](#createenginetypecomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create engineType component |

| [GetEntityEngineTypeStr](#getentityenginetypestr) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the entity type name | 
| [GetEntityEngineType](#getentityenginetype) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get entity type | 
| [CreateEntityEventComponent](#createentityeventcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create entityEvent component | 
| [TriggerEntityCustomEvent](#triggerentitycustomevent) | style="display:inline;color:#ff5555">Server</span> | Trigger custom events for creatures | 
| [CreateExtraDataComponent](#createextradatacomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create extraData component | 
| [GetExtraData](#getextradata) | <span style="display:inline;color:#ff5555">Server</span> | Get the custom data of an entity or the custom data of the world, the value corresponding to a key. Get entity data and pass in the corresponding entity id | 
| [SaveExtraData](#saveextradata) | <span style="display:inline;color:#ff5555">Server</span> | Used to save custom data of the entity or custom data of the world | 
| [SetExtraData](#setextradata) | <span style="display:inline;color:#ff5555">Server</span> | Used to set custom data of the entity or custom data of the world. The data is saved in the form of key-value pairs. When setting entity data, use the corresponding entity id to create a component, and when setting world data, use levelId to create a component | 
| [CleanExtraData](#cleanextradata) | <span style="display:inline;color:#ff5555">Server</span> | Clear the custom data of the entity or the custom data of the world. When clearing the entity data, use the corresponding entity id to create a component, and when clearing the world data, use levelId to create a component | 
| [GetWholeExtraData](#getwholeextradata) | <span style="display:inline;color:#ff5555">Server</span> | Get the complete custom data of the entity or the custom data of the world. When getting the entity data, use the corresponding entity id to create a component, and when getting the world data, use levelId to create a component | 
| [CreateExpComponent](#createexpcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create exp component | 
| [GetPlayerExp](#getplayerexp) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's experience value at the current level | 
| [AddPlayerExp](#addplayerexp) | <span style="display:inline;color:#ff5555">Server</span> | Add player experience value | 
| [GetPlayerTotalExp](#getplayertotalexp) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's total experience value | 
| [SetPlayerTotalExp](#setplayertotalexp) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's total experience value | 
| [GetOrbExperience](#getorbexperience) | <span style="display:inline;color:#ff5555">Server</span> | Get the experience of the experience ball | 
| [SetOrbExperience](#setorbexperience) | <span style="display:inline;color:#ff5555">Server</span> | Set the experience of the experience ball | 
| [CreateExperienceOrb](#createexperienceorb) | <span style="display:inline;color:#ff5555">Server</span> | Create a dedicated experience ball | 
| [CreateExplosionComponent](#createexplosioncomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create an explosion component | 
| [CreateExplosion](#createexplosion) | <span style="display:inline;color:#ff5555">Server</span> | Used to generate explosions | 
| [CreateFeatureComponent](#createfeaturecomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create feature component | 
| [AddNeteaseFeatureWhiteList](#addneteasefeaturewhitelist) | <span style="display:inline;color:#ff5555">Server</span> | Add structure to script-level listener for PlaceNeteaseStructureFeatureEvent event | 
| [RemoveNeteaseFeatureWhiteList](#removeneteasefeaturewhitelist) | <span style="display:inline;color:#ff5555">Server</span> | Remove structureName from script-level listener for PlaceNeteaseStructureFeatureEvent event | 
| [ClearAllNeteaseFeatureWhiteList](#clearallneteasefeaturewhitelist) | style="display:inline;color:#ff5555">Server</span> | Clear all script-level listeners of the PlaceNeteaseStructureFeatureEvent event for the Netease Structure Feature that has been added | 
| [LocateStructureFeature](#locatestructurefeature) | <span style="display:inline;color:#ff5555">Server</span> | Similar to the [/locate command](https://minecraft-zh.gamepedia.com/%E5%91%BD%E4%BB%A4/locate), it is used to locate some structures in the original version, such as underwater temples and end cities. | 
| [LocateNeteaseFeatureRule](#locateneteasefeaturerule) | <span style="display:inline;color:#ff5555">Server</span> | Similar to the [/locate command](https://minecraft-zh.gamepedia.com/%E5%91%BD%E4%BB%A4/locate), used to locate <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/4-Custom Dimensions/4-Custom Features.html#Feature Rules (feature-rules)" rel="noopenner"> NetEase Custom Feature Rules </a> | 
| [CreateFlyComponent](#createflycomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create fly component | 
| [IsPlayerFlying](#isplayerflying) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the player is flying | 
| [ChangePlayerFlyState](#changeplayerflystate) | <span style="display:inline;color:#ff5555">Server</span> | Grant/cancel flying ability and enter flying/non-flying state | 
| [CreateGameComponent](#creategamecomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create game component | 
| [AddBlockProtectField](#addblockprotectfield) | <span style="display:inline;color:#ff5555">Server</span> | Set a block area that cannot be destroyed by players/entities | 
| [RemoveBlockProtectField](#removeblockprotectfield) | <span style="display:inline;color:#ff5555">Server</span> | Cancel a block area that cannot be destroyed by players/entities | 
| [CleanBlockProtectField](#cleanblockprotectfield) | <span style="display:inline;color:#ff5555">Server</span> | Cancel all blocks that cannot be destroyed by players/entities | 
| [KillEntity](#killentity) | <span style="display:inline;color:#ff5555">Server</span> | Kill an Entity | 
| [CreateEngineEntityByTypeStr](#createengineentitybytypestr) | <span style="display:inline;color:#ff5555">Server</span> | Create an entity with the specified identifier | 
| [PlaceStructure](#placestructure) | <span style="display:inline;color:#ff5555">Server</span> | Place structure | 
| [AddTimer](#addtimer) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add timer, non-repeating | 
| [AddRepeatedTimer](#addrepeatedtimer) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Add a timer triggered by the server, repeating | 
| [CancelTimer](#canceltimer) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Cancel the timer | 
| [GetEntitiesInArea](#getentitiesinarea) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the entity list in the area | 
| [GetEntitiesAround](#getentitiesaround) | <span style="display:inline;color:#ff5555">Server</span> | Get the entity list in the area | 
| [ShowHealthBar](#showhealthbar) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to show the health bar | 
| [SetNameDeeptest](#setnamedeeptest) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the name is perspective | 
| [GetScreenSize](#getscreensize) | <span style="display:inline;color:#7575f9">Client</span> | Get the game resolution | 
| [SetRenderLocalPlayer](#setrenderlocalplayer) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the local player is rendered | 
| [AddPickBlacklist](#addpickblacklist) | <span style="display:inline;color:#7575f9">Client</span> | Add a blacklist when using the camera component to select an entity, that is, the entity will not be selected | 
| [ClearPickBlacklist](#clearpickblacklist) | <span style="display:inline;color:#7575f9">Client</span> | Clear the blacklist of entities selected using the camera component | 
| [CheckWordsValid](#checkwordsvalid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Check whether the statement is legal, that is, it does not contain sensitive words | 
| [CheckNameValid](#checknamevalid) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Check whether the nickname is legal, that is, it does not contain sensitive words | 
| [GetScreenViewInfo](#getscreenviewinfo) | <span style="display:inline;color:#7575f9">Client</span> | Get the game perspective information. When the resolution is 1313,618, the canvas is twice 376,250, so the viewport is 1313 + (2-(1313%2)). The y value is similar. Please refer to <a href="../../../../mcguide/18-界面与互動/1-界面编辑使用说明.html#《我的世界》界面修改方法" rel="noopenner">《我的世界》界面修改方法 </a> |

| [SimulateTouchWithMouse](#simulatetouchwithmouse) | <span style="display:inline;color:#7575f9">Client</span> | Simulate using the mouse to control the UI (PC F11 shortcut key) | 
| [GetCurrentDimension](#getcurrentdimension) | <span style="display:inline;color:#7575f9">Client</span> | Get the current dimension of the client | 
| [GetChinese](#getchinese) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the Chinese corresponding to langStr, refer to \handheld\bed-loc\handheld\data\resource_packs\vanilla\texts\zh_CN.lang in the PC development package | 
| [SetDisableHunger](#setdisablehunger) | <span style="display:inline;color:#ff5555">Server</span> | Set whether to block hunger | 
| [SetOneTipMessage](#setonetipmessage) | <span style="display:inline;color:#ff5555">Server</span> | Pop up a tip notification above a specific player's inventory, located above the popup notification. For this function, it is recommended to use the corresponding interface SetTipMessage of the game component on the client. | 
| [SetPopupNotice](#setpopupnotice) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Pop up a popup notification above the inventory, located below the tip message. The server call is for all players, and the client call only affects the local player | 
| [SetTipMessage](#settipmessage) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Pop up a tip notification above the inventory, located above the pop-up notification. The server call is for all players, and the client call only affects the local player. | 
| [SetNotifyMsg](#setnotifymsg) | <span style="display:inline;color:#ff5555">Server</span> | Set message notification | 
| [GetPlayerGameType](#getplayergametype) | <span style="display:inline;color:#ff5555">Server</span> | Get the game mode of the specified player | 
| [HasEntity](#hasentity) | style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Determine if entity exists | 
| [IsEntityAlive](#isentityalive) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Determine if biological entity is alive or non-biological entity exists | 
| [CreateGravityComponent](#creategravitycomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create gravity component | 
| [GetEntityGravity](#getentitygravity) | <span style="display:inline;color:#ff5555">Server</span> | Get the entity's gravity factor. When the creature's gravity factor is 0, the world's gravity factor is applied. | 
| [SetEntityGravity](#setentitygravity) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity's gravity factor. When the creature's gravity factor is 0, the world's gravity factor is applied. | 
| [CreateHurtComponent](#createhurtcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create a hurt component | 
| [SetHurtByEntity](#sethurtbyentity) | <span style="display:inline;color:#ff5555">Server</span> | Cause damage to an entity | 
| [SetHurtByEntityNew](#sethurtbyentitynew) | <span style="display:inline;color:#ff5555">Server</span> | Cause damage to the entity | 
| [SetEntityImmuneDamage](#setentityimmunedamage) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the entity is immune to damage (this property is archived) | 
| [CreateItemBannedComponent](#createitembannedcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create itembanned component | 
| [AddBannedItem](#addbanneditem) | <span style="display:inline;color:#ff5555">Server</span> | Add banned items | 
| [GetBannedItemList](#getbanneditemlist) | <span style="display:inline;color:#ff5555">Server</span> | Get the list of banned items | 
| [RemoveBannedItem](#removebanneditem) | <span style="display:inline;color:#ff5555">Server</span> | Remove banned items | 
| [ClearBannedItems](#clearbanneditems) | <span style="display:inline;color:#ff5555">Server</span> | Clear banned items | 
| [CreateItemComponent](#createitemcomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create item component | 
| [GetItemBasicInfo](#getitembasicinfo) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get basic information of items | 
| [GetLocalPlayerId](#getlocalplayerid) | <span style="display:inline;color:#7575f9">Client</span> | Get local player's id | 
| [ClearPlayerOffHand](#clearplayeroffhand) | <span style="display:inline;color:#ff5555">Server</span> | Clear player's left hand items | 
| [GetPlayerItem](#getplayeritem) | <span style="display:inline;color:#ff5555">Server</span> | Get player items, including backpack, armor bar, off-hand and main-hand items | 
| [ChangePlayerItemTipsAndExtraId](#changeplayeritemtipsandextraid) | <span style="display:inline;color:#ff5555">Server</span> | Modify the custom tips and custom identifiers of player items | 
| [AddEnchantToInvItem](#addenchanttoinvitem) | <span style="display:inline;color:#ff5555">Server</span> | Add enchantment information to items in the inventory | 
| [GetInvItemEnchantData](#getinvitemenchantdata) | <span style="display:inline;color:#ff5555">Server</span> | Get enchantment information of items in the inventory | 
| [GetOffhandItem](#getoffhanditem) | <span style="display:inline;color:#7575f9">Client</span> | Get information about left-hand items | 
| [SetInvItemNum](#setinvitemnum) | <span style="display:inline;color:#ff5555">Server</span> | Set the number of items in the player's backpack | 
| [SpawnItemToLevel](#spawnitemtolevel) | <span style="display:inline;color:#ff5555">Server</span> | Generate item drops. If you need to obtain the entityId of the item, you can call the server system interface CreateEngineItemEntity | 
| [SpawnItemToPlayerInv](#spawnitemtoplayerinv) | <span style="display:inline;color:#ff5555">Server</span> | Generate items to the player's backpack | 
| [SpawnItemToPlayerCarried](#spawnitemtoplayercarried) | <span style="display:inline;color:#ff5555">Server</span> | Generate items to the player's right hand | 
| [GetCarriedItem](#getcarrieditem) | <span style="display:inline;color:#7575f9">Client</span> | Get the information of the right-hand item | 
| [GetSlotId](#getslotid) | <span style="display:inline;color:#7575f9">Client</span> | Get the slot id of the currently held shortcut bar | 
| [GetItemFormattedHoverText](#getitemformattedhovertext) | <span style="display:inline;color:#7575f9">Client</span> | Get the formatted hover text of the item, such as: §fDisaster Banner§r | 
| [GetItemHoverName](#getitemhovername) | <span style="display:inline;color:#7575f9">Client</span> | Get the hover name of the item, such as: Disaster Banner§r | 
| [GetItemEffectName](#getitemeffectname) | <span style="display:inline;color:#7575f9">Client</span> | Get the item status description, such as: §7Protection 0§r | 
| [GetUserDataInEvent](#getuserdatainevent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Make the <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary" rel="noopenner"> Item Information Dictionary </a> parameter of the item-related client event contain userData. Just call it when the mod is initialized | 
| [ChangeItemTexture](#changeitemtexture) | <span style="display:inline;color:#7575f9">Client</span> | Replace the texture of the item. After the modification, all items using this texture will be changed, and subsequent items of this type created will also be changed. It will also modify the display of the item on the UI interface, the display when holding it, and the display when dropped in the scene. | 
| [CreateLvComponent](#createlvcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create lv component | 
| [GetPlayerLevel](#getplayerlevel) | <span style="display:inline;color:#ff5555">Server</span> | Get player level | 
| [AddPlayerLevel](#addplayerlevel) | <span style="display:inline;color:#ff5555">Server</span> | Modify player level | 
| [CreateMobSpawnComponent](#createmobspawncomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create mobSpawn component | 
| [SpawnCustomModule](#spawncustommodule) | <span style="display:inline;color:#ff5555">Server</span> | Set up custom monster spawning | 
| [CreateModAttrComponent](#createmodattrcomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create modAttr component | 
| [SetEntityModAttr](#setentitymodattr) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set attribute values |

| [GetEntityModAttr](#getentitymodattr) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get attribute values | 
| [RegisterEntityModAttrUpdateFunc](#registerentitymodattrupdatefunc) | <span style="display:inline;color:#7575f9">Client</span> | Register the callback function for attribute value changes. This function will be called when the attribute changes. | 
| [UnRegisterEntityModAttrUpdateFunc](#unregisterentitymodattrupdatefunc) | <span style="display:inline;color:#7575f9">Client</span> | Unregister the callback function for attribute value changes | 
| [CreateModelComponent](#createmodelcomponent) | style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create model component | 
| [SetEntityOpacity](#setentityopacity) | <span style="display:inline;color:#7575f9">Client</span> | Set the transparency of the biological model | 
| [PlayEntityAnim](#playentityanim) | <span style="display:inline;color:#7575f9">Client</span> | Play skeleton animation | 
| [GetEntityModelId](#getentitymodelid) | <span style="display:inline;color:#7575f9">Client</span> | Get the id of the skeleton model, mainly used for special effects binding skeleton model | 
| [SetEntityModel](#setentitymodel) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the skeleton model | 
| [ResetEntityModel](#resetentitymodel) | <span style="display:inline;color:#7575f9">Client</span> | Restore the entity to the original model | 
| [BindModelToEntity](#bindmodeltoentity) | <span style="display:inline;color:#7575f9">Client</span> | After the entity replaces the skeleton model, attach another skeleton model to it. | 
| [UnBindModelToEntity](#unbindmodeltoentity) | <span style="display:inline;color:#7575f9">Client</span> | Unbind a skeleton model attached to the entity. After unhooking, the model of this modelId will be destroyed and can no longer be used. If it is temporarily hidden, you can use HideModel | 
| [CreateMoveToComponent](#createmovetocomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create moveTo component | 
| [SetEntityMoveSetting](#setentitymovesetting) | <span style="display:inline;color:#ff5555">Server</span> | Pathfinding component | 
| [CreateMsgComponent](#createmsgcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create msg component | 
| [SendMsg](#sendmsg) | <span style="display:inline;color:#ff5555">Server</span> | Simulate a player sending a chat message to everyone | 
| [SendMsgToPlayer](#sendmsgtoplayer) | <span style="display:inline;color:#ff5555">Server</span> | Simulate a player sending a chat message to another player | 
| [NotifyOneMessage](#notifyonemessage) | <span style="display:inline;color:#ff5555">Server</span> | Send a chat message to a specified player | 
| [CreateNameComponent](#createnamecomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create a name component | 
| [GetEntityName](#getentityname) | <span style="display:inline;color:#ff5555">Server</span> | Get the custom name of the creature, that is, the name set by the name tag or SetName interface | 
| [SetEntityName](#setentityname) | <span style="display:inline;color:#ff5555">Server</span> | Used to set the custom name of the creature, the same as the original name tag, players and new wandering traders are not supported yet | 
| [SetPlayerPrefixAndSuffixName](#setplayerprefixandsuffixname) | <span style="display:inline;color:#ff5555">Server</span> | Set the player prefix and suffix name | 
| [SetEntityShowName](#setentityshowname) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the creature name is displayed according to the default game logic | 
| [SetEntityAlwaysShowName](#setentityalwaysshowname) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the creature's name is always displayed, even when the aiming point is not pointing at the creature | 
| [CreatePersistenceComponent](#createpersistencecomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create persistence component | 
| [SetEntityPersistence](#setentitypersistence) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the entity is saved | 
| [CreatePetComponent](#createpetcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create pet component | 
| [DisablePet](#disablepet) | <span style="display:inline;color:#ff5555">Server</span> | Disable the official partner function. Single-player games and local online games do not support this interface. | 
| [EnablePet](#enablepet) | <span style="display:inline;color:#ff5555">Server</span> | Enable the official partner function. Single-player games and local online games do not support this interface. | 
| [CreatePlayerComponent](#createplayercomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create player component | 
| [EnablePlayerKeepInventory](#enableplayerkeepinventory) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the player to not drop items when he dies | 
| [CreatePortalComponent](#createportalcomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create portal component | 
| [CreatePosComponent](#createposcomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create pos component | 
| [GetEntityPos](#getentitypos) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get entity position | 
| [GetEntityFootPos](#getentityfootpos) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get the position of the entity's feet | 
| [SetEntityPos](#setentitypos) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity's position | 
| [SetEntityFootPos](#setentityfootpos) | <span style="display:inline;color:#ff5555">Server</span> | Set the position of the entity's feet | 
| [CreateProjectileComponent](#createprojectilecomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create a projectile component | 
| [CreateProjectileEntity](#createprojectileentity) | <span style="display:inline;color:#ff5555">Server</span> | Create a projectile (direct launch) | 
| [CreateRecipeComponent](#createrecipecomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create a recipe component | 
| [GetRecipeResult](#getreciperesult) | <span style="display:inline;color:#ff5555">Server</span> | Get the recipe result based on the recipe id. Only supports crafting recipes | 
| [GetRecipesByResult](#getrecipesbyresult) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Query the input materials required for the recipe through the output items | 
| [GetRecipesByInput](#getrecipesbyinput) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Query the recipe through the input items | 
| [CreateRedStoneComponent](#createredstonecomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create redStone component | 
| [CreateRideComponent](#createridecomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create ride component | 
| [CreateRotComponent](#createrotcomponent) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Create rot component | 
| [GetEntityRot](#getentityrot) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Get entity angle | 
| [SetEntityRot](#setentityrot) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the angle of the entity's head | 
| [SetEntityLookAtPos](#setentitylookatpos) | <span style="display:inline;color:#ff5555">Server</span> | Set the non-player entity to look at a certain position | 
| [GetBodyRot](#getbodyrot) | <span style="display:inline;color:#7575f9">Client</span> | Get the angle of the entity's body | 
| [LockLocalPlayerRot](#locklocalplayerrot) | <span style="display:inline;color:#7575f9">Client</span> | Lock the local player's head angle when detaching the camera |

| [SetPlayerLookAtPos](#setplayerlookatpos) | <span style="display:inline;color:#7575f9">Client</span> | Set the local player to look at a certain position | 
| [CreateScaleComponent](#createscalecomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create a scale component | 
| [CreateTameComponent](#createtamecomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create a tame component | 
| [CreateTimeComponent](#createtimecomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create a time component | 
| [GetTime](#gettime) | <span style="display:inline;color:#ff5555">Server</span> | Get the current world time | 
| [CreateWeatherComponent](#createweathercomponent) | <span style="display:inline;color:#ff5555">Server</span> | Create weather component | 
| [CreateActorCollidableComponent](#createactorcollidablecomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create actorCollidable component | 
| [CreateActorRenderComponent](#createactorrendercomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create actorRender component | 
| [CreateCustomAudioComponent](#createcustomaudiocomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create customAudio component | 
| [CreateBrightnessComponent](#createbrightnesscomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create brightness component | 
| [SetEntityBrightness](#setentitybrightness) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the brightness of the entity | 
| [CreateCameraComponent](#createcameracomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create camera component | 
| [PickFacing](#pickfacing) | <span style="display:inline;color:#7575f9">Client</span> | Get the entity or block selected by the crosshair | 
| [CreateFogComponent](#createfogcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create fog component | 
| [CreateFrameAniControlComponent](#createframeanicontrolcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create frameAniControl component | 
| [SetFrameAniLoop](#setframeaniloop) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the sequence frame is looped, the default is no | 
| [SetFrameAniFaceCamera](#setframeanifacecamera) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the sequence frame is always facing the camera, the default is yes | 
| [SetFrameAniDeepTest](#setframeanideeptest) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the sequence frame is perspective, the default is no | 
| [CreateFrameAniEntityBindComponent](#createframeanientitybindcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create frameAniEntityBind component | 
| [BindFrameAniToEntity](#bindframeanitoentity) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Bind entity | 
| [CreateFrameAniSkeletonBindComponent](#createframeaniskeletonbindcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create frameAniSkeletonBind component | 
| [BindFrameAniToSkeleton](#bindframeanitoskeleton) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Bind skeleton model | 
| [CreateFrameAniTransComponent](#createframeanitranscomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create frameAniTrans component | 
| [GetFrameAniPos](#getframeanipos) | <span style="display:inline;color:#7575f9">Client</span> | Get sequence frame position | 
| [GetFrameAniRot](#getframeanirot) | <span style="display:inline;color:#7575f9">Client</span> | Get the angle of the sequence frame | 
| [GetFrameAniScale](#getframeaniscale) | <span style="display:inline;color:#7575f9">Client</span> | Get the scale of the sequence frame | 
| [SetFrameAniPos](#setframeanipos) | <span style="display:inline;color:#7575f9">Client</span> | Set the position of the sequence frame | 
| [SetFrameAniRot](#setframeanirot) | <span style="display:inline;color:#7575f9">Client</span> | Set the angle of the special effect | 
| [SetFrameAniScale](#setframeaniscale) | <span style="display:inline;color:#7575f9">Client</span> | Set the scale of the sequence frame | 
| [CreateHealthComponent](#createhealthcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create health component | 
| [ShowEntityHealth](#showentityhealth) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to display the health bar of an entity. The default is to display it | 
| [CreateOperationComponent](#createoperationcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create operation component | 
| [SetCanAll](#setcanall) | <span style="display:inline;color:#7575f9">Client</span> | Set SetCanMove, SetCanJump, SetCanAttack, SetCanWalkMode, SetCanPerspective, SetCanPause, SetCanChat, SetCanScreenShot, SetCanOpenInv, SetCanDrag, SetCanInair at the same time | 
| [CreateDeviceComponent](#createdevicecomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create device component | 
| [CreateParticleControlComponent](#createparticlecontrolcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create particleControl component | 
| [CreateParticleEntityBindComponent](#createparticleentitybindcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create particleEntityBind component | 
| [BindParticleToEntity](#bindparticletoentity) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Bind particle effects to entity | 
| [CreateParticleSkeletonBindComponent](#createparticleskeletonbindcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create particleSkeletonBind component | 
| [BindParticleToSkeleton](#bindparticletoskeleton) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Bind particle effects to skeleton model | 
| [CreateParticleTransComponent](#createparticletranscomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create particleTrans component | 
| [GetParticlePos](#getparticlepos) | <span style="display:inline;color:#7575f9">Client</span> | Get special effect position | 
| [GetParticleRot](#getparticlerot) | <span style="display:inline;color:#7575f9">Client</span> | Get special effect angle | 
| [SetParticlePos](#setparticlepos) | <span style="display:inline;color:#7575f9">Client</span> | Set special effect position | 
| [SetParticleRot](#setparticlerot) | <span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> | Set the angle of special effects | 
| [CreatePlayerViewComponent](#createplayerviewcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create playerView component | 
| [GetPlayerPerspective](#getplayerperspective) | <span style="display:inline;color:#7575f9">Client</span> | Get the current perspective mode | 
| [SetPlayerPerspective](#setplayerperspective) | <span style="display:inline;color:#7575f9">Client</span> | Set the perspective mode | 
| [LockPlayerPerspective](#lockplayerperspective) | <span style="display:inline;color:#7575f9">Client</span> | Lock the player's camera mode | 
| [CreateQueryVariableComponent](#createqueryvariablecomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create queryVariable component | 
| [CreateSkyRenderComponent](#createskyrendercomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create skyRender component |

| [CreateTextBoardComponent](#createtextboardcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create textBoard component | 
| [CreateTextNotifyClientComponent](#createtextnotifyclientcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create textNotifyClient component | 
| [CreateConfigClientComponent](#createconfigclientcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create config component | 
| [CreateVirtualWorldComponent](#createvirtualworldcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create virtualWorld component instance component | 
| [CreatePlayerAnimComponent](#createplayeranimcomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create player animation component | 
| [CreatePostProcessComponent](#createpostprocesscomponent) | <span style="display:inline;color:#7575f9">Client</span> | Create PostProcess component | 

## GetEntityId 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get object entity ID 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str or int | Entity ID or None | 

## ToPlayerPreset 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Force type conversion to player preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| PlayerPreset | Player preset or None | 

## ToEntityPreset 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Force type conversion to entity preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| EntityPreset | Entity preset or None | 

## ToEffectPreset 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Force type conversion to special effect preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| EffectPreset | Special effect preset or None | 

## ToBlockPreset 


<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Force type conversion to block preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockPreset | Block preset or None | 

## ToUIPreset 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Force type conversion to UI preset 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| UIPreset | UI preset or None | 

## GetServerSystem 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 


Returns the server system that the current object can use 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ServerSystem | Server system, client returns empty | 

## GetClientSystem 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Returns the client system that the current object can use 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ClientSystem | Client system, server returns empty | 

## GetSystem 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Returns the system that the current object can use 

- Parameters 

None 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ClientSystem or ServerSystem | Returns the system that the current object can use | 

## GetLevelId 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the level_id of the current object 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | level_id | 

## CreateComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a component for an entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity ID of the owner of the component | 
| nameSpace | str | Component namespace, namespace of registerComponent | 
| name | str | Component name | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BaseComponent | Component instance | 

## GetMinecraftEnum 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Used to get the enumeration value in the enumeration value document 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| minecraftEnum | Enumeration collection class | 

- Example 

```python 
self.GetMinecraftEnum().GameType.Survival 
``` 

## DestroyEntity 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Destroy entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Destroyed entity ID | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Destruction success | 

## CreateActionComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create action component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ActionCompServer | action component instance | 

## SetEntityAttackTarget 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the target of hatred 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| targetId | str | Target entity id | 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SetEntityAttackTarget(entityId, targetId) 
``` 

## ResetEntityAttackTarget 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Clear the target of hatred 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.ResetEntityAttackTarget(entityId) 
``` 

## GetEntityAttackTarget 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description


Get the target of hatred 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Entity id of the target of hatred | 

- Example 

```python 
self.GetEntityAttackTarget(entityId) 
``` 

## SetMobKnockback 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the initial speed of the knockback, and consider the influence of resistance 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| xd | float | x-axis direction, used to control the angle | 
| zd | float | z-axis direction, used to control the angle | 
| power | float | Used to control the initial speed in the horizontal direction | 
| height | float | Initial speed in the vertical direction | 
| heightCap | float | Upward speed threshold, this value needs to be considered when the entity itself already has an upward speed, to ensure that the final upward speed does not exceed heightCap | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None | No return value | 


- Example 

```python 
self.SetMobKnockback(entityId, 0.1, 0.1, 1.0, 1.0, 1.0) 
``` 

## CreateActorLootComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create actorLoot component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ActorLootComponentServer | actorLoot component instance | 

## SpawnLootTable 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Use the creature type to simulate a random drop. The generated items are related to the probability defined in json 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Drop position | 
| identifier | str | Entity identifier, such as minecraft:guardian | 
| playerKillerId | str | Player killer (can only be a player). If not set, it will drop randomly in a player dimension | 
| damageCauseEntityId | str | The entity ID of the damage source (the drop is related to the looting enchantment level of the item held by the entity), default is None |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the drop is generated successfully | 

- Notes 
- Need to be generated near the corresponding player entity, otherwise the generation will fail. For some special creatures, such as minecraft:sheep, you need to use the SpawnLootTableWithActor interface to simulate random drops. 

- Example 

```python 
result = self.SpawnEntityLootTable((1, 4, 5), 'minecraft:guardian') 
``` 

## SpawnLootTableWithActor 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Use a creature instance to simulate a random drop. The generated items are related to the probability defined in json 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Drop position | 
| entityId | str | Creature ID of simulated creature | 
| playerKillerId | str | Player killer (can only be a player), if not set, it will drop randomly in a player dimension | 
| damageCauseEntityId | str | Damage source entity ID (drop is related to the looting enchantment level of the item held by the entity), default None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the drop is generated successfully | 

- Notes 
- Need to be generated near the corresponding player entity, otherwise the generation will fail 

- Example 

```python 
result = self.SpawnLootTableWithActor((1, 4, 5), '-335007449086')

``` 

## CreateActorMotionComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create actorMotion component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ActorMotionComponentServer or ActorMotionComponentClient | actorMotion component instance | 

## GetDirFromRot 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the orientation by the rotation angle 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| rot | tuple(float,float) | Pitch angle and angle around the vertical direction, the unit is degree | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Unit vector of the player's direction | 


- Example 

```python 
direction = self.GetDirFromRot((0, 0)) 
``` 

## SetEntityMotion 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the instantaneous moving direction vector of the creature. The server can only be used for non-players, and the client can only be used for local players. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| motion | tuple(float,float,float) | The direction is the vector in the world coordinate system. The positive direction of the x, z, and y axes is the positive value. The rot component of the current creature can be used to determine the direction the player is currently facing. In development mode, press F3 to observe the value change. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# Make the creature rush a certain distance in the direction of the crosshair 
rot = self.GetEntityRot(entityId) 
x, y, z = self.GetDirFromRot(rot) 
self.SetMotion(entityId, (x * 5, y * 5, z * 5)) 
# Relationship between rot and world coordinate system 
# ^ x -90° 
# | 
# 180°/-180 ----------> z 0° 
# | 90° 
``` 

## GetEntityMotion 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span>


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the instantaneous movement direction vector of the creature (including the player) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(int,int,int) | Instantaneous movement direction vector, returns None in case of exception | 

- Example 

```python 
self.GetEntityMotion(entityId) 
``` 

## GetInputVector 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the input of the local player's direction keys (moving the roulette wheel) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Returns a unit vector, the first item of the vector is the size to the left, and the second item is the size to the front | 

- Example 

```python

left, up = self.GetInputVector() 
``` 

## LockInputVector 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Lock the input of the local player's direction keys (moving the wheel), so that the local player can continue to move in the specified direction and will not be affected by the player's input 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| inputVector | tuple(float,float) | Input vector, the first item controls the size to the left, and the second item controls the size to the front. When (0, 0) is passed in, the player will be forced to stay in place and is not allowed to move. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the lock is successful, True: success False: failure | 

- Notes 
- The vector passed in will be converted to a unit vector, so passing in (10, 0) has the same effect as passing in (0.1, 0) 

- Example 

```python 
# Make the player move continuously to the left front 
self.LockInputVector((1, 1)) 
``` 

## UnlockInputVector 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Unlock the input of the local player's direction keys (moving the wheel) 

- Parameters


    None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether unlocking is successful, True: success False: failure | 

## CreateActorOwnerComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create actorOwner component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ActorOwnerComponentServer | actorOwner component instance | 

## SetEntityOwner 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the owner of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id |

| ownerId | str | Owner entity id, if None, set the entity owner to null | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful, True means the setting is successful | 

- Example 

```python 
result = self.SetEntityOwner(entityId, ownerId) 
``` 

## GetEntityOwner 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the owner of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Entity owner id | 

- Example 

```python 
ownerId = self.GetEntityOwner(entityId) 
``` 

## CreateActorPushableComponent 

<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create an actorPushable component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ActorPushableCompServer | actorPushable component instance | 

## SetActorPushable 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether the entity is pushable 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| isPushable | int | 0: Not pushable 1: Pushable | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the setting is successful | 

- Example 

```python 
success = self.SetActorPushable(entityId, 1) 
``` 




## CreateAttrComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create attr component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| AttrCompServer or AttrCompClient | attr component instance | 

## IsEntityOnFire 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get whether the entity is on fire 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether on fire | 

- Example 

```python

isOnFire = self.IsEntityOnFire(entityId) 
``` 

## SetEntityOnFire 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the entity on fire 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| seconds | int | Time on fire (unit: seconds) | 
| burn_damage | int | HP deducted per second when on fire, default is 1 if not passed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- It will not take effect in water or rain, and the ignition time is affected by the biological equipment and the state of the biological. The value range of burn_damage is 0~1000. If it is less than 0, it will be 0, and if it is greater than 1000, it will be 1000 

- Example 

```python 
self.SetEntityOnFire(entityId, 1, 2) 
``` 

## GetEntityAttrValue 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get attribute values, including health, hunger, and movement speed 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| attrType | int | <a href="../../../1-ModAPI/Enumeration value/AttrType.html">AttrType enumeration</a> | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Attribute result | 

- Example 

```python 
self.GetEntityAttrValue(entityId, self.GetMinecraftEnum().AttrType.HEALTH) 
``` 

## GetEntityAttrMaxValue 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the maximum value of attributes, including health, hunger, and speed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| attrType | int | <a href="../../../1-ModAPI/Enumeration value/AttrType.html">AttrType enumeration</a> | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Attribute value result | 

- Example

```python
self.GetEntityAttrMaxValue(entityId, self.GetMinecraftEnum().AttrType.HEALTH)
```



## SetEntityAttrValue 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set attribute values, including health, hunger, and movement speed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| attrType | int | <a href="../../../1-ModAPI/Enumeration value/AttrType.html">AttrType enumeration</a> | 
| value | float | Attribute value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Setting interface does not support ABSORPTION 

- Example 

```python 
self.SetEntityAttrValue(entityId, self.GetMinecraftEnum().AttrType.HEALTH, 20) 
``` 

## SetEntityAttrMaxValue 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the maximum value of attributes, including health, hunger, and movement speed 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| entityId | str or int | entity id | 
| attrType | int | <a href="../../../1-ModAPI/Enumeration Value/AttrType.html">AttrType Enumeration</a> | 
| value | float | attribute value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- The maximum saturation cannot exceed the current hunger value; after eating food, the maximum saturation will be modified by the original game mechanism 
- The setting interface does not support ABSORPTION 

- Example 

```python 
self.SetEntityAttrMaxValue(entityId, serverApi.GetMinecraftEnum().AttrType.SPEED, 0.2) 
``` 

## SetPlayerStepHeight 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the maximum step height that the player can climb when moving forward without jumping. The default value is 0.5625. If it is 1, it means that the player can climb one step. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str or int | Player id | 
| stepHeight | float | Maximum height, needs to be greater than 0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is the setting successful? | 

- Notes 
- In order to avoid errors caused by floating point errors, the setting usually increases by 1/16 of the block size, that is, 0.0625. So here we set 2.0625. The default value in the game is 0.5625, which is half a grid height. 
- Only applies to players, and this attribute cannot be modified for other entities 
- The modification does not affect the jump logic and jump height, and it will not jump higher. Therefore, in some specific cases, you can walk on the block but cannot jump up.


- Example 

```python 
#If there is a two-block high block in front, the player can go up directly by pressing forward without jumping 
self.SetPlayerStepHeight(playerId, 2.0625) 
``` 

## GetPlayerStepHeight 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Returns the maximum step height that the player can go up when moving forward without jumping 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Player id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | step height | 

## ResetPlayerStepHeight 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Restore the engine default maximum step height that the player can climb when moving forward without jumping 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Player id | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

## IsEntityInLava 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Whether the entity is in the lava 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Is it in lava? True means it is in lava, False means it is not in lava | 

- Notes 
- Only the entities loaded by the local client can be obtained whether they are in lava. If the entity is in other dimensions or not loaded (too far from the local player), the acquisition will fail. 

- Example 

```python 
isInLava = self.isEntityInLava(entityId) 
``` 

## IsEntityOnGround 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Whether the entity is touching the ground


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether it touches the ground, True means it touches the ground, False means it does not touch the ground | 

- Notes 
- When the client entity is just created, the engine calculation has not been completed. At this time, getting whether the entity is on the ground will return the default value True. You need to delay one frame to get the correct data 
- When the creature is in a riding state, such as a player riding on a pig, it is also considered to be on the ground 
- Only entities loaded by the local client can be obtained to see whether they are on the ground. If the entity is in another dimension or not loaded (too far from the local player), the acquisition will fail 

- Example 

```python 
isOnGound = self.isEntityOnGround(entityId) 
``` 

## CreateAuxValueComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create auxValue component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| AuxValueComponentServer or AuxValueComponentClient | auxValue component instance | 



## GetEntityAuxValue 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the additional value of the arrow shot or the potion thrown 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | auxValue | 

- Example 

```python 
self.GetAuxValue(entityId) 
``` 

## CreateBiomeComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create biome component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| BiomeCompServer | biome component instance | 

## GetBiomeName 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the biome information of a certain location 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| pos | tuple(int,int,int) | Specified position | 
| dimId | int | Dimension id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Biome name of the location | 

- Notes 
- If the original biomes with hills_transformation and mutate_transformation components are not rewritten in the custom biome, the names of these related biomes that have not been rewritten may be incorrect. 

- Example 

```python 
biomeName = self.GetBiomeName((0, 80, 0), 0) 
``` 

## CreateBlockComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a block component 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockCompServer | block component instance | 

## RegisterBlockPatterns 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Register special block combination 

- Parameter 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pattern | list(str) | Block combination position | 
| defines | dict | Block combination type | 
| result_actor_name | str | Synthesis result | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
pattern = [ 
' # ', 
'XXX', 
' X ' 
] 
defines ={ 
'#': 'minecraft:gold_block', 
'X': 'minecraft:iron_block' 
} 
self.RegisterBlockPatterns(pattern, defines, 'minecraft:chicken') 
#In this example, iron blocks are placed in the left, middle, right and bottom, and gold blocks are placed on top, which will generate a chicken.

``` 

## CreateMicroBlockResStr 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Generates a Json string of a miniature block resource 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| identifier | str | Unique identifier of a miniature block | 
| start | tuple(int,int,int) | Miniature start coordinates | 
| end | tuple(int,int,int) | Miniature end coordinates | 
| colorMap | dict | Default is None, miniature block color correspondence table | 
| isMerge | bool | Default is False, whether to merge blocks of the same type | 
| icon | str | Default is an empty string, microblock icon, needs to be defined in terrain_texture.json | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Resource string of the generated microblock | 

- Example 

```python 
result = self.CreateMicroBlockResStr("x", (12, 60, 12), (26, 76, 26), colorMap={'minecraft:grass': [12, 22, 123, 255]}, isMerge=True, icon="micro_block_datiangou") 
with open("micro_block_x.json", "w+") as f: 
f.write(result) 
#In this example, the block will be (12 60 12) As the starting point, and (26 76 26) as the end point, the color of all grass blocks in the final miniature block is rgba(12,22,123,255). The actual display color will be fine-tuned according to the ambient light. The icon in the inventory is the image corresponding to micro_block_datiangou in terrain_texture.json. 
``` 

## CreateBlockEntityData 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 


Create blockEntityData component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockEntityExDataCompServer | blockEntityData component instance | 

## GetCustomBlockEntityData 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Used to obtain an object that can operate a custom block entity data, the operation method is similar to dict 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension | 
| pos | tuple(int,int,int) | Block position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockEntityData or None | Object that can manipulate the data in the block entity | 

- Notes 
- GetBlockEntityData returns None usually because the block where the block is located is not loaded, the game is exiting, the block is not a custom block, or the netease:block_entity component is not configured in the json of the custom block.<br>Before operating the object returned by GetBlockEntityData, please first determine whether it is empty, otherwise it will cause the ```'NoneType' object has no attribute '__getitem__'``` error.
- Supports basic python data types (int/float/string/bool/dict/list), does not support tuple and **dict's key must be a string** 
- **When storing a list, the data types of each item in the list should be the same, otherwise the storage will fail**. For example, [True, False] can be stored successfully, and [True, 1, 0.5] will fail to store 
- **Although the returned object operation is similar to dict, it does not support nested storage and only allows direct assignments such as blockEntityData['key'] = value. For example, operations such as blockEntityData["value5"] ["v1"] = 9 or blockEntityData["value6"].append(True) will not be able to successfully store data. ** 
- When storing integers, if the value range exceeds the maximum range that int can represent, it will not be successfully stored. It is recommended to convert such values to strings for storage. 

- Example 

```python 
dimension = 0

pos = (4, 3, 2) 
# GetBlockEntityData will return None in some cases. Before operating on the returned result, be sure to check whether it is empty. 
blockEntityData = self.GetCustomBlockEntityData(dimension, pos) 
# Store data 
# Supports storing basic python data types (int/float/string/bool/dict/list), does not support tuple, and key must be a string 
# When storing a list, the data types of each item in the list should be the same, otherwise the storage will fail 
if blockEntityData: 
blockEntityData['value1'] = 10 
blockEntityData['value2'] = 3.5 
blockEntityData['value3'] = True 
blockEntityData['value4'] = "hello" 
blockEntityData['value5'] = {"v1": 10, "v2": 3.5, "v3": [0,1,2]} 
blockEntityData['value6'] = [True, False] 
# Read data 
if blockEntityData: 
value1 = blockEntityData['value1'] 
value5 = blockEntityData['value5'] 
# Data that does not exist in the block entity will return None 
valueNone = blockEntityData['valueNone'] 
``` 

## CreateBlockInfoComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create blockInfo component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockInfoComponentServer or BlockInfoComponentClient | blockInfo component instance | 

## GetBlock 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span>


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the block at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| dimensionId | int | The dimension where the block is located. The server can get the block in the constant loading block of the corresponding dimension. It is invalid for the client. The client can only get the current dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Block Information Dictionary" rel="noopenner"> Block information dictionary </a> | 

- Notes 
- Block information can only be obtained for terrain that has been loaded. It supports obtaining block information in the corresponding dimension of the constantly loaded block 
- For blocks with multiple states, aux calculations are more complicated. It is recommended to use GetBlockStates to obtain the block state dictionary 

- Example 

```python 
blockDict = self.GetBlock((0, 5, 0), 0) 
``` 

## SetBlock 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set a block at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Block position | 
| blockDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Block Information Dictionary" rel="noopenner"> Block Information Dictionary </a> | 
| oldBlockHandling | int | 0: Replace, 1: Destroy, 2: Keep, the default is 0 | 
| dimensionId | int | The dimension where the block is located, a required parameter |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- Blocks can only be set on terrain that has been loaded. Blocks can be set in the constant loading block of the corresponding dimension. 
- **If the SetBlockNew interface is used to replace a block containing a block entity, except for custom block entities, when the block entity type before and after the replacement is the same, the data in the block entity will not change. ** 
For example, if items are placed in a box, after using the SetBlockNew interface to replace the box block with a box block, the new box still retains the items in the old box. <br> 
To avoid this situation, add a block replacement with a different block entity type (or without a block entity) in the middle. For example, replace the box with air first, and then replace the air with a box. 
- For blocks with multiple states, the aux calculation method is more complicated. It is recommended to set the block first and then use SetBlockStates to set the block state dictionary 

- Example 

```python 
blockDict = { 
'name': 'minecraft:wool', 
'aux': 5 
} 
self.SetBlockNew((0, 5, 0), blockDict, 0, 0) 
``` 

## GetTopBlockHeight 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the height of the highest non-air block at a certain position in the current dimension 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int) | x-axis and z-axis positions | 
| dimension | int | Dimension id, default is 0, invalid for the client, the server can get the highest non-air block height in the constantly loaded chunk | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int or None | Height. If there is no non-air block at the position, -1 is returned. If the chunk is not loaded, None is returned | 

- Example


```python 
height = self.GetTopBlockHeight((5, 5)) 
``` 

## GetBlockDestroyTime 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the time required to destroy a block using an item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block identifier, format [namespace:name:auxvalue], auxvalue defaults to 0 | 
| itemName | str | Item identifier, format [namespace:name:auxvalue], auxvalue defaults to 0, defaults to None (no item used) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Time required | 

- Example 

```python 
self.GetBlockDestroyTime("minecraft:diamond_block", "minecraft:stone_pickaxe") 
``` 

## GetBlockEntityData 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Used to obtain the data of blocks (including custom blocks), the data is read-only and cannot be written 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension | 
| pos | tuple(int,int,int) | Block position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict or None | Object of data in block entity | 

- Notes 
- **With the update of versions, the data structure contained in the block may be adjusted by the Microsoft team and will not be announced. Developers using this interface should pay attention to testing and compatibility when the version is updated. Data encoding is UTF-8 
Applicable to: [Block Entity](https://minecraft-zh.gamepedia.com/%E6%96%B9%E5%9D%97%E5%AE%9E%E4%BD%93) 
Special case: The item information of the ender chest cannot be obtained through this interface 

- Example 

```python 
blockEntityData = self.GetBlockEntityData(0, (4, 3, 2)) 
``` 

## CreateBlockStateComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create blockState component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockStateComponentServer | blockState component instance | 

## GetBlockStates 


<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block Status" rel="noopenner"> Block Status </a> 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Block Position | 
| dimensionId | int | Block Dimension | 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| dict | Block state, None in case of exception | 

- Notes 
- Only block states in loaded blocks can be obtained, and block states in normally loaded blocks of corresponding dimensions can be obtained 

- Example 

```python 
self.GetBlockStates((4,4,3), 0) 
``` 

## SetBlockStates 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State" rel="noopenner"> Block State </a> 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Block position | 
| data | dict | Block status | 
| dimensionId | int | Dimension where the block is located | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Only the block state in the loaded block can be set, and the block state in the constantly loaded block of the corresponding dimension can be set 

- Example 

```python 
# Set white wool to orange wool 
pos = (4,4,3) 
state = self.GetBlockStates(pos, 0) # state = { 'color': 'white' } 
state['color'] = 'orange' 
self.SetBlockStates(pos, state, 0) 
``` 

## GetBlockAuxValueFromStates 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the block additional value AuxValue according to the block name and <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block Status" rel="noopenner">Block Status</a> 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| blockName | str | Block Name | 
| states | dict | Block Status | 

- Return Value 

| <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | 
| int | Block additional value AuxValue, -1 in case of exception | 

- Example 

```python 
states = self.GetBlockAuxValueFromStates("minecraft:hopper", {"facing_direction": 0, "toggle_bit": 0}) 
``` 




## GetBlockStatesFromAuxValue 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State" rel="noopenner">Block State</a> according to the block name and block additional value AuxValue 

- Parameters 

| Parameter Name | <div style="width: 4em">Data Type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block Name | 
| auxValue | int | Block Additional Value AuxValue | 

- Return Value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Block state, None in case of exception | 

- Example 

```python 
states = self.GetBlockStatesFromAuxValue('minecraft:sapling', 9) 
``` 

## CreateBlockUseEventWhiteList 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create blockUseEventWhiteList component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BlockUseEventWhiteListComponentServer or BlockUseEventWhiteListComponentClient | blockUseEventWhiteList component instance | 

## AddBlockItemListenForUseEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Add script layer monitoring of ServerBlockUseEvent event to blockName block 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block name, format: namespace:name:auxvalue, where namespace:name:* matches all auxvalues | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful | 

- Example 

```python 
self.AddBlockItemListenForUseEvent("minecraft:nether_brick_stairs:2") 
# Note that the format of blockName is namespace:name:auxvalue. If auxvalue is not filled, the default value is 0 
# For detailed values of auxValue, please refer to the official wiki, such as 'Block data value' in https://minecraft-zh.gamepedia.com/梯 
``` 

## RemoveBlockItemListenForUseEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Remove the script layer monitoring of the ServerBlockUseEvent event of the blockName block 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| blockName | str | Block name, format: name: auxvalue, where namespace: name: * matches all auxvalue | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the removal is successful | 

- Example 

```python 
self.RemoveBlockItemListenForUseEvent("minecraft:nether_brick_stairs:2") 
# Note that the format of blockName is namespace:name:auxvalue. If auxvalue is not filled in, the default value is 0 
# For detailed values of auxValue, please refer to the official wiki, such as https://minecraft-zh.gamepedia.com/梯

``` 

## ClearAllListenForBlockUseEventItems 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Clears all script layer listeners for ServerBlockUseEvent events for added blocks 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether clearing is successful | 

## CreateBreathComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description


Create breath component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BreathCompServer | breath component instance | 

## GetUnitBubbleAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Oxygen reserve value corresponding to the number of unit bubbles 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Oxygen reserve value corresponding to the number of bubbles | 

## GetEntityCurrentAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Current oxygen reserve value of organism 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Current oxygen reserve value of the organism | 

- Remarks 
- Note: This value returns the number of logical frames supported by the current oxygen reserve = oxygen reserve value * logical frame number (20 frames per second) 

- Example 

```python 
self.GetCurrentAirSupply(entityId) 
``` 

## GetEntityMaxAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the maximum oxygen reserve value of the organism 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Maximum oxygen reserve value | 

- Remarks 
- Note: The value returned is the maximum oxygen reserve supported logical frame number = oxygen reserve value * logical frame number (20 frames per second) 

- Example 

```python

self.GetEntityMaxAirSupply(entityId) 
``` 

## SetEntityCurrentAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the oxygen reserve value of the organism 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 
| data | int | Set the current oxygen value of the organism | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Note: This value sets the number of logical frames supported by the current oxygen reserve = oxygen reserve value * logical frame number (20 frames per second) 

- Example 

```python 
self.SetEntityCurrentAirSupply(entityId, 300) 
``` 

## SetEntityMaxAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the maximum oxygen reserve value of the organism 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| data | int | Set the maximum oxygen value of the organism | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Remarks 
- Note: This value sets the maximum number of logical frames supported by the oxygen reserve = oxygen reserve value * logical frame number (20 frames per second) 

- Example 

```python 
self.SetEntityMaxAirSupply(entityId, 400) 
``` 

## IsEntityConsumingAirSupply 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get whether the organism is currently consuming oxygen 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to consume oxygen | 

- Example 

```python 
self.IsEntityConsumingAirSupply(entityId) 
```



## SetEntityRecoverTotalAirSupplyTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the time to restore the maximum oxygen, in seconds 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 
| timeSec | float | Restore the maximum oxygen value of the organism | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Note: When the maximum oxygen value is set to less than (timeSec*10), the value of the oxygen recovery per frame is 0 

- Example 

```python 
self.SetEntityRecoverTotalAirSupplyTime(entityId, 10) 
``` 

## CreateBulletAttributesComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create bulletAttributes component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BulletAttributesComponentServer | bulletAttributes component instance | 

## GetEntitySourceId 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the projectile launcher entity id 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Projectile launcher entity id | 

- Example 

```python 
self.GetEntitySourceId(entityId) 
``` 

## CreateChestBlockComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a chestBlock component


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ChestContainerCompServer | chestBlock component instance | 

## GetChestBoxSize 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the box capacity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Chest position | 
| dimensionId | int | The dimension where the box is located, you can get the box capacity in the constant loading block of the corresponding dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Box size, error value -1 | 

- Example 

```python 
self.GetChestBoxSize((x, y, z), 0) 
``` 

## SetChestBoxItemNum 

<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the number of items in a box slot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(int,int,int) | Box position | 
| slotPos | int | Box slot | 
| num | int | Number of items | 
| dimensionId | int | The dimension where the block is located. You can set the block in the constant loading block of the corresponding dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Example 

```python 
self.SetChestBoxItemNum((x,y,z), 0, 10, 0) 
``` 

## SetChestBoxItemExchange 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Exchange the slots of items in the box 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | player id | 
| pos | tuple(int,int,int) | box position | 
| slotPos1 | int | box slot 1 | 
| slotPos2 | int | box slot 2 | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns True if set successfully, False if failed | 

- Example 

```python 
self.SetChestBoxItemExchange(playerId, (x,y,z), 0, 1) 
``` 

## CreateChunkSourceComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create chunkSource component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ChunkSourceCompServer or ChunkSourceCompClient | chunkSource component instance | 

## SetAddArea 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set constant loading of blocks 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| key | str | Name of the constantly loading area | 
| dimensionId | int | Dimension of the chunk | 
| minPos | tuple(int,int,int) | Minimum coordinates of the loading area | 
| maxPos | tuple(int,int,int) | Maximum coordinates of the loading area | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting was successful | 

- Notes 
- The key must be unique. If the key already exists when adding an area, the addition will fail. 
- The constantly loading area created in this way will not tick, that is, entities, block entities, and random ticks will not be updated. If the area needs to be ticked, please use the original [tickingarea command](https://minecraft-zh.gamepedia.com/%E5%91%BD%E4%BB%A4/tickingarea). 
- When setting a currently unloaded chunk as a constantly loaded chunk, creatures will not be loaded from the save file. However, if it is a currently loaded chunk, the entities in the chunk will remain loaded after the player moves away from the chunk. 
- In a constantly loaded chunk, you can use the API to create entities, place blocks, place structures, and modify block entity data. However, due to the characteristics of chunk loading, you need to set the area 80 blocks around the operation location to constantly load. For example, if you need to generate creatures/place blocks at (0,5,0), you need to set the area from (-80,0,-80) to (80,0,80) to constantly load. 

- Example 

```python 
self.SetAddArea('Area0', 0, (0,0,0), (60,0,60)) 
``` 

## DeleteArea 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Delete a constant loading area 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| key | str | Name of the constant loading area | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the deletion is successful | 

- Example 

```python

self.DeleteArea('Area0') 
``` 

## DeleteAllArea 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Delete all constantly loaded areas 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Number of areas to delete, None if error occurs | 

## GetAllAreaKeys 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the name list of all frequently loaded areas 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Name list list | 

## CheckChunkState

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Check whether the chunk at the specified position has been loaded 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension where the chunk is located | 
| pos | tuple(int,int,int) | Coordinates of the specified position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the loading is completed | 

- Example 

```python 
self.CheckChunkState(0, (0, 0, 0)) 
``` 

## GetLoadedChunks 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the coordinate list of all chunks that have been loaded in the specified dimension 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| None or list(tuple(int,int)) | List of chunk coordinates (chunk coordinates are (x,z)). Returns None if the specified dimension does not exist or has not been created. | 

- Example 

```python 
result = self.GetLoadedChunks(0) 
print "dimension {} has chunk {}".format(0, result) 
``` 

## GetChunkEntities 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get a list of all entity and player IDs in the chunk at the specified location 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension | 
| pos | tuple(int,int,int) | Coordinates of the specified position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| None or list(str) | List of entity and player IDs. Returns None when the chunk at the specified position does not exist or has not been loaded | 

- Example 

```python 
entityList = self.GetChunkEntites(0, (0, 0, 0)) 
print "GetChunkEntities entityList={}".format(entityList) 
``` 

## GetChunkMobNum 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description


Get the number of mobs in a chunk (excluding players but including armor stands) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension of the chunk | 
| chunkPos | tuple(int,int) | Coordinates of the specified chunk | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Number of mobs in the chunk | 

- Notes 
- A return value of -1 is usually because the dimension is not loaded or the chunk is not loaded 

- Example 

```python 
mobNum = self.GetChunkMobNum(0, (1, 3)) 
``` 

## IsChunkGenerated 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get whether a chunk has been generated. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension of the chunk | 
| chunkPos | tuple(int,int) | Coordinates of the specified chunk | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the chunk has been generated | 


- Notes 
- Chunks that have been explored by the player (with the player as the center and the simulation distance (in the game's settings page) as the radius), or chunks near the constantly loaded chunks set using SetAddArea, are all generated chunks. These chunks will be saved in the archive, and will be read from the archive when explored again, and will not be regenerated. 

- Example 

```python 
# Get whether the chunk at the coordinates of the main world (10000,0,10000) has been generated 
result = self.IsChunkGenerated(0, comp.GetChunkPosFromBlockPos((10000, 0, 10000))) 
``` 

## CreateCollisionBoxComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create collisionBox component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| CollisionBoxComponentServer | collisionBox component instance | 

## SetEntityCollisionBoxSize 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the bounding box of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| entityId | str or int | entity id | 
| size | tuple(float,float) | The first digit indicates width and length, the second digit indicates height | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- For newly generated entities, it takes 5 frames before the bounding box size is set to take effect 

- Example 

```python 
self.SetEntityCollisionBoxSize(entityId, (2,3)) 
``` 

## GetEntityCollisionBoxSize 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the bounding box of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Bounding box size | 

- Example 

```python 
self.GetEntityCollisionBoxSize(entityId) 
``` 



## CreateCommandComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create command component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| CommandCompServer | Command component instance | 

## SetCommand 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Use in-game commands 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| cmdStr | str | Command | 
| playerId | str | Player id (optional). If playerId is not set, a random player is selected | 
| showOutput | bool | Whether to output to the chat window: optional, default False. If True, the return information will be output just like the native command input in the chat window. OnCommandOutputServerEvent and OnCommandOutputClientEvent will be triggered only when this parameter is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the command is executed successfully | 

- Example 


```python 
# Send command 
self.SetCommand("/tp @p 100 5 100") 
``` 

## GetCommandPermissionLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Returns the permission level of OP when using the /op command (corresponding to the op-permission-level configuration in server.properties) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Permission level: 1-OP can bypass respawn point protection; 2-OP can use all single-player cheat commands; 3-OP can use most multiplayer game-specific commands; 4-OP can use all commands | 

- Example 

```python 
opLevel = self.GetCommandPermissionLevel() 
print "GetCommandPermissionLevel oplevel={}".format(opLevel) 
``` 

## SetCommandPermissionLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the OP's permission level when the player uses the /op command (corresponding to the op-permission-level configuration in server.properties) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| opLevel | int | Permission level: 1-OP can bypass respawn point protection; 2-OP can use all single-player cheat commands; 3-OP can use most multiplayer game-unique commands; 4-OP can use all commands | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the command is executed successfully | 

- Notes 
- This API will not modify the permission level of players who have already obtained op, but only affects players who obtain op after calling the API. It is recommended to call this API when the game is initialized 

- Example 

```python 
opLevel = 4 
suc = self.SetCommandPermissionLevel(opLevel) 
print "SetCommandPermissionLevel to {} suc={}".format(opLevel, suc) 
``` 

## GetDefaultPlayerPermissionLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Returns the permission identity of the new player when joining (corresponding to the default-player-permission-level configuration in server.properties) 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Permission identity: 0-Visitor; 1-Member; 2-Operator; 3-Custom | 

- Example 

```python 
opLevel = self.GetDefaultPlayerPermissionLevel() 
print "GetDefaultPlayerPermissionLevel oplevel={}".format(opLevel) 
``` 



## SetDefaultPlayerPermissionLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the permission identity when a new player joins (corresponding to the default-player-permission-level configuration in server.properties) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| opLevel | int | Permission identity: 0-Visitor; 1-Member; 2-Operator; 3-Custom | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the command is executed successfully | 

- Notes 
- This API will not modify the permissions of players who have already joined the game. It only affects players who join after calling the API. It is recommended to call this API when the game is initialized. 

- Example 

```python 
opLevel = 1 
suc = self.SetDefaultPlayerPermissionLevel(opLevel) 
print "SetDefaultPlayerPermissionLevel to {} suc={}".format(opLevel, suc) 
``` 

## CreateControlAiComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create controlAi component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int |Entity id |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ControlAiCompServer | controlAi component instance | 

## SetEntityBlockControlAi 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the native AI of the shielded creature 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| isBlock | bool | Whether to keep AI, False means shielding | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Mobs with AI blocked cannot move, are not affected by gravity, and cannot be pushed. However, they can be damaged and can be interacted with by players (for example, horses can be ridden or villagers can be traded) 

- Example 

```python 
self.SetBlockControlAi(entityId, False) 
``` 

## CreateDimensionComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description


    Create dimension component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| DimensionCompServer | Dimension component instance | 

## GetEntityDimensionId 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the dimension where the entity is located 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Dimension id, 0-main world; 1-nether; 2-the end; or other custom dimensions | 

## ChangeEntityDimension 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Teleport entities other than players


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| dimensionId | int | Dimension id, 0-Main world; 1-Nether; 2-The End; or other custom dimensions | 
| pos | tuple(int,int,int) | Coordinates of the teleportation. If None is entered, the portal of the target dimension is selected as the destination first, and then the dimension coordinate mapping logic is used to determine the destination | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- This interface cannot be used for players. Players should use ChangePlayerDimension 

- Example 

```python 
self.ChangeEntityDimension(entityId, 0, (0,4,0)) 
``` 

## ChangePlayerDimension 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Teleport player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Player id | 
| dimensionId | int | Dimension, 0-overWorld; 1-nether; 2-theEnd | 
| pos | tuple(int,int,int) | Teleported coordinates | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 


- Notes 
- When the interface successfully switches dimensions, the pos position is the position of the player's head, which is 1.62 lower than the set position 

- Example 

```python 
self.ChangePlayerDimension(playerId, 0, (0,4,0)) 
``` 

## MirrorDimension 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Copy terrain of different dimensions 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fromId | int | Original dimensionId | 
| toId | int | Target dimensionId | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Only the block information that has been generated in the source dimension is copied to the new dimension. For the ungenerated source dimension blocks, the generation logic cannot be completely copied, and some of the new dimension's own information may be used. 

- Example 

```python 
self.MirrorDimension(0, 1) 
``` 

## CreateDimension 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface


- Description 

Create a new dimension 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimensionId | int | Dimension. Dimensions 0/1/2 do not need to be created. To create a dimension greater than 20, you need to register it in dimension_config.json. Note that dimension 21 is not available. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the creation is successful | 

- Notes 
- It is recommended to call it uniformly when the mod is initialized 

- Example 

```python 
self.CreateDimension(3) 
``` 

## RegisterEntityAOIEvent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Register the sensing area. There will be a message notification when an entity enters and leaves 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension id | 
| name | str | Registered sensing area name | 
| aabb | tuple(float,float,float,float,float,float) | Coordinate range of the sensing area, in order of minX, minY, minZ, maxX, maxY, maxZ | 
| ignoredEntities | list(str) | List of ignored entity ids | 
| entityType | int | Entity type expected to respond to, if not passed, respond to all entity types <a href="../../../1-ModAPI/Enumeration value/EntityType.html">EntityType enumeration</a> | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Notes 
- After registering the sensing area, you need to listen to the OnEntityAreaEvent or NewOnEntityAreaEvent event to obtain the sensing event 

- Example 

```python 
self.RegisterEntityAOIEvent(0, "test", (0, 0, 0, 1, 1, 1), None) 
``` 

## UnRegisterEntityAOIEvent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Unregister sensing area 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | dimension id | 
| name | str | name of the sensing area to be unregistered | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether registration is successful | 

- Example 

```python 
self.UnRegisterEntityAOIEvent(0, "test") 
``` 

## SetUseLocalTime 

<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Let a dimension have its own local time rules. After turning it on, the dimension can have different time and day and night rules from other dimensions 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension id | 
| value | bool | Whether to turn on local time rules | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to set successfully | 

- Notes 
- We have added the concept of "local time rules" to the main world and custom dimensions. Before this, all dimensions shared a "global time", that is, when setting time or dodaynightcycle rules, it will take effect on all dimensions.
Now, we can set a dimension to use local time rules and set its time (see [SetLocalTime](#setlocaltime)) and dodaynightcycle rules (see [SetLocalDoDayNightCycle](#setlocaldodaynightcycle)) separately. 
In the following, we will call the dimension using local time rules "local dimension" and the dimension using global time rules "global dimension". By default, all dimensions are global dimensions. 
The original time command, the gamerule dodaylightcycle command and the setting of turning on the day and night cycle, and the daylock command and the setting of always being daylight will not work on local dimensions. 
When there are both local dimensions and global dimensions in the world, there are only two situations in which you can sleep to skip the night: 
1. All players sleep in the global dimension. In this case, the global time will jump to the next morning. 
2. All players sleep in the same local dimension. In this case, the time of the local dimension will jump to the next morning. 
- When local time rules are enabled, the global time and day-night alternation rules are inherited by default 
- Time rules are invalid for the original Nether and the End, these two dimensions are always dark and have no day-night alternation 
- It is recommended to call them uniformly when the game starts 
- In the PC development kit, you can type `dmtime on` or `dmtime off` in the chat bar to test turning on and off the local time of the current dimension 

- Example 

```python 
self.SetUseLocalTime(3, True) 
``` 

## GetUseLocalTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get whether a dimension is set to use local time rules 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to use local time rules | 

- Remarks 
- For "local time rules", see [SetUseLocalTime](#setuselocaltime) 

- Example 

```python 
self.GetUseLocalTime(3) 
``` 

## SetLocalTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the time using the local time rule dimension 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension id | 
| time | int | Time, in frames. Indicates the time since the archive was created, not the time in the current game day. One game day in MC is equivalent to 20 minutes in reality, that is, 24,000 frames | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The game has the concept of days, which needs to be considered when using it. You can also use [SetLocalTimeOfDay](#setlocaltimeofday) to set the time of day without calculating the number of days. 
- Can only be set when using the local time rule dimension 
- For "local time rule", see [SetUseLocalTime](#setuselocaltime)


- Example 

```python 
# Get the current time 
passedTime = self.GetLocalTime(3) 
# Get the current day 
day = passedTime / 24000 
# Set to noon of the day 
self.SetLocalTime(3, day * 24000 + 6000) 
# Set to sunrise of the next day 
self.SetLocalTime(3, (day + 1) * 24000 + 0) 
``` 

## SetLocalTimeOfDay 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the time of the day using the local time rule dimension 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| dimension | int | Dimension id | 
| timeOfDay | int | Time, in frames, representing the time in a game day, ranging from 0 to 24000. One game day in MC is equivalent to 20 minutes in reality, that is, 24,000 frames | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The specific logic is the same as the time instruction. If timeOfDay is later than the current time, it is set to the timeOfDay of the current day; if timeOfDay is earlier than the current time, it is set to the timeOfDay of the next day. 
- In the PC development kit, you can type `dmtime time <int: frame number>` in the chat bar to test setting the local time of the current dimension 

- Example 

```python 
# Set to noon 
self.SetLocalTimeOfDay(3, 6000) 
``` 




## GetLocalTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the time of a dimension 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Time, in frames, indicating the time since the archive was created, not the time in the current game day. One game day in mc is equivalent to 20 minutes in reality, that is, 24000 frames | 

- Notes 
- When the dimension uses the local time rule, the local time is returned; when it is not used, the global time is returned 
- For "local time rule", see [SetUseLocalTime](#setuselocaltime) 

- Example 

```python 
# Total number of frames since the start of the game 
passedTime = self.GetLocalTime(3) 
# Number of frames in the current game day 
timeOfDay = passedTime % 24000 
# Number of game days since the start of the game 
day = passedTime / 24000 
``` 

## SetLocalDoDayNightCycle 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether the dimension using local time rules turns on day and night changes


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension id | 
| value | bool | Whether to open the day and night cycle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Only dimensions that use local time rules can be set 
- For "local time rules", see [SetUseLocalTime](#setuselocaltime) 
- In the PC development kit, you can type `dmtime cycle on` or `dmtime cycle off` in the chat bar to test whether to open and close the day and night cycle of the current dimension 

- Example 

```python 
self.SetLocalDoDayNightCycle(3, False) 
``` 

## GetLocalDoDayNightCycle 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Gets whether the dimension has day and night cycles turned on 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dimension | int | Dimension id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether to turn on day and night cycles | 

- Notes

- When the dimension uses the local time rule, it returns the dimension's own day and night change rule; when it does not use it, it returns the global day and night change rule 
- For "local time rule", see [SetUseLocalTime](#setuselocaltime) 

- Example 

```python 
self.GetLocalDoDayNightCycle(3) 
``` 

## CreateEffectComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create effect component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| EffectComponentServer | effect component instance | 

## RemoveEffectFromEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Delete the specified status effect for the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id |

| effectName | str | Status effect name string, including custom status effects and original status effects. Original status effects can be found in the wiki | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True indicates successful deletion | 

- Example 

```python 
res = self.RemoveEffectFromEntity(entityId, "speed") 
``` 

## AddEffectToEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Adds the specified status effect to the entity. If the added status already exists, the following situations will occur: 1. If the level is greater than the existing one, update the status level and duration; 2. If the status levels are equal and the remaining duration is greater than the existing one, refresh the remaining duration; 3. If the level is less than the existing one, do not modify it; 4. The particle effect is based on the new one. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| effectName | str | Status effect name string, including custom status effects and vanilla status effects. Vanilla status effects can be found on the wiki | 
| duration | int | Status effect duration, in seconds | 
| amplifier | int | Additional level of the status effect. Must be between 0 and 255 (inclusive). If not specified, defaults to 0. Note that the first level of status effects (such as life recovery I) corresponds to 0, so the second level status effects, such as life recovery II, should specify an intensity of 1. Some effects and custom status effects have no intensity difference, such as night vision | 
| showParticles | bool | Whether to display particle effects, True to display, False not to display | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True means the setting is successful | 

- Example 

```python 
res = self.AddEffectToEntity(entityId, "speed", 30, 2, True) 
``` 



## GetEntityEffects 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get all current status effects of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(dict) | List of status effect information dictionary | 

- Notes 
- Status effect information dictionary effectDict 
| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| effectName | str | Status effect name | 
| duration | int | Status effect remaining duration, in seconds | 
| amplifier | int | Status effect additional level | 

- Example 

```python 
effectDictList = self.GetEntityEffects(entityId) 
``` 

## CreateEngineTypeComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create engineType component 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| EngineTypeComponentServer or EngineTypeComponentClient | engineType component instance | 

## GetEntityEngineTypeStr 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the type name of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Entity type name, such as minecraft:husk | 

- Example 

```python 
engineType = self.GetEntityEngineTypeStr(entityId) 
``` 

## GetEntityEngineType 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- describe


Get entity type 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | See <a href="../../../1-ModAPI/Enumeration value/EntityType.html">EntityType enumeration</a> for details | 

- Example 

```python 
entityType = self.GetEntityEngineType(entityId) 
# Take the example of judging whether it is a Mob. If you want to judge whether it is a projectile, find the corresponding type Projectile and modify it. 
if entityType & self.GetMinecraftEnum().EntityType.Mob == self.GetMinecraftEnum().EntityType.Mob: 
logger.info("{} is Mod".format(self.GetEngineTypeStr(entityId))) 
``` 

## CreateEntityEventComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create entityEvent component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| EntityEventComponentServer | entityEvent component instance | 

## TriggerEntityCustomEvent 

<span style="display:inline;color:#ff5555">Server side</span>


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Trigger custom events for creatures 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str | Creature ID | 
| eventName | str | Event name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- Trigger creeper explosion 
Add the following event to the `events` field in the creeper entity json file, and then run the sample code in the mod: 
```json 
"netease:custom_exploading":{ 
"sequence": [ 
{ 
"filters": {
                    "test": "has_component",
                        "operator": "!=",
                        "value": "minecraft:is_charged"
                      },
                      "add": {
                        "component_groups": [
                          "minecraft:forced_exploding"
                        ]
                      }
                    },
                    {
                      "filters": {
                        "test": "has_component",
                        "value": "minecraft:is_charged"
                      },
                      "add": {
                        "component_groups": [
                          "minecraft:forced_charged_exploding"
                        ]
                      }
                    }
                  ]

} 
``` 

- Example 

```python 
#Trigger entity custom event 
eventName = "netease:custom_exploading" 
self.TriggerCustomEvent(entityId, eventName) 
``` 

## CreateExtraDataComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create extraData component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id, if not passed, use LevelId | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ExDataCompServer | extraData component instance | 

## GetExtraData 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the custom data of the entity or the custom data of the world, the value corresponding to a key. Get the entity data and pass it in the corresponding entity id 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| key | str | custom key | 
| entityId | str or int | entity id, if not passed, use LevelId | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| any | Value corresponding to key | 

- Example 

```python 
self.GetExtraData("globalMsg") 
``` 

## SaveExtraData 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Used to save custom data of entities or custom data of the world 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id, if not passed, use LevelId | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Save result | 

- Example 

```python 
# Save custom data 
self.SaveExtraData() 
``` 

## SetExtraData


<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Used to set custom data of entities or custom data of the world. The data is saved in the form of key-value pairs. When setting entity data, use the corresponding entity id to create a component. When setting world data, use levelId to create a component. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| key | str | Custom key | 
| value | any | The value corresponding to the key, supports Python basic data types | 
| entityId | str or int | Entity id, if not passed, use LevelId | 
| autoSave | bool | Automatically save by default, the default is True. If you set data in batches, please set this parameter to False, and call the SaveExtraData interface when the data setting is completed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Example 

```python 
self.SetExtraData("globalMsg", "helloWorld") 
``` 

## CleanExtraData 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Clear the custom data of the entity or the custom data of the world. When clearing entity data, use the corresponding entity id to create a component. When clearing world data, use levelId to create a component. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| key | str | Custom key | 
| entityId | str or int | Entity id, if not passed, use LevelId | 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
suc = self.CleanExtraData("globalMsg") 
print "CleanExtraData for level suc=%s" % suc 
``` 

## GetWholeExtraData 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the complete entity's custom data or the world's custom data. When getting entity data, use the corresponding entity id to create a component. When getting world data, use levelId to create a component. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id, if not passed, use LevelId | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict or None | Get the specified entity or global extra storage data dictionary. If there is no extra storage data, return None or an empty dictionary | 

- Example 

```python 
dataDict = self.GetWholeExtraData() 
if dataDict: 
for key, value in dataDict.iteritems(): 
print "key=%s value=%s" % (key, str(value)) 
``` 

## CreateExpComponent 

<span style="display:inline;color:#ff5555">Server</span>


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create exp component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ExpComponentServer | exp component instance | 

## GetPlayerExp 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the player's experience value at the current level 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Player id | 
| isPercent | bool | Is it a percentage | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| float | Player experience value | 

- Notes 
- If the return percentage is set to False, the absolute value of the player's experience at the current level (not the current player's total experience value) is returned. 

- Example 

```python

print(self.GetPlayerExp(playerId, False)) 
``` 

## AddPlayerExp 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Increase player experience 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str or int | Player id | 
| exp | int | Player experience, can be set to negative | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- If the set exp value is a negative number and exceeds the existing experience value of the current level, after calling the interface, the player's level will not decrease but the experience value will be set to the minimum value 

- Example 

```python 
self.AddPlayerExp(entityId, 25) 
``` 

## GetPlayerTotalExp 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the total experience value of the player 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Player id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Total experience value, a positive integer. Returns -1 if the acquisition fails. | 

- Example 

```python 
print(self.GetPlayerTotalExp(playerId)) 
``` 

## SetPlayerTotalExp 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the total experience of the player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str or int | Player id | 
| exp | int | Total experience, positive integer | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The level will be recalculated based on the total experience value. This interface can cause level changes 
- Internal calculations use floating point numbers, and errors will occur when the value is large 

- Example 

```python 
self.SetPlayerTotalExp(playerId, 25)

``` 

## GetOrbExperience 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the experience of the experience ball 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Experience ball entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Experience value, positive integer. Returns -1 if acquisition fails. | 

- Example 

```python 
print(self.GetOrbExperience(entityId)) 
``` 

## SetOrbExperience 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the experience of the experience ball 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Experience ball entity id | 
| exp | int | Experience ball experience |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Set the experience of the experience ball. entityId is the entityId of the experience ball. If the experience is less than or equal to 0, no experience will be added after picking it up. 

- Example 

```python 
self.SetOrbExperience(entityId, 25) 
``` 

## CreateExperienceOrb 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a dedicated experience ball 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | int | Exclusive player ID, only this player can pick up the generated experience ball | 
| exp | int | Experience ball experience | 
| position | tuple(float,float,float) | Created position | 
| isSpecial | bool | Whether it is an exclusive experience ball | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.CreateExperienceOrb(playerId, 25, (10,10,10), False) 
``` 




## CreateExplosionComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create explosion component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ExplosionComponentServer | Explosion component instance | 

## CreateExplosion 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Used to generate explosions 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Explosion position | 
| radius | int | Explosion power. For specific meanings, please refer to the explanation of explosions in [wiki](https://minecraft-zh.gamepedia.com/%E7%88%86%E7%82%B8) | 
| fire | bool | Whether to bring fire | 
| breaks | bool | Whether to destroy blocks | 
| sourceId | str | Entity id of the explosion damage source | 
| playerId | str | Entity id created by the explosion | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Set result | 

- Example 

```python 
self.CreateExplosion((50,50,50),10,True,True,sourceId,playerId) 
``` 

## CreateFeatureComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create feature component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| FeatureCompServer | feature component instance | 

## AddNeteaseFeatureWhiteList 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Add the script layer listener of the structure to the PlaceNeteaseStructureFeatureEvent event 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| structureName | str | Structure identifier | 


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Add successfully | 

- Example 

```python 
# Note that the format of structureName is floderName:structureName 
self.AddNeteaseFeatureWhiteList("test:pumpkins") 
``` 

## RemoveNeteaseFeatureWhiteList 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Remove the script layer monitoring of the PlaceNeteaseStructureFeatureEvent event from structureName 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| structureName | str | structure name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the removal is successful | 

- Example 

```python 
# Note that the format of structureName is floderName:structureName 
self.RemoveNeteaseFeatureWhiteList("test:pumpkins") 
``` 

## ClearAllNeteaseFeatureWhiteList 

<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Clear all script-level listeners of the PlaceNeteaseStructureFeatureEvent event for the added Netease Structure Feature 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether clearing is successful | 

- Example 

```python 
self.ClearAllNeteaseFeatureWhiteList() 
``` 

## LocateStructureFeature 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Similar to the [/locate command](https://minecraft-zh.gamepedia.com/%E5%91%BD%E4%BB%A4/locate), it is used to locate some structures in the original version, such as underwater temples, end cities, etc. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| featureType | int | Original structure type, <a href="../../../1-ModAPI/Enumeration value/StructureFeatureType.html">StructureFeatureType</a> enumeration | 
| dimensionId | int | The dimension where the structure is located, **Requires that the dimension has been loaded** | 
| pos | tuple(int,int,int) | Find the nearest structure with this position as the center | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) or None | The block location of the nearest structure (x coordinate, z coordinate), the y coordinate is uncertain, and None is returned if positioning fails | 

- Notes 
- Positioning failure is usually due to the dimension not existing, the dimension not being loaded, the structure not existing in the dimension, the structure being too far from the passed position, etc.

- The return value of this interface is the coordinates of the block where the corresponding structure is located, which may be a certain distance away from the actual generated location of the structure 

- Example 

```python 
pos = self.LocateStructureFeature(self.GetMinecraftEnum().StructureFeatureType.Village, 0, (0, 64, 0)) 
``` 

## LocateNeteaseFeatureRule 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Similar to the [/locate command](https://minecraft-zh.gamepedia.com/%E5%91%BD%E4%BB%A4/locate), it is used to locate <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/4-Custom Dimensions/4-Custom Features.html#Feature Rules (feature-rules)" rel="noopenner"> NetEase Custom Feature Rules </a> 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| ruleName | str | Feature rule name, in the form of namespace:featureRuleIdentifier, such as custombiomes:overworld_pumpkins_feature_rule | 
| dimensionId | int | Find dimension, **Requires the dimension to be loaded** | 
| pos | tuple(int,int,int) | Use this position as the center to find coordinates that meet the distribution conditions of NetEase custom feature rules | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) or None | The nearest coordinate that meets the distribution conditions of NetEase custom feature rules. If positioning fails, None is returned | 

- Notes 
- Positioning failure is usually due to the non-existence of the input dimension, the dimension is not loaded, there are no coordinates that meet the distribution conditions of the custom feature rule, the target coordinates are too far from the input position (with the position as the center, it cannot be found within a radius of 100 blocks), etc. 
- If a filter rule other than the judgment dimension is filled in in "minecraft:biome_filter" in "conditions" in feature rules, there is a probability that the coordinates that meet the distribution conditions of the custom feature rule cannot be located. It is recommended that developers use query.is_biome instead in "iterations" of "distribution" 
- The positioning principle is to find possible locations based on the distribution conditions of NetEase's custom feature rules, so it is possible to locate the structure location that was canceled in the PlaceNeteaseStructureFeatureEvent event. Developers should pay attention to identification and try to avoid calling the positioning function for the feature rule file corresponding to the structure that may be canceled in the PlaceNeteaseStructureFeatureEvent event. 

- Example 

```python 
pos = self.LocateNeteaseFeatureRule("custombiomes:overworld_pumpkins_feature_rule", 0, (0, 64, 0)) 
``` 

## CreateFlyComponent 

<span style="display:inline;color:#ff5555">Server</span>


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create fly component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str or int | Player id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| FlyComponentServer | fly component instance | 

## IsPlayerFlying 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get whether the player is flying 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Player id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: Yes False: No | 

- Example 

```python 
self.IsPlayerFlying(playerId) 
``` 




## ChangePlayerFlyState 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Grant/cancel flying ability and enter flying/non-flying state 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str or int | Player id | 
| isFly | bool | Flying state, True: flying mode, False: normal walking mode | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: Yes False: No | 

- Example 

```python 
self.ChangePlayerFlyState(playerId, True) 
``` 

## CreateGameComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create game component 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| GameComponentServer or GameComponentClient | Game component instance | 

## AddBlockProtectField 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

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
| int | Returns the unique ID of the area when successful, which can be used to cancel the indestructible area, and returns -1 when failed | 

- Example 

```python 
field = self.AddBlockProtectField(0, (-20, 0, -20), (20, 255, 20)) 
if field > 0: 
print "AddBlockProtectField success field={}".format(field) 
else: 
print "AddBlockProtectField fail" 
``` 

## RemoveBlockProtectField 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Removes a block from being destructible by the player/entity 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| field | int | Unique ID of the indestructible area, return value of AddBlockProtectField | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | success True means cancellation is successful, False means cancellation fails | 

## CleanBlockProtectField 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Cancel all areas where blocks that have been set cannot be destroyed by players/entities 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | success True means cancellation is successful, False means cancellation is failed | 

## KillEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Kill an Entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| entityId | str | The entityId of the target to be killed | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the killing was successful | 

- Example 

```python 
self.KillEntity(entityId) 
``` 

## CreateEngineEntityByTypeStr 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create an entity with the specified identifier 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| engineTypeStr | str | Entity identifier, such as 'minecraft:husk' | 
| pos | tuple(float,float,float) | Coordinates of the generated entity | 
| rot | tuple(float,float) | Mob orientation | 
| dimensionId | int | Dimension of the generated entity, default value is 0 (0 is the Overworld, 1 is the Underworld, 2 is the End) | 
| isNpc | bool | Whether it is an NPC, default value is False. NPCs will not move, turn, or save. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str or None | Entity ID or None | 

- Notes 
- Cannot create in unloaded chunks 
To generate villagers, please use "minecraft:villager_v2" 

- Example 

```python 
self.CreateEngineEntityByTypeStr('minecraft:husk', (0, 5, 0), (0, 0), 0)

``` 

## PlaceStructure 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Place structure 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| pos | tuple(float,float,float) | Position of placing structure | 
| structureName | str | Structure name | 
| dimensionId | int | Dimension where you want to place the structure. You can place the structure in the constant loading block of the corresponding dimension. The default is -1 | 
| rotation | int | Rotation angle of the placed structure. The default is 0 (can only rotate 90, 180, 270 degrees) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the placement is successful, True means the placement is successful, False means the placement fails | 

- Notes 
- When placing, you need to ensure that the blocks to be placed have been loaded, otherwise the placement will fail or be partially missing 
- This interface is executed synchronously, please do not place a large number of structures in one frame, which will cause the game to freeze 

- Example 

```python 
self.PlaceStructure((100, 70, 100), "test:structureName", 0) 
``` 

## AddTimer 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Add timer, non-repeating


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| delay | float | Delay time, in seconds | 
| func | function | Timer trigger function | 
| *args | any | Variable length parameter, optional | 
| **kwargs | any | Dictionary variable length parameter, optional | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| CallLater | Returns a single-trigger timer instance | 

## AddRepeatedTimer 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Add a timer triggered by the server and execute it repeatedly 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| delay | float | Delay time, in seconds | 
| func | function | Timer trigger function | 
| *args | any | Variable length parameter, can be left blank | 
| **kwargs | any | Dictionary variable length parameter, can be left blank | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| CallLater | Return the triggered timer instance | 

## CancelTimer 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface


- Description 

Cancel the timer 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| timer | CallLater | Timer instance returned by AddTimer and AddRepeatedTimer | 

- Return value 

None 

## GetEntitiesInArea 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the entity list in the area 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| startPos | tuple(int,int,int) | initial position | 
| endPos | tuple(int,int,int) | end position | 
| dimensionId | int | The dimension where the area is located. Only valid on the server side. You can get the entity list in the constant loading block of the corresponding dimension. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Returns a list of entityId | 

- Example 

```python 
self.GetEntitiesInSquareArea((0,0,0), (100,100,100), 0) 
``` 

## GetEntitiesAround


<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the entity list in the area 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str | A certain entityId | 
| radius | int | Cube area radius | 
| filters | dict | Filter settings dictionary | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) | Returns a list of entityIds | 

- Example 

```python 
#Use filters to get entities around the player 
#The filters in the example represent entities that meet the conditions of "being a player" or "not wearing a pumpkin hat" 
filters = { 
"any_of": [ 
{ 
"subject" : "other", 
"test" : "is_family", 
"value" : "player" 
}, 
{ 
"test" : "has_equipment", 
"domain": "head", 
"subject" : "other", 
"operator" : "not", 
"value" : "carved_pumpkin" 
} 
] 
} 
self.GetEntitiesAround(entityId, 100, filters) 
``` 

## ShowHealthBar


<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether to display the health bar 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| show | bool | True means display. After enabling, you can use the health component to set the color of an entity's health bar and whether to display it | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.ShowHealthBar(True) 
``` 

## SetNameDeeptest 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether the name is perspective 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| deeptest | bool | True means no perspective. Perspective by default | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful |


- Example 

```python 
# Set to non-perspective 
self.SetNameDeeptest(True) 
``` 

## GetScreenSize 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the game resolution 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | Width and height (pixels) | 

- Example 

```python 
width, height = self.GetScreenSize() 
``` 

## SetRenderLocalPlayer 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether the local player is rendered 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| render | bool | True for rendering | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# Do not render local players 
self.SetRenderLocalPlayer(False) 
``` 

## AddPickBlacklist 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Add a blacklist when using the camera component to select an entity, that is, the entity will not be selected 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# Add blacklist 
self.AddPickBlacklist(entityId) 
``` 



## ClearPickBlacklist 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Clear the blacklist of entities selected using the camera component 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether successful | 

- Example 

```python 
# Clear all entities in the blacklist 
self.ClearPickBlacklist() 
``` 

## CheckWordsValid 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Check whether the statement is legal, that is, it does not contain sensitive words 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| words | str | Statement | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: The statement is legal<br>False: The statement is illegal |


- Example 

```python 
isValid = self.CheckWordsValid("creeper? Aww man") 
``` 

## CheckNameValid 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Check whether the nickname is legal, that is, it does not contain sensitive words 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| name | str | Nickname | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: Nickname is valid False: Nickname is invalid | 

- Example 

```python 
isValid = self.CheckNameValid("Steve") 
``` 

## GetScreenViewInfo 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get game perspective information. When the resolution is 1313,618, the canvas is twice 376,250, so the viewport gets 1313 + (2-(1313%2)). The y value is similar. Please refer to <a href="../../../../mcguide/18-Interface and Interaction/1-Interface Editor Instructions.html#《My World》Interface Adaptation Method" rel="noopenner">《My World》Interface Adaptation Method </a> 

- Parameters


    None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float,float) | width, height, x offset, y offset | 

- Example 

```python 
width, height, offsetX, offsetY= self.GetScreenViewInfo() 
``` 

## SimulateTouchWithMouse 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Simulate using the mouse to control the UI (PC F11 shortcut key) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| touch | bool | True: enter mouse mode, False: exit mouse mode | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Simulation result | 

- Example 

```python 
self.SimulateTouchWithMouse(True) 
``` 

## GetCurrentDimension 

<span style="display:inline;color:#7575f9">Client</span>


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the current dimension of the client 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Dimension id. If the client has not completed the login or is cutting the dimension, -1 is returned | 

- Example 

```python 
dimId = self.GetCurrentDimension() 
``` 

## GetChinese 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the Chinese corresponding to langStr. Please refer to \handheld\bed-loc\handheld\data\resource_packs\vanilla\texts\zh_CN.lang in the PC development kit 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| langStr | str | The passed langStr | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | The Chinese corresponding to langStr. If the corresponding Chinese cannot be found, langStr itself will be returned | 

- Example 

```python

# Get the Chinese corresponding to "entity.wolf.name" ("狼") 
Chinese = self.GetChinese("entity.wolf.name") 
``` 

## SetDisableHunger 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether to block hunger 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| isDisable | bool | Whether to block hunger | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- If you need to hide hunger, please use HideHungerGui of extraClientApi 

- Example 

```python 
self.SetDisableHunger(True) 
``` 

## SetOneTipMessage 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Pop up a tip type notification above the inventory of a specific player, located above the popup type notification. For this function, it is recommended to use the corresponding interface SetTipMessage of the game component on the client 

- Parameters


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Specific player ID | 
| message | str | Message content, you can add extraServerApi.GenerateColor("RED") characters before the message to set the color, refer to the sample for details | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# Change the playerId variable to a specific player ID 
self.SetOneTipMessage(playerId, serverApi.GenerateColor("RED") + "tip prompt") 
``` 

## SetPopupNotice 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Pop up a popup notification above the inventory, below the tip message. The server call is for all players, and the client call only affects the local player. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| message | str | Message content, you can add extraClientApi.GenerateColor("RED") characters to set the color before the message, refer to the sample for details | 
| subtitle | str | Message subtitle content, the effect is the same as message, you can also set the color, the position is above the message | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetPopupNotice(clientApi.GenerateColor("RED") + "Message notification", "Message subtitle") 
``` 




## SetTipMessage 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Pop up a tip notification above the inventory, located above the popup notification. The server call is for all players, and the client call only affects the local player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| message | str | Message content, you can add extraServerApi.GenerateColor("RED") characters before the message to set the color, refer to the sample for details | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetTipMessage(serverApi.GenerateColor("RED") + "tip prompt") 
``` 

## SetNotifyMsg 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set message notification 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| msg | str | Message content | 
| color | str | ColorCode, default is white | 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetNotifyMsg("Message notification", self.GetMinecraftEnum().ColorCode.BLUE)) 
``` 

## GetPlayerGameType 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the game mode of the specified player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | <a href="../../../1-ModAPI/Enumeration value/GameType.html">GameType enumeration</a> | 

- Example 

```python 
gameType = self.GetPlayerGameType(playerId) 
``` 

## HasEntity 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description


Check if entity exists 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | 0 means does not exist, 1 means exists | 

- Example 

```python 
exist = self.HasEntity(entityId) 
``` 

## IsEntityAlive 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Determine whether a biological entity is alive or a non-biological entity exists 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | false means that the biological entity has died or the non-biological entity has been destroyed, true means that the biological entity is alive or the non-biological entity exists | 

- Remarks 
- Note that if the block where the detected entity is located is unloaded, the interface returns False. Therefore, it is necessary to pay attention to whether the block where the entity is located is loaded. 
- Block unloading: The game will only load blocks around the player. When the player moves to another area, the blocks in the original area will be unloaded. Please refer to [Block Introduction](https://minecraft-zh.gamepedia.com/%E5%8C%BA%E5%9D%97) 

- Example


```python 
alive = self.IsEntityAlive(entityId) 
``` 

## CreateGravityComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create gravity component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| GravityComponentServer | Gravity component instance | 

## GetEntityGravity 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the gravity factor of the entity. When the gravity factor of the creature is 0, the gravity factor of the world is applied 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| float | Gravity factor | 

- Example 

```python 
self.GetEntityGravity(entityId) 
``` 

## SetEntityGravity 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the gravity factor of the entity. When the gravity factor of the creature is 0, the gravity factor of the world is applied 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| gravity | float | Negative number, indicating the downward speed per frame | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SetEntityGravity(entityId, -0.08) 
``` 

## CreateHurtComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 


Create hurt component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| HurtCompServer | hurt component instance | 

## SetHurtByEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Causes damage to an entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 
| attackerId | str | entity id of the source of damage | 
| damage | int | damage value | 
| byPassArmor | bool | whether to ignore armor | 
| knocked | bool | whether the entity was knocked back, it can be missing, the default value is True when missing | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

## SetHurtByEntityNew 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 


- Description 

Causes damage to an entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| damage | int | Damage value | 
| cause | str | Damage source, see <a href="../../../1-ModAPI/Enumeration value/ActorDamageCause.html">ActorDamageCause enumeration</a> in the Minecraft enumeration value document for details | 
| attackerId | str | Entity id of the source of damage, default is None | 
| childAttackerId | str | Child entity id of the source of damage, default is None, for example, if the player uses a projectile to cause damage to the entity, the value should be the projectile id | 
| knocked | bool | Whether the entity was knocked back, the default value is True | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

## SetEntityImmuneDamage 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether the entity is immune to damage (this property is archived) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| immune | bool | Whether to be immune to damage | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetEntityImmuneDamage(entityId, True)

``` 

## CreateItemBannedComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create itembanned component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ItemBannedCompServer | itembanned component instance | 

## AddBannedItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Add banned items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemName | str | Item identifier, format [namespace:name:auxvalue], auxvalue defaults to 0, auxvalue is * when it matches any auxvalue value. For example: minecraft:egg (you can also start and disable by filling in the configuration file config/banned_items.json) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the addition is successful | 


- Example 

```python 
self.AddBannedItem("minecraft:egg") 
``` 

## GetBannedItemList 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get a list of banned items 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(str) or None | List of banned items or None (abnormal situation), list elements are item identifiers, format [namespace:name:auxvalue], auxvalue defaults to 0, auxvalue is * when it matches any auxvalue value. | 

## RemoveBannedItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Remove banned items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemName | str | Item identifier, format [namespace:name:auxvalue], auxvalue defaults to 0, auxvalue matches any auxvalue value when *. | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Whether the removal is successful | 

- Example 

```python 
self.RemoveBannedItem("minecraft:stained_glass:2") 
``` 

## ClearBannedItems 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Clear the disabled items 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the clearing is successful | 

## CreateItemComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create item component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ItemCompServer or ItemCompClient | Item component instance | 

## GetItemBasicInfo 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the basic information of the item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemName | str | Item identifier | 
| auxValue | int | Item additional value auxvalue, default is 0 | 
| isEnchanted | bool | Whether it is enchanted, default is False. idAux used for return | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Basic information dictionary, see notes | 

- Notes 
- The default value of auxValue is 0, which can be left unset. If the item does not exist, the return value is None 
| Keywords | Data Type | Description | 
| ----------| --------------------- | ---------| 
| itemName | str | Localized item name | 
| maxStackSize |int| Maximum number of stacks of items | 
| maxDurability |int| Maximum durability of items | 
| idAux |int| Mainly used for client UI binding, see client interface for details | 
| tierDict |dict| Mining-related properties defined by custom blocks netease:tier, returns None when not set | 
| itemCategory |str| Creation column category | 
| itemType |str| Item type | 
| itemTierLevel |int| Tool level | 
- The itemCategory value of a custom item is the category field value in the json file. The client reads the json file of the resource package, and the server reads the json file in the behavior package. The category fields in the two json files need to be consistent, otherwise an error will be reported 
- Description of the creation column categories 
| Creation column categories | Meaning | 
| --------- | -----| 
| construction | construction | 
| nature | nature | 
| equipment | equipment | 
| items | items |

| custom | Custom | 
| Empty string | Not in the creation column | 
- Item type, the value is an empty string or one of the following type names: 
| Type name | Meaning | 
| ----- | ----- | 
| book | Book | 
| sword | Sword | 
| shears | Scissors | 
| axe | Axe | 
| clock | Clock | 
| bucket | Bucket | 
| fishing_rod | Fishing rod | 
| hoe | Hoe | 
| shovel | Shovel | 
| pickaxe | Pickaxe | 
| dye | Bone meal | 
- Tool level represents different materials. If there is no tool level, the value is -1. The corresponding relationship between tool level and material is as follows 
| Tool level | Material | 
| ------- | ---- | 
| 0 | Wooden/gold tools | 
| 1 | Stone tools | 
| 2 | Iron tools | 
| 3 | Diamond Tool | 

- Example 

```python 
self.GetItemBasicInfo("minecraft:bow") 
``` 

## GetLocalPlayerId 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the local player's id 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| str | Client player ID | 

## ClearPlayerOffHand 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Clear the player's left hand items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str | Player ID | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.ClearPlayerOffHand(playerId) 
``` 

## GetPlayerItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get player items, support getting backpack, armor bar, off-hand and main-hand items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| posType | int | <a href="../../../1-ModAPI/Enumeration value/ItemPosType.html">ItemPosType enumeration</a> |

| slotPos | int | slot position, needs to be set when getting INVENTORY and ARMOR, write 0 in other cases | 
| getUserData | bool | whether to get userData, default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary" rel="noopenner">Item Information Dictionary</a>, return None if there is no item | 

- Example 

```python 
self.GetPlayerItem(playerId, self.GetMinecraftEnum().ItemPosType.INVENTORY, 0) 
``` 

## ChangePlayerItemTipsAndExtraId 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Modify the custom tips and custom identifiers of player items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| posType | int | <a href="../../../1-ModAPI/Enumeration value/ItemPosType.html">ItemPosType enumeration</a> | 
| slotPos | int | Box slot | 
| customTips | str | Custom tips for items | 
| extraId | str | Custom identifier for items | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.ChangePlayerItemTipsAndExtraId(playerId, self.GetMinecraftEnum().ItemPosType.INVENTORY, 0, "custom tips", "custom identifier") 
``` 




## AddEnchantToInvItem 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Add enchantment information to items in the inventory 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| slotPos | int | Inventory slot | 
| enchantType | int | Enchant type, you can view the enumeration value document | 
| level | int | Enchant level | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.AddEnchantToInvItem(playerId, 0, serverApi.GetMinecraftEnum().EnchantType.BowDamage, 2) 
``` 

## GetInvItemEnchantData 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the enchantment information of the item in the inventory 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| slotPos | int | Inventory slot |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(tuple(int,int)) | Each tuple in the list consists of an enchantment type (<a href="../../../1-ModAPI/Enumeration value/EnchantType.html">EnchantType enumeration</a>) and an enchantment level. Empty list if no enchantment | 

- Example 

```python 
self.GetInvItemEnchantData(playerId, 0) 
``` 

## GetOffhandItem 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the information of the left-hand item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player ID | 
| getUserData | bool | Whether to get the userData of the item, the default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary" rel="noopenner"> Item Information Dictionary </a>, returns None if there is no item | 

- Example 

```python 
offhandData = self.GetOffhandItem(entityId) 
``` 

## SetInvItemNum 

<span style="display:inline;color:#ff5555">Server</span> 


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the number of items in the player's backpack 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str | Player ID | 
| slotPos | int | Inventory slot | 
| num | int | Number of items. You can clear the backpack items by setting the number to 0 | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SetInvItemNum(playerId, 0, 10) 
``` 

## SpawnItemToLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Generates item drops. If you need to obtain the entityId of the item, you can call the server system interface CreateEngineItemEntity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary" rel="noopenner">Item Information Dictionary </a> | 
| dimensionId | int | Set dimension | 
| pos | tuple(float,float,float) | Generation location | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| bool | Set result | 

- Example 

```python 
itemDict = { 
'itemName': 'minecraft:bow', 
'count': 1, 
'enchantData': [(serverApi.GetMinecraftEnum().EnchantType.BowDamage, 1),], 
'auxValue': 0, 
'customTips':'§c new item §r', 
'extraId': 'abc', 
'userData': {}, 
} 
self.SpawnItemToLevel(itemDict, 0, (0,80,20)) 
# When the maximum number of items to be generated is 1, you can continue to call to generate 2 items 
self.SpawnItemToLevel(itemDict, 0, (0,80,20)) 
``` 

## SpawnItemToPlayerInv 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Generate items to the player's backpack 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary" rel="noopenner">Item Information Dictionary </a> | 
| playerId | str | Player id | 
| slotPos | int | Backpack slot (optional) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Notes 
- When slotPos is not set, when the set number exceeds the upper limit of a single slot stack, the excess items will be set to other free slots. If the generated items are the same as the items in the slots in the backpack, the interface will also add the items to these slots. Note: If the sum of the number of remaining items in the backpack and the number of added items is greater than 64, the number of generated items will be 64, but the interface returns failure. 

- Example 


```python
itemDict = {
    'itemName': 'minecraft:bow',
    'count': 1,
    'enchantData': [(self.GetMinecraftEnum().EnchantType.BowDamage, 1),],
    'auxValue': 0,
    'customTips':'§c new item §r',
    'extraId': 'abc',
    'userData': { },
}
self.SpawnItemToPlayerInv(itemDict, playerId, 0)
```



## SpawnItemToPlayerCarried

<span style="display:inline;color:#ff5555">Server</span>

method in Preset.Model.SdkInterface.SdkInterface

- describe

Generate items to the player's right hand 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemDict | dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary" rel="noopenner">Item Information Dictionary </a> | 
| playerId | str | Player id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
itemDict = { 
'itemName': 'minecraft:bow', 
    'count': 1,
    'enchantData': [(self.GetMinecraftEnum().EnchantType.BowDamage, 1),],
    'auxValue': 0,
    'customTips':'§c new item §r',
    'extraId': 'abc',
    'userData': { },
}

self.SpawnItemToPlayerCarried(itemDict, playerId) 
``` 

## GetCarriedItem 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the information of the right hand item 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| getUserData | bool | Whether to get the userData of the item, the default is False | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary" rel="noopenner">Item Information Dictionary</a>, returns None if there is no item | 

## GetSlotId 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the slot id of the currently held shortcut bar 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | 0 to 8 | 

- Example


```python 
slotId = self.GetSlotId() 
``` 

## GetItemFormattedHoverText 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the formatted hover text of the item, such as: §fDisaster Banner§r 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemName | str | Item identifier | 
| auxValue | int | Item additional value auxValue, default is no auxValue (0) | 
| showCategory | bool | Whether to include item category information, default is False | 
| userData | dict | Item userData, default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Formatted hover text of the item | 

- Example 

```python 
# Disaster Banner 
self.GetItemFormattedHoverText("minecraft:banner", 15, True, {'Type': 1}) 
``` 

## GetItemHoverName 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the hover name of the item, such as: Disaster Banner§r


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| itemName | str | Item identifier | 
| auxValue | int | Item additional value auxValue, default is no auxValue (0) | 
| userData | dict | Item userData, default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Item hover name | 

- Example 

```python 
# Disaster banner 
self.GetItemHoverName("minecraft:banner", 15, {'Type': 1}) 
``` 

## GetItemEffectName 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the item status description, such as: §7 protection 0§r 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| itemName | str | Item identifier | 
| auxValue | int | Item additional value auxValue, default is no auxValue (0) | 
| userData | dict | Item userData, default is None | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Item status description | 

- Example 


```python 
# Disaster Banner 
self.GetItemEffectName("minecraft:banner", 15, {'Type': 1}) 
``` 

## GetUserDataInEvent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Make the <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Item Information Dictionary" rel="noopenner">Item Information Dictionary</a> parameter of item-related client events have userData. Just call it when the mod is initialized 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| eventName | str | Engine event name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Success | 

- Example 

```python 
# After calling this, the itemDict parameter of the ActorAcquiredItemClientEvent event will have the userData field 
self.GetUserDataInEvent("ActorAcquiredItemClientEvent") 
``` 

## ChangeItemTexture 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Replace the texture of the item. After the modification, all items using the texture will be changed, and such items created subsequently will also be changed. It will also modify the display of the item on the UI interface, the display when holding it, and the display when dropping in the scene. 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| identifier | str | Item identifier, format [namespace:name:auxvalue], auxvalue defaults to 0 | 
| texturePath | str | Texture path | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the modification is successful (because of the use of delayed loading, the return success here does not mean that the texture path is correct. The wrong path will cause the texture to be lost and the display to be abnormal during rendering) | 

- Remarks 
- Because all items using this texture will be modified at the same time, be as cautious as possible when using it. It is not recommended to modify the original items. It is recommended to only modify items that use new textures defined by yourself. 
- Sequence frame texture items do not support dynamic texture modification 
- Some items have special logic and cannot be modified: boxes, flags, creature heads, shields, tridents, fishing rods 

- Example 

```python 
print(self.ChangeItemTexture("mytool:hatchet_1:0", "textures/items/hatchet_1")) 
``` 

## CreateLvComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create lv component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Player id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| LevelComponentServer | lv component instance | 

## GetPlayerLevel 


<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get player level 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str or int | Player id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Player level | 

- Example 

```python 
self.GetPlayerLevel(playerId) 
``` 

## AddPlayerLevel 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Modify player level 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str or int | Player id | 
| level | int | Player level, can be set to negative | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful |


- Example 

```python 
self.AddPlayerLevel(playerId, 2) 
``` 

## CreateMobSpawnComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a mobSpawn component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| MobSpawnComponentServer | mobSpawn component instance | 

## SpawnCustomModule 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set custom spawning 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| biomeType | int | <a href="../../../1-ModAPI/Enumeration value/BiomeType.html">BiomeType enumeration</a> | 
| change | int | <a href="../../../1-ModAPI/Enumeration value/Change.html">Change enumeration</a> | 
| entityType | int | <a href="../../../1-ModAPI/Enumeration Value/EntityType.html">EntityType enumeration</a> |

| probability | int | spawn weight [1, 10] | 
| minCount | int | minimum spawn count [0, 10] | 
| maxCount | int | maximum spawn count [0, 10] | 
| environment | int | 1: spawn on the surface; 2: spawn in water | 
| minBrightness | int | minimum light level when spawning the creature [1, 15], use the default value if not set | 
| maxBrightness | int | maximum light level when spawning the creature [1, 15], use the default value if not set | 
| minHeight | int | minimum altitude when spawning the creature [0, 256], use the default value if not set | 
| maxHeight | int | maximum altitude when spawning the creature [0, 256], use the default value if not set | 

- return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SpawnCustomModule(BiomeType.river,Change.Add,EntityType.Dolphin,10,1,10,2) 
``` 

## CreateModAttrComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create modAttr component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ModAttrComponentServer or ModAttrComponentClient | modAttr component instance | 

## SetEntityModAttr 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span>


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set attribute value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| paramName | str | Attribute name. It is recommended to prefix str with mod name to avoid conflicts between multiple mods | 
| paramValue | any | Attribute value, supports Python basic data | 

- Return value 

None 

- Remarks 
- Note: tuple and set will be converted to list during synchronization. It is recommended to use non-collection types such as numbers and strings. 

- Example 

```python 
self.SetEntityModAttr(entityId, 'health', 1) 
self.SetEntityModAttr(entityId, 'testDict', {'key':'value'}) 
``` 

## GetEntityModAttr 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get attribute value 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| paramName | str | Attribute name. It is recommended to prefix the name of str with the mod name to avoid conflicts between multiple mods. | 
| defaultValue | any | Attribute default value. This default value is returned when the attribute does not exist. In this case, the attribute value is still not set. | 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| any | Return attribute value | 

- Notes 
- DefaultValue is None by default when not passed 

- Example 

```python 
# If you modify the collection type obtained by GetAttr directly, you need to call SetAttr again to ensure that it is updated 
testDict = self.GetEntityModAttr(entityId, 'testDict') 
testDict['key'] = 'newValue' 
self.SetEntityModAttr(entityId, 'testDict', testDict) 
``` 

## RegisterEntityModAttrUpdateFunc 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Register a callback function for attribute value changes. This function will be called when the attribute changes. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| paramName | str | Attribute name to monitor | 
| func | function | Callback function to monitor | 

- Return value 

None 

- Notes 
- The callback function needs to accept a parameter, which is a dict. The specific data example is: {'oldValue': 0, 'newValue': 1, 'entityId': ’-433231231231‘} 

- Example 

```python 
# This entityId passes the ID of the object that needs to be monitored. 
self.RegisterEntityModAttrUpdateFunc(entityId, 'health', self.jumpingText) 
# When the health attribute of the script layer changes, self.jumpingText will be called.

def jumpingText(self, data): 
entityId = data['entityId'] 
oldValue = data['oldValue'] 
newValue = data['newValue'] 
``` 

## UnRegisterEntityModAttrUpdateFunc 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Callback function when unregistering attribute value change 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| paramName | str | Attribute name to be monitored | 
| func | function | Callback function to be monitored | 

- Return value 

None 

- Notes 
- Need to pass the same function as the parameter when registering 

- Example 

```python 
self.UnRegisterEntityModAttrUpdateFunc(entityId, 'health', self.jumpingText) 
``` 

## CreateModelComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create model component


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ModelComponentServer or ModelComponentClient | Model component instance | 

## SetEntityOpacity 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the transparency of the biological model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 
| opacity | float | transparency value, the range is [0, 1], the smaller the value, the more transparent | 

- Return value 

None 

- Example 

```python 
self.SetEntityOpacity(entityId, 0.2) 
``` 

## PlayEntityAnim 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 


- Description 

Play skeletal animation 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 
| aniName | str | Animation name | 
| isLoop | bool | Whether to play in a loop | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.PlayEntityAnim(entityId, "run", True) 
``` 

## GetEntityModelId 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the id of the skeleton model, mainly used for binding the skeleton model with special effects 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | The id of the current skeleton model instance | 

- Example 


```python 
modelId = self.GetEntityModelId(entityId) 
``` 

## SetEntityModel 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the skeleton model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| modelName | str | Model name, reset the model when the value is "" | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SetModel(entityId, "xuenv") 
``` 

## ResetEntityModel 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Restore the entity to the original model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.ResetModel(entityId) 
``` 

## BindModelToEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

After the entity replaces the skeleton model, other skeleton models are attached to it. 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| boneName | str | Attached bone name | 
| modelName | str | Attached bone model name | 
| offset | tuple(float,float,float) | Offset | 
| rot | tuple(float,float,float) | Rotation | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | The ID of the bone model attached to the bone, -1 if failed | 

- Example 

```python 
# Attach the bone model named gun to the rightHand bone 
gunModelId = self.BindModelToEntity(entityId, "rightHand", "gun")
```



## UnBindModelToEntity 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Unbind a skeletal model from an entity. After unhooking, the model of this modelId will be destroyed and can no longer be used. If it is temporarily hidden, you can use HideModel 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 
| modelId | int | The id of the skeleton model to be unhooked | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the unhooking is successful | 

## CreateMoveToComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create moveTo component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| MoveToComponentServer | moveTo component instance | 




## SetEntityMoveSetting 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Pathfinding component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| pos | tuple(float,float,float) | Pathfinding target position | 
| speed | float | Movement speed | 
| maxIteration | int | Maximum number of iterations of the pathfinding algorithm Default 200 | 
| callback | function | Pathfinding end callback function | 

- Return value 

None 

- Notes 
- When using this interface, you need to configure a pathfinding json component in the creature. After configuring the pathfinding json component, the interface will automatically select the corresponding type of pathfinding 
Currently supported pathfinding json components include: 
- minecraft:navigation.walk 
Land pathfinding, the same as the pathfinding of the original zombie 
- minecraft:navigation.generic 
Aquatic pathfinding, supports land and water, the same as the pathfinding of the original drowned corpse 
- minecraft:navigation.climb 
Land pathfinding, but supports climbing walls, the same as the pathfinding of the original spider. This kind of pathfinding may be blocked by overhead blocks and cannot reach the destination. 
- minecraft:navigation.fly 
Pathfinding in the air, the same as the pathfinding of the original parrot 
The above pathfinding needs to be used with some other json components (such as movement). For details, please refer to the example of NavigationMod 
The navigation types not mentioned above are not supported yet, such as minecraft:navigation.float (such as the original evil spirit), minecraft:navigation.hover (such as the original bee) 
- Different creatures have different default maximum follow distances. If the distance to the target point to be pathfinded is greater than this value, the engine will refuse to pathfind. To modify the distance, you can configure it in the entity's json. 
```json 
{ 
"format_version": "1.8.0", 
"minecraft:entity": { 
"components": { 
"minecraft:follow_range": { 
"value": 48, 
"max": 48 
} 
} 
}

} 
``` 
- About the maxIteration parameter 
This parameter affects the length of the actual path found. If the pathfinding algorithm fails to find the target point after a certain number of iterations, it will return to the local optimal solution, that is, the creature will only go halfway. 

In the absence of large obstacles, the reference pathfinding distance corresponding to the parameter is as follows: The default value of this parameter is 200 and the maximum value is 2000. Please choose according to the actual situation. 
| maxIteration | Straight-line distance from the target point | 
| ------------ | ---------------- | 
| 200 | 13 | 
| 500 | 20 | 
| 1000 | 30 | 
| 2000 | 43 | 
- About callback function 
This function needs to accept two parameters, the first parameter is the pathfinding entityId, type str, the second parameter is the pathfinding result, type int 

(The position obtained by the player will be 1.62 grids higher than the ground. If the player's position is used as the target point, the y axis needs to be subtracted by 1.62 first, otherwise the callback will always return 1) 
| Result | Description | 
| ---- | ------------------------------------------------------------ | 
| -3 | Pathfinding failed, greater than the follow distance, or used for a flying creature that is pathfinding | 
| -2 | Pathfinding failed, the creature has no pathfinding component (referring to minecraft:navigation) | 
| -1 | Pathfinding failed, parameter error, or creature does not exist | 
| 0 | Pathfinding completed. Reached the set target point | 
| 1 | Pathfinding completed, but did not reach the target point (maybe due to the small maxIteration parameter) | 
| 2 | Pathfinding interrupted. Obstacle encountered midway | 
| 3 | Pathfinding interrupted. Overwritten by the creature's original pathfinding behavior, or repeatedly calling the moveTo component before the pathfinding is completed | 
- Demo introduction: 
Entering walk/generic/climb/fly in the chat bar will generate a creature using the corresponding navigation json component on the spot, then run to another location, and then enter go, which will navigate the creature just generated to the player's current location. 
The behavior json of these 4 sample creatures can be viewed in the NavigationMod_behavior/entities directory. 
The maximum pathfinding distance of the 4 sample creatures is set to 48 grids. 

- Example

```python
def myCallback(entityId, result):
    if result in (-1,-2,-3):
        self.LogError('[SetMoveSetting] failed')
    elif result==0:
        self.LogInfo('[SetMoveSetting] success')
    elif result in (1,2,3):
        self.LogError('[SetMoveSetting] terminated')

self.SetMoveSetting(entityId, (x,y,z),2.0,200,myCallback)
```



## CreateMsgComponent

<span style="display:inline;color:#ff5555">Server</span>

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create msg component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| MsgComponentServer | msg component instance | 

## SendMsg 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Simulates a player sending a chat message to everyone 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| name | str | Sender player's name | 
| msg | str | Message content | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Setting result | 

- Remarks 
- The name parameter needs to set the player's name (which can be obtained through the name component). If the set player name does not exist, a random player will be found to send the message 

- Example 

```python 
self.SendMsg("playerName","test")

``` 

## SendMsgToPlayer 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Simulate a player sending a chat message to another player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| fromEntityId | str | Sender player ID | 
| toEntityId | str | Receiver player ID | 
| msg | str | Message content | 

- Return value 

None 

- Example 

```python 
self.SendMsgToPlayer(fromEntityId, toEntityId, "test") 
``` 

## NotifyOneMessage 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Send a chat box message to the specified player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Specified player id | 
| msg | str | Message content |

| color | str | Color style code string, refer to wiki [style code] (https://minecraft-zh.gamepedia.com/%E6%A0%B7%E5%BC%8F%E4%BB%A3%E7%A0%81), default is white | 

- Return value 

None 

- Example 

```python 
self.NotifyOneMessage(playerId, "test", "§c") 
``` 

## CreateNameComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create name component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| NameComponentServer or NameComponentClient | name component instance | 

## GetEntityName 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the custom name of the creature, that is, the name set by the name tag or SetName interface 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| str | Custom name of the creature | 

- Example 

```python 
name = self.GetEntityName(entityId) 
``` 

## SetEntityName 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Used to set the custom name of the creature, the same as the original name tag, players and new version of wandering traders are not supported 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| name | str | Name | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Example 

```python 
self.SetEntityName(entityId, "new Name") 
``` 

## SetPlayerPrefixAndSuffixName


<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the player prefix and suffix name 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Player id | 
| prefix | str | Prefix content | 
| prefixColor | str | Prefix content color description, you can use GenerateColor interface to pass in parameters | 
| suffix | str | Suffix content | 
| suffixColor | str | Suffix content color description, you can use GenerateColor interface to pass in parameters | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
color = self.GetMinecraftEnum().ColorCode.RED 
self.SetPlayerPrefixAndSuffixName(playerId, "Red Team", color, 'Tough Shield', color) 
``` 

## SetEntityShowName 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether the creature name is displayed according to the default game logic 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| show | bool | True for display |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Notes 
- When set to True, the name display of the creature follows the default rendering logic of the game, that is, the name of the ordinary creature needs to be pointed at the center point of the creature to display the name, while the name of the player will always be displayed 

- Example 

```python 
# Do not display the name above the head 
self.SetEntityShowName(entityId, False) 
``` 

## SetEntityAlwaysShowName 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether the creature name is always displayed, and it can be displayed even when the aiming point is not pointing at the creature 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| show | bool | True for display | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Returns whether the setting is successful | 

- Notes 
- This interface is only valid for ordinary creatures and has no effect on player settings 

- Example 

```python 
# Do not display the name above the head 
self.SetEntityAlwaysShowName(entityId, False)

``` 

## CreatePersistenceComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create persistence component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PersistenceCompServer | persistence component instance | 

## SetEntityPersistence 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether the entity is saved to disk 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| isPersistent | bool | True means save to disk, False means not save to disk | 

- Return value 

None 

- Notes

- Entities are saved by default. Entities set to not save will not be saved when the chunk is unloaded or when exiting the game. 

- Example 

```python 
self.SetEntityPersistence(entityId, True) 
``` 

## CreatePetComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create pet component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PetComponentServer | pet component instance | 

## DisablePet 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Disable the official partner function. Single-player games and local online games do not support this interface 

- Parameters 

None 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Disable result | 

## EnablePet 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Enable the official partner function. Single-player games and local online games do not support this interface 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Enable result | 

## CreatePlayerComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create player component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PlayerCompServer | player component instance | 




## EnablePlayerKeepInventory 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the player to not drop items when dying 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str or int | Entity id | 
| enable | bool | Whether to enable "keep inventory" | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.EnablePlayerKeepInventory(playerId, True) 
``` 

## CreatePortalComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create portal component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value


    | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PortalComponentServer | portal component instance | 

## CreatePosComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create pos component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PosComponentServer or PosComponentClient | pos component instance | 

## GetEntityPos 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get entity position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| tuple(float,float,float) | Position information | 

- Notes 
- For non-players, the position of the sole of the foot is obtained 
- For players, if they are walking, standing, swimming, sneaking, or gliding, the position obtained is 1.62 higher than the sole of the foot; if they are sleeping, the position obtained is 0.2 higher than the lowest position 

## GetEntityFootPos 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the position of the entity's foot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Position information | 

## SetEntityPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set entity position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 
| pos | tuple(int,int,int) | xyz value |

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

- Notes 
- The behavior is the same as using the tp command, the entity will teleport to the target point 
- For all types of entities, the foot position is set, which is equivalent to [SetFootPos](#setfootpos) 
- Calling this interface in bed will return False 

- Example 

```python 
self.SetEntityPos(entityId, (1,2,3)) 
``` 

## SetEntityFootPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the position of the entity's foot 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| pos | tuple(float,float,float) | Entity foot position | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- The behavior is consistent with using the tp command, the entity will teleport to the target point 
- Calling this interface while on the bed will return False 

- Example 

```python 
self.SetEntityFootPos(entityId, (0, 4, 0))

``` 

## CreateProjectileComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a projectile component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ProjectileComponentServer | Projectile component instance | 

## CreateProjectileEntity 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a projectile (direct launch) 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| spawnerId | str | Creator Id | 
| entityIdentifier | str | Category of the created projectile, such as minecraft:snowball | 
| param | dict | Default is None, see the notes for detailed description | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| str | Id of the created projectile, "-1" if failed | 

- Notes 
- The param parameter is explained as follows: 
| Parameter | Type | Explanation | 
| ----------------- | ----- | ------------------------------------------------------------ | 
| position | tuple(float,float,float) | Initial position | 
| direction | tuple(float,float,float) | Initial direction | 
| power | float | Throwing power value | 
| gravity | float | Projectile gravity factor, defaults to the value in the json configuration | 
| damage | float | Projectile damage value, defaults to the value in the json configuration | 
| targetId | str | Projectile target (after specifying the target, it will have the same effect as the projectile of the tracking missile launched by the shulk), not specified by default | 
| isDamageOwner | bool | Whether to cause damage to the creator, no damage by default | 

- Example 

```python 
param = { 
'position': (1,1,1), 
'direction': (1,1,1) 
} 
self.CreateProjectileEntity(playerId, "minecraft:snowball", param) 
``` 

## CreateRecipeComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a recipe component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| RecipeCompServer or RecipeCompClient | recipe component instance | 



## GetRecipeResult 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the recipe result based on the recipe id. Only supports synthesis recipes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| recipeId | str | Recipe id, corresponding to the identifier field in the recipe json file | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(dict) | See the notes for the resultDict dictionary of the list elements | 

- Notes 
- The resultDict dictionary content is as follows 
| Keywords | Data type | Description | 
| ----------| --------------------- | ---------| 
| itemName | str | Item name id | 
|auxValue| int | Item additional value | 
|num| int | Item number | 

- Example 

```python 
self.GetRecipeResult(recipe1) 
``` 

## GetRecipesByResult 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Query the input materials required for the recipe through the output items 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| resultIdentifier | str | Output item identifier | 
| tag | str | Corresponding value in the tags field in the recipe json | 
| aux | int | Additional value of the output item. If no parameter is passed, the default value is 0 | 
| maxResultNum | int | Maximum number of output items. If it is greater than or equal to 0, and the result exceeds maxResultNum, only maxResultNum items will be returned. Default is -1, indicating to return all | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(dict) | Returns a list of recipes that meet the conditions | 

- Notes 
- When obtaining brewing stand recipes, the tag label and aux value are not matched. The identifier of the potion needs to be entered in full, for example: minecraft:potion_type:long_turtle_master, otherwise the correct recipe cannot be obtained. 

- Example 

```python 
print(self.GetRecipesByResult("minecraft:boat", "crafting_table", 4, -1)) 
``` 

## GetRecipesByInput 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Query recipes by inputting items 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| inputIdentifier | str | Identifier of the input item | 
| tag | str | The value in the tags field in the corresponding recipe json | 
| aux | int | Output item's additional value, defaults to 0 if no parameter is passed | 
| maxResultNum | int | Maximum number of output items, if greater than or equal to 0, and the result exceeds maxResultNum, only maxResultNum items will be returned. Default is -1, indicating that all items will be returned | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| list(dict) | Returns a list of recipes that meet the criteria | 

- Notes

- When getting the brewing stand recipe, the tag and aux values do not match. The potion identifier needs to be entered in full, for example: minecraft:potion_type:long_turtle_master, otherwise the correct recipe cannot be obtained. 
- Need to traverse more data, do not recommend frequent calls 

- Example 

```python 
print(self.GetRecipesByInput("minecraft:log", "crafting_table", 0, -1)) 
``` 

## CreateRedStoneComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create redStone component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| RedStoneComponentServer | redStone component instance | 

## CreateRideComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a ride component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| RideCompServer | Ride component instance | 

## CreateRotComponent 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create rot component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| RotComponentServer or RotComponentClient | rot component instance | 

## GetEntityRot 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the entity angle 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | (up and down angle, left and right angle) The unit is angle instead of radian | 

## SetEntityRot 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the angle of the entity's head 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| rot | tuple(float,float) | Pitch angle and angle around vertical direction, unit is degree | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- It is recommended to only use it to set local players. If other creatures are set, they will be overwritten by the creature's own behavior. 

- Example 

```python 
# Set to look up 45 degrees and face the positive direction of the world z axis 
self.SetEntityRot(entityId, (-45, 0)) 
``` 

## SetEntityLookAtPos 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 


Set non-player entities to look at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| targetPos | tuple(float,float,float) | Target position to look at | 
| minTime | float | Minimum duration of gaze behavior, in seconds | 
| maxTime | float | Maximum duration of gaze behavior, in seconds, with a maximum value of 60<br>The actual duration of the behavior will be a random value between minTime and maxTime | 
| reject | bool | Whether to prohibit triggering other behaviors when performing gaze behavior<br>True prohibits other behaviors<br>False allows other behaviors (at this time, the gaze behavior may not be obvious) | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful, True for success, False for failure | 

- Notes 
- Calling this interface will interrupt the ongoing behavior of the creature, and the creature will not look at the target position immediately, but will gradually look at the target position 
- Calling this interface for some entities that will not turn may return failure or success but no actual performance 

- Example 

```python 
# Set the entity to look at the position (0,78,0). The gaze behavior lasts for at least 2 seconds and at most 3 seconds. Other behaviors are prohibited during the gaze process 
self.SetEntityLookAtPos(entityId, (0,78,0), 2, 3, True) 
``` 

## GetBodyRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the angle of the entity's body 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| float | The angle of the body around the vertical direction, in degrees. If there is no body, it returns 0 | 

- Example 

```python 
y = self.GetBodyRot(entityId) 
``` 

## LockLocalPlayerRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

When separating the camera, lock the head angle of the local player 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| lock | bool | Pass True to lock the local player's head angle<br> Pass False to unlock the local player's head angle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: Setting successful<br>False: Setting failed | 

- Notes 
- Only localplayer can be set 
- The head angle will be reset when the player respawns or switches dimensions 
- When the local player's head angle is locked, the camera can be rotated in the first-person perspective, but the player's head angle will not change. The next time you switch to the first-person perspective, the camera angle will still be the locked angle 
- After locking the local player's head angle, the player's head angle will try to get close to the locked angle when rowing. If it cannot turn to that angle, it will look left or right (depending on which side is closer to the target angle) 

- Example 

```python 
# Detach camera 
self.DepartCamera() 
# Lock the local player's head angle 
self.LockLocalPlayerRot(True) 
``` 



## SetPlayerLookAtPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the local player to look at a certain position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| targetPos | tuple(float,float,float) | Target position to look at | 
| pitchStep | float | Angular velocity of rotation in pitch direction (per frame), minimum 0.2 | 
| yawStep | float | Angular velocity of rotation in yaw direction (per frame), minimum 0.2 | 
| blockInput | bool | Whether to block player operations when turning to the target angle, the default is True<br>True: Block player operations, the player cannot turn or move<br>False: Do not block player operations, if the player moves or the camera turns, the turn set by this interface will be interrupted | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful, True is successful, False is failed | 

- Notes 
- When the local player is not separated from the camera, calling this interface will cause the camera to look at the specified position together<br>When the local player is separated from the camera, calling this interface will only change the direction of the local player model 

- Example 

```python 
# Set the local player to look at the position (0,78,0) at a pitch rate of 0.2 degrees per frame and a yaw rate of 1 degree per frame, and shield the player's operation during the turning process 
self.SetPlayerLookAtPos((0,78,0), 0.2, 1, True) 
``` 

## CreateScaleComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a scale component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ScaleComponentServer | scale component instance | 

## CreateTameComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create tame component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TameComponentServer | Tame component instance | 

## CreateTimeComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create time component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TimeComponentServer | time component instance | 

## GetTime 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the current world time 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | Current time, in frames, indicating the time since the archive was created, not the time in the current game day. One game day in mc is equivalent to 20 minutes in reality, that is, 24,000 frames | 

- Example 

```python 
# Total number of frames since the start of the game 
passedTime = self.GetTime() 
# Number of frames in the current game day 
timeOfDay = passedTime % 24000 
# Number of game days since the start of the game 
day = passedTime / 24000 
``` 

## CreateWeatherComponent 

<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 


Create weather component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| WeatherComponentServer | Weather component instance | 

## CreateActorCollidableComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create actorCollidable component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ActorCollidableCompClient | actorCollidable component instance | 

## CreateActorRenderComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create actorRender component 


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ActorRenderCompClient | actorRender component instance | 

## CreateCustomAudioComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a customAudio component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| AudioCustomComponentClient | customAudio component instance | 

## CreateBrightnessComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create brightness component 

- Parameters 


| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| BrightnessCompClient | brightness component instance | 

## SetEntityBrightness 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the brightness of the entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 
| brightness | float | 0: pure black<br>1: normal brightness<br>1-14: brighter or even pure white<br>More than 14: usually pure white, no obvious change even if the value changes | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | True: setting successful False: setting failed | 

- Notes 
- Currently only supports modifying the brightness of entities that have replaced the skeleton model, and entities using the game's native model are not supported. 

- Example 

```python 
success = self.SetEntityBrightness(entityId, 0.5) 
``` 

## CreateCameraComponent 

<span style="display:inline;color:#7575f9">Client</span> 


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a camera component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| CameraComponentClient | Camera component instance | 

## PickFacing 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the entity or block selected by the crosshair 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| dict | Data of the selected target, see the notes for details | 

- Notes 
- When the selected target is an entity, the return value is: 
```python 
{ 
"type": "Entity", 
"entityId": entityId 
} 
``` 
- When the selected target is a block, the return value is: 
```python

{ 
"type": "Block", 
"x": x, 
"y": y, 
"z": z, 
"face": face 
} 
``` 
- When no target is selected, the return value is: 
```python 
{ 
"type": "None" 
} 
``` 

- Example 

```python 
pickData = self.PickFacing() 
``` 

## CreateFogComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create fog component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| FogCompClient | fog component instance | 

## CreateFrameAniControlComponent 

<span style="display:inline;color:#7575f9">Client</span>


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a frameAniControl component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| frameEntityId | str or int | Sequence frame entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| FrameAniControlComp | frameAniControl component instance | 

## SetFrameAniLoop 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether the sequence frame is played in a loop, the default is no 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| frameEntityId | str or int | Sequence frame entity id | 
| loop | bool | True means loop playback | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# Set to loop playback 
self.SetFrameAniLoop(frameEntityId, True) 
```



## SetFrameAniFaceCamera 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Sets whether the sequence frame is always facing the camera, the default is yes 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| frameEntityId | str or int | Sequence frame entity id | 
| face | bool | True means facing the camera | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# Set to not always face the camera 
self.SetFaceCamera(frameEntityId, False) 
``` 

## SetFrameAniDeepTest 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether the sequence frame is perspective, the default is no 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| frameEntityId | str or int | Sequence frame entity id |

| deepTest | bool | False means perspective, so the sequence frame can still be seen when blocked by objects/blocks | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
# Set to perspective 
self.SetDeepTest(frameEntityId, False) 
``` 

## CreateFrameAniEntityBindComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create frameAniEntityBind component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| FrameAniEntityBindComp | frameAniEntityBind component instance | 

## BindFrameAniToEntity 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Bind entity


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| frameEntityId | int | ID of the sequence frame entity | 
| bindEntityId | str | ID of the bound entity | 
| offset | tuple(float,float,float) | Binding offset | 
| rot | tuple(float,float,float) | Binding rotation angle | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.BindFrameAniToEntity(frameEntityId, entityId, (0, 1, 0), (0, 0, 0)) 
``` 

## CreateFrameAniSkeletonBindComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create frameAniSkeletonBind component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| FrameAniSkeletonBindComp | frameAniSkeletonBind component instance | 

## BindFrameAniToSkeleton 


<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Bind bone model 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| frameEntityId | int | ID of the sequence frame entity | 
| modelId | int | ID of the bound bone model (see GetModelId of the model component) | 
| boneName | str | Name of the specific bone to be bound | 
| offset | tuple(float,float,float) | Binding offset | 
| rot | tuple(float,float,float) | bound rotation angle | 

- return value 

| <div style="width: 4em">data type</div> | description | 
| :--- | :--- | 
| bool | whether the setting is successful | 

- example 

```python 
self.BindFrameAniToSkeleton(frameEntityId, modelId, "root", (0, 1, 0), (0, 0, 0)) 
``` 

## CreateFrameAniTransComponent 

<span style="display:inline;color:#7575f9">client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- description 

create frameAniTrans component 

- parameters 

| parameter name | <div style="width: 4em">data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 


| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| FrameAniTransComp | frameAniTrans component instance | 

## GetFrameAniPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get sequence frame position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Position information | 

## GetFrameAniRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the angle of the sequence frame 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- |

| tuple(float,float) | (upper and lower angles, left and right angles) units are degrees instead of radians | 

## GetFrameAniScale 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the scaling of the sequence frame 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | For planar sequence frames, the first parameter is the horizontal scale of the texture, the second parameter is the vertical scale, and the third parameter is useless. For circular sequence frames, it is the scaling on three coordinate axes | 

## SetFrameAniPos 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the sequence frame position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 
| pos | tuple(int,int,int) | xyz value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result |



## SetFrameAniRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the angle of the special effect 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 
| rot | tuple(float,float) | Pitch angle and angle around the vertical direction, the unit is degree | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

## SetFrameAniScale 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the scaling of the sequence frame 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| scale | tuple(float,float,float) | For a flat sequence frame, the first parameter is the horizontal scaling of the texture, the second parameter is the vertical scaling, and the third parameter is useless. For a circular sequence frame, it is the scaling on the three coordinate axes | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful |


- Example 

```python 
# Horizontally stretch to 2 times, vertically unchanged 
self.SetFrameAniScale(frameEntityId, (2, 1, 1)) 
``` 

## CreateHealthComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create health component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| HealthComponentClient | health component instance | 

## ShowEntityHealth 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set whether to display the health bar of an entity. The default is to display 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| show | bool | Set whether to display |


- Return value 

None 

- Notes 
- ShowHealthBar must be set first 

- Example 

```python 
# Set the entity not to display the health bar 
self.ShowHealth(entityId, False) 
``` 

## CreateOperationComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create an operation component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| OperationCompClient | operation component instance | 

## SetCanAll 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set SetCanMove, SetCanJump, SetCanAttack, SetCanWalkMode, SetCanPerspective, SetCanPause, SetCanChat, SetCanScreenShot, SetCanOpenInv, SetCanDrag, SetCanInair at the same time


- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| flag | bool | True means all responses | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Notes 
- Set before setting other properties, otherwise the settings before all will be overwritten 

- Example 

```python 
# Set all to non-response 
self.SetCanAll(False) 
``` 

## CreateDeviceComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create device component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| DeviceCompClient | device component instance | 

## CreateParticleControlComponent


<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create particleControl component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ParticleControlComp | particleControl component instance | 

## CreateParticleEntityBindComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create particleEntityBind component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ParticleEntityBindComp | particleEntityBind component instance | 

## BindParticleToEntity 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span>


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Particle effect binding entity 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| particleId | int | Effect ID | 
| bindEntityId | str | ID of the bound entity | 
| offset | tuple(float,float,float) | Binding offset, relative to the center of the bound entity's feet | 
| rot | tuple(float,float,float) | Binding rotation angle | 
| correction | bool | Not enabled by default, enabling it allows the rotation angle of the effect to be accurately set to the relative angle of the reference player | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set whether it is successful | 

- Example 

```python 
self.BindParticleToEntity(particleId, entityId, (0, 1, 0), (0, 0, 0)) 
``` 

## CreateParticleSkeletonBindComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create particleSkeletonBind component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | 
| ParticleSkeletonBindComp | particleSkeletonBind component instance | 

## BindParticleToSkeleton 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Bind particle effects to skeleton models 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| particleId | int | Effect ID | 
| modelId | int | ID of the bound skeleton model (see GetModelId of the model component) | 
| boneName | str | Name of the specific bone to bind | 
| offset | tuple(float,float,float) | Offset of binding | 
| rot | tuple(float,float,float) | Rotation angle of binding | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.BindParticleToEntity(particleId, modelId, "root", (0, 1, 0), (0, 0, 0)) 
``` 

## CreateParticleTransComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create a particleTrans component 

- Parameters


    | Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ParticleTransComp | particleTrans component instance | 

## GetParticlePos 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the special effect position 

- Parameter 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float,float) | Location information | 

## GetParticleRot 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get special effect angle 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description |

| :--- | :--- | :--- | 
| entityId | str or int | entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| tuple(float,float) | (upper and lower angles, left and right angles) units are degrees instead of radians | 

## SetParticlePos 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the special effect position 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| entityId | str or int | Entity id | 
| pos | tuple(int,int,int) | xyz value | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Set result | 

## SetParticleRot 

<span style="display:inline;color:#7575f9">Client</span>/<span style="display:inline;color:#ff5555">Server</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the angle of the special effect 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- |

| entityId | str or int | entity id | 
| rot | tuple(float,float) | pitch angle and angle around vertical direction, unit is degree | 

- return value 

| <div style="width: 4em">data type</div> | description | 
| :--- | :--- | 
| bool | whether the setting is successful | 

## CreatePlayerViewComponent 

<span style="display:inline;color:#7575f9">client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- description 

create playerView component 

- parameters 

| parameter name | <div style="width: 4em">data type</div> | description | 
| :--- | :--- | :--- | 
| playerId | str or int | player id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PlayerViewCompClient | playerView component instance | 

## GetPlayerPerspective 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Get the current perspective mode 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Entity id |


- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| int | 0: first-person perspective; 1: third-person perspective; 2: front-view third-person perspective | 

- Example 

```python 
persp = self.GetPlayerPerspective(playerId) 
``` 

## SetPlayerPerspective 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Set the perspective mode 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str or int | Entity id | 
| persp | int | 0: first-person perspective; 1: third-person perspective; 2: front-view third-person perspective | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the setting is successful | 

- Example 

```python 
self.SetPlayerPerspective(playerId, 1) 
``` 

## LockPlayerPerspective 

<span style="display:inline;color:#7575f9">Client</span> 


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Lock the player's perspective mode 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| playerId | str or int | Entity id | 
| persp | int | 0: first-person perspective; 1: third-person perspective; 2: front-view third-person perspective Other values: unlock | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| bool | Whether the lock is successful | 

- Example 

```python 
self.LockPlayerPerspective(playerId, 1) 
``` 

## CreateQueryVariableComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create queryVariable component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| QueryVariableComponentClient | queryVariable component instance | 




## CreateSkyRenderComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create skyRender component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| SkyRenderCompClient | skyRender component instance | 

## CreateTextBoardComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create textBoard component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TextBoardComponentClient | textBoard component instance | 

## CreateTextNotifyClientComponent


<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create textNotifyClient component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| entityId | str or int | Entity id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| TextNotifyComponet | textNotifyClient component instance | 

## CreateConfigClientComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Create config component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| levelId | str | Archive Id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| ConfigCompClient | config component instance | 

## CreateVirtualWorldComponent 

<span style="display:inline;color:#7575f9">Client</span>


method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Creates a virtualWorld component instance component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| levelId | str | Archive Id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| VirtualWorldCompClient | virtualWorld component instance | 

## CreatePlayerAnimComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface 

- Description 

Creates a player animation component 

- Parameters 

| Parameter name | <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | :--- | 
| playerId | str | Player Id | 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PlayerAnimCompClient | Player animation component instance | 

## CreatePostProcessComponent 

<span style="display:inline;color:#7575f9">Client</span> 

method in Preset.Model.SdkInterface.SdkInterface


- Description 

Create a PostProcess component 

- Parameters 

None 

- Return value 

| <div style="width: 4em">Data type</div> | Description | 
| :--- | :--- | 
| PostProcessComponent | Post-processing effect component instance | 

