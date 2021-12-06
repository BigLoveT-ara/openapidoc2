**接口说明**：创建一个外呼任务

**接口地址**：https://www.xfyeta.com/openapi/outbound/v1/task/create?token=08236d0aeeee4d5b566db5f4adc41a63 


### 请求参数说明

| 名称             | 必填 |   类型   |                             说明                             |                  备注                  |
| ---------------- | :--: | :------: | :----------------------------------------------------------: | :------------------------------------: |
| task_name        |  是  |  string  |                           任务名称                           |                                        |
| line_num         |  是  |  string  |                           线路号码                           |          如果是多个，分号分隔          |
| robot_id         |  是  |  string  |                            话术id                            |                                        |
| recall_count     |  否  |   int    |                         重试外呼次数                         |             最大3次，默认0             |
| time_recall_wait |  否  |   long   |                         重试等待时间                         |                 单位秒                 |
| time_range       |  是  | string[] | 外呼时间段，<br>例如:["09:00:00-12:00:00", <br>"13:30:00-20:00:00"] <br>| 注意该时间需要在<br>企业允许的工作时间之内 |
| time_begin       |  是  |   long   |                         任务开始时间                         |               毫秒时间戳               |
| time_end         |  否  |   long   |                         任务结束时间                         |               毫秒时间戳               |
| voice_code       |  否  |  string  |                          发音人编码                          |                                        |
| trubo_mode       |  否  | boolean  |                          高性能模式                          |               默认false                |

### 请求示例

~~~
{
   "task_name": "测试外呼",
   "line_num": "055169101407",
   "robot_id": "11",
   "recall_count": 1,
   "time_recall_wait": 600,
   "time_range": ["09:00:00-12:00:00", "13:00:00-17:30:00"],
   "time_begin": 1527321492000,
   "time_end": 1527325092000
}
~~~

### 响应示例

~~~
{
    "code": 0,  
    "message": "ok",  
    "result": {
       "task_id": "129"
    }     
}
~~~


### result返回结果集说明

| 名称    |  类型  |               说明               |
| ------- | :----: | :------------------------------: |
| task_id | string | 任务Id。用于任务数据提交和管理。 |
