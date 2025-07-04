--- 
front: 
hard: Advanced 
time: 20 minutes 
--- 

# Inherit the chicken animation 

#### Author: Boundary 

Put green_head_duck.geo.json into the texture pack, in the entity folder of the models folder. 

Put green_head_duck.png into the texture pack, in the entity folder of the textures folder. 

In the entity folder of the texture pack, create a new green_head_duck.entity.json file. 

```
{
	"format_version": "1.10.0",
	"minecraft:client_entity": {
		"description": {
            "identifier": "design:green_head_duck",
            "render_controllers": [
				"controller.render.default"
            ],
            "textures": {
				"default": "textures/entity/green_head_duck"
			},
			"geometry": {
				"default": "geometry.green_head_duck"
			},
			"materials": {
				"default": "entity_alphatest"
			},
			"animations": {
				"move": "animation.chicken.move",
				"look_at_target": "animation.common.look_at_target"
			},
			"scripts": {
				"animate": [
				  	{ "move": "query.modified_move_speed" },
				  	"look_at_target"
				]
			},
			"spawn_egg": {
				"base_color": "#256143",

"overlay_color": "#dd9238" 
} 
} 
} 
} 
``` 

1) First, we define the name domain as design:green_head_duck. 

2) Then we use the original default basic rendering controller, "controller.render.default", which will control the creature to render into a creature image composed of a model, a texture, and a material. 

3) Then in textures, we point the texture resource path to the green_head_duck texture stored in textures/entity. Please note that here, you do not need to write the texture file suffix. 

4) In geometry, we point the model resource to the geometric model made earlier. At the beginning of the project, the model we exported was modified from the chicken model. Therefore, when opening the teal model, the model's name domain is still geometry.chicken. In order to avoid resource conflicts, you need to change it to geometry.green_head_duck in advance. 

5) In materials, set the material to entity_alphatest, which will allow creatures to use textures with transparent channels. 

6) Under animations, load the chicken's movement animation and gaze animation. 

7) Under scripts/animate, load the animation. 

8) In spawn_egg, we add two attribute keys, one is "base_color", the value is "#256143", which represents a dark green color, and the value represents the base color of the egg. Add a "overlay_color", the value is "#dd9238", and the value represents the spot color of the egg. 

