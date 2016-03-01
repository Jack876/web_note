###目录
- [1.字体与段落](#1.字体与段落)
	+ [首行缩进](#首行缩进)
	+ [首字下沉](#首字下沉)
	+ [文字，字符间距](#文字，字符间距)
	+ [文本溢出(单行)](#文本溢出)
	+ [文本溢出(多行)](#文本溢出2)
	+ [禁止选中文本](#禁止选中文本)

- [2.边框与图片](#2.边框与图片)
	+ [retina屏幕高清图片设置](#retina屏幕高清图片设置)
	+ [图片加载优化](#图片加载优化)
	+ [图片虚化](#图片虚化)
	+ [图片lomo效果](#图片lomo效果)

- [3.按钮与链接](#3.按钮与链接)
	+ [注重用户点击愉悦感](#注重用户点击愉悦感)

- [4.背景与颜色](#4.背景与颜色)
	+ [对div进行裁切](#对div进行裁切)

- [5.变化与动画](#5.变化与动画)
	+ [增加ios移动端滑感](#增加ios移动端滑感)
	+ [动画特效加速（适当用）](#动画特效加速)

- [6.页面与布局](#6.页面与布局)
	+ [清除浮动](#清除浮动)
	+ [表格防止溢出](#表格防止溢出)
	+ [定位底部footer](#定位底部footer)
	+ [ios端fixed属性BUG解决方案](#ios端fixed属性BUG解决方案)

- [7.美化与装饰](#7.美化与装饰)
	+ [android隐藏原生滚动条](#android隐藏原生滚动条)

---

<h3 id="1.字体与段落">1.字体与段落</h3>

<h6 id="首行缩进"> ·首行缩进</h6>
```css
	p { text-indext:24px; }
```

<h6 id="首字下沉"> ·首字下沉</h6>
```css
	p:first-letter { float:left; }
```

<h6 id="文字，字符间距"> ·文字，字符间距</h6>
```css
	p {
		word-spacing:20px;				//空格长度
		letter-spacing:20px;			//字间距
		white-spacing:pre;				//保留多个空格
		white-space: nowrap;			//禁止换行
		white-space: pre-wrap;			//保留所有空格和回车
		white-space: pre-line;			//忽略多个空格为1个，保留回车
	}
```

<h6 id="文本溢出"> ·文本溢出(单行)</h6>
```css
	p { 
		white-space: nowrap;
		overflow:hidden;				
		overflow: ellipsis; 			//使用省略号
	}				
```

<h6 id="文本溢出2"> ·文本溢出(多行)</h6>
```css
	p { 
		display: -webkit-box;			//将对象作为弹性伸缩盒子模型显示
		text-overflow: ellipsis;		//多行文本的情况下，使用省略号
		-webkit-line-clamp: 2;          //限制行数
		-webkit-box-orient: vertical; 	//设置伸缩盒对象的子元素的排列方式
	}		
```

<h6 id="禁止选中文本"> ·禁止选中文本</h6>
```css
	p {
		-webkit-user-select:none;
	}
```

<h3 id="2.边框与图片"> 2.边框与图片</h3>

<h6 id="retina屏幕高清图片设置"> ·retina屏幕高清图片设置</h6>
- 不支持image-set：在不支持image-set的浏览器下，解析background-image中的背景图像；
- 支持image-set：支持image-sete，普通显屏下浏览器选择image-set中的@1x背景图像；
- Retina屏幕下的image-set：支持image-set，Retina屏幕下浏览器会选择image-set中的@2x背景图像。
```css
	div {
	  background-image: url(image.png);
	  background: image-set(url(image-normal.png) 1x,url(image-ritina.png) 2x) center;
	}
```

<h6 id="图片加载优化"> ·图片加载优化</h6>
除base64格式外，多用jpg，大图尽量避免png，相对jpg解析速度快。

<h6 id="图片虚化"> ·图片虚化</h6>
```css
	img {
		-webkit-filter: blur(3px);
		filter: blur(3px);
	}
```

<h6 id="图片lomo效果"> ·图片lomo效果</h6>
```css
	.lomo {
		position:relative;
		-webkit-filter: contrast(.9) sepia(.2);
    	filter: contrast(.9) sepia(.2);
	}
	.lomo:before,
	.lomo:after {
		content: '';
	    display: block;
	    height: 100%;
	    width: 100%;
	    top: 0;
	    left: 0;
	    position: absolute;
	    pointer-events: none;
	}
	.lomo:before {
		z-index:2;
	}
	.lomo:after {
		z-index:3;
		background: -webkit-radial-gradient(circle,#d0ba8e 20%,#360309 85%,#1d0210 100%);
	    background: radial-gradient(circle,#d0ba8e 20%,#360309 85%,#1d0210 100%);
	    mix-blend-mode: overlay;
	}
	img {
		display: block;
		width: 100%;
    	z-index: 1;
	}
```
html代码
```html
	<figure class="lomo">
    	<img src="image.jpg">
    </figure>
```

<h3 id="3.按钮与链接"> 3.按钮与链接</h3>

<h6 id="注重用户点击愉悦感"> ·注重用户点击愉悦感</h6>
- 增大导航菜单项的内边距
- 增大可点击范围（40px）
- 增大页面和内容块的外边距
- 增加表单输入框的大小和间距

<h3 id="4.背景与颜色"> 4.背景与颜色</h3>

<h6 id="对div进行裁切"> ·对div进行裁切</h6>
```css
	div { clip-path: url("#cp"); } 		//#cp为svg
```

<h3 id="5.变化与动画"> 5.变化与动画</h3>

<h6 id="增加ios移动端滑感"> ·增加ios移动端滑感</h6>
```css
	div{ -webkit-overflow-scrolling : touch; }
```

<h6 id="动画特效加速"> ·动画特效加速（适当用）</h6>
```css
	.div {
		-webkit-transform: translate3d(0, 0, 0);
		-moz-transform: translate3d(0, 0, 0);
		-ms-transform: translate3d(0, 0, 0);
		transform: translate3d(0, 0, 0);
	}
```

<h3 id="6.页面与布局">6.页面与布局</h3> 

<h6 id="清除浮动"> ·清除浮动</h6>
```css
	.clear:after {
		content: "."; 
		display: block; 
		clear: both; 
		visibility: hidden; 
		line-height: 0; 
		height: 0; 
	}
```

<h6 id="表格防止溢出"> ·表格防止溢出</h6>
```css
	table { table-layout:fixed; }
	td { word-break: break-all; }
```

<h6 id="定位底部footer"> ·定位底部footer</h6>
```css
	.con {
		min-height: 100%;
		margin-bottom: -150px; 
	}
	.con:after {
		content: "";
		display: block;
	}
	.footer, .con:after {
		height: 150px; 
	}
```

<h6 id="ios端fixed属性BUG解决方案"> ·ios端fixed属性BUG解决方案</h6>
```css
	.con {								//.con为主体内容容器
		position:fixed;					//或absolute
		top:50px;
		bottom:50px;
		width:100%;
		overflow:scroll;
		-webkit-overflow-scrolling : touch;
	}
```

<h3 id="7.美化与装饰"> 7.美化与装饰</h3>

<h6 id="android隐藏原生滚动条">·android隐藏原生滚动条</h6> 
android
```css
	::-webkit-scrollbar{
	    opacity: 0;
	}
```
