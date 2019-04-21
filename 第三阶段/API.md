# API
XianYux闲余挣闲钱系统API文档

- [API](#api)
- [服务器IP和端口号](#%E6%9C%8D%E5%8A%A1%E5%99%A8ip%E5%92%8C%E7%AB%AF%E5%8F%A3%E5%8F%B7)
- [用户](#%E7%94%A8%E6%88%B7)
  - [获取手机验证码](#%E8%8E%B7%E5%8F%96%E6%89%8B%E6%9C%BA%E9%AA%8C%E8%AF%81%E7%A0%81)
  - [用户注册](#%E7%94%A8%E6%88%B7%E6%B3%A8%E5%86%8C)
  - [完善或修改个人信息](#%E5%AE%8C%E5%96%84%E6%88%96%E4%BF%AE%E6%94%B9%E4%B8%AA%E4%BA%BA%E4%BF%A1%E6%81%AF)
  - [获取个人信息](#%E8%8E%B7%E5%8F%96%E4%B8%AA%E4%BA%BA%E4%BF%A1%E6%81%AF)
  - [用户密码登录](#%E7%94%A8%E6%88%B7%E5%AF%86%E7%A0%81%E7%99%BB%E5%BD%95)
  - [找回密码-手机验证](#%E6%89%BE%E5%9B%9E%E5%AF%86%E7%A0%81-%E6%89%8B%E6%9C%BA%E9%AA%8C%E8%AF%81)
  - [找回密码-重置密码](#%E6%89%BE%E5%9B%9E%E5%AF%86%E7%A0%81-%E9%87%8D%E7%BD%AE%E5%AF%86%E7%A0%81)
  - [用户短信登录](#%E7%94%A8%E6%88%B7%E7%9F%AD%E4%BF%A1%E7%99%BB%E5%BD%95)
  - [用户退出登录](#%E7%94%A8%E6%88%B7%E9%80%80%E5%87%BA%E7%99%BB%E5%BD%95)
  - [获得当前用户发布\领取的任务列表](#%E8%8E%B7%E5%BE%97%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E5%8F%91%E5%B8%83%E9%A2%86%E5%8F%96%E7%9A%84%E4%BB%BB%E5%8A%A1%E5%88%97%E8%A1%A8)
  - [获取当前用户的关注列表](#%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E7%9A%84%E5%85%B3%E6%B3%A8%E5%88%97%E8%A1%A8)
  - [获取当前用户的粉丝列表](#%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E7%9A%84%E7%B2%89%E4%B8%9D%E5%88%97%E8%A1%A8)
- [任务](#%E4%BB%BB%E5%8A%A1)
  - [获取任务大厅的任务列表](#%E8%8E%B7%E5%8F%96%E4%BB%BB%E5%8A%A1%E5%A4%A7%E5%8E%85%E7%9A%84%E4%BB%BB%E5%8A%A1%E5%88%97%E8%A1%A8)
  - [接受任务](#%E6%8E%A5%E5%8F%97%E4%BB%BB%E5%8A%A1)
  - [取消任务](#%E5%8F%96%E6%B6%88%E4%BB%BB%E5%8A%A1)
  - [发布任务](#%E5%8F%91%E5%B8%83%E4%BB%BB%E5%8A%A1)
- [钱包](#%E9%92%B1%E5%8C%85)
  - [获取当前用户的余额](#%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E7%9A%84%E4%BD%99%E9%A2%9D)
  - [获取当前用户的交易历史](#%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E7%9A%84%E4%BA%A4%E6%98%93%E5%8E%86%E5%8F%B2)
  - [当前用户的闲余币充值](#%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E7%9A%84%E9%97%B2%E4%BD%99%E5%B8%81%E5%85%85%E5%80%BC)


# 服务器IP和端口号
- IP : 120.77.146.251
- Port : 8080

# 用户

## 获取手机验证码
> `GET /user/phone_verification`

**参数**
```
{
    "user_phone":  "string"    //手机号
}
```

**返回值**
```
{
    "code":                 integer,     //状态码
    "message":              "string",    //信息
    "verification_code":    "string"     //手机验证码
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "verification_code": "5128"
}
```
- 400
```
    "code": 400,
    "message": "无效的手机号",
```


## 用户注册
> `POST /user`

**参数**
```
{
    "user_phone":       "string",    //手机号
    "user_password":    "string"     //密码
}
```

**返回值**
```
{
    "code":       integer,    //状态码
    "message":    "string"    //信息
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
}
```
- 400
```
    "code": 400,
    "message": "该手机号已经被注册"
```


## 完善或修改个人信息
> `PUT /user/profile`

**参数**
```
{
    "user_icon":       string,    //头像，图片的byte数组转成字符串
    "user_name":       string,    //真实姓名
    "user_school":     string,    //学校
    "user_academy":    string,    //学院
    "user_number":     string,    //学号
    "user_gender":     int        //性别，0为女，1为男
}
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```


## 获取个人信息
> `GET /user/profile`

**参数**
```
{
    无
}
```

**返回值**
```
{
    "user_phone":      string,    //手机号
    "user_icon":       string,    //头像，图片的byte数组转成字符串
    "user_name":       string,    //真实姓名
    "user_school":     string,    //学校
    "user_academy":    string,    //学院
    "user_number":     string,    //学号
    "user_gender":     int        //性别，0为女，1为男
}
```

**返回示例**
- 200
```
    "user_phone": "15988991556"
    "user_icon": "x\86\45...",    
    "user_name": "张三",   
    "user_school": "中山大学", 
    "user_academy": "数据科学与计算机学院",    
    "user_number": "16330033",   
    "user_gender": 0 
```
- 400
```
    "code": 400,
    "message": "ERROR"
```

## 用户密码登录
> `POST /user/password/session`

**参数**
```
{
    "user_phone":       "string",    //手机号
    "user_password":    "string"     //密码
}
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
}
```
- 400
```
    "code": 400,
    "message": "用户名或密码错误"
```


## 找回密码-手机验证
> `POST /user/password/phone_verification`

**参数**
```
{
    "user_phone":       "string",    //手机号
    "verification_code":    "string"     //验证码
}
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
}
```
- 400
```
    "code": 400,
    "message": "手机验证码错误"
```


## 找回密码-重置密码
> `PUT /user/password`

**参数**
```
{
    "user_phone":       string,
    "user_password":    string
}
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string"    //信息
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```


## 用户短信登录
> `POST /user/phone_verification/session`

**参数**
```
{
    "user_phone":       "string",    //手机号
    "verification_code":    "string"     //验证码
}
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
}
```
- 400
```
    "code": 400,
    "message": "手机验证码错误"
```


## 用户退出登录
> `DELETE /user/session`

**参数**
```
无
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```


## 获得当前用户发布\领取的任务列表
> `GET /user/order`

**参数**
```
{
    "type":    integer    //0为当前用户发布的，1为领取的
}
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
    "order": [
        {
            "order_id":                int,        //订单ID(主键)
            "order_type":              string,     //订单类型
            "order_bonus":             integer,    //悬赏金额
            "order_published_date":    string,     //发布时间  
            "order_description":       string,     //订单描述      
            "order_accepted":          bool,       //是否接受
            "order_finished":          bool,       //是否完成
            "order_finished_date":     string,     //完成时间  
        }
    ]
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
    "order": [
        {
            //省略...
        }
    ]
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```


## 获取当前用户的关注列表
> `GET /user/followings`

**参数**
```
无
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
    "user": [
        {
            "user_icon":       string,    //头像，图片的byte数组转成字符串
            "user_name":       string,    //真实姓名
            "user_school":     string,    //学校
            "user_academy":    string,    //学院
            "user_number":     string,    //学号
            "user_gender":     int        //性别，0为女，1为男
        }
    ]
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
    "user": [
        {
            //省略...
        }
    ]
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```



## 获取当前用户的粉丝列表
> `GET /user/fans`

**参数**
```
无
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
    "user": [
        {
            "user_icon":       string,    //头像，图片的byte数组转成字符串
            "user_name":       string,    //真实姓名
            "user_school":     string,    //学校
            "user_academy":    string,    //学院
            "user_number":     string,    //学号
            "user_gender":     int        //性别，0为女，1为男
        }
    ]
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
    "user": [
        {
            //省略...
        }
    ]
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```


# 任务

## 获取任务大厅的任务列表
> `GET /order`

**参数**
```
{
    "type":    int    //0为最新，1为最热，2为关注，3为按价钱排序
}
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
    "order": [
        {
            "order_id":                int,        //订单ID(主键)
            "order_type":              string,     //订单类型
            "order_bonus":             integer,    //悬赏金额
            "order_published_date":    string,     //发布时间  
            "order_description":       string,     //订单描述      
            "order_accepted":          bool,       //是否接受
            "order_finished":          bool,       //是否完成
            "order_finished_date":     string,     //完成时间  
            publisher: {
                "user_phone":          string,     //手机号
                "user_icon":           string,     //头像，图片的byte数组转成字符串
                "user_name":           string,     //真实姓名
                "user_school":         string,     //学校
                "user_academy":        string,     //学院
                "user_number":         string,     //学号
                "user_gender":         int         //性别，0为女，1为男
            }
        }
    ]
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "order": [
        {
            //省略...
        }
    ]
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```


## 接受任务
> `POST /order/acception` 

**参数**
```
{
    "order_id":    int    //订单ID(主键)
}
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```


## 取消任务
> `DELETE /order` 

**参数**
```
{
    "order_id":    int    //订单ID(主键)
}
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```


## 发布任务
> `POST /order` 

**参数**
```
{
    "order_type":              string,     //订单类型
    "order_bonus":             integer,    //悬赏金额
    "order_published_date":    string,     //发布时间  
    "order_description":       string,     //订单描述      
    "order_accepted":          bool,       //是否接受
    "order_finished":          bool,       //是否完成
    "order_finished_date":     string,     //完成时间
}
```

**返回值**
```
{
    "code":       integer,     //状态码
    "message":    "string",    //信息
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK"
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```


# 钱包

## 获取当前用户的余额
> `GET /balance`

**参数**
```
无
```

**返回值**
```
{
    "code":            integer,     //状态码
    "message":         "string",    //信息
    "user_balance":    double      //用户闲余币
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "user_balance": 100.20
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```


## 获取当前用户的交易历史
> `GET /balance/detail`

**参数**
```
无
```

**返回值**
```
{
    "code":            integer,     //状态码
    "message":         "string",    //信息
    "transaction": [
        {
            "type":                        string,     //"income"为收入，"expend"为支出
            "order": {
                "order_type":              string,     //订单类型
                "order_bonus":             integer,    //悬赏金额
                "order_published_date":    string,     //发布时间  
                "order_description":       string,     //订单描述      
                "order_accepted":          bool,       //是否接受
                "order_finished":          bool,       //是否完成
                "order_finished_date":     string,     //完成时间
            }
        }
    ]
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "transaction": [
        {
            //省略...
        }
    ]
}
```
- 400
```
    "code": 400,
    "message": "ERROR"
```


## 当前用户的闲余币充值
> `暂未开放`


