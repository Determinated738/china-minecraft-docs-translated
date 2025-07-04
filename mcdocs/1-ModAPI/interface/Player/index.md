--- 
sidebarDepth: 1 
--- 
# Index 

Including the interface of player attributes and behaviors. For player acquisition, see [World/Entity Management](../World/Index.md#Entity Management). Players are also entities, so the interfaces under the [Entity](../Entity/Index.md) category also apply to players 

--- 

- [Properties](#Properties) 
- [Behaviors](#Behaviors) 
- [Rendering](#Rendering) 
- [Backpacks](#Backpacks) 
- [Cameras](#Cameras) 
- [Animations](#Animations) 
- [Game Modes](#Game Modes) 
- [Permissions](#Permissions) 
- [Navigation](#Navigation) 

### Properties 

| Interfaces | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddPlayerExperience](properties.md#addplayerexperience) | <span style="display:inline;color:#ff5555">Server</span> | Increase player experience | 
| [AddPlayerLevel](properties.md#addplayerlevel) | <span style="display:inline;color:#ff5555">Server</span> | Modify player level | 
| [CollectOnlineClientData](property.md#collectonlineclientdata) | <span style="display:inline;color:#ff5555">Server</span> | Collect online player client data to determine whether the player is cheating | 
| [GetPlayerExp](property.md#getplayerexp) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's experience value at the current level | 
| [GetPlayerHealthLevel](property.md#getplayerhealthlevel) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's health threshold. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural recovery are turned on. The default value in the original version is 18 | 
| [GetPlayerHealthTick](attribute.md#getplayerhealthtick) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's natural recovery speed. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural recovery are turned on. The default value in the original version is 80 ticks (i.e., 1 health point is restored every 4 seconds) | 
| [GetPlayerHunger](attribute.md#getplayerhunger) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's hunger, displayed on the UI hunger progress bar, with an initial value of 20, i.e., each drumstick represents 2 hunger points. **Saturation**: The player's current saturation, with an initial value of 5, and the maximum value is always the player's current hunger. This value directly affects the player's **hunger**. <br>1) Increase method: Eat food. <br>2) Decrease method: Every time a **consumption event** is triggered, the value decreases by 1. If the value is not greater than 0, directly reduce the player's **hunger** by 1. | 
| [GetPlayerLevel](Attribute.md#getplayerlevel) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's level | 
| [GetPlayerMaxExhaustionValue](Attribute.md#getplayermaxexhaustionvalue) | <span style="display:inline;color:#ff5555">Server</span> | Get the zero value of the player's foodExhaustionLevel, a constant value, the default is 4. **Exhaustion** refers to the current exhaustion level of the player. The initial value is 0. This value will increase with the influence of a series of player actions (such as jumping). When this value is greater than the maximum exhaustion (maxExhaustion), it will return to zero and the saturation (saturation) will be reduced by 1 (in order to illustrate the hunger mechanism, we define this as a **exhaustion event**) | 
| [GetPlayerStarveLevel](Property.md#getplayerstarvelevel) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's hunger threshold. When the hunger value is less than the hunger threshold, the health will be automatically deducted. It is effective when the hunger value and hunger blood loss are turned on. The default value in the original version is 1 | 
| [GetPlayerStarveTick](attribute.md#getplayerstarvetick) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's hunger blood loss rate. When the hunger value is less than the hunger threshold, the blood will be automatically deducted. It is effective when the hunger value and hunger blood loss are enabled. The default value in the original version is 80 ticks (i.e. 1 health point is deducted every 4 seconds) | 
| [GetPlayerTotalExp](attribute.md#getplayertotalexp) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's total experience value | 
| [IsPlayerNaturalRegen](attribute.md#isplayernaturalregen) | <span style="display:inline;color:#ff5555">Server</span> | Whether to enable the player's natural regeneration. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural regeneration are enabled. Enabled by default in the original version | 
| [IsPlayerNaturalStarve](attribute.md#isplayernaturalstarve) | <span style="display:inline;color:#ff5555">Server</span> | Whether to enable the player's health loss due to hunger. When the hunger value is less than the hunger threshold, the player's health will be automatically restored. This is effective when the hunger value and hunger loss are enabled. The default setting is enabled in the original version. | 
| [SetPlayerHealthLevel](property.md#setplayerhealthlevel) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's health threshold. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural recovery are enabled. The default value in the original version is 18. | 
| [SetPlayerHealthTick](property.md#setplayerhealthtick) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's natural recovery speed. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural recovery are enabled. The default value in the original version is 80 ticks (i.e., 1 health point is restored every 4 seconds). | 
| [SetPlayerHunger](property.md#setplayerhunger) | <span style="display:inline;color:#ff5555">Server</span> | Sets the player's hunger level. | 
| [SetPlayerMaxExhaustionValue](property.md#setplayermaxexhaustionvalue) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's **maxExhaustion**. By adjusting the **maxExhaustion**, you can adjust the **hunger** consumption rate. When the **maxExhaustion** is very large, the hunger may seem to never decrease. | 
| [SetPlayerNaturalRegen](property.md#setplayernaturalregen) | <span style="display:inline;color:#ff5555">Server</span> | Set whether to enable the player's natural regeneration. When the hunger value is greater than or equal to the health threshold, the health will be automatically restored. It is effective when the hunger value and natural regeneration are enabled. The original version is enabled by default. | 
| [SetPlayerNaturalStarve](property.md#setplayernaturalstarve) | <span style="display:inline;color:#ff5555">Server</span> | Set whether to enable player's hunger blood loss. When the hunger value is less than the hunger critical value, the blood will be automatically deducted. It is effective when the hunger value and hunger blood loss are enabled. The original version is enabled by default. | 
| [SetPlayerPrefixAndSuffixName](property.md#setplayerprefixandsuffixname) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's prefix and suffix name | 
| [SetPlayerStarveLevel](property.md#setplayerstarvelevel) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's hunger critical value. When the hunger value is less than the hunger critical value, the blood will be automatically deducted. It is effective when the hunger value and hunger blood loss are enabled. The default value of the original version is 1 | 
| [SetPlayerStarveTick](property.md#setplayerstarvetick) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's hunger blood loss speed. When the hunger value is less than the hunger threshold, the blood will be automatically deducted. It is effective when the hunger value and hunger blood loss are turned on. The default value of the original version is 80 ticks (i.e., 1 blood point is deducted every 4 seconds) | 
| [SetPlayerTotalExp](property.md#setplayertotalexp) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's total experience value | 
| [Swing](property.md#swing) | <span style="display:inline;color:#7575f9">Client</span> | The local player plays the original attack action | 
| [getUid](property.md#getuid) | <span style="display:inline;color:#7575f9">Client</span> | Get the local player's uid | 


### Behavior 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddPlayerAroundEntityMotion](Behavior.md#addplayeraroundentitymotion) | <span style="display:inline;color:#ff5555">Server</span> | Add entity surround motion to the player | 
| [AddPlayerAroundPointMotion](Behavior.md#addplayeraroundpointmotion) | <span style="display:inline;color:#ff5555">Server</span> | Add point surround motion to the player | 
| [AddPlayerTrackMotion](Behavior.md#addplayertrackmotion) | <span style="display:inline;color:#ff5555">Server</span> | Add track motion to the player | 
| [AddPlayerVelocityMotion](Behavior.md#addplayervelocitymotion) | <span style="display:inline;color:#ff5555">Server</span> | Add velocity motion to the player | 
| [BeginSprinting](Behavior.md#beginsprinting) | <span style="display:inline;color:#7575f9">Client</span> | Make the local player enter and maintain a forward sprinting state | 
| [ChangePlayerDimension](Behavior.md#changeplayerdimension) | <span style="display:inline;color:#ff5555">Server</span> | Teleport the player | 
| [ChangePlayerFlyState](Behavior.md#changeplayerflystate) | <span style="display:inline;color:#ff5555">Server</span> | Grant/cancel the flying ability and enter the flying/non-flying state | 
| [EnableKeepInventory](Behavior.md#enablekeepinventory) | <span style="display:inline;color:#ff5555">Server</span> | Set the player to not drop items when he dies | 
| [EndSprinting](Behavior.md#endsprinting) | <span style="display:inline;color:#7575f9">Client</span> | End the local player's forward sprinting state | 
| [GetEntityRider](Behavior.md#getentityrider) | <span style="display:inline;color:#ff5555">Server</span> | Get the id of the entity the player is riding. | 
| [GetIsBlocking](Behavior.md#getisblocking) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's shield activation status | 
| [GetPlayerExhaustionRatioByType](Behavior.md#getplayerexhaustionratiobytype) | <span style="display:inline;color:#ff5555">Server</span> | Get the hunger consumption multiplier of a certain behavior of the player | 
| [GetPlayerMotions](Behavior.md#getplayermotions) | <span style="display:inline;color:#ff5555">Server</span> | Get all motion devices on the player | 
| [GetPlayerRespawnPos](Behavior.md#getplayerrespawnpos) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's resurrection point | 
| [GetRelevantPlayer](Behavior.md#getrelevantplayer) | <span style="display:inline;color:#ff5555">Server</span> | Get a list of nearby player IDs | 
| [IsEntityRiding](Behavior.md#isentityriding) | <span style="display:inline;color:#ff5555">Server</span> | Check if the player is riding. | 
| [IsPlayerFlying](Behavior.md#isplayerflying) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the player is flying | 
| [PickUpItemEntity](Behavior.md#pickupitementity) | <span style="display:inline;color:#ff5555">Server</span> | A player picks up an item ItemEntity | 
| [PlayerDestoryBlock](Behavior.md#playerdestoryblock) | <span style="display:inline;color:#ff5555">Server</span> | Use the tool in hand to destroy the block | 
| [PlayerUseItemToEntity](Behavior.md#playeruseitemtoentity) | <span style="display:inline;color:#ff5555">Server</span> | The player uses the item in hand to use a creature | 
| [PlayerUseItemToPos](Behavior.md#playeruseitemtopos) | <span style="display:inline;color:#ff5555">Server</span> | The player uses an item to a certain coordinate | 
| [RemovePlayerMotion](Behavior.md#removeplayermotion) | <span style="display:inline;color:#ff5555">Server</span> | Remove the motion device on the player | 
| [SetPickUpArea](Behavior.md#setpickuparea) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's pickup range. After setting, the player's pickup range will be changed based on the original pickup range. | 
| [SetPlayerAttackSpeedAmplifier](Behavior.md#setplayerattackspeedamplifier) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's attack speed multiplier, 1.0 means normal level, 1.2 means 20% speed reduction, 0.8 means 20% speed gain | 
| [SetPlayerExhaustionRatioByType](Behavior.md#setplayerexhaustionratiobytype) | <span style="display:inline;color:#ff5555">Server</span> | Set the hunger consumption multiplier of a certain behavior of the player | 
| [SetPlayerJumpable](Behavior.md#setplayerjumpable) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the player can jump | 
| [SetPlayerMovable](Behavior.md#setplayermovable) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the player can move | 
| [SetPlayerRespawnPos](Behavior.md#setplayerrespawnpos) | <span style="display:inline;color:#ff5555">Server</span> | Set the position and dimension of the player's resurrection | 
| [SetPlayerRideEntity](Behavior.md#setplayerrideentity) | <span style="display:inline;color:#ff5555">Server</span> | Set the player to ride a creature (or a boat or a minecart) | 
| [StartPlayerMotion](Behavior.md#startplayermotion) | <span style="display:inline;color:#ff5555">Server</span> | Start a certain motion device on the player | 
| [StopEntityRiding](Behavior.md#stopentityriding) | <span style="display:inline;color:#ff5555">Server</span> | Force the player to dismount. | 
| [StopPlayerMotion](Behavior.md#stopplayermotion) | <span style="display:inline;color:#ff5555">Server</span> | Stop a certain motion device on the player | 
| [isGliding](Behavior.md#isgliding) | <span style="display:inline;color:#7575f9">Client</span> | Is the player flying with elytra? | 
| [isInWater](Behavior.md#isinwater) | <span style="display:inline;color:#7575f9">Client</span> | Is the player in water? | 
| [isMoving](Behavior.md#ismoving) | <span style="display:inline;color:#7575f9">Client</span> | Is the player walking? | 
| [isRiding](Behavior.md#isriding) | <span style="display:inline;color:#7575f9">Client</span> | Is riding | 
| [isSneaking](Behavior.md#issneaking) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the player is in sneaking state | 
| [isSneaking](Behavior.md#issneaking) | <span style="display:inline;color:#7575f9">Client</span> | Is sneaking | 
| [isSprinting](Behavior.md#issprinting) | <span style="display:inline;color:#7575f9">Client</span> | Is sprinting | 
| [isSwimming](Behavior.md#isswimming) | <span style="display:inline;color:#ff5555">Server</span> | Gets whether the player is swimming. | 
| [isSwimming](Behavior.md#isswimming) | <span style="display:inline;color:#7575f9">Client</span> | Whether to swim | 
| [setMoving](Behavior.md#setmoving) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to walk, can only be set for local players (only applicable to mobile terminals) | 
| [setSneaking](Behavior.md#setsneaking) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to sneak, can only be set for local players (only applicable to mobile terminals) | 
| [setSprinting](Behavior.md#setsprinting) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to sprint, can only be set for local players (only applicable to mobile terminals) | 
| [setUsingShield](behavior.md#setusingshield) | <span style="display:inline;color:#7575f9">Client</span> | Activate shield status | 


### Rendering 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddPlayerAnimation](Rendering.md#addplayeranimation) | <span style="display:inline;color:#7575f9">Client</span> | Add player rendering animation | 
| [AddPlayerAnimationController](Rendering.md#addplayeranimationcontroller) | <span style="display:inline;color:#7575f9">Client</span> | Add player rendering animation controller | 
| [AddPlayerAnimationIntoState](Rendering.md#addplayeranimationintostate) | <span style="display:inline;color:#7575f9">Client</span> | Add animation in the state of the player's animation controller | 
| [AddPlayerGeometry](rendering.md#addplayergeometry) | <span style="display:inline;color:#7575f9">Client</span> | Add player rendering geometry | 
| [AddPlayerParticleEffect](rendering.md#addplayerparticleeffect) | <span style="display:inline;color:#7575f9">Client</span> | Add player special effect resources | 
| [AddPlayerRenderController](rendering.md#addplayerrendercontroller) | <span style="display:inline;color:#7575f9">Client</span> | Add player <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_7-Custom Rendering Controller">Rendering Controller</a> | 
| [AddPlayerRenderMaterial](Rendering.md#addplayerrendermaterial) | <span style="display:inline;color:#7575f9">Client</span> | Add <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_3-Custom Materials">materials</a> required for player rendering | 
| [AddPlayerSoundEffect](Rendering.md#addplayersoundeffect) | <span style="display:inline;color:#7575f9">Client</span> | Add player sound effect resources | 
| [AddPlayerTexture](Rendering.md#addplayertexture) | <span style="display:inline;color:#7575f9">Client</span> | Add player rendering textures | 
| [RebuildPlayerRender](rendering.md#rebuildplayerrender) | <span style="display:inline;color:#7575f9">client</span> | Rebuild the player's data renderer | 
| [RemovePlayerAnimationController](rendering.md#removeplayeranimationcontroller) | <span style="display:inline;color:#7575f9">client</span> | Remove the player render animation controller | 
| [RemovePlayerGeometry](rendering.md#removeplayergeometry) | <span style="display:inline;color:#7575f9">client</span> | Remove the player render geometry | 
| [RemovePlayerRenderController](rendering.md#removeplayerrendercontroller) | <span style="display:inline;color:#7575f9">client</span> | Remove the player <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/3-Custom Creatures/01-Custom Basic Creatures.html#_7-Custom Rendering Controller">Rendering Controller</a> | 
| [SetPlayerItemInHandVisible](Rendering.md#setplayeriteminhandvisible) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to hide the player's handheld item model display | 
| [SetSkin](Rendering.md#setskin) | <span style="display:inline;color:#7575f9">Client</span> | Replace the original custom skin | 

### Backpack 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddEnchantToInvItem](Backpack.md#addenchanttoinvitem) | <span style="display:inline;color:#ff5555">Server</span> | Add enchantment information to items in the inventory | 
| [AddModEnchantToInvItem](Backpack.md#addmodenchanttoinvitem) | <span style="display:inline;color:#ff5555">Server</span> | Add custom enchantment information to items in the inventory | 
| [ChangePlayerItemTipsAndExtraId](Backpack.md#changeplayeritemtipsandextraid) | <span style="display:inline;color:#ff5555">Server</span> | Modify the custom tips and custom identifiers of player items | 
| [ChangeSelectSlot](Backpack.md#changeselectslot) | <span style="display:inline;color:#ff5555">Server</span> | Set the index of the player's currently selected quick bar item | 
| [GetCarriedItem](Backpack.md#getcarrieditem) | <span style="display:inline;color:#7575f9">Client</span> | Get the information of the right-hand item | 
| [GetInvItemEnchantData](Backpack.md#getinvitemenchantdata) | <span style="display:inline;color:#ff5555">Server</span> | Get the enchantment information of the item in the inventory | 
| [GetInvItemModEnchantData](Backpack.md#getinvitemmodenchantdata) | <span style="display:inline;color:#ff5555">Server</span> | Get the custom enchantment information of the item in the inventory | 
| [GetOffhandItem](Backpack.md#getoffhanditem) | <span style="display:inline;color:#7575f9">Client</span> | Get the information of the left hand item | 
| [GetPlayerAllItems](Backpack.md#getplayerallitems) | <span style="display:inline;color:#ff5555">Server</span> | Get the batch item information of the player's specified slot | 
| [GetPlayerItem](Backpack.md#getplayeritem) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's items, including backpack, armor bar, off-hand and main-hand items | 
| [GetSelectSlotId](Backpack.md#getselectslotid) | <span style="display:inline;color:#ff5555">Server</span> | Get the player's currently selected slot | 
| [GetSlotId](Backpack.md#getslotid) | <span style="display:inline;color:#7575f9">Client</span> | Get the slot id of the currently held quick bar | 
| [RemoveEnchantToInvItem](Backpack.md#removeenchanttoinvitem) | <span style="display:inline;color:#ff5555">Server</span> | Remove enchantment information from items in the inventory | 
| [RemoveModEnchantToInvItem](Backpack.md#removemodenchanttoinvitem) | <span style="display:inline;color:#ff5555">Server</span> | Remove custom enchantment information from items in the inventory | 
| [SetInvItemExchange](Backpack.md#setinvitemexchange) | <span style="display:inline;color:#ff5555">Server</span> | Exchange player backpack items | 
| [SetInvItemNum](Backpack.md#setinvitemnum) | <span style="display:inline;color:#ff5555">Server</span> | Set the number of items in the player's backpack | 
| [SetPlayerAllItems](Backpack.md#setplayerallitems) | <span style="display:inline;color:#ff5555">Server</span> | Add batch item information to the specified slot | 
| [SpawnItemToPlayerCarried](Backpack.md#spawnitemtoplayercarried) | <span style="display:inline;color:#ff5555">Server</span> | Spawn items to the player's right hand | 
| [SpawnItemToPlayerInv](Backpack.md#spawnitemtoplayerinv) | <span style="display:inline;color:#ff5555">Server</span> | Spawn items to the player's backpack | 
### Camera 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [DepartCamera](Camera.md#departcamera) | <span style="display:inline;color:#7575f9">Client</span> | Separate the player from the camera | 
| [GetCameraAnchor](Camera.md#getcameraanchor) | <span style="display:inline;color:#7575f9">Client</span> | Get the camera anchor |

| [GetCameraOffset](Camera.md#getcameraoffset) | <span style="display:inline;color:#7575f9">Client</span> | Get the camera offset | 
| [GetCameraPitchLimit](Camera.md#getcamerapitchlimit) | <span style="display:inline;color:#7575f9">Client</span> | Get the camera up and down angle limit | 
| [GetCameraRot](Camera.md#getcamerarot) | <span style="display:inline;color:#7575f9">Client</span> | Get the camera rotation | 
| [GetForward](Camera.md#getforward) | <span style="display:inline;color:#7575f9">Client</span> | Returns the camera forward direction | 
| [GetFov](Camera.md#getfov) | <span style="display:inline;color:#7575f9">Client</span> | Get the field of view | 
| [GetFpHeight](Camera.md#getfpheight) | <span style="display:inline;color:#7575f9">Client</span> | Get the camera height offset in the first-person perspective of the local player in the current state. It will be different when swimming, gliding and in normal state | 
| [GetPerspective](Camera.md#getperspective) | <span style="display:inline;color:#7575f9">Client</span> | Get the current perspective mode | 
| [GetPosition](Camera.md#getposition) | <span style="display:inline;color:#7575f9">Client</span> | Return to the center of the camera | 
| [IsModCameraLockPitch](Camera.md#ismodcameralockpitch) | <span style="display:inline;color:#7575f9">Client</span> | Whether to lock the up and down angle of the camera | 
| [IsModCameraLockYaw](Camera.md#ismodcameralockyaw) | <span style="display:inline;color:#7575f9">Client</span> | Whether to lock the left and right angle of the camera | 
| [LockCamera](Camera.md#lockcamera) | <span style="display:inline;color:#7575f9">Client</span> | Lock the camera | 
| [LockModCameraPitch](Camera.md#lockmodcamerapitch) | <span style="display:inline;color:#7575f9">Client</span> | Lock the camera up and down (effective in third-person perspective, the viewing angle cannot be adjusted up and down after locking) | 
| [LockModCameraYaw](Camera.md#lockmodcamerayaw) | <span style="display:inline;color:#7575f9">Client</span> | Lock the camera left and right (effective in third-person perspective, the viewing angle cannot be adjusted left and right with the mouse after locking) | 
| [LockPerspective](Camera.md#lockperspective) | <span style="display:inline;color:#7575f9">Client</span> | Lock the player's perspective mode | 
| [ResetCameraBindActorId](Camera.md#resetcamerabindactorid) | <span style="display:inline;color:#7575f9">Client</span> | Rebind the camera back to the protagonist | 
| [SetCameraAnchor](Camera.md#setcameraanchor) | <span style="display:inline;color:#7575f9">Client</span> | Set the camera anchor point. Only height is supported for now. Other dimensions are invalid | 
| [SetCameraBindActorId](Camera.md#setcamerabindactorid) | <span style="display:inline;color:#7575f9">Client</span> | Bind the camera to the target entity (the caller and the target must be in the same dimension and within the loading range. If the target leaves the range or dies after binding, it will be automatically unbound) | 
| [SetCameraOffset](Camera.md#setcameraoffset) | <span style="display:inline;color:#7575f9">Client</span> | Set the camera offset | 
| [SetCameraPitchLimit](Camera.md#setcamerapitchlimit) | <span style="display:inline;color:#7575f9">Client</span> | Set the camera's up and down angle limits, the default is (-90, 90) | 
| [SetCameraPos](Camera.md#setcamerapos) | <span style="display:inline;color:#7575f9">Client</span> | Set the position of the camera center | 
| [SetCameraRot](Camera.md#setcamerarot) | <span style="display:inline;color:#7575f9">Client</span> | Set the camera's direction | 
| [SetFov](Camera.md#setfov) | <span style="display:inline;color:#7575f9">Client</span> | Set the field of view | 
| [SetPerspective](Camera.md#setperspective) | <span style="display:inline;color:#7575f9">Client</span> | Set the viewing angle mode | 
| [SetSpeedFovLock](Camera.md#setspeedfovlock) | <span style="display:inline;color:#7575f9">Client</span> | Whether to lock the camera's field of view fov, which will not change with speed after locking | 
| [UnDepartCamera](Camera.md#undepartcamera) | <span style="display:inline;color:#7575f9">Client</span> | Bind player and camera | 
| [UnLockCamera](Camera.md#unlockcamera) | <span style="display:inline;color:#7575f9">Client</span> | Unlock camera | 

### Animation 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [PlayTpAnimation](Animation.md#playtpanimation) | <span style="display:inline;color:#7575f9">Client</span> | Play player common actions from third person perspective | 
| [StopAnimation](Animation.md#stopanimation) | <span style="display:inline;color:#7575f9">Client</span> | Stop playing player common actions | 

### Game Mode 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetPlayerGameType](GameMode.md#getplayergametype) | <span style="display:inline;color:#ff5555">Server</span> | Get the game mode of the specified player | 
| [SetPlayerGameType](GameMode.md#setplayergametype) | <span style="display:inline;color:#ff5555">Server</span> | Set the player's personal game mode | 

### Permissions 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetPlayerAbilities](Permissions.md#getplayerabilities) | <span style="display:inline;color:#ff5555">Server</span> | Get player specific permissions | 
| [GetPlayerOperation](Permissions.md#getplayeroperation) | <span style="display:inline;color:#ff5555">Server</span> | Get player permission type information | 

### Navigation 


| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetNavPath](导航.md#getnavpath) | <span style="display:inline;color:#7575f9">客户端</span> | Get the path from the local player to the target point. Developers can customize the navigation system through this interface. | 
| [StartNavTo](导航.md#startnavto) | <span style="display:inline;color:#7575f9">客户端</span> | We provide a navigation system implementation based on GetNavPath. The approach is to generate sequence frames on the path to guide the player to the target point, and re-navigate when the player deviates from the path. | 
| [StopNav](导航.md#stopnav) | <span style="display:inline;color:#7575f9">客户端</span> | Terminate the current navigation | 

