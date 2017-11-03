
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
* [4、修改学校](#2-4) 
* [5、所有学校](#2-5) 
* [6、根据学校id获取学校信息](#2-6) 

#### 教师管理
* [1、教师列表](#3-1) 
* [2、添加教师](#3-2) 
* [3、删除教师](#3-3) 
* [4、更新教师](#3-4) 
* [5、根据教师id获取教室信息](#3-5) 

#### 学生管理
* [1、学生列表](#4-1) 
* [2、添加学生](#4-2) 
* [3、删除学生](#4-3) 
* [4、修改学生](#4-4) 
* [5、根据学生id获取学生信息](#4-5) 

#### 年级管理
* [1、年级列表](#5-1) 
* [2、添加年级](#5-2) 
* [3、修改年级](#5-3) 
* [4、删除年级](#5-4) 
* [5、根据学校id获取年级列表](#5-5) 
* [6、根据年级id获取年级信息](#5-6) 

#### 班级管理
* [1、班级列表](#6-1) 
* [2、添加班级](#6-2) 
* [3、删除班级](#6-3) 
* [4、修改班级](#6-4) 
* [5、根据学校id获取年级班级（年级名字班级名字）](#6-5) 
* [6、根据班级id获取班级信息](#6-6) 

#### 课程管理
* [1、课程列表](#7-1) 
* [2、根据id查找课程](#7-2) 
* [3、修改课程](#7-3) 
* [4、上传课程（excel上传）](#7-4) 


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
* /school/updateSchool.json

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
* phone：手机号
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
100200012 | 账号存在但是在删除状态

<h3 id="3-3">10.删除教师</h3>

#### 接口名字
* /teacher/delTeacher.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* teacherId*：教师id
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

<h3 id="3-4">11.更新教师</h3>

#### 接口名字
* /teacher/updateTeacher.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* teacherId*：教师id
* teacherName：姓名
* gender：性别（1 男 2 女）
* age：年龄
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

<h3 id="2-5">12.所有学校</h3>

#### 接口名字
* /school/schools.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)

#### 接口正确返回
````
   {
       "code": 200,
       "description": "",
       "detail": [
           {
               "amCourse": null,
               "courseId": null,
               "courseName": null,
               "createTime": null,
               "endTime": null,
               "id": 1,
               "name": "天使学校",
               "startTime": null,
               "status": 0,
               "validateDay": 0
           },
           {
               "amCourse": null,
               "courseId": null,
               "courseName": null,
               "createTime": null,
               "endTime": null,
               "id": 2,
               "name": "小学学校",
               "startTime": null,
               "status": 0,
               "validateDay": 0
           }
       ]
   }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="4-1">13.学生列表</h3>

#### 接口名字
* /student/stuList.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* sid：学校id
* phone：手机号
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
                   "student_no": "20",
                   "address": "北京",
                   "entrancetime": 1505232000000,
                   "gender": 1,
                   "phone": "13910000030",
                   "name": "20",
                   "id": 334383,
                   "state": 1,
                   "schoolName": "天使音乐小学",
                   "age": 12
               },
               {
                   "student_no": "19",
                   "address": "北京",
                   "entrancetime": 1505232000000,
                   "gender": 1,
                   "phone": "13910000029",
                   "name": "19",
                   "id": 334382,
                   "state": 1,
                   "schoolName": "天使音乐小学",
                   "age": 12
               }
           ],
           "totalCount": 974
       }
   }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="4-2">13.添加学生</h3>

#### 接口名字
* /student/addStu.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* stuName*：姓名
* phone*：手机号
* gender：性别
* age：年龄
* address：地址
* classId*：班级id
* entranceTime：入学时间

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
100200008 | 手机已经使用
100200012 | 账号已存在但是已删除

<h3 id="4-3">14.删除学生</h3>

#### 接口名字
* /student/delStu.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* stuIds*：学生id（多个之间以逗号隔开）

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

<h3 id="4-4">15.修改学生</h3>

#### 接口名字
* /student/updateStu.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* stuId*：学生id
* stuName：姓名
* phone：手机号
* gender：性别
* age：年龄
* address：地址
* classId：班级id
* entranceTime：入学时间

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

<h3 id="5-1">16.年级列表</h3>

#### 接口名字
* /grade/findAllGrades.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* sid：学校id
* name：年级名字
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
                  "school_id": 293,
                  "create_time": 1505268248000,
                  "name": "音乐课程",
                  "id": 188,
                  "schoolName": "天使音乐小学"
              },
              {
                  "school_id": 292,
                  "create_time": 1500787421000,
                  "name": "音乐课程",
                  "id": 187,
                  "schoolName": "新徽实验学校"
              }
          ],
          "totalCount": 87
      }
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="5-2">17.添加年级</h3>

#### 接口名字
* /grade/addGrade.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* sid*：学校id
* name*：名字

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
100200001 | 学校id不能为空
100200002 | 名字不能为空


<h3 id="5-3">18.修改年级</h3>

#### 接口名字
* /grade/updateGrade.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* gid*：年级id
* name*：名字

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
100200003 | 年级id不能为空

<h3 id="5-4">19.修改年级</h3>

#### 接口名字
* /grade/delGrade.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* gid*：年级id

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
100200003 | 年级id不能为空

<h3 id="5-5">20.根据学校id获取年级列表</h3>

#### 接口名字
* /grade/findGradesBySid.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* sid*：学校id

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
100200001 | 学校id不能为空

<h3 id="6-1">21.班级列表</h3>

#### 接口名字
* /class/classList.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* sid：学校id
* state：班级状态（1正常 2删除）
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
                  "create_time": 1505268264000,
                  "name": "1班",
                  "id": 100,
                  "gname": "音乐课程",
                  "schoolName": "天使音乐小学"
              },
              {
                  "create_time": 1500787421000,
                  "name": "1班1",
                  "id": 99,
                  "gname": "音乐课程",
                  "schoolName": "新徽实验学校"
              }
          ],
          "totalCount": 98
      }
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="6-2">22.添加班级</h3>

#### 接口名字
* /class/delClass.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* sid*：学校id
* gid*：年级id
* className*：班级名字

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
100100014 | 学校id不能为空
100200003 | 年级id不能为空
100200010 | 班级已经存在

<h3 id="6-3">23.删除班级</h3>

#### 接口名字
* /class/delClass.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* cid*：班级id

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
100100011 | 班级id不能为空

<h3 id="6-4">24.修改班级</h3>

#### 接口名字
* /class/updateClass.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* cid*：班级id
* gid：年级id
* className：班级名字（班级名字和年级id至少有一个不为空）

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
100100011 | 班级id不能为空
100200011 | 参数错误

<h3 id="6-5">25.根据学校获取年级班级</h3>

#### 接口名字
* /class/findGradeClass.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* sid*：学校id

#### 接口正确返回
````
  {
      "code": 200,
      "description": "请求成功",
      "detail": [
          {
              "className": "一年级一班",（年级名字+班级名字）
              "id": 1
          },
          {
              "className": "一年级二班",
              "id": 2
          }
      ]
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100100011 | 班级id不能为空
100200011 | 参数错误

<h3 id="2-6">26.根据学校id获取学校信息</h3>

#### 接口名字
* /school/findSchool.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* sid*：学校id

#### 接口正确返回
````
  {"code":200,
  "description":"请求成功",
  "detail":{"amCourse":null,"courseId":1,"courseName":null,"createTime":"2017-02-13 19:21:02",
            "endTime":"2017-12-31","id":1,"name":"天使学校","startTime":"2017-01-01","status":1,"validateDay":1
           }
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="3-5">27.根据教师id获取教师信息</h3>

#### 接口名字
* /teacher/findTeacher.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* teacherId*：教师id

#### 接口正确返回
````
  {"code":200,
  "description":"请求成功",
  "detail":{"address":"北京市","age":23,"classIds":[1,2,3,4,5,6,7,8,11],"classList":null,"classStr":null,
            "createTime":null,"gender":1,"graduated":"北京音乐学院","id":1,"level":1,"name":"葛老师",
            "phone":"13700000003","school":null,"school_id":1,"state":1,"teachTime":2
           }
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
2000 | 参数错误

<h3 id="4-5">28.根据学生id获取学生信息</h3>

#### 接口名字
* /student/findStudent.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* stuId*：学生id

#### 接口正确返回
````
  {"code":200,
  "description":"请求成功",
  "detail":{"entranceTime":1441814400000,"address":"test撒旦法十多分","stuId":1,"gender":1,"phone":"10000001108",
            "className":"一年级一班","stuName":"杰克","age":23,"stuNo":null,"status":1
           }
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="5-6">29.根据年级id获取年级信息</h3>

#### 接口名字
* /grade/findGrade.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* gid*：年级id

#### 接口正确返回
````
  {"code":200,
  "description":"请求成功",
  "detail":{"classList":null,"createTime":"2017-02-14 10:43:48","id":102,"name":"一年级",
            "school":null,"schoolId":1,"sequence":0,"state":1
           }
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="6-6">30.根据班级id获取班级信息</h3>

#### 接口名字
* /class/findClass.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* cid*：班级id

#### 接口正确返回
````
  {"code":200,
  "description":"请求成功",
  "detail":{"gid":102,"school_id":1,"create_time":1487040228000,"name":"一班","id":1}}
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="7-1">31.课程列表</h3>
#### 接口名字
* /course/findCourseList.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* name：名字
* state：状态

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
                  "course_id": 1,
                  "part_sort": 11,
                  "path": "一年级-->第一课",
                  "is_light": 0,
                  "name": "游戏",
                  "pid": 1,
                  "id": 15,
                  "has_source": 1,
                  "state": 1,
                  "type": 1    type：值 102 103 下面有资源  
              },
              {
                  "course_id": 1,
                  "part_sort": 10,
                  "path": "一年级-->第一课",
                  "is_light": 0,
                  "name": "补充聆听",
                  "pid": 1,
                  "id": 14,
                  "has_source": 1,
                  "state": 1,
                  "type": 1
              },
              {
                  "course_id": 1,
                  "part_sort": 9,
                  "path": "一年级-->第一课",
                  "is_light": 0,
                  "name": "补充歌唱",
                  "pid": 1,
                  "id": 13,
                  "has_source": 1,
                  "state": 1,
                  "type": 1
              }
          ],
          "totalCount": 15
      }
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="7-2">32.根据id获取课程</h3>

#### 接口名字
* /course/findCourse.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* id*：id

#### 接口正确返回
````
  {
      "code": 200,
      "description": "请求成功",
      "detail": {
          "path": "一年级-->第一课-->弹奏",
          "hasSource": 2,
          "isLight": 0,
          "name": "认识黑白键1",
          "pid": 7,
          "id": 8,
          "state": 1,
          "source": "1-1-1-1.mp4",
          "type": 102,
          "courseId": 1
      }
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100200013 | 课程id不能为

<h3 id="7-3">33.修改课程</h3>

#### 接口名字
* /course/updateCourse.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* id*：id
* name：名字
* isLight：是否亮灯 0 不亮灯 1亮灯
* isScreen：是否投屏 0 不投 1投屏
* state：状态 1正常 2删除


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
100200013 | 课程id不能为

<h3 id="7-4">34.上传课程</h3>

#### 接口名字
* /course/uploadCourse.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)

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