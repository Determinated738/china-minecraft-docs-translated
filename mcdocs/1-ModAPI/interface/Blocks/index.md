--- 
sidebarDepth: 1 
--- 
# Index 

Including the interface of block and block entity attributes. For the placement and acquisition of blocks, see [World/Block Management](../World/Index.md#Block Management) 

--- 

- [Block Status and Additional Value](#Block Status and Additional Value) 
- [Block Entity](#Block Entity) 
- [Block Geometry Model](#Block Geometry Model) 
- [Block Palette](#Block Palette) 
- [Rendering](#Rendering) 
- [Container](#Container) 
- [Redstone](#Redstone) 
- [Signboard](#Signboard) 
- [Bed](#Bed) 
- [Attributes](#Attributes) 

### Block Status and Additional Value 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetBlockAuxValueFromStates](Block state and additional value.md#getblockauxvaluefromstates) | <span style="display:inline;color:#ff5555">Server</span> | Get the block's additional value AuxValue based on the block name and <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State">Block State</a> | 
| [GetBlockStates](Block State and Additional Value.md#getblockstates) | <span style="display:inline;color:#ff5555">Server</span> | Get <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State">Block State</a> | 
| [GetBlockStatesFromAuxValue](Block State and Additional Value.md#getblockstatesfromauxvalue) | <span style="display:inline;color:#ff5555">Server</span> | Get <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block State">Block State</a> according to the block name and block additional value AuxValue | 
| [SetBlockStates](Block State and Additional Value.md#setblockstates) | <span style="display:inline;color:#ff5555">Server</span> | Set <a href="../../../../mcguide/20-Gameplay Development/10-Basic Concepts/1-My World Basic Concepts.html#Item Information Dictionary#Block Status">Block Status</a> | 

### Block Entity 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CleanBlockTileEntityCustomData](Block Entity.md#cleanblocktileentitycustomdata) | <span style="display:inline;color:#ff5555">Server</span> | Clear the custom data stored in the TileEntity bound to the special block (box, skull, furnace, flower pot, etc.) at the specified location. | 
| [CreateFrameEffectForBlockEntity](块对象.md#createframeeffectforblockentity) | <span style="display:inline;color:#7575f9">客户端</span> | Create a sequence frame effect on a custom block entity. After creation, this interface returns the ID of the sequence frame effect. With this ID, you can use the interface in the effect/sequence frame to play, set the position, size, and other operations on the sequence frame effect. Similar to the creation of the entity's sequence frame effect. | 
| [CreateParticleEffectForBlockEntity](块对象.md#createparticleeffectforblockentity) | <span style="display:inline;color:#7575f9">客户端</span> | Create a particle effect on a custom block entity. After creation, this interface returns the ID of the particle effect. With this ID, you can use the interface in the effect/particle to play, set the position, size, and other operations on the particle effect. This is similar to the way particle effects are created for entities. If a custom block entity already has an effect with the same key name, a new effect will not be created and the interface will return the existing effect ID. | 
| [GetBlockEntityData](BlockEntity.md#getblockentitydata) | <span style="display:inline;color:#ff5555">Server</span> | Used to get an object that can manipulate a custom block entity data, the operation method is similar to dict | 
| [GetBlockEntityData](BlockEntity.md#getblockentitydata) | <span style="display:inline;color:#ff5555">Server</span> | Used to get the data of blocks (including custom blocks), the data is read-only and not writable | 
| [GetBlockEntityMolangValue](BlockEntity.md#getblockentitymolangvalue) | <span style="display:inline;color:#7575f9">Client</span> | Get the value of the Molang variable of the custom block entity. | 
| [GetBlockTileEntityCustomData](BlockEntity.md#getblocktileentitycustomdata) | <span style="display:inline;color:#ff5555">Server</span> | Reads the custom data stored in the TileEntity bound to the special block (chest, skull, furnace, flower pot, etc.) at the specified location. | 
| [GetBlockTileEntityWholeCustomData](BlockEntity.md#getblocktileentitywholecustomdata) | <span style="display:inline;color:#ff5555">Server</span> | Reads the custom data dictionary stored in the TileEntity bound to the special block (chest, skull, furnace, flower pot, etc.) at the specified location. | 
| [GetFrameEffectIdInBlockEntity](BlockEntity.md#getframeeffectidinblockentity) | <span style="display:inline;color:#7575f9">Client</span> | Get the ID of the specified sequence frame effect created in the custom block entity. There are two types of created effects: one is the effect defined by "netease_frame_effects" in the entity json file under resource_pack/entity/; the other is the effect created using the interface CreateFrameEffectForBlockEntity. The returned effect ID can be used to play, set the position, size, etc. of the sequence frame effect using the interface in the effect/sequence frame. It is similar to the way to create the entity's sequence frame effect. | 
| [GetParticleEffectIdInBlockEntity](BlockEntity.md#getparticleeffectidinblockentity) | <span style="display:inline;color:#7575f9">Client</span> | Get the ID of the specified particle effect created in the custom block entity. There are two types of created effects: one is the effect defined by "netease_particle_effects" in the entity json file under resource_pack/entity/; the other is the effect created using the interface CreateParticleEffectForBlockEntity. The returned effect ID can be used to play, set the position, size, etc. of the particle effect using the interface in the effect/particle. It is similar to the way the particle effect is created for the entity. | 
| [RemoveFrameEffectInBlockEntity](BlockEntity.md#removeframeeffectinblockentity) | <span style="display:inline;color:#7575f9">Client</span> | Removes a sequence frame effect created on a custom block entity. The effect ID will be invalid after removal. | 
| [RemoveParticleEffectInBlockEntity](BlockEntity.md#removeparticleeffectinblockentity) | <span style="display:inline;color:#7575f9">Client</span> | Removes a particle effect created on a custom block entity. The effect ID will be invalid after removal. | 
| [SetBlockEntityMolangValue](BlockEntity.md#setblockentitymolangvalue) | <span style="display:inline;color:#7575f9">Client</span> | Sets the Molang variable of a custom block entity, which has the same function as the entity's molang variable. Currently, it is mainly used to control the animation state transition of a custom entity. The definition of Molang variables is the same as that of the original entity. For details, please refer to the tutorial document on custom block entity animation. | 
| [SetBlockTileEntityCustomData](BlockEntity.md#setblocktileentitycustomdata) | <span style="display:inline;color:#ff5555">Server</span> | Sets the custom data stored in the TileEntity bound to the special block (box, skull, furnace, flower pot, etc.) at the specified location. | 
| [SetEnableBlockEntityAnimations](BlockEntity.md#setenableblockentityanimations) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to enable the animation effect of the custom block entity. When enabled, the custom entity block will animate according to the animation state machine defined by animation_controller in the entity file. When disabled, all animation playback will be stopped. | 

### Block geometry model


| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CombineBlockBetweenPosToGeometry](Block Geometry Model.md#combineblockbetweenpostogeometry) | <span style="display:inline;color:#7575f9">Client</span> | According to the two input positions, search for all blocks between the two positions, and merge and convert these blocks into geometric models that can be used for entities. | 
| [CombineBlockFromPosListToGeometry](Block Geometry Model.md#combineblockfromposlisttogeometry) | <span style="display:inline;color:#7575f9">Client</span> | According to the input block position list, search for all blocks in these positions, and merge and convert these blocks into geometric models that can be used for entities. | 
| [CombineBlockPaletteToGeometry](BlockGeometryModel.md#combineblockpalettetogeometry) | <span style="display:inline;color:#7575f9">Client</span> | Combine all blocks in BlockPalette and convert them into a geometry model that can be used for entities. | 
| [EnableActorBlockGeometryTransparent](BlockGeometryModel.md#enableactorblockgeometrytransparent) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to allow entity block geometry models to generate transparency. If it is enabled, the block geometry model will become transparent by adjusting the transparency of the block geometry. | 
| [SetActorBlockGeometryOffset](BlockGeometryModel.md#setactorblockgeometryoffset) | <span style="display:inline;color:#7575f9">Client</span> | Sets the position offset of the entity's block geometry model. | 
| [SetActorBlockGeometryRotation](BlockGeometryModel.md#setactorblockgeometryrotation) | <span style="display:inline;color:#7575f9">Client</span> | Sets the rotation angle of the entity's block geometry model. | 
| [SetActorBlockGeometryTransparency](BlockGeometryModel.md#setactorblockgeometrytransparency) | <span style="display:inline;color:#7575f9">Client</span> | Sets the transparency of the entity's block geometry model. Note that this interface will only take effect after calling the interface EnableActorBlockGeometryTransparent to enable the transparency of the block geometry model. | 

### Block Palette 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [DeleteBlockInBlockPalette](Block Palette.md#deleteblockinblockpalette) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Delete a block of a certain type in the Block Palette BlockPalette. | 
| [DeserializeBlockPalette](BlockPalette.md#deserializeblockpalette) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Deserialize the data in the BlockPalette data dictionary, which is used to transmit the event data of the BlockPalette between the client and the server. | 
| [GetBlockCountInBlockPalette](BlockPalette.md#getblockcountinblockpalette) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Get the number of blocks of a certain type in the BlockPalette BlockPalette. | 
| [GetLocalPosListOfBlocks](BlocksPalette.md#getlocalposlistofblocks) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Get the relative position list of a block in the Block Palette. The Block Palette records a combination of blocks in a three-dimensional space, and the relative position refers to the relative position of the coordinate axis with the position of the block with the smallest coordinate among these blocks as the origin. | 
| [GetVolumeOfBlockPalette](BlockPalette.md#getvolumeofblockpalette) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Get the length, width and height of the cuboid occupied by the BlockPalette. The length refers to the length of the BlockPalette in the x-axis direction in the world coordinates, the width refers to the length of the BlockPalette in the z-axis direction, and the height refers to the length of the BlockPalette in the y-axis direction. | 
| [ReplaceAirByStructureVoid](BlockPalette.md#replaceairbystructurevoid) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Sets whether to replace all air in the BlockPalette with structure voids. | 
| [ReplaceBlockInBlockPalette](BlockPalette.md#replaceblockinblockpalette) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Replace a block of a certain type in the BlockPalette. | 
| [SerializeBlockPalette](BlockPalette.md#serializeblockpalette) | <span style="display:inline;color:#ff5555">Server</span><br><span style="display:inline;color:#7575f9">Client</span> | Serialize the data in the block palette, which is used to transmit the event data of the block palette between the client and the server. | 

### Rendering 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [ChangeBlockTextures](Rendering.md#changeblocktextures) | <span style="display:inline;color:#7575f9">Client</span> | Replace block texture | 
| [GetBlockTextures](Rendering.md#getblocktextures) | <span style="display:inline;color:#7575f9">Client</span> | Get the initial texture information of the block | 
| [SetBlockEntityFramePosOffset](Rendering.md#setblockentityframeposoffset) | <span style="display:inline;color:#7575f9">Client</span> | Set the offset value of the sequence frame special effect position in the custom block entity, which is used to adjust the offset of the sequence frame special effect relative to the block position. Unlike the special effect/sequence frame/SetPos interface, this interface adjusts the position offset value relative to the block position, not the world coordinates. | 
| [SetBlockEntityModelPosOffset](Rendering.md#setblockentitymodelposoffset) | <span style="display:inline;color:#7575f9">Client</span> | Set the entity model position offset value of the custom block entity, which is used to adjust the offset of the entity model relative to the block position. This interface can be used to adjust the position of the entity model of the custom block entity. It will only take effect if the entity model is defined by the custom block entity. The entity model is defined under resource_pack/entity/. For details, please refer to the teaching document of custom block entity animation. | 
| [SetBlockEntityModelRotation](Rendering.md#setblockentitymodelrotation) | <span style="display:inline;color:#7575f9">Client</span> | Set the rotation value of the entity model of the custom block entity on each axis. This interface can be used to adjust the rotation of the entity model of the custom block entity. This is only effective when the entity model is defined by the custom block entity. The entity model is defined under resource_pack/entity/. For details, please refer to the teaching document of custom block entity animation. | 
| [SetBlockEntityModelScale](Rendering.md#setblockentitymodelscale) | <span style="display:inline;color:#7575f9">Client</span> | Set the scale value of the entity model size of the custom block entity. This interface can be used to adjust the size of the entity model of the custom block entity. This is only effective when the entity model is defined by the custom block entity. The entity model is defined under resource_pack/entity/. For details, please refer to the teaching document of custom block entity animation. | 
| [SetBlockEntityParticlePosOffset](Rendering.md#setblockentityparticleposoffset) | <span style="display:inline;color:#7575f9">Client</span> | Sets the particle effect position offset value in the custom block entity, which is used to adjust the offset of the particle effect relative to the block position. Unlike the effect/particle/SetPos interface, this interface adjusts the position offset value relative to the block position, not the world coordinates. | 

### Container 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetChestBoxSize](Container.md#getchestboxsize) | <span style="display:inline;color:#ff5555">Server</span> | Get the capacity of the box | 
| [GetChestPairedPosition](Container.md#getchestpairedposition) | <span style="display:inline;color:#ff5555">Server</span> | Get the coordinates of box B that is combined with box A into a large box | 
| [GetContainerItem](Container.md#getcontaineritem) | <span style="display:inline;color:#ff5555">Server</span> | Get the items in the container | 
| [GetContainerSize](Container.md#getcontainersize) | <span style="display:inline;color:#ff5555">Server</span> | Get container capacity | 
| [GetEnderChestItem](Container.md#getenderchestitem) | <span style="display:inline;color:#ff5555">Server</span> | Get items in ender chest | 
| [GetInputSlotItem](Container.md#getinputslotitem) | <span style="display:inline;color:#ff5555">Server</span> | Get furnace input bar items, support the following parameters to clear specific slots: itemDict is empty, {}, or itemName is minecraft:air, or count is 0 | 
| [GetOpenContainerItem](Container.md#getopencontaineritem) | <span style="display:inline;color:#ff5555">Server</span> | Get the items in the open container | 
| [GetOutputSlotItem](Container.md#getoutputslotitem) | <span style="display:inline;color:#ff5555">Server</span> | Get the items in the furnace output bar | 
| [GetPlayerUIItem](Container.md#getplayeruiitem) | <span style="display:inline;color:#ff5555">Server</span> | Get the items in the synthesis container | 
| [SetChestBoxItemExchange](Container.md#setchestboxitemexchange) | <span style="display:inline;color:#ff5555">Server</span> | Exchange the slots of items in the box |

| [SetChestBoxItemNum](Container.md#setchestboxitemnum) | <span style="display:inline;color:#ff5555">Server</span> | Set the number of chest slot items | 
| [SetInputSlotItem](Container.md#setinputslotitem) | <span style="display:inline;color:#ff5555">Server</span> | Set the furnace input bar item | 
| [SetPlayerUIItem](Container.md#setplayeruiitem) | <span style="display:inline;color:#ff5555">Server</span> | Set the item for crafting container | 
| [SpawnItemToContainer](Container.md#spawnitemtocontainer) | <span style="display:inline;color:#ff5555">Server</span> | Spawn items to the inventory of the container block | 
| [SpawnItemToEnderChest](Container.md#spawnitemtoenderchest) | <span style="display:inline;color:#ff5555">Server</span> | Spawn items to ender chest | 

### Redstone 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetBlockPoweredState](Redstone.md#getblockpoweredstate) | <span style="display:inline;color:#ff5555">Server</span> | Get the power state of a block at a certain coordinate | 
| [GetStrength](Redstone.md#getstrength) | <span style="display:inline;color:#ff5555">Server</span> | Get the redstone signal strength at a certain coordinate | 

### Signboard 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetSignBlockText](告示牌.md#getsignblocktext) | <span style="display:inline;color:#ff5555">Server</span> | Get the text content of the sign (block) | 
| [SetSignBlockText](告示牌.md#setsignblocktext) | <span style="display:inline;color:#ff5555">Server</span> | Set the text content of the sign (block) | 

### Bed 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetBedColor](床.md#getbedcolor) | <span style="display:inline;color:#ff5555">Server</span> | Get the color of the bed (block) | 
| [SetBedColor](Bed.md#setbedcolor) | <span style="display:inline;color:#ff5555">Server</span> | Set the color of the bed (block) | 

### Properties 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetBlockBasicInfo](Property.md#getblockbasicinfo) | <span style="display:inline;color:#ff5555">Server</span> | Get basic information of the block | 
| [SetBlockBasicInfo](Property.md#setblockbasicinfo) | <span style="display:inline;color:#ff5555">Server</span> | Set basic information of the block | 

