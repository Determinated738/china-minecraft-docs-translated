# UiBaseLayer 

class in mod.common.minecraftEnum 

- Description 

Customize the hierarchical macro definition of the UI interface, used to coordinate the occlusion relationship of the UI interface between multiple plugins 

```python 
class UiBaseLayer(object): 
Desk = 0 # Main interface 
DeskFloat = 15000 # Main interface floating prompt (floating prompt information) 
PopUpLv1 = 25000 # First level pop-up interface 
PopUpLv2 = 45000 # Second level pop-up interface 
PopUpModal = 60000 # Modal pop-up interface (pop-up prompt) 
PopUpFloat = 75000 # Floating prompt above the modal pop-up (loudspeaker) 

``` 

