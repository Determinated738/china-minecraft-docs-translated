--- 
sidebarDepth: 1 
--- 

# <span id="Launcher Information API"></span>Launcher Information API 

The following interface is used to obtain launcher information 

<span id="Player"></span> 
### Player 

<span id="ApplyUserFriend"></span> 
#### ApplyUserFriend 

- Description 

**Lobby/Game interface**, apply to be added as a friend in the launcher 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| requestUID | int | Player's uid | 
| appliedUID | int | Player's uid | 
| message | str | Description of the friend applied for | 
| callback | function | Callback function, the function has only one dict type parameter. Dict description: "code": status code, 0 means successful, others mean failed; "message": status information; "details": detailed information of the status, an empty string; "entity": a dictionary, containing the field b_success, b_success indicates whether the application is successful. | 
- Return value 

None 
- Example 

```python 
def callback(response): 
#Application success return example: {u'message': 'Normal return', u'code': 0, u'details': u'', u'entity': {u'b_success': true}} 
#Application failure return example: {u'message': 'Normal return', u'code': 0, u'details': u'', u'entity': {u'b_success': false}} 
#Error return example: {u'message': 'Parameter error', u'code': 1, u'details': u'', u'entity': ''} 
print 'callback', response 
import apolloCommon.launcherApi as launcherApi 
launcherApi.ApplyUserFriend(123, 456, 'I want to add a friend', callback) 
``` 
<span id="GetPcGameUserLike"></span> 
#### GetPcGameUserLike 

- Description 

**Master/Service/Lobby/Game interface**, get whether the player has liked the current network service (only supports PC players) 

- Parameters 

| Parameter name | Data type | Description |

| :--- | :--- | :--- | 
| uid | int/long | Player's PC uid | 
| callback | function | Callback function, the function has only one dict type parameter. dict description: "code": status code, 0 means correct, other means failed; "message" status information; "details": detailed information of the status, an empty string; "entity": a dictionary containing the field is_like, the value is bool, indicating whether the player likes it | 
- Return value 

None 
- Example 

```python 
def callback(response): 
#Normal return example: {u'message': 'Normal return', u'code': 0, u'details': u'', u'entity': {u'is_like': True}} 
#Error return example: {u'message': 'Parameter error', u'code': 1, u'details': u'', u'entity': ''} 
print 'callback', response 
import apolloCommon.launcherApi as launcherApi 
launcherApi.GetPeGameUserStars(123, callback) 
``` 
<span id="GetPeGameUserStars"></span> 
#### GetPeGameUserStars 

- Description 

**Master/Service/Lobby/Game interface**, get the player's rating of this game 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player's uid | 
| callback | function | Callback function, the function has only one dict type parameter. Dict description: "code": status code, 0 means correct, other means failed; "message" status information; "details": detailed information of the status, empty string; "entity": a dictionary, containing the field stars, indicating the player's rating, the normal rating range is 1-5, and the value -1 means there is no rating data. | 
- Return value 

None 
- Example 

```python 
def callback(response): 
#Normal return example:{u'message': 'Normal return', u'code': 0, u'details': u'', u'entity': {u'stars': 1}} 
#Error return example:{u'message': 'Parameter error', u'code': 1, u'details': u'', u'entity': ''} 
print 'callback', response 
import apolloCommon.launcherApi as launcherApi 
launcherApi.GetPeGameUserStars(123, callback) 
``` 
<span id="GetUIDByNickname"></span> 
#### GetUIDByNickname 

- Description 

**Master/Service/Lobby/Game interface**, get the player uid based on the player nickname 

- Parameters


| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| nickname | str | Player nickname, utf8 encoding required | 
| callback | function | Callback function, the function has only one dict type parameter. Dict description: "code": status code, 0 means correct, other means failed; "message" status information; "details": detailed information of the status, an empty string; "entity": a dictionary containing the field uid, which indicates the player's uid. | 
- Return value 

None 
- Example 

```python 
def callback(response): 
#Normal return example:{u'message': 'Normal return', u'code': 0, u'details': u'', u'entity': {u'uid': 2147583768}} 
#Error return example:{u'message': 'Parameter error', u'code': 1, u'details': u'', u'entity': ''} 
print 'callback', response 
import apolloCommon.launcherApi as launcherApi 
launcherApi.GetUIDByNickname('My nickname', callback) 
``` 
<span id="GetUserAuthInfo"></span> 
#### GetUserAuthInfo 

- Description 

**Master/Service/Lobby/Game interface**, get the real-name system and binding information of online players 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player's uid | 
| callback | function | Callback function, the function has only one dict type parameter. dict description: "code": status code, 0 means correct, other means failed; "message" status information; "details": detailed information of the status, empty string; "entity": a dictionary containing the following fields: b_real_name indicates whether the player is real-name registered, id_hash indicates the unique identifier of the player's identity, empty if not real-name registered (multiple accounts can be bound to one ID card, this field can be used to determine whether multiple accounts are bound to one identity), b_bind_phone indicates whether the player is bound to a phone | 
- Return value 

None 
- Example 

```python 
def callback(response): 
#Normal return example, player real-name authentication and bound phone:{u'message': 'Normal return', u'code': 0, u'details': u'', u'entity': {u'b_real_name': True, u'id_hash':u'92251e8665e19be62c86ff039528e16e', u'b_bind_phone':True}} 
#Error return example:{u'message': 'Parameter error', u'code': 1, u'details': u'', u'entity': ''} 
print 'callback', response 
import apolloCommon.launcherApi as launcherApi 
launcherApi.GetUserAuthInfo(123, callback) 
``` 
<span id="GetUserFriend"></span> 
#### GetUserFriend 

- Description 

**Master/Service/Lobby/Game interface**, get player friend information in the launcher


- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player's uid | 
| callback | function | Callback function, the function has only one dict type parameter. Dict description: "code": status code, 0 means correct, other means failed; "message" status information; "details": detailed information of the status, an empty string; "entity": a dictionary, containing the field friend_uids, the corresponding content of friend_uids is a list, corresponding to the friend player uid list. | 
- Return value 

None 
- Example 

```python 
def callback(response): 
#Normal return example:{u'message': 'Normal return', u'code': 0, u'details': u'', u'entity': {u'friend_uids': [234,456]}} 
#Error return example:{u'message': 'Parameter error', u'code': 1, u'details': u'', u'entity': ''} 
print 'callback', response 
import apolloCommon.launcherApi as launcherApi 
launcherApi.GetUserFriend(123, callback) 
``` 
<span id="GetUserGuest"></span> 
#### GetUserGuest 

- Description 

**Master/Service/Lobby/Game interface**, get the information whether the player in the launcher is a guest, this interface has been abandoned 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player's uid | 
| callback | function | Callback function, the function has only one dict type parameter. Dict description: "code": status code, 0 means correct, other means failed; "message" status information; "details": detailed information of the status, an empty string; "entity": a dictionary, including the field guest, indicating whether the player is a guest, the field meaning 0: non-guest, 1: guest, 2: uncertain. | 
- Return value 

None 
- Remarks 

Except for the official website channel and Apple channel, other third-party channel launchers cannot return confirmed visitor information, and the guest field returns 2 

This interface has been deprecated 


- Example 

```python 
def callback(response): 
#Normal return example: {u'message': 'Normal return', u'code': 0, u'details': u'', u'entity': {u'guest': 1}} 
#Error return example: {u'message': 'Parameter error', u'code': 1, u'details': u'', u'entity': ''} 
print 'callback', response

import apolloCommon.launcherApi as launcherApi 
launcherApi.GetUserGuest(123, callback) 
``` 
<span id="GetUsersVIP"></span> 
#### GetUsersVIP 

- Description 

**Master/Service/Lobby/Game interface**, get player membership information in the launcher 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uids | list(int/long) | Player uid list, list length does not exceed 20 | 
| callback | function | Callback function, which will be executed asynchronously. The function has only one dict type parameter. Dict description: "code": status code, 0 means correct, other means failed; "message" status information; "details": detailed information of the status, empty string; "entity": a dictionary, including the field users_vip, the corresponding content of users_vip is a dict, key represents the player's uid, value represents whether it is a vip. | 
- Return value 

None 
- Remarks 

Only member information of players who have experienced this game can be obtained. Requires to configure the game ID in MCStudio (path: server configuration->more->game ID) 


- Example 

```python 
def callback(response): 
#Normal return example:{u'message': 'Normal return', u'code': 0, u'details': u'', u'entity': {u'users_vip': {u'123': True}}} 
#Error return example:{u'message': 'Parameter error', u'code': 1, u'details': u'', u'entity': ''} 
print 'callback', response 
import apolloCommon.launcherApi as launcherApi 
launcherApi.GetUsersVIP([123], callback) 
``` 
<span id="IsGameUnderMaintenance"></span> 
#### IsGameUnderMaintenance 

- Description 

**Master/Service/Lobby/Game interface**, whether the game is under maintenance 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| callback | function | Callback function, the function has only one dict type parameter. Dict description: "code": status code, 0 means correct, other means failed; "message" status information; "details": detailed information of the status, an empty string; "entity": a dictionary containing the field b_maintain, indicating whether the player is under maintenance. | 
- Return value 

None 
- Example


```python 
def callback(response): 
#Normal return example, game maintenance: {u'message': 'Normal return', u'code': 0, u'details': u'', u'entity': {u'b_maintain': True}} 
#Error return example: {u'message': 'Parameter error', u'code': 1, u'details': u'', u'entity': ''} 
print 'callback', response 
import apolloCommon.launcherApi as launcherApi 
launcherApi.IsGameUnderMaintenance(callback) 
``` 
<span id="ShareApolloGame"></span> 
#### ShareApolloGame 

- Description 

**Lobby/Game interface**, pull up the "Online Game Sharing" interface on RN, the interface includes the game ICON and description 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player's uid | 
| message | str | Description of sharing, cannot exceed 20 characters, requires passing in utf8 string | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Whether the sharing interface is successfully pulled up. False: There are sensitive words or the game ID is 0 or the player is not online or the shared information exceeds 20 characters | 
- Notes 

This function can only be called in the lobby server and game server, and does not support the function server and control server environment 

This function only supports players who log in on the mobile phone 


- Example 

```python 
import apolloCommon.launcherApi as launcherApi 
# Note that utf8 string is required 
ret = launcherApi.ShareApolloGame(123, u'This game is pretty good, everyone try it') 
``` 
