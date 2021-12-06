# 会话推送

接口模块名称：receiveDialog  
接口地址：[企业预先配置url]  

### 请求参数说明

| 名称             | 必填 |  类型   |      说明      |            备注            |
| ---------------- | :--: | :-----: | :------------: | :------------------------: |
| business_id      |      | string  |     企业id     |                            |
| app_id           |      | string  |     应用id     |                            |
| robot_id         |      | string  |   话术话术id   |                            |
| task_id          |      | string  |     任务id     |                            |
| task_data_id     |      | string  | 外呼任务数据id | task_data_id是任务id的子集 |
| call_relation_id |      | string  |   呼入关联id   |                            |
| call_uuid        |  是  | string  |    通话UUID    |                            |
| time_begin       |      |  long   |   开始时间戳   |                            |
| time_end         |      |  long   |   结束时间戳   |                            |
| **dialog**       |  是  |  array  |    交互记录    |                            |
| 	seq          |      |   int   |    节点序号    |                            |
| 	role         |      | string  |    节点角色    |   robot机器人customer客户   |
| 	node_id      |      | string  |     节点id     |                            |
| 	node_name    |      | string  |    节点名称    |                            |
| 	node_type    |      | string  |    节点类型    |                            |
| content_id | | string | 话术节点设置ID | |
| 	label        |      | string  |    节点标签    |                            |
| 	tag_name     |      | string  |      意向      |                            |
| 	tag_desc     |      | string  |    意向说明    |                            |
| 	text_robot   |      | string  |  话术输出内容  |                            |
| 	text_man     |      | string  |  用户输入内容  |                            |
| 	question_id  |      | String  |    问题uuid    |                            |
| 	time_start   |      |  long   | 节点开始时间戳 |                            |
| 	time_speaking  |      |  long   | 用户说话时间戳 |                            |
| **hits**     |      |  array  |      命中      |                            |
| hit      |      | string  |    命中内容    |                            |
| pick     |      | boolean |    是否选中    |                            |
| answer_id |      | string  |    回答uuid    |                            |  |

#### node_type节点类型说明

| node_type         |      说明      |
| ----------------- | :------------: |
| AnyNode           |  任意回答节点  |
| CollectInputNode  | 自定义输入节点 |
| ConditionNode     |  按键输入节点  |
| EndNode           |    结束节点    |
| HookInfoNode      |  动态引用节点  |
| KeyNavigationNode |  按键导航节点  |
| NoNeedAnswerNode  |  无需回答节点  |
| NormalNode        |  普通交互节点  |

### 请求示例

~~~
{
    "business_id": "10527",
    "app_id": "123",
    "robot_id": "10527",
    "call_uuid": "f3b13ebc-6394-11e8-907d-ebcc4d560c04",
    "task_id":"3457986492696704",
    "task_data_id":"346252615123869699",
    "call_relation_id":"346252615123869699",
    "time_begin":1618795847425,
    "time_end":1618795868298,
    "dialog": [
        {
            "seq": "6",
            "role": "customer",
            "node_id": "words_node_9bdd01e7-1",
            "node_name": "开场询问",
            "node_type": "NormalNode",
            "content_id": "a75f4j9uN32d440b13ac08m",
            "time_start": 1618795849743,
            "time_speaking": 1618795858958,
            "text_robot": "喂,您好!",
            "text_man": "你说",
            "question_id": "",
            "hits": [
                {
                    "hit": "肯定",
                    "pick": true,
                    "answer_id": ""
                }
            ]
        },
        {
            "seq": "7",
            "role": "robot",
            "node_id": "words_node_97ab88da-d",
            "node_name": "优惠券介绍",
            "node_type": "NormalNode",
            "time_start": 1618795859788,
            "text_robot": "喂,您好!",
            "text_man": "",
            "question_id": ""
        }
    ]
}
~~~

### 响应示例

接口返回"success"字符串代表成功

~~~
"success"
~~~
