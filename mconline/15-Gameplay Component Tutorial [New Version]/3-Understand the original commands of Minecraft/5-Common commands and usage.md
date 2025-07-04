--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Advanced 
time: 20 minutes 
--- 
# Common commands and usage 

In this section, we introduce some of the most commonly used commands and how to use them. We introduce common commands from the perspectives of entities, worlds, chats, blocks, sound effects, and particles. 

## Entity commands 

### summon 

The `/summon` command can be used to summon a series of entities in the world. Its syntax is: 

```shell 
summon <entityType: EntityType> [spawnPos: x y z] [spawnEvent: string] [nameTag: string] 
``` 

- `entityType`: EntityType type, entity type, can be entity ID.
- `spawnPos`: x y z type, the spawn point, the spawn coordinates of the entity you want to summon. 
- `spawnEvent`: string type, the spawn event, the event triggered by the entity when it is spawned. 
- `nameTag`: string type, the name that the entity is born with. 

### scoreboard 

The `scoreboard` command is a command that can track values and perform mathematical operations on a per-entity basis, using a container called a **Scoreboard**. Scoreboards are very complex, and if you want to learn more, you can refer to the [Minecraft Wiki's Scoreboard page](https://minecraft.fandom.com/zh/wiki/%E8%AE%B0%E5%88%86%E6%9D%BF). 

### tag 

The `tag` command allows you to track tags on a per-entity basis. There are several subcommands: 

Add a tag to a target: 

```shell 
tag <entity: targets> add <name: string> 
``` 

Remove a tag from a target: 

```shell 
tag <entity: targets> remove <name: string> 
``` 

List all tags owned by a target: 

```shell 
tag <entity: targets> list 
```


## World Commands 

### time 

The `time` command can be used to adjust the world time. Its syntax is as follows: 

- `set` subcommand: 

```shell 
/time set <amount: int> 
/time set <time: TimeSpec> 
``` 

- `query` subcommand: 

```shell 
time query <daytime|gametime|day> 
``` 

- `add` subcommand: 

```shell 
time add <amount: int> 
``` 

The `set` subcommand is used to set the current time. The parameter immediately following it is the time value to be set or the `TimeSpec` enumeration value. The enumeration value can be `day`, `night`, `noon`, `midnight`, `sunrise`, and `sunset`. 

The `query` subcommand is used to query the time of day, game time, and day. 

The `add` subcommand is used to add a certain amount of time to the current time. 

### weather 

The `weather` command is used to adjust the weather. Its syntax is as follows: 

```shell 
/weather <clear|rain|thunder> [duration: int] 
``` 

The first literal parameter is the target to be adjusted: 

- `clear` represents sunny weather. 
- `rain` represents rain and snow. 
- `thunder` represents thunderstorms. 

The second optional parameter represents the duration of the state, in game ticks, where 20 game ticks equal 1 second. 

### gamemode 


The `gamemode` command can be used to change a player's game mode. Its syntax is as follows: 

```shell 
/gamemode <gameMode: GameMode> [player: target] 
/gamemode <gameMode: int> [player: target] 
``` 

As we can see, the first parameter is required and can be an integer representing the game mode or a `GameMode` enumeration value. Enumeration values can be `survival` (`s`) survival mode, `creative` (`c`) creative mode, `adventure` (`a`) adventure mode, and `default` (`d`) default game mode. 

The second parameter is optional. If not specified, the game mode of the player currently executing the command is changed by default. If a player is specified, the game mode of the specified player is changed. This parameter can be a player name or a target selector. 

### gamerule 

The `gamerule` command is used to update a **Game Rule**. There are a large number of game rules that control whether various events in the game should occur. We can use this command with the following syntax: 

```shell 
/gamerule <rule: BoolGameRule> [value: Boolean] 
/gamerule <rule: IntGameRule> [value: int] 
``` 

Game rules come in two forms, boolean game rules, which can only have values of `true` or `false`, and integer game rules, which can have values of integers. A complete list of game rules can be found on the [Minecraft Wiki Game Rules page](https://minecraft.fandom.com/zh/wiki/%E6%B8%B8%E6%88%8F%E8%A7%84%E5%88%99). 

## Chat Commands 

### tell 

The `tell` command is used to send a private message to one or more players. This command has two aliases, `msg` and `w`, which have the same effect as the original name. The format is as follows: 

```shell 
tell <target: target> <message: message> 
msg <target: target> <message: message> 
w <target: target> <message: message> 
``` 

The first parameter can be a player name or a target selector. You can select multiple players through the target selector. The second parameter is a message text, that is, the message you want to send. By using this command flexibly, you can send different exclusive messages to different players in the world. It is very useful to make some achievements and trading messages that are different for everyone. 

## Block Command 

### setblock 

The `setblock` command can place a specified block at the specified coordinates. 

```shell 
setblock <position: x y z> <tileName: Block> [tileData: int] [destroy|keep|replace] 
setblock <position: x y z> <tileName: Block> [blockStates: block states] [destroy|keep|replace] 
``` 

The last literal parameter can be used to select the following three modes: 

- `destroy`: destruction mode, the block at the original position will be simulated and destroyed, falling normally and playing the destruction sound effect. This mode is the default value.

- `keep`: keep mode, the block will be placed successfully only if the original position is air, otherwise the original block will be kept unchanged. 
- `replace`: replace mode, the original block disappears directly and is replaced by a new block, without being destroyed or falling. 

### fill 

The `fill` command is used to fill blocks in a rectangular area in batches, and its syntax is as follows: 

```shell 
fill <from: x y z> <to: x y z> <tileName: Block> [tileData: int] [oldBlockHandling: FillMode] 
fill <from: x y z> <to: x y z> <tileName: Block> [blockStates: block states] [oldBlockHandling: FillMode] 
``` 

In addition to the above three modes, the last `oldBlockHandling` enumeration parameter also supports the following two modes: 

- `hollow`: hollow mode, the outermost block of the area is changed to the specified block, and the interior is replaced with air.
- `outline`: Outline mode, changes the outermost block of the area to the specified block, and keeps the inside as it is. 

The default value of this parameter is `replace`. 

### clone 

The `clone` command is used to copy (clone) a terrain to another place, which is essentially a copy of a block. 

```shell 
clone <begin: x y z> <end: x y z> <destination: x y z> [maskMode: MaskMode] [cloneMode: CloneMode] 
clone <begin: x y z> <end: x y z> <destination: x y z> filtered <cloneMode: CloneMode> <tileName: Block> <blockStates: block states> 
clone <begin: x y z> <end: x y z> <destination: x y z> filtered <cloneMode: CloneMode> <tileName: Block> <tileData: int> 
``` 

The `maskMode` enumeration parameter can specify the mask mode, which has the following types: 

- `masked`: Performs a process similar to the "masked or" process in computers, even if the final result is to copy only non-air blocks, keeping the blocks in the destination area that would otherwise be replaced with air unchanged. 
- `replace`: Performs a pure replacement process, overwriting all blocks in the target area with blocks in the source area. This mode is the default. 
- `filtered`: Performs a filtering-like process so that the command only copies the specified blocks. It is essentially a mask mode, but requires an additional block to be specified with some parameters. 

The `cloneMode` enumeration parameter can specify the clone mode, which has the following three types: 

- `force`: Force cloning, even if the source and target areas overlap. 
- `move`: Move the clone and replace the source area with air. If the mask mode is `filtered`, only the specified cloned block positions will be replaced with air. 
- `noraml`: Normal cloning, no forcing or moving. This mode is the default. 

## Sound Effect Commands 

### playsound 

The `playsound` command is used to play a sound in the game. The syntax is as follows: 

```shell 
playsound <sound: string> [player: target] [position: x y z] [volume: float] [pitch: float] [minimumVolume: float] 
```


The `sound` parameter must specify a sound event defined in `sound_definitions.json`, such as `mob.fox.ambient`. 

## Particle Commands 

### particle 

The main function of the `particle` command is to generate an international version of the particle emitter in the game. 

```shell 
particle <effect: string> <position: x y z> 
``` 

The `effect` parameter is the ID of the particle emitter and must be namespaced. `position` is the initial coordinate of the particle emitter, and the emitter may change position later according to the configuration in its definition file.