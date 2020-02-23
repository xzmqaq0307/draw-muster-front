
# API
```
网址：http://www.weixiaoyuan.xyz:8081
对应接口的使用: http://www.weixiaoyuan.xyz:8081 + 接口名称
数据返回code说明: 成功(200)，失败(400)，服务器内部错误(500)
```

- [API](#api)
- [用户注册](#用户注册)
- [检验姓名是否存在（接口）](#检验姓名是否存在接口)
- [检验邮箱是否存在（接口）](#检验邮箱是否存在接口)        
- [获取账户验证码](#获取账户验证码)            
- [验证用户验证码](#验证用户验证码)    
- [用户登录](#用户登录)    
- [修改用户信息](#修改用户信息)    
- [创建收藏夹](#创建收藏夹)    
- [获取收藏夹列表](#获取收藏夹列表)    
- [收藏夹内容](#收藏夹内容)    
- [添加作品到收藏夹](#添加作品到收藏夹)    
- [创建画册](#创建画册)    
- [其他人获取画册（只能看到公开的）](#其他人获取画册只能看到公开的)
- [用户获取画册（全部）](#用户获取画册全部)
- [创建主题](#创建主题)
- [获取主题列表](#获取主题列表)
- [获取某一个主题详情](#获取某一个主题详情) 
- [获取主题下图片列表](#获取主题下图片列表)
- [添加图片到主题](#添加图片到主题)
- [获取某个用户创建的主题列表](#获取某个用户创建的主题列表)
- [创建画画](#创建画画)
- [上传小文件接口（仅限于画画、头像、封面）](#上传小文件接口仅限于画画头像封面)
- [查看某一幅画详情](#查看某一幅画详情) 
- [搜索作品](#搜索作品) 
- [搜索用户](#搜索用户)

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

#### 检验姓名是否存在（接口）

```
GET /api/v1/user/register/checkname
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

#### 检验邮箱是否存在（接口）

```
GET /api/v1/user/register/checkemail
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

#### 获取账户验证码
```
GET /api/v1/user/register/getcode
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

#### 验证用户验证码
```
GET /api/v1/user/register/checkcode
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

## 修改用户信息

**接口**
```
POST /api/v1/user/modifymsg
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

## 收藏夹内容

**接口**
```
GET /fav/content
```
**请求头部**
```
"Authorization": "用户的token"
```
**请求参数**
```
"fav_id": 5  //  收藏夹ID
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

## 添加作品到收藏夹

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
"fav_id": 5,         // 收藏夹id号
"pic_id": 39,        // 图片id号
```
**返回内容**
```
{
	"code": 200,
	"msg": "success",
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

## 创建画画

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
"track_path": 这里需要调用上传视频的api，得到上传后返回的视频存储路径，再填写
```
**请求参数**
```
"picture_name": "画画名字",
"picture_intro": "画画的介绍",
"public_status": 0为私密，1为公开，
"album_id": 3
"label_name": ["标签一","标签二"],
"picture_path": "画存储的路径"
"type": "picture"
"track_path": "视频存储路径"
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









