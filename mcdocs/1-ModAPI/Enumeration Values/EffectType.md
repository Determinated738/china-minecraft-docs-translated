# EffectType 

class in mod.common.minecraftEnum 

- Description 

Enumeration value describing the effect type 

```python 
class EffectType(object): 
EMPTY_EFFECT = "empty" # No status effect 
MOVEMENT_SPEED = "speed" # Speed, increase walking speed 
MOVEMENT_SLOWDOWN = "slowness" # Slow, reduce walking speed 
DIG_SPEED = "haste" # Haste, increase mining speed and attack speed 
DIG_SLOWDOWN = "mining_fatigue" # Fatigue, slow down mining speed and attack speed 
DAMAGE_BOOST = "strength" # Strength, increase melee attack damage 
HEAL = "instant_health" # Instant treatment, instant recovery of entity health, damage to undead creatures 
HARM = "instant_damage" # Instant damage, instant damage to entities, treatment of undead creatures 
JUMP = "jump_boost" # Jump boost, increase jump height, reduce fall damage 
CONFUSION = "nausea" # Nausea, cause distorted vision 
REGENERATION = "regeneration" # Recovery, continuous health recovery over time 
DAMAGE_RESISTANCE = "resistance" # Damage resistance increased, reduce most damage 
FIRE_RESISTANCE = "fire_resistance" # Fire resistance, immune to fire damage 
WATER_BREATHING = "water_breathing" # Underwater breathing, no oxygen consumption when underwater 
INVISIBILITY = "invisibility" # Invisibility, gain invisibility effect 
BLINDNESS = "blindness" # Blindness, weakened vision, unable to sprint and produce critical strikes 
NIGHT_VISION = "night_vision" # Night vision, increase vision brightness 
HUNGER = "hunger" # Hunger, increase hunger level, speed up hunger value reduction 
WEAKNESS = "weakness" # Weakness, reduces melee attack damage 
POISON = "poison" # Poisoning, deals damage over time, not fatal 
WITHER = "wither" # Withering, deals damage over time, can be fatal 
HEALTH_BOOST = "health_boost" # Health boost, increases health limit 
ABSORPTION = "absorption" # Damage absorption, increases health used to absorb damage 
SATURATION = "saturation" # Satiation, restores hunger and saturation 
LEVITATION = "levitation" # Levitation, allows entities to continuously increase their height 
FATAL_POISON = "fatal_poison" # Fatal poisoning, deals damage over time, can be fatal 
CONDUIT_POWER = "conduit_power" # Conduit energy, has three effects when underwater: increased vision brightness, increased mining and attack speed, and underwater breathing 
SLOW_FALLING = "slow_falling" # Slow down the landing, reduce the falling speed, and reduce the falling damage 
BAD_OMEN = "bad_omen" # Bad omen, triggers an attack when entering the village 
HERO_OF_THE_VILLAGE = "village_hero" # Village hero, the transaction price with villagers is reduced 

``` 

