# 一.绑定openid

## 1.接口说明

### 1.1接口描述

   根据手机号码和微信的openid进行后端绑定

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/openid_bind |
| ------------- | ------------------------------------- |
| 格式          | JSON                                  |
| https请求方式 | POST                                  |
| 编码类型      | UTF-8                                 |

### 2.2url参数说明



| **参数** | **是否必填** | **类型** |   **描述**   |
| :------: | :----------: | :------: | :----------: |
|  mobile  |      是      |  string  |   手机号码   |
|  openid  |      是      |  string  | 微信的openid |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/openid_bind?mobile=18516393654&openid=A1231D34
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** |                  **描述**                  |
| :----------: | :------: | :----------: | :----------------------------------------: |
|     code     |  string  |              | 1001绑定未成功,1002绑定成功,1003换绑成功。 |
|   message    |  string  |              |                  返回信息                  |
|     data     |  string  |              |                 员工的信息                 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
	"code":1002,
	"message":"恭喜您绑定成功",
	"data":{
		"identity":1,
		"job":"养猫专业户"
	}
}
```



### 3.6错误返回示例

```
application/json;charset=UTF-8
{
	"errcode" : "1001",
	"errmsg" : "亲，该手机号码暂未在系统后台维护，请联系管理员协助解决!"
} 
```



# 二：获取openid

## 1.接口说明

### 1.1接口描述

   根据js_code获取微信的openid 

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_openid |
| ------------- | ------------------------------------ |
| 格式          | JSON                                 |
| https请求方式 | POST                                 |
| 编码类型      | UTF-8                                |

### 2.2url参数说明

| **参数** | **是否必填** | **类型** | **描述** |
| :------: | :----------: | :------: | :------: |
| js_code  |      是      |  string  | js_code  |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_openid?js_code=A1231D34
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** |   **描述**   |
| :----------: | :------: | :----------: | :----------: |
|    openid    |  string  |              | 微信的openid |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
	"openid":"12312Asa123",
}
```



# 三：获取相关项目列表 (点击我的项目)

## 1.接口说明

### 1.1接口描述

  点击我的项目获取项目列表

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_project |
| ------------- | ------------------------------------- |
| 格式          | JSON                                  |
| https请求方式 | POST                                  |
| 编码类型      | UTF-8                                 |

### 2.2url参数说明



|   **参数**   | **是否必填** | **类型** |     **描述**     |
| :----------: | :----------: | :------: | :--------------: |
| project_name |      是      |  string  | 项目名称可以为空 |
|    openid    |      是      |  string  |   微信的openid   |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_project?project_name='金山'&openid=A1231D34
```



### 3.4返回参数说明

|  **参数说明**  | **类型** | **参数路径** |             **描述**             |
| :------------: | :------: | :----------: | :------------------------------: |
|   project_id   |  Number  |              |             项目的id             |
|  project_name  |  string  |              |             项目名称             |
| difference_day |  Number  |              |            相差的天数            |
|     status     |  Number  |              | 是否已经完成，完成是1，未完成是0 |
|    percent     |  string  |              |              百分比              |
|  create_date   |   Date   |              |             创建时间             |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
[
{
"project_id":2,
"project_name":"金山太阳能",
"difference_day":15,
"create_date":'2015-10-16',
"status":0,
"percent":21%
},
{
"project_id":21,
"project_name":"沃农供应链",
"difference_day":18,
"create_date":'2015-10-16',
"status":1,
"percent":15%
},
{
"project_id":32,
"project_name":"星贝达化工",
"difference_day":18,
"create_date":'2015-10-16',
"status":1,
"percent":28%
}
]
```



# 四：获取任务

## 1.接口说明

### 1.1接口描述

  获取任务信息

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_task |
| ------------- | ---------------------------------- |
| 格式          | JSON                               |
| https请求方式 | POST                               |
| 编码类型      | UTF-8                              |

### 2.2url参数说明



|  **参数**  | **是否必填** | **类型** |   **描述**   |
| :--------: | :----------: | :------: | :----------: |
| project_id |      是      |  Numebr  |   项目的id   |
|   openid   |      是      |  string  | 微信的openid |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_task?project_id=25&openid=A1231D34
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** |             **描述**             |
| :----------: | :------: | :----------: | :------------------------------: |
|     code     |  String  |              |             返回编码             |
|   message    |  string  |              |             返回信息             |
|  task_name   |  string  |              |             任务名称             |
|   task_id    |  Number  |              |              任务id              |
|    state     |  string  |              | 是否已经完成，完成是1，未完成是0 |
|   end_date   |   Date   |              |           项目完成日期           |
|  followers   |   List   |              |            抄送人列表            |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"获取信息成功!",
'data':
    [
        {
        'task_name':'任务的名称',
        'task_id':13,
        'state':1,
        'end_date':'2020-12-01',
        'followers':['张三','李四','王五']
        },
        {
        .......
        },
    ]
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "获取失败!"
	"data"：[]
} 
```



# 五：填写工时单

## 1.接口说明

### 1.1接口描述

  填写工时单

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/fill_timesheet |
| ------------- | ---------------------------------------- |
| 格式          | JSON                                     |
| https请求方式 | POST                                     |
| 编码类型      | UTF-8                                    |

### 2.2url参数说明



|  **参数**  | **是否必填** | **类型** |      **描述**      |
| :--------: | :----------: | :------: | :----------------: |
| project_id |      是      |  Numebr  |      项目的id      |
|   openid   |      是      |  Number  |    微信的openid    |
| fill_time  |      是      |  String  | 战斗时长，类似8:30 |
|    memo    |      是      |   Text   |        总结        |
|   title    |      是      |  string  |        标题        |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/fill_timesheet?project_id=25&openid=A1231D34&fill_time=8:30&memo="我是总结"&title="标题,,,,"
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** | **描述** |
| :----------: | :------: | :----------: | :------: |
|     code     |  String  |              | 返回编码 |
|   message    |  string  |              | 返回信息 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"插入信息成功!",
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "插入信息失败!"
} 
```



# 六：获取本周的总计工时

## 1.接口说明

### 1.1接口描述

  获取本周的总计工时

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_this_week_timesheet |
| ------------- | ------------------------------------------------- |
| 格式          | JSON                                              |
| https请求方式 | POST                                              |
| 编码类型      | UTF-8                                             |

### 2.2url参数说明



| **参数** | **是否必填** | **类型** |   **描述**   |
| :------: | :----------: | :------: | :----------: |
|  openid  |      是      |  Number  | 微信的openid |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_this_week_timesheet?openid=A1231D34
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** |               **描述**               |
| :----------: | :------: | :----------: | :----------------------------------: |
|     code     |  String  |              |               返回编码               |
|   message    |  string  |              |               返回信息               |
|  total_hour  |  String  |              |                总工时                |
|     days     |   List   |              | ['07','08','09','10','11','12','13'] |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"获取信息成功!",
‘total_hour’:'25h',
'days':['07','08','09','10','11','12','13']
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "获取信息失败!"
	“total_hour”:'0h'
} 
```



# 七：获取人员列表的接口

## 1.接口说明

### 1.1接口描述

  获取人员列表的接口

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_hr_employee_list |
| ------------- | ---------------------------------------------- |
| 格式          | JSON                                           |
| https请求方式 | POST                                           |
| 编码类型      | UTF-8                                          |

### 2.2url参数说明



| **参数** | **是否必填** | **类型** |   **描述**   |
| :------: | :----------: | :------: | :----------: |
|  openid  |      是      |  Number  | 微信的openid |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_hr_employee_list?openid=A1231D34
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** | **描述** |
| :----------: | :------: | :----------: | :------: |
|     code     |  String  |              | 返回编码 |
|   message    |  string  |              | 返回信息 |
|  employees   |   List   |              | 员工列表 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"获取信息成功!",
‘employees’:[
            {'id':15,'name':李逵,'image':sadadaadadad},
            {'id':16,'name':刘备,'image':sadadaadadad},
            {'id':17,'name':刘美,'image':sadadaadadad}
            ]
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "获取信息失败!"
	“employees”:'0h'
} 
```



# 八：创建grow计划接口

## 1.接口说明

### 1.1接口描述

 创建grow计划

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/create_grow_plan |
| ------------- | ------------------------------------------ |
| 格式          | JSON                                       |
| https请求方式 | POST                                       |
| 编码类型      | UTF-8                                      |

### 2.2url参数说明



|    **参数**     | **是否必填** | **类型** |    **描述**    |
| :-------------: | :----------: | :------: | :------------: |
|     openid      |      是      |  Number  |  微信的openid  |
|    plan_name    |      是      |  String  |    计划名称    |
|   project_id    |      是      |  Number  |    项目的id    |
| plan_begin_date |      是      |   Date   |  计划开始时间  |
|  plan_end_date  |      是      |   Date   |  计划结束时间  |
|       cc        |      是      |   List   |     抄送人     |
|     content     |      是      |   TXT    |    计划内容    |
|     m_plan      |      否      |  Number  | 是否是多人计划 |
|    executor     |      否      |  Number  |     执行人     |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/create_grow_plan?openid=A1231D34&plan_name=.......
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** | **描述** |
| :----------: | :------: | :----------: | :------: |
|     code     |  String  |              | 返回编码 |
|   message    |  string  |              | 返回信息 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"创建计划成功!"
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "创建计划失败!"
} 
```



# 九：返回未完成计划接口

## 1.接口说明

### 1.1接口描述

未完成接口

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_not_done_grow_plan_list |
| ------------- | ----------------------------------------------------- |
| 格式          | JSON                                                  |
| https请求方式 | POST                                                  |
| 编码类型      | UTF-8                                                 |

### 2.2url参数说明



| **参数** | **是否必填** | **类型** |   **描述**   |
| :------: | :----------: | :------: | :----------: |
|  openid  |      是      |  Number  | 微信的openid |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_not_done_grow_plan_list?openid=A1231D34
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** | **描述** |
| :----------: | :------: | :----------: | :------: |
|     code     |  String  |              | 返回编码 |
|   message    |  string  |              | 返回信息 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"查询信息成功!"
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "查询信息失败!"
} 
```



# 十：计划完成接口

## 1.接口说明

### 1.1接口描述

未完成接口

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/done_plan |
| ------------- | ----------------------------------- |
| 格式          | JSON                                |
| https请求方式 | POST                                |
| 编码类型      | UTF-8                               |

### 2.2url参数说明



| **参数** | **是否必填** | **类型** |   **描述**   |
| :------: | :----------: | :------: | :----------: |
|  openid  |      是      |  Number  | 微信的openid |
| plan_id  |      是      |  Number  |   计划的id   |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/done_plan?openid=A1231D34&plan_id=3
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** | **描述** |
| :----------: | :------: | :----------: | :------: |
|     code     |  String  |              | 返回编码 |
|   message    |  string  |              | 返回信息 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"完成计划成功!"
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "完成计划失败!"
} 
```

