# EntityTeleportCause 

class in mod.common.minecraftEnum 

- Description 

Teleportation reason enumeration 

```python 
class EntityTeleportCause(object): 
Unknown = "0" # Not yet classified, Enderman self-teleport is currently classified as this 
Projectile = "1" # Projectile, similar to Ender Pearl 
Command = "3" # op command, similar to tp command, changedimension command 
ChorusFruit = "2" # Eat chorus fruit to teleport 
Behavior = "4" # Microsoft native script component 
Agent = "agent" # Education version guide teleport 
Client = "client" # Teleport movement package sent by the client 
GateWay = "gateway" # Teleportation gate 
Script = "script" # Python interface, similar to SetPos, SetFootPos, ChangePlayerDimension, ChangeEntityDimension 

``` 

