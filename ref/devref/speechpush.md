

# 话单推送

接口模块名称：receiveCallRecord

接口地址：[企业预先配置url]  

注意：为了满足应用方对即时性的要求，平台对外呼的话单可能会进行两次推送。两次推送分别为基本属性话单消息和外呼属性话单消息，外呼话单消息中包含基本话单消息的所有字段项，两种消息可以通过是否包含task_row_index属性进行区分。受限于网络等因素，两次话单推送的顺序不做保证。
可以通过接听时间戳time_answer判定是否接通。

### 请求参数说明

| 名称             |  必填  |  类型  |     说明     |          备注          |
| ---------------- | :----: | :----: | :----------: | :--------------------: |
| business_id      |        | string |    企业id    |                        |
| app_id           |        | string |    应用id    |                        |
| robot_id         |        | string |  话术话术id  |                        |
| call_uuid        |   是   | string |   通话UUID   | 录音和会话的唯一关联。 |
| caller           |        | string |   主叫号码   |                        |
| callee           |        | string |   被叫号码   |                        |
| direction        |   是   |  int   |   呼叫方向   |     1:呼入 2 呼出      |
| time_answer      |   是   |  long  |  接听时间戳  |       unix_time        |
| time_hangup      |   是   |  long  |  挂断时间戳  |       unix_time        |
| duration_ring    |   是   |  int   | 拨号振铃时长 |           秒           |
| duration_call    |   是   |  int   |   通话时长   |           秒           |
| call_relation_id | 仅呼入 | string |    关联ID    |    业务侧的唯一标识    |
| task_id          | 仅呼出 | string |  外呼任务id  |                        |
| task_data_id     | 仅呼出 | string |  外呼任务id  |                        |
| time_dial        | 仅呼出 |  long  |  拨号时间戳  |       unix_time        |
| time_ring        | 仅呼出 |  long  |  振铃时间戳  |       unix_time        |
| task_result      | 仅呼出 | string |   外呼结果   |                        |
| task_result_desc | 仅呼出 | string | 外呼结果描述 |                        |
| task_tries       | 仅呼出 |  int   | 外呼重试次数 |                        |
| task_row_index   | 仅呼出 |  int   | 外呼数据行号 |                        |
| task_row_head    | 仅呼出 | array  | 外呼数据行头 |                        |
| task_row_value   | 仅呼出 | array  | 外呼数据行值 |                        |   |

#### 外呼结果说明

| task_result |   task_result_desc   |                  备注                  |
| ----------- | :------------------: | :------------------------------------: |
| -1          |         超时         |                                        |
| 0           |         成功         |                                        |
| 2           |      正在通话中      |                                        |
| 3           |       无法接通       |           无法接听,无法接通            |
| 4           |         关机         |                                        |
| 5           |       用户正忙       |           短忙音,长忙音,静音           |
| 6           |         空号         |               空号,改号                |
| 7           |       号码错误       |                                        |
| 8           |       用户拒接       |                用户拒接                |
| 9           |         停机         |           停机,暂停服务,欠费           |
| 15          | 客户接听后并主动挂机 |                                        |
| 16          |       客户掉线       |                                        |
| 18          |         接通         |                                        |
| 19          |        转人工        |                                        |
| 20          |       用户未接       | 回铃音,彩铃,无人接听,用户拒接,来电提醒 |
| 22          |       来电提醒       |                                        |
| 23          |       呼入限制       |                                        |
| 25          |       呼叫转移       |              呼叫转移失败              |
| 26          |       网络故障       |                                        |
| 27          |       呼出受限       |             拨号方式不正确             |
| 28          |       线路故障       |            线路故障,网络忙             |

### 请求示例

~~~
{
    "business_id":"2745",
    "app_id":"test",
    "robot_id":"2745001",
    "call_uuid":"123425c-6483-11e8-b8fa-2769c24918cd",
    "call_relation_id":"test-123",
    "task_id":"0",
    "task_data_id":"262381",
    "caller":"055196866001",
    "callee":"19900000001",
    "direction":1,
    "time_dial":1527737756729,
    "time_ring":1527737757449,
    "time_answer":1527737763429,
    "time_hangup":1527737784829,
    "duration_ring":7,
    "duration_call":28,
    "task_result":"0",
    "task_result_desc":"成功",
    "task_tries":0,
    "task_row_index":34951420,
    "task_row_head":[
        "客户手机号码",
        "装货时间",
        "装货地三级地址",
        "卸货地三级地址"
    ],
    "task_row_value":[
        "0271111111",
        "3月13日",
        "河北省张家口市张北县",
        "天津市天津市宁河区"
    ]
}
~~~

### 响应示例

接口返回"success"字符串代表成功

~~~
"success"
~~~

