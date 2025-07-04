--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Overview of Custom Dimensions and Related Content 

## Concept of Dimension 

[Dimension](https://minecraft-zh.gamepedia.com/Dimension)(Dimension) is the name of the parallel world in Minecraft, including: the Main World, the Nether, the End, etc. 

## Dimension Classification 

### MC Built-in Dimensions 

As introduced in the official wiki, the current Bedrock Edition dimensions include the Main World, the Nether, and the End, and the corresponding *DimensionId* is 0~2. 

### MOD SDK Custom Dimensions 

#### Old Version Custom Dimensions 

When the official Identity V mod was launched, we expanded the built-in dimensions to 3~20, that is, 17 new custom dimensions were added. The custom dimensions used by existing developers are all selected from the dimensions between 3~20. 

#### New version of custom dimensions 

**Problem**: 

The old version of custom dimensions will cause a serious problem: **conflicts between custom dimension values used by developers**. The new solution is to increase the range of custom dimension settings [22~int maximum value). 

**Solution:** 

The larger the range of custom dimension ID values, the less likely it is that multiple mods will conflict. Therefore, a new custom dimension setting scheme has been added in the new version, [see details](./1-custom dimension.md#jump_to_custom_dimension). 

## Custom biome related 

In a custom biome, when setting the biome terrain, you need to specify the corresponding [custom dimension](./2-biome terrain.md#jump_to_terrant). This dimension setting can use the old version of the setting or the new version of the custom dimension method. 

