# AniCheatMove 

class in mod.common.minecraftEnum 

- Description 

Anti-cheat configuration enumeration value, movement check switch 

```python 
class AniCheatMove(object): 
CheckStyle = "server-authoritative-movement" # Displacement check mode 
CorrectSwitch = "correct-player-movement" # Whether to correct the client with displacement problems 
MinCorrectDelayTick = "player-rewind-min-correction-delay-ticks" # The minimum number of ticks from the server to send a correction command from the discovery of cheating, 0 means that the correction command is sent every frame when cheating is discovered (int) 
TickHistorySize = "player-rewind-history-size-ticks" # The client saves the historical frame number for rewind simulation. 20 frames per second (int) 

``` 

