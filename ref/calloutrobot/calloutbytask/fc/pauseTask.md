**接口说明**：暂时停止任务呼叫。可以通过启动外呼任务接口恢复任务呼叫。

**接口地址**：https://www.xfyeta.com/openapi/outbound/v1/task/pause?token=08236d0aeeee4d5b566db5f4adc41a63 

### 请求参数说明

| 名称    | 必填 |  类型  |  说明  |
| ------- | :--: | :----: | :----: |
| task_id |  是  | string | 任务id |

### 请求示例

~~~
{
   "task_id": "129"
}
~~~

### 响应示例

~~~
{
    "code": 0,  
    "message": "ok",  
    "result": {}     
}
~~~

### result返回结果集说明

无。通过code响应码表示是否成功。