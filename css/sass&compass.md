**`目录`**

- [安装、使用](#安装、使用)
	+ [安装ruby](#安装ruby)
	+ [安装sass&compass](#安装sass&compass)
	+ [使用](#使用)
- [sass常用语法](#sass常用语法)
	+ [声明变量](#声明变量)
	+ [语法嵌套](#语法嵌套)
	+ [声明混合宏](#声明混合宏)
	+ [继承](#继承)
	+ [占位符%](#占位符%)
	+ [注意事项](#混合宏 VS 继承 VS 占位符)
- [compass常用语法](#compass常用语法)
	+ [reset模块](#reset模块)
	+ [layput模块](#layput模块)
	+ [browser模块](#browser模块)
	+ [css3模块](#css3模块)
	+ [helpers模块](#helpers模块)
	+ [typography模块](#typography模块)
	+ [utilities模块](#utilities模块)
- [视频教程]()
	+ [sass(1小时33分)](http://www.imooc.com/learn/364)
	+ [compass(2小时41分)](http://www.imooc.com/learn/371)

---

<h2 id="安装、使用">安装、使用</h2>


<h4 id="安装ruby">安装ruby</h4>
<h6>windows系统</h6>

> 使用cmd指令前先安装[ruby(windows版)](http://rubyinstaller.org/downloads/)即可

<h6>os x系统</h6>

> 打开cmd工具安装brew： /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

> 通过[cakebrew](https://www.cakebrew.com/)(brew可视化工具)安装gpg：
all formulae中搜索gnupg并安装gnupg2

> 打开cmd工具安装rvm，先输入： gpg2 --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
等待安装完毕后再输入： \\curl -sSL https://get.rvm.io | bash -s stable
(整个过程如有失败可能需要翻墙)

<br>

**`rvm使用指令`**
<table>
	<tbody>
		<tr>
			<td>rvm list known</td>
			<td>查看当前ruby可用版本</td>
		</tr>
		<tr>
			<td>rvm list</td>
			<td>已安装的ruby版本</td>
		</tr>
		<tr>
			<td>rvm install 2.2.1</td>
			<td>安装指定版本的ruby</td>
		</tr>
		<tr>
			<td>rvm use 2.0.0</td>
			<td>默认使用某版本ruby</td>
		</tr>
	</tbody>
</table>

<br>

<h4 id="安装sass&compass">安装sass&compass</h4>

cmd指令|说明
-----|-----
gem sources --remove https://rubygems.org/ | 移除旧源（国内网络原因）
gem sources -a https://ruby.taobao.org/ | 添加淘宝源
gem sources -l | 查看当前现有源
gem install sass | 安装[sass](http://sass-lang.com/)
gem install sass --version=3.3.0 | 安装指定版本sass
gem list | 列出gem本地所有程序包
gem uninstall sass --version=3.3.0 | 删除指定版本sass
gem install compass | 安装[compass](http://compass-style.org/reference/compass/)
gem install compass-normalize | 安装normalize插件（sass语法增强）

<br>

<h4 id="使用">使用</h4>
> 指定目录下打开cmd窗口使用指令。

windows系统写代码过程转译会有乱码或报错的情况，找到engine.rb文件（一般位于Ruby22\lib\ruby\gems\2.2.0\gems\sass-3.4.18\lib\sass目录下面），在所有的require后面新增如下代码：**Encoding.default_external = Encoding.find('utf-8')**

cmd指令 | 说明
-----|-----
compass create 文件名 | 在指定文件夹创建compass目录
sass main.cscc main.css | 转译scss文件（scss/sass文件目录下使用）
compass watch | 实时监听scss文件，自动转译（compass根目录下）
compass compile | 输出css,配置在config.rb中（例压缩模式：13行中添加output_style = :compressed）


---
<h2 id="sass常用语法">sass常用语法</h2>
`统一文件后缀名.scss`


<h6 id="声明变量"> ·声明变量</h6>

```sass
$width:500px;
```	  
<br>


<h6 id="声明默认变量"> ·声明默认变量</h6>

```sass
$width:500px !default;
```

> 默认变量用来设置默认变量，根据需求覆盖，覆盖时重新声明默认变量即可	  

<br>

<h6 id="语法嵌套"> ·语法嵌套</h6>

```sass
a {
  	color：red;
      	&:before {
     	content:””
  	}
  	body & {
		color:blue;
  	}
}
```	  
<br>


<h6 id="声明混合宏"> ·声明混合宏</h6>
```sass
@mixin border-radius($radius) {
	-webkit-border-radius:$radius;
	border-radius:$radius;
}
```
> $radius也可以给一个默认值，如@mixin border-radius($radius:50%)

调用混合宏
```sass
button {
	@include border-radius(5px);
}
```	  
<br>


<h6 id="多个参数的混合宏"> ·多个参数的混合宏</h6>
```sass
@mixin center($width,$height){
	width: $width;
	height: $height;
	position: absolute;
	top: 50%;
	left: 50%;
	margin-top: -($height) / 2;
	margin-left: -($width) / 2;
}
```

调用
```sass
div {
	@include center;
}
```
> 混合宏的缺点是会造成过多冗余的代码，sass不会智能合并  

<br>


<h6 id="继承"> ·继承</h6>
```sass
.btn {
	border: 1px solid #ccc;
	padding: 6px 10px;
	font-size: 14px;
}

.btn-primary {
	background-color: #f36;
	color: #fff;
	@extend .btn; //继承.btn所有属性
}
```	  
<br>


<h6 id="占位符%"> ·占位符%</h6>
```sass
%mt5 { margin-top: 5px; }
%pt5{ padding-top: 5px; }

.btn {
	@extend %mt5;
	@extend %pt5;
}

.block {
@extend %mt5;
	span {
		@extend %pt5;
	}
}

```
输出结果：
```css
.btn, .block { margin-top: 5px; }
.btn, .block span { padding-top: 5px; }
```
> %placeholder 声明的代码，如果不被 @extend 调用的话，不会产生任何代码。与$不同的是它可以合并代码。  	  

<br>


<h6 id="混合宏 VS 继承 VS 占位符"> ·混合宏 VS 继承 VS 占位符</h6>
- 如果你的代码块中涉及到变量，建议使用混合宏来创建相同的代码块；
- 如果不需要任何参数，且有一个基类已在文件中存在，那么建议使用 Sass 的继承。  	  

<br>


<h6 id="注释"> ·注释</h6>
//不会被编译，/\*\*/会被编译; 	
如想保留压缩版的注释，在首个*号后加!  

<br>


<h6 id="运算"> ·运算</h6>
- 被乘除数后不能加单位；
- 减号前面要加空格，除号/要在公式外加括号（）；
- 复杂的公式同正常数学一样用（）表明先后  

<br>

<h2 id="compass常用语法">compass常用语法</h2>
> 注:compass中只有reset和layout模块是要单独引用的，如 @import "compass/reset"  @import "compass/layout"。其他5大模块引用@import "compass"即可;

> 如需引用normalize模块，config.rb文件2行加入：
```ruby
require 'compass-normalize'
```

<br>

<h6 id="reset模块">reset模块</h6>
浏览器样式重置模块，如需单独加载reset某模块，参考：[参考文档](http://compass-style.org/reference/compass/reset/utilities/)

<br>

<h6 id="layout模块">layout模块</h6>
页面布局模块。[参考文档](http://compass-style.org/reference/compass/layout/)
> **stretch($top, $right, $bottom, $left)**  `默认值:(0,0,0,0)`
```css
div {
	position: absolute;
	top:$top;
	right: $right;
	bottom: $bottom;
	left: $left;
}
```

<br>

> **sticky-footer($height, #root, #root-footer, #footer)**
```html
<style>
	html,body{ height:100%; }
	#root {
		clear: both;
		min-height: 100%;
		height: auto !important;
		height: 100%;
		margin-bottom: $height;
	}
	#root-footer { height: $height;}
	#footer {
		clear: both;
		position: relative;
		height: $height;
	}
</style>
<body>
  <div id="root">
    <div id="root_footer"></div>
  </div>
  <div id="footer"></div>
</body>
```

<br>

<h6 id="browser模块">browser模块</h6>
配置compass默认支持哪些浏览器,scss文件中输入@debug browsers()查看当前支持。[参考文档](http://compass-style.org/reference/compass/support/)
```sass
/*设置需要支持哪些浏览器*/
$supported-browsers:chrome,firefox;

/*最低要求需要支持到哪个版本*/
$browser-minimum-versions:("ie":"8");
```

<br>

<h6 id="css3模块">css3模块</h6>
跨浏览器的css3能力。[参考文档](http://compass-style.org/reference/compass/css3/animation/)

**使用方法：**`@include box-shadow(1px 1px 5px rgba(0,0,0,.5));`


| 常用支持属性 | 备注    |
| :------------- | :------------- |
| animation       |        |
| background-size       |        |
| border-radius       |        |
| box-shadow       |        |
| box-sizing       |        |
| css3 pie       |  需要额外安装插件      |
| columms       |        |
| filter      |        |
| flexbox       |        |
| font-face       |        |
| opacity       |        |
| text-shadow       |        |
| inline-block       |        |
| transform       |        |
| transition       |        |


<br>

<h6 id="helpers模块">helpers模块</h6>
函数模块。[参考文档](http://compass-style.org/reference/compass/helpers/)

<br>

<h6 id="typography模块">typography模块</h6>
主要修饰文本样式。[参考文档](http://compass-style.org/reference/compass/typography/)
> **hover-link**
```sass
@mixin hover-link {
  text-decoration: none;
  &:hover, &:focus {
    text-decoration: underline;
  }
}
```

<br>

> **link-colors($normal, $hover, $active, $visited, $focus)**
默认值可以只传$normal(标签常态下color值);

<br>



<h6 id="utilities模块">utilities模块</h6>
函数模块，与helper不同的是主要是mixin。[参考文档](http://compass-style.org/reference/compass/utilities/)

> **legacy-pie-clearfix**`清除浮动`
```css
div:after {
	content: "\0020";
	display: block;
	height: 0;
	clear: both;
	overflow: hidden;
	visibility: hidden;
}
```

<br>

**sprite功能使用**
```sass
/*将file文件夹下所有png合为一张图*/
@import "file/*.png";

/*url自动定位,filename只取最后一个路径的名字*/
@include all-[filename]-sprites();

/*使用背景图,class名在编译后的css文件里找*/
<div class="图片class名"></div>

/*使用同一个背景图片*/
@include logo-sprite("图片class名(不用加.)");
```
> 如有hover修饰，在对应图片名后加上_hover或_active即可
