# Push Notification 说明

## 收集 Token 

App 会在每一次启动的时候, 请求服务器接口, 把 Divice Token 发送给服务器; 

## 发送 Push Notification, 让 App 下载最新的期刊 

	{
	    "aps": {
	        "content-available": 1
	    }
	}

App 接收到以上信息后, 会自动下载最新一起的期刊. 

## 发送 Push Notification, 让 App 下载特定的期刊 


	{
	    "aps": {
	        "content-available": 1
	    },
	    "content-name": "VogueIssue36"
	}
	
App 接收到以上信息后, 会自动下载指定的, 如此例子 `VogueIssue36` . 

## 注意

做后台下载的 Push Notification 需要知道以下: 

* 24 小时内, 后台下载只能发生一次. 开发的时候可以修改文件 `AppDelegate.m` 开启 `NKDontThrottleNewsstandContentNotifications` , 修改示例代码为以下: 

		- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
		{
		    [[NSUserDefaults standardUserDefaults] setBool:YES forKey:@"NKDontThrottleNewsstandContentNotifications"];
		    ...
	
	
* 可以自定义 ` notification payload ` 来扩展 App 接收到 remote 时候的信息 (如以下, 当然自定义字段需要 app 开发对于的功能), 需要注意的是, 不要在 `aps` key 下添加自定义的字段, `aps` key 放的是 Apple 定义的信息. 

		
		{
		    "aps": {
		        "content-available": 1
		    },
		    "test_key": "testing value"
		}
		
* payload 不能超过 256 个 字符. 