## 成功

以下是登录成功返回的信息
    
```json
{
   "status":200,
   "data":{
       "userinfo":{
           "id":59,
           "pid":0,
           "username":"sailengsi",
           "email":"mhleilei@163.com",
           "sex":"3",
           "status":1,
           "create_time":"2017-01-27 10:27:08",
           "birthday":"1992-11-05",
           "address":"苏州街52号院。",
           "token":"90f84db602b502cd5666b89064607a78",
           "access_status":2,
           "web_routers":null,
           "api_routers":null,
           "default_web_routers":null,
           "is_update_pass":1
       }
   }
}
```


## 错误

以下是操作错误返回的信息
```json
{
    "status":404,
    "msg":"登录信息失效"
}
```
