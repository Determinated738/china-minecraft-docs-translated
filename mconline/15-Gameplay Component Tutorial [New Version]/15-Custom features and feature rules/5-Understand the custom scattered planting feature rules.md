--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Advanced 
time: 10 minutes 
--- 
# Understand the custom scattered planting feature rules 

We continue to use the blue fern block in the previous section to write scattered planting features. We hope to generate more blue ferns in the world to form a cluster. 

## Set up fern scattered planting features 

We create the `blue_fern_cluster_feature.json` file in the feature folder. 

```json
{
  "format_version": "1.13.0",
  "minecraft:scatter_feature": {
    "description": {
      "identifier": "tutorial_demo:blue_fern_cluster_feature"
    },
    "places_feature": "tutorial_demo:blue_fern_feature",
    "iterations": 10,
    "scatter_chance": 50.0,
    "x": {
      "distribution": "uniform",
      "extent": [ 0, 5 ]
    },
    "y": 0,
    "z": {
      "distribution": "uniform",
      "extent": [ 0, 5 ]
    } } 
} 
``` 

Note that in terms of naming, we are accustomed to calling a uniformly distributed plant group a **cluster**, and a Gaussian distributed plant community a **patch**. Of course, for the game engine itself, naming may not be so important, but for readability, a good name is still necessary. 

When placing scattered plant features, as long as at least one target feature in the iteration is successfully placed, it will be judged as successful, and if all target features in all iterations fail, it will be judged as a failure. 

## Attach feature rules 

We create a new `overworld_blue_fern_cluster_feature.json` file in the feature rule folder. 

```json 
{ 
"format_version": "1.13.0", 
"minecraft:feature_rules": { 
"description": {

      "identifier": "tutorial_demo:overworld_blue_fern_cluster_feature",
      "places_feature": "tutorial_demo:blue_fern_cluster_feature"
    },
    "conditions": {
      "placement_pass": "surface_pass",
      "minecraft:biome_filter": [
        {
          "any_of": [
            {
              "test": "has_biome_tag",
              "operator": "==",
              "value": "overworld"
            },
            {
              "test": "has_biome_tag",
              "operator": "==",
              "value": "overworld_generation"
            }
          ]
        }
      ]
    },
    "distribution": {
      "iterations": 5,
      "x": {
        "distribution": "uniform",
        "extent": [ 0, 16 ] 
}, 
"y": "query.heightmap(variable.worldx, variable.worldz)", 
"z": { 
"distribution": "uniform", 
"extent": [ 0, 16 ] 
} 
} 
} 
} 
``` 

We iterate 5 times, plus the feature itself has a 50% probability of placement, which is equivalent to placing 2.5 blue fern clusters in one block on average. 

![](./images/16.5_blue_fern_cluster_in-game.png) 

As you can see, the generation is in line with our expectations!