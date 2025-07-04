# AniCheatConsts 

class in mod.common.minecraftEnum 

- Description 

Anti-cheat configuration switch macro definition 

```python 
class AniCheatConsts(object): 
Open = "on" # Anti-cheat switch: open 
Close = "off" # Anti-cheat switch: closed 
MoveOff = "client-auth" # No displacement check, full trust client 
MoveOn = "server-auth" # Server has displacement check, no rewind simulation 
MoveRewind = "server-auth-with-rewind" # Server has displacement check, rewind simulation 

``` 

