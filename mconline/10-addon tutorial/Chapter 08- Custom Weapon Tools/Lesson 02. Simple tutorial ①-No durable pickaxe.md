--- 
front: 
hard: Advanced 
time: 10 minutes 
--- 

# Simple tutorial ①: Pickaxe without durability 

#### Author: Realm 

``` 
{ 
"format_version":"1.10", 
"minecraft:item":{ 
"components":{ 
"minecraft:max_damage":10, 
"minecraft:max_stack_size":1, 
"netease:weapon":{ 
"attack_damage":10, 
"enchantment":10, 
"level":0, 
"speed":1, 
"type":"pickaxe" 
} 
}, 
"description":{ 
"category":"Equipment", 
"identifier":"design:custom_hatchet", 
"register_to_create_menu":true 
} 
} 
} 
``` 

1) Enter the level editor and create weapon and tool components. 

2) Change the tool type to pickaxe. 

3) Enter the behavior pack/netease_items_beh (NetEase version items) folder through the resource manager and find the custom item file. 

4) By default, the item setting file generated by the editor will come with the "minecraft:max_damage" key pair, which is the component that controls the durability of the tool. We will delete this line. 

5) Enter the game and you can see that the pickaxe does not consume durability during mining.