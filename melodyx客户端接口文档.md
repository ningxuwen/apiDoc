
## melodyx客户端接口文档

### 版本
版本        | 修改日期		| 修改人  | 修改记录
:---------- |:-------------|:-----|:--------
1.0.0    | 20170911 | 宁旭温 | 创建文档

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
#### 登录系列
* [1、教师端登录接口](#1) 
* [2、教师修改密码](#2)
* [3、学生登录](#4)
#### 版本更新
* [1、获取最新版本信息](#3)
#### 年级班级相关接口
* [1、根据老师获取其授课班级](#5)
* [2、根据班级获取所有学生](#6)
#### 课程相关接口
* [1、查询课程信息](#7)
* [2、获取课程信息用于下载](#8)

#### 问答接口
* [1、根据节课id(courseId)获取问答信息](#9)
* [2、保存学生答案](#10)
* [3、根据学生id和问答id查找答题信息](#11)
* [4、根据班级id、节课id 查询改班级下所有学生在该节课的答题正确数错误数](#12)
* [5、查询某个班级下所有学生 对某道题的答题情况](#13)



### 接口详情

<h3 id="1">1.教师端登录接口</h3>

#### 接口名字
* /client/teacherLogin.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* account* ：教师账号
* password* ：教师密码（必须MD5加密）

#### 接口正确返回
````
    {
        "code": 200,
        "description": "请求成功",
        "detail": {
            "teacherId": 2,
            "phone": "13700000001",
            "schoolId": 2,
            "nickname": "程序猿甲",
            "schoolName": "小学学校"
        }
    }
````

#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100100001 | 账号为空
100100002 | 密码为空
100100003 | 学校过期
100100004 | 用户不存在

<h3 id="2">2.教师修改密码</h3>

#### 接口名字
* /client/resetPass.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* account* ：教师账号
* oldPassword* ：教师原密码（必须MD5加密）
* newPassword* ：教师新密码（必须MD5加密）
* confirmPassword* ：确认密码（必须MD5加密）

#### 接口正确返回
````
    {
        "code": 200,
        "description": "请求成功",
        "detail": {
        }
    }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100100001 | 账号为空
100100002 | 密码为空
100100005 | 新密码为空
100100006 | 确认密码为空
100100007 | 旧密码不正确
100100008 | 两次输入密码不一致

<h3 id="3">3.获取最新版本信息</h3>

#### 接口名字
* /client/version/versionInfo.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* type* ：客户端类型（值1代表教师端 2代表学生端）

#### 接口正确返回
````
    {
      "code": 200,
      "description": "请求成功",
      "detail": {
        "code": "0.0.2",
        "createDate": "2017-02-20 12:02:18",
        "id": 5,
        "info": "走过路过看Yi看fgfdgfdgfgfg",
        "isforced": 1,  //1不强制升级 2强制升级
        "remark": "哈哈啊",
        "state": 1,
        "type": 1,   //1教师端2学生端
        "url": "/apk/2017-02-16/teacher_v2.0.2.apk"
      }
    }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100100009 | 客户端类型不合法
100100010 | 版本信息获取错误

<h3 id="4">4.学生登录</h3>

#### 接口名字
* /client/stuLogin.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* account*：账号

#### 接口正确返回
````
    {
      "code": 200,
      "description": "请求成功",
      "detail": {
        "classId": 1,
        "phone": "05631011002",
        "schoolId": 4,
        "className": "1班",
        "id": 2,
        "stuName": "2",
        "schoolName": "宣称十一小学"
      }
    }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100100012 | 账号不能为空


<h3 id="5">5.获取老师的所有授课班级</h3>

#### 接口名字
* /client/school/findAllGradeAndClass.json

#### 接口请求方式
* GET/POST

#### 接口请求参数
* schoolId*：学校id
* type*：老师类型（2代表老师 3代表管理员）
* phone*：手机号

#### 接口返回值
* 正确返回：
```
{"code":200,"description":"请求成功","detail":
[{"gName":"一年级","gid":102,"classArray":[{"cName":"一班","cid":1}]}]}
```
#### 接口错误码
错误码 | 说明 |
|:-----|:-----|
|100100014|学校id不能为空|
|100100015|用户手机号不能为空|
|100100016|用户type不能为空|

<h3 id="6">6.获取班级下的所有学生</h3>

#### 接口名字
* /client/class/findStuByCid.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* cid*：班级id

#### 接口正确返回
````
   {
       "code": 200,
       "description": "请求成功",
       "detail": [
           {
               "address": "12",
               "age": 12,
               "classId": 80,
               "className": null,
               "entrancetime": "2017-06-24 00:00:00",
               "gender": 1,
               "id": 801,
               "name": "1",
               "phone": "15315895301",
               "schoolId": 74,
               "state": 1,
               "studentNo": null
           },
           {
               "address": "12",
               "age": 12,
               "classId": 80,
               "className": null,
               "entrancetime": "2017-06-24 00:00:00",
               "gender": 1,
               "id": 802,
               "name": "2",
               "phone": "15315895302",
               "schoolId": 74,
               "state": 1,
               "studentNo": null
           }
       ]
   }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100100011 | 班级id不能为空

<h3 id="7">7.查询课程信息</h3>

#### 接口名字
* /client/course/findCoursePart.json

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
           xxxxx
       ]
   }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100100014 | 学校id不能为空
100100017 | 学校不存在
100100018 | 课程id为空

<h3 id="8">8.获取课程信息用于下载</h3>

#### 接口名字
* client/course/findCourseOnlyPath.json

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
           xxxxx
       ]
   }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100100014 | 学校id不能为空
100100017 | 学校不存在
100100018 | 课程id为空

<h3 id="9">9.根据节课id(coursepartId)获取问答信息</h3>

#### 接口名字
* /client/question/findQuestions.json

#### 接口请求方式
* GET/POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* courseId*：节课id

#### 接口正确返回
````
   {
       "code": 200,
       "description": "请求成功",
       "detail": [
           {
               "correctOption": "D",  //正确答案
               "coursepartId": 1,
               "createTime": 1512028943000,
               "id": 1,
               "optionType": "1", //选项类型（1 代表文字，2代表图片，3代表音频）
               "quesDesc": null, //问题描述（为空或者图片）
               "quesOptions": "今天周一|今天周二|今天周三|今天周四",
               "quesTitle": "下面选项正确的是？",//问题标题
               "state": 1
           },
           {
               "correctOption": "B",
               "coursepartId": 1,
               "createTime": 1512029281000,
               "id": 2,
               "optionType": "2",
               "quesDesc": null,
               "quesOptions": "/question/img/1A.png|/question/img/1B.png",
               "quesTitle": "下面那个图片是对的？",
               "state": 1
           },
           {
               "correctOption": "A",
               "coursepartId": 1,
               "createTime": 1512029495000,
               "id": 3,
               "optionType": "1",
               "quesDesc": "/question/img/Do.png",
               "quesOptions": "Do|Re|Mi|Fa",
               "quesTitle": "下面图片是？",
               "state": 1
           }
       ]
   }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
2000 | 参数错误

<h3 id="10">10.保存学生答案</h3>

#### 接口名字
* /client/questionStudent/submitOption.json

#### 接口请求方式
* POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* stuOption*：学生答案
* quesId*：问答id
* stuId*：学生id
* classId*：班级id

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
100100020 | 问答id不能为空
100100021 | 学生id不能为空

<h3 id="11">11.根据学生id和问答id查找答题信息</h3>

#### 接口名字
* /client/questionStudent/findQuestionStudent.json

#### 接口请求方式
* POST

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* quesId*：问答id
* stuId*：学生id

#### 接口正确返回
````
   {
     "code": 200,
     "description": "请求成功",
     "detail": {
       "count": null,
       "createTime": 1512110071000,
       "id": 1,
       "isCorrect": 1, //是否正确 1正确 2错误
       "quesId": 1, //问题id
       "state": 1,
       "stuId": 1,//学生id
       "stuOption": "D"//学生答案
     }
   }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100100020 | 问答id不能为空
100100021 | 学生id不能为空

<h3 id="12">12.根据班级id、节课id 查询改班级下所有学生在该节课的答题正确数错误数</h3>

#### 接口名字
* /client/questionStudent/findQuestionStudent.json

#### 接口请求方式
* POST/GET

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* classId*：班级id
* coursepartId*：节课id

#### 接口正确返回
````
   {
     "code": 200,
     "description": "请求成功",
     "detail": [
       {
         "classId": 1,
         "correctCount": 1, //正确问题数
         "count": null,
         "coursepartId": 1,
         "createTime": 1512373876000,
         "errorCount": 2,//错误问题数
         "id": 5,
         "nooptionCount": 0,//未回答问题数
         "state": 1,
         "stuId": 1
       },
       {
         "classId": 1,
         "correctCount": 1,
         "count": null,
         "coursepartId": 1,
         "createTime": 1512378355000,
         "errorCount": 0,
         "id": 6,
         "nooptionCount": 2,
         "state": 1,
         "stuId": 2
       }
     ]
   }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100100011 | 班级id不能为空
100200013 | 课程id不能为空

<h3 id="13">13.查询某个班级下所有学生 对某道题的答题情况</h3>

#### 接口名字
* /client/questionStudent/findQuesStuInfo.json

#### 接口请求方式
* POST/GET

#### 接口请求参数(带*为必传。所有接口统一这样规定)
* classId*：班级id
* quesId*：问题id

#### 接口正确返回
````
   {
     "code": 200,
     "description": "请求成功",
     "detail": [
       {
         "classId": 1,
         "count": null,
         "createTime": 1512373876000,
         "id": 17,
         "isCorrect": 1,//是否正确 1正确 2错误
         "quesId": 1,
         "state": 1,
         "stuId": 1,
         "stuOption": "D" //学生答案
       },
       {
         "classId": 1,
         "count": null,
         "createTime": 1512378355000,
         "id": 20,
         "isCorrect": 1,
         "quesId": 1,
         "state": 1,
         "stuId": 2,
         "stuOption": "D"
       }
     ]
   }
````
#### 接口错误码
错误码 | 说明 |
|:-----|:-----
100100011 | 班级id不能为空
100100020 | 问题id不能为空

