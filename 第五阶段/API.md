# API
XianYux闲余挣闲钱系统API文档

- [API](#api)
- [服务器IP和端口号](#%E6%9C%8D%E5%8A%A1%E5%99%A8ip%E5%92%8C%E7%AB%AF%E5%8F%A3%E5%8F%B7)
- [前端请求设置（注意！！！）](#%E5%89%8D%E7%AB%AF%E8%AF%B7%E6%B1%82%E8%AE%BE%E7%BD%AE%E6%B3%A8%E6%84%8F)
  - [前端请求路径](#%E5%89%8D%E7%AB%AF%E8%AF%B7%E6%B1%82%E8%B7%AF%E5%BE%84)
  - [前端请求参数的数据类型](#%E5%89%8D%E7%AB%AF%E8%AF%B7%E6%B1%82%E5%8F%82%E6%95%B0%E7%9A%84%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B)
  - [前端请求header设置X-CSRFtoken](#%E5%89%8D%E7%AB%AF%E8%AF%B7%E6%B1%82header%E8%AE%BE%E7%BD%AEx-csrftoken)
- [手机短信](#%E6%89%8B%E6%9C%BA%E7%9F%AD%E4%BF%A1)
  - [向手机发送验证码](#%E5%90%91%E6%89%8B%E6%9C%BA%E5%8F%91%E9%80%81%E9%AA%8C%E8%AF%81%E7%A0%81)
  - [验证手机验证码](#%E9%AA%8C%E8%AF%81%E6%89%8B%E6%9C%BA%E9%AA%8C%E8%AF%81%E7%A0%81)
- [用户](#%E7%94%A8%E6%88%B7)
  - [用户注册](#%E7%94%A8%E6%88%B7%E6%B3%A8%E5%86%8C)
  - [完善或修改当前用户的信息](#%E5%AE%8C%E5%96%84%E6%88%96%E4%BF%AE%E6%94%B9%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E7%9A%84%E4%BF%A1%E6%81%AF)
  - [获取当前用户的信息](#%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E7%9A%84%E4%BF%A1%E6%81%AF)
  - [用户密码登录](#%E7%94%A8%E6%88%B7%E5%AF%86%E7%A0%81%E7%99%BB%E5%BD%95)
  - [找回密码-重置密码](#%E6%89%BE%E5%9B%9E%E5%AF%86%E7%A0%81-%E9%87%8D%E7%BD%AE%E5%AF%86%E7%A0%81)
  - [用户短信登录](#%E7%94%A8%E6%88%B7%E7%9F%AD%E4%BF%A1%E7%99%BB%E5%BD%95)
  - [用户退出登录](#%E7%94%A8%E6%88%B7%E9%80%80%E5%87%BA%E7%99%BB%E5%BD%95)
  - [获取当前用户的余额](#%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E7%9A%84%E4%BD%99%E9%A2%9D)
  - [获得当前用户发布/领取的所有任务id和共同属性](#%E8%8E%B7%E5%BE%97%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E5%8F%91%E5%B8%83%E9%A2%86%E5%8F%96%E7%9A%84%E6%89%80%E6%9C%89%E4%BB%BB%E5%8A%A1id%E5%92%8C%E5%85%B1%E5%90%8C%E5%B1%9E%E6%80%A7)
  - [根据用户/关注的人/粉丝id批量获取用户信息(user_id/following_id/fan_id都适用)](#%E6%A0%B9%E6%8D%AE%E7%94%A8%E6%88%B7%E5%85%B3%E6%B3%A8%E7%9A%84%E4%BA%BA%E7%B2%89%E4%B8%9Did%E6%89%B9%E9%87%8F%E8%8E%B7%E5%8F%96%E7%94%A8%E6%88%B7%E4%BF%A1%E6%81%AFuseridfollowingidfanid%E9%83%BD%E9%80%82%E7%94%A8)
  - [当前用户关注其它用户](#%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E5%85%B3%E6%B3%A8%E5%85%B6%E5%AE%83%E7%94%A8%E6%88%B7)
  - [当前用户取关其它用户](#%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E5%8F%96%E5%85%B3%E5%85%B6%E5%AE%83%E7%94%A8%E6%88%B7)
  - [获取当前用户关注的所有用户的id](#%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E5%85%B3%E6%B3%A8%E7%9A%84%E6%89%80%E6%9C%89%E7%94%A8%E6%88%B7%E7%9A%84id)
  - [获取当前用户的所有粉丝的id](#%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E7%9A%84%E6%89%80%E6%9C%89%E7%B2%89%E4%B8%9D%E7%9A%84id)
- [任务](#%E4%BB%BB%E5%8A%A1)
  - [关于任务API（注意事项）](#%E5%85%B3%E4%BA%8E%E4%BB%BB%E5%8A%A1api%E6%B3%A8%E6%84%8F%E4%BA%8B%E9%A1%B9)
  - [获取任务大厅的所有任务id和共同属性](#%E8%8E%B7%E5%8F%96%E4%BB%BB%E5%8A%A1%E5%A4%A7%E5%8E%85%E7%9A%84%E6%89%80%E6%9C%89%E4%BB%BB%E5%8A%A1id%E5%92%8C%E5%85%B1%E5%90%8C%E5%B1%9E%E6%80%A7)
  - [根据任务id获取拿快递和外卖的详细信息](#%E6%A0%B9%E6%8D%AE%E4%BB%BB%E5%8A%A1id%E8%8E%B7%E5%8F%96%E6%8B%BF%E5%BF%AB%E9%80%92%E5%92%8C%E5%A4%96%E5%8D%96%E7%9A%84%E8%AF%A6%E7%BB%86%E4%BF%A1%E6%81%AF)
  - [根据任务id获取问卷和题目的详细信息](#%E6%A0%B9%E6%8D%AE%E4%BB%BB%E5%8A%A1id%E8%8E%B7%E5%8F%96%E9%97%AE%E5%8D%B7%E5%92%8C%E9%A2%98%E7%9B%AE%E7%9A%84%E8%AF%A6%E7%BB%86%E4%BF%A1%E6%81%AF)
  - [接受一个跑腿的任务(前端需要判断任务是否是自己发布的, 是否有人领取了, 是否取消了)](#%E6%8E%A5%E5%8F%97%E4%B8%80%E4%B8%AA%E8%B7%91%E8%85%BF%E7%9A%84%E4%BB%BB%E5%8A%A1%E5%89%8D%E7%AB%AF%E9%9C%80%E8%A6%81%E5%88%A4%E6%96%AD%E4%BB%BB%E5%8A%A1%E6%98%AF%E5%90%A6%E6%98%AF%E8%87%AA%E5%B7%B1%E5%8F%91%E5%B8%83%E7%9A%84-%E6%98%AF%E5%90%A6%E6%9C%89%E4%BA%BA%E9%A2%86%E5%8F%96%E4%BA%86-%E6%98%AF%E5%90%A6%E5%8F%96%E6%B6%88%E4%BA%86)
  - [完成拿快递和外卖的任务(平台把钱给领取者)](#%E5%AE%8C%E6%88%90%E6%8B%BF%E5%BF%AB%E9%80%92%E5%92%8C%E5%A4%96%E5%8D%96%E7%9A%84%E4%BB%BB%E5%8A%A1%E5%B9%B3%E5%8F%B0%E6%8A%8A%E9%92%B1%E7%BB%99%E9%A2%86%E5%8F%96%E8%80%85)
  - [发布者取消拿快递和外卖的任务(钱退回给发布者)(前端需要保证只能取消未完成的任务)](#%E5%8F%91%E5%B8%83%E8%80%85%E5%8F%96%E6%B6%88%E6%8B%BF%E5%BF%AB%E9%80%92%E5%92%8C%E5%A4%96%E5%8D%96%E7%9A%84%E4%BB%BB%E5%8A%A1%E9%92%B1%E9%80%80%E5%9B%9E%E7%BB%99%E5%8F%91%E5%B8%83%E8%80%85%E5%89%8D%E7%AB%AF%E9%9C%80%E8%A6%81%E4%BF%9D%E8%AF%81%E5%8F%AA%E8%83%BD%E5%8F%96%E6%B6%88%E6%9C%AA%E5%AE%8C%E6%88%90%E7%9A%84%E4%BB%BB%E5%8A%A1)
  - [新建一个拿快递和外卖的任务(发布者把钱寄存在平台上, 当任务完成, 平台将钱给完成者)](#%E6%96%B0%E5%BB%BA%E4%B8%80%E4%B8%AA%E6%8B%BF%E5%BF%AB%E9%80%92%E5%92%8C%E5%A4%96%E5%8D%96%E7%9A%84%E4%BB%BB%E5%8A%A1%E5%8F%91%E5%B8%83%E8%80%85%E6%8A%8A%E9%92%B1%E5%AF%84%E5%AD%98%E5%9C%A8%E5%B9%B3%E5%8F%B0%E4%B8%8A-%E5%BD%93%E4%BB%BB%E5%8A%A1%E5%AE%8C%E6%88%90-%E5%B9%B3%E5%8F%B0%E5%B0%86%E9%92%B1%E7%BB%99%E5%AE%8C%E6%88%90%E8%80%85)
  - [新建一个问卷任务(执行这个操作, 发布者会先把钱给平台)](#%E6%96%B0%E5%BB%BA%E4%B8%80%E4%B8%AA%E9%97%AE%E5%8D%B7%E4%BB%BB%E5%8A%A1%E6%89%A7%E8%A1%8C%E8%BF%99%E4%B8%AA%E6%93%8D%E4%BD%9C-%E5%8F%91%E5%B8%83%E8%80%85%E4%BC%9A%E5%85%88%E6%8A%8A%E9%92%B1%E7%BB%99%E5%B9%B3%E5%8F%B0)
  - [填写者提交问卷的答案(前端需要保证只填写未截止的问卷)](#%E5%A1%AB%E5%86%99%E8%80%85%E6%8F%90%E4%BA%A4%E9%97%AE%E5%8D%B7%E7%9A%84%E7%AD%94%E6%A1%88%E5%89%8D%E7%AB%AF%E9%9C%80%E8%A6%81%E4%BF%9D%E8%AF%81%E5%8F%AA%E5%A1%AB%E5%86%99%E6%9C%AA%E6%88%AA%E6%AD%A2%E7%9A%84%E9%97%AE%E5%8D%B7)
  - [填写者获取自己填写过的答卷(包含题目和答案)](#%E5%A1%AB%E5%86%99%E8%80%85%E8%8E%B7%E5%8F%96%E8%87%AA%E5%B7%B1%E5%A1%AB%E5%86%99%E8%BF%87%E7%9A%84%E7%AD%94%E5%8D%B7%E5%8C%85%E5%90%AB%E9%A2%98%E7%9B%AE%E5%92%8C%E7%AD%94%E6%A1%88)
  - [发布者查看问卷的统计信息](#%E5%8F%91%E5%B8%83%E8%80%85%E6%9F%A5%E7%9C%8B%E9%97%AE%E5%8D%B7%E7%9A%84%E7%BB%9F%E8%AE%A1%E4%BF%A1%E6%81%AF)
  - [发布者截止问卷](#%E5%8F%91%E5%B8%83%E8%80%85%E6%88%AA%E6%AD%A2%E9%97%AE%E5%8D%B7)
- [账单](#%E8%B4%A6%E5%8D%95)
  - [获取当前用户的交易历史](#%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E7%9A%84%E4%BA%A4%E6%98%93%E5%8E%86%E5%8F%B2)
  - [当前用户的闲余币充值](#%E5%BD%93%E5%89%8D%E7%94%A8%E6%88%B7%E7%9A%84%E9%97%B2%E4%BD%99%E5%B8%81%E5%85%85%E5%80%BC)

# 服务器IP和端口号
- IP : 120.77.146.251
- Port : 8000


# 前端请求设置（注意！！！）

## 前端请求路径

例如，密码登录的请求路径为：http://120.77.146.251:8000/user/password/session

其它API同理

## 前端请求参数的数据类型

前端的请求参数为`json`类型，在请求的header中设置为`"Content-Type": "application/json"`

## 前端请求header设置X-CSRFtoken

登录后，后端会在cookie中设置csrftoken(string类型)并返回给前端

对于登录后的请求, 前端需要获取cookie，然后在cookie中获取csrftoken字段的值，类似于`csrf = cookies.get("csrftoken")`

获取了csrftoken，就在header中设置X-CSRFtoken字段：`"X-CSRFtoken": csrf`，若csrf为空，就设置为：`"X-CSRFtoken": ""`，否则会无法通过csrf验证, 返回一个403


# 手机短信

## 向手机发送验证码
> `GET /sms/verification_code/{user_phone}`

**参数**
```
把 url 中的 {user_phone} 替换成 11 位数字手机号
```

**参数示例**
```
GET /sms/verification_code/15989061915
```

**返回值**

```
{
    "code":       integer,    //状态码
    "message":    string,     //信息
    "data": {}                //数据，这里为空对象
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {}
}
```
- 400
```
    "code": 400,
    "message": "验证码发送失败"  //服务器发生错误（备选）
                              
```


## 验证手机验证码
> `POST /sms/verification`

**参数**
```
{
    "user_phone":           string,    //手机号
    "verification_code":    string,    //验证码
}
```

**参数示例**
```
{
    "user_phone": "15989061915",
    "verification_code": "5218"
}
```

**返回值**
```
{
    "code":       integer,    //状态码
    "message":    string,     //信息
    "data": {}                //数据，这里为空对象
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {}
}
```
- 400
```
    "code": 400,
    "message": "手机验证码错误"  //服务器发生错误（备选）
```


# 用户

## 用户注册
> `POST /user`

**参数**

```
{
    "user_phone":           string,    //手机号
    "user_password":        string,    //密码
    "verification_code":    string     //参数增加手机验证码，为了防止越过短信验证而直接注册
}
```

**参数示例**
```
{
    "user_phone": "15989061915",
    "user_password": "123456",
    "verification_code": "4892"
}
```

**返回值**
```
{
    "code":       integer,    //状态码
    "message":    string,     //信息
    "data": {}                //数据，这里为空对象
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {}
}
```
- 400
```
    "code": 400,
    "message": "该手机号已经被注册"  //服务器发生错误（备选）
                                   //无效的手机号（备选）
```


## 完善或修改当前用户的信息
> `PUT /user/profile`

**参数**
```
{
    "user_icon":              string,    //头像，图片的byte数组转成字符串
    "student_name":           string,    //真实姓名
    "student_university":     string,    //学校
    "student_academy":        string,    //学院
    "student_number":         string,    //学号
    "student_gender":         integer    //性别，0为女，1为男
}
```

**参数示例**
```
{
    "user_icon": "dxba1at...",
    "student_name": "陈xx",
    "student_university": "中山大学",
    "student_academy": "数据科学与计算机学院",
    "student_number": "16340034",
    "student_gender": 1
}
```

**返回值**
```
{
    "code":       integer,    //状态码
    "message":    string,     //信息
    "data": {}                //数据，这里为空对象
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {}
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"  
```

* 401

```
    "code": 401,
    "message": "用户未登录"
```



## 获取当前用户的信息

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
    "code":                      integer,    //状态码
    "message":                   string,     //信息
    "data": {
        "user": {
            "user_id"                integer,    //用户id
            "user_phone":            string,     //手机号
            "user_icon":             string,     //头像，图片的byte数组转成字符串
            "user_balance":          integer,    //用户余额
            "user_fillln":           integer     //是否填写了个人信息，1为已经填写，0为未填写
        },
        "student": {
            "student_id":            integer,    //学生id         
            "user_id":               integer,    //学生对应的用户id
            "student_number":        string,     //学号
            "student_name":          string,     //真实姓名
            "student_university":    string,     //学校
            "student_academy":       string,     //学院
            "student_gender":        integer     //性别，0为女，1为男
        }
    }
}
```

**返回示例**
- 200
```
    "code": 200,
    "message": "OK,
    "data": {
        ...  //省略
    }
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```

## 用户密码登录

> `POST /user/password/session`

**参数**

```
{
    "user_phone":       string,    //手机号
    "user_password":    string     //密码
}
```

**参数示例**
```
{
    "user_phone": "15989061915",
    "user_password": "123456"
}
```

**返回值**

```
{
    "code":               integer,    //状态码
    "message":            string,     //信息
    "data": {
        "user_fillln":    integer     //用户是否完善了个人信息，0为否，1为是
    } 
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {
        "user_fillln": 0
    }
}
```
- 400
```
    "code": 400,
    "message": "用户名不存在"  //密码错误（备选）
                              //服务器发生错误（备选）
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 找回密码-重置密码

> `PUT /user/password`

**参数**
```
{
    "user_phone":           string,
    "user_password":        string,
    "verification_code":    string     //参数增加手机验证码，为了防止密码被他人修改而不是本人修改
}
```

**参数示例**
```
{
    "user_phone": "15989061915"
    "user_password": "123456"
    "verification_code": "5489"
}
```

**返回值**
```
{
    "code":       integer,    //状态码
    "message":    string,     //信息
    "data": {}                //数据，这里为空对象
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {}
}
```
- 400
```
    "code": 400,
    "message": "手机验证码错误"  //服务器发生错误（备选）
```


## 用户短信登录

> `POST /user/sms/session`

**参数**
```
{
    "user_phone":           string,    //手机号
    "verification_code":    string     //验证码
}
```

**参数示例**
```
{
    "user_phone": "15989061915",
    "verification_code": "1548"
}
```

**返回值**
```
{
    "code":               integer,    //状态码
    "message":            string,     //信息
    "data": {
        "user_fillln":    integer     //用户是否完善了个人信息，0为否，1为是
    }
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {
        "user_fillln": 0
    }
}
```
- 400
```
    "code": 400,
    "message": "手机验证码错误"  //服务器发生错误（备选）
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
    "code":       integer,    //状态码
    "message":    string,     //信息
    "data": {}                //数据，这里为空对象
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {}
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 获取当前用户的余额
> `GET /user/balance`

**参数**
```
无
```

**返回值**
```
{
    "code":                integer,    //状态码
    "message":             string,     //信息
    "data": {
        "user_balance":    integer     //用户闲余币
    }
}
```

**返回示例**

- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {
        "user_balance": 100
    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 获得当前用户发布/领取的所有任务id和共同属性

> `GET /user/tasks/{t_type}`

**参数**	

```
{
    把 url 中的 {t_type} 替换成integer类型的 0 或 1 ，0为用户发布的，1为用户领取的
}
```

**参数示例**
```
{
    GET /user/tasks/1
}
```

**返回值**

```
// 返回的结果按发布时间从大到小排序，即最新发布的任务存储在tasks数组前面

{
    "code":                            integer,    
    "message":                         string,
    "data": {
        "tasks": [
            {
                "task_id":             integer,    //任务id
                "user_id":             integer,    //发布者id
                "task_type":           integer,    //任务类型，0为拿快递和外卖，1为填问卷
                "task_sketch":         string,     //任务简述
                "task_bonus":          integer,    //任务酬劳
                "task_publishDate":    string      //发布日期
            }
        ]
    }
}
```

**返回示例**

- 200
```
{
    "code": 200,    
    "message": "OK",
    "data": {
        "tasks": [
            {
                //省略...
            }
        ]
    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```





## 根据用户/关注的人/粉丝id批量获取用户信息(user_id/following_id/fan_id都适用)

> `POST /user/batch/information`


**参数**

```
{
    "user_ids":  [
        {
            "user_id":    integer    //用户id
        }
    ]
}
```

**参数示例**
```
{
    "user_ids":  [
        {
            "user_id": 1
        },
        {
            "user_id": 2
        },
        {
            "user_id": 3
        }
    ]  
}
```

**返回值**

```
{
    "code":                                  integer,    //状态码
    "message":                               string,     //信息
    "data": {
        "users": [
            {
                "user": {
                    "user_id"                integer,    //用户id
                    "user_phone":            string,     //手机号
                    "user_icon":             string,     //头像，图片的byte数组转成字符串
                    "user_balance":          integer,    //用户余额
                    "user_fillln":           integer     //是否填写了个人信息
                },
                "student": {
                    "student_id":            integer,    //学生id      
                    "user_id":               integer,    //学生对应的用户id   
                    "student_number":        string,     //学号
                    "student_name":          string,     //真实姓名
                    "student_university":    string,     //学校
                    "student_academy":       string,     //学院
                    "student_gender":        integer     //性别，0为女，1为男
                }  
            }   
        ]
    }
}
```

**返回示例**

- 200

```
{
    "code": 200,
    "message": "OK",
    "data": {
        "users": [
            {
                //省略...
            }
        ]
    }
}
```

- 400

```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 当前用户关注其它用户

> `POST /user/following`

**参数**
```
{
    "user_id":    integer    //要关注的其他用户的id
}
```

**参数示例**
```
{
    "user_id": 1
}
```

**返回值**

```
{
    "code":       integer,    //状态码
    "message":    string,     //信息
    "data": {}                //数据，这里为空对象
}
```

**返回示例**

- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {}
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 当前用户取关其它用户

> `DELETE /user/following`

**参数**
```
{
    "user_id":    integer    //要取关的其他用户的id
}
```

**参数示例**
```
{
    "user_id": 1
}
```

**返回值**

```
{
    "code":       integer,    //状态码
    "message":    string,     //信息
    "data": {}                //数据，这里为空对象
}
```

**返回示例**

- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {}
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 获取当前用户关注的所有用户的id

> `GET /user/followings`

**参数**
```
无
```

**返回值**

```
{
    "code":                        integer,    //状态码
    "message":                     string,     //信息
    "data": {
        "followings": [
            {
                "following_id":    integer     //元素是当前用户关注的用户的id
            }
        ]
    }
}
```

**返回示例**

- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {
        "followings": [
            {
                "following_id": 5    
            }
            {
                "following_id": 12    
            }
            ...
        ]
    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 获取当前用户的所有粉丝的id 
> `GET /user/fans`

**参数**
```
无
```

**返回值**
```
{
    "code":                  integer,    //状态码
    "message":               string,     //信息
    "data": {
        "fans": [
            {
                "fan_id":    integer     //元素是用户的粉丝的id
            }
        ]
    }
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {
        "fans": [
            {
                "fan_id": 5    
            }
            {
                "fan_id": 12    
            }
            ...
        ]
    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```



# 任务

## 关于任务API（注意事项）

任务有两种类型：
- 一种是递送任务，包括拿快递和外卖
- 另一种是填写问卷

这两种任务的数据表的部分属性是不同的，而另一部分属性是相同的。

共同属性为：
```
{
    "user_id":             integer,    //发布者的id
    "task_type":           integer,    //任务类型，0拿快递和外卖，1为填问卷
    "task_sketch":         string,     //任务简述
    "task_bonus":          integer,    //酬劳
    "task_publishDate":    string      //发布日期
}
```
所以前端获取关于任务的信息时，必须先获取任务的共同属性，得到该任务的类型（递送任务或问卷任务），然后再根据递送任务或问卷任务的API获取特殊的信息。

## 获取任务大厅的所有任务id和共同属性
> `GET /task/{t_type}`
`已测试`
**参数**	

```
{
    把 url 中的 {t_type} 替换成integer类型的 0、1、2, 0为最新任务, 1关注的人发布的任务, 2为价格最高, 如下所示：

    GET /task/1
}
```

**返回值**

```
{
    "code":                             integer,    //状态码
    "message":                          string,     //信息
    "data": {
         tasks": [    
            {
                "task_id":              integer,    //任务ID(主键)
                "user_id":              integer,    //发布者id	
                "task_type":            string,     //任务类型，0为拿快递和外卖，1为问卷
                "task_sketch":          string,     //任务简介
                "task_bonus":           integer,    //悬赏金额
                "task_publishDate":     string      //发布时间，#格式为YYYY-MM-DD HH:MM:SS
            }
        ]   
    }
}
```

**返回示例**

- 200
```
{
    "code": 200,
    "message": "OK",
    "data":{
        tasks": [
            {
                //省略...
            }
        ]    
    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 根据任务id获取拿快递和外卖的详细信息

> `GET /task/delivery/detail/{task_id}`
`已测试`
**参数**	

```
{
    把 url 中的 {task_id} 替换成integer类型的任务id
}
```

**返回值**

```
{
    "code":                             integer,    //状态码
    "message":                          string,     //信息
    "data": {
  		"delivery": {
            "delivery_id":              integer,    //递送任务id
            "task_id":                  integer,    //递送任务对应的任务id
            "delivery_detail":          string,     //订单类型，0为拿快递和外卖，1为问卷
            "delivery_picked":          string,     //任务简介
            "delivery_complished":      integer,    //悬赏金额
            "delivery_complishDate"     string      //发布时间，#格式为YYYY-MM-DD HH:MM:SS
        }      
    }

}
```

**返回示例**

- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {
  		"delivery": {
            //省略...
        }
    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 根据任务id获取问卷和题目的详细信息

> `GET /task/questionnaire/detail/{task_id}`
`已测试`
**参数**	

```
{
    把 url 中的 {task_id} 替换成integer类型的任务id
}
```

**返回值**

```
{
    "code":                                     integer,    //状态码
    "message":                                  string,     //信息
    "data": {
    	"questionnaire": {
            "questionnaire_id":                 integer,    //问卷id
            "task_id":                          integer,    //问卷对应的任务id
            "questionnaire_closed":             integer,    //是否截止
            "questionnaire_deadline":           string,     //截止时间，#格式为YYYY-MM-DD HH:MM:SS
            "questions": [
                {
                    "question_id":              integer,    //题目id
                    "questionnaire_id":         integer,    //题目所属的问卷id
                    "question_description":     string,     //题目描述
                    "question_type":            integer,    //题目类型，0为单选，1为多选，2为填空题
                    "question_a":               string,     //选项A描述
                    "question_b":               string,     //选项B描述
                    "question_c":               string,     //选项C描述
                    "question_d":               string      //选项D描述
                }
            ]
        }     
    }  
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {
        //省略...
    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 接受一个跑腿的任务(前端需要判断任务是否是自己发布的, 是否有人领取了, 是否取消了)

> `POST /task/acceptance`
`已测试`
**参数**

```
{
    "task_id":    integer     //订单ID(主键)
}
```

**返回值**

```
{
    "code":       integer,    //状态码
    "message":    string,     //信息
    "data": {                 //空对象

    }
}
```

**返回示例**

- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {

    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```



## 完成拿快递和外卖的任务(平台把钱给领取者)

> `POST /task/delivery/complishment` 
`已测试`
**参数**

```
{
    "task_id":    integer     //订单ID(主键)
}
```

**返回值**

```
{
    "code":       integer,    //状态码
    "message":    string,     //信息
    "data": {                 //空对象

    }
}
```

**返回示例**

- 200

```
{
    "code": 200,
    "message": "OK",
    "data": {

    }
}
```

- 400

```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```





## 发布者取消拿快递和外卖的任务(钱退回给发布者)(前端需要保证只能取消未完成的任务)

> `DELETE /task/delivery/{task_id}` 
`已测试`
**参数**	

```
{
    把 url 中的 {task_id} 替换成integer类型的任务id
}
```

**返回值**

```
{
    "code":       integer,    //状态码
    "message":    string,     //信息
    "data":                   //空对象
}
```

**返回示例**

- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {

    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 新建一个拿快递和外卖的任务(发布者把钱寄存在平台上, 当任务完成, 平台将钱给完成者)
`已测试`
> `POST /task/delivery` 

**参数**

```
{
    "task": {
        "task_type":                integer,    //订单类型，0为拿快递和外卖，1为问卷
        "task_sketch":              string      //任务简述
        "task_bonus":               integer,    //悬赏金额
    }
    "delivery" {
        "delivery_detail":          string,     //递送任务详情
    }
}
```

**参数示例**

```
{
    "task": {
        "task_type":                0,
        "task_sketch":              "帮忙拿快递",
        "task_bonus":               1
    },
    "delivery": {
        "delivery_detail":          "菜鸟驿站5号柜包裹码xxxx-xxxx"
    }
}
```

**返回值**

```
{
    "code":       integer,    //状态码
    "message":    string      //信息
    "data": {                 //空对象

    }
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {

    }
}
```
- 400
```
    "code": 400,
    "message": "余额不足"
```

```
    "code": 400,
    "message": "服务器发生错误"
```
- 401

```
    "code": 401,
    "message": "用户未登录"
```

## 新建一个问卷任务(执行这个操作, 发布者会先把钱给平台)
`已测试`
> `POST /task/questionnaire` 

**参数**

```
{
    "task": {
        "task_type":                       string,     //订单类型，0为拿快递和外卖，1为问卷
        "task_sketch":                     string      //任务简述
        "task_bonus":                      integer,    //悬赏金额
    },
    "questionnaire": {
        "questionnaire_number":			   integer,	   //打算发布的问卷份数(task_bonus * questionnaire_number = 总金额)
        "questions": [
            {
                "question_description":    string,     //题目描述
                "question_type":           integer,    //题目类型，0为单选，1为多选，2为填空题
                "question_a":              string,     //选项A描述
                "question_b":              string,     //选项B描述
                "question_c":              string,     //选项C描述
                "question_d":              string      //选项D描述
            }
        ]
    }   
}
```

**参数示例**

```
{
    "task": {
        "task_type":                1,
        "task_sketch":              "大学生运动爱好调查",
        "task_bonus":               1 
    },
    "questionnaire": {
        "questionnaire_number":			   2,	 
        "questions": [
            {
                "question_description":    "你的姓名",
                "question_type":           2,
                "question_a":              "",
                "question_b":              "",
                "question_c":              "",
                "question_d":              ""
            },
            {
                "question_description":    "你喜欢什么运动?",
                "question_type":           1,
                "question_a":              "篮球",     
                "question_b":              "羽毛球",    
                "question_c":              "乒乓球",    
                "question_d":              "排球"     
            }
        ]
    }
}
```

**返回值**

```
{
    "code":       integer,    //状态码
    "message":    string      //信息
    "data": {                 //空对象

    }
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {

    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```
- 401

```
    "code": 401,
    "message": "用户未登录"
```

## 填写者提交问卷的答案(前端需要保证只填写未截止的问卷)

> `POST /task/questionnaire/answer` 
`已测试`
**参数**

```
{
    "questionnaire_id":    integer,    //问卷id
    "answers": [
        {
            "question_id":    integer,    //题目id
            "answer_content":    string    //答案，单选示例"A",多选示例"ABD",填空示例"watchcat2k"
        }
    ]
}
```

**参数示例**

```
{
    "questionnaire_id":    1,
    "answers": [
        {
            "question_id":    1,
            "answer_content": "CoderUtil"
        },
        {
            "question_id":    2,
            "answer_content": "AB"
        }
    ]
}
```

**返回值**

```
{
    "code":       integer,    //状态码
    "message":    string      //信息
    "data": {                 //空对象

    }
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {

    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```
- 401

```
    "code": 401,
    "message": "用户未登录"
```

## 填写者获取自己填写过的答卷(包含题目和答案)

> `GET /task/questionnaire/answerSheet/{questionnaire_id}` 
`已测试`
**参数**	

```
{
    把 url 中的 {questionnaire_id} 替换成integer类型的问卷id
}
```

**返回值**

```
{
    "code":                                integer,    //状态码
    "message":                             string      //信息
    "data": {
    	"answerSheet": [
            {
                "question": {
                    "question_id":             integer,    //题目id
                    "questionnaire_id":        integer,    //问卷id
                    "question_description":    string,     //问题描述
                    "question_type":           integer,    //问题类型,0为单选，1为多选，2为填空
                    "question_a":              string,     //选项a的描述
                    "question_b":              string,
                    "question_c":              string,
                    "question_d":              string,
                },
                "answer": {
                    "answer_id":               integer,    //答案id
                    "answerSheet_id":          integer,    //答卷id
                    "question_id":             integer,    //问题id
                    "answer_content":          string      //答案，单选示例"A",多选示例"ABD",填空示例"watchcat2k"
                }
            }
        ]     
    }  
}
```

**返回示例**

- 200
```
{
    "code": 200,
    "message": "OK"
    "data": {
        ...
    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```
- 401

```
    "code": 401,
    "message": "用户未登录"
```

## 发布者查看问卷的统计信息

> `GET /task/questionnaire/Statistics/{questionnaire_id}` 
`已测试`
**参数**

```
{
    把 url 中的 {questionnaire_id} 替换成integer类型的问卷id
}
```

**返回值**

```
{
    "code":                                     integer,    //状态码
    "message":                                  string      //信息
    "data": {
     	"statistics": [
            {
                question: {
                    "question_id":                  integer,    //题目id
                    "questionnaire_id":             integer,    //问卷id
                    "question_description":         string,     //问题描述
                    "question_type":                integer,    //问题类型,0为单选，1为多选，2为填空
                    "question_a":                   string,     //选项a的描述
                    "question_b":                   string,
                    "question_c":                   string,
                    "question_d":                   string,
                }
                "answer": {
                    "answer_id":                  	integer,    //答案id
                    "answer_a_count":               integer,    //选A的数量
                    "answer_b_count":               integer,  
                    "answer_c_count":               integer,  
                    "answer_d_count":               integer,    
                    "answer_gap_filling" [
                        {
                            gap_filling_content:    string    //填空题答案
                        }
                    ]
                }
            }
        ]     
    }
}
```

**返回示例**

- 200
```
{
    "code": 200,
    "message": "OK"
    "data": {
        ...
    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```
- 401

```
    "code": 401,
    "message": "用户未登录"
```


## 发布者截止问卷

> `PUT /task/questionnaire/closure` 
`已测试`
**参数**

```
{
    "questionnaire_id":    integer,    //问卷id
}
```

**返回值**

```
{
    "code":       integer,    //状态码
    "message":    string      //信息
    "data": {                 //空对象

    }
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {
        
    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```
- 401

```
    "code": 401,
    "message": "用户未登录"
```


# 账单


## 获取当前用户的交易历史

> `GET /bill`
`已测试`
**参数**

```
无
```

**返回值**

```
{
    "code":                         integer,    //状态码
    "message":                      string,     //信息
    "data": {
     	"bills": [
            {
                "bill_id":              integer,    //账单id
                "user_id":              integer,    //账单所属用户id
                "bill_type":            integer,    //0为收入，1为支出
                "bill_number":          integer,    //账单金额
                "bill_description":     string,     //账单描述
                "bill_time":            string,     //账单时间
            }
        ]   
    }
}
```

**返回示例**
- 200
```
{
    "code": 200,
    "message": "OK",
    "data": {
         //省略...
    }
}
```
- 400
```
    "code": 400,
    "message": "服务器发生错误"
```

- 401

```
    "code": 401,
    "message": "用户未登录"
```



## 当前用户的闲余币充值

> `暂未开放`


