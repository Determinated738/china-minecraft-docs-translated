--- 
sidebarDepth: 1 
--- 
# Index 

Including the interface of entity attributes and behaviors. For the acquisition, generation and destruction of entities, see [World/Entity Management](../World/Index.md#Entity Management) 

--- 

- [Entity Type](#Entity Type) 
- [Added Value](#Added Value) 
- [Attribute](#Attribute) 
- [Behavior](#Behavior) 
- [Status Effect](#Status Effect) 
- [Rendering](#Rendering) 
- [Backpack](#Backpack) 
- [Custom Attribute](#Custom Attribute) 
- [Custom Data](#Custom Data) 
- [molang](#molang) 
- [Projectile](#Projectile) 
- [Experience Ball](#Experience Ball) 
- [Official Partner](#Official Partner) 
- [Tag](#Tag) 

### Entity Type 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetEngineType](EntityType.md#getenginetype) | <span style="display:inline;color:#ff5555">Server</span> | Get the entity type, mainly used to determine whether the entity belongs to a certain type of creature. | 
| [GetEngineType](EntityType.md#getenginetype) | <span style="display:inline;color:#7575f9">Client</span> | Get the entity type, mainly used to determine whether the entity belongs to a certain type of creature. | 
| [GetEngineTypeStr](EntityType.md#getenginetypestr) | <span style="display:inline;color:#ff5555">Server</span> | Get the entity's type name | 
| [GetEngineTypeStr](EntityType.md#getenginetypestr) | <span style="display:inline;color:#7575f9">Client</span> | Get the entity's type name | 

### Additional Value 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetAuxValue](Additional Value.md#getauxvalue) | <span style="display:inline;color:#ff5555">Server</span> | Get the additional value of the arrow shot or the potion thrown | 
| [GetAuxValue](Additional Value.md#getauxvalue) | <span style="display:inline;color:#7575f9">Client</span> | Get the additional value of the arrow shot or the potion thrown | 

### Attributes 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [ChangeEntityDimension](attribute.md#changeentitydimension) | <span style="display:inline;color:#ff5555">Server</span> | Transfer entity | 
| [GetAttrMaxValue](attribute.md#getattrmaxvalue) | <span style="display:inline;color:#ff5555">Server</span> | Get the maximum value of the engine attribute of the entity | 
| [GetAttrMaxValue](attribute.md#getattrmaxvalue) | <span style="display:inline;color:#7575f9">Client</span> | Get the maximum value of attributes, including health, hunger, speed, etc. | 
| [GetAttrValue](attribute.md#getattrvalue) | <span style="display:inline;color:#ff5555">Server</span> | Get the engine attributes of the entity | 
| [GetAttrValue](attribute.md#getattrvalue) | <span style="display:inline;color:#7575f9">Client</span> | Get attribute values, including health, hunger, speed | 
| [GetBodyRot](attribute.md#getbodyrot) | <span style="display:inline;color:#7575f9">Client</span> | Get the angle of the entity's body |

| [GetCurrentAirSupply](attribute.md#getcurrentairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Current oxygen reserve value of organisms | 
| [GetEntityDimensionId](attribute.md#getentitydimensionid) | <span style="display:inline;color:#ff5555">Server</span> | Get the dimension where the entity is located | 
| [GetEntityOwner](attribute.md#getentityowner) | <span style="display:inline;color:#ff5555">Server</span> | Get the owner of the entity | 
| [GetFootPos](attribute.md#getfootpos) | <span style="display:inline;color:#ff5555">Server</span> | Get the position of the entity's feet | 
| [GetFootPos](attribute.md#getfootpos) | <span style="display:inline;color:#7575f9">Client</span> | Get the position of the entity's feet | 
| [GetGravity](attribute.md#getgravity) | <span style="display:inline;color:#ff5555">Server</span> | Get the entity's gravity factor. When the creature's gravity factor is 0, the world's gravity factor is applied | 
| [GetMaxAirSupply](attribute.md#getmaxairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Get the creature's maximum oxygen reserve value | 
| [GetName](attribute.md#getname) | <span style="display:inline;color:#ff5555">Server</span> | Get the creature's custom name, that is, the name set using a name tag or the SetName interface | 
| [GetPos](attribute.md#getpos) | <span style="display:inline;color:#ff5555">Server</span> | Get entity position | 
| [GetPos](attribute.md#getpos) | <span style="display:inline;color:#7575f9">Client</span> | Get entity position | 
| [GetRot](attribute.md#getrot) | <span style="display:inline;color:#ff5555">Server</span> | Get the pitch angle of the entity head and the horizontal direction and the rotation angle of the vertical direction. After obtaining the angle, the GetDirFromRot interface can be used to convert it into a unit vector of the direction <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/10-Vector3.html">MC Coordinate System Description</a> | 
| [GetRot](attribute.md#getrot) | <span style="display:inline;color:#7575f9">Client</span> | Get the pitch angle of the entity head and the horizontal direction and the rotation angle of the vertical direction. After obtaining the angle, you can use the GetDirFromRot interface to convert it into a unit vector of the direction <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/10-Vector3.html">MC Coordinate System Description</a> | 
| [GetSize](attribute.md#getsize) | <span style="display:inline;color:#ff5555">Server</span> | Get the bounding box of the entity | 
| [GetTypeFamily](attribute.md#gettypefamily) | <span style="display:inline;color:#ff5555">Server</span> | Get the biological behavior package field type_family | 
| [GetUnitBubbleAirSupply](property.md#getunitbubbleairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Oxygen reserve value corresponding to the number of bubbles per unit | 
| [IsConsumingAirSupply](property.md#isconsumingairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the creature is currently consuming oxygen | 
| [LockLocalPlayerRot](property.md#locklocalplayerrot) | <span style="display:inline;color:#7575f9">Client</span> | When separating the camera, lock the head angle of the local player | 
| [SetAttrMaxValue](property.md#setattrmaxvalue) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum value of the entity's engine attribute | 
| [SetAttrValue](attribute.md#setattrvalue) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity's engine attribute | 
| [SetCurrentAirSupply](attribute.md#setcurrentairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Set the oxygen reserve value of the organism | 
| [SetEntityLookAtPos](attribute.md#setentitylookatpos) | <span style="display:inline;color:#ff5555">Server</span> | Set the non-player entity to look at a certain position | 
| [SetEntityOwner](attribute.md#setentityowner) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity's owner | 
| [SetFootPos](attribute.md#setfootpos) | <span style="display:inline;color:#ff5555">Server</span> | Set the position of the entity's feet | 
| [SetGravity](attribute.md#setgravity) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity's gravity factor. When the creature's gravity factor is 0, the world's gravity factor is applied | 
| [SetMaxAirSupply](attribute.md#setmaxairsupply) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum oxygen reserve value of the creature | 
| [SetName](attribute.md#setname) | <span style="display:inline;color:#ff5555">Server</span> | Used to set a custom name for the mob, which has the same function as the original name tag. It is not supported by players and new wandering traders yet. | 
| [SetPersistent](property.md#setpersistent) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity to not be [cleared](https://minecraft.fandom.com/zh/wiki/%E7%94%9F%E6%88%90#.E5.9F.BA.E5.B2.A9.E7.89.88_2) because it is too far away from the player | 
| [SetPlayerLookAtPos](property.md#setplayerlookatpos) | <span style="display:inline;color:#7575f9">Client</span> | Set the local player to look at a certain position | 
| [SetPos](property.md#setpos) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity position | 
| [SetRecoverTotalAirSupplyTime](attribute.md#setrecovertotalairsupplytime) | <span style="display:inline;color:#ff5555">Server</span> | Set the time to restore the maximum oxygen volume, in seconds | 
| [SetRot](attribute.md#setrot) | <span style="display:inline;color:#ff5555">Server</span> | Set the pitch angle of the entity head and the horizontal direction and the rotation angle of the vertical direction <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/10-Vector3.html">MC Coordinate System Description</a> | 
| [SetRot](attribute.md#setrot) | <span style="display:inline;color:#7575f9">Client</span> | Set the pitch angle of the entity head and the horizontal direction and the rotation angle of the vertical direction <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/10-Vector3.html">MC Coordinate System Description</a> | 
| [SetSize](attribute.md#setsize) | <span style="display:inline;color:#ff5555">Server</span> | Set the bounding box of the entity | 
| [isEntityInLava](attribute.md#isentityinlava) | <span style="display:inline;color:#7575f9">Client</span> | Whether the entity is in the magma | 
| [isEntityOnGround](attribute.md#isentityonground) | <span style="display:inline;color:#7575f9">Client</span> | Whether the entity is touching the ground | 

### Behavior 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddEntityAroundEntityMotion](Behavior.md#addentityaroundentitymotion) | <span style="display:inline;color:#ff5555">Server</span> | Add an entity around motion to the entity (excluding the player) | 
| [AddEntityAroundPointMotion](Behavior.md#addentityaroundpointmotion) | <span style="display:inline;color:#ff5555">Server</span> | Add a point around motion to the entity (excluding the player) | 
| [AddEntityTrackMotion](Behavior.md#addentitytrackmotion) | <span style="display:inline;color:#ff5555">Server</span> | Add a trajectory motion device to an entity (excluding players) | 
| [AddEntityVelocityMotion](Behavior.md#addentityvelocitymotion) | <span style="display:inline;color:#ff5555">Server</span> | Add a velocity motion device to an entity (excluding players) | 
| [GetAttackTarget](Behavior.md#getattacktarget) | <span style="display:inline;color:#ff5555">Server</span> | Get the target of hatred | 
| [GetBlockControlAi](Behavior.md#getblockcontrolai) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the creature's native AI is blocked | 
| [GetCustomGoalCls](Behavior.md#getcustomgoalcls) | <span style="display:inline;color:#ff5555">Server</span> | Base class for obtaining server-defined behavior nodes. When implementing a new behavior node, you need to inherit the class returned by this interface | 
| [GetEntityMotions](Behavior.md#getentitymotions) | <span style="display:inline;color:#ff5555">Server</span> | Get all motion devices on an entity (excluding players) | 
| [GetMotion](Behavior.md#getmotion) | <span style="display:inline;color:#ff5555">Server</span> | Get the instantaneous movement direction vector of a creature (including players) | 
| [GetMotion](Behavior.md#getmotion) | <span style="display:inline;color:#7575f9">Client</span> | Get the instantaneous movement direction vector of a creature |

| [GetOwnerId](Behavior.md#getownerid) | <span style="display:inline;color:#ff5555">Server</span> | Get the owner ID of the tamed creature | 
| [GetStepHeight](Behavior.md#getstepheight) | <span style="display:inline;color:#ff5555">Server</span> | Returns the maximum step height that the player can climb when moving forward without jumping | 
| [Hurt](Behavior.md#hurt) | <span style="display:inline;color:#ff5555">Server</span> | Set entity damage | 
| [ImmuneDamage](Behavior.md#immunedamage) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the entity is immune to damage (this attribute is archived) | 
| [IsEntityOnFire](Behavior.md#isentityonfire) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the entity is on fire | 
| [RemoveEntityMotion](Behavior.md#removeentitymotion) | <span style="display:inline;color:#ff5555">Server</span> | Remove the motion device on the entity (excluding the player) | 
| [ResetAttackTarget](Behavior.md#resetattacktarget) | <span style="display:inline;color:#ff5555">Server</span> | Clear the target of hatred | 
| [ResetMotion](Behavior.md#resetmotion) | <span style="display:inline;color:#ff5555">Server</span> | Reset the instantaneous movement direction vector of the creature (excluding the player) | 
| [ResetStepHeight](Behavior.md#resetstepheight) | <span style="display:inline;color:#ff5555">Server</span> | Restore the engine default maximum step height that the player can climb when moving forward without jumping | 
| [SetActorCollidable](Behavior.md#setactorcollidable) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the entity is collidable | 
| [SetActorPushable](Behavior.md#setactorpushable) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the entity is pushable | 
| [SetAttackTarget](Behavior.md#setattacktarget) | <span style="display:inline;color:#ff5555">Server</span> | Set the target of hatred | 
| [SetBlockControlAi](Behavior.md#setblockcontrolai) | <span style="display:inline;color:#ff5555">Server</span> | Set to block the creature's native AI | 
| [SetCanOtherPlayerRide](Behavior.md#setcanotherplayerride) | <span style="display:inline;color:#ff5555">Server</span> | Set whether other players have the right to ride, True means every player can ride, False means only the tamer can ride | 
| [SetControl](Behavior.md#setcontrol) | <span style="display:inline;color:#ff5555">Server</span> | Set the creature to be able to walk and jump without equipping a saddle | 
| [SetEntityInteractFilter](Behavior.md#setentityinteractfilter) | <span style="display:inline;color:#ff5555">Server</span> | Set the conditions for interacting with the creature | 
| [SetEntityOnFire](Behavior.md#setentityonfire) | <span style="display:inline;color:#ff5555">Server</span> | Set entity on fire | 
| [SetEntityRide](Behavior.md#setentityride) | <span style="display:inline;color:#ff5555">Server</span> | Tame rideable creatures | 
| [SetEntityShareablesItems](Behavior.md#setentityshareablesitems) | <span style="display:inline;color:#ff5555">Server</span> | Set the list of items that can be shared/picked up by the creature | 
| [SetEntityTamed](Behavior.md#setentitytamed) | <span style="display:inline;color:#ff5555">Server</span> | Set creature taming, which needs to be used with entityEvent component. This type of taming does not include the riding function. | 
| [SetJumpPower](Behavior.md#setjumppower) | <span style="display:inline;color:#ff5555">Server</span> | Set the jump power of the creature, 0.42 is the normal level | 
| [SetMobKnockback](Behavior.md#setmobknockback) | <span style="display:inline;color:#ff5555">Server</span> | Set the initial speed of the knockback, and consider the influence of resistance | 
| [SetMotion](Behavior.md#setmotion) | <span style="display:inline;color:#ff5555">Server</span> | Set the instantaneous movement direction vector of the creature (excluding the player) | 
| [SetMotion](Behavior.md#setmotion) | <span style="display:inline;color:#7575f9">Client</span> | Set the instantaneous movement direction vector, for local players | 
| [SetMoveSetting](Behavior.md#setmovesetting) | <span style="display:inline;color:#ff5555">Server</span> | Pathfinding component | 
| [SetPersistence](Behavior.md#setpersistence) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the entity is persistent. | 
| [SetRidePos](Behavior.md#setridepos) | <span style="display:inline;color:#ff5555">Server</span> | Set the creature's riding position | 
| [SetRiderRideEntity](Behavior.md#setriderrideentity) | <span style="display:inline;color:#ff5555">Server</span> | Set the entity to ride the creature (or boat and minecart) | 
| [SetStepHeight](Behavior.md#setstepheight) | <span style="display:inline;color:#ff5555">Server</span> | Set the maximum step height that the player can climb when moving forward without jumping. The default value is 0.5625. 1 means that you can climb one step | 
| [StartEntityMotion](Behavior.md#startentitymotion) | <span style="display:inline;color:#ff5555">Server</span> | Start a motion device on an entity (excluding players) | 
| [StopEntityMotion](Behavior.md#stopentitymotion) | <span style="display:inline;color:#ff5555">Server</span> | Stop a motion device on an entity (excluding players) | 
| [TriggerCustomEvent](Behavior.md#triggercustomevent) | <span style="display:inline;color:#ff5555">Server</span> | Trigger a creature custom event | 

### Status Effect 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddEffectToEntity](StatusEffect.md#addeffecttoentity) | <span style="display:inline;color:#ff5555">Server</span> | Add a specified status effect to the entity. If the added status already exists, the following situations will occur: 1. If the level is greater than the existing one, update the status level and duration; 2. If the status levels are equal and the remaining duration is greater than the existing one, refresh the remaining time; 3. If the level is less than the existing one, do not modify it; 4. The particle effect is based on the new one | 
| [GetAllEffects](StatusEffect.md#getalleffects) | <span style="display:inline;color:#ff5555">Server</span> | Get all current status effects of the entity | 
| [RemoveEffectFromEntity](StatusEffect.md#removeeffectfromentity) | <span style="display:inline;color:#ff5555">Server</span> | Delete the specified status effect for the entity | 

### Rendering 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddActorAnimation](rendering.md#addactoranimation) | <span style="display:inline;color:#7575f9">client</span> | Add creature rendering animation | 
| [AddActorAnimationController](rendering.md#addactoranimationcontroller) | <span style="display:inline;color:#7575f9">client</span> | Add creature rendering animation controller | 
| [AddActorBlockGeometry](rendering.md#addactorblockgeometry) | <span style="display:inline;color:#7575f9">client</span> | Add block geometry model for entity. | 
| [AddActorGeometry](rendering.md#addactorgeometry) | <span style="display:inline;color:#7575f9">Client</span> | Add biological rendering geometry | 
| [AddActorParticleEffect](rendering.md#addactorparticleeffect) | <span style="display:inline;color:#7575f9">Client</span> | Add biological special effects resources |

| [AddActorRenderController](Rendering.md#addactorrendercontroller) | <span style="display:inline;color:#7575f9">Client</span> | Add creature <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_7-Custom Rendering Controller">Rendering Controller</a> | 
| [AddActorRenderControllerArray](Rendering.md#addactorrendercontrollerarray) | <span style="display:inline;color:#7575f9">Client</span> | Add dictionary arrays elements in the creature rendering controller list | 
| [AddActorRenderMaterial](Rendering.md#addactorrendermaterial) | <span style="display:inline;color:#7575f9">Client</span> | Add creature rendering required <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_3-Custom Materials">Material</a> | 
| [AddActorScriptAnimate](Rendering.md#addactorscriptanimate) | <span style="display:inline;color:#7575f9">Client</span> | Add animation/animation controller to the scripts/animate node in the creature's client entity definition (minecraft:client_entity) json | 
| [AddActorSoundEffect](Rendering.md#addactorsoundeffect) | <span style="display:inline;color:#7575f9">Client</span> | Add creature sound effect resources | 
| [AddActorTexture](Rendering.md#addactortexture) | <span style="display:inline;color:#7575f9">Client</span> | Add biological rendering map | 
| [BindEntityToEntity](rendering.md#bindentitytoentity) | <span style="display:inline;color:#7575f9">Client</span> | The bound skeleton model follows other entities, and the camera also follows other entities | 
| [ClearActorBlockGeometry](rendering.md#clearactorblockgeometry) | <span style="display:inline;color:#7575f9">Client</span> | Delete all block geometry models in the entity. | 
| [DeleteActorBlockGeometry](rendering.md#deleteactorblockgeometry) | <span style="display:inline;color:#7575f9">Client</span> | Delete the specified block geometry model in the entity. | 
| [GetNotRenderAtAll](Rendering.md#getnotrenderatall) | <span style="display:inline;color:#7575f9">Client</span> | Get whether the entity is not rendered | 
| [RebuildActorRender](Rendering.md#rebuildactorrender) | <span style="display:inline;color:#7575f9">Client</span> | Rebuild the creature's data renderer (this interface does not support players, players should use RebuildPlayerRender) | 
| [RemoveActorAnimationController](Rendering.md#removeactoranimationcontroller) | <span style="display:inline;color:#7575f9">Client</span> | Remove the creature rendering animation controller | 
| [RemoveActorGeometry](Rendering.md#removeactorgeometry) | <span style="display:inline;color:#7575f9">Client</span> | Remove creature rendering geometry | 
| [RemoveActorRenderController](Rendering.md#removeactorrendercontroller) | <span style="display:inline;color:#7575f9">Client</span> | Remove creature <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_7-Custom Rendering Controller">Rendering Controller</a> | 
| [RemoveActorTexture](Rendering.md#removeactortexture) | <span style="display:inline;color:#7575f9">Client</span> | Remove creature rendering texture | 
| [ResetBindEntity](Rendering.md#resetbindentity) | <span style="display:inline;color:#7575f9">Client</span> | Cancel the binding entity of the target entity. After cancellation, it will no longer follow any other entity. | 
| [SetActorAllBlockGeometryVisible](Rendering.md#setactorallblockgeometryvisible) | <span style="display:inline;color:#7575f9">Client</span> | Sets whether all the block geometry models in the entity are displayed. | 
| [SetActorBlockGeometryVisible](Rendering.md#setactorblockgeometryvisible) | <span style="display:inline;color:#7575f9">Client</span> | Sets whether the specified block geometry model in the entity is displayed. | 
| [SetAlwaysShowName](rendering.md#setalwaysshowname) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the creature's name is always displayed, even when the aiming point is not pointing at the creature | 
| [SetColor](rendering.md#setcolor) | <span style="display:inline;color:#7575f9">Client</span> | Set the color and background color of the health bar | 
| [SetHealthBarDeviation](rendering.md#sethealthbardeviation) | <span style="display:inline;color:#7575f9">Client</span> | Set the relative height of an entity's health bar | 
| [SetNameDeeptest](rendering.md#setnamedeeptest) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the name is transparent | 
| [SetNotRenderAtAll](Rendering.md#setnotrenderatall) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to turn off entity rendering | 
| [SetRenderLocalPlayer](Rendering.md#setrenderlocalplayer) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the local player is rendered | 
| [SetShowName](Rendering.md#setshowname) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the creature name is displayed according to the default game logic | 
| [ShowHealth](Rendering.md#showhealth) | <span style="display:inline;color:#7575f9">Client</span> | Set whether a certain entity displays a health bar, the default is to display | 
| [ShowHealthBar](Rendering.md#showhealthbar) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to display health bar | 

### Backpack 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetEntityItem](Backpack.md#getentityitem) | <span style="display:inline;color:#ff5555">Server</span> | Get biological items, support getting backpack, armor bar, off-hand and main hand items | 
| [GetEquItemEnchant](Backpack.md#getequitemenchant) | <span style="display:inline;color:#ff5555">Server</span> | Get the enchantment of the armor in the equipment slot | 
| [GetEquItemModEnchant](Backpack.md#getequitemmodenchant) | <span style="display:inline;color:#ff5555">Server</span> | Get the custom enchantment of the armor in the equipment slot | 
| [SetEntityItem](Backpack.md#setentityitem) | <span style="display:inline;color:#ff5555">Server</span> | Set biological items. It is recommended that developers set them according to the characteristics of the biological. Some biological equipment may not be displayed after setting, but they will still drop the set equipment after death | 

### Custom attributes 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetAttr](Custom attributes.md#getattr) | <span style="display:inline;color:#ff5555">Server</span> | Get attribute values | 
| [GetAttr](Custom attributes.md#getattr) | <span style="display:inline;color:#7575f9">Client</span> | Get attribute value | 
| [RegisterUpdateFunc](Custom Attribute.md#registerupdatefunc) | <span style="display:inline;color:#7575f9">Client</span> | Register the callback function when the attribute value changes. The function will be called when the attribute changes | 
| [SetAttr](Custom Attribute.md#setattr) | <span style="display:inline;color:#ff5555">Server</span> | Set attribute value | 
| [SetAttr](Custom Attribute.md#setattr) | <span style="display:inline;color:#7575f9">Client</span> | Set client attribute value | 
| [UnRegisterUpdateFunc](Custom Attribute.md#unregisterupdatefunc) | <span style="display:inline;color:#7575f9">Client</span> | Callback function when deregistering attribute value change | 

### Custom data 


| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CleanExtraData](CustomData.md#cleanextradata) | <span style="display:inline;color:#ff5555">Server</span> | Clears the custom data of an entity or a world. When clearing entity data, use the corresponding entity id to create a component. When clearing world data, use the levelId to create a component. | 
| [GetExtraData](CustomData.md#getextradata) | <span style="display:inline;color:#ff5555">Server</span> | Gets the value corresponding to a key in the custom data of an entity or a world. When getting entity data, use the corresponding entity id to create a component, and when getting world data, use levelId to create a component | 
| [GetWholeExtraData](Custom Data.md#getwholeextradata) | <span style="display:inline;color:#ff5555">Server</span> | Get the complete custom data of an entity or the custom data of the world. When getting entity data, use the corresponding entity id to create a component, and when getting world data, use levelId to create a component | 
| [SaveExtraData](Custom Data.md#saveextradata) | <span style="display:inline;color:#ff5555">Server</span> | Used to save custom data of an entity or custom data of the world | 
| [SetExtraData](Custom Data.md#setextradata) | <span style="display:inline;color:#ff5555">Server</span> | Used to set custom data of an entity or custom data of the world. The data is saved in the form of key-value pairs. When setting entity data, use the corresponding entity id to create a component. When setting world data, use levelId to create a component. | 

### molang 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [Get](molang.md#get) | <span style="display:inline;color:#7575f9">Client</span> | Get the value of a certain entity calculation node. If it does not exist, return the default value at registration. | 
| [GetMolangValue](molang.md#getmolangvalue) | <span style="display:inline;color:#7575f9">Client</span> | Get the value of the entity molang variable | 
| [GetStringHash64](molang.md#getstringhash64) | <span style="display:inline;color:#7575f9">Client</span> | Returns the hash64 of the string variable | 
| [Register](molang.md#register) | <span style="display:inline;color:#7575f9">Client</span> | Register entity computing node | 
| [Set](molang.md#set) | <span style="display:inline;color:#7575f9">Client</span> | Set the value of a certain entity computing node | 
| [UnRegister](molang.md#unregister) | <span style="display:inline;color:#7575f9">Client</span> | Unregister entity computing node | 

### Projectile 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetSourceEntityId](Projectile.md#getsourceentityid) | <span style="display:inline;color:#ff5555">Server</span> | Get the projectile launcher entity id | 

### Experience Ball 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetOrbExperience](Experience Ball.md#getorbexperience) | <span style="display:inline;color:#ff5555">Server</span> | Get the experience of the experience ball | 
| [SetOrbExperience](Experience Ball.md#setorbexperience) | <span style="display:inline;color:#ff5555">Server</span> | Set the experience of the experience ball | 

### Official Partner 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [Disable](Official Partner.md#disable) | <span style="display:inline;color:#ff5555">Server</span> | Disable the official partner function. Single-player games and local online games do not support this interface | 
| [Enable](Official Partner.md#enable) | <span style="display:inline;color:#ff5555">Server</span> | Enable the official partner function. Single-player games and local online games do not support this interface | 

### Tags 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddEntityTag](标签.md#addentitytag) | <span style="display:inline;color:#ff5555">Server</span> | Add entity tags | 
| [EntityHasTag](标签.md#entityhastag) | <span style="display:inline;color:#ff5555">Server</span> | Determine whether an entity has a specified tag | 
| [GetEntityTags](标签.md#getentitytags) | <span style="display:inline;color:#ff5555">Server</span> | Get a list of entity tags | 
| [RemoveEntityTag](标签.md#removeentitytag) | <span style="display:inline;color:#ff5555">Server</span> | Remove a specified tag from an entity | 

