# TransferServerFailReason 

class in mod.common.minecraftEnum 

- Description 

Error code for failed transfer 

```python 
class TransferServerFailReason(object): 
TypeNotExist = 10 # The target server does not exist 
VersionNotExist = 11 # The target server version does not match the player client version 
ServerIsFull = 12 # The target server is full 
VersionNotFix = 13 # The target server version does not match the player client version 
TargetIsFull = 14 # The target server is full 
TargetNotVaild = 15 # The target server does not exist or has been disconnected from the control server 
ApiInputFail = 16 # The target player is not online 

``` 

