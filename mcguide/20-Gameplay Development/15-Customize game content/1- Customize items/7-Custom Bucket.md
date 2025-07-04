--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Custom Bucket 

## Overview 

Custom Buckets are mainly used to hold custom fluids. They are usually used with custom fluids. After use, they can pour out the specified fluid blocks 

## custom_item_type setting 

- The custom bucket's **custom_item_type** needs to be set to **bucket** 

## Registration 

1. Same as steps 1-6 for registering custom basic items 
2. Set custom_item_type to **bucket** in the json of behavior/netease_items_beh 
3. Add the definition related to the custom bucket, including a required **netease:bucket component**. For the component parameters, see [json component](#json component). Note: The maximum stacking number of custom buckets is 1, and cannot be modified by max_stack_size 

```json 
{ 
"format_version": "1.10", 
"minecraft:item": { 
"description": { 
"identifier": "customBucket:green_bucket", 
"custom_item_type": "bucket", 
"register_to_create_menu": true 
}, 
"components": { 
"netease:bucket": { 
"fill_liquid": "flowing_green_water" 
} 
} 
}, 
} 
``` 

## JSON components 


### NetEase components 

* netease:bucket 

| Key | Type | Default | Explanation | 
| ----------- | ------ | --------------- | ---------------------------- | 
| fill_liquid | string | "flowing_water" | Optional, the id of the fluid block to be poured out when used | 

**Note: The fluid block must be a dynamic fluid of a custom fluid** 
