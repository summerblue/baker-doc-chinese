# 书架文件 self.json 的格式说明

## 作用

书架列表文件 `self.json` 是所有期刊类表的 json 文件, App 使用此文件来构架首页杂志列表.

此文件为服务器端维护, 作为期刊的入口, App 启动的时候会请求此接口, 以更新本地的数据. 

App 里文件 `Constants.h` 文件上 `NEWSSTAND_MANIFEST_URL` 定义了请求的 URL 地址. 

## 示例

	[
	  {
	    "name": "VogueIssue36",
	    "title": "Vogue 第 36 刊",
	    "info": "这里是第 36 刊的描述",
	    "date": "2013-07-10 10:10:10",
	    "cover": "http://www.condenastsub.com.cn/newsstand-books/VogueIssue36-cover.png",
	    "url": "http://www.condenastsub.com.cn//newsstand-books/VogueIssue36-cover.hpub",
	    "product_id": "com.condenast.Vogue10Plus.issues.36"
	  },
	  {
	     "name": "VogueIssue35",
	    "title": "Vogue 第 35 刊",
	    "info": "这里是第 35 刊的描述",
	    "date": "2013-06-10 10:10:10",
	    "cover": "http://www.condenastsub.com.cn/newsstand-books/VogueIssue35-cover.png",
	    "url": "http://www.condenastsub.com.cn//newsstand-books/VogueIssue35-cover.hpub",
	    "product_id": "com.condenast.Vogue10Plus.issues.35"
	  }
	  
	  ...
	  
	]
	
## 字段解释

### name ( string ):

此次期刊的唯一标示符 (unique identifier) , App 利用此名字来定义 `目录结构` 还有 `期刊的标记`, 此 ID 必须保证唯一性, 此属性用户不可见. 

### title ( string ):

期刊的标题. 

### date ( string ):

期刊的发布时间, App 使用此属性来排序 (最新的排在最上面), 格式是固定的 `YYYY-MM-DD HH:MM:SS` , 此属性用户不可见. 

### cover ( string ):

期刊的封面, 视乎是最重要的属性. 

### url ( string ):

格式为 HPub 包的杂志下载地址. 

### info ( string , optional):

期刊的基本描述, 可有可无. 

### product_id ( string, optional):

期刊的唯一标示符, 为 iTunes Connect 使用. 可有可无. 