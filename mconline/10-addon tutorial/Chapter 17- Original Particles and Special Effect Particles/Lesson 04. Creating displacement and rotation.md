--- 
front: 
hard: Advanced 
time: 20 minutes 
--- 

# Create displacement and rotation 



#### Author: Boundary 



#### Original Particle Dynamic Tutorial 



#### Create displacement 

1) Select shape in snowstorm, and use offset to offset the position of the particle emitter, and the starting point of the particle will also be offset. 

2) Swipe to the motion folding panel. When the mode is dynamic, you can give the particle a speed (starting speed) or an acceleration. 

3) Swipe to the rotation folding panel. When the mode is dynamic, you can give the particle a start rotation (initial rotation angle), a speed (rotation speed), and an acceleration (rotation acceleration). 

3) There is an air drag under the movement and rotation panels, which can be described as air friction. The larger the value, the worse the displacement and rotation effects.



#### Special Effect Particle Rendering Dynamic Tutorial 

#### Creating Displacement 

1) Click the particle attribute panel. There is a column of special effect direction (direction) on the basic attributes. If you choose Inwards, the particle will move inward. If you choose Outwards, it will move from the inside to the outside. When selecting the initial direction of the particle, you can customize the direction of the particle. The direction is the direction in which the particle will fly out when the speed of movement is given later. 

2) The initial speed is the initial speed, the constant force is the subsequent acceleration, and the damping force is the friction force. 

3) The particle size refers to the size of the particle before facing the player's camera. 

4) The initial rotation is the initial rotation angle, and the rotation speed is the constant acceleration of the rotation. 

5) Most basic attributes have minimum and maximum values. When the minimum and maximum values are different, the final attribute value acting on the particle will be random between the minimum and maximum values.