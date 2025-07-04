--- 
front: 
hard: Advanced 
time: 20 minutes 
--- 

# Performance switch 

​ Performance switch is divided into two types: unified and individual. 

​ Turn off/on the predefined game native logic as a whole. All logic defaults to [on] (that is, is_disable=False). Only when this interface is called to turn it off, it will enter the [off] state. Turning off this kind of native logic can improve the performance of the server and carry a higher number of people online at the same time. At the same time, it will also invalidate some survival server gameplay. In addition, it is strongly recommended to call this interface when the server is initialized, and do not modify it during the server operation. 

​ Turn off/on a game native logic. All logic defaults to [on] (that is, is_disable=False). 
Only when this interface is called to turn it off, it will enter the [off] state. Turning off this kind of native logic can improve the performance of the server, 
carry a higher number of people online at the same time, and at the same time, it will invalidate some survival server gameplay. In addition, it is strongly recommended to call this interface when the server is initialized, and do not modify it while the server is running. 

​ Performance switch <a href="../../../mcdocs/2-Apollo/4-SDK/6-Lobby and Game Service API.html#Performance Switch" rel="noopenner"> Introduction </a> 

​ 

