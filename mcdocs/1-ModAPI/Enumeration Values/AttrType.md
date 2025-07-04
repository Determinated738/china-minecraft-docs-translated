# AttrType 

class in mod.common.minecraftEnum 

- Description 

Describes the attribute enumeration value, used to set and get the current and maximum values of the entity's engine attributes 

- Notes 
- ABSORPTION: The quantitative value of the damage absorption effect, see the wiki document for details: [Damage Absorption](https://minecraft-zh.gamepedia.com/index.php?title=%E4%BC%A4%E5%AE%B3%E5%90%B8%E6%94%B6&variant=zh) 

```python 
class AttrType(object): 
HEALTH = 0 # Health value, the original value range is [0,20] 
SPEED = 1 # Movement speed, the original value range is [0,+∞] 
DAMAGE = 2 # Attack power, the original value range is [1,1] 
UNDERWATER_SPEED = 3 # Speed in water, the original value range is [0, +∞] 
HUNGER = 4 # hunger value, the original value range is [0, 20] 
SATURATION = 5 # saturation value, the original value range is [0, 20] 
ABSORPTION = 6 # damage absorption health value, see notes for details, the original value range is [0, 16] 
LAVA_SPEED = 7 # speed in lava, the original value range is [0, +∞] 
LUCK = 8 # luck value, the original value range is [-1024, 1024] 

``` 

