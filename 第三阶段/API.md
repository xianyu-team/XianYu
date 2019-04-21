# API
XianYux闲余挣闲钱系统API文档

- [API](#api)
- [服务器IP和端口号](#%E6%9C%8D%E5%8A%A1%E5%99%A8ip%E5%92%8C%E7%AB%AF%E5%8F%A3%E5%8F%B7)
- [用户](#%E7%94%A8%E6%88%B7)
  - [获取手机验证码](#%E8%8E%B7%E5%8F%96%E6%89%8B%E6%9C%BA%E9%AA%8C%E8%AF%81%E7%A0%81)
  - [用户注册](#%E7%94%A8%E6%88%B7%E6%B3%A8%E5%86%8C)
  - [完善个人信息](#%E5%AE%8C%E5%96%84%E4%B8%AA%E4%BA%BA%E4%BF%A1%E6%81%AF)
  - [获取个人信息](#%E8%8E%B7%E5%8F%96%E4%B8%AA%E4%BA%BA%E4%BF%A1%E6%81%AF)
  - [用户密码登录](#%E7%94%A8%E6%88%B7%E5%AF%86%E7%A0%81%E7%99%BB%E5%BD%95)
  - [找回密码-手机验证](#%E6%89%BE%E5%9B%9E%E5%AF%86%E7%A0%81-%E6%89%8B%E6%9C%BA%E9%AA%8C%E8%AF%81)
  - [找回密码-重置密码](#%E6%89%BE%E5%9B%9E%E5%AF%86%E7%A0%81-%E9%87%8D%E7%BD%AE%E5%AF%86%E7%A0%81)
  - [用户短信登录](#%E7%94%A8%E6%88%B7%E7%9F%AD%E4%BF%A1%E7%99%BB%E5%BD%95)
  - [用户退出登录](#%E7%94%A8%E6%88%B7%E9%80%80%E5%87%BA%E7%99%BB%E5%BD%95)
- [任务](#%E4%BB%BB%E5%8A%A1)
  - [获取任务列表](#%E8%8E%B7%E5%8F%96%E4%BB%BB%E5%8A%A1%E5%88%97%E8%A1%A8)


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


## 完善个人信息
> `POST /user/profile`

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

# 任务

## 获取任务列表
> `GET /assignment`

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
    "assignment": {
    
    }
}
```

**返回示例**


