**接口说明**：查询任务信息和任务列表。

**接口地址**：https://www.xfyeta.com/openapi/outbound/v1/task/query?token=08236d0aeeee4d5b566db5f4adc41a63  

### 请求参数说明

| 名称             | 必填 |  类型   |              说明               |                             备注                             |
| ---------------- | :--: | :-----: | :-----------------------------: | :----------------------------------------------------------: |
| task_id          |  否  | string  |             任务id              |                                                              |
| time_begin       |  否  |  long   |            开始时间             |                                                              |
| time_end         |  否  |  long   |            结束时间             |                                                              |
| task_name        |  否  | string  |            任务名称             |                           模糊检索                           |
| task_status_list |  否  |  int[]  |          任务状态数组           | 0：新建，<br>1：启动，<br>2：运行，<br>3：手动暂停，<br>4：完成，<br>5：等待下轮重试，<br>6：不在工作时段，<br>7：过期 |
| page_size        |  否  |   int   |             页大小              |                       最大值50，默认20                       |
| page_index       |  否  |   int   |            当前页码             |                           从1开始                            |
| sort_name        |  否  | string  |            排序字段             | ID：任务编号，<br>NAME：任务名称，<br>CREATETIME：任务创建时间<br>，STARTTIME：任务开始时间<br>，ENDTIME：任务结束时间 |
| sort_order       |  否  | string  |          排序字段方式           |                    "ASC" 正序 <br>"DESC" 倒序                    |
| show_remaining   |  否  | boolean |       是否展示正在处理的数量 |  |                                                            |

### 请求示例

~~~
{
  "time_begin": 153000000,
  "show_remaining":true
}
~~~

### 响应示例

~~~
{
    "code":0,
    "message":"ok",
    "result":{
        "total_rows":30,
        "rows":[
            {
                "task_id":"1909",
                "task_name":"task_test1",
                "status":4,
                "deleted":0,
                "time_task_start":1533289491345,
                "time_task_finish":1533820104848,
                "count_total_task":4,
                "count_tel":4,
                "count_recalled":0,
                "time_task_estimate_begin":1478157571217,
                "time_task_estimate_end":0,
                "line_num":"96866001",
                "robot_id":"719",
                "robot_name":"测试话术无参数",
                "voice_code":"60030",
                "voice_speed":1,
                "count_max_recall":2,
                "status_recall":"[1,1]",
                "time_recall_wait":2000,
                "time_range":"["07:30:00-23:30:00"]",
                "intention_push":"["A","B"]",
                "process_count":7,
                "process_tel_count":7,
                "process_through_count":4,
                "process_through_rate":1
                "remaining":12
            }
        ]
    }
}
~~~


### result返回结果集说明

| 名称                     |   类型   |       必填       |         说明         |                             值域                             |
| ------------------------ | :------: | :--------------: | :------------------: | :----------------------------------------------------------: |
| total_rows               |   int    |        是        |        总行数        |                                                              |
| **rows**                 | object[] |        是        |       结果列表       |                                                              |
| task_id                  |  string  |        是        |        任务id        |                                                              |
| task_name                |  string  |        否        |       任务名称       |                                                              |
| status                   |   int    |        是        |       任务状态       | 0：新建，<br>1：启动，<br>2：运行，<br>3：手动暂停，<br>4：完成，<br>5：等待下轮重试，<br>6：不在工作时段，<br>7：过期 |
| task_type                |   int    |        是        |       任务类型       |                    0：普通任务,<br>2：任务池                     |
| deleted                  |   int    |        否        |       删除标志       |                       1：删除，<br>0：正常                       |
| time_task_start          |   long   |        否        |     运行开始时间     |                          毫秒时间戳                          |
| time_task_finish         |   long   | 否(仅限普通任务) |     运行结束时间     |                          毫秒时间戳                          |
| process_count            |   int    |        否        |      已呼叫次数      |                                                              |
| process_tel_count        |   int    |        否        |     已呼叫号码数     |                                                              |
| process_through_count    |   int    |        否        |       已接通量       |                                                              |
| process_through_rate     |  double  |        否        |      当前接通率      |                                                              |
| count_tel                |   int    |        否        |      任务号码量      |                                                              |
| count_recalled           |   int    | 否(仅限普通任务) |    任务已重试次数    |                                                              |
| time_task_estimate_begin |   long   | 否(仅限普通任务) |     预设开始时间     |                                                              |
| time_task_estimate_end   |   long   | 否(仅限普通任务) |     预设结束时间     |                                                              |
| line_num                 |  string  | 否(仅限普通任务) |       线路号码       |                                                              |
| robot_id                 |  string  | 否(仅限普通任务) |        话术id        |                                                              |
| robot_name               |  string  | 否(仅限普通任务) |       话术名称       |                                                              |
| voice_code               |  string  | 否(仅限普通任务) |      发音人编码      |                                                              |
| voice_speed              |   int    | 否(仅限普通任务) |  发音人语速，默认1   |                                                              |
| count_max_recall         |   int    | 否(仅限普通任务) |   预设任务重试次数   |                                                              |
| time_recall_wait         |   int    | 否(仅限普通任务) | 预设重试外呼等待时间 |                          单位：秒。                          |
| time_range               |  string  | 否(仅限普通任务) |    预设外呼时间段    |                                                              |
| intention_push           |  string  | 否(仅限普通任务) |  预设推送意向度门限  |                                                              |
| remaining                |   int    |        否        |  正在处理的数量      |                                                              |