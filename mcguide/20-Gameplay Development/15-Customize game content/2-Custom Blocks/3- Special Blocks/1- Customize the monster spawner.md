--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Custom spawner 

## base_block settings 

- **The base_block of the custom spawner block needs to be set to mob_spawner,** 
- **The following settings should also be made in blocks.json:** 

![special-3](.././picture/customblock/special-3.png) 

## netease:mob_spawner 

You can set the spawner type in the netease:mob_spawner component. Currently, native mobs and Microsoft custom mobs are supported. 

| Key | Type | Default | Explanation | 
| ---- | ------ | ------ | -------------------------------- | 
| type | string | | Required to control the type of creatures spawned | 

- The type of native creatures is "minecraft:Namespaced ID", such as "minecraft:parrot". For Namespaced ID, please refer to the detailed information of each Mob in the [official wiki](https://minecraft.gamepedia.com/Mob#List_of_mobs). 
- The type of Microsoft custom creatures is the "identifier" item of "description" in "minecraft:entity". Please refer to the customblocks_test_mobspawner1.json in the [Custom Creature Documentation](../../3-Custom Creatures/01-Custom Basic Creatures.md) and [CustomBlocksMod](../../../13-Module SDK Programming/60-Demo Example.md#CustomBlocksMod).