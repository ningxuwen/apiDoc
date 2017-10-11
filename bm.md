
## melodyx后台接口文档

### 版本
版本        | 修改日期		| 修改人  | 修改记录
:---------- |:-------------|:-----|:--------
1.0.0    | 20171009 | 宁旭温 | 创建文档

### 系统错误码
|错误码 | 描述 |
:--------|:-------|
-1 | 系统异常|
200 | 操作成功|
201 | 操作失败|

### 所有接口返回格式
* （正确）{"code": 200,"description": "","detail": {}}
* （错误）{"code": xxxxxx,"description": "xxxxxx","detail": null}

### 接口描述

#### 登录
* [1、登录接口](#1-1) 
* [2、退出](#1-2) 
* [3、是否登录](#1-3)

#### 学校管理
* [1、学校列表](#2-1) 
* [2、添加学校](#2-2) 
* [3、删除学校](#2-3) 
* [3、修改学校](#2-4) 

#### 教师管理
* [1、教师列表](#3-1) 
* [2、添加教师](#3-2) 


### 接口详情

<h3 id="1-1">1.登录接口</h3>

#### 接口名字
* /login.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* userName* ：教师账号
* password* ：教师密码

#### 接口正确返回
````
    {
        "code": 200,
        "description": "请求成功",
        "detail": {
        "createTime":"2017-01-11 20:27:06",
        "id":null,
        "loginIp":null,
        "loginTime":"2017-07-24 17:00:46",
        "status":0,
        "userName":"admin",
        "userPassword":null
        }
    }
````

#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100200004 | 用户名不能为空
100200005 | 密码不能为空
100200006 | 用户名或者密码错误

<h3 id="1-2">2.退出</h3>

#### 接口名字
* /logout.json

#### 接口请求方式
* POST/GET

#### 接口请求参数
无

#### 接口返回结果：
* 正确返回：
```
     {
        code: 200,
        description: "操作成功",
        detail: null
    }
```
* 错误返回：
```
```

#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="1-3">3.是否登录</h3>

#### 接口名字
* /isLogin.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
无

#### 接口正确返回
````
    {
        "code": 200,
        "description": "请求成功",
        "detail": null
    }
````

#### 接口错误码
错误码 | 说明 |
|:-----|:-----
10020 | 用户未登录

<h3 id="2-1">4.学校列表</h3>

#### 接口名字
* /school/schoolList.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* pageNo ：页码

#### 接口正确返回
````
    {
        "code": 200,
        "description": "",
        "detail": {
            "nextPage": 2,
            "pageNo": 1,
            "pageSize": 10,
            "prePage": 1,
            "rows": [
                {
                    "amCourse": null,
                    "courseId": 6,
                    "courseName": "幼儿园",
                    "createTime": null,
                    "endTime": "2018-09-13",
                    "id": 512,
                    "name": "天使音乐",
                    "startTime": "2017-09-13",
                    "status": 0,
                    "validateDay": 0
                },
                {
                    "amCourse": null,
                    "courseId": 6,
                    "courseName": "幼儿园",
                    "createTime": null,
                    "endTime": "2018-09-13",
                    "id": 511,
                    "name": "天使音乐",
                    "startTime": "2017-09-13",
                    "status": 0,
                    "validateDay": 0
                }
            ],
            "totalCount": 298
        }
    }
````

#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="2-2">5.添加学校</h3>

#### 接口名字
* /school/addSchool.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* schoolName*：学校名
* courseType*：课程类型
* startTime*：开始时间（格式：2017-02-01）
* endTime*：结束时间（格式：2017-02-01）

#### 接口正确返回
````
    {
        "code": 200,
        "description": "",
        "detail":null
    }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100200007 | 学校参数异常

<h3 id="2-3">6.删除学校</h3>

#### 接口名字
* /school/delSchool.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* sid*：学校id

#### 接口正确返回
````
    {
        "code": 200,
        "description": "",
        "detail":null
    }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="2-4">7.修改学校</h3>

#### 接口名字
* /school/modifySchool.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* sid*：学校id
* schoolName*：学校名
* courseType*：课程类型
* startTime*：开始时间（格式：2017-02-01）
* endTime*：结束时间（格式：2017-02-01）

#### 接口正确返回
````
    {
        "code": 200,
        "description": "",
        "detail":null
    }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
201 | 操作失败

<h3 id="3-1">8.教师列表</h3>

#### 接口名字
* /teacher/findAllTeachers.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* sid ：学校id
* state：状态（1正常 2删除）
* pageNo：页码
#### 接口正确返回
````
    {
        "code": 200,
        "description": "请求成功",
        "detail": {
            "nextPage": 2,
            "pageNo": 1,
            "pageSize": 10,
            "prePage": 1,
            "rows": [
                {
                    "address": "12",
                    "age": 12,
                    "classIds": null,
                    "classList": null,
                    "classStr": null,
                    "createTime": null,
                    "gender": 1,
                    "graduated": "北京",
                    "id": 195,
                    "level": 1,
                    "name": "李老师",
                    "phone": "13600000001",
                    "school": null,
                    "schoolId": 292,
                    "state": 1,
                    "teachTime": 12
                },
                {
                    "address": "北京",
                    "age": 22,
                    "classIds": null,
                    "classList": null,
                    "classStr": null,
                    "createTime": null,
                    "gender": 1,
                    "graduated": "北京",
                    "id": 194,
                    "level": 1,
                    "name": "姚老师",
                    "phone": "10635007001",
                    "school": null,
                    "schoolId": 92,
                    "state": 1,
                    "teachTime": 3
                }
            ],
            "totalCount": 188
        }
    }
````

#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="3-2">9.添加教师</h3>

#### 接口名字
* /teacher/addTeacher.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* teacherName*：姓名
* gender：性别（1 男 2 女）
* age：年龄
* phone*：账号
* address：地址
* level：教师级别
* classIds：授课班级id（int数组）
* schoolId：学校id
* graduated：毕业院校
* teachTime：教龄
#### 接口正确返回
````
    {
        "code": 200,
        "description": "请求成功",
        "detail": null
    }
````

#### 接口错误码
错误码 | 说明 |
|:-----|:-----
2000 | 参数错误
100200008 | 账号重复