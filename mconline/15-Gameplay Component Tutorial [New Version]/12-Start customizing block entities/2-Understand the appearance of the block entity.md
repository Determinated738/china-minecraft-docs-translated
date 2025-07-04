--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Advanced 
time: 15 minutes 
--- 
# Understanding the appearance of block entities 

After the behavior pack defines the components of the block entity, we can also define the client entity used by the block entity on the client. 

## Define the entity and its appearance 

We make a client entity definition file like the entity described in Chapter 8, including various resources of the entity, and then prepare it in the resource pack. In order to attach the entity to the block entity, we need to modify the `blocks.json` file in the root directory of the resource pack. 

```json 
{ 
"format_version": [ 1, 1, 0 ], 
///... 
"customblocks:custom_block_entity": { 
"sound": "grass", 
// Can be used with the netease_model field to define the block model of the block 
"netease_model": "customblocks:customblocks_model_decoration", 
// --- Entity model configuration --- 
// This block entity will use the entity model 
"client_entity": { 
// Corresponding to the identifier in custom_block_entity.entity.json 
"identifier": "customblocks:custom_block_entity", 
// Whether the holding model or the model when the block entity is dropped uses this entity model. 
"hand_model_use_client_entity": true, 
// The item icon texture of this block entity 
"block_icon": "test_block_icon", 
// Texture used when the block entity is destroyed 
"destoryed_textures":"destroy_entity" 
}, 
}, 
///... 
} 
``` 

This is an example of an entity attachment definition for a block entity. We can see that the `client_entity` field will be responsible for attaching the entity to the block. 

- `identifier`: string, the entity identifier, which needs to be consistent with the identifier in the entity's client definition. 
- `hand_model_use_client_entity`: optional, boolean value, whether the player's hand model and the model of the block's drops should use the entity model. If `false`, the entity model is used only when the block is placed in the world. In other cases (handheld and dropped), the model defined by `netease_model` or the original block shape is used. 
- `block_icon`: optional, string, the short name of the icon texture when the block is used as an item in the inventory. In fact, due to the game mechanism, the icon of the item cannot render an entity, so for blocks, only a flat icon, a Microsoft block shape, or a custom block model can be rendered. If it is not defined here, the block model defined by `netease_model` or the original block shape will be automatically rendered as the icon. The short name is defined in the texture atlas definition file `textures/terrain_texture.json` of the resource pack. 
- `destoryed_textures`: optional, string, the short name of the texture of the block destruction particle. When a block is destroyed, the `terrain` particles in the old version of particles (see Chapter 2 for an introduction) will be generated, and the `terrain` particles will select the texture from the specified UV in the terrain atlas of the block (see Chapter 10 for definition) as their map. Here, you can specify the texture UV of the generated `terrain` particles in disguise by changing the short name in the terrain atlas. If not defined, the existence of the texture defined in the `block_icon` field, the texture defined in the model defined in the `netease_model` field, and the texture defined in the `textures` field will be automatically detected in turn, and the first one detected will be used. The short name of this field is also defined in the texture atlas definition file `textures/terrain_texture.json` of the resource pack. 

So far, we have defined the entity corresponding to the block entity, and the various resources of the block entity, including the model, will be controlled by this entity, so that we can play more "patterns" with our blocks. 

## Connecting to the module SDK 


After the server-side entity definition of the block entity is completed, we have many more interfaces to connect to this entity. Unlike the interfaces in the previous section, the interfaces for the entity part of the block entity are all located on the client. This is also easy to understand, after all, this is an entity defined in the resource pack representing the client. 

| Interface | Belong to | Use | 
| ------------------------------------------------------------ | -------------------------------------------------------- | ---------------------------------------------- | 
| <a href="../../../mcdocs/1-ModAPI/接口/方块/创作.html#setblockentitymodelposoffset" rel="noopenner"> `SetBlockEntityModelPosOffset` </a> | <span style="display:inline;color:#7575f9">客户端</span> | Set the position offset of the entity model of the custom block entity. | 
| <a href="../../../mcdocs/1-ModAPI/接口/块/Rendering.html#setblockentitymodelrotation" rel="noopenner"> `SetBlockEntityModelRotation` </a> | <span style="display:inline;color:#7575f9">客户端</span> | Sets the rotation of the entity model of the custom block entity on each axis. | 
| <a href="../../../mcdocs/1-ModAPI/界面/块/Rendering.html#setblockentitymodelscale" rel="noopenner"> `SetBlockEntityModelScale` </a> | <span style="display:inline;color:#7575f9">客户端</span> | Sets the scale of the entity model of the custom block entity. | 
| <a href="../../../mcdocs/1-ModAPI/接口/块/Rendering.html#setenableblockentityanimations" rel="noopenner"> `SetEnableBlockEntityAnimations` </a> | <span style="display:inline;color:#7575f9">客户端</span> | Sets whether to enable animations for custom block entities. | 
| <a href="../../../mcdocs/1-ModAPI/界面/块/Rendering.html#setblockentitymolangvalue" rel="noopenner"> `SetBlockEntityMolangValue` </a> | <span style="display:inline;color:#7575f9">客户端</span> | Sets the value of the Molang variable of the custom block entity. | 
| <a href="../../../mcdocs/1-ModAPI/接口/块/Rendering.html#getblockentitymolangvalue" rel="noopenner"> `GetBlockEntityMolangValue` </a> | <span style="display:inline;color:#7575f9">Client</span> | Get the value of the Molang variable of a custom block entity. | 
