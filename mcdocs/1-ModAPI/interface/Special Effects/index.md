--- 
sidebarDepth: 1 
--- 
# Index 

--- 

- [General](#General) 
- [Text Panel](#Text Panel) 
- [Sequence Frame](#Sequence Frame) 
- [Particle](#Particle) 
- [Model Effect](#Model Effect) 
- [Microsoft Particle](#Microsoft Particle) 

### General 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [DestroyEntity](General.md#destroyentity) | <span style="display:inline;color:#7575f9">Client</span> | Destroy Effect | 

### Text Panel 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CreateTextBoardInWorld](Text Panel.md#createtextboardinworld) | <span style="display:inline;color:#7575f9">Client</span> | Create text panel | 
| [RemoveTextBoard](Text Panel.md#removetextboard) | <span style="display:inline;color:#7575f9">Client</span> | Delete text panel | 
| [SetBoardBackgroundColor](Text Panel.md#setboardbackgroundcolor) | <span style="display:inline;color:#7575f9">Client</span> | Modify background color | 
| [SetBoardBindEntity](Text Panel.md#setboardbindentity) | <span style="display:inline;color:#7575f9">Client</span> | Bind text panel to entity object | 
| [SetBoardDepthTest](Text Panel.md#setboarddepthtest) | <span style="display:inline;color:#7575f9">Client</span> | Set whether to enable depth test, it is enabled by default | 
| [SetBoardFaceCamera](Text Panel.md#setboardfacecamera) | <span style="display:inline;color:#7575f9">Client</span> | Set the orientation of the text panel | 
| [SetBoardPos](Text Panel.md#setboardpos) | <span style="display:inline;color:#7575f9">Client</span> | Modify position | 
| [SetBoardRot](Text Panel.md#setboardrot) | <span style="display:inline;color:#7575f9">Client</span> | Modify the rotation angle, if the text is set to face the camera, the modification of the rotation angle will not take effect | 
| [SetBoardScale](Text Panel.md#setboardscale) | <span style="display:inline;color:#7575f9">Client</span> | Content overall scaling | 
| [SetBoardTextColor](Text Panel.md#setboardtextcolor) | <span style="display:inline;color:#7575f9">Client</span> | Modify font color | 
| [SetText](Text Panel.md#settext) | <span style="display:inline;color:#7575f9">Client</span> | Modify text panel content | 

### Sequence frame 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [Bind](Sequence frame.md#bind) | <span style="display:inline;color:#7575f9">Client</span> | Bind entity | 
| [Bind](sequence frame.md#bind) | <span style="display:inline;color:#7575f9">Client</span> | Bind skeleton model | 
| [CreateEngineSfx](sequence frame.md#createenginesfx) | <span style="display:inline;color:#7575f9">Client</span> | Create sequence frame effects | 
| [CreateEngineSfxFromEditor](sequence frame.md#createenginesfxfromeditor) | <span style="display:inline;color:#7575f9">Client</span> | Refers to using effects/xxx.json in the resource package to create a sequence frame according to the parameters edited in the editor. Supports circular sequence frames | 
| [GetPos](sequence frame.md#getpos) | <span style="display:inline;color:#7575f9">Client</span> | Get the position of the sequence frame effect | 
| [GetRot](sequence frame.md#getrot) | <span style="display:inline;color:#7575f9">Client</span> | Get the rotation angle of the sequence frame effect | 
| [GetScale](sequence frame.md#getscale) | <span style="display:inline;color:#7575f9">Client</span> | Get the scale value of the sequence frame effect | 
| [Pause](sequence frame.md#pause) | <span style="display:inline;color:#7575f9">Client</span> | Pause playback, freeze the sequence frame at the current moment, and continue playing when Play is called again | 
| [Play](sequence frame.md#play) | <span style="display:inline;color:#7575f9">Client</span> | Play sequence frame | 
| [SetDeepTest](sequence frame.md#setdeeptest) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the sequence frame is perspective, the default is no |

| [SetFaceCamera](sequence frame.md#setfacecamera) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the sequence frame always faces the camera. The default is yes. | 
| [SetFadeDistance](sequence frame.md#setfadedistance) | <span style="display:inline;color:#7575f9">Client</span> | Set the distance at which the sequence frame starts to automatically adjust its transparency. When the distance between the sequence frame and the camera is less than this value, the transparency of the sequence frame will be automatically adjusted. The closer the distance to the camera, the more transparent the sequence frame. | 
| [SetLayer](sequence frame.md#setlayer) | <span style="display:inline;color:#7575f9">Client</span> | Set the rendering layer of the sequence frame. The default layer is 1. When the layer is not 1, it means that the special effect enables the special effect layered rendering function. When special effects (particles and frame animations) are rendered in layers, the higher the level, the later the rendering will be. Larger levels will occlude lower levels, and special effects at the same level will have the correct mutual occlusion relationship based on the relative positions of the special effects. | 
| [SetLoop](sequence frame.md#setloop) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the sequence frame is played in a loop, the default is no | 
| [SetMixColor](sequence frame.md#setmixcolor) | <span style="display:inline;color:#7575f9">Client</span> | Set the mixed color of the sequence frame | 
| [SetPos](sequence frame.md#setpos) | <span style="display:inline;color:#7575f9">Client</span> | Set the position of the sequence frame | 
| [SetRot](sequence frame.md#setrot) | <span style="display:inline;color:#7575f9">Client</span> | Set the rotation of the sequence frame | 
| [SetRotUseZXY](sequence frame.md#setrotusezxy) | <span style="display:inline;color:#7575f9">Client</span> | Set the rotation of the sequence frame. The rotation order is around the z, x, and y axes. | 
| [SetScale](SequenceFrame.md#setscale) | <span style="display:inline;color:#7575f9">Client</span> | Set the scale of the sequence frame | 
| [SetUsePointFiltering](SequenceFrame.md#setusepointfiltering) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the sequence frame uses point filtering | 
| [Stop](SequenceFrame.md#stop) | <span style="display:inline;color:#7575f9">Client</span> | Stop the sequence frame (not pause) | 

### Particles 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [Bind](particle.md#bind) | <span style="display:inline;color:#7575f9">Client</span> | Bind entity | 
| [Bind](particle.md#bind) | <span style="display:inline;color:#7575f9">Client</span> | Bind skeleton model | 
| [CreateEngineParticle](particle.md#createengineparticle) | <span style="display:inline;color:#7575f9">Client</span> | Used to create particle effects | 
| [GetParticleEmissionRate](particle.md#getparticleemissionrate) | <span style="display:inline;color:#7575f9">Client</span> | Get the frequency of particle emitter emitting particles per frame. | 
| [GetParticleMaxNum](particle.md#getparticlemaxnum) | <span style="display:inline;color:#7575f9">Client</span> | Get the maximum number of particles contained in the particle emitter. | 
| [GetParticleMaxSize](particle.md#getparticlemaxsize) | <span style="display:inline;color:#7575f9">Client</span> | Get the maximum size of particles in particle effects. | 
| [GetParticleMinSize](particle.md#getparticleminsize) | <span style="display:inline;color:#7575f9">Client</span> | Get the minimum size of particles in particle effects. | 
| [GetParticleVolumeSize](particle.md#getparticlevolumesize) | <span style="display:inline;color:#7575f9">Client</span> | Get the volume size scaling value of the particle emitter. | 
| [GetPos](particle.md#getpos) | <span style="display:inline;color:#7575f9">Client</span> | Get the world coordinate position of the particle emitter | 
| [GetRot](particle.md#getrot) | <span style="display:inline;color:#7575f9">Client</span> | Get the rotation angle of the particle emitter | 
| [Pause](particle.md#pause) | <span style="display:inline;color:#7575f9">Client</span> | Pause playback, freeze the particle at the current moment, and continue playing when Play is called again | 
| [Play](particle.md#play) | <span style="display:inline;color:#7575f9">Client</span> | Play particle effects | 
| [SetFadeDistance](particle.md#setfadedistance) | <span style="display:inline;color:#7575f9">Client</span> | Set the distance at which particles start to automatically adjust transparency. When the distance between the particle and the camera is less than this value, the particle transparency will be automatically adjusted. The closer the distance to the camera, the more transparent the particle. | 
| [SetLayer](particle.md#setlayer) | <span style="display:inline;color:#7575f9">Client</span> | The default particle level is 1. When the level is not 1, it means that the special effect has enabled the special effect layered rendering function. When special effects (particles and frame animations) are rendered in layers, the higher the level, the later the rendering. The larger the level, the lower the level will be. And the special effects of the same level will have the correct mutual occlusion relationship according to the relative position of the special effects. | 
| [SetParticleEmissionRate](Particle.md#setparticleemissionrate) | <span style="display:inline;color:#7575f9">Client</span> | Set the frequency of particle emission per frame. The higher the frequency, the more particles are emitted per frame, but the number of particles will not exceed the particle capacity of the particle emitter. At the same time, due to performance considerations, the number of particles emitted per frame will not exceed 100. | 
| [SetParticleMaxNum](Particle.md#setparticlemaxnum) | <span style="display:inline;color:#7575f9">Client</span> | Set the particle capacity of the particle emitter, that is, the maximum number of particles contained in the particle emitter. This number does not represent the number of particles currently emitted by the particle emitter. If you need to increase the number of emitted particles, you need to change the particle emission frequency at the same time. | 
| [SetParticleSize](Particle.md#setparticlesize) | <span style="display:inline;color:#7575f9">Client</span> | Sets the minimum and maximum particle sizes in the particle effect. | 
| [SetParticleVolumeSize](Particle.md#setparticlevolumesize) | <span style="display:inline;color:#7575f9">Client</span> | Sets the volume size of the particle emitter, without affecting the size of individual particles. The larger the volume of the particle emitter, the larger the emission range of the particles. | 
| [SetPos](particle.md#setpos) | <span style="display:inline;color:#7575f9">Client</span> | Set the world coordinate position of the particle emitter | 
| [SetRelative](particle.md#setrelative) | <span style="display:inline;color:#7575f9">Client</span> | When a particle is bound to an entity or a skeleton model, the emitted particles use the entity coordinate system or the world coordinate system. This has the same function as the "Relative Hanging Point Movement" option for particles in the mcstudio special effects editor. | 
| [SetRotUseZXY](particle.md#setrotusezxy) | <span style="display:inline;color:#7575f9">Client</span> | Set the rotation of the particle emitter. The rotation order is around the z, x, and y axes. | 
| [SetUsePointFiltering](particle.md#setusepointfiltering) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the particle material's texture filtering uses the point filtering method. Bilinear filtering is used by default | 
| [Stop](particle.md#stop) | <span style="display:inline;color:#7575f9">Client</span> | Stop particle playback | 

### Model effects 

| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [CreateEngineEffectBind](model effects.md#createengineeffectbind) | <span style="display:inline;color:#7575f9">Client</span> | Refers to using the editor to save all the effects of all the edited hanging points generated by models/bind/xxx_bind.json in the resource pack. The generated effects will be automatically hung and played, and the effects set to invisible in the editor will also be played. And when using the special effects created in this way, the developer does not need to maintain the attachment special effects caused by the entity entering and exiting the field of view. The engine will automatically create all special effects every time the entity enters the field of view. | 
| [Pause](Model Special Effects.md#pause) | <span style="display:inline;color:#7575f9">Client</span> | Pause model special effects (that is, special effects created using CreateEngineEffectBind) | 
| [Resume](Model Special Effects.md#resume) | <span style="display:inline;color:#7575f9">Client</span> | Continue playing model special effects (that is, special effects created using CreateEngineEffectBind) | 

### Microsoft Particles 


| Interface | <div style="width: 3em"></div> | Description | 
| --- | --- | --- | 
| [BindEntity](Microsoft Particles.md#bindentity) | <span style="display:inline;color:#7575f9">Client</span> | Bind the particle emitter to the specified bone of the specified entity | 
| [BindModel](Microsoft Particles.md#bindmodel) | <span style="display:inline;color:#7575f9">Client</span> | Bind the particle emitter to the specified bone of the specified bone model | 
| [Create](Microsoft Particles.md#create) | <span style="display:inline;color:#7575f9">Client</span> | Create a particle emitter and play it immediately after creation | 
| [CreateBindEntity](Microsoft Particles.md#createbindentity) | <span style="display:inline;color:#7575f9">Client</span> | Create a particle emitter and bind it to the specified bone of the specified entity. Play it immediately after creation | 
| [EmitManually](Microsoft Particle.md#emitmanually) | <span style="display:inline;color:#7575f9">Client</span> | Manually emit particles once | 
| [Exist](Microsoft Particle.md#exist) | <span style="display:inline;color:#7575f9">Client</span> | Determine whether the specified particle emitter exists | 
| [GetActiveDuration](Microsoft Particle.md#getactiveduration) | <span style="display:inline;color:#7575f9">Client</span> | Get the activation period of the particle emitter | 
| [GetBindingID](Microsoft Particle.md#getbindingid) | <span style="display:inline;color:#7575f9">Client</span> | Returns the bound target id. If not, it returns "0" | 
| [GetBindingModleID](Microsoft Particles.md#getbindingmodleid) | <span style="display:inline;color:#7575f9">Client</span> | Returns the bound skeleton model id. If not, it returns -1 | 
| [GetDuration](Microsoft Particles.md#getduration) | <span style="display:inline;color:#7575f9">Client</span> | Gets the playback cycle (activation + sleep time) of the particle emitter | 
| [GetFacingMode](Microsoft Particles.md#getfacingmode) | <span style="display:inline;color:#7575f9">Client</span> | Returns the particle facing mode of the particle emitter | 
| [GetLoopAge](Microsoft Particles.md#getloopage) | <span style="display:inline;color:#7575f9">Client</span> | Get the time played in the current playback cycle of the particle emitter | 
| [GetPos](Microsoft Particle.md#getpos) | <span style="display:inline;color:#7575f9">Client</span> | Get the position of the particle emitter | 
| [GetRot](Microsoft Particle.md#getrot) | <span style="display:inline;color:#7575f9">Client</span> | Get the local rotation of the particle emitter | 
| [GetSleepDuration](Microsoft Particle.md#getsleepduration) | <span style="display:inline;color:#7575f9">Client</span> | Get the sleep period of the particle emitter | 
| [GetTimeScale](Microsoft Particle.md#gettimescale) | <span style="display:inline;color:#7575f9">Client</span> | Get the playback speed of the particle emitter | 
| [GetVariable](Microsoft Particles.md#getvariable) | <span style="display:inline;color:#7575f9">Client</span> | Get the Molang variable value of the particle emitter | 
| [Hide](Microsoft Particles.md#hide) | <span style="display:inline;color:#7575f9">Client</span> | Hide the particle emitter (do not render) | 
| [IsHiding](Microsoft Particles.md#ishiding) | <span style="display:inline;color:#7575f9">Client</span> | Returns whether the particle emitter is being hidden (do not render) | 
| [IsPausing](Microsoft Particles.md#ispausing) | <span style="display:inline;color:#7575f9">Client</span> | Returns whether the logic of the particle emitter is being paused | 
| [Pause](Microsoft Particles.md#pause) | <span style="display:inline;color:#7575f9">Client</span> | Pause the logic update of the particle emitter, but keep the rendering state | 
| [Play](Microsoft Particles.md#play) | <span style="display:inline;color:#7575f9">Client</span> | Play the particle emitter | 
| [PlayAt](Microsoft Particles.md#playat) | <span style="display:inline;color:#7575f9">Client</span> | Set the particle emitter playback time point | 
| [Remove](Microsoft Particles.md#remove) | <span style="display:inline;color:#7575f9">Client</span> | Destroy the specified particle emitter | 
| [RemoveByName](Microsoft Particles.md#removebyname) | <span style="display:inline;color:#7575f9">Client</span> | Destroy all particle emitters with the specified name (identifier in particle emitter json) in the scene | 
| [Replay](Microsoft Particles.md#replay) | <span style="display:inline;color:#7575f9">Client</span> | Replay the particle emitter | 
| [Resume](Microsoft Particles.md#resume) | <span style="display:inline;color:#7575f9">Client</span> | Resume the logical update of the particle emitter without affecting the rendering state | 
| [SetPos](Microsoft Particles.md#setpos) | <span style="display:inline;color:#7575f9">Client</span> | Set the particle emitter position | 
| [SetRelative](Microsoft Particles.md#setrelative) | <span style="display:inline;color:#7575f9">Client</span> | Set whether the particle is calculated in local space | 
| [SetRot](Microsoft Particles.md#setrot) | <span style="display:inline;color:#7575f9">Client</span> | Set the local rotation of the particle emitter | 
| [SetTimeScale](Microsoft Particles.md#settimescale) | <span style="display:inline;color:#7575f9">Client</span> | Set the playback speed of the particle emitter | 
| [SetVariable](Microsoft Particles.md#setvariable) | <span style="display:inline;color:#7575f9">Client</span> | Set the Molang variable value of the particle emitter | 
| [Show](Microsoft Particles.md#show) | <span style="display:inline;color:#7575f9">Client</span> | Display particle emitter (turn on rendering) | 
| [Stop](Microsoft Particles.md#stop) | <span style="display:inline;color:#7575f9">Client</span> | Stop particle emitter playback (do not render and do not update logic) | 
| [Unbind](Microsoft Particles.md#unbind) | <span style="display:inline;color:#7575f9">Client</span> | Unbind the specified particle emitter | 

