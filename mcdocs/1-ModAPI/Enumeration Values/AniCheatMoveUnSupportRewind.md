# AniCheatMoveUnSupportRewind 

class in mod.common.minecraftEnum 

- Description 

Anti-cheat configuration enumeration value, special scene related parameters that do not support rewind simulation 

```python 
class AniCheatMoveUnSupportRewind(object): 
PositionThreshold = "player-rewind-unsupported-position-threshold" # In a certain frame, the square threshold of the distance between the client position and the server position, exceeding the threshold will trigger anti-cheat correction (float) 
VelocityThreshold = "player-rewind-unsupported-velocity-threshold" # In a certain frame, the square threshold of the difference between the client speed and the server speed, exceeding this threshold will trigger anti-cheat correction (float) 
PositionAcceptance = "player-rewind-unsupported-position-acceptance" # In a certain frame, if the square of the distance between the client position and the server position is less than this value, the server will use the client's value (float) 
PositionPersuasion = "player-rewind-unsupported-position-persuasion" # If the client and server positions are inconsistent, the server will add this value (float) to the client's calculated direction every frame 

``` 

