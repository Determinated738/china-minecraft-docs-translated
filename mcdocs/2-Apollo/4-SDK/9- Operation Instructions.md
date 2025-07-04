# Operation instructions 

- Usage 
``` 
post url: http:masterip:masterport/baseurl 
post body: 
json format, for example: 
{ 
"serverId":3, 
"ip":"192.168.43.170", 
"port":12001, 
"masterPort":12002, 
"type":"lobby" 
} 
response: 
json format, format: 
{ 
"code":1, #1 is success, 2 is failure 
"message":"reason",#If it fails, introduce the reason for failure 
"entity":content #Detailed information 
} 
``` 
Developers can log in to the machine where the master is located and use the curl command to send a request. The usage is as follows: 
``` 
curl -X POST http://masterip:masterport/baseurl -d 'postbody' 
``` 
If you use the "/online-num/query" command to get the number of online game users, you can send the following curl command on the master: 
``` 
curl -X POST http://11.11.11.11:8503/online-num/query -d '{"server_type":"game"}' 
``` 
If you need to use the mall plug-in neteaseShop to query the order operation command (/check-single-order command), you can send the following curl command on the master: 
``` 
curl -X POST http://11.11.11.11:8503/check-single-order -d '{"orderid" : 1234,"uid" : 123456789}' 
``` 

## Query UID 

* **/netease/get-online-uids** 

- Description 

Query the uid of the current online player 

- No post body json parameter 

- Response entity parameter 
dict. The key is the server id, and the value is the list of online player uids; when there is no player in the corresponding server, the server id will not appear as a key 

- Example: 
```

post url: http://111.222.333.444:1101/netease/get-online-uids 
post body: 
{ 
} 
response: 
{ 
"code": 0, 
"message": "", 
"entity": { 
"4000":[1989540401,2147585444] 
} 
} 
``` 

* **/netease/get-lazy-uids** 

- Description 

Query the uid of the player who recently requested to log in and the time of the request to log in 

- No post body json parameter 

- response entity parameter 
list(string). Each record contains the uid and the time of the corresponding login request, sorted by the time of the login request (the more recent the better); up to 30 records 

- Example: 
``` 
post url: http://111.222.333.444:1101/netease/get-lazy-uids 
post body: 
{ 
} 
response: 
{ 
"code": 0, 
"message": "", 
"entity": { 
"uid=680116908 login=2021-05-26 15:12:41", 
"uid=1989540401 login=2021-05-26 15:12:08", 
"uid=2147585444 login=2021-05-26 15:11:24" 
} 
} 
``` 

## Number of online players 
* **/netease/update-player-online-limit** 

- Description 

Modify the global maximum number of online players at the same time 


- post body parameter 

| keyword | data type | description | 
| ---------- | -------- | ------------ | 
| online_limit | int | The maximum number of people online at the same time that needs to be set. When set to 0, it means that there is no limit on the maximum number of people online at the same time| 

- response entity parameter 
| keyword | data type | description | 
| ---------- | -------- | ------------ | 
| code | int | The return code of the entire command, 1 for success, other numbers for failure| 
| message | str | The return result description of the entire command, generally empty for success, and the reason for failure will be described for failure| 
| entity | dict | The keyword version is the version number of the global simultaneous online limit in the current configuration file, which is temporarily useless; the keyword old_online_limit is the global maximum number of people online at the same time before the modification. Returning 0 means that there is no limit on the maximum number of people online at the same time before the modification| 

- Example: 
``` 
post url: http://111.222.333.444:1101/netease/update-player-online-limit 
post body: 
{ 
"online_limit":8000 
} 
response: 
{ 
"code": 1, 
"entity": { 
"version": 0, 
"old_online_limit": 6000 
}, 
"message": "" 
} 
``` 

* **/online-num/query** 

- Description 

Get the number of online players of proxy/lobby/game or the total number of online players. 

- post body parameter 

| keyword | data type | description | 
| ---------- | -------- | ------------ | 
| serverType | str | server type, such as "lobby", "game", "proxy", if this value is not passed in, it means the total number of online users| 

- response entity parameter 
| keyword | data type | description | 
| ---------- | -------- | ------------ | 
| onlineNum | int | number of online users| 
- example: 
``` 
post url: http://111.222.333.444:1101/online-num/query

post body: 
{ 
"serverType":"game" 
} 
response: 
{ 
"code": 1, 
"entity": { 
"onlineNum": 0 
}, 
"message": "" 
} 
``` 

* **/online-num/query-by-server-id** 

- Description 

Get the number of online users of a proxy/game/lobby 

- post body parameters 

| Keywords | Data type | Description | 
| ---------- | -------- | ------------ | 
| serverId | int | server id| 

- response entity parameters 
| Keywords | Data type | Description | 
| ---------- | -------- | ------------ | 
| onlineNum | int | number of online users| 
- Example: 

``` 
post url: http://111.222.333.444:1101/online-num/query-by-server-id 
post body: 
{ 
"serverId":1 
} 
response: 
{ 
"code": 1, 
"entity": { 
"onlineNum": 2 
}, 
"message": "" 
} 
``` 

## Log level 


* **/conf/set-log-debug-level** 

- Description 

Set the log level of the server startup tool to debug or info level 

- Post body parameter 

| Keyword | Data type | Description | 
| ---------- | -------- | ------------ | 
| debugLevel | bool | true: log is set to debug log level; false: log is set to info log level | 

- No response entity parameter 

- Example: 
``` 
post url: http://111.222.333.444:1101/conf/set-log-debug-level 
post body: 
{ 
"debugLevel":false 
} 
response: 
{ 
"code": 1, 
"entity": null, 
"message": "" 
} 
``` 

* **/conf/set-server-log-debug-level** 

- Description 

Set the log level of a server. 

- post body parameters 

| Keywords | Data type | Description | 
| ---------- | -------- | ------------ | 
| serverId | int | Server id. It can be the serverid of proxy, lobby, game, service. If it is 0, it means master. | 
| debugLevel | bool | true: the log is set to debug log level; false: the log is set to info log level | 

- No response entity parameter 

- Example: 
``` 
post url: http://111.222.333.444:1101/conf/set-server-log-debug-level 
post body: 
{ 
"serverId":1,

"debugLevel":false 
} 
response: 
{ 
"code": 1, 
"entity": null, 
"message": "" 
} 
``` 
## Server 

* **/query-all-server-status** 

- Description 

Query all server status 

- No post body json parameter 

- Response entity parameter 
dict. key is server id, value is server status. The server status are: 
1: disconnected state 
2: connected state 
3: shutdown state 
4: graceful shutdown state 
6, rolling update intermediate state, about to switch to state 7 
7 is also a rolling update intermediate state, about to switch to state 1 or 2 

- Example: 
``` 
post url: http://111.222.333.444:1101/query-all-server-status 
post body: 
{ 
} 
response: 
{ 
"code": 1, 
"entity": { 
"1": 1, 
"2": 1 
} 
"message": "" 
} 
``` 

* **/query-one-server-status** 

- Description 


Query a server status 

- post body parameters 

| keywords | data type | description | 
| ---------- | -------- | ------------ | 
| serverId | int | proxy/lobby/game server id | 

- response entity parameters 

| keywords | data type | description | 
| ---------- | -------- | ------------ | 
| status | int | Server status. The server status is as follows: <br/> 1: disconnected status <br/> 2: connected status <br/> 3: shutdown status <br/> 4: graceful shutdown status <br/> 6, rolling update intermediate status, about to switch to status 7 <br/> 7 is also a rolling update intermediate status, about to switch to status 1 or 2 | 

- Example: 
``` 
post url: http://111.222.333.444:1101/query-one-server-status 
post body: 
{ 
"serverId":1 
} 
response: 
{ 
"message": "", 
"code": 1, 
"entity": { 
"status": 1 
} 
} 
``` 
## mute, unmute 

* **/silent** 

- Description 

mute a player 

- post body json parameter 

| keyword | data type | description | 
| ------------ | -----------| ------------ | 
| uid |int | player id | 
| banTime |int | ban time, in seconds, -1 means permanent ban| 
| reason |str | ban reason| 
| type |str | ban type, customizable, public screen ban is `Commom`| 

- No response entity parameter 

- Example:

``` 
post url: http://111.222.333.444:1101/silent 
post body: 
{ 
"uid":11111, 
"banTime":40, 
"reason":"Player cheating", 
"type":"Common" 
} 
response: 
{ 
"code": 1, 
"entity": null, 
"message": "" 
} 
``` 

* **/unban-silent** 

- Description 

Unban a player 

- post body json parameter 

| Keyword | Data type | Description | 
| ------------ | -----------| ------------ | 
| uid |int | Unban player's uid| 
| type |str | Ban type, customizable, public screen ban is `Commom`| 

- No response entity parameter 

- Example: 
``` 
post url: http://111.222.333.444:1101/unban-silent 
post body: 
{ 
"uid":11111, 
"type":"Commom" 
} 
response: 
{ 
"code": 1, 
"entity": null, 
"message": "" 
} 
``` 

* **/global-silent** 


- Description 

Global public screen mute switch 

- Post body json parameter 

| Keyword | Data type | Description | 
| ------------ | -----------| ------------ | 
| isSilent |bool | Global mute switch, `true` means to turn on global mute, `false` means to turn off global mute| 
| reason |str | Reason for mute| 

- No response entity parameter 

- Example: 
``` 
Post url: http://111.222.333.444:1101/global-silent 
Post body: 
{ 
"isSilent":true, 
"reason":"System maintenance" 
} 
response: 
{ 
"code": 1, 
"entity": null, 
"message": "" 
} 
``` 

## Kick out the player 

* **/kickout-user** 

- Description 

Kick a player out of the game 

- Post body json parameters 

| Keywords | Data type | Description | 
| ------------ | -----------| ------------ | 
| uid |int | UID of the kicked player| 
| reason |str | Reason for kicking out| 

- No response entity parameter 

- Example: 
``` 
Post url: http://111.222.333.444:1101/kickout-user 
Post body:

{ 
"uid":11111, 
"reason":"Player cheating", 
} 
response: 
{ 
"code": 1, 
"entity": null, 
"message": "" 
} 
``` 
## Ban, unban 

* **/ban-user** 

- Description 

Ban a player 

- Post body json parameter 

| Keyword | Data type | Description | 
| ------------ | -----------| ------------ | 
| uid |int | The uid of the banned player| 
| banTime |int | Ban time, in seconds, -1 means permanent ban| 
| reason |str | Ban reason| 
| bCombineReason |bool | Whether to display the ban reason in combination. If True, handle as described in the notes, otherwise the banned player will be prompted with [reason] when logging in | 

- No response entity parameter 

- Example: 
``` 
post url: http://111.222.333.444:1101/ban-user 
post body: 
{ 
"uid":11111, 
"banTime":40, 
"reason":"Player cheating", 
} 
response: 
{ 
"code": 1, 
"entity": null, 
"message": "" 
} 
``` 
- Note 
If banTime>0, the banned player will be prompted with the following login message: Your account has been banned, remaining ban time: x days y hours z minutes, ban reason: [reason]. If you have any questions, please go to the customer service area to give feedback. 
If banTime=-1, the banned player will be prompted to log in: Your account has been permanently banned, ban reason: [reason]. If you have any questions, please go to the customer service area to give feedback. 


* **/unban-user** 

- Description 

Unban a player 

- Post body json parameter 

| Keyword | Data type | Description | 
| ------------ | -----------| ------------ | 
| uid |uint32 | Unban player's uid| 

- No response entity parameter 

- Example: 
``` 
Post url: http://111.222.333.444:1101/unban-user 
Post body: 
{ 
"uid":11111, 
} 
Response: 
{ 
"code": 1, 
"entity": null, 
"message": "" 
} 
``` 
## Force the player to be released online 

* **/netease/release-online-lock** 

- Description 

Forcefully remove the online identification of the player with the specified UID 

- post body json parameter 

| Keywords | Data type | Description | 
| ------------ | -----------| ------------ | 
| uidList |list(int) | List of UIDs of players whose online identification needs to be removed| 

- response entity parameter 
| Keywords | Data type | Description | 
| ---------- | -------- | ------------ | 
| sucUids | list(int) | List of UIDs whose online identification of players is successfully removed, including those who are no longer online at the time of the request| 
| failUids | list(int) | List of UIDs whose online identification of players fails to be removed| 

- Example: 
```

post url: http://111.222.333.444:1101/netease/release-online-lock 
post body: 
{ 
"uidList":[2147585444,2819362897], 
} 
response: 
{ 
"code": 1, 
"message": "", 
"entity": { 
"sucUids": [2147585444,2819362897], 
"failUids": [] 
} 
} 
``` 

* **/netease/release-online-lock-by-server** 

- Description 

Forcefully remove the online identification of the current online player on the specified ID server 

- post body json parameters 

| Keywords | Data type | Description | 
| ------------ | -----------| ------------ | 
| serverId |list(int) | Server IDs that need to be released online| 

- response entity parameters 
| Keywords | Data type | Description | 
| ---------- | -------- | ------------ | 
| sucUids | list(int) | List of UIDs that successfully released online player IDs| 
| failUids | list(int) | List of UIDs that released online player IDs| 

- Example: 
``` 
post url: http://111.222.333.444:1101/netease/release-online-lock-by-server 
post body: 
{ 
"serverId": 4000, 
} 
response: 
{ 
"code": 1, 
"message": "", 
"entity": { 
"sucUids": [2147585444,2819362897],
           "failUids": []
         }
     }

``` 

## Service shutdown for maintenance 

* **/invalid-all-servers** 

- Description 

Enable/disable service shutdown for maintenance 

- Post body json parameter 

| Keyword | Data type | Description | 
| ------------ | -----------| ------------ | 
| invalid |bool | Service shutdown for maintenance switch, `true` means to enable service shutdown for maintenance, `false` means to disable service shutdown for maintenance | 
| reason |str | Service shutdown for maintenance reason | 

- No response entity parameter 

- Example: 
``` 
Post url: http://111.222.333.444:1101/invalid-all-servers 
Post body: 
{ 
"invalid":true, 
"reason":"Service shutdown for maintenance", 
} 
Response: 
{ 
"code": 1, 
"entity": null, 
"message": "" 
} 
``` 
## Hunter debugging command 

* **/netease/hunter-debug** 

- Description 

Make the destination server execute the Python script. The information printed by **print** in the script will be reflected in the request response. At the same time, it will also be printed in the log file of the destination server, specifically the following n lines of the "hunterDebug exec" log. 

- post body json parameter 

| Keywords | Data type | Description | 
| ------------ | -----------| ------------ | 
| opServerIds |list(int) |Optional parameter, list of server IDs that need to execute the python script, 0 means master| 
| opServerType |str |Optional parameter, list of server types that need to execute the python script| 
| script |str | Python script that the server needs to execute, use `\n` to wrap lines|

| command |str | console command that the server needs to execute| 

- response entity parameters 
dict. key is the server id, value is also a dict with two keys, code and message 
code=0 means the script is executed successfully on the corresponding server, and the information in the message is the information printed by **print** in the script; 
code=1 means the script fails to be executed on the corresponding server, and the information in the message is the reason for the failure; 

- Example: 
``` 
post url: http://111.222.333.444:1101/netease/hunter-debug 
post body: 
{ 
"opServerIds": [0,8000,4000,6000], 
"script":"import time\nprint time.time()" 
} 
response: 
{ 
"code": 0, 
"message": "", 
"entity": { 
"0": {"message": "1623327430.98\n", "code": 0},
"4000": {"message": "1623327431.04\n", "code": 0}, 
"6000": {"message": "1623327431.04\n", "code": 0}, 
"8000": {"message": "1623327431.04\n", "code": 0} 
} 
} 
The corresponding server log file contains the following log: 
[2019-06-03 10:21:29 INFO] Python:hunterDebug exec 
[2019-06-03 10:21:29 INFO] Python:1559543269.12 
``` 

* **/hunter-debug** 

- Description 

Make the destination server execute the Python script, and print the result to the log file of the destination server, specifically the following n lines of the "hunterDebug exec" log. 

- post body json parameter 

| Keywords | Data type | Description | 
| ------------ | -----------| ------------ | 
| serverId |int | Server corresponding ID, 0 represents master| 
| script |str | Python script that the server needs to execute, use `\n` to wrap lines| 
| command |str | Console command that the server needs to execute| 

- No response entity parameter 

- Example: 
``` 
post url: http://111.222.333.444:1101/hunter-debug

post body: 
{ 
"serverId":101, 
"script":"import time\nprint time.time()" 
} 
response: 
{ 
"code": 1, 
"entity": null, 
"message": "" 
} 
The 101 server log file contains the following logs: 
[2019-06-03 10:21:29 INFO] Python:hunterDebug exec 
[2019-06-03 10:21:29 INFO] Python:1559543269.12 
``` 
## Performance Analysis 

* **/check-memory-run** 

- Description 

Check for memory leaks at the server script layer. Two instructions need to be executed, the first to generate a snapshot, and the second to generate a diff with the first. 

- post body json parameter 

| keyword | data type | description | 
| ------------ | -----------| ------------ | 
| serverId |int || 
| useList |list | usually ["tracemalloc", "objreport"]| 
| objNames |list | usually empty| 

- no response entity parameter 

- example: 
``` 
post url: http://111.222.333.444:1101/check-memory-run 
post body: 
{ 
"serverId":101, 
"useList":["tracemalloc", "objreport"], 
"objNames":[] 
} 
response: 
{ 
"code": 1, 
"entity": null, 
"message": "" 
} 

The server log file contains the following logs:

	[2019-09-11 17:09:33 INFO] Python: run_tracemalloc traceback
	[2019-09-11 17:09:33 INFO] Python:[Top 10 differences]
	[2019-09-11 17:09:33 INFO] Python:/tmp/tmpxlycSu/scripts/mod/server/memory/obj_report.py:43: size=12.0 KiB (+12.0 KiB), count=1 (+1), average=12.0 KiB
	[2019-09-11 17:09:33 INFO] Python:/tmp/tmpxlycSu/scripts/mod/server/memory/obj_report.py:45: size=10.0 KiB (+10.0 KiB), count=11 (+11), average=992 B
	[2019-09-11 17:09:33 INFO] Python:/tmp/tmpxlycSu/scripts/mod/server/memory/check_memory.py:61: size=10.0 KiB (+10.0 KiB), count=127 (+127), average=84 B
	[2019-09-11 17:09:33 INFO] Python:/tmp/tmpxlycSu/scripts/mod/server/memory/obj_report.py:12: size=1736 B (+1736 B), count=6 (+6), average=289 B
	[2019-09-11 17:09:33 INFO] Python:/tmp/tmpxlycSu/scripts/mod/server/memory/obj_report.py:6: size=1007 B (+1007 B), count=5 (+5), average=201 B
	[2019-09-11 17:09:33 INFO] Python:/usr/local/lib/python2.7/site-packages/tracemalloc.py:380: size=864 B (+864 B), count=4 (+4), average=216 B
	[2019-09-11 17:09:33 INFO] Python:/usr/local/lib/python2.7/json/decoder.py:380: size=704 B (+704 B), count=11 (+11), average=64 B
	[2019-09-11 17:09:33 INFO] Python:/usr/local/lib/python2.7/site-packages/tracemalloc.py:518: size=672 B (+672 B), count=4 (+4), average=168 B
	[2019-09-11 17:09:33 INFO] Python:<unknown>:0: size=650 B (+650 B), count=2 (+2), average=325 B
	[2019-09-11 17:09:33 INFO] Python:/tmp/tmpxlycSu/scripts/mod/server/memory/check_memory.py:66: size=544 B (+544 B), count=1 (+1), average=544 B
	[2019-09-11 17:09:33 INFO] Python:[QA] [DIFF_MORE]
	[2019-09-11 17:09:33 INFO] Python:[QA] [DIFF_LESS] 
[2019-09-11 17:09:33 INFO] Python:-2 <type 'tuple'> 
Log description, prints the top ten files with memory changes between two [/check-memory] commands, and reduces 2 tuple instances between the two commands. 
``` 

* **/profile** 
- Description 

Used to measure the CPU time occupied by Python functions. Two commands need to be executed, the first to start the profile and the second to generate the performance data file. The performance data file is placed in the profile subdirectory under the directory where the execution file is located. The format of the performance data file name: profile+timestamp of the generated file 
- post body json parameter 

| Keywords | Data type | Description | 
| ------------ | -----------| ------------ | 
| serverId |int ||Server corresponding ID. 0 means master, -1 means all servers, and others mean the server ID of lobby/game/service| 
| bBegin |bool |true: start profile; false: complete profile| 

- No response entity parameter 
- Example: 
``` 
Performance data file name: profile_1574325974 
File content: 
33 function calls in 0.000 seconds 

Ordered by: internal time 

ncalls tottime percall cumtime percall filename:lineno(function) 
1 0.000 0.000 0.000 0.000 {_log.logInfo} 
2 0.000 0.000 0.000 0.000 logout.py:83(write) 
1 0.000 0.000 0.000 0.000 logout.py:62(split_and_log)
        1 0.000 0.000 0.000 0.000 netServerApp.py:17(TickApp)
        1 0.000 0.000 0.000 0.000 Queue.py:93(empty)
        1 0.000 0.000 0.000 0.000 timer.py:72(scheduler)
        1 0.000 0.000 0.000 0.000 idvScript.modMaster.httpHandlerSys:141(Update)
        1 0.000 0.000 0.000 0.000 async_task_pool.py:293(schedule)
        1 0.000 0.000 0.000 0.000 netgameApp.py:3(Tick) 
1 0.000 0.000 0.000 0.000 async_task_pool.py:302(exec_callback)

        2 0.000 0.000 0.000 0.000 {len}
        1 0.000 0.000 0.000 0.000 baseApp.py:73(ClearNeedsUpdate)
        5 0.000 0.000 0.000 0.000 {method 'has_key' of 'dict' objects}
        1 0.000 0.000 0.000 0.000 {time.time}
        1 0.000 0.000 0.000 0.000 {method 'acquire' of 'thread.lock' objects}
        1 0.000 0.000 0.000 0.000 {method 'replace' of 'str' objects}
        2    0.000 0.000 0.000 0.000 {method 'splitlines' of 'str' objects}
        1 0.000 0.000 0.000 0.000 mongopool.py:194(tick)
        1 0.000 0.000 0.000 0.000 redispool.py:274(do_tick)
        1 0.000 0.000 0.000 0.000 Queue.py:200(_qsize)
        1 0.000 0.000 0.000 0.000 memoryScripts.MasterMemorySys:21(Update)
        1 0.000 0.000 0.000 0.000 {method 'release' of 'thread.lock' objects} 
1 0.000 0.000 0.000 0.000 redispool.py:271(tick) 
3 0.000 0.000 0.000 0.000 baseSystem.py:86(Update) 
Content interpretation: 
First line: 33 function calls are monitored, and the total CPU running time of these functions is 0.000 seconds 
Next, the meaning of the output fields: 
ncalls: indicates the number of function calls; 
tottime: indicates the total running time of the specified function, excluding the running time of the sub-functions called in the function; 
percall: (the first percall) is equal to tottime/ncalls; 
cumtime: indicates the calling and running time of the function and all its sub-functions, that is, the time from the start of the function call to the return; 
percall: (the second percall) is the average time for the function to run once, which is equal to cumtime/ncalls; 
filename:lineno(function): Detailed information of each function call; 

```