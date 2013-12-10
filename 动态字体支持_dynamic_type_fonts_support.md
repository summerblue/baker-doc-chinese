# 动态字体支持 Dynamic type fonts support

## 支持 Dynamic Type

iOS7 允许用户可以设置系统字体大小 `Settings -> General -> Text Size` , 这是新属性  Dynamic Type 的支持, 见 [Text Kit](https://developer.apple.com/library/ios/documentation/StringsTextFonts/Conceptual/TextAndWebiPhoneOS/CustomTextProcessing/CustomTextProcessing.html#//apple_ref/doc/uid/TP40009542-CH4-SW1).

想在 HTML 中支持  Dynamic Type 的话, 可以使用 `-apple-system-*`  进行 CSS 样式定制. 

	<div style="font:-apple-system-headline">This is the headline...</div>
	<div style="font:-apple-system-body">...and this is a body</div>
	
上面的文字使用此方式定义 CSS 的 font , 可以允许和 App 使用同一套 `font-family`, 样式, 还有大小. 


## 高级用法

可以使用 CSS 的 	override 属性来重写默认提供的字体属性, 如以下, 继承其他的如 `font-size` , 但是重写 `font-family`

	<div style='font:-apple-system-headline; font-family:"BodoniSvtyTwoITCTT-Book"'>This is the headline...</div> 
	

或者可以写为以下: 

		
	<div style="font:-apple-system-headline">
	  <div style="font-size:2em">This is the headline...</div>
	</div>