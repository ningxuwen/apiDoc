
## 酷音后台接口文档

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
* [5、获取所有类型的课程](#7-5) 

#### 问答管理
* [1、问题列表](#8-1) 
* [2、添加问答](#8-2) 
* [3、删除问答](#8-3) 
* [4、修改问答](#8-4) 
* [5、根据课程类型的课程id查找节课信息](#8-5) 
* [6、根据id查找问答](#8-6)

#### 学生答题
* [1、学生答题列表](#9-1) 
* [2、修改学生答案](#9-2) 
* [3、根据id查找学生答案](#9-3) 

#### musicxml管理
* [1、上传musicxml](#10-1) 
* [2、根据musicxml的名字获取按键信息](#10-2) 


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
                    "name": "酷音",
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
                    "name": "酷音",
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
               "name": "酷音学校",
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
                   "schoolName": "酷音小学",
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
                   "schoolName": "酷音小学",
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
                  "schoolName": "酷音小学"
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
                  "schoolName": "酷音小学"
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
            "endTime":"2017-12-31","id":1,"name":"酷音学校","startTime":"2017-01-01","status":1,"validateDay":1
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

<h3 id="8-1">35.问题列表</h3>

#### 接口名字
* /question/findQuestionList.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* coursepartId：节课id
* state：状态（1正常 2删除）
* pageNo：页码

#### 接口正确返回
````
  {
      "code": 200,
      "description": "请求成功",
      "detail": {
          "nextPage": 1,
          "pageNo": 1,
          "pageSize": 10,
          "prePage": 1,
          "rows": [
              {
                  "optionType": "1",
                  "quesTitle": "下面选项正确的是？",
                  "quesOptions": "今天周一|今天周二|今天周三|今天周四",
                  "createTime": 1512028943000,
                  "coursepartId": 1,
                  "id": 1,
                  "correctOption": "D",
                  "state": 1
              },
              {
                  "optionType": "2",
                  "quesTitle": "下面那个图片是对的？",
                  "quesOptions": "/question/img/1A.png|/question/img/1B.png",
                  "createTime": 1512029281000,
                  "coursepartId": 1,
                  "id": 2,
                  "correctOption": "B",
                  "state": 1
              },
              {
                  "optionType": "1",
                  "quesTitle": "下面图片是？",
                  "quesOptions": "Do|Re|Mi|Fa",
                  "createTime": 1512029495000,
                  "coursepartId": 1,
                  "id": 3,
                  "correctOption": "A",
                  "state": 1,
                  "quesDesc": "/question/img/Do.png"
              },
              {
                  "optionType": "1",
                  "quesTitle": "哪一个不是笑的？",
                  "quesOptions": "哈哈|呵呵|嘿嘿|乎乎",
                  "createTime": 1512094874000,
                  "coursepartId": 3,
                  "id": 4,
                  "correctOption": "D",
                  "state": 1
              }
          ],
          "totalCount": 4
      }
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="8-2">36.添加问答(json格式请求)</h3>

#### 接口名字
* /question/insertQuestion.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* quesTitle*：问题标题
* quesDesc：问题描述（此处一般为图片、音频等等，可以位空）
* optionType*：选项类型（1代表文字型的 2代表资源型的）
* quesOptions*：问题选项（选项之间以 | 隔开，如：哈哈|呵呵|嘿嘿|乎乎）
* correctOption*：正确答案
* coursepartId*：那一节课添加

#### 接口正确返回
````
  {
      "code": 200,
      "description": "请求成功",
      "detail":null 
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100200014 | 标题不能为空
100200015 | 问题选项类型不能为空
100200016 | 问题选项不能为空
100200017 | 正确答案不能为空
100200018 | 节课id不能为空

<h3 id="8-3">37.删除问答</h3>

#### 接口名字
* /question/deleteQuestion.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* id* ：id
* quesTitle*：问题标题
* quesDesc：问题描述（此处一般为图片、音频等等，可以位空）
* optionType*：选项类型（1代表文字型的 2代表资源型的）
* quesOptions*：问题选项（选项之间以 | 隔开，如：哈哈|呵呵|嘿嘿|乎乎）
* correctOption*：正确答案
* coursepartId*：那一节课添加

#### 接口正确返回
````
  {
      "code": 200,
      "description": "请求成功",
      "detail":null 
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="8-4">38.修改问答</h3>

#### 接口名字
* /question/updateQuestion.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* id* ：id
* quesTitle：问题标题
* quesDesc：问题描述（此处一般为图片、音频等等，可以位空）
* optionType：选项类型（1代表文字型的 2代表资源型的）
* quesOptions：问题选项（选项之间以 | 隔开，如：哈哈|呵呵|嘿嘿|乎乎）
* correctOption：正确答案
* coursepartId：那一节课添加

#### 接口正确返回
````
  {
      "code": 200,
      "description": "请求成功",
      "detail":null 
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="7-5">39.获取所有类型的课程</h3>

#### 接口名字
* /course/findAllCourse.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)

#### 接口正确返回
````
  {
      "code": 200,
      "description": "请求成功",
      "detail": [
          {
              "createTime": 1493978837000,
              "description": "幼儿园",
              "id": 6,
              "name": "幼儿园",
              "status": 1,
              "type": 3
          },
          {
              "createTime": 1490584858000,
              "description": "丰台一小用的",
              "id": 5,
              "name": "丰台一小",
              "status": 1,
              "type": 2
          },
          {
              "createTime": 1488363287000,
              "description": "社培用",
              "id": 4,
              "name": "C版社培",
              "status": 1,
              "type": 4
          },
          {
              "createTime": 1487037442000,
              "description": "幼儿园的",
              "id": 3,
              "name": "幼儿园",
              "status": 1,
              "type": 3
          },
          {
              "createTime": 1487037442000,
              "description": "示范课",
              "id": 2,
              "name": "示范课",
              "status": 1,
              "type": 2
          },
          {
              "createTime": 1487037442000,
              "description": "一年级",
              "id": 1,
              "name": "一年级",
              "status": 1,
              "type": 1
          }
      ]
  }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="8-5">40.根据课程类型的课程id获取节课信息</h3>

#### 接口名字
* /question/findCoursePartByCourseId.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* courseId*：课程类型id

#### 接口正确返回
````
{
    "code": 200,
    "description": "请求成功",
    "detail": [
        {
            "course_id": 1,
            "part_sort": 1,
            "path": "一年级",
            "is_light": 0,
            "name": "第一课",
            "pid": 0,
            "id": 1,
            "has_source": 1,
            "state": 1,
            "type": 0,
            "is_screen": 0
        },
        {
            "course_id": 1,
            "part_sort": 2,
            "path": "一年级",
            "is_light": 0,
            "name": "第二课",
            "pid": 0,
            "id": 16,
            "has_source": 1,
            "state": 1,
            "type": 0,
            "is_screen": 0
        },
        {
            "course_id": 1,
            "part_sort": 3,
            "path": "一年级",
            "is_light": 0,
            "name": "第三课",
            "pid": 0,
            "id": 36,
            "has_source": 1,
            "state": 1,
            "type": 0,
            "is_screen": 0
        },
        {
            "course_id": 1,
            "part_sort": 4,
            "path": "一年级",
            "is_light": 0,
            "name": "第四课",
            "pid": 0,
            "id": 51,
            "has_source": 1,
            "state": 1,
            "type": 0,
            "is_screen": 0
        }
    ]
}
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100200013 | 课程id不能为空

<h3 id="8-6">41.根据id获取问答</h3>

#### 接口名字
* /question/findQuestion.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* id*：问答id

#### 接口正确返回
````
{
  "code": 200,
  "description": "请求成功",
  "detail": {
    "correctOption": "D",
    "coursepartId": 3,
    "createTime": 1512094874000,
    "id": 4,
    "optionType": "1",
    "quesDesc": null,
    "quesOptions": "哈哈|呵呵|嘿嘿|乎乎",
    "quesTitle": "哪一个不是笑的？",
    "state": 1
  }
}
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="9-1">42.学生答案列表</h3>

#### 接口名字
* /questionStudent/findQuesStuList.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* schoolId：学校id
* classId：班级id
* coursepartId：节课id
* pageNo：页码
* state：状态

#### 接口正确返回
````
{
  "code": 200,
  "description": "请求成功",
  "detail": {
    "nextPage": 1,
    "pageNo": 1,
    "pageSize": 10,
    "prePage": 1,
    "rows": [
      {
        "classId": 1,
        "stuId": 1,
        "createTime": 1513131744000,
        "stuOption": "B",
        "className": "1班",
        "id": 23,
        "state": 1,
        "schoolName": "宣称十一小学",
        "quesId": 3,
        "isCorrect": 2
      },
      {
        "classId": 1,
        "stuId": 1,
        "createTime": 1513131720000,
        "stuOption": "A",
        "className": "1班",
        "id": 22,
        "state": 1,
        "schoolName": "宣称十一小学",
        "quesId": 2,
        "isCorrect": 1
      },
      {
        "classId": 1,
        "stuId": 1,
        "createTime": 1513131693000,
        "stuOption": "D",
        "className": "1班",
        "id": 21,
        "state": 1,
        "schoolName": "宣称十一小学",
        "quesId": 1,
        "isCorrect": 1
      }
    ],
    "totalCount": 3
  }
}
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="9-2">43.修改学生答案</h3>

#### 接口名字
* /questionStudent/updateQuesStu.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* stuOption*：学生答案

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
100100019 | 学生答案不能为空

<h3 id="9-3">44.根据id查找学生答案</h3>

#### 接口名字
* /questionStudent/findQuesStu.json

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
    "classId": 1,
    "count": null,
    "coursepartId": 1,
    "createTime": 1513131720000,
    "id": 22,
    "isCorrect": 1,
    "quesId": 2,
    "schoolId": 1,
    "state": 1,
    "stuId": 1,
    "stuOption": "A"
  }
}
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="10-1">45.上传musicxml</h3>

#### 接口名字
* /musicxml/uploadMusixXml.json

#### 接口请求方式
* POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)

#### 接口正确返回
````
{
  "code": 200,
  "description": "请求成功",
  "detail": ...
}
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----

<h3 id="10-2">46.根据musicxml的名字获取按键信息</h3>

#### 接口名字
* /musicxml/findMusicxml.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* fileName*：名字

#### 接口正确返回
````
{
	"code": 200,
	"description": "请求成功",
	"detail": "{\"P1\":[[-1],[72],[71],[72],[74],[75],[67],[68],[70],[68],[65],[77],[75],[74],[72],[71],[80],[79],[77],[75],[74],[72],[71],[72],[74],[72],[74],[74],[72],[74],[75],[74],[72],[74],[75],[77],[79],[0],[79],[0],[77],[0],[-1],[0],[77],[0],[77],[0],[75],[0],[-1],[0],[74],[0],[75],[0],[68],[0],[68],[65],[70],[65],[0],[67],[0],[75],[0],[75],[74],[75],[70],[72],[75],[80],[79],[77],[75],[74],[72],[70],[74],[79],[77],[75],[74],[72],[70],[68],[72],[77],[72],[74],[0],[0],[74],[75],[70],[72],[70],[79],[0],[0],[0],[79],[70],[72],[70],[80],[0],[0],[0],[80],[70],[75],[74],[79],[77],[80],[79],[84],[82],[80],[79],[77],[82],[80],[82],[79],[82],[80],[82],[75],[79],[77],[79],[72],[74],[75],[77],[74],[75],[77],[79],[75],[77],[79],[80],[82],[80],[84],[82],[80],[79],[77],[80],[74],[0],[0],[0],[74],[74],[79],[74],[75],[72],[74],[70],[72],[0],[0],[0],[72],[79],[78],[81],[72],[70],[72],[0],[72],[78],[76],[74],[82],[0],[0],[76],[78],[79],[0],[79],[0],[67],[66],[67],[69],[70],[62],[63],[65],[63],[60],[72],[70],[69],[67],[66],[75],[74],[72],[70],[69],[67],[66],[67],[69],[67],[69],[69],[0],[0],[67],[69],[70],[69],[67],[69],[70],[72],[74],[0],[74],[0],[72],[0],[-1],[0],[72],[0],[72],[0],[70],[0],[-1],[0],[69],[0],[70],[0],[63],[0],[63],[60],[65],[60],[62],[0],[70],[0],[70],[69],[70],[65],[67],[70],[75],[74],[72],[70],[69],[67],[65],[69],[74],[72],[70],[69],[67],[65],[63],[67],[72],[67],[69],[0],[0],[69],[70],[65],[67],[65],[74],[0],[0],[0],[74],[65],[67],[65],[75],[0],[0],[0],[75],[65],[70],[69],[74],[72],[75],[74],[79],[77],[75],[74],[72],[77],[75],[77],[74],[72],[70],[69],[74],[72],[75],[74],[72],[70],[69],[72],[77],[0],[0],[0],[77],[67],[72],[71],[75],[74],[77],[75],[80],[79],[77],[75],[74],[79],[77],[79],[75],[74],[72],[71],[72],[74],[75],[67],[68],[70],[68],[65],[77],[75],[74],[72],[71],[80],[79],[77],[75],[74],[72],[71],[72],[74],[72],[74],[74],[0],[0],[72],[74],[75],[74],[72],[74],[75],[77],[79],[0],[79],[0],[77],[0],[-1],[0],[77],[0],[77],[0],[75],[74],[79],[77],[80],[79],[79],[0],[0],[80],[74],[0],[72],[72,36]],\"P2\":[[-1],[0],[0],[0],[0],[0],[0],[0],[0],[0],[0],[0],[0],[0],[0],[-1],[0],[0],[0],[0],[0],[0],[0],[0],[0],[0],[0],[0],[0],[0],[-1],[0],[60],[59],[60],[62],[63],[55],[56],[58],[56],[53],[65],[63],[62],[60],[59],[68],[67],[65],[63],[62],[60],[59],[60],[62],[60],[62],[62],[0],[0],[60],[62],[63],[62],[60],[62],[63],[65],[67],[0],[67],[0],[65],[0],[-1],[0],[65],[0],[65],[0],[63],[0],[-1],[0],[62],[0],[63],[0],[56],[0],[56],[53],[58],[53],[55],[0],[63],[0],[63],[62],[63],[58],[60],[63],[68],[67],[65],[63],[62],[60],[58],[62],[67],[65],[63],[62],[60],[58],[56],[60],[65],[60],[62],[0],[0],[62],[63],[58],[60],[58],[67],[0],[0],[0],[67],[58],[60],[58],[68],[0],[0],[0],[68],[58],[63],[62],[67],[65],[68],[67],[72],[70],[68],[67],[65],[70],[68],[70],[67],[0],[51],[53],[55],[57],[58],[50],[51],[53],[51],[48],[60],[58],[57],[55],[54],[63],[62],[60],[58],[57],[55],[54],[55],[57],[55],[57],[57],[55],[57],[58],[57],[55],[57],[58],[60],[62],[0],[62],[0],[60],[0],[-1],[0],[60],[0],[60],[0],[58],[0],[-1],[0],[57],[0],[58],[0],[51],[0],[51],[48],[53],[48],[0],[50],[0],[58],[0],[58],[57],[58],[53],[55],[58],[63],[62],[60],[58],[57],[55],[53],[57],[62],[60],[58],[57],[55],[53],[51],[55],[60],[55],[57],[0],[0],[57],[58],[53],[55],[53],[62],[0],[0],[0],[62],[53],[55],[53],[63],[0],[0],[0],[63],[53],[58],[57],[62],[60],[63],[62],[67],[65],[63],[62],[60],[65],[63],[65],[62],[65],[63],[65],[58],[62],[60],[62],[55],[57],[58],[60],[57],[58],[60],[62],[58],[60],[62],[63],[65],[63],[67],[65],[63],[62],[60],[63],[57],[0],[0],[0],[57],[50],[55],[54],[58],[57],[60],[58],[63],[62],[60],[58],[57],[62],[60],[62],[59],[65],[63],[62],[60],[58],[56],[55],[53],[51],[50],[48],[55],[0],[43],[0],[48],[0],[0],[50],[51],[53],[55],[0],[55],[0],[53],[0],[-1],[0],[53],[0],[53],[0],[51],[0],[51],[53],[51],[50],[48],[46],[44],[43],[41],[39],[41],[43],[0],[36],[0],[48],[47],[48],[50],[51],[43],[44],[46],[44],[41],[53],[51],[50],[48],[47],[56],[55],[53],[51],[50],[48],[47],[48],[43],[44],[41],[43],[43],[0],[0]]}"
}
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
