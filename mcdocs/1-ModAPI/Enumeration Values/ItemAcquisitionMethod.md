# ItemAcquisitionMethod 

class in mod.common.minecraftEnum 

- Description 

Enumeration value of the method to obtain items 

```python 
class ItemAcquisitionMethod(object): 
Unknown = -1 # Unknown acquisition method. 
MethodNone = 0 # No acquisition method. 
PickedUp = 1 # Acquired by picking up the item. Triggered by both the server and the client. 
Crafted = 2 # Acquired by crafting tools, including workbenches, cartography tables, grinding wheels, looms, and stonecutters. Triggered from the client. 
TakenFromChest = 3 # Acquired by taking from a chest. Triggered from the client. 
TakenFromEnderchest = 4 # Acquired by taking from an ender chest. Currently, only the value of TakenFromChest is returned when taking items from an ender chest. 
Bought = 5 # Acquired by trading with villagers. Currently, trading with villagers only returns the value of Trading. 
Anvil = 6 # Obtained by anvil. Triggered by the client. 
Smelted = 7 # Obtained by smelting, including furnaces, smokers and blast furnaces. Triggered by the client. 
Brewed = 8 # Obtained by brewing. Triggered as long as the props are taken from the brewing stand. Triggered from the client. 
Filled = 9 # Obtained by filling an empty bottle, bucket or cauldron, or pouring the contents from it, triggered by both the server and the client. 
# Note that the event is only triggered from the server when the object is a cauldron. 
Trading = 10 # Obtained by trading. Triggered from the client. 
Fishing = 11 # Obtained by fishing. Triggered by both the server and the client. 
Container = 13 # Obtained by container, currently only supports forging. Triggered from the client. 
Feeding = 14 # Being fed. Triggered from the server. 

``` 

