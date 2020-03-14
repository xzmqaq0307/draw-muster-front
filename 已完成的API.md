# API

## 目录

- [目录](#目录)
- [阅前说明](#阅前说明)
- [用户注册](#用户注册)
		- [检验姓名是否存在（接口）(<font color="blue">v1版本修改</font>)](#检验姓名是否存在接口font-colorbluev1版本修改font)
		- [检验邮箱是否存在（接口）(<font color="blue">v1版本修改</font>)](#检验邮箱是否存在接口font-colorbluev1版本修改font)
		- [获取账户验证码(<font color="blue">v1版本修改</font>)](#获取账户验证码font-colorbluev1版本修改font)
		- [验证用户验证码(<font color="blue">v1版本修改</font>)](#验证用户验证码font-colorbluev1版本修改font)
- [用户登录](#用户登录)
- [修改用户信息(<font color="blue">v1版本修改</font>)](#修改用户信息font-colorbluev1版本修改font)
- [修改用户密码(<font color="blue">v2版本新增</font>)](#修改用户密码font-colorbluev2版本新增font)
- [创建收藏夹](#创建收藏夹)
- [获取收藏夹列表](#获取收藏夹列表)
- [收藏夹内容(<font color="blue">v1版本修改</font>)](#收藏夹内容font-colorbluev1版本修改font)
- [添加作品到收藏夹 (<font color="blue">v1版本修改</font>)](#添加作品到收藏夹-font-colorbluev1版本修改font)
- [删除整个收藏夹 (<font color="blue">v1版本修改</font>)](#删除整个收藏夹-font-colorbluev1版本修改font)
- [删除收藏夹某一个内容(<font color="blue">v1版本修改</font>)](#删除收藏夹某一个内容font-colorbluev1版本修改font)
- [创建画册](#创建画册)
- [其他人获取画册（只能看到公开的）](#其他人获取画册只能看到公开的)
- [用户获取画册（全部）](#用户获取画册全部)
- [创建主题](#创建主题)
- [获取主题列表](#获取主题列表)
- [获取某一个主题详情](#获取某一个主题详情)
- [获取主题下图片列表](#获取主题下图片列表)
- [添加图片到主题](#添加图片到主题)
- [获取某个用户创建的主题列表](#获取某个用户创建的主题列表)
- [创建画画(<font color="blue">v1版本修改</font>)](#创建画画font-colorbluev1版本修改font)
- [上传小文件接口（仅限于画画、头像、封面）](#上传小文件接口仅限于画画头像封面)
- [查看某一幅画详情](#查看某一幅画详情)
- [搜索作品](#搜索作品)
- [搜索用户](#搜索用户)
- [创建评论(<font color="blue">v2版本新增</font>)](#创建评论font-colorbluev2版本新增font)
- [回复某条评论(<font color="blue">v2版本新增</font>)](#回复某条评论font-colorbluev2版本新增font)
- [查询某个页面下的所有评论(<font color="blue">v2版本新增</font>)](#查询某个页面下的所有评论font-colorbluev2版本新增font)
- [查看某个评论下的回复(<font color="blue">v2版本新增</font>)](#查看某个评论下的回复font-colorbluev2版本新增font)
- [删除某条回复(<font color="blue">v2版本新增</font>)](#删除某条回复font-colorbluev2版本新增font)
- [删除某条评论（以及下面所有回复）(<font color="blue">v2版本新增</font>)](#删除某条评论以及下面所有回复font-colorbluev2版本新增font)
- [点赞(<font color="blue">v2版本新增</font>)](#点赞font-colorbluev2版本新增font)
- [获取公告列表(<font color="blue">v2版本新增</font>)](#获取公告列表font-colorbluev2版本新增font)

## 阅前说明

```
网址：http://www.weixiaoyuan.xyz:8081
* 对应接口的使用: http://www.weixiaoyuan.xyz:8081/paint + 接口名称(千万不要忽略了/paint)
* 数据返回code说明: 成功(200)，失败(400)，服务器内部错误(500)
说明：
* 请求参数都是JSON格式、返回的参数也都是JSON格式！！！！
* 轮播图板块接口、画家榜板块接口暂时未投入使用
* 注明修改的V1版本修改接口，基本都是修改了参数的命名格式，如pic_list修改成picList
* 注明新增的V2版本接口是更新的接口
```


## 用户注册

**接口**
```
POST /api/vi/user/register
```
**参数**
```
account: 邮箱
password: 密码
nickname: 昵称
```
**返回的头部 header**
一般是token，前端存储这个token，下次访问携带token，就可以免账号密码登录，一般只保持7天有效。
```
{
	"Authorization": "用户的token"
}
```
**返回的数据**
```
{
	"code": 200,
	"msg": "success",
	"data": {
		"account": 1061138927@qq.com
		"userInfo": {
			"id": 60350,
			"nickname": "北风那个吹",
			"sex": 0,
			"likes": 0,
		}
	}
}
```

#### 检验姓名是否存在（接口）(<font color="blue">v1版本修改</font>)

```
GET /api/v1/user/register/check/name
```
**参数**
```
nickname: 北风那个吹
```
**失败返回**
```
{
	"code": 400,
	"errorCode": "100004",
	"msg": "用户名已存在"
}
```
**成功返回**
```
{
	"code": 200,
	"msg": success
}
```

#### 检验邮箱是否存在（接口）(<font color="blue">v1版本修改</font>)

```
GET /api/v1/user/register/check/email
```
**参数**
```
email: 1061138927@qq.com
```
**失败返回**
```
{
	"code": 400,
	"errorCode": "100004",
	"msg": "账户已存在"
}
```
**返回**
```
{
	"code": 200,
	"msg": success
}
```

#### 获取账户验证码(<font color="blue">v1版本修改</font>)
```
GET /api/v1/user/register/get/code
```
**参数**
```
email: 1061138927@qq.com
```
**返回说明**
```
邮箱验证码会延迟发送到邮箱，并且验证码7分钟内会失效
```
**返回**
```
{
	"code": 200,
	"msg": success
}
```

#### 验证用户验证码(<font color="blue">v1版本修改</font>)
```
GET /api/v1/user/register/check/code
```
**参数**
```
email: 邮箱
verifycode: 验证码
```
**成功返回**
```
{
	"code": 200,
	"msg": success
}
```

## 用户登录

```
GET /api/v1/user/login
```

**参数**
```
account: 邮箱
password: 密码
```

**响应头部 header**
一般是token，前端存储这个token，下次访问携带token，
客户端需要缓存token，就可以免账号密码登录，一般只保持7天有效。
```
{
	"Authorization": "用户的token"
}
```

返回
```
{
	"code": 200,
	"msg": "success",
	"data": {
		"account": "1061138927@qq.com",
		"data":{
			"nickname": "北风那个吹",
			"address": "地址"
			"phone": "123456"
			"sex": 0
			"introduction": "aaa"
			"likes": 123
			"avatar": "aaa"
		}
	}
}
```

## 修改用户信息(<font color="blue">v1版本修改</font>)

**接口**
```
POST /api/v1/user/update/msg
```
**请求头部**
```
"Authorization": "用户的token"
```
**请求参数**

```
sex: 0为女，1为男
nickName: 姓名，
phone：13250122476
introduction： 个人简介
```

**返回**
```
{
	"code": 200,
	"msg": "success"
}
```

## 修改用户密码(<font color="blue">v2版本新增</font>)

**接口**

```
GET /api/v1/user/register/get/code
GET /api/v1/user/register/check/code
POST /api/v1/user/change/pwd
```

**接口解释**

```
1、第一个接口是调用验证码接口获取验证码
2、第二个接口是验证验证码是否正确
3、第三个接口是验证码通过之后便可以更改密码
```

**请求参数**

```
前两个接口上述已有说明
第三个接口参数
"password": "q123456"
```

**返回**

```
{
	"code": 200,
	"msg": "success"
}
```

## 创建收藏夹

**接口**
```
POST /api/v1/fav/create
```
**请求头部**
```
"Authorization": "用户的token"
```

**请求参数**
```
{
	"name": "收藏夹的名字",
	"introduction": "收藏夹介绍",
	"status": 1   // 公开的状态
}
```

**返回**
```
{
	"code": 200,
	"msg": "success"
}
```

## 获取收藏夹列表

**接口**
```
GET /api/v1/fav/list
```
**请求头部**
```
"Authorization": "用户的token"
```
**请求参数**
```
无
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
	"data": [
				{
					"id": 5,
					"favName": "默认收藏夹",
					"favIntro": "这是我的默认收藏夹",
					"publicStatus": true,
					"uid": 60348
				}
	]
}
```

## 收藏夹内容(<font color="blue">v1版本修改</font>)

**接口**
```
GET /api/v1/fav/content
```
**请求头部**
```
"Authorization": "用户的token"
```
**请求参数**
```
"favId": 5  //  收藏夹ID
"start": 0   //  从第几条开始
"sum": 10    //  共返回几条，一般来说是10条
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
	"data": [
				{
					"id": 38,
					"type": "picture",
					"pictureName": "最后的晚餐",
					"pictureIntro": "这是我的第一幅画",
					"picturePath": "这是图片的路径",
					"createTime": 1582395420000,
					"trackPath": "这是视频的路径",
					"likes": 0
				},
				{
					"id": 39,
					"type": "video",
					"pictureName": "素描的技巧",
					"pictureIntro": "这是我的第一个视频教程",
					"picturePath": "这是图片的路径",
					"createTime": 1582395892000,
					"trackPath": "这是视频的路径",
					"likes": 0
				}
		]
}
```

## 添加作品到收藏夹 (<font color="blue">v1版本修改</font>)

**接口**
```
POST /api/v1/fav/add/content
```
**请求头部**
```
"Authorization": "用户的token"
```
**请求参数**
```
"favId": 5,         // 收藏夹id号
"picId": 39,        // 图片id号
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
}
```

## 删除整个收藏夹 (<font color="blue">v1版本修改</font>)

**接口**

```
GET /api/v1/fav/del
```

**请求头部**

```
"Authorization": "用户的token"
```

**请求参数**

```
"favId": 5
```

**返回内容**

```
{
    "code": 200,
    "msg": "success"
}
```

## 删除收藏夹某一个内容(<font color="blue">v1版本修改</font>)

**接口**

```
GET /paint/api/v1/fav/del/content
```

**请求头部**

```
"Authorization": "用户的token"
```

**请求参数**

```
"picList": [38,39],
"favId": 5
```

**参数说明**

```
picList是图片对应的ID号
favId是收藏夹对应的ID号
```

**返回内容**

```
{
    "code": 200,
    "msg": "success"
}
```

## 创建画册

**接口**
```
POST /api/v1/album/create
```
**请求头部**
```
"Authorization": "用户的token"
```
**请求参数**
```
"name": "画册的名字"
"status": 0为私有，1为公开
"introduction": "画册的状态"
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
}
```

## 其他人获取画册（只能看到公开的）

**接口**
```
GET /api/v1/album/public/list
```

**请求参数**
```
uid: 60348
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"id": 3,
			"albumName": "画册一",
			"albumIntro": "这是我第一本画册",
			"sum": 0,
			"publicStatus": true
		},
		{
			"id": 4,
			"albumName": "画册二",
			"albumIntro": "这是我第二本画册",
			"sum": 0,
			"publicStatus": true
		},
		{
			"id": 6,
			"albumName": "画册三",
			"albumIntro": "这是我第三本画册",
			"sum": 0,
			"publicStatus": true
		}
	]

}
```

## 用户获取画册（全部）

**接口**
```
GET /api/v1/album/list
```
**请求头部**
```
"Authorization": "用户的token"
```
**请求参数**
```
无
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"id": 3,
			"albumName": "画册一",
			"albumIntro": "这是我第一本画册",
			"sum": 0,
			"publicStatus": true
		},
		{
			"id": 4,
			"albumName": "画册二",
			"albumIntro": "这是我第二本画册",
			"sum": 0,
			"publicStatus": true
		},
		{
			"id": 5,
			"albumName": "测试",
			"albumIntro": "测试",
			"sum": 0,
			"publicStatus": false
		},
		{
			"id": 6,
			"albumName": "画册三",
			"albumIntro": "这是我第三本画册",
			"sum": 0,
			"publicStatus": true
		}
	]
}
```

## 创建主题

**接口**
```
POST /api/v1/theme/create
```
**请求头部**
```
"Authorization": "用户的token"
```
**请求参数**
```
"name": "主题名字",
"introduction": "主题简介"
"cover": "主题封面"
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
}
```

## 获取主题列表

**接口**
```
GET /api/v1/theme/list
```

**请求参数**
```
"start": 0,
"sum": 10
```

**返回内容**
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"id": 2,
			"themeName": "主题一",
			"themeCover": "这是主题一的封面",
			"createTime": 1582393996000,
			"likes": 0,
			"themeIntro": "这是主题一的介绍",
			"uid": 60349
		},
		{
			"id": 3,
			"themeName": "主题二",
			"themeCover": "这是主题二的封面",
			"createTime": 1582453988000,
			"likes": 0,
			"themeIntro": "这是主题二的介绍",
			"uid": 60348
		}
	]
}
```


## 获取某一个主题详情

**接口**
```
GET /api/v1/theme/detail
```

**请求参数**
```
"themeId": 2
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
	"data": {
		"id": 2,
		"themeName": "主题一",
		"themeCover": "这是主题一的封面",
		"createTime": 1582393996000,
		"likes": 0,
		"themeIntro": "这是主题一的介绍",
		"uid": 60349
	}
}
```

## 获取主题下图片列表

**接口**
```
GET /api/v1/theme/content
```

**请求参数**
```
"themeId": 1
"start": 0
"sum": 10
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"id": 38,
			"type": "picture",
			"pictureName": "最后的晚餐",
			"pictureIntro": "这是我的第一幅画",
			"picturePath": "这是图片的路径",
			"createTime": 1582395420000,
			"trackPath": "这是视频的路径",
			"likes": 0
		}
	]
}
```


## 添加图片到主题

**接口**
```
GET /api/v1/theme/add/content
```
**请求头部**
```
"Authorization": "用户的token"
```
**请求参数**
```
"themeId": 1,
"picId": 38
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
}
```

## 获取某个用户创建的主题列表

**接口**

```
GET /api/v1/theme/user/list
```

**请求参数**
```
"uid": 60348,
```

**返回内容**
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"id": 3,
			"themeName": "主题二",
			"themeCover": "这是主题二的封面",
			"createTime": 1582453988000,
			"likes": 0,
			"themeIntro": "这是主题二的介绍",
			"uid": 60348
		},
		{
			"id": 4,
			"themeName": "主题三",
			"themeCover": "这是主题三的封面",
			"createTime": 1582478907000,
			"likes": 0,
			"themeIntro": "这是主题三的介绍",
			"uid": 60348
		}
	]
}
```

## 创建画画(<font color="blue">v1版本修改</font>)

**接口**
```
POST /api/v1/picture/create
```
**请求头部**
```
"Authorization": "用户的token"
```
**请求参数说明**
```
"album_id": 画册的id，
"picture_path": 这里需要调用上传图片的api，得到上传后返回的图片存储路径，再填写
"track_path":   这里需要调用上传视频的api，得到上传后返回的视频存储路径，再填写
```
**请求参数**

```
"pictureName": "画画名字",
"pictureIntro": "画画的介绍",
"publicStatus": 0为私密，1为公开，
"albumId": 3
"labelName": ["标签一","标签二"],
"picturePath": "画存储的路径"
"type": "picture"
"trackPath": "视频存储路径"
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
}
```

## 上传小文件接口（仅限于画画、头像、封面）

**接口**
```
POST /api/v1/upload/file
```

**请求头部**
```
"Authorization": "用户的token"
```

**请求参数说明**
```
type填写包括["video","picture","cover","avatar"]
```

**请求参数**
```
"file": 文件，
"type": 文件类型
```

**返回内容**
```
{
	"code": 200,
	"msg": "success",
}
```


## 查看某一幅画详情

**接口**
```
GET /api/v1/picture/detail
```

**请求参数**
```
"picId": 39
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
	"data": {
		"id": 39,
		"pictureName": "素描的技巧",
		"pictureIntro": "这是我的第一个视频教程",
		"picturePath": "这是图片的路径",
		"publicStatus": true,
		"createTime": 1582395892000,
		"trackPath": "这是视频的路径",
		"likes": 0,
		"labels": [
			{
				"id": 3,
				"labelName": "素描"
			},
			{
				"id": 24,
				"labelName": "素描教程"
			}
		],
		"themes": [
			{
				"id": 2,
				"themeName": "主题一",
				"themeCover": null,
				"createTime": null,
				"likes": null,
				"themeIntro": null,
				"uid": null
			}
		],
		"album": {
			"id": 3,
			"albumName": "画册一"
		},
		"userInfo": {
			"id": 60348,
			"nickname": "Ventidate",
			"introduction": "二手画家",
			"avatar": "头像"
		}
	}
}
```

## 搜索作品

**接口**
```
GET /api/v1/search/works
```

**请求参数说明**
```
type包括["picture","video"]
orderByTime: 1为随时间升序，0为降序。默认为1
orderByHot: 1为随热度升序， 0为降序。默认为1
```

**请求参数**
```
"keyword": "关键字"
"start": 0,
"sum": 10,
"type": "picture",
"orderByTime": 1,
"orderByHot": 1,
```
**返回内容**

```
{
    "code": 200,
    "msg": "success",
    "data": [
        {
            "id": 38,
            "type": "picture",
            "pictureName": "最后的晚餐",
            "pictureIntro": "这是我的第一幅画",
            "picturePath": "这是图片的路径",
            "createTime": "2020-02-22 18:17:00",
            "trackPath": "这是视频的路径",
            "likes": 1,
            "userInfo": {
                "id": 60348,
                "nickname": "Ventidate",
                "introduction": "二手画家",
                "avatar": "头像"
            }
        }
    ]
}
```

## 搜索用户

**接口**
```
GET /api/v1/search/user
```

**请求参数**
```
"keyword": "关键字",
"start": 0,
"sum": 10
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"id": 60347,
			"nickname": "爱吃鱼的猫",
			"sex": 0,
			"likes": 0,
			"avatar": "头像"
		}
	]
}
```

## 创建评论(<font color="blue">v2版本新增</font>)

**接口**

```
GET /api/v1/comment/create
```

**请求参数**

```
"content": "这是评论的内容",
"type": 1,
"belongId": 38
```

**请求参数解释**

```
type：0为公告下的评论，1为画作下的评论
belongId：这个指的是在哪个作品的id下的
```

**返回数据**

```
{
	"code": 200,
	"msg": "success"
}
```

## 回复某条评论(<font color="blue">v2版本新增</font>)

**接口**

```
GET /api/v1/comment/create/reply
```

**参数**

```
"commentId": 1,
"content": "这是回复的内容",
"ruid": 60349,
"uid":  60348
```

**参数解释**

```
commentId：指的是回复哪一条评论的id号
ruid: 指的是回复人id号
uid: 指的是被回复人的id号
```

**返回**

```
{
	"code": 200,
	"msg": "success"
}
```

## 查询某个页面下的所有评论(<font color="blue">v2版本新增</font>)

**接口**

```
GET /api/v1/comment/get
```

**参数**

```
"start": 0
"sum": 10
"type": 1
"belongId": 38
```

**返回**

```
{
    "code": 200,
    "msg": "success",
    "data": [
        {
            "uid": 60348,
            "comments": "这是第二条评论",
            "commentType": 1,
            "belongId": 38,
            "createTime": "2020-02-25 11:10:04",
            "likes": 0,
            "commentId": 2,
            "replies": [
                {
                    "comments": "这是第四条回复",
                    "uid": 60348,
                    "ruid": 60349,
                    "createTime": "2020-03-13 21:06:14",
                    "likes": 0,
                    "replyId": 7
                }
            ]
        },
        {
            "uid": 60348,
            "comments": "这是第二条评论",
            "commentType": 1,
            "belongId": 38,
            "createTime": "2020-03-13 21:07:30",
            "likes": 0,
            "commentId": 3,
            "replies": [
                {
                    "comments": "这是第五条回复",
                    "uid": 60348,
                    "ruid": 60349,
                    "createTime": "2020-03-13 21:06:46",
                    "likes": 0,
                    "replyId": 8
                }
            ]
        }
    ]
}
```

## 查看某个评论下的回复(<font color="blue">v2版本新增</font>)

**接口**

```
GET /api/v1/comment/get/reply
```

**参数**

```
"start": 0,
"sum": 10,
"commentId": 1
```

**返回**

```
{
    "code": 200,
    "msg": "success",
    "data": [
        {
            "comments": "这是第四条回复",
            "uid": 60348,
            "ruid": 60349,
            "createTime": "2020-03-13 21:06:14",
            "likes": 0,
            "replyId": 7
        },
        {
            "comments": "这是第六条回复",
            "uid": 60348,
            "ruid": 60349,
            "createTime": "2020-03-13 21:09:20",
            "likes": 0,
            "replyId": 9
        }
    ]
}
```

## 删除某条回复(<font color="blue">v2版本新增</font>)

**接口**

```
GET /api/v1/comment/delete/reply
```

**参数**

```
"replyId": 1
```

**返回**

```
{
    "code": 200,
    "msg": "success"
}
```

## 删除某条评论（以及下面所有回复）(<font color="blue">v2版本新增</font>)

**接口**

```
GET /api/v1/comment/delete/commentId
```

**参数**

```
"commentId": 1
```

**返回**

```
{
    "code": 200,
    "msg": "success"
}
```

## 点赞(<font color="blue">v2版本新增</font>)

**接口**

```
GET /api/v1/like/change/status
```

**参数**

```
"likeStatus": 0,
"belongId": 60348,
"likeType": 1
```

**参数解释**

```
likeStatus: 点赞的状态，
belongId: 点赞的ID号，（如评论ID号，用户ID号等）
likeType: 点赞类型（0为评论，1为用户）
```

**返回**

```
{
    "code": 200,
    "msg": "success"
}
```

## 获取公告列表(<font color="blue">v2版本新增</font>)

**接口**

```
GET /api/v1/announce/get/list
```

**参数**

```
"start":  0
"sum" :  10
```

**参数解释**

```
start代表从第几条开始，sum代表返回多少条
比如说第0条开始返回10条，那么下一页获取10条是从第11条开始获取新10条数据，以此类推
```

**返回**

```
{
    "code": 200,
    "msg": "success",
    "data": [
        {
            "id": 1,
            "anTitle": "公告一",
            "anContent": "这是公告一的内容",
            "createTime": "2020-02-27 00:57:42",
            "likes": 0
        },
        {
            "id": 2,
            "anTitle": "公告二",
            "anContent": "这是公告二的内容",
            "createTime": "2020-02-27 01:16:50",
            "likes": 3
        }
    ]
}
```





