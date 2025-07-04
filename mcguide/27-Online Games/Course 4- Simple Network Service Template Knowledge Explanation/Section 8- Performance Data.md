--- 
front: 
hard: Advanced 
time: 5 minutes 
--- 

# Performance data 

## Determine the number of service processes deployed on a machine 

​ MC has a very large degree of freedom, and the implementation of each online game varies greatly. Different online games use different mods, and the performance consumption of different mods is also different. Some online games are complex to play, and a physical machine may deploy 20 games; some online games are simple to play, and a physical machine may deploy 30 games. 

​ We recommend that online game server owners actively contact us, and we will guide the server owners to deploy in the best way. 

## Evaluate the maximum number of online players in the game server 

- The server's carrying capacity is inversely proportional to the square of the number of online players. The more online players there are, the more CPU the server consumes. 
- The map size mainly affects the memory occupied by the server, and has a weaker impact on the server's carrying capacity. At present, the maximum memory of a single server process is fixed at 8G. 
- The server will not load all maps at once. It will load blocks on demand and store unused blocks to disk.
- Server performance consumption is composed of mods and engines, and mod performance consumption cannot be ignored. Server owners can improve the performance of online games by optimizing mods, and server owners should try their best to optimize mods. 
- Maximum online player evaluation method: It is recommended to conduct a limited deletion test before the online service is officially launched. During the deletion test, observe the server performance and obtain the maximum number of online players in the lobby/game. Specific process: In the initial stage, set the maximum number of online players in the lobby to 50~100, and the maximum number of online players in the game to 10~30. Then observe the server performance, and then continuously update and adjust the maximum number of online players. 

## Performance data of the fifth personality 

### Deployment method 
The fifth personality uses a low-frequency host with 40 cores, 128G memory, and a main frequency of 2.3GHZ. A total of 18 low-frequency physical machines are used. The specific deployment method is as follows: 

- 1 master, 2 services, and 10 games are deployed on one physical machine. 
- 10 proxies are deployed on one physical machine. 
- 20 lobby are deployed on one physical machine.
- 300 games are deployed to 20 physical machines, and 15 games are deployed on each physical machine. 
- The memory limit of each server process is 8G at most. 

### Number of people 
The server can carry so many people, and the following conditions must be met: 
- The main thread CPU of the server process does not exceed 80% most of the time. 
- The memory occupied by the process is not allowed to exceed 8G. 
- There is no obvious lag or delay on the client. 

The following introduces the carrying capacity of each server of Identity V: 
- A proxy can carry 600 people, and 10 proxies can carry 6,000 people. 
- A lobby can carry 200 people, and 20 lobby can carry 4,000 people. 
- A game can carry 15 people, and 310 games can carry 4,650 people. The number of people carried by a game of Identity V is relatively low, mainly due to gameplay restrictions. A game can only be opened 3 times, and each game has only 5 people. 

Conclusion: When Identity V is deployed using 18 physical machines, the proxy can carry 6,000 people, and the lobby+game can carry 8,650 people. Taking the minimum of the two, Identity V can carry 6,000 people. 
