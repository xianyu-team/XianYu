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


# 模型
## user
```
{
    user_phone           string     //手机号(主键)
    user_password        string     //密码
    user_display_name    string     //昵称
    user_icon            string     //头像(base64)
    user_balance         integer    //闲余币余额
}
```

## student
```
{
    student_id        string    //学生ID(主键)  
    student_name      string    //姓名
    student_number    string    //学号
    student_major     string    //专业
    student_grade     string    //年级
}
```

## order
```
{
    order_id                string     //订单ID(主键)
    order_type              string     //订单类型
    order_bonus             integer    //悬赏金额
    order_published_date    string     //发布时间  
    order_description       string     //订单描述      
    order_accepted          bool       //是否接受
    order_finished          bool       //是否完成
    order_finished_date     string     //发布时间  
}
```