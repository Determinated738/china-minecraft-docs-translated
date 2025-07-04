--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Material Classification 

## Preface 

This article will introduce the commonly used materials in MC games. If developers need to modify the performance of certain objects, they can refer to this article to modify the corresponding materials and shaders. 
The following materials are based on the data\resource_packs\vanilla\materials directory 

## Sky 

### sky.material material file 

#### sun_moon 

Sun and Moon 

#### stars 

Stars 

#### cubemap 

The skybox composed of six faces used to render the sky 

#### skyplane 

Used to render the color of the sky above. A large circular grid will be placed at the top of the game, parallel to the ground 

#### end_sky 

Used to render the color and texture of the sky above the end. A large circular grid will be placed at the top of the game, parallel to the ground 

### fancy.material, sad.material material files 

#### clouds 

Clouds 

## Terrain blocks (blocks placed on the ground) 

### terrain.material material file 

#### terrain_opaque 

Opaque terrain blocks


##### terrain_far 

Opaque terrain blocks will use this material to render when they are far away 

#### terrain_blend 

Translucent terrain block materials, such as water, glass, etc. 

##### terrain_blend_far 

Translucent blocks will use this material to render when they are far away 

#### terrain_alpha 

Some block materials have fully transparent areas in some parts, and both sides need to be rendered. The engine uses anvils, bamboo, rails, potions, cacti, corals, crops, etc. 

##### terrain_alpha_single_side 

Some materials have fully transparent areas in some parts, but back-face clipping is turned on and only one side is rendered. The engine uses beacons, carrots, redstone comparators, composters, doors, mushrooms, etc. 

#### terrain_doubleside 

Currently used to render beds 

#### terrain_opaque_seasons 

Currently used to render opaque leaves with snow on them 

##### terrain_seasons_far 

Currently used to render opaque leaves with snow on them in the distance 

#### terrain_alpha_seasons 

Currently used to render translucent leaves with snow on them 

##### terrain_seasons_far_alpha 

Currently used to render translucent leaves with snow on them 

### barrier.material material file 

#### barrier 

Barrier blocks 

### portal.material material file 

#### portal_base


End portal 

## Non-terrain blocks and entities (handheld or independent in the scene) 

### entity.material material file 

#### entity_static 

Static entity 

#### entity_flat_color_line 

Used to render the line of the fishing rod 

#### entity_loyalty_rope 

Used to render the leash 

#### opaque_block 、 opaque_block_color 、 opaque_block_color_uv2 

Opaque block rendering 

#### alpha_block 、 alpha_block_color 

Blocks with transparent areas 

#### map 

Map rendering 

#### entity_alphablend 、 entity_alphablend_nocolor 

Entity objects with transparency blending 

#### item_in_hand 、 item_in_hand_multicolor_tint 、 item_in_hand_entity_alphatest_color, item_in_hand_glint

Used for rendering various handheld items

#### moving_block, moving_block_seasons, moving_block_alpha_seasons, moving_block_alpha_single_side, moving_block_alpha, moving_block_double_side, moving_block_blend

Used for rendering dynamically changing blocks

### Netease extended entity.material material file content

The file is located in the data, resource_packs, vanilla_netease, materials directories, mainly adding materials for bone model rendering

#### Resources with vip words

Usually used in member materials, generally good results, more complex shader implementation, can be used for learning reference


#### entity_for_skeleton 、 entity_for_skeleton_cpu 

Used to render ordinary opaque skeleton models 

#### entity_for_skeleton_hide_cpu 、 entity_for_skeleton_hide 

Used to show the hidden state of the entity, the effect is to render a solid color semi-transparent model 

#### entity_for_skeleton_alpha_cpu 、 entity_for_skeleton_alpha 

Used to render skeleton models with transparency 

#### entity_for_skeleton_bright 、 entity_for_skeleton_bloom 、 entity_for_skeleton_glint、 entity_for_skeleton_bloom_glint 

Some skeleton models will use various special effects, such as highlights, glows, and sweeping light effects. 

#### entity_for_skeleton_frame_ani 

Used to implement skeleton model sequence frame animation 

## Particles 

### particles.material material file 

#### particles_opaque 

Opaque particles native to the engine 

#### particles_alpha 

Particles native to the engine with transparency clipping enabled 

#### particles_blend 

Particles native to the engine with transparency 

#### particles_effects 

Particles native to the engine with special UV change effects with transparency clipping enabled 

#### common_particle, common_particle_add, common_particle_add_texture, common_particle_blend, common_particle_blend_texture 

NetEase particle system, custom particle special effects basically use these, and the functions correspond to the above-mentioned native particles. 

## Shadows 

### shadows.material material file 

The shadow rendering uses Stencil masking technology


#### shadow_front 、 shadow_back 

No actual rendering is performed at the position marked by the mask shadow 

### shadow_overlay 

The actual rendering is performed at the position marked in the mask 

## UI 

### ui3D.material material file 

Contains some special UI related to objects in the scene, or materials related to weather UI 

#### selection_XXX 

The words "selection" are basically the rendering of the selection effect after selecting a block or entity 

#### selection_box 

Pointing to an object after turning on outline selection will display a wireframe 

#### name_tag、name_tag_depth_tested 

Name background above the entity's head 

#### sign_text、name_text_depth_tested 

Name text above the entity's head 

#### rain 

Rain 

#### snow 

Snow 

#### lightning 

Lightning 

### ui.material Material file 

UI materials used on the UI interface 

Since many UIs use the same material, each material may be used in multiple places. We will not list every place here. Here we will only give examples of materials used by several common UI interface objects 

#### Item Quick Bar


ui_textured_and_glcolor 

#### Joystick, menu button on top, move, sneak, fly, etc. buttons on the upper right corner, jump button on the lower right corner 

ui_texture_and_color 

#### Item icons in backpack or item shortcut bar 

ui_item 

#### Crosshair in the center of the screen 

ui_crosshair 

#### Background image of loading scene 

ui_cubemap 

#### Text on UI 

ui_text 

