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
让用户能够在地图上分享和寻找自己感兴趣的照片

# 目标
前期目标：用户可以上传图片到地图，并自动标记在地图上，也可以上传图片在地图上搜索是否有相似的图片
后期目标：让用户可以查看附近的图片，以自己为中心产生相册地图

# 背景和战略契合处
## 背景
随着智能手机和移动互联网的发展，用户产生照片的频次越来越高，用户对于分享的渴望也越来越高，市面上还没有以地理为单位的分享照片的APP，而分享与搜索则是交流的核心
## 战略契合
需要运用到静态地图和相似图片搜索的功能，将用户上传的图片在地图上显示，将用户搜索的相似图片在地图上显示，将用户周围的图片在地图上显示
# 假设条件
* 用户拍了张照片想分享到地图上
* 用户看到张图感兴趣想搜索是哪儿
* 用户想知道周围有什么人拍的什么地方的照片
# 需求
|No.|标题|用户案例|重要歌词|
|---|---|---|---|
|1|分享|今天在武当山顶，好不容易登顶了，拍了一张照片，觉得还不错上传到了APP上，图片出现在了武当山的地图上|重要|
|2|搜索|今天在朋友圈看到张武当山顶的图片感觉还不错，上传到APP上，搜索出了别人上传的武当山顶，虽然拍摄时间啥的不同，但经典的风景角度仍然可以认出来|重要|

#  使用者交互及设计
* 用户上传的图片会被标记在地图上
* 用户可以通过中间的+号上传图片
* 用户可以通过右下角的搜索搜索图片
![APP界面](https://github.com/yly49930454/final_APP/blob/master/media/%E6%88%AA%E5%B1%8F2019-12-11%E4%B8%8A%E5%8D%8810.19.40.png)
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
