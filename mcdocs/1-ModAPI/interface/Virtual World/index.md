--- 
sidebarDepth: 1 
--- 
# Index 

--- 

- [World](#World) 
- [Camera](#Camera) 
- [Model](#Model) 
- [Other Objects](#Other Objects) 

### World 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [VirtualWorldCreate](世界.md#virtualworldcreate) | <span style="display:inline;color:#7575f9">Client</span> | Create a virtual world. Only one virtual world is allowed. Calling this method when a virtual world already exists will be invalid. | 
| [VirtualWorldDestroy](世界.md#virtualworlddestroy) | <span style="display:inline;color:#7575f9">Client</span> | Destroy virtual world | 
| [VirtualWorldSetCollidersVisible](世界.md#virtualworldsetcollidersvisible) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the bounding box of the model in the virtual world is displayed. It is mainly used for debugging and is not displayed by default. | 
| [VirtualWorldSetSkyBgColor](世界.md#virtualworldsetskybgcolor) | <span style="display:inline;color:#7575f9">Client</span> | Set the color of the sky background in the virtual world | 
| [VirtualWorldSetSkyTexture](世界.md#virtualworldsetskytexture) | <span style="display:inline;color:#7575f9">Client</span> | Set the texture of the sky in the virtual world | 
| [VirtualWorldToggleVisibility](世界.md#virtualworldtogglevisibility) | <span style="display:inline;color:#7575f9">客户端</span> | Set whether the virtual world is displayed | 

### Camera 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CameraGetClickModel](摄像.md#cameragetclickmodel) | <span style="display:inline;color:#7575f9">客户端</span> | Get the id of the model the camera is currently pointing to. It will return the one closest to the camera. It is usually used in conjunction with GetEntityByCoordEvent | 
| [CameraGetFov](摄像.md#cameragetfov) | <span style="display:inline;color:#7575f9">客户端</span> | Get the camera's field of view | 
| [CameraGetPos](Camera.md#cameragetpos) | <span style="display:inline;color:#7575f9">Client</span> | Returns the camera position | 
| [CameraGetZoom](Camera.md#cameragetzoom) | <span style="display:inline;color:#7575f9">Client</span> | Gets the camera's zoom value | 
| [CameraLookAt](Camera.md#cameralookat) | <span style="display:inline;color:#7575f9">Client</span> | Modifies the camera's orientation | 
| [CameraMoveTo](Camera.md#cameramoveto) | <span style="display:inline;color:#7575f9">Client</span> | Sets the camera's moving animation, which will be interpolated and displayed according to the current camera state and the passed parameters in time | 
| [CameraSetFov](Camera.md#camerasetfov) | <span style="display:inline;color:#7575f9">Client</span> | Set the camera field of view | 
| [CameraSetPos](Camera.md#camerasetpos) | <span style="display:inline;color:#7575f9">Client</span> | Set the camera position | 
| [CameraSetZoom](Camera.md#camerasetzoom) | <span style="display:inline;color:#7575f9">Client</span> | Set the camera zoom | 
| [CameraStopActions](Camera.md#camerastopactions) | <span style="display:inline;color:#7575f9">Client</span> | Stop the camera movement animation | 

### Model 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [ModelCancelAllBoneMask](Model.md#modelcancelallbonemask) | <span style="display:inline;color:#7575f9">Client</span> | Cancel all bone masks in the animation. | 
| [ModelCreateMinecraftObject](Model.md#modelcreateminecraftobject) | <span style="display:inline;color:#7575f9">Client</span> | Create Microsoft original models in the virtual world | 
| [ModelCreateObject](Model.md#modelcreateobject) | <span style="display:inline;color:#7575f9">Client</span> | Create NetEase skeleton models in the virtual world | 
| [ModelGetPos](Model.md#modelgetpos) | <span style="display:inline;color:#7575f9">Client</span> | Get the coordinates of the model | 
| [ModelGetRot](Model.md#modelgetrot) | <span style="display:inline;color:#7575f9">Client</span> | Return the rotation angle of the model | 
| [ModelIsVisible](Model.md#modelisvisible) | <span style="display:inline;color:#7575f9">Client</span> | Return model visibility | 
| [ModelMoveTo](Model.md#modelmoveto) | <span style="display:inline;color:#7575f9">Client</span> | Set model translation movement | 
| [ModelPlayAnimation](Model.md#modelplayanimation) | <span style="display:inline;color:#7575f9">Client</span> | Model plays animation, supports action fusion, its function is the same as the model interface ModelPlayAni. |

| [ModelRegisterAnim1DControlParam](Model.md#modelregisteranim1dcontrolparam) | <span style="display:inline;color:#7575f9">Client</span> | When playing multiple skeletal animations at the same time, create a new parameter to control the 1D linear blending of the animations. Currently, linear blending only supports blending two animations. The value range of the new parameter is [0,1]. The specified bone will perform linear blending of the two animations according to the value of this parameter. | 
| [ModelRemove](Model.md#modelremove) | <span style="display:inline;color:#7575f9">Client</span> | Destroy the model in the virtual world | 
| [ModelRotate](Model.md#modelrotate) | <span style="display:inline;color:#7575f9">Client</span> | How many degrees the model rotates around a certain axis | 
| [ModelRotateTo](Model.md#modelrotateto) | <span style="display:inline;color:#7575f9">Client</span> | Set the model rotation movement | 
| [ModelSetAnim1DControlParam](Model.md#modelsetanim1dcontrolparam) | <span style="display:inline;color:#7575f9">Client</span> | After creating the 1D control parameters of the animation, use this interface to control the corresponding parameters. | 
| [ModelSetAnimAllBoneMask](Model.md#modelsetanimallbonemask) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to block the animation of all bones in the animation. If the bone shielding is turned on, the bone will no longer play the actions in the animation. This interface will take effect on all bones in the animation. The parameter ignoreBoneList can be used to specify the names of bones that are not affected. By shielding the animation of the specified bones, different action animations can be played on different bones of the same bone model at the same time, thereby achieving quick action fusion. | 
| [ModelSetAnimBoneMask](Model.md#modelsetanimbonemask) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to block the animation of the specified bones in the animation. If the bone shielding is turned on, the bone will no longer play the actions in the animation. By shielding the animation of the specified bones, different action animations can be played on different bones of the same bone model at the same time, thereby achieving quick action fusion. | 
| [ModelSetAnimLayer](Model.md#modelsetanimlayer) | <span style="display:inline;color:#7575f9">Client</span> | Set the level of skeletal animation. The higher the animation level, the higher the priority. The bones of the skeletal model will play the animation with the highest priority first. For animations of the same level, the first animation played will be played first. | 
| [ModelSetBoxCollider](Model.md#modelsetboxcollider) | <span style="display:inline;color:#7575f9">Client</span> | Set the bounding box of the model | 
| [ModelSetPos](Model.md#modelsetpos) | <span style="display:inline;color:#7575f9">Client</span> | Set the model coordinates | 
| [ModelSetRot](Model.md#modelsetrot) | <span style="display:inline;color:#7575f9">Client</span> | Set the rotation angle of the model | 
| [ModelSetScale](Model.md#modelsetscale) | <span style="display:inline;color:#7575f9">Client</span> | Set the scale value of the model | 
| [ModelSetVisible](Model.md#modelsetvisible) | <span style="display:inline;color:#7575f9">Client</span> | Set model visibility | 
| [ModelStopActions](Model.md#modelstopactions) | <span style="display:inline;color:#7575f9">Client</span> | Stop the movement and rotation of the model | 
| [ModelStopAnimation](Model.md#modelstopanimation) | <span style="display:inline;color:#7575f9">Client</span> | Stop playing the specified model animation. | 
| [ModelUpdateAnimationMolangVariable](Model.md#modelupdateanimationmolangvariable) | <span style="display:inline;color:#7575f9">Client</span> | Update Microsoft's original model expression variables to control the changes of actions | 

### Other objects 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [BindModel](Other objects.md#bindmodel) | <span style="display:inline;color:#7575f9">Client</span> | Bind objects to models, support binding sequence frames, particles, text and other models | 
| [MoveToVirtualWorld](Other objects.md#movetovirtualworld) | <span style="display:inline;color:#7575f9">Client</span> | Move objects from the main world to the virtual world. Unbound sequence frames, texts, and particles need to call this method before they appear in the virtual world. Bound ones can omit calling this method. | 

