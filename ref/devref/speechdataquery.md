# 话术动态数据查询

**此接口仅面向电话呼入对接，且话术存在动态数据的业务场景，其它场景可以不实现此接口。**

yeta开放平台在电话呼入时主动请求应用方接口

接口模块名称：getDialogContext

接口地址：[企业预先配置url]  

### 请求参数说明

| 名称             | 必填 |  类型  |     说明     |            备注             |
| ---------------- | :--: | :----: | :----------: | :-------------------------: |
| business_id      |      | string |    企业id    |   取自sip头X-business-id    |
| app_id           |      | string |    应用id    |      取自sip头X-app-id      |
| robot_id         |      | string |  话术话术id  |     取自sip头X-robot-id     |
| call_relation_id |  是  | string | 业务侧关联id | 取自sip头X-call-relation-id |

### 请求示例

~~~
{
	"call_relation_id":"1111",
	"business_id":"167",
	"app_id":"3333",
	"robot_id":"4444"
}
~~~

### 响应示例

map<string,string> 当前通话话术要求的上下文动态数据

~~~
{
    "key1": "value1",
    "性别": "男",
    "姓名": "张三"
}
~~~

