# HPub 1.0 定义


## 抽象概念

HPub (HTML Publication)  标准, 是一个文件格式, 定义了以包的概念来管理和打包 Book, Book 由多个 html 文件组成, 每个 html 文件为一篇文章, 包里面的资源为完全独立, 可以想象为离线的 HTML5 minisite. 

## 标准

* 一个 HPub 包为一个通常的 .zip 包, 后缀名改为 .hpub ;
* 内容格式必须为 HTML5;
* 必须包含文件 `book.json` , 名字必须是一模一样的, 属性设置见 章节 `book.json 说明`; 
* 所有的 assets 文件 (css, images, js, …) 都必须打包起来, 在 HTML文件里, 以相对路径引用; 
* 可选的, index.html 文件用来做所有文字的列表, 导航主页;


## book.json 说明

文件 `book.json` 内容格式必须为 [json](http://www.json.org/) 文件 

### 最小内容的 book.json 示例: 


	{
	  "title": "Vogue 10+ 第 36 刊",
	  "author": "Vogue编辑",
	  "url": "book://bakerframework.com/books/arthurconandoyle-thestudyinscarlet",
	
	  "contents": [
	    "Article-1.html",
	    "Article-2.html",
	    "Article-3.html",
	    "Article-4.html",
	    "Article-5.html"
	  ]
	}
	
### 以下是一个完整的 book.json 示例: 
	
	
	{
	  "hpub": 1,
	  "title": "Vogue 10+ 第 36 刊",
	  "author": "Vogue编辑",
	  "creator": ["D. Casali", "M. Colombo", "A. Morandi", "F. Fortes"],
	  "publisher": "Baker Pubs",
	  "date": "2011-08-23",
	  "url": "book://bakerframework.com/books/arthurconandoyle-thestudyinscarlet",
	  "cover": "images/cover1.png",
	
	  "orientation": "both",
	  "zoomable": false,
	
	  "-baker-background": "#000000",
	  "-baker-vertical-bounce": true,
	  "-baker-index-bounce": true,
	  "-baker-index-height": 150,
	  "-baker-media-autoplay": true,
	
	  "-treesaver-loopArticles": "true",
	
	  "contents": [
	    "Book Cover.html",
	    "Book Index.html",
	    {
	        "url": "Front-Article.html",
	        "title": "The Wonders of Hpub",
	        "author": "The community"
	    },
	    "Part1-01.html",
	    "Part1-02.html",
	    "Part1-03.html",
	    "Part1-04.html",
	    "Part1-05.html",
	    "Part1-06.html",
	    "Part1-07.html",
	    "Part2-01.html",
	    "Part2-02.html",
	    "Part2-03.html",
	    "Part2-04.html",
	    "Part2-05.html",
	    "Part2-06.html",
	    "Part2-07.html",
	    "Colophon.html"
	  ]
	}
	
### 必备参数
	
#### title ( string ): 

杂志的标题.
	
#### author ( string|array ): 

杂志的作者

#### url ( string ): 

Book 的唯一标示符, 使用 book:// 协议

#### contents ( array ): 

文章列表, 这里的顺序就是文章的顺序. 为文件的名称, 或者是加上 `hash` 的文件的名称.  


### 可选参数

#### hpub ( number, default: 1 ): 

hpub 标准的版本. 

#### creator ( string|array ): 

创建者, 谁编辑, 整理和发布了创建了此 数字化版本的 Book; 

#### publisher ( string ): 

出版社. 

#### date ( string ): 


Book 的发布时间, 也可以为编辑的修改时间, 格式必须为 "yyyy-mm-dd" (年, 月, 日: i.e. "2011-10-03").

#### orientation ( string, default: both ): 

支持设备的方向. 可选的选项为 "both", "portrait", "landscape", 注意要小写.

#### zoomable ( bool, default: false ): 

是否支持放大缩小. 

#### cover ( string ): 

封面图片, 相对路径.


## 扩展选项:



### 视觉属性

* -baker-background ( string, default: "#000000" ): 背景颜色, 点击进入 Book 的时候, 可以看到. 注意此属性仅仅当 `-baker-background-image-*` 没有设置的时候, 才能生效;
* -baker-background-image-portrait ( string ): 在竖屏模式下 , 点击进入 Book 时候, 会有一个过渡的 view , 这里可以设置此 view 的 Background. e.g. "book/background-portrait.png". 注意这里的分辨率为 768x1024 px;
* -baker-background-image-landscape ( string ): 横屏模式下, 如上 e.g. "book/background-landscape.png". 分辨率为 1024x768 px. 
* -baker-page-numbers-color ( string, default: "#FFFFFF" ): 当 loading 下一页的时候, 会有个数字和 title , 这里的设置可以修改默认的颜色. 
* -baker-page-numbers-alpha ( number, default: 0.3 ): 上面的属性, 加上透明效果. 
* -baker-page-screenshots ( string ) : 存放截屏文件的路径, 当 loading 下一页的时候, 对于顺序的截屏文件可以用来作为 placeholder, 让用户感觉加载很快, 文件名必须为 `screenshot-portrait-1.jpg` 这种格式, 支持横向屏幕的话使用 `screenshot-landscape-1.jpg`, `1` 为页码 (1, 2, 3, ...). 没有截图的情况下, app 不会自动生成这些截图, 可以考虑使用程序自动截图. 

### 行为属性

* -baker-rendering ( string, default: "screenshots" ): 可用的选项有 "screenshots" 和 "three-cards", 
	* screenshots App 自动截屏, 访问过的页面, 下次加载同一个页面的时候, 会提前加载此截屏, 给用户假象, 加载很快; 
	* three-cards 上一篇和下一篇文章提前加载, 如 当你在看 第 3 篇文章的时候, 第2, 4 文章都已经加载;
* -baker-vertical-bounce ( boolean, default: true ): 是否开启 `bounce` 的效果, 上下滑动到达底部或者顶部时的 `弹动` 效果;
* -baker-media-autoplay ( boolean, default: true ): 当用户打开一篇文章的时候, 是否自动播放此页面上得多媒体文件. (  UIWebView 可以看下此属性 mediaPlaybackRequiresUserAction ).
* -baker-vertical-pagination ( boolean, default: false ): 是否上线滑动的时候使用分页, 允许在 html 的 head 标签内利用以下代码来重写这个属性 <meta name="paged" content="YES"> .
* -baker-page-turn-tap ( boolean, default: true )  允许使用 tap 页面的左右来实现上下页的切换; 
* -baker-page-turn-swipe ( boolean, default: true ) 是否使用左右滑动的手势来实现上下页切换;



### Book 的相关属性

* -baker-index-height ( number, default: null ): index.html 文件, 也就是那个双击时出现导航栏的高度;
* -baker-index-width ( number, default: null ): index.html 文件, 也就是那个双击时出现导航栏的宽度;
* -baker-index-bounce ( boolean, default: false ): 同上, 设置 bounce 属性;
* -baker-start-at-page ( number, default: 1 ) 打开 book 时候的默认开始页面, 也可以设置为负数 (i.e. -baker-start-at-page: -1 or -baker-start-at-page: -2), 负数的情况下 app 会把书从倒序取出来. 