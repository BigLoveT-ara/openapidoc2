**接口说明**：用户在访问其他需要权限认证的接口时需要在请求的查询参数中携带此token，否则无法访问

**接口地址**：https://www.xfyeta.com/openapi/oauth/v1/token 

### 请求参数说明

| 名称       | 必填 |  类型  |       说明       |
| ---------- | :--: | :----: | :--------------: |
| app_key    |  是  | string |  应用的app_key   |
| app_secret |  是  | string | 应用的app_secret |

##### 如何获取您的app_key和app_secret?

使用您的yeta账户登录yeta平台，在后台“应用管理”中获取。

### 请求示例

~~~
POST /openapi/oauth/v1/token HTTP/1.1
Host: www.xfyeta.com
Content-Type: application/json;charset=UTF-8
Cache-Control: no-cache

{
   "app_key": "ODM1ZTk4ODAtYTMyZC00ZjBiLTkzMDQtY2VjNWU0ZDUyZWQ5",
   "app_secret": "MTM5NUM3NjlGQ0M2REUwN0FBREE3QjUxMkU1Qzg5NUQ="
}
~~~

### 响应示例

~~~
HTTP/1.1 200 OK
Content-Length:98
Date:Fri, 10 Aug 2018 06:58:01 GMT

{
    "code": 0,  
    "message": "ok",  
    "result": {
       "token": "08236d0aeeee4d5b566db5f4adc41a63",
       "time_expire": 3600
    }      
}
~~~

### result返回结果集说明

| 名称        | 必填 |  类型  |  说明  |         备注         |
| ----------- | :--: | :----: | :----: | :------------------: |
| token       |  是  | string |  令牌  |                      |
| time_expire |  是  |  long  | 有效期 | 单位：秒。默认3600。 |

