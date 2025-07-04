--- 
front: 
hard: Advanced 
time: 30 minutes 
--- 

# Simple tutorial ①: Make a creature with a complete attack animation 

#### Author: Boundary 



Download the advanced slime sample package: Download [sample package](https://g79.gdl.netease.com/guidedemo-case11.zip). 

① The additional package in the appendix contains an advanced slime creature. Let the creature have a complete attack animation. In concept, it generally means that the creature's attack will have a delay due to the animation effect. If the slime attacks the target, we don't want it to cause damage to the target when it reaches the attack distance. We would rather it carry a better attack animation and deal the damage at a certain moment in the animation. Fortunately, the original ravager carries such behavior, and it also uses such animation effects. Therefore, it becomes simple to create an effect with a complete attack animation. 

② Before you allow an entity to have an attack behavior, you must add at least one pathfinding component behavior, a movement component behavior, a movement speed component behavior, and an attack power component behavior. The attack behavior will only be effective after the pathfinding and movement component behaviors are turned on. The movement component behavior and the movement speed component behavior enable the creature to move to the target. After the attack power component behavior is added, the creature will have the ability to damage in close combat. 

③ In the advanced slime behavior, we added minecraft:behavior.delayed_attack, which is the delayed attack component behavior. Detailed attribute comments have been written next to the component behavior. 

④ Then switch to the resource pack and open the animation controller, you can see the animation controller file of the advanced slime. It already contains an attack animation controller dedicated to the advanced slime. Before using the "molang syntax", according to the document prompt, the "query" function matched with the delayed attack component behavior is called "query.is_delayed_attacking". When the creature makes an attack action, it will return "1.0", that is, true, otherwise it will return "0.0", that is, false at other times. Therefore, the loop mode used by the attack animation is single, and when "query.is_delayed_attacking" returns "0.0", that is, the attack ends, it switches back to the initial state. 

