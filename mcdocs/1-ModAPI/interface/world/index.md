--- 
sidebarDepth: 1 
--- 
# Index 

--- 

- [Map](#Map) 
- [Entity Management](#Entity Management) 
- [Block Management](#Block Management) 
- [Mob Spawn](#Mob Spawn) 
- [Recipes](#Recipes) 
- [Block Combinations](#Block Combinations) 
- [Rendering](#Rendering) 
- [Time](#Time) 
- [Weather](#Weather) 
- [Game Rules](#Game Rules) 
- [Custom Data](#Custom Data) 
- [Commands](#Commands) 
- [Messages](#Messages) 

### Map 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CanSee](Map.md#cansee) | <span style="display:inline;color:#ff5555">Server</span> | Determine whether the starting object can see the target object, based on the object's Head position | 
| [CheckBlockToPos](Map.md#checkblocktopos) | <span style="display:inline;color:#ff5555">Server</span> | Determine whether there are blocks between positions | 
| [CheckChunkState](Map.md#checkchunkstate) | <span style="display:inline;color:#ff5555">Server</span> | Determine whether the chunk at the specified position has been loaded | 
| [CreateDimension](Map.md#createdimension) | <span style="display:inline;color:#ff5555">Server</span> | Create a new dimension | 
| [CreateExplosion](Map.md#createexplosion) | <span style="display:inline;color:#ff5555">Server</span> | Used to generate explosions | 
| [DeleteAllArea](Map.md#deleteallarea) | <span style="display:inline;color:#ff5555">Server</span> | Delete all constantly loading areas | 
| [DeleteArea](Map.md#deletearea) | <span style="display:inline;color:#ff5555">Server</span> | Delete a constantly loading area | 
| [DetectStructure](Map.md#detectstructure) | <span style="display:inline;color:#ff5555">Server</span> | Detect the structure of custom doors | 
| [GetAllAreaKeys](Map.md#getallareakeys) | <span style="display:inline;color:#ff5555">Server</span> | Get a list of all the names of the constantly loading areas | 
| [GetBiomeName](Map.md#getbiomename) | <span style="display:inline;color:#ff5555">Server</span> | Get the biome information of a certain location | 
| [GetBlockLightLevel](Map.md#getblocklightlevel) | <span style="display:inline;color:#ff5555">Server</span> | Get the light level of the block location | 
| [GetChunkEntites](Map.md#getchunkentites) | <span style="display:inline;color:#ff5555">Server</span> | Get a list of all entity and player IDs in the chunk at the specified location | 
| [GetChunkMaxPos](Map.md#getchunkmaxpos) | <span style="display:inline;color:#ff5555">Server</span> | Get the coordinates of the maximum point of a chunk | 
| [GetChunkMinPos](Map.md#getchunkminpos) | <span style="display:inline;color:#ff5555">Server</span> | Get the coordinates of the minimum point of a chunk | 
| [GetChunkMobNum](Map.md#getchunkmobnum) | <span style="display:inline;color:#ff5555">Server</span> | Get the number of mobs in a chunk (excluding players, but including armor stands) | 
| [GetChunkPosFromBlockPos](Map.md#getchunkposfromblockpos) | <span style="display:inline;color:#ff5555">Server</span> | Get the block coordinates of the chunk through the block coordinates | 
| [GetChunkPosFromBlockPos](Map.md#getchunkposfromblockpos) | <span style="display:inline;color:#7575f9">Client</span> | Get the block coordinates of the block through the block coordinates | 
| [GetCurrentDimension](Map.md#getcurrentdimension) | <span style="display:inline;color:#7575f9">Client</span> | Get the current dimension of the client | 
| [GetEntitiesAround](Map.md#getentitiesaround) | <span style="display:inline;color:#ff5555">Server</span> | Get the entity list in the area | 
| [GetEntitiesAroundByType](Map.md#getentitiesaroundbytype) | <span style="display:inline;color:#ff5555">Server</span> | Get a list of entities of a certain type in the area | 
| [GetEntitiesInSquareArea](Map.md#getentitiesinsquarearea) | <span style="display:inline;color:#ff5555">Server</span> | Get the entity list in the area | 
| [GetEntityInArea](Map.md#getentityinarea) | <span style="display:inline;color:#7575f9">Client</span> | Returns the entity in the area, and can get the list of entities loaded in the area | 
| [GetLevelId](Map.md#getlevelid) | <span style="display:inline;color:#ff5555">Server</span> | Get levelId. Some components require levelId to create, and this interface can be used to get levelId. The level is the game of the current map. | 
| [GetLevelId](Map.md#getlevelid) | <span style="display:inline;color:#7575f9">Client</span> | Get levelId. Some components need levelId to create, and this interface can be used to obtain levelId. The level is the game of the current map. | 
| [GetLoadedChunks](Map.md#getloadedchunks) | <span style="display:inline;color:#ff5555">Server</span> | Get the coordinate list of all blocks that have been loaded in the specified dimension |

| [GetSpawnDimension](Map.md#getspawndimension) | <span style="display:inline;color:#ff5555">Server</span> | Get the world spawn dimension | 
| [GetSpawnPosition](Map.md#getspawnposition) | <span style="display:inline;color:#ff5555">Server</span> | Get the world spawn point coordinates | 
| [IsChunkGenerated](Map.md#ischunkgenerated) | <span style="display:inline;color:#ff5555">Server</span> | Get whether a chunk has been generated. | 
| [IsSlimeChunk](Map.md#isslimechunk) | <span style="display:inline;color:#ff5555">Server</span> | Get whether a chunk is a slime chunk. | 
| [LocateNeteaseFeatureRule](地图.md#locateneteasefeaturerule) | <span style="display:inline;color:#ff5555">Server</span> | Similar to the [/locate command](https://minecraft-zh.gamepedia.com/%E5%91%BD%E4%BB%A4/locate), used to locate <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/4-Custom Dimensions/4-Custom Features.html#Feature Rules (feature-rules)">NetEase Custom Feature Rules</a> | 
| [LocateStructureFeature](地图.md#locatestructurefeature) | <span style="display:inline;color:#ff5555">Server</span> | Similar to the [/locate command](https://minecraft-zh.gamepedia.com/%E5%91%BD%E4%BB%A4/locate), it is used to locate some structures in the vanilla game, such as underwater temples and end cities. | 
| [MayPlace](Map.md#mayplace) | <span style="display:inline;color:#ff5555">Server</span> | Determine whether the block can be placed | 
| [MayPlaceOn](Map.md#mayplaceon) | <span style="display:inline;color:#ff5555">Server</span> | Determine whether the item can be placed at the specified location | 
| [MirrorDimension](Map.md#mirrordimension) | <span style="display:inline;color:#ff5555">Server</span> | Copy terrain of different dimensions | 
| [PlaceStructure](Map.md#placestructure) | <span style="display:inline;color:#ff5555">Server</span> | Place structure | 
| [SetAddArea](Map.md#setaddarea) | <span style="display:inline;color:#ff5555">Server</span> | Set the constant loading of the chunk | 
| [SetMergeSpawnItemRadius](Map.md#setmergespawnitemradius) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the newly generated items are stacked | 
| [SetSpawnDimensionAndPosition](Map.md#setspawndimensionandposition) | <span style="display:inline;color:#ff5555">Server</span> | Set the world spawn point dimension and coordinates | 
| [UpgradeMapDimensionVersion](Map.md#upgrademapdimensionversion) | <span style="display:inline;color:#ff5555">Server</span> | Upgrade the version number of the specified map dimension. If the version number does not match the dimension, the map archive information will be discarded. After use, the saved map versions will be upgraded to the latest version. If you want to use this interface to clean up the map archive of a specified dimension, you need to call it when the blocks of the dimension have not been loaded. | 

### Entity Management 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CreateEngineEntityByTypeStr](Entity Management.md#createengineentitybytypestr) | <span style="display:inline;color:#ff5555">Server</span> | Create an entity with the specified identifier | 
| [CreateEngineItemEntity](Entity Management.md#createengineitementity) | <span style="display:inline;color:#ff5555">Server</span> | Used to create an item entity (i.e., a drop), and return the entityId of the item entity | 
| [CreateExperienceOrb](Entity Management.md#createexperienceorb) | <span style="display:inline;color:#ff5555">Server</span> | Create an exclusive experience ball | 
| [CreateProjectileEntity](Entity Management.md#createprojectileentity) | <span style="display:inline;color:#ff5555">Server</span> | Create a projectile (direct launch) | 
| [DestroyEntity](Entity Management.md#destroyentity) | <span style="display:inline;color:#ff5555">Server</span> | Destroy the entity | 
| [GetDroppedItem](Entity Management.md#getdroppeditem) | <span style="display:inline;color:#ff5555">Server</span> | Get the item information of the dropped item | 
| [GetEngineActor](Entity Management.md#getengineactor) | <span style="display:inline;color:#ff5555">Server</span> | Get all entities (excluding players). | 
| [GetLocalPlayerId](Entity Management.md#getlocalplayerid) | <span style="display:inline;color:#7575f9">Client</span> | Get the local player's id | 
| [GetPlayerList](Entity Management.md#getplayerlist) | <span style="display:inline;color:#ff5555">Server</span> | Get the id list of all players in the level | 
| [HasEntity](Entity Management.md#hasentity) | <span style="display:inline;color:#7575f9">Client</span> | Determine whether entity exists | 
| [IsEntityAlive](Entity Management.md#isentityalive) | <span style="display:inline;color:#ff5555">Server</span> | Determine whether a biological entity is alive or a non-biological entity exists | 
| [IsEntityAlive](Entity Management.md#isentityalive) | <span style="display:inline;color:#7575f9">Client</span> | Determine whether a biological entity is alive or a non-biological entity exists | 
| [KillEntity](Entity Management.md#killentity) | <span style="display:inline;color:#ff5555">Server</span> | Kill an Entity | 
| [SpawnItemToLevel](Entity Management.md#spawnitemtolevel) | <span style="display:inline;color:#ff5555">Server</span> | Generate item drops. If you need to obtain the entityId of the item, you can call the server system interface CreateEngineItemEntity | 
| [SpawnLootTable](Entity Management.md#spawnloottable) | <span style="display:inline;color:#ff5555">Server</span> | Use the creature type to simulate a random drop. The generated items are related to the probability defined in json | 
| [SpawnLootTableWithActor](Entity Management.md#spawnloottablewithactor) | <span style="display:inline;color:#ff5555">Server</span> | Use the creature instance to simulate a random drop. The generated items are related to the probability defined in json | 
| [SpawnResources](Entity Management.md#spawnresources) | <span style="display:inline;color:#ff5555">Server</span> | Generate random drops of blocks (this method does not apply to entity blocks) | 
| [SpawnResourcesSilkTouched](Entity Management.md#spawnresourcessilktouched) | <span style="display:inline;color:#ff5555">Server</span> | Simulate accurate drop of blocks | 

### Block Management 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetBlock](Block Management.md#getblock) | <span style="display:inline;color:#7575f9">Client</span> | Get the block at a certain position | 
| [GetBlockClip](Block Management.md#getblockclip) | <span style="display:inline;color:#ff5555">Server</span> | Get the current <a href="../../../../mcguide/20-Gameplay Development/15-Custom Game Content/2-Custom Blocks/1-JSON Component.html#netease-aabb">clip's aabb</a> of a block at a certain position | 
| [GetBlockClip](Block Management.md#getblockclip) | <span style="display:inline;color:#7575f9">Client</span> | Get the aabb of the current clip of the block at the specified position | 
| [GetBlockCollision](Block Management.md#getblockcollision) | <span style="display:inline;color:#ff5555">Server</span> | Get the aabb of the current collision of the block at a certain position | 
| [GetBlockCollision](Block Management.md#getblockcollision) | <span style="display:inline;color:#7575f9">Client</span> | Get the aabb of the current collision of the block at the specified position | 
| [GetBlockNew](Block Management.md#getblocknew) | <span style="display:inline;color:#ff5555">Server</span> | Get the block at a certain position | 
| [GetDestroyTotalTime](Block Management.md#getdestroytotaltime) | <span style="display:inline;color:#ff5555">Server</span> | Get the time required to destroy blocks using items | 
| [GetDestroyTotalTime](Block Management.md#getdestroytotaltime) | <span style="display:inline;color:#7575f9">Client</span> | Get the time required to destroy blocks using items |

| [GetLiquidBlock](Block Management.md#getliquidblock) | <span style="display:inline;color:#ff5555">Server</span> | Get the fluid information interface of a block at a certain location | 
| [GetTopBlockHeight](Block Management.md#gettopblockheight) | <span style="display:inline;color:#ff5555">Server</span> | Get the height of the highest non-air block at a certain location | 
| [GetTopBlockHeight](Block Management.md#gettopblockheight) | <span style="display:inline;color:#7575f9">Client</span> | Get the height of the highest non-air block at a certain location in the current dimension | 
| [SetBlockNew](Block Management.md#setblocknew) | <span style="display:inline;color:#ff5555">Server</span> | Set the block at a certain position | 
| [SetLiquidBlock](Block Management.md#setliquidblock) | <span style="display:inline;color:#ff5555">Server</span> | Set the extraBlock of the block at a certain position, where you can set the water content of the block, etc. | 
| [SetSnowBlock](Block Management.md#setsnowblock) | <span style="display:inline;color:#ff5555">Server</span> | Set the snow content of the block at a certain position | 

### Mob Spawn 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetEntityLimit](Mob Spawn.md#getentitylimit) | <span style="display:inline;color:#ff5555">Server</span> | Get the maximum number of entities that can be generated in the world. See [SetEntityLimit](Mob Spawn.md#setentitylimit) for the meaning of spawnable entities | 
| [SetEntityLimit](Mob Spawn.md#setentitylimit) | <span style="display:inline;color:#ff5555">Server</span> | Sets the maximum number of spawnable entities in the world. Spawnable entities are entities with spawnrules. When the number of spawnable entities currently loaded in the world exceeds this limit, mobs will no longer spawn through spawnrules. | 
| [SpawnCustomModule](Creature Spawn.md#spawncustommodule) | <span style="display:inline;color:#ff5555">Server</span> | Set custom spawners | 

### Recipes 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddBrewingRecipes](Recipes.md#addbrewingrecipes) | <span style="display:inline;color:#ff5555">Server</span> | Add brewing stand recipe interface | 
| [GetRecipeResult](Recipes.md#getreciperesult) | <span style="display:inline;color:#ff5555">Server</span> | Get recipe result based on recipe id. Only supports crafting recipes | 
| [GetRecipesByInput](recipes.md#getrecipesbyinput) | <span style="display:inline;color:#ff5555">Server</span> | Query recipes by input items | 
| [GetRecipesByInput](recipes.md#getrecipesbyinput) | <span style="display:inline;color:#7575f9">Client</span> | Query recipes by input items | 
| [GetRecipesByResult](recipes.md#getrecipesbyresult) | <span style="display:inline;color:#ff5555">Server</span> | Query the input materials required for a recipe by output items | 
| [GetRecipesByResult](recipes.md#getrecipesbyresult) | <span style="display:inline;color:#7575f9">Client</span> | Query the input materials required for the recipe through the output items | 

### Block combination 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CreateMicroBlockResStr](Block combination.md#createmicroblockresstr) | <span style="display:inline;color:#ff5555">Server</span> | Generate a microblock resource Json string | 
| [GetBlankBlockPalette](Block combination.md#getblankblockpalette) | <span style="display:inline;color:#ff5555">Server</span> | Get a blank block palette. | 
| [GetBlankBlockPalette](Block combination.md#getblankblockpalette) | <span style="display:inline;color:#7575f9">Client</span> | Get a blank block palette. | 
| [GetBlockPaletteBetweenPos](Block combination.md#getblockpalettebetweenpos) | <span style="display:inline;color:#ff5555">Server</span> | Create and get a block palette based on the two input block positions. The block palette is used to describe and record the combination of multiple blocks in the world. This block palette contains all the blocks between the two positions and their relative positions. | 
| [GetBlockPaletteBetweenPos](Block Combination.md#getblockpalettebetweenpos) | <span style="display:inline;color:#7575f9">Client</span> | Create and get a block palette based on the two input positions. This interface will search for all blocks between the two positions to create a block palette. The block palette is used to describe and record the combination of multiple blocks in the world. This block palette contains all blocks between the two positions and their relative positions. | 
| [GetBlockPaletteFromPosList](Block Combination.md#getblockpalettefromposlist) | <span style="display:inline;color:#ff5555">Server</span> | Create and get a block palette based on the input block position list. The block palette is used to describe and record the combination of multiple blocks in the world. The created block palette contains all blocks in this position list and their relative positions. | 
| [GetBlockPaletteFromPosList](Block Combination.md#getblockpalettefromposlist) | <span style="display:inline;color:#7575f9">Client</span> | Create and get a block palette based on the input block position list. The block palette is used to describe and record the combination of multiple blocks in the world. The created block palette contains all the blocks in this position list and their relative positions. | 
| [RegisterBlockPatterns](Block combination.md#registerblockpatterns) | <span style="display:inline;color:#ff5555">Server</span> | Register special block combination | 
| [SetBlockByBlockPalette](Block combination.md#setblockbyblockpalette) | <span style="display:inline;color:#ff5555">Server</span> | According to the input block palette content, set all blocks recorded in the palette to actual blocks. | 

### Rendering 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetAmbientBrightness](Rendering.md#getambientbrightness) | <span style="display:inline;color:#7575f9">Client</span> | Get ambient light brightness, affects sky brightness, does not affect entity and block lighting | 
| [GetFogColor](Rendering.md#getfogcolor) | <span style="display:inline;color:#7575f9">Client</span> | Get current fog effect color | 
| [GetFogLength](Rendering.md#getfoglength) | <span style="display:inline;color:#7575f9">Client</span> | Get fog effect range | 
| [GetMoonRot](rendering.md#getmoonrot) | <span style="display:inline;color:#7575f9">Client</span> | Get the moon angle | 
| [GetSkyColor](rendering.md#getskycolor) | <span style="display:inline;color:#7575f9">Client</span> | Get the sky color | 
| [GetSkyTextures](rendering.md#getskytextures) | <span style="display:inline;color:#7575f9">Client</span> | Get the current dimension skybox texture, the skybox has 6 textures in total |

| [GetStarBrightness](rendering.md#getstarbrightness) | <span style="display:inline;color:#7575f9">Client</span> | Get star brightness | 
| [GetSunRot](rendering.md#getsunrot) | <span style="display:inline;color:#7575f9">Client</span> | Get the sun angle | 
| [GetUseAmbientBrightness](rendering.md#getuseambientbrightness) | <span style="display:inline;color:#7575f9">Client</span> | Determine whether the ambient light brightness is set in the mod | 
| [GetUseFogColor](rendering.md#getusefogcolor) | <span style="display:inline;color:#7575f9">Client</span> | Determine whether the fog effect color is currently enabled. The default value is False. It is True after using the color value passed in by the mod | 
| [GetUseFogLength](rendering.md#getusefoglength) | <span style="display:inline;color:#7575f9">Client</span> | Determine whether the fog effect range is currently enabled. The default value is False. It is True after using the range value passed in by the mod | 
| [GetUseMoonRot](rendering.md#getusemoonrot) | <span style="display:inline;color:#7575f9">Client</span> | Determine whether the moon angle is set in the mod | 
| [GetUseSkyColor](rendering.md#getuseskycolor) | <span style="display:inline;color:#7575f9">Client</span> | Determine whether the sky color is set in the mod | 
| [GetUseStarBrightness](rendering.md#getusestarbrightness) | <span style="display:inline;color:#7575f9">Client</span> | Determine whether the star brightness is set in the mod | 
| [GetUseSunRot](rendering.md#getusesunrot) | <span style="display:inline;color:#7575f9">Client</span> | Determine whether the sun angle is set in the mod | 
| [HideNameTag](rendering.md#hidenametag) | <span style="display:inline;color:#7575f9">Client</span> | Hide all name displays in the scene, including player names, custom names of creatures, floating text of item display frames and command blocks, etc. | 
| [ResetAmbientBrightness](rendering.md#resetambientbrightness) | <span style="display:inline;color:#7575f9">Client</span> | Reset ambient light brightness | 
| [ResetFogColor](rendering.md#resetfogcolor) | <span style="display:inline;color:#7575f9">Client</span> | Reset fog color | 
| [ResetFogLength](rendering.md#resetfoglength) | <span style="display:inline;color:#7575f9">Client</span> | Reset fog range | 
| [ResetMoonRot](rendering.md#resetmoonrot) | <span style="display:inline;color:#7575f9">Client</span> | Reset moon angle | 
| [ResetSkyColor](rendering.md#resetskycolor) | <span style="display:inline;color:#7575f9">Client</span> | Reset Sky Color | 
| [ResetSkyTextures](Rendering.md#resetskytextures) | <span style="display:inline;color:#7575f9">Client</span> | Reset the current dimension skybox texture. If you use addon to configure the texture, the configured texture will be used, otherwise the game will default to no texture | 
| [ResetStarBrightness](rendering.md#resetstarbrightness) | <span style="display:inline;color:#7575f9">Client</span> | Reset star brightness | 
| [ResetSunRot](rendering.md#resetsunrot) | <span style="display:inline;color:#7575f9">Client</span> | Reset sun angle | 
| [SetAmbientBrightness](rendering.md#setambientbrightness) | <span style="display:inline;color:#7575f9">Client</span> | Set ambient light brightness, affects sky brightness, does not affect entity and block lighting | 
| [SetFogColor](rendering.md#setfogcolor) | <span style="display:inline;color:#7575f9">Client</span> | Set fog effect color | 
| [SetFogLength](rendering.md#setfoglength) | <span style="display:inline;color:#7575f9">Client</span> | Set fog effect range | 
| [SetMoonRot](rendering.md#setmoonrot) | <span style="display:inline;color:#7575f9">Client</span> | Set the angle of the moon | 
| [SetSkyColor](rendering.md#setskycolor) | <span style="display:inline;color:#7575f9">Client</span> | Set the sky color | 
| [SetSkyTextures](rendering.md#setskytextures) | <span style="display:inline;color:#7575f9">Client</span> | Set the current dimension skybox texture. The skybox needs 6 textures. | 
| [SetStarBrightness](rendering.md#setstarbrightness) | <span style="display:inline;color:#7575f9">Client</span> | Set the star brightness. Stars can also be displayed during the day. | 
| [SetSunRot](rendering.md#setsunrot) | <span style="display:inline;color:#7575f9">Client</span> | Set the angle of the sun. | 
| [SkyTextures](rendering.md#skytextures) | <span style="display:inline;color:#7575f9">Client</span> | Modify the textures of the sun, moon, cloud distribution, and skybox. Use addon configuration, non-python interface. | 

### Time 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetLocalDoDayNightCycle](time.md#getlocaldodaynightcycle) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the dimension has day and night cycles turned on | 
| [GetLocalTime](time.md#getlocaltime) | <span style="display:inline;color:#ff5555">Server</span> | Get the time of the dimension | 
| [GetTime](time.md#gettime) | <span style="display:inline;color:#ff5555">Server</span> | Get the current world time | 
| [GetUseLocalTime](time.md#getuselocaltime) | <span style="display:inline;color:#ff5555">Server</span> | Get whether a dimension is set to use local time rules | 
| [SetLocalDoDayNightCycle](time.md#setlocaldodaynightcycle) | <span style="display:inline;color:#ff5555">Server</span> | Set whether the dimension using local time rules turns on day and night rotation | 
| [SetLocalTime](time.md#setlocaltime) | <span style="display:inline;color:#ff5555">Server</span> | Set the time of the dimension using local time rules | 
| [SetLocalTimeOfDay](time.md#setlocaltimeofday) | <span style="display:inline;color:#ff5555">Server</span> | Set the time of the dimension using local time rules in a day | 
| [SetTime](time.md#settime) | <span style="display:inline;color:#ff5555">Server</span> | Set the current world time | 
| [SetTimeOfDay](time.md#settimeofday) | <span style="display:inline;color:#ff5555">Server</span> | Set the time of the current world in a day | 
| [SetUseLocalTime](time.md#setuselocaltime) | <span style="display:inline;color:#ff5555">Server</span> | Allow a dimension to have its own local time rules. After turning it on, the dimension can have different time and day and night rules from other dimensions | 

### Weather 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetDimensionLocalWeatherInfo](weather.md#getdimensionlocalweatherinfo) | <span style="display:inline;color:#ff5555">Server</span> | Get independent dimension weather information (must first use SetDimensionUseLocalWeather interface to set this dimension to have its own independent weather) | 
| [GetDimensionUseLocalWeather](Weather.md#getdimensionuselocalweather) | <span style="display:inline;color:#ff5555">Server</span> | Get whether a dimension has its own weather rules | 
| [IsRaining](Weather.md#israining) | <span style="display:inline;color:#ff5555">Server</span> | Get whether it is raining |

| [IsThunder](Weather.md#isthunder) | <span style="display:inline;color:#ff5555">Server</span> | Get whether it is thundering | 
| [SetDimensionLocalDoWeatherCycle](Weather.md#setdimensionlocaldoweathercycle) | <span style="display:inline;color:#ff5555">Server</span> | Set whether to open the weather cycle for a certain dimension (must first use the SetDimensionUseLocalWeather interface to set this dimension to have its own independent weather) | 
| [SetDimensionLocalRain](Weather.md#setdimensionlocalrain) | <span style="display:inline;color:#ff5555">Server</span> | Set a certain dimension to rain (must first use the SetDimensionUseLocalWeather interface to set this dimension to have its own independent weather) | 
| [SetDimensionLocalThunder](Weather.md#setdimensionlocalthunder) | <span style="display:inline;color:#ff5555">Server</span> | Set a dimension to have thunder (must first use the SetDimensionUseLocalWeather interface to set this dimension to have its own independent weather) | 
| [SetDimensionUseLocalWeather](Weather.md#setdimensionuselocalweather) | <span style="display:inline;color:#ff5555">Server</span> | Set a dimension to have its own weather rules. After turning it on, the dimension can have different weather and weather change rules from other dimensions | 
| [SetRaining](Weather.md#setraining) | <span style="display:inline;color:#ff5555">Server</span> | Set whether it rains | 
| [SetThunder](Weather.md#setthunder) | <span style="display:inline;color:#ff5555">Server</span> | Set whether it thunders | 

### Game rules 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [AddBannedItem](Game rules.md#addbanneditem) | <span style="display:inline;color:#ff5555">Server</span> | Add banned items | 
| [AddBlockProtectField](Game rules.md#addblockprotectfield) | <span style="display:inline;color:#ff5555">Apollo</span> | Set a block area that cannot be destroyed by players/entities | 
| [CleanBlockProtectField](Game rules.md#cleanblockprotectfield) | <span style="display:inline;color:#ff5555">Apollo</span> | Cancel all blocks that cannot be destroyed by players/entities | 
| [ClearBannedItems](GameRule.md#clearbanneditems) | <span style="display:inline;color:#ff5555">Server</span> | Clear banned items | 
| [DisableVineBlockSpread](GameRule.md#disablevineblockspread) | <span style="display:inline;color:#ff5555">Server</span> | Set whether to disable vine spreading | 
| [ForbidLiquidFlow](GameRule.md#forbidliquidflow) | <span style="display:inline;color:#ff5555">Server</span> | Forbid/allow fluid flow in the map | 
| [GetBannedItemList](GameRule.md#getbanneditemlist) | <span style="display:inline;color:#ff5555">Server</span> | Get banned item list | 
| [GetGameDiffculty](Game rules.md#getgamediffculty) | <span style="display:inline;color:#ff5555">Server</span> | Get game difficulty | 
| [GetGameRulesInfoServer](Game rules.md#getgamerulesinfoserver) | <span style="display:inline;color:#ff5555">Server</span> | Get game rules | 
| [GetGameType](Game rules.md#getgametype) | <span style="display:inline;color:#ff5555">Server</span> | Get default game mode | 
| [GetLevelGravity](Game rules.md#getlevelgravity) | <span style="display:inline;color:#ff5555">Server</span> | Get gravity factor | 
| [GetSeed](Game rules.md#getseed) | <span style="display:inline;color:#ff5555">Server</span> | Get the archive seed | 
| [IsDisableCommandMinecart](Game rules.md#isdisablecommandminecart) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the command block minecart built-in logic instructions are currently allowed to run. Currently only Apollo network server is available | 
| [IsLockDifficulty](Game rules.md#islockdifficulty) | <span style="display:inline;color:#ff5555">Server</span> | Get whether the game difficulty of the current world is locked | 
| [LockDifficulty](Game rules.md#lockdifficulty) | <span style="display:inline;color:#ff5555">Server</span> | Lock the game difficulty of the current world (valid only for this game). After locking, no player can modify the game difficulty through commands or pause menu in the game | 
| [OpenCityProtect](Game Rules.md#opencityprotect) | <span style="display:inline;color:#ff5555">Apollo</span> | Enable city protection, including prohibiting the destruction of blocks, prohibiting the use of items on blocks, prohibiting monsters from attacking players, prohibiting players from attacking each other, prohibiting day and night switching, prohibiting weather changes, and prohibiting monster group refreshes | 
| [RemoveBannedItem](Game Rules.md#removebanneditem) | <span style="display:inline;color:#ff5555">Server</span> | Remove banned items | 
| [RemoveBlockProtectField](Game Rules.md#removeblockprotectfield) | <span style="display:inline;color:#ff5555">Apollo</span> | Cancels a block that cannot be destroyed by players/entities | 
| [SetCanActorSetOnFireByLightning](GameRules.md#setcanactorsetonfirebylightning) | <span style="display:inline;color:#ff5555">Server</span> | Disable/allow lightning to ignite entities | 
| [SetCanBlockSetOnFireByLightning](GameRules.md#setcanblocksetonfirebylightning) | <span style="display:inline;color:#ff5555">Server</span> | Disable/allow lightning to ignite blocks | 
| [SetDefaultGameType](GameRules.md#setdefaultgametype) | <span style="display:inline;color:#ff5555">Server</span> | Set the default game mode | 
| [SetDisableCommandMinecart](GameRules.md#setdisablecommandminecart) | <span style="display:inline;color:#ff5555">Server</span> | Set to stop/start running command block minecart built-in logic instructions, currently only available in Apollo network server | 
| [SetDisableContainers](Game rules.md#setdisablecontainers) | <span style="display:inline;color:#ff5555">Server</span> | Disable opening of all container interfaces, including player backpacks, various container blocks containing backpack interfaces such as workbenches and boxes, and entity interactions containing backpack interfaces such as horse backpacks and villager trading | 
| [SetDisableDropItem](Game rules.md#setdisabledropitem) | <span style="display:inline;color:#ff5555">Server</span> | Set to prohibit dropping items | 
| [SetDisableGravityInLiquid](Game rules.md#setdisablegravityinliquid) | <span style="display:inline;color:#ff5555">Server</span> | Whether to block the gravity of all entities in liquids (water, magma) | 
| [SetDisableHunger](GameRule.md#setdisablehunger) | <span style="display:inline;color:#ff5555">Server</span> | Set whether to block hunger | 
| [SetGameDifficulty](GameRule.md#setgamedifficulty) | <span style="display:inline;color:#ff5555">Server</span> | Set game difficulty | 
| [SetGameRulesInfoServer](GameRule.md#setgamerulesinfoserver) | <span style="display:inline;color:#ff5555">Server</span> | Set game rules. All parameters are optional. | 
| [SetHurtCD](GameRule.md#sethurtcd) | <span style="display:inline;color:#ff5555">Server</span> | Set the damage CD | 
| [SetLevelGravity](GameRule.md#setlevelgravity) | <span style="display:inline;color:#ff5555">Server</span> | Set the gravity factor | 

### Custom Data 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CleanExtraData](CustomData.md#cleanextradata) | <span style="display:inline;color:#ff5555">Server</span> | Clear the custom data of the entity or the world. When clearing entity data, use the corresponding entity id to create a component. When clearing world data, use levelId to create a component | 
| [GetExtraData](Custom data.md#getextradata) | <span style="display:inline;color:#ff5555">Server</span> | Get the custom data of the entity or the custom data of the world, the value corresponding to a key. When getting entity data, use the corresponding entity id to create a component, and when getting world data, use levelId to create a component. | 
| [GetWholeExtraData](Custom data.md#getwholeextradata) | <span style="display:inline;color:#ff5555">Server</span> | Get the complete entity's custom data or the custom data of the world. When getting entity data, use the corresponding entity id to create a component, and when getting world data, use levelId to create a component. |

| [SaveExtraData](CustomData.md#saveextradata) | <span style="display:inline;color:#ff5555">Server</span> | Used to save entity custom data or world custom data | 
| [SetExtraData](CustomData.md#setextradata) | <span style="display:inline;color:#ff5555">Server</span> | Used to set entity custom data or world custom data, data is saved in the form of key-value pairs. When setting entity data, use the corresponding entity id to create a component. When setting world data, use levelId to create a component. | 

### Commands 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [GetCommandPermissionLevel](command.md#getcommandpermissionlevel) | <span style="display:inline;color:#ff5555">Server</span> | Returns the OP permission level when using the /op command (corresponding to the op-permission-level configuration in server.properties) | 
| [GetDefaultPlayerPermissionLevel](command.md#getdefaultplayerpermissionlevel) | <span style="display:inline;color:#ff5555">Server</span> | Returns the permission identity when a new player joins (corresponding to the default-player-permission-level configuration in server.properties) | 
| [SetCommand](command.md#setcommand) | <span style="display:inline;color:#ff5555">Server</span> | Use in-game commands | 
| [SetCommandPermissionLevel](command.md#setcommandpermissionlevel) | <span style="display:inline;color:#ff5555">Server</span> | Set the OP permission level when the player uses the /op command (corresponding to the op-permission-level configuration in server.properties) | 
| [SetDefaultPlayerPermissionLevel](command.md#setdefaultplayerpermissionlevel) | <span style="display:inline;color:#ff5555">Server</span> | Set the permission identity when a new player joins (corresponding to the default-player-permission-level configuration in server.properties) | 

### Message 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [NotifyOneMessage](Message.md#notifyonemessage) | <span style="display:inline;color:#ff5555">Server</span> | Send a chat message to a specified player | 
| [SendMsg](Message.md#sendmsg) | <span style="display:inline;color:#ff5555">Server</span> | Simulate a player sending a chat message to everyone | 
| [SendMsgToPlayer](Message.md#sendmsgtoplayer) | <span style="display:inline;color:#ff5555">Server</span> | Simulate a player sending a chat message to another player | 
| [SetLeftCornerNotify](Message.md#setleftcornernotify) | <span style="display:inline;color:#7575f9">Client</span> | Set the notification information in the upper left corner of the client | 
| [SetNotifyMsg](Message.md#setnotifymsg) | <span style="display:inline;color:#ff5555">Server</span> | Set the message notification | 
| [SetOnePopupNotice](Message.md#setonepopupnotice) | <span style="display:inline;color:#ff5555">Server</span> | Pop up a popup type notification above a specific player's inventory, located below the tip type message. For this function, it is recommended that the client use the corresponding interface SetPopupNotice of the game component | 
| [SetOneTipMessage](Message.md#setonetipmessage) | <span style="display:inline;color:#ff5555">Server</span> | Pop up a tip notification above a specific player's inventory, located above the popup notification. For this function, it is recommended to use the corresponding interface SetTipMessage of the game component on the client | 
| [SetPopupNotice](Message.md#setpopupnotice) | <span style="display:inline;color:#ff5555">Server</span> | Pop up a popup notification above all players' inventory, located below the tip message | 
| [SetPopupNotice](Message.md#setpopupnotice) | <span style="display:inline;color:#7575f9">Client</span> | Pop up a popup notification above the local player's inventory, located below the tip message | 
| [SetTipMessage](Message.md#settipmessage) | <span style="display:inline;color:#ff5555">Server</span> | Pop up a tip notification above all players' inventory, located above the popup notification | 
| [SetTipMessage](message.md#settipmessage) | <span style="display:inline;color:#7575f9">Client</span> | Pop up a tip notification above the local player's inventory, located above the popup notification | 

