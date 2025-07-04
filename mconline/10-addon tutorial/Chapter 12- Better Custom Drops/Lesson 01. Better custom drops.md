--- 
front: 
hard: Advanced 
time: 5 minutes 
--- 

# More Complete Custom Drops 

#### Author: Boundary 

Custom drops can not only drop creature-related items, but also, with reasonable configuration and imagination, developers can use drop pools, drop functions, drop conditions, special drop entrances and other methods to implement a variety of loot systems. . This chapter will disassemble the details of each method one by one. 

#### The following are a few points to note when customizing drops: 

- Crash: When there is an incorrect syntax in the drop configuration file, once you generate a creature with equipment, kill a creature, destroy a custom block, open a reward box with modified loot, fish, or interact with a creature to generate the drop in the file, the game will crash immediately without providing any error prompts. 
- Equipment Loot: Only original elytra, helmets, armor, leggings, shoes, and pillager banners can be equipped by mobs; mobs cannot be equipped with mob heads, custom equipment, or carved pumpkins; items that can be held in the player's off-hand, such as shields, can also be held in the mob's off-hand by equipping loot. 
- Enchanting: When setting enchantments for dropped items, enchantments cannot be given to items that do not have enchantability.