--- 
front: https://nie.res.netease.com/r/pic/20220408/a5a602e2-e859-4a41-bf9b-3ada874fc9b7.png 
hard: Getting Started 
time: 5 minutes 
selection: true 
--- 
# Apollo Network Server Architecture 

## Comparison 

### Java Server 

Traditional Java servers generally refer to servers that use Spigot and other similar servers. Players can join the game using any client. This type of server is purely driven by the server. Without some special means, it is impossible to force the client to install some mods to enhance the gaming experience. 

### Apollo 

Apollo servers can not only use servers for driving like Java servers, but also synchronously send relevant Mods that match the server to the client, and use these Mods to communicate with the server in two directions to achieve effects such as opening the interface and playing animations after triggering an event. 

It should be noted that in Java servers, ProtocolLib or net.minecraft.server (NMS for short) is often used to bypass the Spigot API to implement various functions, such as scoreboards, titles, etc. In the development of Apollo, there are no similar protocol APIs available, but ModSDK can be used to implement more powerful client performance functions. For example, the scoreboard function can be implemented by making a Hud using ModSDK. Here, Java server plug-in developers need to understand and change their minds in advance. 

## Architecture 

![](./images/structure-1.png) 

As shown in the figure above, Apollo network server has 5 different types of servers, clients (Client) and databases (DB) 

### Server 

#### Proxy 

Proxy is a proxy server. All player connections will pass through the proxy server and then be distributed to each game server or lobby server. The function is similar to BungeeCord of Java server. However, the proxy server cannot install plug-ins like BungeeCord. 

#### Game 

Game is a game server, which provides players with a specific gameplay and is the main carrier of players. An online player can only exist in one Game or Lobby. 

#### Lobby 

Lobby is a lobby server, which is mainly used as a transit station between various gameplays. Players can choose the gameplay they want to play in the lobby server, and it provides the function of cross-server jump. The interface of the Lobby server is basically the same as that of the Game server. 

#### Service 

Service is a functional server, which is mainly used as the backend server of each Game/Lobby server. The Service server can be used to centrally process the data of some other servers. The Service server can actively/passively send data to each server, and other servers can also listen to the messages of the Service server and call callbacks to complete a series of responses. 

The cooperation between Service and Game is relatively important, and an example will be given below to introduce it. 

- GameA server created the Bed Wars gameplay. After the gameA server is started, it will notify the Service server to allow players to enter this server. 

- When there are enough players to start the game on the gameA server, gameA will start the game logic and notify the Service not to match new players to enter the server.


- After the game is over, gameA sends the player back to the lobby and resets the map. 

- After the map is reset, gameA notifies Service again that the server is ready for players to join. 

More communication-related content will be explained in the next section. 

#### Master 

The Master is the control server, which can be used to call administrator commands to complete a series of operation and maintenance operations. 

### Client 

The client is the player's terminal, and each player can be regarded as a Client. 

### Database 

The database is the carrier of the data mentioned above. For details, see [Concept of Database](../1-Preparation Knowledge/3-Concept of Database.html). 

