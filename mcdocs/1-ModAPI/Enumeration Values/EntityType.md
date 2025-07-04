# EntityType 

class in mod.common.minecraftEnum 

- Description 

Entity type enumeration 

- Notes 
- When using [runtime_identifier](https://mc.163.com/dev/mcmanual/mc-dev/mconline/15-%E7%8E%A9%E6%B3%95%E7%BB%84%E4%BB%B6%E6%95%99%E7%A8%8B%E3%80%90%E6%96%B0%E7%89%88%E3%80%91/7-%E8%87%AA%E5%AE%9A%E4%B9%89%E5% AE%9E%E4%BD%93/4-%E6%8E%A2%E7%B4%A2%E5%AE%9E%E4%BD%93%E7%9A%84%E8%A1%8C%E4%B8%BA%E6%96%87%E4%BB%B6.html#%E7%90%86%E8%A7%A3%E5%AE%9E%E4%BD%93%E8%A1%8C%E4%B8%BA%E7%9A%84%E6%8F%8F%E8%BF%B0%E4%BF%A1%E6%81%AF) 
When a field inherits the characteristics of an entity, the entity belongs to the same category as the entity pointed to by runtime_indentifier. 
- When a custom entity does not use the runtime_identifier field, the entity belongs to the Mob class by default.

```python 
class EntityType(object): 
Undefined = 1 # Undefined type 
TypeMask = 0x000000ff # Type filter 
Mob = 0x00000100 # Mob 
PathfinderMob = 0x00000200 | Mob # PathfinderMob 
Monster = 0x00000800 | PathfinderMob # Hostile monster 
Animal = 0x00001000 | PathfinderMob # Animal 
TamableAnimal = 0x00004000 | Animal # Tamable animal 
Ambient = 0x00008000 | Mob # Environment 
UndeadMob = 0x00010000 | Monster # Undead creature 
ZombieMonster = 0x00020000 | UndeadMob # Zombie mob 
Arthropod = 0x00040000 | Monster # Arthropod mob 
Minecart = 0x00080000 # Minecart 
SkeletonMonster = 0x00100000 | UndeadMob # Skeleton mob 
EquineAnimal = 0x00200000 | TamableAnimal # Equine mob 
Projectile = 0x00400000 # Projectile 
AbstractArrow = 0x00800000 # Abstract arrow 
WaterAnimal = 0x00002000 | PathfinderMob # Aquatic mob 
VillagerBase = 0x01000000 | PathfinderMob # Villager mob 
Chicken = 10 | Animal # Chicken 
Cow = 11 | Animal # Cow 
Pig = 12 | Animal # Pig 
Sheep = 13 | Animal # Sheep 
Wolf = 14 | TamableAnimal # Wolf 
Villager = 15 | VillagerBase # Villager 
MushroomCow = 16 | Animal # Mooshroom 
Squid = 17 | WaterAnimal # Squid 
Rabbit = 18 | Animal # Rabbit 
Bat = 19 | Ambient # Bat 
IronGolem = 20 | PathfinderMob # Iron Golem 
SnowGolem = 21 | PathfinderMob # Snow Golem 
Ocelot = 22 | TamableAnimal # Ocelot 
Horse = 23 | EquineAnimal # Horse 
PolarBear = 28 | Animal # Polar Bear

Llama = 29 | Animal # Alpaca 
Parrot = 30 | TamableAnimal # Parrot 
Dolphin = 31 | WaterAnimal # Dolphin 
Donkey = 24 | EquineAnimal # Donkey 
Mule = 25 | EquineAnimal # Mule 
SkeletonHorse = 26 | EquineAnimal | UndeadMob # Skeleton Horse 
ZombieHorse = 27 | EquineAnimal | UndeadMob # Zombie Horse 
Zombie = 32 | ZombieMonster # Zombie 
Creeper = 33 | Monster # Creeper 
Skeleton = 34 | SkeletonMonster # Skeleton 
Spider = 35 | Arthropod # Spider 
PigZombie = 36 | UndeadMob # Zombified Piglin 
Slime = 37 | Monster # Slime 
EnderMan = 38 | Monster # Enderman 
Silverfish = 39 | Arthropod # Silverfish 
CaveSpider = 40 | Arthropod # Cave Spider 
Ghast = 41 | Monster # Ghast 
LavaSlime = 42 | Monster # Lava 
Blaze = 43 | Monster # Blaze 
ZombieVillager = 44 | ZombieMonster # ZombieVillager 
Witch = 45 | Monster # Witch 
Stray = 46 | SkeletonMonster # Stray 
Husk = 47 | ZombieMonster # Husk 
WitherSkeleton = 48 | SkeletonMonster # Wither Skeleton 
Guardian = 49 | Monster # Guardian 
ElderGuardian = 50 | Monster # Elder Guardian 
Npc = 51 | Mob # NPCs 
WitherBoss = 52 | UndeadMob 
Dragon = 53 | Monster 
Shulker = 54 | Monster 
Endermite = 55 | Arthropod 
Agent = 56 | Mob 
Vindicator = 57 | Monster 
Phantom = 58 | UndeadMob 
IllagerBeast = 59 | Monster 
ArmorStand = 61 | Mob 
TripodCamera = 62 | Mob 
Player = 63 | Mob 
ItemEntity = 64 
PrimedTnt = 65 
FallingBlock = 66 
MovingBlock = 67 Moving blocks 
ExperiencePotion = 68 | Projectile # Bottle of Enchanting 
Experience = 69 # Experience Ball 
EyeOfEnder = 70 # Eye of Ender 
EnderCrystal = 71 # Ender Crystal 
FireworksRocket = 72 # Fireworks Rocket 
Trident = 73 | Projectile | AbstractArrow # Trident 
Turtle = 74 | Animal # Turtle 
Cat = 75 | TamableAnimal # Cat

ShulkerBullet = 76 | Projectile # ShulkerBullet 
FishingHook = 77 # Float 
Chalkboard = 78 # Chalkboard 
DragonFireball = 79 | Projectile # Ender Dragon Fireball 
Arrow = 80 | Projectile | AbstractArrow # Arrow 
Snowball = 81 | Projectile # Snowball 
ThrownEgg = 82 | Projectile # Egg 
Painting = 83 # Painting 
LargeFireball = 85 | Projectile # Fireball 
ThrownPotion = 86 | Projectile # Splash Potion 
Enderpearl = 87 | Projectile # Enderpearl 
LeashKnot = 88 # Leash Knot 
WitherSkull = 89 | Projectile # Black Wither Skull 
BoatRideable = 90 # Rideable Boat 
WitherSkullDangerous = 91 | Projectile # Blue Wither Skeleton 
LightningBolt = 93 # Lightning 
SmallFireball = 94 | Projectile # Small Fireball 
AreaEffectCloud = 95 # Area Effect Cloud 
LingeringPotion = 101 | Projectile # Lingering Potion 
LlamaSpit = 102 | Projectile # Alpaca Spit 
EvocationFang = 103 | Projectile # Evocation Fang 
EvocationIllager = 104 | Monster # Evocation 
Vex = 105 | Monster # Vex 
MinecartRideable = 84 | Minecart # Rideable Minecart 
MinecartHopper = 96 | Minecart # Hopper Minecart 
MinecartTNT = 97 | Minecart # TNT Minecart 
MinecartChest = 98 | Minecart # Transport Minecart 
MinecartFurnace = 99 | Minecart # Fueled Minecart 
MinecartCommandBlock = 100 | Minecart # Command Block Minecart 
IceBomb = 106 | Projectile # Ice Bomb 
Balloon = 107 # Balloon 
Pufferfish = 108 | WaterAnimal # Pufferfish 
Salmon = 109 | WaterAnimal # Salmon 
Drowned = 110 | ZombieMonster # Drowned 
Tropicalfish = 111 | WaterAnimal # Tropical Fish 
Fish = 112 | WaterAnimal # Fish 
Panda = 113 | Animal # Panda 
Pillager = 114 | Monster # Pillager 
VillagerV2 = 115 | VillagerBase # Villager 
ZombieVillagerV2 = 116 | ZombieMonster # Zombie Villager 
Shield = 117 # Shield 
WanderingTrader = 118 | PathfinderMob # Wandering Trader 
Lectern = 119 # Lectern 
ElderGuardianGhost = 120 | Monster # Elder Guardian Ghost 
Fox = 121 | Animal # Fox 
Bee = 122 | Mob # Bee 
Piglin = 123 | Mob # Piglin 
Hoglin = 124 | Animal # Hoglin 
Strider = 125 | Animal # Striders 
Zoglin = 126 | Mob # Zombie Hoglin

PiglinBrute = 127 | Mob # Piglin Brute 
Goat = 128 | Animal # Goat 
GlowSquid = 129 | WaterAnimal # Glow Squid 
Axolotl = 130 | Animal # Axolotl 
CustomProjectile = 254 | Projectile # Custom Projectile 
EntityExtension = 255 # Entity Extension 
MAX_ENTITY_ID = 256 # Maximum Entity ID 

``` 

