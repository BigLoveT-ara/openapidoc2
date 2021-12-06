# 语义数据查询

获取语义接口用于支持应用方的个性化语义处理需求场景；`Yeta开放平台`向应用方提供此次对话的`基本属性、话术上下文动态数据和人机交互过程数据`，`应用方`返回语义分析处理后的`结果数据`。

示例场景 —— 高血压语义接口：机器人询问用户血压之后，将用户语音输入内容提交给应用方，应用方根据其业务模型对输入的模糊内容进行语义分析和处理，提供评估诊断精确的结果数据。

接口地址：[企业预先配置url]  

### 请求参数说明

| 名称             | 必填 |  类型   |          说明          |         备注          |
| ---------------- | :--: | :-----: | :--------------------: | :-------------------: |
| business_id      |      | string  |         企业id         |                       |
| app_id           |      | string  |         应用id         |                       |
| robot_id         |      | string  |       话术话术id       |                       |
| task_data_id     |      | string  |       外呼任务id       |                       |
| call_relation_id |      | string  |       呼入关联id       |                       |
| call_uuid        |  是  | string  |        通话UUID        |                       |
| caller           |      | string  |        主叫号码        |                       |
| callee           |      | string  |        被叫号码        |                       |
| direction        |      | string  | 呼叫方向1:呼入  2:呼出 |                       |
| context          |      | string  |   话术上下文动态数据   |                       |
| code             |      | string  |      接口功能代码      |                       |
| task_id          |  是  | string  |         任务id         |                       |
| **dialog**       |  是  |  array  |        交互记录        |                       |
| seq              |      |   int   |        节点序号        |                       |
| role             |      | string  |        节点角色        | robot话术customer客户 |
| node_id          |      | string  |         节点id         |                       |
| node_name        |      | string  |        节点名称        |                       |
| node_type        |      | string  |        节点类型        |                       |
| label            |      | string  |        节点标签        |                       |
| tag_name         |      | string  |          意向          |                       |
| tag_desc         |      | string  |        意向说明        |                       |
| text_robot       |      | string  |      话术输出内容      |                       |
| text_man         |      | string  |      用户输入内容      |                       |
| question_id      |      | String  |        问题uuid        |                       |
| time_start       |      |  long   |     节点开始时间戳     |                       |
| time_speaking    |      |  long   |     用户说话时间戳     |                       |
| **hits**         |      |  array  |          命中          |                       |
| hit              |      | string  |        命中内容        |                       |
| pick             |      | boolean |        是否选中        |                       |
| answer_id        |      | string  |        回答uuid        |                       ||



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
    "code": "SELF1",
    "task_data_id": 275821623314507,
    "callee": "19900000001",
    "dialog": [
        {
            "node_type": "NormalNode",
            "text_robot": "测试18805512125发短信功能",
            "tag_name": "B",
            "reject": 0,
            "tag_desc": "中zhong",
            "node_name": "开始节点",
            "text_man": "18005699514",
            "has_reply": 1,
            "un_hit": 1,
            "seq": 0,
            "node_id": "words_start_8fafbbb1-9"
        },
        {
            "node_type": "NormalNode",
            "text_robot": "测试发短信功能辅助",
            "tag_name": "B",
            "reject": 1,
            "tag_desc": "中zhong",
            "node_name": "开始节点",
            "text_man": "18005699514",
            "has_reply": 1,
            "un_hit": 2,
            "seq": 1,
            "node_id": "words_start_8fafbbb1-9"
        },
        {
            "hit": {
                "pick": true,
                "name": "多次未识别发短信回答",
                "id": "judge_node_d2691c8b-5"
            },
            "node_type": "NormalNode",
            "text_robot": "多次未识别发短信",
            "reject": 0,
            "node_name": "多次未识别发短信",
            "text_man": "我199123456789",
            "has_reply": 1,
            "un_hit": 0,
            "seq": 2,
            "node_id": "words_node_ebf2b05d-6"
        },
        {
            "hit": {
                "pick": true,
                "name": "新建按键正确回答",
                "id": "judge_node_7d4db64c-4"
            },
            "node_type": "ConditionNode",
            "text_robot": "这是按键话术",
            "reject": 0,
            "node_name": "按键话术",
            "text_man": "18005699514",
            "has_reply": 1,
            "un_hit": 0,
            "seq": 3,
            "node_id": "words_node_0997e480-6"
        },
        {
            "node_type": "NormalNode",
            "text_robot": "结束语发短信",
            "reject": 0,
            "node_name": "结束语发短信",
            "text_man": "18005699514",
            "has_reply": 1,
            "un_hit": 0,
            "seq": 4,
            "node_id": "words_start_07deddaa-1"
        }
    ],
    "caller": "055196866001",
    "robot_id": 1993,
    "context": {
        "jwyuan": "ryhan",
        "按键话术": "19900000001",
        "开始节点": "19900000001",
        "手机号码": "19900000001",
        "结束语发短信": "19900000001",
        "多次未识别发短信": "我19900000001",
        "客户手机号码": "19900000001"
    },
    "call_uuid": "019G2J01JGCV5AO1345H7B5AES074LH5",
    "call_relation_id": "111",
    "reply": "18005699514",
    "business_id": 167,
    "app_id": "1232432",
    "direction": 1
}

~~~

### 响应示例

> 注：如果是提供数据给yeta平台，则返回数组里面的对象必须是{"key":"","type":"integer","value":8}格式
> 其中type的有效类型integer/string。平台推送数据的不做严格要求

~~~
[
    {
        "key": "reportorRelation",
        "type": "integer",
        "value": 8
    }
]
~~~
