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
|  task_id   |      否      |  Number  |   任务的id   |



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
|  task_id   |      是      |  Number  |      任务的id      |
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
|    total     |  Number  |              |               元宝总数               |
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



# 十：完成计划接口

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



# 十一：获取工时表信息接口

## 1.接口说明

### 1.1接口描述

未完成接口

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_timesheet_list |
| ------------- | -------------------------------------------- |
| 格式          | JSON                                         |
| https请求方式 | POST                                         |
| 编码类型      | UTF-8                                        |

### 2.2url参数说明



|  **参数**   | **是否必填** | **类型** |   **描述**   |
| :---------: | :----------: | :------: | :----------: |
|   openid    |      是      |  Number  | 微信的openid |
| project_id  |      否      |  Number  |   项目的id   |
| search_date |      否      |   Date   |  搜寻的日期  |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_timesheet_list?openid=A1231D34&project_id=3&search_date=‘2010-10-11’
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** |  **描述**  |
| :----------: | :------: | :----------: | :--------: |
|     code     |  String  |              |  返回编码  |
|   message    |  string  |              |  返回信息  |
|     data     |   List   |              | 工时表信息 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"获取信息成功!"，
‘data’:[.....]
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "获取信息失败!"
} 
```



# 十二：发布日报接口

## 1.接口说明

### 1.1接口描述

发布日报接口

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/publish_daily |
| ------------- | --------------------------------------- |
| 格式          | JSON                                    |
| https请求方式 | POST                                    |
| 编码类型      | UTF-8                                   |

### 2.2url参数说明



|   **参数**    | **是否必填** | **类型** |   **描述**   |
| :-----------: | :----------: | :------: | :----------: |
|    openid     |      是      |  Number  | 微信的openid |
| time_sheet_id |      否      |  Number  |  工时表的id  |
|     memo      |      否      |   Text   |     总结     |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/publish_daily?openid=A1231D34&time_sheet_id=3
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
'message':"发布日报成功!"
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "发布日报失败!"
} 
```



# 十三：返回日报列表接口

## 1.接口说明

### 1.1接口描述

返回日报列表接口

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_daily_list |
| ------------- | ---------------------------------------- |
| 格式          | JSON                                     |
| https请求方式 | POST                                     |
| 编码类型      | UTF-8                                    |

### 2.2url参数说明



| **参数**  | **是否必填** | **类型** |   **描述**   |
| :-------: | :----------: | :------: | :----------: |
|  openid   |      是      |  Number  | 微信的openid |
| this_date |      否      |   Date   |   搜寻日期   |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_daily_list?openid=A1231D34&this_date=‘2020-10-12’
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** | **描述** |
| :----------: | :------: | :----------: | :------: |
|     code     |  String  |              | 返回编码 |
|   message    |  string  |              | 返回信息 |
|     data     |   List   |              | 返回数据 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"获取信息成功!"
‘date’:[
		{
		 'image':13123131A2310,
		 'name':张三,
		 'date':[
		 			{'title':'不回家啊谁都不会的能看出你考虑',
		            'content':'阿萨德鸡巴单据你确定秒企鹅的恐怕确定我皮卡丘的看破'}，
		            {'title':'不回家啊谁都不会的能看出你考虑',
		            'content':'阿萨德鸡巴单据你确定秒企鹅的恐怕确定我皮卡丘的看破'}，
		            {'title':'不回家啊谁都不会的能看出你考虑',
		            'content':'阿萨德鸡巴单据你确定秒企鹅的恐怕确定我皮卡丘的看破'}，
		            {'title':'不回家啊谁都不会的能看出你考虑',
		            'content':'阿萨德鸡巴单据你确定秒企鹅的恐怕确定我皮卡丘的看破'}，
		          ]
		 }
		]
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "发布日报失败!"
} 
```



# 十四：返回未读日报消息总数

## 1.接口说明

### 1.1接口描述

返回未读日报消息总数

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_unread_total |
| ------------- | ------------------------------------------ |
| 格式          | JSON                                       |
| https请求方式 | POST                                       |
| 编码类型      | UTF-8                                      |

### 2.2url参数说明



| **参数** | **是否必填** | **类型** |   **描述**   |
| :------: | :----------: | :------: | :----------: |
|  openid  |      是      |  Number  | 微信的openid |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_unread_total?openid=A1231D34 
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** |      **描述**       |
| :----------: | :------: | :----------: | :-----------------: |
|     code     |  String  |              |      返回编码       |
|   message    |  string  |              |      返回信息       |
|     data     |   List   |              | id集合[1,23,4,2,12] |
|    total     |  Number  |              |        总数         |
|     type     |  String  |              |        类型         |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"成功!",
‘data’:[1,2,3,4,5,6],
'total':5,
'type':'ribao'
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "失败!"
} 
```



# 十五：日报消息的详细列表

## 1.接口说明

### 1.1接口描述

返回日报消息详细列表

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/read_ribao_message |
| ------------- | -------------------------------------------- |
| 格式          | JSON                                         |
| https请求方式 | POST                                         |
| 编码类型      | UTF-8                                        |

### 2.2url参数说明



| **参数** | **是否必填** | **类型** |   **描述**   |
| :------: | :----------: | :------: | :----------: |
|  openid  |      是      |  Number  | 微信的openid |
|   data   |      是      |   List   |   id的list   |
|   type   |      是      |  String  |     类型     |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/read_ribao_message?openid=A1231D34&data=[1,2,3,4,5,6]&type='ribao'
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** | **描述** |
| :----------: | :------: | :----------: | :------: |
|     code     |  String  |              | 返回编码 |
|   message    |  string  |              | 返回信息 |
|     data     |   List   |              | 数据集合 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"成功!",
‘data’:[1,2,3,4,5,6],
'total':5,
'type':'ribao'
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "失败!"
} 
```



# 十六：系统消息总数

## 1.接口说明

### 1.1接口描述

系统消息总数接口

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_system_total |
| ------------- | ------------------------------------------ |
| 格式          | JSON                                       |
| https请求方式 | POST                                       |
| 编码类型      | UTF-8                                      |

### 2.2url参数说明



| **参数** | **是否必填** | **类型** |   **描述**   |
| :------: | :----------: | :------: | :----------: |
|  openid  |      是      |  Number  | 微信的openid |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/read_ribao_message?openid=A1231D34&data=[1,2,3,4,5,6]&type='ribao'
```



### 3.4返回参数说明

|  **参数说明**  | **类型** | **参数路径** | **描述** |
| :------------: | :------: | :----------: | :------: |
|      code      |  String  |              | 返回编码 |
|    message     |  string  |              | 返回信息 |
| remind_message |  String  |              | 提示信息 |
|     total      |  Number  |              |   总数   |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"获取信息成功!",
‘remind_message’:‘今天的日报还没发送哦’,
'total':5,
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "获取信息失败!"
} 
```



# 十七：获取自己工时 

## 1.接口说明

### 1.1接口描述

获取自己工时，如果日期没传就默认是今天。

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_my_day_timesheet |
| ------------- | ---------------------------------------------- |
| 格式          | JSON                                           |
| https请求方式 | POST                                           |
| 编码类型      | UTF-8                                          |

### 2.2url参数说明



|  **参数**   | **是否必填** | **类型** |   **描述**   |
| :---------: | :----------: | :------: | :----------: |
|   openid    |      是      |  Number  | 微信的openid |
| search_date |      否      |   Date   |   查询日期   |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_my_day_timesheet?openid=A1231D34&search_date=’2015-10-12‘
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** | **描述** |
| :----------: | :------: | :----------: | :------: |
|     code     |  String  |              | 返回编码 |
|   message    |  string  |              | 返回信息 |
|     data     |   List   |              | 数据列表 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"获取信息成功!",
‘data’:[
		{'fill_time':12,
		'memo':'w撒大大',
		'title':'这个是标题',
		'project_id':2,
		'project_name':'金山太阳能你',
		'employee_name':'张三丰',
		'employee_image':'d12easd1-213asd1231'},
		
		{'fill_time':11,
		'memo':'sdasda',
		'title':'adasd',
		'project_id':2,
		'project_name':'asd',
		'employee_name':'asd',
		'employee_image':'asdasdaadad31'},
	   ],
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "获取信息失败!"
} 
```



# 十八：获取计划详情接口

## 1.接口说明

### 1.1接口描述

获取计划详情的接口

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_grow_plan_detail |
| ------------- | ---------------------------------------------- |
| 格式          | JSON                                           |
| https请求方式 | POST                                           |
| 编码类型      | UTF-8                                          |

### 2.2url参数说明



| **参数** | **是否必填** | **类型** |   **描述**   |
| :------: | :----------: | :------: | :----------: |
|  openid  |      是      |  Number  | 微信的openid |
| plan_id  |      是      |  Number  |   计划的id   |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_grow_plan_detail?openid=A1231D34&plan_id=26
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** | **描述** |
| :----------: | :------: | :----------: | :------: |
|     code     |  String  |              | 返回编码 |
|   message    |  string  |              | 返回信息 |
|     data     |   List   |              | 数据列表 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"查询信息成功!",
‘data’:{
		‘project_name’:'我是尼玛偶像',
		‘project_id’:'项目的id',
		‘title’:'dasda',
		'plan_begin_date':2020-10-11,
		'plan_end_date':2020-10-11,
		'cc':['乔峰','段誉','张海'],
		'content':'adasdasdasd',
		'm_plan':True,
		'executor':['乔峰','段誉','张海']
	}
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



# 十九：开始评论接口

## 1.接口说明

### 1.1接口描述

开始评论接口

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/begin_comment |
| ------------- | --------------------------------------- |
| 格式          | JSON                                    |
| https请求方式 | POST                                    |
| 编码类型      | UTF-8                                   |

### 2.2url参数说明



|  **参数**   | **是否必填** | **类型** |   **描述**   |
| :---------: | :----------: | :------: | :----------: |
|   openid    |      是      |  Number  | 微信的openid |
|    date     |      是      |   Date   |     日期     |
| employee_id |      是      |  Number  |   员工的id   |
| project_id  |      是      |  Number  |   项目的id   |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/begin_comment?date='2020-12-13'&employee_id=26&project_id=2
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** | **描述** |
| :----------: | :------: | :----------: | :------: |
|     code     |  String  |              | 返回编码 |
|   message    |  string  |              | 返回信息 |
|     date     |   Date   |              | 日期格式 |
|  project_id  |  Number  |              | 项目的id |
| employee_id  |  Number  |              | 员工的id |
|     data     |   List   |              | 数据列表 |
|   comment    |  String  |              | 评论内容 |
|    total     |  Number  |              |   星级   |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"获取信息成功!",
‘data’:{
		‘project_name’:'我是尼玛偶像',
		‘project_id’:'项目的id',
		‘title’:'dasda',
		'plan_begin_date':2020-10-11,
		'plan_end_date':2020-10-11,
		'cc':['乔峰','段誉','张海'],
		'content':'adasdasdasd',
		'm_plan':True,
		'executor':['乔峰','段誉','张海']
	}
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



# 二十：评论完成

## 1.接口说明

### 1.1接口描述

评论完成

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/done_comment |
| ------------- | -------------------------------------- |
| 格式          | JSON                                   |
| https请求方式 | POST                                   |
| 编码类型      | UTF-8                                  |

### 2.2url参数说明



|  **参数**   | **是否必填** | **类型** |   **描述**   |
| :---------: | :----------: | :------: | :----------: |
|   openid    |      是      |  Number  | 微信的openid |
|    date     |      是      |   Date   |     日期     |
| employee_id |      是      |  Number  |   员工的id   |
| project_id  |      是      |  Number  |   项目的id   |
|    memo     |      是      |   Text   |  评论的内容  |
|    total    |      是      |  Number  |    星级数    |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/done_comment?date='2020-12-13'&employee_id=26&project_id=2&memo="不知道写什么评论"&total=2
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
'message':"评论成功!",
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "评论失败!"
} 
```



# 二十一：近期任务

## 1.接口说明

### 1.1接口描述

近期任务接口

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/get_new_three_task |
| ------------- | -------------------------------------------- |
| 格式          | JSON                                         |
| https请求方式 | POST                                         |
| 编码类型      | UTF-8                                        |

### 2.2url参数说明



| **参数** | **是否必填** | **类型** |   **描述**   |
| :------: | :----------: | :------: | :----------: |
|  openid  |      是      |  Number  | 微信的openid |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/get_new_three_task?openid=123123A123
```



### 3.4返回参数说明

| **参数说明** | **类型** | **参数路径** | **描述** |
| :----------: | :------: | :----------: | :------: |
|     code     |  String  |              | 返回编码 |
|   message    |  string  |              | 返回信息 |
|     data     |   List   |              | 任务数据 |
|    phone     |  String  |              | 电话号码 |

### 3.5正确返回示例

JSON示例: 

```
application/json;charset=UTF-8
{
‘code':1001,
'message':"获取信息成功!",
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "获取信息失败!"
} 
```



# 二十二：删除评论

## 1.接口说明

### 1.1接口描述

删除评论接口

## 2.接口调用说明

### 2.1请求说明

| url           | http://v12grow.qitong.xin/delete_comment |
| ------------- | ---------------------------------------- |
| 格式          | JSON                                     |
| https请求方式 | POST                                     |
| 编码类型      | UTF-8                                    |

### 2.2url参数说明



|  **参数**  | **是否必填** | **类型** |   **描述**   |
| :--------: | :----------: | :------: | :----------: |
|   openid   |      是      |  Number  | 微信的openid |
| comment_id |      是      |  Number  |   评论的id   |



### 3.3请求示例

```
POST http://v12grow.qitong.xin/delete_comment?openid=123123A123&comment_id=2
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
'message':"删除成功!",
}
```

### 3.6错误返回示例

JSON示例: 

```
{
	"code" : "1002",
	"message" : "删除失败!"
} 
```

