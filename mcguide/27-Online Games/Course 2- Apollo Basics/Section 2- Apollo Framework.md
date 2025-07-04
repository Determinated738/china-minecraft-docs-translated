--- 
front: 
hard: Getting Started 
time: 15 minutes 
--- 

# Apollo Framework 
## Framework Introduction 
![](./images/apollo_framework.png) 

- **DB** is a global storage system shared by all game servers, which can be redis, mysql or mongodb, etc. Among them, redis is used to cache temporary data, such as player online status, online time of the day, etc., mysql and mongo are used to persist game data. Developers choose according to their needs. 
- **proxy** is a proxy server, whose functions include message encryption and decryption, message compression and decompression, login authentication and message forwarding. It maintains the connection between the client and the server. Developers cannot develop proxy. 
- **game** is a game server, which provides game logic functions. An online player only exists in one game or lobby. Developers develop gameplay on the game, such as implementing cool running games, shooting games, and fighting games. 
- **lobby** is a lobby server, which provides lobby functions. Developers develop lobby functions in the lobby, such as providing an entrance for NPC server selection and an entrance for combat dungeons. 
- **master** is a control server used to manage other servers. It is a single point for the entire server and provides http services to the outside world. The http service is the entry for operation commands (gm commands). Developers can develop operation commands in the master, such as issuing reward commands and banning speaking commands. The following introduces the master function through the requirements of the mute command: 
- Requirements: A player uses inappropriate words and needs to be banned from chatting. 
- Implementation: Add a mute command to the master. The developer uses http to send a mute request to the master. The master will record the mute information in the db, and then send a message to the player's server to ban the player from speaking. The next time the player logs in, the mute information is read from the db to determine whether it is still possible to chat. 
- **service** is a functional server used to provide distributed single-point services. Developers can develop guilds, all-server bosses, all-server matching and other functions in the service. The following introduces the service function through the full-server matching requirements: 
- Requirements: There are two lobby servers, lobby1 and lobby2. Players in the two lobby servers must be matched according to attributes such as level and combat power to enter the same copy game. 
- Implementation: When a player applies for matching, lobby1 or lobby2 applies for matching to the service. The service maintains a matching queue and records all matching players. The service will periodically take out the queue players and assign the matched players to the specified copy game according to the level and combat power matching method. 

## Usage example 

Introduce the use of the Apollo framework through a simple online game requirement. 
### Requirements 
Players can sign in in the lobby to receive rewards, and then experience two games: Bed Wars and Battle PVP. In addition, the game provides a mute command. Battle PVP requires a maximum of two players in a battle, and the player level difference is at most 2. 
### Implementation 

The following introduces what developers need to develop: 

- Master mod: Implement the mute command. The master receives the mute message and records it to mysql, and then notifies the player's server that the player is prohibited from chatting.
- Service mod: realizes full-server matching. Service maintains the matching queue, records all matching players, and then matches according to the player level, and assigns the two successfully matched players to the pvp server. 
- Game mod: realizes Bed Wars and PVP respectively; receives the master's mute message to prohibit players from chatting; logs in to read the player's data to determine whether to mute. 
- Lobby mod: 
- Provides a sign-in function, using mysql to record the player's items and sign-in reward time 
- Provides two NPCs, clicks on the NPC to enter the Bed Wars game or applies to the service for matching to enter PVP 
- Receives the master's mute message to prohibit players from chatting; logs in to read the player's data to determine whether to mute. 
### Function execution process 

Describes the functions completed by the engine (service opening tool framework) and the developer mod during the player's experience of the game. 

#### Sign-in process 
1. Players log in to the lobby: the engine will assign players to the lobby. 
2. Players receive sign-in rewards: the developer lobby mod completes the sign-in function. 
#### Muting process (assuming the player is in lobby1) 
1. The developer sends an http request to the master: the engine will receive the http request and then pass the request to the developer's master mod 
2. Ban players from chatting: the developer's master mod handles the muting message, and the developer's game/lobby mod implements the muting function

3. HTTP request returns: the developer master mod informs the engine of the execution result, and the engine returns the result to the request initiator 
#### Enter Bed Wars 
1. The player logs in and enters the lobby: the engine will assign the player to the lobby. 
2. Player clicks on NPC, and the player switches to the game of Bed Wars: the developer lobby mod implements NPC and server switching functions 
3. Experience Bed Wars: the developer game mod implements Bed Wars gameplay 
4. The game ends, and the player returns to the lobby: the developer game mod switches the player to the lobby 
#### Enter the battle pvp 
1. Player A and player B log in to the lobby: the engine will assign the players to the corresponding lobby 
2. Player A and player B click on NPC to apply for matching: the developer lobby mod applies for matching to the service, the developer service mod completes the matching, and assigns the player to the battle pvp game server 
4. Experience pvp battle: the developer game mod implements pvp battle gameplay 
4. The game ends, and the player returns to the lobby: the developer game mod switches the player to the lobby