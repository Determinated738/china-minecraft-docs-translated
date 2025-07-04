--- 
front: https://nie.res.netease.com/r/pic/20210728/5507b669-4c6f-4958-b5d0-b8556ab4cfb5.png 
hard: Advanced 
time: 20 minutes 
--- 
# Component and interface usage optimization 

## Preface 

MC's strength lies in its openness, providing developers with a large number of system functions and APIs for support, but many functions are prone to performance problems if used improperly. Here are some system functions that need attention. 

## Character special effects quantity control 

### Significance 

Because in actual games, there will be multiple characters displayed on the screen at the same time, so if it is a special effect bound to the character, it is necessary to pay more attention to performance issues, and avoid attaching particle special effects that will emit a large number of particles to the character, or attaching a large number of sequence frames or texts. 

### Too many particle effects 

- Wrong way to write: 
(Custom wings, define 200 to 300 particles per second, too many. If there are 6 players on the same screen, it will be 1200 to 1800 particles. The update and rendering of particles have certain performance consumption) 
```json 
# Definition of a certain wing testWind.json: 
{ 
"particleeffect": { 
"emissionrate": { 
"max": "300.0", 
"min": "200.0" 
}, 
...(Irrelevant code omitted) 
} 
``` 

- Correct way to write: 
(The following solutions can be used in combination) 
```python 
1) Solution 1, strictly control the number of particles to about 100 
# Definition of a certain wing testWind.json: 
{ 
"particleeffect": { 
"emissionrate": { 
"max": "100.0", 
"min": "80.0" 
}, 
...(Irrelevant code omitted) 
} 

2) Solution 2, define multiple wings in different levels, and let players choose according to their device configuration in the game 
# High-end wings

{ 
"particleeffect": { 
"emissionrate": { 
"max": "300.0", 
"min": "280.0" 
}, 
...(Irrelevant code omitted) 
} 
# Medium-end wings 
{ 
"particleeffect": { 
"emissionrate": { 
"max": "200.0", 
"min": "180.0" 
}, 
...(Irrelevant code omitted) 
} 
# Low-end wings 
{ 
"particleeffect": { 
"emissionrate": { 
"max": "100.0", 
"min": "80.0" 
}, 
...(Irrelevant code omitted) 
} 
3) Solution 3, provide a switch button to display and hide special effects, and provide a switch button to display and hide other player special effects. Players can switch at any time when they feel stuck. 
``` 

## Point-to-point message synchronization 

### Significance 

If the server can send messages to the client point-to-point, do not broadcast them. In the game, the server often needs to send messages to the client. If broadcast is used, all clients will receive them. Messages sent only to a certain player should not be broadcasted. 

Example: There are three players A, B, and C in the game, and the server sends a message to A: 

- Wrong way to write: 
(Broadcast to everyone, in fact, other people don’t need to receive this message at all, which will waste the extra traffic and performance) 
```python 
# Client: 
class MyClientSystem(ClientSystem): 
def __init__(self, namespace, systemName): 
ClientSystem.__init__(self, namespace, systemName) 
# Register for listening 
self.ListenForEvent(clientApi.GetEngineNamespace(), clientApi.GetEngineSystemName(), 'OnServerSay', self, self.OnServerSay) 

# Listening callback function 
def OnServerSay(self, data): 
if data["playerId"] == clientApi.GetLocalPlayerId():

print("server talk to me, content:", data["content"]) 

# Server 
class UIDemoServerSystem(ServerSystem): 
def talkToClient(self, playerId): 
# Broadcast method 
self.BroadcastToAllClient("OnServerSay", { 
"playerId": playerId, 
"content": "hello!" 
}) 

def func(self): 
self.talkToClient(playerAId) 
``` 

- Correct way to write: 
```python 
# Client: 
class MyClientSystem(ClientSystem): 
def __init__(self, namespace, systemName): 
ClientSystem.__init__(self, namespace, systemName) 
# Register listener 
self.ListenForEvent(clientApi.GetEngineNamespace(), clientApi.GetEngineSystemName(), 'OnServerSay', self, self.OnServerSay) 

# Listening callback function 
def OnServerSay(self, data): 
print("server talk to me, content:", data["content"]) 

# Server 
class UIDemoServerSystem(ServerSystem): 
def talkToClient(self, playerId): 
# Point-to-point sending method 
self.NotifyToClient(playerId, "OnServerSay", { 
"content": "hello!" 
}) 

def func(self): 
self.talkToClient(playerAId) 
``` 
