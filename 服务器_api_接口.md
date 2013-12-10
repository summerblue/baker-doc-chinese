# 服务器 API 接口

在 App 端看来, 需要服务器端做以下接口

* 提供 `shelf.json` 文件, 做杂志期刊列表; 
* 接受 `Divice Token` 的接口;

## 通用的请求参数

### app_id

应用的 ID , 用来区分 App 的, 还记得不, Vogue , Self , GQ 都需要使用同一个接口, 此 ID 为 App 的 `Bundle ID` , 如: com.condenast.vogue10plus

### user_id

所谓的用户 ID , 是 App 上自动生成的随机字串, 用来跟踪独立用户使用的, 以后的统计上会用到. 

> 注意: 当用户删除并重装 App 的时候, 此 ID 会重置. 

### environment

environment 可以用来辨别客户端的属性, 选项见以下, 在测试的时候会特别有用, 如在 debug 情况下, 返回一些测试数据. 

* dubug 当 preprocessor 设置 DEBUG 的时候, 默认会发送此属性; 
* production 生产环境
* staging 上线前调试

## shelf.json 文件


Constants.h 文件下, 定义了 URL 路径

	GET <NEWSSTAND_MANIFEST_URL> 
	
Request parameters

* app_id
* user_id
* environment


## APNS device token

Constants.h 文件下, 定义了 URL 路径

	POST <POST_APNS_TOKEN_URL>
	
Request parameters

* app_id
* user_id
* environment 
* apns_token: the APNS device token