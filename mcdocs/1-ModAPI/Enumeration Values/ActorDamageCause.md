# ActorDamageCause 

class in mod.common.minecraftEnum 

- Description 

Describes the enumeration value of the entity's damage source and the reason why the entity was damaged. 

```python 
class ActorDamageCause(object): 
NONE = "none" # Other 
Override = "override" # Abnormal method (such as the script directly sets the health to 0), the damage of this method will not be absorbed by armor and buffs 
Contact = "contact" # Contact damage (such as cactus) 
EntityAttack = "entity_attack" # Biological attack 
Projectile = "projectile" # Projectile attack 
Suffocation = "suffocation" # Suffocation (sealed space) 
Fall = "fall" # Fall 
Fire = "fire" # Fire 
FireTick = "fire_tick" # Continuous fire (biological fire, in fire) 
Lava = "lava" # Lava 
Drowning = "drowning" # Drowning 
BlockExplosion = "block_explosion" # Block explosion 
EntityExplosion = "entity_explosion" # Explosion of creatures 
Void = "void" # Void 
Suicide = "suicide" # Suicide (kill command) 
Magic = "magic" # Damage caused by fangs to creatures, magic damage caused by guardians to creatures, potion damage, etc. 
Wither = "wither" # Wither effect 
Starve = "starve" # Hunger 
Anvil = "anvil" # Falling anvil 
Thorns = "thorns" # Thorns rebound damage 
FallingBlock = "falling_block" # Falling block (except anvil) 
Piston = "piston" # Piston 
FlyIntoWall = "fly_into_wall" # Gliding (hitting the wall) 
Magma = "magma" # Magma (such as standing on a magma block) 
Fireworks = "fireworks" # Fireworks 
Lightning = "lightning" # Lightning 
Freezing = "freezing" # Freezing 
Stalactite = "stalactite" # Hit by stalactites 
Stalagmite = "stalagmite" # Falling on stalagmites 
RamAttack = "ram_attack" # Goat attack 

``` 

