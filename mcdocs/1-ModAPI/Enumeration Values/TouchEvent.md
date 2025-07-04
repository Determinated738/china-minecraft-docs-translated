# TouchEvent 

class in mod.common.minecraftEnum 

- Description 

Touch callback event enumeration value 

```python 
class TouchEvent: 
TouchUp = 0 # callback triggered when the button is lifted 
TouchDown = 1 # callback triggered when the button is pressed 
TouchCancel = 3 # callback triggered when the mouse is lifted after the button is pressed and moved out of the button range 
TouchMove = 4 # callback triggered when the mouse is moved after the button is pressed 
TouchMoveIn = 5 # callback triggered when the mouse is pressed and moved into the button 
TouchMoveOut = 6 # callback triggered when the mouse is pressed and moved out of the button 
TouchScreenExit = 7 # triggered when the mouse is not lifted when the canvas where the button is located exits 

``` 

