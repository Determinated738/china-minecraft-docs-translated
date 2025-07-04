# PE module adaptation to PC 

Since the original development goal of the PE module was to run on mobile terminals, neither the interface nor the logic can be directly used on the PC terminal. The most important limitation is the UI display and buttons. Because the interface input on the PE terminal comes from clicking on the screen, the display UI needs to have a button to receive the click event and the logic code to handle the button callback. On the PC terminal, most of the interface input can be replaced by keyboard events, and the UI display will inevitably be different. 

This course will teach the PE module adaptation to PC from two aspects: key binding adaptation and platform UI adaptation, and use the old version of the simple shooting template as an example to facilitate developers to understand. 

## Key binding adaptation 

In order to facilitate developers to adapt to PC buttons, the MCEditor level editor has added a key binding component. This component can help developers register custom events and bind custom events to keyboard, mouse and other buttons. When a keyboard button is pressed or lifted, the custom event will automatically call the <a href="../../../mcdocs/1-ModAPI/接口/通用/事件.html#notifytoserver" rel="noopenner"> NotifyToServer </a> interface to broadcast to the server, and automatically call the <a href="../../../mcdocs/1-ModAPI/界面/通用/事件.html#broadcastevent" rel="noopenner"> BroadcastEvent </a> interface to broadcast to the client. Developers only need to listen to the response of the custom event. 

### Key Binding Component 

Create a new key binding component in the level editor, as shown below. 

![20210828204839](./picture/peTOpc/20210828204839.png) 

After creation, click the key binding node to set the key binding in the property window. 

First, click the "+" button in the figure below to add a custom event binding. 

![20210828210231](./picture/peTOpc/20210828210231.png) 

Then fill in the custom event string and add several system keys you want to bind, as shown below. 

![20210828213107](./picture/peTOpc/20210828213107.png) 

After completing the binding, when the module is running and the Backspace or Enter key is pressed, the MyEvent custom event will be triggered, and the developer can listen to the MyEvent event and perform corresponding callback processing on the client and server.

### Key binding in the old version of the simple shooting template 

There are three buttons in the interface of the simple shooting template, corresponding to the shooting, aiming, and reloading functions, and a function that is very commonly used in shooting games to press the Alt key to call out the mouse, so the key binding component can be used for reconstruction. 

![20210828215544](./picture/peTOpc/20210828215544.png) 

As shown in the figure, four custom events are registered, ReloadEvent binds the R key to reload, Shoot binds the F key to shoot, AimEvent binds the Tab key to aim, and AltEvent binds the Alt key to call out the mouse. 

Take the shooting as an example. After the binding is completed, listen to the Shoot event in the server code and write a callback to execute the shooting logic when the F key is pressed. 

```python
class FpsServerSystem(ServerSystem):
    def ListenEvent(self):
        ...
        self.ListenForEvent(inputBindConfig.ModName, inputBindConfig.InputBindClientSystem, modConfig.ShootEvent, self, self.OnKeyBoardShoot)

    def OnKeyBoardShoot(self, args):
        isDown = args["isDown"]
        if isDown == '0':
            self.OnShoot(args)

```


## Platform UI Adaptation 

Due to the different operations of PE and PC, the performance of UI is also different, so we need to create different UIs according to the current platform. 

Here, we directly use the <a href="../../../mcdocs/1-ModAPI/接口/通用/地方设备.html#getplatform" rel="noopenner"> GetPlatform </a> interface to obtain, and then create different UIs according to the returned results. 

### Platform UI Adaptation in the Old Version of Simple Shooting Template 

Here is the code directly. 

```python
    def OnUIInitFinished(self, args):
        ...
        if clientApi.GetPlatform() == 0:
            self.mFpsBattleUINode = clientApi.CreateUI(modConfig.ModName, modConfig.FpsBattlePCUIName, {"isHud": 1})
        else:
            self.mFpsBattleUINode = clientApi.CreateUI(modConfig.ModName, modConfig.FpsBattleUIName, {"isHud": 1}) 

``` 

The interface displayed on the PC is as shown in the figure 

![20210828222031](./picture/peTOpc/20210828222031.png) 

The interface displayed on the PE is as shown in the figure 

![20210828222138](./picture/peTOpc/20210828222138.png)