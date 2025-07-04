--- 
front: 
hard: Advanced 
time: 20 minutes 
--- 

# Get to know MODSDK 

#### Author: Boundary 

#### What is Mod 

The native AddOn method can change a lot of original game content and add custom game content, but it is generally unable to implement some more complex logic, such as giving items when right-clicking a custom block. This requires the use of scripts. 

In the Chinese version of Minecraft, we use python to write mod scripts. 

The Flower Group encapsulates many game events and components with MODSDK. Game events refer to the triggering of an operation or the reaching of a certain condition in the game (for example, the player right-clicks a custom block), which can notify our code and implement our logic. Components are our encapsulated game engine interfaces, which can be used to set or obtain certain data (such as operating the player's backpack, placing blocks), or perform some special functions. 

Script development is a process of listening to events and calling components, and combining your own logic to achieve cool gameplay. To learn about the latest events and interface documents, please read the <a href="../../../mcdocs/1-ModAPI/接口/通用/指数.html" rel="noopenner">official document website</a>. 

#### How Mod Works 

When loading a MOD, it is similar to an add-on pack. There are contents that run on the server and on the client separately. Therefore, the events and interfaces of the server and client are clearly separated in the MOD document. Common information such as the player's health, hunger, saturation, and the coordinates, behaviors, and properties of the creatures distributed in the world are all public resources, that is, they will be run on the server. Whenever the player needs to use this data, the client will request the server to obtain this data. Therefore, the interface for generating an entity creature will be used on the server because it is a public resource and it is synchronized. The interface for generating a special effect is used on the client, because just like the original particle resources are placed in the resource package, that is, run on the client, some particles will only be displayed when a player meets a certain condition, or such resources have different performances in front of different players. 

Therefore, some players often say that when the online room is opened, the performance of some #modules is no longer as stable as when playing alone. One of the reasons is that the room owner will bear the computing pressure of the client and the server at the same time, and will continue to accept the pressure of data requests from players in other rooms. This is a world of difference from the amount of data transmission required for single-player play, and network communication is required for transmission between the server and the client. When the network environment of the room owner is very different from that of other online members, it is easy to cause members to freeze and have a poor experience. Therefore, the task of optimization is always the most important hurdle for all developers. The better the optimization, the more players will naturally be reached, and the audience of the module will also increase! 

#### Development environment construction 

The development environment construction is mainly divided into two parts, one is the installation of Python, and the other is the installation of tools. The former can be understood as a programming language environment required for MOD work, just like the PC JAVA version of Minecraft must install the JAVA language environment before running. The latter can be understood as the construction of a production environment, that is, a series of supporting tools are needed for MOD programming operations. 

To install Python, you need to go to the Python official website to download and select the Python2 version [[https://www.python.org/downloads/](https://www.python.org/downloads/)]. At the same time, choose to download the installation file according to whether your computer is 64-bit or 32-bit. When installing, you need to choose to add python to the environment variable, and click Next for the rest. 

The production environment needs to configure production tools. The integrated development environment (IDE) can help us write code very well. For python, pycharm and vscode are both very good IDEs. Here we take pycharm as an example. Go to the official website download page of pycharm, select the Community version to download, and then click Next to install according to the prompts. 

Mod SDK completion allows the code editor to automatically complete the input content according to the context. 

In MCSTUDIO->Editor->Level Editor environment, click the menu bar [Tools] → [Install 1.22.0 stable completion library] to automatically install. If an error message is prompted, please check whether Python has been added to the environment variable. 



#### Getting started with Python 

Python is a very easy-to-learn programming language. Developers who have not been exposed to Python can first browse the following pages of [https://www.liaoxuefeng.com/wiki/897692888725344](https://www.liaoxuefeng.com/wiki/897692888725344) and follow the sample code above to learn about Python: 


The first Python program 

Using a text editor 

Python basics 

Data types and variables 

Conditional judgment and loops 

Using dict 

Functions 

Calling functions 

Defining functions 

Function parameters 

Modules 

Using modules 

Object-oriented programming 

Classes and examples 



#### Adding scripts to custom modules 

①Open the sample folder in the tutorial appendix, and you can see that the folder only contains the contents of the Beh (Behavior) behavior pack. In the Chinese version of Minecraft, it must be noted that the entities folder must be added to the behavior pack to be recognized as a behavior pack. Even if all the formats are correct, the recognition will fail without this folder. 

②In addition to the entities folder, there is a folder called TutorialStepOneScripts, which is used to store all MOD script files. One behavior pack can contain multiple script folders, but they must end with xxxScripts. 

③Create a modMain.py file in the folder, which is regarded as the entry file of the module. Currently, the name of the entry file cannot be determined by the developer, so this is a specification that must be followed. In addition, a new __init__.py file needs to be created in the folder to make this folder a module that can be imported by the script engine. If you follow the previously recommended Python online tutorial, you will understand this after learning to a certain extent. If you haven't learned it yet, just remember this point. You need to create such a __init__.py file in the module folder and its subfolders. 

④ Use any text editor or IDE to open the file, and you can see the code content inside. Their functions at this time will only output logs to the console when the game is loaded. Additional introduction will be in the next section. 

⑤ Compress the TutorialModBeh folder with zip and import it into MCSTUDIO to see it! 



#### Script structure 

① Then look at the second script folder in the TutorialBeh folder, namely TutorialStepTwoScripts. 
② Unlike the TutorialStepTwoScripts folder, we have officially added two files of our own here, one is ServerSys.py used as the server system, and the other is ClientSys.py used as the client system. The code logic of the former will only run on the server, and the code logic of the latter will only run on the client. Developers are also requested not to import the server interface on the client, and vice versa, which will cause the risk of abnormal operation of the module. 

③ServerSys can be created by developers as a new class. Before learning the object-oriented link, it can be simply understood as creating a system entrance, which is a class. It needs to inherit the official system class to use the MODSDK interface and listen to events in the game. The same is true for ClientSys. We will move the print information to the two system classes. When the game is opened later, these two information will be printed in the console under normal operation.


④ Back to modMain.py, we imported two new modules through the code prompt package provided by MODSDK above. Name the server module ServerApi, name the client module ClientApi, and register the system class in xxxSys.py in the entry function of the server. The working logic of our MOD will also be carried out there. 



#### Naming suggestions 

In order to facilitate developers to unify writing standards and avoid unnecessary conflict risks. The Flowering Group recommends using the team name [Scripts], such as SDKTeamTestScripts, to standardize the name of each script directory folder. 



#### How to debug 

The Mod code currently does not support breakpoint debugging, so the code can only be debugged by logging in different places. You can use print or logging modules to log (you will see it when reading AwesomeMod later). The log will be displayed in the "Script Test Log" window. It is best to add a special prefix to the script log for easy search. 

It is recommended to use the mod_log module to print logs. 

Currently, the Mod code supports hot update debugging. When running the game for development and testing, after adding, deleting, and modifying related local Python files, return to the Studio or editor interface, and Studio will automatically hot update the modified content and prompt "Reloading related Python modules" in the "Script Test Log" window. 



#### Let's get started 

First read the system introduction, event introduction, and component introduction, then start with modMain.py and read the code and comments of TutorialMod. 

After fully understanding, find a few things you are interested in from the server events and server components, try to add them to the mod, and see if they work! 

After mastering the usage of events and components, you can find sample modules of your interest from the official examples for practice, or continue to study the developer tutorial. 

After becoming familiar with the usage of modsdk, you can continue to read the "Advanced Features", "Object-Oriented Programming", and "Common Built-in Modules" on this website, which will help you write more complex gameplay logic using Python. 

When you encounter a problem that you cannot solve by yourself, communicate with the official in a timely manner (through the MC Studio built-in developer forum or web page), or try to seek help from others in the forum.