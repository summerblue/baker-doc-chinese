# 如果打包一个 HPub 文件;


## 准备材料

首先, HPub包 可以想为一个独立的小 HTML5 网站. 

开发的时候可以利用 Mobile Safari 进行开发, 甚至是, 你可以使用桌面比较新颖的浏览器如 Chrome 进行查看, 当然, 会少一些和 Native App 交互的一些功能, 但是渲染还是差不多的. 

`index.html` 是双击屏幕的时候调用, 如 minimap 的功能. 

## 打包

文件列表为以下: 

	$ tree . -L 1 --dirsfirst
	.
	├── fonts
	├── images
	├── js
	├── sounds
	├── styles
	├── Cover.html
	├── Interactivity.html
	├── Introduction.html
	├── Maps.html
	├── Structure_and_Columns.html
	├── book.json
	└── index.html

### 文件说明


    ├── fonts                      => 字体文件夹
    ├── images                     => 图片文件夹
    ├── js                         => JavaScript 文件夹
    ├── sounds                     => 语音文件存放目录
    ├── styles                     => 样式文件存放目录
    ├── Cover.html                 => 在本杂志里面, 为cover 的意义, 顺序在 book.json 定义
    ├── Interactivity.html         => 文章之一
    ├── Introduction.html          => 文章之一
    ├── Maps.html                  => 文章之一
    ├── Structure_and_Columns.html => 文章之一
    ├── book.json                  => 这个文件很重要, 定义了很多东西, 如顺序等, 见专门的说明
    └── index.html                 => 是双击屏幕的时候调用, 如 minimap 的功能.

## 打包格式

把所有文件打包成为一个 `zip 文件` , 注意, 把所有文件夹和文件打包, 而不是把文件存放的文件夹打包. 
	
	$ unzip -l laker.hpub
	Archive:  laker.hpub
	  Length     Date   Time    Name
	 --------    ----   ----    ----
	      735  11-22-13 14:37   book.json
	     4644  04-11-12 04:22   Cover.html
	        0  11-22-13 12:39   fonts/
	        0  11-22-13 12:39   fonts/oswald/
	    20002  04-11-12 04:22   fonts/oswald/oswald-webfont.eot
	    67540  04-11-12 04:22   fonts/oswald/oswald-webfont.svg
	    . . . 
	    

## 注意

因为所有的内容事实上就是一个离线的 HTML5 小网站, 所以, 所有的资源都要做好离线处理, 并保证内部链接使用 `相对路径`
	    
	    
	    
	
