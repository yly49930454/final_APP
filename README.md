# 相册地图APP PRD
# Product Requirements
|发布日期|2019.12.05|
|---|---|
|史诗|让用户能够在地图上分享和寻找自己感兴趣的照片|
|文件现状|进行中|
|文件的主人|叶立业|
|领头的设计师|叶立业|
|领头的开发者|叶立业|
|领头的测试者|叶立业|



# 加值宣言
加值功能为能够通过图片搜索其他用户上传的相似的图片，并显示在它上传图片时的地图上，调用了百度API的相似图片搜索API可以搜索自定义库里的图片，帮助用户找到他想找到的地方
# 核心价值


# 目标


# 背景和战略契合处

# 假设条件

# 需求
|No.|标题|用户案例|重要歌词|笔记|
|—|—|
|1|title|userstory|importance|notes|

#  使用者交互及设计

# API使用
1. 百度相似图像搜索API
* HTTP 方法：POST
* 请求URL：https://aip.baidubce.com/rest/2.0/image-classify/v1/realtime_search/similar/search
* API价值主张：相似图片搜索，可以建立一个本地的图像库，当用户上传时可以跟库里的图片进行比对，相似度最高的返回其的展品介绍
* API使用实例
``` python
import base64
f = open(‘th (1).png’, ‘rb’)
img = base64.b64encode(f.read())

import requests
host = ‘https://aip.baidubce.com/rest/2.0/image-classify/v1/realtime_search/similar/search’
headers={
   ‘Content-Type’:’application/x-www-form-urlencoded’
}
access_token= ’24.c95f780f275c859fa0463438cdc9ebda.2592000.1578373144.282335-17966623’
host=host+’?access_token=‘+access_token

data={}
data[‘access_token’]=access_token
data[‘image’] =img
res = requests.post(url=host,headers=headers,data=data)
req=res.json()
print(req[‘result’])
```
* API返回实例
``` 
{
    “result_num”: 1,
    “result”: [
        {
            “score”: 0.97976700290421,
            “brief”: “./data/jay1.jpg”,
            “cont_sign”: “475124309,1080176642”
        }
    ],
	“has_more”: “false”,
    “log_id”: 1968648150
}
```

# 问题

# 不做
