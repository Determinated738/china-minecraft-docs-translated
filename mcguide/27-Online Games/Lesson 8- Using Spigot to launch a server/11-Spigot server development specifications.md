---
front: 
hard: Getting Started
time: 60 minutes
---

# Spigot server development specifications

## Spigot server deployment specifications

- **<span style="font-size: 25px; color: red;">Only supports the 1.12.2 version compiled by the official BuildTools of spigot, and cannot use the modified spigot</span>**
- [Official BuildTools wiki](https://www.spigotmc.org/wiki/buildtools/)

## Spigot server.properties parameter specifications

- view-distance
```
Recommended value: 4-6
```
Determines the block information data sent by the server, which has a huge impact on server performance and traffic consumption. It is recommended to reduce it.

- online-mode
```
Required value: false
```
Determines whether the Spigot server is authenticated. In Apollo, login authentication is handled by proxy, and spigot does not need to be authenticated again.

- allow-flight
```
Required value: true
```
Determines whether Spigot performs flight detection. Since the current Bedrock Edition login Java server needs to go through the Geyser server translation protocol, during this process, the player movement related packages cannot be perfectly translated. If this field is set to false, there is a possibility that the player's movement will be blocked by the server as flight.

- network-compression-threshold

```
Required value: -1
```

Determines the compression level of the spigot and bc communication protocol. Because spigot and bc are in the same intranet, the traffic does not require cost, so not compressing the network protocol saves performance

## BungeeCord server config.yml parameter specification
- connection_throttle_limit
```
Recommended value: 100

```
The number of players that the BC server allows to log in from the same IP at the same time. Because players in Apollo log in from the protocol server, this value needs to be increased.

- online-mode
```
Required value: false
```

Determines whether the BC server performs genuine verification. In Apollo, login authentication is handled by proxy, and BC does not need to verify again.

- network_compression_threshold

```
Required value: -1
```

Determines the compression level of the communication protocol between BC and the protocol server. Because BC and the protocol server are in the same intranet, the traffic does not cost, so not compressing the network protocol saves performance