# Network synchronization 

Next, we will introduce the network synchronization function of parts and how to use it in parts 

## Function introduction 

The network synchronization function is used to simplify the synchronization of server and client data in part development. After using the network synchronization function, when the specified fields in the server part are modified (including the addition, deletion and modification of sub-elements in dictionaries and lists), the relevant fields in the client part will also be modified synchronously. 

## Supported data structures 

The network synchronization function supports the data structures of Number, String, List, Tuple, Dictionary. And the combination and nesting of the above data. 

## Usage method 

Let's take the template part NetworkReplicatedPart as an example to introduce how to use the network synchronization function. 

To use the network synchronization function, you only need to add the field name you want to synchronize to the replicated field of the part during initialization, as shown in the following code 

```python 
def __init__(self): 
super(NetworkReplicatedPart, self).__init__() 
self.name = "Network replication test part" 
self.intProperty = 0 
self.intProperty2 = 0 
self.strProperty = "0" 
self.strProperty2 = "0" 
self.listProperty = ["0", "0", "0"] 
self.listProperty2 = ["0", "0", "0"] 
self.dictProperty = {"key": 0} 
self.dictProperty2 = {"key": 0} 
self.tupleProperty = ("0", "0", "0") 
self.tupleProperty2 = ("0", "0", "0") 

   self.flexProperty = ("0", "0", {"key": [0]})
   self.flexProperty2 = ("0", "0", {"key": [0]})
   
   # Synchronize intProperty, strProperty, listProperty, dictProperty, tupleProperty, flexProperty
   self.replicated = ["intProperty", "strProperty", "listProperty", "dictProperty", "tupleProperty", "flexProperty"]
   self.tickIndex = 0
```

In the code above, we use the network synchronization function for six different types of fields: intProperty, strProperty, listProperty, dictProperty, tupleProperty, and flexProperty. 

Next, we modify the value of the relevant field in the server's tick and print it out in the client's tick 

```python 
def TickClient(self): 
self.tickIndex += 1 
if self.tickIndex % 150 == 30: 
print("TickClient", self) 

def TickServer(self): 
self.tickIndex += 1 
if self.tickIndex % 150 == 0: 
self.intProperty += 1 
self.intProperty2 += 1 
self.strProperty = str(self.intProperty) 
self.strProperty2 = str(self.intProperty) 
self.listProperty[0] = self.strProperty 
self.listProperty2[0] = self.strProperty 
self.dictProperty["key"] = self.intProperty 
self.dictProperty2["key"] = self.intProperty 
self.tupleProperty = tuple(self.listProperty) 
self.tupleProperty2 = tuple(self.listProperty) 
self.flexProperty[2]["key"].append(self.intProperty) 
self.flexProperty2[2]["key"].append(self.intProperty) 
print("TickServer", self) 
``` 

After testing with development test, the script debugging interface log is as follows (for easy viewing, useless logs are omitted and log indentation is adjusted) 

`[17:11:17] ('TickClient', {` 
`......` 
`"dictProperty": {"key": 2},` 
`"dictProperty2": {"key": 0},` 
`"flexProperty": ["0","0", {"key": [0, 1, 2]}],`
    `"flexProperty2": ["0", "0", {"key": [0]}],`
    `"intProperty": 2,`
    `"intProperty2": 0,`
    `"listProperty": [ "2", "0", "0"],`
    `"listProperty2": ["0", "0", "0" ],`
    `"name": "NetworkReplicated",`
    `"partType": "NetworkReplicatedPart",`
    `"replicated": [ "intProperty", "strProperty", "listProperty", "dictProperty", "tupleProperty", "flexProperty"],`
    `"strProperty": "2",`
    `"strProperty2": "0",` `"tickEnable": true,`

`"tickIndex": 300,` 
`......` 
`"tupleProperty": [ "2", "0", "0" ],` 
`"tupleProperty2": [ "0", "0", "0"` 
`]` 

`})` 

*Note: The tuple type is still the tuple type on the client side and is printed as tuple because the printed value is the json string of the part structure 

It can be seen that the values of the six fields intProperty, strProperty, listProperty, dictProperty, tupleProperty, and flexProperty in the client part are synchronized to the client by the server part, and the fields that are not written to replicated are not synchronized. 

## Notes 

- 1. The fields that need to be synchronized need to be initialized before the replicated fields 

- 2. The fields must be supported data structures, otherwise they will fail to synchronize and an error will be reported 

- 3. Using the network synchronization function will incur additional performance loss, please use it according to actual needs 

- 4. The data synchronized by the client will be delayed, generally 1 frame + network transmission time. 

