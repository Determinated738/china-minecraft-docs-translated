--- 
sidebarDepth: 1 
--- 

# <span id="7-Public API"></span>7-Public API 

Below is the interface of the asynchronous task pool 

<span id="Asynchronous thread pool"></span> 
### Asynchronous thread pool 

<span id="EmitOrder"></span> 
#### EmitOrder 

- Description 

Add an asynchronous task 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| key | string/int | Tasks with the same key are executed sequentially by the thread pool; tasks with different keys are executed in parallel by the thread pool. You can confirm that some tasks are executed in sequence. | 
| func | function | The function corresponding to the task, which will run in the thread pool. The task and the main thread will be executed in parallel, and you need to confirm that the task is thread-safe. The function must return a tuple. If the return value is empty, an empty tuple ("()") is required. The function input parameter is *args | 
| callback | function | callback function, which is executed in the main thread. The return value of func will be the actual parameter of callback. If there is no callback, None is passed. | 
| *args | *args | non-keyword parameters of func function | 
- Return value 

None 
- Example 

```python 
import time 
import apolloCommon.workerPool as workerPool 
def Callbacks(idx, result): 
print "callbacks",idx, result 
def Test(idx): 
print "test start %d" % idx 
time.sleep(1) 
print "test fin %d" % idx 
result = idx + 5 
return (idx, result)#The task must have a return value. If there is no return value, please return "()" 
ins = workerPool.ForkNewPool(4) 
for i in xrange(4): 
#Add asynchronous tasks. Tasks with odd i are executed sequentially, and tasks with even i are executed sequentially. These two batches of tasks are executed in parallel. 
ins.EmitOrder(i%2, Test, Callbacks, i) 
ins.Finish(None) #Wait for the thread pool to exit. 
``` 
<span id="Finish"></span> 
#### Finish


- Description 

Wait for the thread pool to exit. The thread pool will exit after executing all asynchronous tasks, which will block the main thread. It is recommended to execute when the Mod exits. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| timeout | int | Waiting thread pool exit time, in seconds. If None, it will wait forever. It is recommended to use None. | 
- Return value 

None 
- Example 

```python 
import apolloCommon.workerPool as workerPool 
ins = workerPool.ForkNewPool(4) 
ins.Finish(None) #Wait for the thread pool to exit. 
``` 
<span id="ForkNewPool"></span> 
#### ForkNewPool 

- Description 

Create a thread pool and set the thread pool size 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| orderSize | int | Thread pool size | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| MainPool | Thread pool instance | 
- Example 

```python 
import apolloCommon.workerPool as workerPool 
ins = workerPool.ForkNewPool(10) 
``` 
Below is the interface of mysql thread pool 

<span id="mysql connection pool"></span> 
### mysql connection pool 

<span id="AsyncExecuteFunctionWithOrderKey"></span>
#### AsyncExecuteFunctionWithOrderKey


- Description 

Add an asynchronous mysql task, func will be executed in the child thread. Note that func does not support the API provided by the execution engine. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| func | function | mysql asynchronous task, which can have no return value. The task and the main thread will be executed in parallel, and the task must be thread-safe. The first parameter is a mysql long connection, which can be obtained through conn.cursor(). | 
| orderKey | str/int | The same orderKey will be executed sequentially, and different orderKey will be executed in parallel. | 
| callback | function | The callback function has only one input parameter and is executed in the main thread. The return value of func will be the actual parameter of callback. If func throws an exception, the callback input parameter is None. If there is no callback, None is passed | 
| *args | *args | Other non-keyword arguments of func | 
| **kwargs | **kwargs | Not used yet, reserved for future use. |
- return value

    none
- Example

```python
def TestMysqlPoolCallback(records):
        if records is None:
                print "TestMysqlPoolCallback execute fail"
        else:
                print "TestMysqlPoolCallback execute success"
                for line in records:
                        print "single record=%s" % str(line)
def mysqlFunc(conn, num):
        cursor = conn.cursor()
        query = "SELECT * FROM neteaseUserMail LIMIT %s"
        params = (num, )
        try:
                cursor.execute(query, params)
                records = cursor.fetchall()
        except Exception as e:
                logout.error("mysqlFunc error=%s"%str(e))
                records = None
        finally:
                cursor.close()
        return records 
#An example of executing a transaction 
def mysqlTransactionTest(conn): 
conn.autocommit(False) 
cursor = conn.cursor() 
try: 
params = (2, 'test_items') 
query = "insert into neteaseCloudItems (uid, cloud_items) values (%s, %s)" 
cursor.execute(query, params) 
conn.commit() 
except:

conn.rollback() 
finally: 
cursor.close() 
conn.autocommit(True)#Please make sure to restore the connection 
import apolloCommon.mysqlPool as mysqlPool 
mysqlPool.InitDB(5) 
mysqlPool.AsyncExecuteFunctionWithOrderKey(mysqlFunc, "global", TestMysqlPoolCallback, 5) 
mysqlPool.AsyncExecuteFunctionWithOrderKey(mysqlTransactionTest, "test_trans", None) 
mysqlPool.Finish() 
``` 
<span id="AsyncExecuteWithOrderKey"></span> 
#### AsyncExecuteWithOrderKey 

- Description 

Add an asynchronous mysql task to execute all mysql operations 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| orderKey | str/int | The same orderKey will be executed sequentially, and different orderKey will be executed in parallel | 
| sql | str | mysql query statement, formatted string | 
| params | tuple | fill sql | 
| callback | function | callback function, with only one input parameter, it is executed in the main thread. The return value of func will be the actual parameter of callback. If func throws an exception, the callback input parameter is None. If there is no callback, None is passed | 
- Return value 

None 
- Example 

```python 
import apolloCommon.mysqlPool as mysqlPool 
mysqlPool.InitDB(30) 
def Cb(t): 
#Insert successfully, the value of t: True 
#Insert failed, the value of t: False 
print "cb", t 
#Add asynchronous task. 
mysqlPool.AsyncExecuteWithOrderKey('player', 'insert into player values (%s, %s)', (1, "test1"), Cb) 
mysqlPool.Finish() 
``` 
<span id="AsyncExecutemanyWithOrderKey"></span> 
#### AsyncExecutemanyWithOrderKey 

- Description 

Add an asynchronous mysql task, execute each parameter in paramsList once for the same sql statement, and return the number of successfully modified/created records. If any statement fails to execute, all statements will fail to execute and None will be returned. 

- Parameters 


| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| orderKey | string/int | The same orderKey will be executed sequentially, and different orderKey will be executed in parallel | 
| sql | string | mysql insert statement, formatted string | 
| callback | function | callback function, executed in the main thread, with only one parameter, the number of successfully modified/created records. If sql execution fails, the return parameter will be None. If there is no callback, None is passed | 
- Return value 

None 
- Example 

```python 
import time 
import apolloCommon.mysqlPool as mysqlPool 
mysqlPool.InitDB(30) 
def Cb(t): 
#Insert successfully, the value of t: 3 
#Insert failed, some data may be successfully inserted, and the value of t at this time: None 
print "cb", t 
#Add asynchronous task. 
mysqlPool.AsyncExecutemanyWithOrderKey('pay', 'insert into pay values (%s, %s)', [(1,"648"),(2,"328"), (3,"345")], Cb) 
for i in xrange(100): 
mysqlPool.Tick() 
time.sleep(0.2) 
mysqlPool.Finish() 
``` 
<span id="AsyncInsertOneWithOrderKey"></span> 
#### AsyncInsertOneWithOrderKey 

- Description 

Add an asynchronous mysql task to insert a record into a table with a primary key of AUTO INCREASEl type and return the primary key of the newly created record 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| orderKey | string/int | The same orderKey will be executed sequentially, and different orderKey will be executed in parallel | 
| sql | string | mysql insert statement, format string | 
| params | tuple | fill sql | 
| callback | function | callback function, executed in the main thread, with only one parameter, which is the primary key of the new record. If the sql execution fails, the return parameter will be None. If there is no callback, None is passed | 
- Return value 

None 
- Example 

```python 
# The creation statement of the table testTable is as follows 
# CREATE TABLE IF NOT EXISTS `testTable` ( 
# `id` bigint unsigned NOT NULL AUTO_INCREMENT, 
# `col_1` varchar(50) NOT NULL,

# PRIMARY KEY (`uid`) 
# ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4; 
import apolloCommon.mysqlPool as mysqlPool 
mysqlPool.InitDB(30) 
def Cb(t): 
#Insert successfully, an example value of t (that is, the corresponding value of column id in table testTable): 1 
#Insert failed, the value of t: None 
print "cb", t 
#Add asynchronous task. 
mysqlPool.AsyncInsertOneWithOrderKey('pay', 'insert into testTable (col_1) values (%s)', ("648"), Cb) 
mysqlPool.Finish() 
``` 
<span id="AsyncQueryWithOrderKey"></span> 
#### AsyncQueryWithOrderKey 

- Description 

Add an asynchronous mysql task to execute mysql query 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| orderKey | str/int | The same orderKey will be executed sequentially, and different orderKey will be executed in parallel | 
| sql | str | mysql query statement, formatted string | 
| params | tuple | Fill in sql | 
| callback | function | Callback function, only one input parameter, it is executed in the main thread. The return value of func will be the actual parameter of callback. If func throws an exception, the callback input parameter is None. If there is no callback, None is passed | 
- Return value 

None 
- Example 

```python 
import apolloCommon.mysqlPool as mysqlPool 
mysqlPool.InitDB(30) 
def Cb(t): 
#An example value of t when a record is found: ((1L, u'test_name_1', 0L),) 
#The value of t when the query is empty: () 
#The value of t when the query is error: None 
print "cb", t 
#Add asynchronous task. 
mysqlPool.AsyncQueryWithOrderKey('player', 'select uid,name from player where uid = %s', (1,), Cb) 
#Equivalent to 
#mysqlPool.AsyncQuery('player', 'select uid,name from player where uid = %s', (1,), Cb) 
#orderKey is 'player', and the two tasks are executed sequentially. 
mysqlPool.AsyncQueryWithOrderKey('player', 'select uid,name from player where uid = %s', (1,), Cb) 
mysqlPool.Finish() 
``` 
<span id="Finish"></span> 
#### Finish


- Description 

Wait for mysql thread pool to exit, it will wait for all asynchronous tasks in the thread pool to complete execution before exiting 

- Return value 

None 
- Example 

```python 
import apolloCommon.mysqlPool as mysqlPool 
mysqlPool.Finish() 
``` 
<span id="InitDB"></span> 
#### InitDB 

- Description 

Initialize the myqsl connection pool, requiring mysql to be configured in the "Server Configuration" of MCStudio 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| poolSize | int | Connection pool size | 
- Return value 

None 
- Example 

```python 
import apolloCommon.mysqlPool as mysqlPool 
mysqlPool.InitDB(30) 
``` 
<span id="SyncFetchAll"></span> 
#### SyncFetchAll 

- Description 

Blocking execution of sql statements to query data 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| sql | string | mysql query statement, formatted string | 
| params | tuple | Fill sql | 
- Return value 


| Data type | Description | 
| :--- | :--- | 
| None/list | Returns None if an error occurs, otherwise returns a list, each element in the list represents a query record | 
- Notes 

It is recommended to execute this API only when initializing the mod, and not during operation. It will block the main process and may cause the server to freeze. 


- Example 

```python 
import apolloCommon.mysqlPool as mysqlPool 
sql = 'select _id, name from test_user where _id > %s' 
#In case of successful query, an example value of allRecords: ((1L, u'test_name_1', 0L), (2L, u'test22', 2222L), (3L, u'test33', 333L)) 
#In case of failed query, the value of allRecords: None 
allRecords = mysqlPool.SyncFetchAll(sql, (0, )) 
for record in allRecords: 
user['_id'] = record[0]#Corresponding to the first field after select 
user['name'] = record[1]#Corresponding to the second field after select 
``` 
<span id="SyncInsert"></span> 
#### SyncInsert 

- Description 

Blocking execution of sql statements, inserting data 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| sql | string | mysql query statement, format string | 
| params | tuple | Fill sql | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| None/id | Return None if error occurs, otherwise return the successfully inserted id | 
- Notes 

It is recommended to execute this api only when initializing the mod, not during operation. It will block the main process and may cause server lag. 


- Example 

```python 
import apolloCommon.mysqlPool as mysqlPool 
sql = 'insert into test_user(name, age) values(%s, %s)' 
#If the insertion is successful, the return value is the inserted primary key id 
#If the insertion fails, the return value is 0

insertId = mysqlPool.SyncInsert(sql, ("steve", 20)) 
``` 
Below is the interface of the redis thread pool 

<span id="redis connection pool"></span> 
### redis connection pool 

<span id="AsyncDelete"></span> 
#### AsyncDelete 

- Description 

Execute redis operation and delete a redis key, which is equivalent to executing the command: del key in redis 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| key | string | key in redis | 
| callback | function | callback function, the input parameter is the return value of the redis operation, which is an int, indicating the number of deleted redis keys, and it is executed in the main thread. The callback function can be omitted. If the redis operation throws an exception, the callback input parameter is None. If there is no callback, None is passed | 
- Return value 

None 
- Example 

```python 
import apolloCommon.redisPool as redisPool 
def Cb1(t): 
#If the execution is successful and the redis key "player_121" exists, the value of t is: 1 
#If the execution is successful and the redis key "player_121" does not exist, the value of t is: 0 
#If the execution fails, the value of t is: None 
print "cb", t 
redisPool.InitDB(30) #Establish connection pool 
redisPool.AsyncDelete('player_121', cb1) 
redisPool.Finish() 
``` 
<span id="AsyncFuncWithKey"></span> 
#### AsyncFuncWithKey 

- Description 

Add an asynchronous redis task 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| func | function | redis asynchronous task, may have no return value. The task and the main thread will be executed in parallel, and the task must be thread-safe. The first parameter is a redis long connection, which is a redis.StrictRedis instance, and the other parameters are *args | 
| orderKey | str/int | The same orderKey will be executed sequentially, and different orderKeys will be executed in parallel | 
| callback | function | The callback function has only one input parameter and is executed in the main thread. The return value of func is the input parameter of callback. If func throws an exception, the callback input parameter is None. If there is no callback, None is passed in |

| *args | *args | Other non-keyword parameters of func | 
| **kwargs | **kwargs | Not used yet, reserved. | 
- Return value 

None 
- Example 

```python 
import apolloCommon.redisPool as redisPool 
redisPool.InitDB(30) #Establish connection pool 
#Callback, you can get the player information. Here just print the result. 
def Cb1(t): 
#If the execution is successful and the redis key "player_123" exists, an example value of t: 'test_string_value' 
#If the execution is successful and the redis key "player_123" does not exist, the value of t: "" 
#When the execution fails, the value of key: None 
print "cb", t 
#The first parameter is the redis.StrictRedis instance. 
def GetValueFromKey(conn, key): 
ret = conn.get(key) 
return ret if ret is not None else "" 
#Insert a task to get the information of the player with uid 123 from redis. 
redisPool.AsyncFuncWithKey(GetValueFromKey, "player_123", Cb1, 123) 
#Insert the same task, the orderKey is "player_123", so the two tasks will be executed sequentially. 
redisPool.AsyncFuncWithKey(GetValueFromKey, "player_123", Cb1, 123) 
redisPool.Finish() 
``` 
<span id="AsyncGet"></span> 
#### AsyncGet 

- Description 

Execute redis operation to get the value of key, which is equivalent to executing command: get key in redis 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| key | str | key in redis | 
| callback | function | callback function, empty by default. The function input parameter is the value string corresponding to the redis key, which is executed in the main thread. If the redis operation throws an exception, the callback input parameter is None. If there is no callback, pass None | 
- Return value 

None 
- Example 

```python 
import apolloCommon.redisPool as redisPool 
def Cb1(t): 
#If the execution is successful and the redis key "player_123" exists, an example value of t: 'test_string_value' 
#If the execution is successful and the redis key "player_123" does not exist, the value of t: None 
#When the execution fails, the value of key: None

print "cb", t 
redisPool.InitDB(30) #Establish connection pool 
redisPool.AsyncGet("player_123", Cb1) 
redisPool.Finish() 
``` 
<span id="AsyncHgetall"></span> 
#### AsyncHgetall 

- Description 

Execute redis operation to get the value of key, which is equivalent to executing command: hgetall key in redis 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| key | string | key in redis | 
| callback | function | Callback function, the input parameter is the value corresponding to redis key, which is a dict, and it is executed in the main thread. The callback function can be omitted. If the redis operation throws an exception, the callback input parameter is None. If there is no callback, None is passed | 
- Return value 

None 
- Example 

```python 
import apolloCommon.redisPool as redisPool 
def Cb1(t): 
#When the execution is successful and the redis key "player_123" is not empty, an example value of t: {'name': 'name', 'lv': '2'} 
#When the execution is successful and the redis key "player_123" is empty, the value of t: {} 
#When the execution fails, the value of t: None 
print "cb", t 
redisPool.InitDB(30) #Establish connection pool 
redisPool.AsyncHgetall("h_player_123", Cb1) 
redisPool.Finish() 
``` 
<span id="AsyncMget"></span> 
#### AsyncMget 

- Description 

Execute redis operation to get the values of multiple keys, which is equivalent to executing the command in redis: mget key1 key2 ... 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| key | list/tuple | Multiple keys in redis | 
| callback | function | Callback function, empty by default. The function input parameter redis operation return value is a list, each element corresponds to the value of a single redis key, and it is executed in the main thread. If the redis operation throws an exception, the callback input parameter is None. If there is no callback, None is passed | 
- Return value 

None

- Example 

```python 
import apolloCommon.redisPool as redisPool 
def Cb1(t): 
#When the execution is successful and the redis key "test_value_None" does not exist, an example value of t: {'1': 'str', None} 
#When the execution fails, the value of t: None 
print "cb", t 
redisPool.InitDB(30) #Establish a connection pool 
keys = ("test_value_1", "test_value_str", "test_value_None") 
redisPool.AsyncMget(keys, Cb1) 
redisPool.Finish() 
``` 
<span id="AsyncSet"></span> 
#### AsyncSet 

- Description 

Execute redis operation and set the value of key to value, which is equivalent to executing the command in redis: set key value 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| key | string | key in redis | 
| value | string | value of key in redis | 
| callback | function | callback function, empty by default. The function input parameter is the return value of the redis operation, True means the setting is successful, False means failure. If the redis operation throws an exception, the callback input parameter is None. If there is no callback, pass None | 
- Return value 

None 
- Example 

```python 
import apolloCommon.redisPool as redisPool 
redisPool.InitDB(30) #Establish connection pool 
def cb1(t): 
#When the execution succeeds, the value of t is: True 
#When the execution fails, the value of t is: False 
print "cb", t 
redisPool.AsyncSet('player_123', "{'name':'nickname'}", cb1) 
redisPool.Finish() 
``` 
<span id="Finish"></span> 
#### Finish 

- Description 

Wait for the redis thread pool to exit, and it will wait for all asynchronous tasks in the thread pool to complete execution before exiting 

- Return value


None 
- Example 

```python 
import apolloCommon.redisPool as redisPool 
redisPool.InitDB(30) #Create a connection pool 
#Add asynchronous tasks. Execute in redis: set "key1", "value11" 
redisPool.AsyncSet("key1", "value11") 
redisPool.Finish() 
``` 
<span id="InitDB"></span> 
#### InitDB 

- Description 

Initialize the redis connection pool, requiring redis to be configured in the "Server Configuration" of MCStudio 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| poolSize | int | Connection pool size | 
- Return value 

None 
- Example 

```python 
import apolloCommon.redisPool as redisPool 
redisPool.InitDB(30) 
``` 
The following is the interface of the mongo thread pool 

<span id="mongo connection pool"></span> 
### mongo connection pool 

<span id="AsyncExecute"></span> 
#### AsyncExecute 

- Description 

Add an asynchronous mongo task 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| collection | str | A collection in mongo. All operations on the same collection are executed serially, and operations on different collections are executed in parallel. | 
| func | function | A mongo asynchronous task that may not have a return value. The task will be executed in parallel with the main thread, requiring the task to be thread-safe. The first parameter is a mongo long connection, which is a connection in the pymongo.MongoClient connection pool instance |

| callback | function | The callback function has only one input parameter and is executed in the main thread. The return value of func will be the actual parameter of callback. If func throws an exception, the callback input parameter is None. If there is no callback, None is passed | 
| *args | *args | Other non-keyword parameters of func | 
| **kwargs | **kwargs | Not used yet, reserved | 
- Return value 

None 
- Notes 

In the dictionary returned by query mongo database, integers larger than signed int are not returned as int, but as bson.int64.Int64 (although the direct print result is similar to [50000L]). Data of type bson.int64.Int64 cannot be sent to the client or function service as eventData, and needs to be converted to Int type using API: ConvertBsonToInt 


- Example 

```python 
import apolloCommon.mongoPool as mongoPool 
mongoPool.InitDB(32) 
def Insert(col): 
postData = { 
'title': 'Python and MongoDB', 
'content': 'PyMongo is fun, you guys', 
'author': 'Scott' 
} 
col.insert_one(postData) 
def Cb(t): 
print "cb", t 
#Add an asynchronous task. 
mongoPool.AsyncExecute("test_col", Insert, Cb) 
mongoPool.Finish() 
``` 
<span id="AsyncExecuteWithOrderKey"></span> 
#### AsyncExecuteWithOrderKey 

- Description 

Add an asynchronous mongo task. The difference with async_execute is that orderKey can be set explicitly 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| collection | str | A collection in mongo | 
| func | function | A mongo asynchronous task, which can have no return value. The task and the main thread will be executed in parallel, and the task must be thread-safe. The first parameter is a mongo long connection, which is a connection in the pymongo.MongoClient connection pool instance | 
| orderKey | str/int | The same orderKey will be executed sequentially, and different orderKey will be executed in parallel | 
| callback | function | The callback function has only one input parameter and is executed in the main thread. The return value of func will be the actual parameter of callback. If func throws an exception, the callback input parameter is None. If there is no callback, None is passed | 
| *args | *args | Other non-keyword parameters of func | 
| **kwargs | **kwargs | Not used yet, reserved for future use. | 
- Return value 

None 
- Remarks


    In the dictionary returned by querying the mongo database, integers larger than signed int are not returned as int, but as bson.int64.Int64 (although the direct print result is similar to [50000L]). Data of type bson.int64.Int64 cannot be sent to the client or function service as eventData. You need to use the API: ConvertBsonToInt to convert it to Int type. 


- Example 

```python 
import apolloCommon.mongoPool as mongoPool 
mongoPool.InitDB(32) 
def Insert(col): 
postData = { 
'title': 'Python and MongoDB', 
'content': 'PyMongo is fun, you guys', 
'author': 'Scott' 
} 
col.insert_one(postData) 
def Cb(t): 
print "cb", t 
#Add asynchronous task.
#The following operation is equivalent to: mongoPool.AsyncExecute("test_col", Insert, Cb) 
mongoPool.AsyncExecuteWithOrderKey("test_col", Insert, "test_col", Cb) 
#Add the same task, and the two tasks will be executed sequentially. 
mongoPool.AsyncExecuteWithOrderKey("test_col", Insert, "test_col", Cb) 
mongoPool.Finish() 
``` 
<span id="Finish"></span> 
#### Finish 

- Description 

Wait for the mongo thread pool to exit. It will exit after all asynchronous tasks in the thread pool are executed. 

- Return value 

None 
- Example 

```python 
import apolloCommon.mongoPool as mongoPool 
mongoPool.InitDB(32) 
mongoPool.Finish() 
``` 
<span id="InitDB"></span> 
#### InitDB 

- Description 

Initialize the mongo connection pool. It is required to configure mongo in the "Server Configuration" of MCStudio 

- Parameters


| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| poolSize | int | Connection pool size | 
- Return value 

None 
- Example 

```python 
import apolloCommon.mongoPool as mongoPool 
mongoPool.InitDB(32) 
``` 
Below are some interfaces of mysql extended thread pool 

<span id="mysql connection pool extension"></span> 
### mysql connection pool extension 

<span id="AsyncExecuteWithOrderKey"></span> 
#### AsyncExecuteWithOrderKey 

- Description 

Add an asynchronous mysql task to execute all mysql operations. The difference with AsyncExecute is that the orderKey can be specified explicitly 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | string | mysql db name, the name is configured under extra_mysql in deploy.json, see [InitDB](#InitDB) for details | 
| orderKey | string/int | The same orderKey will be executed sequentially, and different orderKey will be executed in parallel | 
| sql | string | mysql query statement, formatted string | 
| params | tuple | Fill in sql | 
| callback | function | callback function, with only one input parameter, it is executed in the main thread. The return value of func will be the actual parameter of callback. If func throws an exception, the callback input parameter is None. If there is no callback, pass None | 
- Return value 

None 
- Example 

```python 
import apolloCommon.extraMysqlPool as extraMysqlPool 
extraMysqlPool.InitDB('mysql_test1', 30) 
def Cb(t): 
print "cb", t 
#Add asynchronous task 
extraMysqlPool.AsyncExecuteWithOrderKey('mysql_test1', 'player', 'insert into player values (%s, %s)', (1, "test1"), Cb) 
extraMysqlPool.Finish() 
``` 
<span id="AsyncQueryWithOrderKey"></span> 
#### AsyncQueryWithOrderKey


- Description 

Add an asynchronous mysql task to execute mysql query. The difference with AsyncQuery is that orderKey can be explicitly specified 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | string | mysql db name, the name is configured under extra_mysql in deploy.json, see [InitDB](#InitDB) for details | 
| orderKey | string/int | The same orderKey will be executed sequentially, and different orderKey will be executed in parallel | 
| sql | string | mysql query statement, formatted string | 
| params | tuple | Fill sql | 
| callback | function | callback function, with only one input parameter, it is executed in the main thread. The return value of func will be the actual parameter of callback. If func throws an exception, the callback input parameter is None. If there is no callback, pass None | 
- Return value 

None 
- Example 

```python 
import apolloCommon.extraMysqlPool as extraMysqlPool 
extraMysqlPool.InitDB('mysql_test1', 30) 
def Cb(t): 
print "cb", t 
#Add asynchronous task 
extraMysqlPool.AsyncQueryWithOrderKey('mysql_test1', 'player', 'select uid,name from player where uid = %s', (1,), Cb) 
#orderKey is 'player', two tasks are executed in sequence 
extraMysqlPool.AsyncQueryWithOrderKey('mysql_test1','player', 'select uid,name from player where uid = %s', (1,), Cb) 
extraMysqlPool.Finish() 
``` 
<span id="Finish"></span> 
#### Finish 

- Description 

Wait for the mysql thread pool to exit. It will exit after all asynchronous tasks in the thread pool are executed. 

- Return value 

None 
- Example 

```python 
import apolloCommon.extraMysqlPool as extraMysqlPool 
extraMysqlPool.Finish() 
``` 
<span id="InitDB"></span> 
#### InitDB 

- Description


Initialize mysql connection pool. Can support multiple mysql instances, it can be used together with "mysql connection pool". Open the configuration file directory in MCStudio and configure extra_mysql in the deploy.json file. For the configuration method, see the notes. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | string | mysql db name. The name is configured under extra_mysql in deploy.json, such as "mysql_test1" in the sample configuration | 
| poolSize | int | Connection pool size | 
- Return value 

None 
- Notes 

Some configuration examples in deploy.json are as follows: 
``` 
"mysql": { 
"database": "mod_test", 
"host": "127.0.0.1", 
"password": "test", 
"port": 3306, 
"user": "test" 
}, 
"extra_mysql":{ 
"test1":{ 
"database": "mysql_test1", 
"host": "127.0.0.2", 
"password": "test", 
"port": 3306, 
"user": "test" 
}, 
"test2":{ 
"database": "mysql_test2", 
"host": "127.0.0.3", 
"password": "test", 
"port": 3306, 
"user": "test" 
} 
}, 
``` 


- Example 

```python 
import apolloCommon.extraMysqlPool as extraMysqlPool 
extraMysqlPool.InitDB('mysql_test1', 30) 
``` 
Below are some interfaces of redis extended thread pool 


<span id="redis connection pool extension"></span> 
### redis connection pool extension 

<span id="AsyncDelete"></span> 
#### AsyncDelete 

- Description 

Execute redis operation and delete a redis key, which is equivalent to executing the command: del key in redis 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | str | redis db name, the name corresponds to the instance name of the newly added redis instance in MCStudio | 
| key | str | key in redis | 
| callback | function | callback function, the default is empty. The function input parameter is the return value of the redis operation, which is an int, indicating the number of deleted redis keys, and it is executed in the main thread. If the redis operation throws an exception, the callback input parameter is None. If there is no callback, pass None | 
- Return value 

None 
- Example 

```python 
import apolloCommon.extraRedisPool as extraRedisPool 
def Cb1(t): 
print "cb", t 
extraRedisPool.InitDB('extra_redis1', 30) #Establish connection pool 
extraRedisPool.AsyncDelete('extra_redis1', 'player_121', Cb1) 
extraRedisPool.Finish() 
``` 
<span id="AsyncFuncWithKey"></span> 
#### AsyncFuncWithKey 

- Description 

Add an asynchronous redis task 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | str | redis db name, the name corresponds to the instance name of the newly added redis instance in MCStudio | 
| func | function | redis asynchronous task, which may have no return value. The task and the main thread will be executed in parallel, and the task must be thread-safe. The first parameter is a redis long connection, which is a redis.StrictRedis instance, and the other parameters are *args | 
| orderKey | str/int | The same orderKey will be executed sequentially, and different orderKeys will be executed in parallel | 
| callback | function | The callback function has only one input parameter and is executed in the main thread. The return value of func is the input parameter of callback. If func throws an exception, the callback input parameter is None. If there is no callback, None is passed in | 
| *args | *args | Other non-keyword parameters of func | 
| **kwargs | **kwargs | Not used yet, reserved | 
- Return value 

None

- Example 

```python 
import apolloCommon.extraRedisPool as extraRedisPool 
extraRedisPool.InitDB('extra_redis1', 30) #Establish connection pool 
#Callback to get player information. Here we just print the result. 
def Cb1(t): 
print "cb", t 
#The first parameter is the redis.StrictRedis instance. 
def GetValueFromKey(conn, key): 
return conn.get(key) 
#Insert a task to get the information of the player with uid 123 from redis. 
extraRedisPool.AsyncFuncWithKey('extra_redis1', GetValueFromKey, 'player_123', Cb1, 123) 
#Insert the same task, the orderKey is "player_123", so the two tasks will be executed sequentially. 
extraRedisPool.AsyncFuncWithKey('extra_redis1', GetValueFromKey, 'player_123', Cb1, 123) 
extraRedisPool.Finish() 
``` 
<span id="AsyncGet"></span> 
#### AsyncGet 

- Description 

Execute redis operation to get the value of key, which is equivalent to executing command: get key in redis 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | str | redis db name, the name corresponds to the instance name of the newly added redis instance in MCStudio | 
| key | str | key in redis | 
| callback | function | callback function, the default is empty. The function input parameter is the value string corresponding to the redis key, which is executed in the main thread. If the redis operation throws an exception, the callback input parameter is None. If there is no callback, None is passed | 
- Return value 

None 
- Example 

```python 
import apolloCommon.extraRedisPool as extraRedisPool 
def Cb1(t): 
print "cb", t 
extraRedisPool.InitDB('extra_redis1', 30) #Establish connection pool 
extraRedisPool.AsyncGet('extra_redis1','player_123', Cb1) 
extraRedisPool.Finish() 
``` 
<span id="AsyncHgetall"></span> 
#### AsyncHgetall 

- Description 

Execute redis operation and get the value of key, which is equivalent to executing command: hgetall key in redis


- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | str | redis db name, the name corresponds to the instance name of the newly added redis instance in MCStudio | 
| key | str | key in redis | 
| callback | function | callback function, empty by default, the function input parameter is the value corresponding to the redis key, which is a dict, and it is executed in the main thread. If the redis operation throws an exception, the callback input parameter is None. If there is no callback, None is passed | 
- Return value 

None 
- Example 

```python 
import apolloCommon.extraRedisPool as extraRedisPool 
def Cb1(t): 
print "cb", t 
extraRedisPool.InitDB('extra_redis1', 30) #Establish connection pool 
extraRedisPool.AsyncHgetall('extra_redis1', 'player_123', Cb1) 
extraRedisPool.Finish() 
``` 
<span id="AsyncMget"></span> 
#### AsyncMget 

- Description 

Execute redis operation to get the values of multiple keys, which is equivalent to executing the command in redis: mget key1 key2 ... 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | str | redis db name, the name corresponds to the instance name of the newly added redis instance in MCStudio | 
| keys | list/tuple | multiple redis keys | 
| callback | function | callback function, empty by default, the function input parameter redis operation return value, is a list, each element corresponds to the value of a single redis key, it is executed in the main thread. If the redis operation throws an exception, the callback input parameter is None | 
- Return value 

None 
- Example 

```python 
import apolloCommon.extraRedisPool as extraRedisPool 
def Cb1(t): 
print "cb", t 
extraRedisPool.InitDB('extra_redis1', 30) #Establish connection pool 
keys = ('player_121', 'player_122') 
extraRedisPool.AsyncMget('extra_redis1', keys, Cb1) 
extraRedisPool.Finish() 
``` 
<span id="AsyncSet"></span>

#### AsyncSet 

- Description 

Execute redis operation, set the value of key to value, equivalent to executing the command in redis: set key value 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | str | redis db name, the name corresponds to the instance name of the newly added redis instance in MCStudio | 
| key | str | key in redis | 
| value | str | value of key in redis | 
| callback | function | callback function, empty by default. The function input parameter is the return value of the redis operation, True means the setting is successful, False means failure. If the redis operation throws an exception, the callback input parameter is None. If there is no callback, pass None | 
- Return value 

None 
- Example 

```python 
import apolloCommon.extraRedisPool as extraRedisPool 
extraRedisPool.InitDB('extra_redis1', 30) #Establish connection pool 
extraRedisPool.AsyncSet('extra_redis1', 'player_123', "{'name':'nickname'}") 
extraRedisPool.Finish() 
``` 
<span id="Finish"></span> 
#### Finish 

- Description 

Wait for the redis db thread pool to exit. It will wait for all asynchronous tasks in the thread pool to complete execution before exiting 

- Return value 

None 
- Example 

```python 
import apolloCommon.extraRedisPool as extraRedisPool 
extraRedisPool.InitDB('extra_redis1', 30) #Establish connection pool 
#Callback to get player information. Here we just print the result. 
def Cb1(t): 
print "cb", t 
#The first parameter is the redis.StrictRedis instance. 
def GetValueFromKey(conn, key): 
return conn.get(key) 
#Insert a task to get the information of the player with uid 123 from redis. 
extraRedisPool.AsyncFuncWithKey('extra_redis1', GetValueFromKey, 'player_123', Cb1, 123) 
extraRedisPool.Finish() 
```

<span id="InitDB"></span> 
#### InitDB 

- Description 

Initialize the redis connection pool, requiring "adding a new redis instance" in the "Server Configuration" of MCStudio 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | str | redis instance name, corresponding to the redis "Instance Name" configuration in MCStudio | 
| poolSize | int | Connection pool size | 
- Return value 

None 
- Example 

```python 
import apolloCommon.extraRedisPool as extraRedisPool 
extraRedisPool.InitDB('extra_redis1', 30) 
``` 
Below are some interfaces of mongo extended thread pool 

<span id="mongo connection pool extension"></span> 
### mongo connection pool extension 

<span id="AsyncExecute"></span> 
#### AsyncExecute 

- Description 

Add an asynchronous mongo task 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | str | mongo db name, the name is configured under extra_mongo in deploy.json, see [InitDB](#InitDB) for details | 
| collection | str | A collection in mongo, all operations on the same collection are executed serially, and operations on different collections are executed in parallel | 
| func | function | mongo asynchronous task, which can have no return value. The task and the main thread will be executed in parallel, and the task must be thread-safe. The first parameter is a mongo long connection, which is a connection in the pymongo.MongoClient connection pool instance | 
| callback | function | callback function, with only one input parameter, is executed in the main thread. The return value of func will be the actual parameter of callback. If func throws an exception, the callback input parameter is None. If there is no callback, None is passed in | 
| *args | *args | non-keyword parameters of func | 
| **kwargs | **kwargs | Not used yet, reserved | 
- Return value 

None 
- Example 

```python

import apolloCommon.extraMongoPool as extraMongoPool
extraMongoPool.InitDB('mongo_test1', 32)
def Insert(col):
        postData = {
                'title': 'Python and MongoDB',
                'content': 'PyMongo is fun, you guys',
                'author': 'Scott'
        }
        col.insert_one(postData)
def Cb(t):
        print "cb", t
#Add asynchronous tasks.
extraMongoPool.AsyncExecute('mongo_test1', 'test_col', Insert, Cb) 
extraMongoPool.Finish() 
``` 
<span id="AsyncExecuteWithOrderKey"></span> 
#### AsyncExecuteWithOrderKey 

- Description 

Add an asynchronous mongo task. The difference with async_execute is that orderKey can be set explicitly 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | str | mongo db name, the name is configured under extra_mongo in deploy.json, see [InitDB](#InitDB) for details | 
| collection | str | A collection in mongo | 
| func | function | mongo asynchronous task, may not have a return value. This task will be executed in parallel with the main thread, and the task must be thread-safe. The first parameter is a mongo long connection, which is a connection in the pymongo.MongoClient connection pool instance. The other parameters are *args | 
| orderKey | str/int | The same orderKey will be executed sequentially, and different orderKeys will be executed in parallel | 
| callback | function | The callback function has only one input parameter and is executed in the main thread. The return value of func will be the actual parameter of callback. If func throws an exception, the callback input parameter is None. If there is no callback, None is passed | 
| *args | *args | Non-keyword parameters of func | 
| **kwargs | **kwargs | Not used yet, reserved | 
- Return value 

None 
- Example 

```python 
import apolloCommon.extraMongoPool as extraMongoPool 
extraMongoPool.InitDB('mongo_test1', 32) 
def Insert(col): 
postData = { 
'title': 'Python and MongoDB', 
'content': 'PyMongo is fun, you guys', 
'author': 'Scott' 
} 
col.insert_one(postData) 
def Cb(t): 
print "cb", t

#Add asynchronous task 
#The following operation is equivalent to: apolloCommon.AsyncExecute('mongo_test1', 'test_col', Insert, Cb) 
apolloCommon.AsyncExecuteWithOrderKey('mongo_test1', 'test_col', Insert, 'test_col', Cb) 
#Add the same task, two tasks are executed in sequence 
apolloCommon.AsyncExecuteWithOrderKey('mongo_test1', 'test_col', Insert, 'test_col', Cb) 
apolloCommon.Finish() 
``` 
<span id="Finish"></span> 
#### Finish 

- Description 

Wait for the mongo thread pool to exit, and will wait for all asynchronous tasks in the thread pool to complete execution before exiting 

- Return value 

None 
- Example 

```python 
import apolloCommon.extraMongoPool as extraMongoPool 
extraMongoPool.Finish() 
``` 
<span id="InitDB"></span> 
#### InitDB 

- Description 

Initialize mongo connection pool. It can support multiple mongo instances and can be used together with "mongo connection pool". Open the configuration file directory in MCStudio and configure extra_mongo in the deploy.json file. For the configuration method, see the notes. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| dbName | str | mongo db name. The name is configured under extra_mongo in deploy.json, such as "mongo_test1" in the example configuration | 
| poolSize | int | Connection pool size | 
- Return value 

None 
- Notes 

The example of some configurations of deploy.json is as follows: 
``` 
"mongo": { 
"database": "test", 
"host": "127.0.0.1", 
"password": "test", 
"port": 27017, 
"user": "test" 
},

"extra_mongo":{ 
"testname1" : { 
"database": "mongo_test1", 
"host": "127.0.0.2", 
"password": "test", 
"port": 27017, 
"user": "test" 
}, 
"testname2" : { 
"database": "mongo_test2", 
"host": "127.0.0.3", 
"password": "test", 
"port": 27017, 
"user": "test" 
} 
}, 
``` 


- Example 

```python 
import apolloCommon.extraMongoPool as extraMongoPool 
extraMongoPool.InitDB('mongo_test1', 30) 
``` 
Below is the public interface 

<span id="General"></span> 
### General 

<span id="ChangeDatabaseSlowLogLimit"></span> 
#### ChangeDatabaseSlowLogLimit 

- Description 

Modify the time limit for the slow request alarm log of the database connection pool 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| db | str | Database connection pool type, mysql/redis/mongo | 
| interval | float | Slow request limit time, a single request return time exceeding this value will record a slow request log, in seconds, the default configuration value for mysql and mongo is 1.0 seconds, and the default configuration for redis is 0.1 seconds | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Execution result | 
- Example 


```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
suc = commonNetgameApi.ChangeDatabaseSlowLogLimit("mysql", 0.1) 
print "ChangeDatabaseSlowLogLimit for mysql suc=%s" % suc 
``` 
<span id="CheckNameValid"></span> 
#### CheckNameValid 

- Description 

Determines whether an input string has passed the name library sensitive word check. If there is no sensitive word, it returns 1, and if there is a sensitive word, it returns 0 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| name | str | String to be checked for sensitive words | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | 1 means no sensitive words, 0 means there are sensitive words | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
isOk = commonNetgameApi.CheckNameValid("xxxxxx") 
if not isOk: 
print "Sensitive words exist in the input" 
return 
``` 
<span id="CheckWordsValid"></span> 
#### CheckWordsValid 

- Description 

Determine whether an input string passes the common library sensitive word check. If there are no sensitive words, 1 is returned, and if there are sensitive words, 0 is returned. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| words | str | String to be checked for sensitive words | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | 1 means there are no sensitive words, 0 means there are sensitive words | 
- Example 


```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
isOk = commonNetgameApi.CheckSensitiveByName("xxxxxx") 
if not isOk: 
print "Sensitive words exist in the input" 
return 
``` 
<span id="CloseAsyncTaskSlowCheck"></span> 
#### CloseAsyncTaskSlowCheck 

- Description 

Stop checking the tasks in the asynchronous thread pool every frame 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Execution result | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.CloseAsyncTaskSlowCheck() 
``` 
<span id="ConvertBsonToInt"></span> 
#### ConvertBsonToInt 

- Description 

Recursively convert all bson.int64.Int64 type objects in the input data to int type 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| input | dict/list/tuple/str/unicode | Input data to be converted | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| dict/list/tuple/str/unicode | Same format as input data, where bson.int64.Int64 type objects will be converted to int type | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
import bson 
bsonInt = bson.Int64(5000000000)
input = {
        "a1": bsonInt,

"a2": [bsonInt, bsonInt], 
"a3": (bsonInt, bsonInt), 
} 
ret = commonNetgameApi.ConvertBsonToInt(input) 
``` 
<span id="DumpAsyncTaskPool"></span> 
#### DumpAsyncTaskPool 

- Description 

Print the queued and executed task information in the current asynchronous thread pool 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Execution result | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.DumpAsyncTaskPool() 
``` 
<span id="GetApolloGameId"></span> 
#### GetApolloGameId 

- Description 

Get the gameId of the current game project (needed when querying orders in the mall) 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | gameId of the current game project | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
gameId = commonNetgameApi.GetApolloGameId() 
``` 
<span id="GetApolloGameKey"></span> 
#### GetApolloGameKey 

- Description 

Get the gameKey of the current game project (needed when querying orders in the mall) 

- Return value 


| Data type | Description | 
| :--- | :--- | 
| int | gameKey of the current game project | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
gameKey = commonNetgameApi.GetApolloGameKey() 
``` 
<span id="GetApolloReviewStage"></span> 
#### GetApolloReviewStage 

- Description 

Get the current review stage of the game 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | 0 Testing stage, 1 Review stage 2 Online stage | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
reviewStage = commonNetgameApi.GetApolloReviewStage() 
``` 
<span id="GetApolloUniqueId"></span> 
#### GetApolloUniqueId 

- Description 

Get the unique ID of the current game project 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| int | The unique ID of the current game project | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
apolloId = commonNetgameApi.GetApolloUniqueId() 
``` 
<span id="GetModJsonConfig"></span> 
#### GetModJsonConfig 

- Description 


Read mod.json configuration file according to the script root directory. Requires mod to have been loaded 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| scriptRootName | str | Python script root directory name | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| dict | Content information in mod.json | 
- Example 

```python 
#Directory structure 
# |-developer_mods 
# |- neteaseNpcLobbyDev 
# mod.json 
# |- neteaseNpcLobby 
import apolloCommon.commonNetgameApi as commonNetgameApi 
confDict = commonNetgameApi.GetModJsonConfig("neteaseNpcLobby") 
print confDict["description"]#Print the description configuration content in mod.json 
#The strings extracted from mod.json are all unicode. If they are Chinese, they need to be manually converted to UTF-8. The transcoding method is as follows: 
npcName = confDict["name"].encode('utf-8') 
``` 
<span id="GetModJsonConfigByName"></span> 
#### GetModJsonConfigByName 

- Description 

Read the json format configuration file under the [pathFile] path based on the script root directory 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| scriptRootName | str | Python script root directory name | 
| pathFile | str | File name relative to the Python script root directory (including relative path) | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| dict | Content information in the json file under the corresponding directory | 
- Example 

```python 
#Directory structure 
# |-developer_mods 
# |- neteaseNpcLobbyDev

# mod.json 
# |- neteaseNpcLobby 
# |- modData 
# skill1.json 
import apolloCommon.commonNetgameApi as commonNetgameApi 
confDict = commonNetgameApi.GetModJsonConfig("neteaseNpcLobby", "modData/skill1.json") 
print confDict # Print the contents of the skill1.json file 
#The strings extracted from json are all unicode encoded. If they are in Chinese, they need to be manually converted to UTF-8 encoding. The conversion method is as follows: 
npcName = confDict["name"].encode('utf-8') 
``` 
<span id="GetModScriptRootDir"></span> 
#### GetModScriptRootDir 

- Description 

Get the absolute path of the script root directory. Requires mod to be loaded 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| scriptRootName | str | Python script root directory name | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| str | Absolute path to script root directory | 
- Example 

```python 
#Directory structure 
# |-developer_mods 
# |- neteaseNpcLobbyDev 
# mod.json 
# |- neteaseNpcLobby 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.GetModScriptRootDir("neteaseNpcLobby") 
#Result:/home/fuzhu/netgame/app/template/lobby/lobby_lobby_2000000/developer_mods/neteaseNpcLobbyDev/ 
``` 
<span id="GetServerType"></span> 
#### GetServerType 

- Description 

Get the server type of this server, corresponding to the configuration in MCStudio: Server Configuration->Game Configuration->Type 

- Return Value 

| Data Type | Description | 
| :--- | :--- |

| str | Server type | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.GetServerType() #The result is: "gameBattleA" 
``` 
<span id="OpenAsyncTaskSlowCheck"></span> 
#### OpenAsyncTaskSlowCheck 

- Description 

Start checking the tasks in the asynchronous thread pool every frame, and print the tasks that have been executed for more than the specified time and have not been completed. This function consumes a lot of resources and is only recommended to be enabled during the testing phase and when encountering online emergency problems 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| interval | float | Task limit time. If a single task enters the asynchronous thread pool queue + the execution time exceeds this time and has not been completed, it will be output in the form of a warning log | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Execution result | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.OpenAsyncTaskSlowCheck(0.01) 
``` 
<span id="StartDatabaseProfile"></span> 
#### StartDatabaseProfile 

- Description 

Start recording database connection pool request information statistics. After starting, call [StopDatabaseMysqlProfile(db)](#StopDatabaseMysqlProfile) to obtain database connection pool request record information between two function calls 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| db | str | Database connection pool type, mysql/redis/mongo | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Execution result | 
- Example 

```python

import apolloCommon.commonNetgameApi as commonNetgameApi
commonNetgameApi.StartDatabaseProfile("mysql")
# Then call StopDatabaseMysqlProfile through a timer or other triggering method
result = commonNetgameApi.StopDatabaseMysqlProfile("mysql")
for single in result:
        action = single["action"]
        if action == "executefunc":
                print "do {} func={} orderKey={} cost={}s ret={}".format(action, single["func"], single["orderKey"], single["costTp"], single["ret"])
        else:
                print "do {} orderKey={} cost={}s ret={}".format(action, single["orderKey"], single["costTp"], single["ret"])
 ```
<span id="StartYappiProfile"></span> 
#### StartYappiProfile 

- Description 

Start the server-side script performance analysis. After starting, call [StopYappiProfile(path)](#StopYappiProfile) to generate the function performance flame graph in the path path 

- Return value 

| Data type | Description | 
| :--- | :--- | 
| bool | Execution result | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.StartYappiProfile() 
modfunc()# Process the corresponding logic 
# Then call StopYappiProfile through a timer or other triggering method 
commonNetgameApi.StopYappiProfile() 
``` 
<span id="StopDatabaseMysqlProfile"></span> 
#### StopDatabaseMysqlProfile 

- Description 

Stop recording database connection pool request information and output statistical results. Used in conjunction with [StartDatabaseProfile(db)](#StartDatabaseProfile). The output result is a dictionary. See the example for details. 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| db | str | Database connection pool type, mysql/redis/mongo | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| list | Database connection pool request statistics. See the example for details. If StartDatabaseProfile has not been called, it will return None | 
- Example


```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.StartDatabaseProfile("mysql") 
# Then call StopDatabaseMysqlProfile through a timer or other trigger method 
result = commonNetgameApi.StopDatabaseMysqlProfile("mysql") 
for single in result: 
action = single["action"] 
if action == "executefunc": 
print "do {} func={} orderKey={} cost={}s".format(action, single["func"], single["orderKey"], single["costTp"]) 
else: 
print "do {} orderKey={} cost={}s".format(action, single["orderKey"], single["costTp"]) 
``` 
<span id="StopYappiProfile"></span> 
#### StopYappiProfile 

- Description 

Stop server-side script performance analysis and generate flame graphs. Used with [StartYappiProfile()](#StartYappiProfile) 

- Parameters 

| Parameter Name | Data Type | Description | 
| :--- | :--- | :--- | 
| fileName | str | Specific path, relative to the path of the Apollo server startup directory. The default is "flamegraph.svg", located in the Apollo server startup directory. For custom paths, make sure the file suffix is ".svg" | 
- Return Value 

| Data Type | Description | 
| :--- | :--- | 
| bool | Execution Result | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.StartYappiProfile() 
modfunc()# Process the corresponding logic 
# Then call StopYappiProfile through a timer or other triggering method 
commonNetgameApi.StopYappiProfile() 
``` 
<span id="UnicodeConvert"></span> 
#### UnicodeConvert 

- Description 

Recursively convert all unicode strings in the input data to utf-8 format 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- |

| input | dict/list/tuple/str/unicode | Input data to be converted | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| dict/list/tuple/str/unicode | Same format as input data, unicode strings will be converted to utf-8 format | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
unicodeStr = "I am unicode encoded".decode("utf-8") 
input = { 
"a1": unicodeStr, 
"a2": [unicodeStr, unicodeStr], 
"a3": (unicodeStr, unicodeStr), 
} 
ret = commonNetgameApi.UnicodeConvert(input) 
``` 
<span id="世界"></span> 
### World 

<span id="AddRepeatedTimer"></span> 
#### AddRepeatedTimer 

- Description 

Add a timer triggered by the server and execute it repeatedly 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| delay | float | Delay time, in seconds | 
| func | func | Timer trigger function | 
| *args | *args | Variable length parameters, can be left blank | 
| **kwargs | **kwargs | Dictionary variable length parameters, can be left blank | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| timer | Return a single-trigger timer | 
- Example 

```python 
def doRepeatPrint(info): 
print "doRepeatPrint", info
import apolloCommon.commonNetgameApi as commonNetgameApi
commonNetgameApi.AddRepeatedTimer(2.0, doRepeatPrint, "this is repeat timer")
 ```
<span id="AddTimer"></span>

#### AddTimer 

- Description 

Add a server-triggered timer, non-repeating 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| delay | float | Delay time, in seconds | 
| func | func | Timer trigger function | 
| *args | *args | Variable length parameters, optional | 
| **kwargs | **kwargs | Dictionary variable length parameters, optional | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| timer | Return a single-trigger timer | 
- Example 

```python 
def doOncePrint(info): 
print "doOncePrint", info 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.AddTimer(5.0, doOncePrint, "this is once timer") 
``` 
<span id="CancelTimer"></span> 
#### CancelTimer 

- Description 

Cancel timer 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| timer | timer object | Timer object returned by AddTimer and AddRepeatedTimer | 
- Return value 

None 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.CancelTimer(timer) 
``` 
<span id="Player"></span> 
### Player


<span id="GetOnlineKey"></span> 
#### GetOnlineKey 

- Description 

Input the player's uid and return the key of the player's online identifier stored in redis 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player's uid | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| str | The key of the player's online identifier stored in redis; it is a hash table containing two hash keys: serverid, proxyid. If it cannot be obtained or only proxyid is obtained but serverid is not, it means that the player is not currently online | 
- Example 

```python 
import apolloCommon.commonNetgameApi as commonNetgameApi 
onlineKey = commonNetgameApi.GetOnlineKey(123) 
``` 
<span id="GetOnlineServerInfoOfMultiPlayers"></span> 
#### GetOnlineServerInfoOfMultiPlayers 

- Description 

Get multiple players' online information 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uids | list(int/long) | Player's netease uid list, the list cannot exceed 100, if it exceeds 100, this api will throw an Exception | 
| callback | function | callback function, which will be executed asynchronously. The function only needs one parameter, which is list(dict) type. Each dict contains the keys and meanings: "uid": the player's netease uid; "serverId": the server id of the lobby or game where the player is located, if the player is not online, it is None; "proxyId": the proxy server id connected by the client, if the player is not online, it is None; "protocolVersion": the player's client protocol version number, if the player is not online, it is None | 
- Return value 

None 
- Example 

```python 
def GetPlayersOnlineCb(args): 
#If the parameters are: {["uid":123, "isPeUser":True, "serverId" :2000000, "proxyId" :1000000, "protocolVersion":422},{"uid":234, "isPeUser":False, "serverId" :None, "proxyId" :None, "protocolVersion":None}] 
#Parameter meaning: The first player's uid is 123, the last time the player logged into the game was from a mobile phone, the player is online, the lobby or game server id is 2000000, the proxy server id the player is connected to is 1000000, and the player's client protocol version number is 422; 
# The second player's uid is 234, the last time the player logged into the game was from a PC, and the player is offline 
print 'GetOnlineServerCb', args 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.GetOnlineServerInfoOfMultiPlayers([123, 234], GetPlayersOnlineCb)

``` 
<span id="GetOnlineServerInfoOfPlayer"></span> 
#### GetOnlineServerInfoOfPlayer 

- Description 

Get player online information 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player's netease uid, unique identifier of the player | 
| callback | function | Callback function, which will be executed asynchronously. The function only needs one parameter, which is a dict type. The keys and meanings of dict: "uid": the player's netease uid; "serverId": the server id of the lobby or game where the player is located, or None if the player is not online; "proxyId": the proxy server id to which the client connects, or None if the player is not online; "protocolVersion": the player's client protocol version number, or None if the player is not online | 
- Return value 

None 
- Example 

```python 
def GetOnlineCb(args): 
#If the parameters are: {"uid":123, "isPeUser":True, "serverId" :2000000, "proxyId" :1000000, "protocolVersion":422} 
#Parameter meaning: The player's uid is 123, the last time the player logged in to the game was from the mobile phone, the player is online, the lobby or game server id is 2000000, the proxy server id the player is connected to is 1000000, and the player's client protocol version number is 422 
#If the parameters are: {"uid":123, "isPeUser":False, "serverId" :None, "proxyId" :None, "protocolVersion":None} 
#Parameter meaning: The player's uid is 123, the last time the player logged in to the game was from the PC, and the player is offline 
#Parameter meaning: If the value of isPeUser is None, it means that this player has never logged in to this game 
print 'GetOnlineServerCb', args 
import apolloCommon.commonNetgameApi as commonNetgameApi 
commonNetgameApi.GetOnlineServerInfoOfPlayer(123, GetOnlineCb) 
``` 
<span id="GetWeekOnlineKey"></span> 
#### GetWeekOnlineKey 

- Description 

Enter the player's uid and return the online time of this player saved in redis this week 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | Player's uid | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| str | The key of this player's online time saved in redis this week; it is a string, and after being converted to int, it is the number of seconds of this player's online time this week | 
<span id="ToPcUid"></span> 
#### ToPcUid 


- Description 

Convert the player's uid to the uid of the pc platform 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | The player's uid | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| int/long | The player's uid of the pc platform | 
<span id="ToPeUid"></span> 
#### ToPeUid 

- Description 

Convert the player's uid to the uid of the pe platform 

- Parameters 

| Parameter name | Data type | Description | 
| :--- | :--- | :--- | 
| uid | int/long | The player's uid | 
- Return value 

| Data type | Description | 
| :--- | :--- | 
| int/long | pe platform player uid | 
