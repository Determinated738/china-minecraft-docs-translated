---
front: 
hard: Advanced
time: 20 minutes
---
# Advanced Code Writing

After learning how to use Python to write logic gameplay, we also need to learn how to improve the quality of our code.

<iframe src="https://cc.163.com/act/m/daily/iframeplayer/?id=6328686fc6dfd1bb76f1d13c" width="800" height="600" allow="fullscreen"/>

## Specifications

First of all, we should pay attention to our own code specifications.

Parts development has its own <a href="../../../../mcguide/20-Gameplay Development/14-Preset Gameplay Programming/2-In-depth Understanding of Parts/6-Parts Development Specifications.html?catalog=1">Specifications</a>, the reserved fields in the specifications have been introduced before, and the content of other parts is relatively simple, you can check it yourself.

There is also <a href="../../../../mcguide/20-Gameplay Development/13-Module SDK Programming/20-Production Specifications.html?catalog=1">Module SDK</a>. Although we use preset gameplay and parts programming to develop gameplay, we actually still use some functions in the module SDK to develop gameplay. Therefore, in this specification, we can refer to all specifications except naming. Naming involves some preset internal file path data that has been saved, so it is not recommended to modify it.

At the same time, we also need to pay attention to coding standards in the process of writing code. The code written in this way is not only error-prone, but also easy to understand by yourself, and can also make other members of the team understand your code faster. Here we extract a part of <a href="../../../../mcguide/27-Online Games/Course 6: Plug-in Teaching/Section 1: Official Plug-in Specifications.html?catalog=1">Official Plug-in Specifications</a> related to code writing for explanation.

- All class names are named in camel case with the first letter capitalized, such as the class GameObjectType.
- Constants are named in camel case with the first letter capitalized, such as ModVersion = "0.0.1"
- Class non-static member variables are named in camel case with an "m" at the beginning, such as mLevel.
- Class non-static member functions are named in camel case with the first letter capitalized, such as Init().
- Events are named in camel case with the first letter capitalized, such as "PlayerTransactionFromClientEvent"
- Use tabs instead of four spaces for indentation.
- example:

```python
class TitleScreen(ScreenNode):
    def __init__(self, namespace, name, param):
        ScreenNode.__init__(self, namespace, name, param)
        self.mMainPanel = "/main_panel"
        self.mTitleText = self.mMainPanel + "/title_text"
        self.mConfirmButton = self.mMainPanel + "/confirm_button"

    def Create(self):
        """
        @description Called when UI is created successfully
        """
        buttonControl = self.GetBaseUIControl(self.mConfirmButton).asButton()
        buttonControl.AddTouchEventParams({"isSwallow": True})
        buttonControl.SetButtonTouchUpCallback(self.OnConfirmButtonClick)

    def OnConfirmButtonClick(self, args):
        text = self.GetBaseUIControl(self.mTitleText).asTextEditBox().GetEditText()
        presetApi.GetPresetByName("TitleScreen").GetPartByName("Interface server monitoring").NotifyToServer("TitleEvent", {"text": text})
        clientApi.PopScreen()
```


## Tips

### Function Encapsulation

For example, if we need to find the average value of a set of data, we can encapsulate a function and call it when we need to use it, which will greatly improve the readability of the code.

```python
def avg(*args)
return sum(args) / len(args)
```

The average value is just a relatively simple application. If it is not a simple calculation like the average value, a large amount of repetition will make the code bloated, and if it needs to be modified in the future, it must be modified in each place where it is used. In contrast, using functions, we can only modify the function definition, thereby reducing the workload.

### Avoid repeated calculations

Suppose we need to use the module SDK interface to make a chain mining function, and we need to call the `PlayerDestoryBlock` interface to mine blocks, and we have found the list of blocks to be destroyed as `blocks` through the search method.

In fact, when calling the `PlayerDestoryBlock` interface in a loop, our blockInfoComp object is exactly the same. So we can get blockInfoComp outside the loop, and then only call `blockInfoComp.PlayerDestoryBlock` in the loop to reduce the amount of calculation.

Wrong way of writing:

```python
for pos in blocks:
blockInfoComp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId)
blockInfoComp.PlayerDestoryBlock(pos,1,False)
```

Correct way of writing:

```python
blockInfoComp = serverApi.GetEngineCompFactory().CreateBlockInfo(playerId)
for pos in blocks:
blockInfoComp.PlayerDestoryBlock(pos,1,False)
```

Using the correct way of writing can greatly improve the running efficiency when the number of blocks to be destroyed is large.

This kind of mistake is made by many novices, so when we consult the interface, we can't just copy the sample code in the document directly into our project without thinking. We should think about what each line of code is used for. At the same time, it should be clear that every additional line of code executed will have a greater performance overhead. How to use faster code to achieve the same effect is worthy of our attention.

### Use xrange instead of range

xrange is a built-in function unique to Python 2. Its usage is exactly the same as range, except that it generates a generator instead of an array.

Compared with range, it has higher execution efficiency.

```python
for i in xrange(5):
print i
```


### Use dict to replace multi-branch if

Before modification:

```python
def getXXX(a):
if a == "a":
return 1
if a == "b":
return 2
if a == "c":
return 3
return 4
```

After modification:

```python
exampleDict = {"a":1,"b":2,"c":3}
def getXXX(a):
result = exampleDict.get(a)
if not result
return result
return 4
```

Compared with multiple ifs, using dictionaries to store data directly and getting and returning data through get will be more efficient when the amount of data is large.

