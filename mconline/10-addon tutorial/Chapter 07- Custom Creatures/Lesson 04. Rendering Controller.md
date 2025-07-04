--- 
front: 
hard: Advanced 
time: 15 minutes 
--- 

# Rendering Controller 

#### Author: Boundary 

The rendering controller helps developers control how creatures are rendered in the game world. It and the animation controller can be regarded as the two most difficult parts of customizing creatures. In the original creatures, not all creatures have only a single expression. For example, after the villager war update, villagers have different skins according to the biome, tropical fish have thousands of combinations, and wolves have red eyes when they are angry. These are all controlled by the rendering controller and stored in the local game file in a JSON structure. In addition to reading the tutorial, the original file is also a natural and in-depth teaching material. I hope that developers can supplement the original file with additional knowledge during the learning process. 

```
{
    "format_version":"1.8.0",
    "render_controllers":{
        "controller.render.default":{
            "geometry":"Geometry.default",
            "materials":[
                {
                    "*":"Material.default"
                }
            ],
            "textures":[
                "Texture.default"
            ],
            "overlay_color":{
                "r":0,
                "g":0,
                "b":0,
                "a":0
            },
            "on_fire_color":{
                "r":0,
                "g":0,
                "b":0,
                "a":0
            },
            "is_hurt_color":{
                "r":0,
                "g":0,
                "b":0,
                "a":0
            }
        }
    }

} 
``` 

#### format_version 

format_version refers to the version number of the rendering controller file, and currently only 1.8.0 is available. 

#### controller.render. 

Each controller must be prefixed with controller.render. The following names can be separated by the name of the creature. 

#### material 

Material means material. Similarly, the value is written as "Material.MaterialKey", where the material key is English characters, which corresponds to the key under the material object in the creature definition file, and its value will lead to the material resource. 

#### texture 

Texture means texture. Similarly, the value is written as "texture.TextureKey", where the texture key is English characters, which corresponds to the key under the texture object in the creature definition file, and its value will lead to the texture resource. 

#### overlay_color 

overlay_color means overlay color. Similar to the color overlay mode of image processing software, where r represents red, g represents green, b represents blue, and a represents transparency. RGB is the three primary colors in color. In the controller, the value is obtained by dividing the color component by 255. For example, RGB (255, 0, 0) represents red, so fill in the above color value with "r": 1.0,"g": 0.0,"b": 0.0,"a": 1.0. 

#### on_fire_color 

on_fire_color means the color of the biological entity when it is on fire. In MC, the default is red. If this item is not customized, it will inherit the color of the original biological fire. The customization form is the same as overlay_color. 

#### is_hurt_color 

is_hurt_color means the color of the biological entity when it is injured. In MC, the default is red. If this item is not customized, it will inherit the color of the original biological injury. The customization form is the same as overlay_color.