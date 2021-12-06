

# 录音推送

接口模块名称：receiveVoice  
接口地址：[企业预先配置url]  

### 请求参数说明

| 名称             | 必填 |  类型  |    说明    |             备注              |
| ---------------- | :--: | :----: | :--------: | :---------------------------: |
| business_id      |      | string |   企业id   |                               |
| app_id           |      | string |   应用id   |                               |
| robot_id         |      | string |   话术id   |                               |
| task_data_id     |      | string | 外呼任务id |                               |
| call_relation_id |      | string | 呼入关联id |                               |
| call_uuid        |  是  | string |  通话UUID  |                               |
| url              |  是  | string |  url路径   | http://voice.kxjlcc.com:9000/ |
| size             |  是  |  long  |  文件大小  |             字节              |
| duration         |  是  |  int   |  录音长度  |              秒               |



### 请求示例

~~~
{
    "call_uuid":"809c825c-6483-11e8-b8db-2769c24918cd",
    "url":"ant/4/ivr/0/2018/05/31/0/452263-7571100e-7afc-42aa-9d69-ac25805d45b6.wav",
    "size":1043244,
    "duration":32,
    "business_id":"10527",
    "app_id":"123",
    "robot_id":"10527"
}

~~~

### 响应示例

接口返回"success"字符串代表成功

~~~
"success"
~~~
