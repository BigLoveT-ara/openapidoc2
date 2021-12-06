**接口说明**：查询企业下的各项资源及配置信息

**接口地址**：https://www.xfyeta.com/openapi/config/v1/query?token=08236d0aeeee4d5b566db5f4adc41a63

注：token的获取见入门指南的账户授权


### 请求参数说明

| 名称      | 必填 | 类型 |                             说明                             |
| --------- | :--: | :--: | :----------------------------------------------------------: |
| type      |  否  | int  | 配置项分类。<br>1：话术，<br>2：线路，<br>3：接口，<br>4：发音人，<br>0：全部（默认）。 |
| pageSize  |  否  | int  |                           分页大小                           |
| pageIndex |  否  | int  |                             页码                             |

### 请求示例

~~~
{
   "type": 1,
   "pageSize":10,
   "pageIndex":1
}
~~~

### 响应示例

~~~
{
    "code": 0,  
    "message": "ok",  
    "result": {
       "lines": [
           {
               "line_num": "055169101407",
               "concurrents": 10,
               "time_work": ["09:00:00-12:00:00", "13:00:00-17:59:59"],
               "status": 1,
               "time_apply": 1527321492000,
               "time_expire": 2592000
           },
           {
               "line_num": "055169101408",
               "concurrents": 100,
               "time_work": ["08:00:00-20:00:00"],
               "status": 0,
               "time_apply": 1527321492000,
               "time_expire": 2592000
           }
       ],
       "robotTotal":123
       "robots": [
           {
               "robot_id": "111111",
               "robot_name": "金融",
               "call_column":["客户手机号码","姓名","性别"],
               "status": 4,
               "type": 1,
               "deleted": 0,
               "time_create": 1527321492000,
               "time_update": 1527325092000
           }
       ],
       "urls": [
           {
               "url": "http://your-service.url/receiveCallRecord",
               "url_module": "receiveCallRecord"
           }
       ],
       "voices": [
           {
               "voice_code": "60020",
               "voice_name": "春春"
           }
       ]
    }  
    
}  
~~~

### result返回结果集说明

| 名称           |   类型   |      说明      |                           备注                           |
| -------------- | :------: | :------------: | :------------------------------------------------------: |
| **lines**      | object[] |      线路      |                                                          |
| line_num       |  string  |      号码      |                                                          |
| concurrents    |   int    |     并发数     |                                                          |
| time_work      | string[] |    工作时段    |                                                          |
| status         |   int    |      状态      |                 0：空闲，<br>1：任务占用中。             |
| time_apply     |   long   |    申请时间    |                        毫秒时间戳                        |
| time_expire    |   long   |     有效期     |                 单位：秒。-1：永久有效。                 |
| **robotTotal** |   Long   |    话术总量    |              进行话术分页时建议单独查询话术              |
| **robots**     | object[] |      话术      |                                                          |
| robot_id       |  string  |    话术编号    |                                                          |
| robot_name     |  string  |    话术名称    |                                                          |
| call_column    | string[] | 外呼数据列模板 |      第一列必须是客户手机号，<br>其他列是话术动态信息。  |
| status         |   int    |    话术状态    |       1：审核中，<br>2：未通过，<br>3：待发布，<br>4：已发布。       |
| type           |   int    |    话术类型    |                1：普通话术，<br>2：动态话术。                |
| deleted        |   int    |    删除标记    |                  0：未删除，<br>1：已删除。                  |
| time_create    |   long   |    创建时间    |                        毫秒时间戳                        |
| time_update    |   long   |    更新时间    |                        毫秒时间戳                        |
| **urls**       | object[] |    接口配置    |                                                          |
| url            |  string  |    接口URL     | 您的数据接收地址，<br>平台会向该地址推送数据<br>(话单/交互/录音) |
| url_module     |  string  |    接口模块    |                    详见接口模块清单                      |
| **voices**     | object[] |     发音人     |                                                          |
| voice_code     |  string  |   发音人编码   |                                                          |
| voice_name     |  string  |   发音人名称   |             |                                            |

### 接口模块清单

| url_module              | 描述                                                                           |
| ------------------------| :----------------------------------------------------------------------------: |
| receiveCallRecord       |   167企业所有话单结果推送到xxx                                                 |
| receiveDialog&#124;AppX	  |   167企业AppX应用的会话推送到xxx                                               |
| receiveVoice&#124;AppX&#124;4567  |   167企业Appx应用4567机器人的录音数据推送到xxx                                 |
| receiveVoice&#124;&#124;4567	  |   167企业4567机器人的录音数据推送到xxx                                         |
| getDialogContext	  |   电话呼入到167企业机器人时，<br>yeta通过xxx地址获得电话对应的话术动态信息。   |


### 常用发音人清单

| voice_name | voice_code | 性别 |
| ---------- | :--------: | :--: |
| 春春       |   65580    | 女声 |
| 晓诗       |   62140    | 女声 |
| 晓燕       |   60020    | 女声 |
| 晓峰       |   60030    | 男声 |
| 小陈       |   65660    | 男声 |
| 楠楠       |   60130    | 女声 |
| 晓医       |   65600    | 女声 |

具体发音效果建议通过Web话术预览进行体验。