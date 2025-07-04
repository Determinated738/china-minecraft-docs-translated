--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Advanced 
time: 15 minutes 
--- 
# Understand the search feature rules 

In this section, we continue to understand the search feature. We try to use the search feature to attach the custom apple block we made in Chapter 10 to our oak tree to form an oak tree that will bear fruit. 

## Set the apple single block feature 

As we remember, our block identifier is `tutorial_demo:apple`. We create a single block feature `apple_feature.json`. 

```json
{
  "format_version": "1.13.0",
  "minecraft:single_block_feature": {
    "description": {
      "identifier": "tutorial_demo:apple_feature"
    },
	"places_block": "tutorial_demo:custom_apple",
    "enforce_survivability_rules": true,
    "enforce_placement_rules": true,
	"may_attach_to": {
      "auto_rotate": false,
      "min_sides_must_attach": 2,
      "top": {
        "name": "minecraft:leaves",
        "states": {
          "old_leaf_type": "oak"
        }
      },
      "west": {
        "name": "minecraft:leaves",
        "states": {
          "old_leaf_type": "oak"
        }
      },
      "north": {
        "name": "minecraft:leaves",
        "states": {
          "old_leaf_type": "oak"
        }
      },
      "east": {
        "name": "minecraft:leaves",
        "states": {
          "old_leaf_type": "oak"
        }

}, 
"south": { 
"name": "minecraft:leaves", 
"states": { 
"old_leaf_type": "oak" 
} 
} 
}, 
"may_replace": [ 
"minecraft:air" 
] 
} 
} 
``` 

Here we have set a strict replacement setting. We expect an apple to be connected like a leaf in at least two directions, up, front, back, left, and right. In this way, our apple will look like it is hanging on the oak tree, and it will not be particularly abrupt. 

## Use the search feature to connect to the apple feature 

We create a new `apple_search_feature.json` file: 

```json 
{ 
"format_version": "1.13.0", 
"minecraft:search_feature": { 
"description": { 
"identifier": "tutorial_demo:apple_search_feature" 
}, 
"places_feature": "tutorial_demo:apple_feature", 
"search_volume": { 
"min": [ -4, -16, -4 ], 
"max": [ 4, 0, 4 ] 
}, 
"search_axis": "-y", 
"required_successes": 1 
} 
} 
``` 

Here we start searching from the input position in the negative direction of the Y axis, that is, downward. When we successfully obtain a position that can make the apple single block feature `tutorial_demo:apple_feature`, we stop searching and place the single block feature. When the number of positions that can make the feature to be placed successful is less than the value of `required_successes`, the placement judgment of the search feature will fail. 

In the next section, we will continue to implement the placement of the search feature through sequence features.