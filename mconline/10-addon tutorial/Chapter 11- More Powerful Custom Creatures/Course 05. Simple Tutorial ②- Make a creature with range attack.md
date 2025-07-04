--- 
front: 
hard: Advanced 
time: 30 minutes 
--- 

# Easy tutorial ②: Make a creature with range attack 

#### Author: Boundary 

#### 

Download the advanced slime sample package: Download [sample package](https://g79.gdl.netease.com/guidedemo-case11.zip). 

① Open the advanced slime behavior in the appendix package again. We have opened a component group, which contains a "knockback_roar" component behavior, which comes from the plunder beast. It is a component behavior that generates range damage and knockback when the plunder beast roars. It is very suitable for making range attacks. The detailed component key pair properties have been written with comments. Let's focus on how to add this component group to the advanced slime activity at the right time. 　 

② Remember the controller and creature events mentioned earlier in this chapter? We once wrote an example that gives a status effect when the creature finds the target and cancels the status effect when the target is lost. Similarly, we can also modify this mode to make the advanced slime generate a range attack with a war cry when it finds a target, and start moving towards the player after the attack ends. Therefore, a controller that controls the triggering of range attacks has been written in the behavior pack's controller. From the document, "query.has_target" returns "1.0", that is, true, when the entity finds the target, otherwise it returns "0.0", that is, false. Therefore, when switching to the "roar" roar state, the target must be found. Then we execute an instruction in "on_entry", which will trigger a full-screen information announcement. Then trigger the start roar event defined in the advanced slime behavior. When the roar ends, we trigger an event to remove the roar component through the roar component's "on_roar_end", so that the creature will start to approach the target until the target disappears, and the controller switches back to the normal state, and will wait for the next target to be found, and continue the roar, forming a closed loop of vivid behavior.