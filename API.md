# API

### 用户登录

```
POST /paint/api/v1/login
```

参数
```
account: "123456"
password: "123456"
```

返回
```
{
	"code": 200,
	"msg": "success",
	"data": {
		"user_id": "abdcd",  //用户获取其他信息的唯一标识
		"nickname": "北风那个吹",
		"address": "地址"
		"phone": "123456"
		"sex": 0
		"introduction": "aaa"
		"likes": 123
		"avatar": "aaa"
	}
}
```

### 收藏夹
```
GET /paint/api/v1/favlist
```

参数
```
user_id: "abdcd"
```

返回
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"id": "用户收藏夹id",
			"fav_name": "收藏夹名称1",
			"fav_intro": "收藏夹简介",
			"sum": 10,
			"public_status": 0
		},

		{
			"id": "用户收藏夹id",
			"fav_name": "收藏夹名称2",
			"fav_intro": "收藏夹简介",
			"sum": 5,
			"public_status": 1
		},
	]
}
```

### 收藏夹内容
```
GET /paint/api/v1/colletion
```

参数
```
fav_id: "2312412"
```

返回
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"id": "1"
			"col_name": "画画名称",
			"col_path": "http://www.weixiaoyuan.xyz/picture/xxx.png"
			"col_time": "2020-2-3"
			"picture_id": "22344"
		}
	]
}
```


### 用户注册
```
POST /paint/api/v1/register
```

参数
```
email: "123456@163.com"
nickname: "北风那个吹"
password: "123456"
repassword: "123456"
verifycode: "atsd"
```

返回
```
{
	"code": 200,
	"msg": "success",
	"data": {
		"decription": "注册成功！"
	}
}
```
```
{
	"code": 200,
	"msg": "error",
	"data": {
		"error_code": "1001",
		"description": "该账号已注册"
	}
}
```

### 用户名验证
```
GET /paint/api/v1/nickname
```

参数
```
nickname: "北风那个吹"
```
返回
```
{
	"code": 200,
	"msg": "success",
	"data": {
		"description": "该用户名可用"
	}
}
```

```
{
	"code": 200,
	"msg": "error",
	"data": {
		"description": "该用户名已被占用"
	}
}
```

### 轮播图
```
GET /paint/api/v1/carousel
```

参数
```
无
```
返回
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"id": "1234",
			"img_path": "/img/1.png"
			"img_intro": "jianjie"
			"img_href": "http://www.weixiaoyuan.xyz/static/img/1.png"
			"use_status": 1
		}
	]
}
```
### 公告
```
GET /paint/api/v1/annoucement
```

参数
```
start: 0
end: 10,
num: 10
```

返回
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"id": 1,
			"title": "标题",
			"content": "内容",
			"create_time": "2020-02-02".
			"likes": 200
		},
		{
			"id": 2,
			"title": "标题",
			"content": "内容",
			"create_time": "2020-02-02".
			"likes": 200
		}
	]

}
```




### 社区推荐
```
GET /paint/api/v1/community
```

参数
```
无
```
返回
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"id": "1234",
			"picture_name": "画画的名称"
			"picture_path": "http://www.weixiaoyuan.xyz/picture/223.png"
			"likes": 123,
			"picture_id": “1234”
		}
	]
}
```
### 画详情页
```
GET /paint/api/v1/picture
```

参数
```
picture_id: 2
```

返回
```
{
	"code": 200,
	"msg": "success",
	"data": {
		"id": 1,
		"picture_name": "画画名称",
		"picture_intro": "画画简介",
		"picture_path": "http://www.weixiaoyuan.xyz/img/picture.png",
		"picture_status": 0,
		“track_path”: "http://www.weixiaoyuan.xyz/redraw/12345.xml",
		"likes": 123,
		"label": "彩绘",
		"theme": "进击的巨人",
		"album": "第一个画册",
		"user": {
			"user_id": "abdcd",  //用户获取其他信息的唯一标识
			"nickname": "北风那个吹",
			"address": "地址"
			"phone": "123456"
			"sex": 0
			"introduction": "aaa"
			"likes": 123
			"avatar": "http://www.weixiaoyuan.xyz/user/avatar.png"
		}
		"create_time": "2020-02-01"
	}
}
```

### 所有画
```
GET /paint/api/v1/all
```

参数
```
// 每一页加载20条数据
type: all
start: 0,
end: 20,
num: 20
```
返回
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"picture_name": "画画名称",
			"picture_intro": "画画简介",
			"picture_path": "http://www.weixiaoyuan.xyz/img/picture.png",
			"label": "彩绘",
			"theme": "进击的巨人1",
			"author": "北风那个吹"
			"create_time": "2020-02-01"
		},
		{
			"picture_name": "画画名称",
			"picture_intro": "画画简介",
			"picture_path": "http://www.weixiaoyuan.xyz/img/picture.png",
			"label": "彩绘",
			"theme": "进击的巨人2",
			"author": "北风那个吹"
			"create_time": "2020-02-01"
		}
	]
}
```

### 标签搜索
```
GET /paint/api/v1/all
```

参数
```
// 每一页加载20条数据
type: label
start: 0,
end: 20,
num: 20
```
返回
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"picture_name": "画画名称",
			"picture_intro": "画画简介",
			"picture_path": "http://www.weixiaoyuan.xyz/img/picture.png",
			"label": "彩绘",
			"theme": "进击的巨人1",
			"author": "北风那个吹"
			"create_time": "2020-02-01"
		},
		{
			"picture_name": "画画名称",
			"picture_intro": "画画简介",
			"picture_path": "http://www.weixiaoyuan.xyz/img/picture.png",
			"label": "彩绘",
			"theme": "进击的巨人2",
			"author": "北风那个吹"
			"create_time": "2020-02-01"
		}
	]
}
```

### 时间排序
```
GET /paint/api/v1/all
```

参数
```
// 每一页加载20条数据
type: time
start: 0,
end: 20,
num: 20
```

返回
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"picture_name": "画画名称",
			"picture_intro": "画画简介",
			"picture_path": "http://www.weixiaoyuan.xyz/img/picture.png",
			"label": "彩绘",
			"theme": "进击的巨人1",
			"author": "北风那个吹"
			"create_time": "2020-02-02"
		},
		{
			"picture_name": "画画名称",
			"picture_intro": "画画简介",
			"picture_path": "http://www.weixiaoyuan.xyz/img/picture.png",
			"label": "彩绘",
			"theme": "进击的巨人2",
			"author": "北风那个吹"
			"create_time": "2020-02-01"
		}
	]
}
```

### 每周推荐榜
```
GET /paint/api/v1/recommend
```

参数
```
无
```

返回
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"picture_id": "123"
			"picture_name": "画画名称",
			"picture_path": "http://www.weixiaoyuan.xyz/img/picture.png",
			"likes": 200
		}
	]
}
```

### 人气画家榜
```
GET /paint/api/v1/recommend
```

参数
```
无
```

返回
```
{
	"code": 200,
	"msg": "success",
	"data": [
		{
			"user_id": "123"
			"user_avatar": "用户头像路径",
			"nickname": "北风那个吹",
			"likes": 200,
		}
	]
}
```






