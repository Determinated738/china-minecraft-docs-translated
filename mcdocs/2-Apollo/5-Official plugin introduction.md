# Introduction to official plugins 

Official plugins are public mods. We recommend that server owners do secondary development based on official plugins to save their own development costs. 

This document is used to quickly understand the role of each official plugin. The specific functions of the plugin can be understood through the readme.txt file and mod.json file in each mod. 

The official plugins currently available can be obtained through the "Public Mod" page of the Bedrock Edition Network Server in MC Studio. 

![Plugin Download](./images/plugin_download.png) 

## Gameplay 
### Territory Plugin 
Supports setting a certain area as a player's exclusive territory. Non-territory owners will be restricted in permissions, such as not being able to destroy blocks, not being able to interact with entities, etc. This plugin is required to implement classic territory and home gameplay. 

### Block Version Territory Plugin 

Block Version Territory Plugin, the plugin functions are: 
1. You can set one area as a player's exclusive territory. Based on the needs of territory migration, it is currently required that only one zero-level territory can exist in a single map block 
2. After using this plugin, developers can set some rules in the territory, such as setting a list of usable blocks, a list of destructible blocks, whether other players can be harmed, etc. 
3. Support the creation of sub-territories 
4. Each territory can set territory permissions separately, and special permissions can be set for external players who are not owners 
5. Support simple client territory area preview and territory creation 
6. Support territory migration 

Plugin dependency: Map transfer database plugin (neteaseMapChunk): Territory migration requires this plugin support 

### Private box plugin 
This plugin supports setting the box as the player's exclusive box. Others need to apply for permissions to open it. It can be used in home and other gameplay. 
![Task plugin](./images/plugin_chest.png) 

### Battle system plugin 
When doing RPG gameplay, a more complex battle numerical system is generally created compared to the original game, and the equipment slots are expanded. The battle system plugin provides such functions. 
![Battle system](./images/plugin_battle.png) 

### Gem plugin 
The gem plugin implements the function of inlaying gems for equipment. The properties of gems can be ultimately added to the player through inlaying. You can refer to this plugin to implement other equipment training systems. 
![Gem system](./images/stone.png) 

### Random teleportation plugin 

Used for random teleportation across servers, across dimensions, and within this dimension. The plugin will automatically search for a safe landing nearby based on random parameters. 

### Turn-based battle plugin 

Realize conventional turn-based battles by specifying roles, attributes, skills, performance, and other content.


![Gem System](./images/round.png) 

## Game System 

### Announcement Plugin 
In the game, we need to pass the game information to the players in a timely manner. The announcement plugin provides three such capabilities: 
- **Mail**: Supports sending emails to players, which can be used for sending rewards, in-game notifications, and other purposes. 
![Mail](./images/plugin_mail.png) 
- **Login Popup**: When the player logs in, a panel will pop up, which can be used to display update announcements. 
![Login Popup](./images/plugin_login.png) 
- **Carousel Announcement**: A carousel message can be displayed on the interface of all players, which can be used for advanced reward announcements, limited-time gameplay opening announcements, and other functions. 
![Carousel](./images/plugin_announce.png) 

### Team Plugin 
Provides a general team function. If there is a gameplay that requires team formation in the network server, it is recommended to use this plugin.
Team plugin supports players to create teams and publish team recruitment information. Players can also send team applications by searching for teams. 
![Team plugin](./images/plugin_team.png) 

### Task plugin 
It provides a general task function, which is suitable for making guide tasks, main tasks, and side tasks, and can be used in various types of servers. 
In addition, the task plugin can use the data made by the dialogue and task components in the level editor. 
![Task plugin](./images/plugin_task.jpg) 

### Friend plugin 
It provides a general friend function, which can add friends through nearby players and search players, and can also automatically add platform friends as in-game friends. 
![Task plugin](./images/plugin_friend.png) 

### Guild plugin 
Guild (also called alliance, gang, community, family, etc.) is a very common social function in the game, which can effectively promote the interaction between players in the game. The guild plugin provides the function of creating and managing guilds. Server owners can develop more guild gameplay based on this. 
![Create a guild](./images/plugin_gang_create.png) 
![Apply to join a guild](./images/plugin_gang_apply.png) 
![Guild management](./images/plugin_gang_manage.png) 

### Economic plugin 
The economic plugin can define multiple virtual currencies, quick custom stores, and universal stall trading functions. 
![Economy plugin-shop](./images/plugin_economy_shop.png) 
![Economy plugin-shop](./images/plugin_economy_booth.png) 

### Main menu plugin 
This plugin supports conveniently adding function entry buttons in the main interface. Up to 16 buttons can be added, which can be collapsed and expanded through the collapse button. 
![Main Menu Plug-in](./images/plugin_mainmenu.png) 

### Speaker Plug-in 
This plug-in can display the speaker announcement content in the middle of the main interface. The appearance and content of the speaker can be customized. 
![Speaker Plug-in](./images/laba.png)


### Pop-up prompt plug-in 
In the main interface, you can set the position to display the pop-up prompt content. When the chat bar is not convenient to display the prompt information, you can use this plug-in instead. 
![Pop-up prompt plug-in](./images/toast.png) 

### Title plug-in 

You can add text or picture titles before, after or on the top of the title. The title can contain attributes (need to be used in conjunction with the battle plug-in). In addition, the plug-in can also be used as a title collection illustration to manage unlocked or unlocked titles. 

![Pop-up prompt plug-in](./images/chenghao.png) 

### Ranking list plug-in 

Supports basic operations of the ranking list, including adding, deleting, refreshing, and settlement. In addition, the ranking list also supports collecting data from the current server or all servers (game, lobby). This plug-in supports a single ranking list. For the usage of multiple ranking lists, please refer to "MCStudio-Bedrock Edition Network Server-Ranking List Template". 

![Popup prompt plugin](./images/paihangbang.png) 

### PVP plugin 

Can be used to filter the team, friends, and guilds of damage, record the killer and enemy, and control the kill drop. 

![Popup prompt plugin](./images/PVP01.png) 

![Popup prompt plugin](./images/PVP04.png) 

### Barrage plugin 

Support barrage display and sending functions, and can set barrage color and barrage avatar. 

![Popup prompt plugin](./images/danmu_01.png) 

### Panel description plugin 

Can set equipment and item panel descriptions in a certain format. Used with the combat plugin, the panel description takes effect in the backpack of the combat plugin. You can also use the interface to display the panel description in other locations. 

![Popup Tips Plugin](./images/itemtips.png) 

## Basic Functions 
### Map Properties Plugin 
This plugin can be used to manage the general properties of the map. Including the following main configurations: 
- Floating text on the map 
- Prohibit vine growth and fluid flow 
- Regularly clean up dropped objects 
- Map boundaries

- Drop and pick up item control 

### Cloud player information plug-in 
In the network server, sometimes it is necessary to synchronize the player's backpack information in different maps, such as the main city to the home, the main city to the RPG copy, etc. This plug-in is used to solve this problem. 

### Functional NPC plug-in 
This plug-in is still being improved, and currently provides a transfer NPC. 
Transfer NPC: After the player clicks the transfer NPC, a dialog box will pop up, and click "Confirm" to transfer to the corresponding server. 

### Permission management plug-in 
Currently, this plug-in is still in the process of improvement, and currently only supports setting chat prefixes for different groups of players. 

### Copy management plug-in 
When the server function is relatively complete, it is necessary to pay attention to performance issues. The copy management plug-in provides a solution for managing multiple copies of a single map, which can better optimize the server load problem. 
Use case: single novice copy, there are 20 novice copy areas in a map, and then 10 games are deployed. Then it supports 200 people playing novice copies at the same time. After using the copy management plug-in, novices will be automatically assigned to free copy areas. For example, if copy area 5 of the current 10th game server is free and copy area 1 of the 1st game server is free, then new players who want to enter the copy will be assigned to one of the two. When all copy areas are full, new players who enter later will appear in the queue interface. 

### Unique ID plug-in 
Used to generate a unique ID in the current network server. For example: the attributes of each piece of equipment are random, and you want an ID to mark each piece of equipment. In this case, you can use the unique ID plug-in. 

### Flight plug-in 

Used to turn on and off flight permissions, set flight conditions, consumption, and flyable areas. 

### Chat plug-in 

Provides local and world chat channels, and chat content supports hyperlinks. Used together with the friend and team plug-in, you can initiate private chats, add friends, team up, and other functions in the hyperlink of the chat bar. 

![Chat_Item Team](./images/chat_item1.png) 

![Chat_Stranger](./images/chat_mosheng.png) 

![Chat_Stranger1](./images/chat_mosheng1.png) 

### Chat History Plugin 

It can be used to record the chats of players in the original chat box and the chats of players in the local/world channels of the official chat plugin. And it provides operation instructions-supports multiple ways to retrieve chat records. 

### Face-to-face Trading Plugin 

It can be used for face-to-face trading of items and currencies between players. Used in conjunction with economic plugins and chat plugins, more powerful functions can be obtained. 

![Chat_Item Team](./images/mianduimianjiaoyi_1.png) 

![Chat_Item Team](./images/mianduimianjiaoyi_2.png) 

### Appearance Management Plugin 

Wardrobe function, can be used to preview and purchase appearance. Appearance includes: fashion, wings, aperture, mount, etc.


![Chat_Item Team](./images/waiguan4.png) 

![Chat_Item Team](./images/waiguan2.png) 

![Chat_Item Team](./images/waiguan3.png) 

### Registration and Matching Plugin 

Provides a complete registration and matching process. Matching supports individual and team registration. In addition to regular matching, the plugin also supports asymmetric confrontation matching. 

![Chat_Item Team](./images/match1.png) 

![Chat_Item Team](./images/match2.png) 

### General Input Interface Plugin 

Contains a general interface with a title, a text introduction, an input box and two buttons. The above text content and button jump logic support settings. Developers can easily use this function interface and obtain input content without paying too much attention to client logic. 

![Chat_Item Team](./images/chajian_input.png) 

### General Integrated Interface Plugin 

A general interface containing a title, a text introduction, and several buttons (the number can be customized). The above text content and button jump logic can be set. Developers can conveniently use this functional interface and specify the jump logic without paying too much attention to the client logic. 

![Chat_Item Team](./images/chajian_mixcommon.png) 

### General Display Interface Plugin 

A general interface containing a text box, and the content of the text box can be set. Developers can conveniently use this functional interface to display various text content without paying too much attention to the client logic. 

![Chat_Item Team](./images/chajian_text.png) 

### Data Transfer Plugin 

Simplify database operations; synchronize map data reading and writing to the database. 

### Map transfer database plug-in 

1. Adjust the target of the game's native map archive reading from the local file to the MySQL database 
2. Cooperate with the block version territory plug-in to realize the territory migration function 




## Activities and Operations 
### Activity Rewards Plugin 
Network servers often have rewards for completing activities: such as first-time recharge rewards, level-up rewards, accumulated points rewards, etc. 
The Activity Rewards Plugin provides a framework for rewarding general conditions for achievement. Server owners only need to modify the completion conditions to reuse it for different activity reward functions. 
![Activity Rewards Plugin](./images/plugin_activityreward.png) 

### Daily Login Rewards Plugin 
Giving players daily login rewards can promote player activity and improve player retention. This plugin provides a general daily login reward function. 
![Daily Login Rewards](./images/plugin_dailyreward.png) 

### Mall Plugin 
The Mall Plugin is used by server owners to more conveniently access the general diamond mall. This plugin can be used when the network server is ready to access commercial functions. 

### Operational data plug-in 
After the network service is launched, you need to check the number of players, retention, income and other data. At this time, you can use the operational data plug-in. This plug-in will record the operational data to the database, and you can view the visual data chart with Grafana. 

### Cumulative consumption activity plug-in 

During the event, if the cumulative consumption reaches a certain amount, you can get the corresponding reward. 

![Daily login reward](./images/plugin_activity_consum.png) 

### Scheduled instruction plug-in 

Can be used to execute operational instructions at a scheduled time. 

### Anti-cheat plug-in 
Anti-cheat plug-in is used to check some common cheating problems of players in the game: 

1. Introduce illegal block destruction monitoring function from Microsoft 
2. Introduce illegal movement monitoring function and rewind simulation function from Microsoft 
3. Monitor and discover memory modification type killing aura behavior 
4. Monitor and discover the use of grinding wheels, looms, stone cutters, forging tables to brush items, and introduce illegal enchantments 

### Operation record plug-in 

Records the player's regular placement, destruction, and killing behaviors, which can be used to roll back the blocks and creatures in the specified area: 

1. Record the player's normal operation of placing blocks

2. Record the player's normal operation to destroy blocks
3. Record the player's normal operation to kill creatures
4. Record the player's behavior of opening various boxes (except the ender box), and record the items in the box at this time
5. Record the player's behavior of closing various boxes (except the ender box), and record the items in the box at this time
6. Roll back the player's operation on the block in the specified area to the specified time point, and record the relevant operations

