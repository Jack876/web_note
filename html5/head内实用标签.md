**`目录`**

- [移动端](#移动端)
	+ [移动端禁止缩放](#移动端禁止缩放)
	+ [禁止字符转链接](#禁止字符转链接)
	+ [webApp设置](#webApp设置)
- [pc端](#pc端)
	+ [指定浏览器内核渲染](#指定浏览器内核渲染)
	+ [网页标题栏icon](#网页标题栏icon)
	+ [seo关键字&描述](#seo关键字&描述)
	+ [判断ie版本](#判断ie版本)
- [通用](#通用)
	+ [自动跳转刷新](#自动跳转刷新)
	+ [去除代码缓存](#去除代码缓存)

---

<h3 id="移动端">移动端</h3>

<h6 id="移动端禁止缩放"> ·移动端禁止缩放</h6>
```html
	<meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no">
```
> width：viewport的宽度; 
 height：viewport的高度;   
 initial-scale：初始的缩放比例;
 minimum-scale：允许用户缩放到的最小比例;   
 maximum-scale：允许用户缩放到的最大比例;  
 user-scalable：用户是否可以手动缩放。 
 有emmet插件的编辑器内简写"meta:vp"加tab键。

<br>

<h6 id="禁止字符转链接"> ·禁止字符转链接</h6>
```html
<!-->不识别手机号<-->
<meta name="format-detection" content="telephone=no">
<!-->不识别邮箱<-->
<meta name="format-detection" content="email=no">
```
<br>

<h6 id="webApp设置"> ·webApp设置</h6>
```html
<!-->开启webApp功能<-->
<meta name="apple-mobile-web-app-capable" content="yes">

<!-->全屏显示webApp<-->
<meta name="apple-touch-fullscreen" content="yes">

<!-->webApp屏幕顶部条的颜色,可选black,black-translucent,默认白色<-->
<meta name="apple-mobile-web-app-status-bar-style" content="black">

<!-->webApp的启动图标,图片尺寸57x57,rintina:117x117,ipad:72x72<-->
<link rel="apple-touch-icon-precomposed" href="webApp/appIcon57.png"/>
<link rel="apple-touch-icon-precomposed" sizes="72x72" href="webApp/appIcon72.png"/>
<link rel="apple-touch-icon-precomposed" sizes="114x114" href="webApp/appIcon114.png"/>

<!-->webApp的启动界面，尺寸320x640<-->
<link rel="apple-touch-startup-image" href="webApp/startup.png" />
```
<br>

<h3 id="pc端">pc端</h3>

<h6 id="指定浏览器内核渲染"> ·指定浏览器内核渲染</h6>
```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```
> 使用最高版本的ie内核进行渲染。

<br>

<h6 id="网页标题栏icon"> ·网页标题栏icon</h6>
```html
<link rel="short icon" style="image/x-icon" href="logo.ico">
```
> [在线ico转换工具](http://www.ico.la/)

<br>

<h6 id="seo关键字&描述"> ·seo关键字&描述</h6>
```html
<meta name="keywords" content="搜索关键词1，关键词2（5个左右）">
<meta name="description" content="网页描述文字（150字左右）">
```
<br>

<h6 id="判断ie版本"> ·判断ie版本</h6>
```html
<!--[if lte IE 8]>
	do something
<![endif]-->
```
>lte:小于或等于;
 lt :小于;
 gte:大于或等于;
 gt :大于;
 ! :不等于。

<br>

<h3 id="通用">通用</h3>

<h6 id="自动跳转刷新"> ·自动跳转刷新</h6>
```html
<meta http-equiv="refresh" content="10; url=http://www.baidu.com/"> 
<meta http-equiv="refresh" content="10">
```
> 10为秒数设置

<br>

<h6 id="去除代码缓存"> ·去除代码缓存</h6>
```html
<meta http-equiv="cache-control" content="no-cache">
<meta http-equiv="expires" content="0">
```
指定过期时间
```html
<meta http-equiv="expires" content="Wed, 20 Jun 2000 22:33:00 GMT">
```