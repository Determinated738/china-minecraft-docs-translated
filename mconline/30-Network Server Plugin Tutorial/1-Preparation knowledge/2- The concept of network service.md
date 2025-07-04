# Concept of Network Server 

## Introduction 

Network server is a game server running on a remote server, which is connected to players through the network. 

Every network game needs a dedicated server to calculate the internal data of the game, and send the calculation results to the client to present to the players. 

The following are some classic network server software for readers to learn about. 

### Minecraft Server 

The official server software of Minecraft Java Edition written by Mojang. 

### Spigot 

A server software of Minecraft Java Edition written in Java. 

### Bedrock Server 

The official server software of Minecraft Bedrock Edition written by Mojang. 

### Nukkit 

A server software of Minecraft Bedrock Edition written by Chinese in Java. 

## The difference between network server and mod 

### Architecture difference 

The online function and single-player game function of Minecraft actually create an internal server under the terminal of the host, and then use the client part to render the game screen. The server computing part of the Mod runs on the terminal of the room owner. 

The network service software specifically separates the server computing part of the game from the client and runs it on a server with higher performance than the player terminal to achieve higher player capacity and stability. 

In other words, the data of players playing on the network service will all be handed over to the professional server for processing. When the Mod is online, all player data will be processed on the room owner's device. If the computing power of the device is not enough, it will greatly affect the game experience. 

### Data storage 

When the Mod is online, most of the generated data will be stored in the map file and loaded into the game when the map is read. 

In the network service, high-performance databases (such as MySQL, MongoDB, Redis) can be used to store data and quickly filter out the required data for caching. Database software has its own advantages, and developers can decide the storage location of data according to their needs. 

