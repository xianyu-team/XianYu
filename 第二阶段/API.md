# API
XianYux闲余挣闲钱系统API文档

## 服务器IP和端口号
- IP : 120.77.146.251
- Port : 8080

## 用户注册
> `POST /user`

**参数**
```
{
  "user_phone":     "string",  //手机号
  "user_password":  "string"   //密码
}
```

**返回值**
```
{
  "code":     integer,  //状态码
  "message":  "string"  //信息
}
```

**返回示例**
- 200
```
{
  "code":  200,
  "message":  "OK"
}
```
- 400
```
  "code":  400,
  "message":  "用户名已存在"
```

## 用户注册发送手机验证码
> `POST /user/phone_verification`

**参数**
```
{
  "user_phone":  "string"  //手机号
}
```

**返回值**
```
{
  "code":               integer,   //状态码
  "message":            "string",  //信息
  "verification_code":  "string"   //手机验证码
}
```

**返回示例**
- 200
```
{
  "code":  200,
  "message":  "OK",
  "verification_code":  "5128"
}
```
- 400
```
  "code":  400,
  "message":  "ERROR",
```

## 用户登录
> `POST /user/session`

**参数**
```
{
  "user_phone":     "string",  //手机号
  "user_password":  "string"   //密码
}
```

**返回值**
```
{
  "code":     integer,   //状态码
  "message":  "string",  //信息
}
```

**返回示例**
- 200
```
{
  "code":  200,
  "message":  "OK"
}
```
- 400
```
  "code":  400,
  "message":  "用户名或密码错误"
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
  "code":     integer,   //状态码
  "message":  "string",  //信息
}
```

**返回示例**
- 200
```
{
  "code":  200,
  "message":  "OK"
}
```
- 400
```
  "code":  400,
  "message":  "ERROR"
```

