**`m目录`**

- [安装](#安装)

- [使用](#使用)
  + [配置文件](#配置文件)
  + [配置属性](#配置属性)
  + [插件属性](#插件属性)
  + [打包阶段插件](#打包阶段插件)
  + [服务器使用](#服务器使用)

<h3 id="安装">安装</h3>
> 安装[fis3](http://fis.baidu.com/)前先安装[nodejs](http://nodejs.cn/)
cnpm代替npm安装淘宝镜像： npm install -g cnpm --registry=https://registry.npm.taobao.org

<table>
  <tbody>
    <tr>
      <td>npm install -g fis3</td>
      <td>全局安装fis3，os x系统没权限的加sudo</td>
    </tr>
    <tr>
      <td>npm update -g fis3</td>
      <td>升级fis3</td>
    </tr>
  </tbody>
</table>
<br>

<h3 id="使用">使用</h3>
> 项目根目录下新建fis3配置文件，格式参考：

```javascript
// fis.match('::packager', {
//   spriter: fis.plugin('csssprites')
// });

// fis.match('*', {
//   useHash: false
// });

// fis.match('*.js', {
//   optimizer: fis.plugin('uglify-js')
// });

// fis.match('*.css', {
//   useSprite: true,
//   optimizer: fis.plugin('clean-css')
// });

// fis.match('*.png', {
//   optimizer: fis.plugin('png-compressor')
// });
```
<br>

<h6 id="release指令">release指令</h6>
| fis3指令 | 描述     |
| :------------- | :------------- |
| fis3 release       | 将根目录输出到服务器（www）文件夹     |
| fis3 release -h       | release使用帮助      |
| fis3 release -d <path>        | 输出根目录文件到path文件夹      |
| fis3 release -w       | 监控项目变化      |
| fis3 release -l       | 内容变化浏览器自动刷新      |
| fis3 release -c       | 清除缓存      |

<br>

<h6 id="配置文件">配置文件</h6>
<table>
  <tbody>
    <tr>
      <td>fis3 release <media></td>
      <td>编译时使用media的配置来编译文件</td>
    </tr>
    <tr>
      <td>fis3 inspect</td>
      <td>查看文件分配到的属性</td>
    </tr>
  </tbody>
</table>
```javascript
  //fis3 release rd 编译到 RD 的远端机器上
  fis.media('rd').match('*', {
    deploy: fis.plugin('http-push', {
      receiver: 'http://remote-rd-host/receiver.php'
    })
  });

  //fis3 release prod 使用定义的prod配置对js进行压缩
  fis.media('prod').match('*.js', {
    optimizer: fis.plugin('uglify-js')
  });
```
<br>

<h6 id="配置属性">配置属性</h6>
| 属性     |  描述    | 示例    |
| :------------- | :------------- | :------------- |
| release     |  文件产出路径，该值可设为false，表示不产出    |  release:'/js/$0'   |
| packTo     | 分配文件合并到这个属性配置的文件中     |  packTo: '/js/package.js'   |
| parkOrder     | 控制合并时的顺序，值越小越在前面。配合 packTo 一起使用     | packOrder: -100    |
| query     | 文件资源定位路径之后的query，比如'/css.css?=t14504902700'     | query: '?=t' + fis.get('new date')   |
|      | 使用前先设置new date     | fis.set('new date', Date.now())；    |
| id     | 设定文件的资源id     | id: 'jquery',    |
|      | 使用     | var $ = require('jquery');
    |
| moduleId     | 指定文件资源的模块id,插件fis3-hook-module里define会用到    | moduleId: 'a'    |
|      | 编译前     | exports.a = 10    |
|      | 编译后     | define('a',function(require,exports,module){exports.a = 10}）    |
| url     | 指定文件的资源定位路径，以/开头,     | release: '/static/$0',url: '/static/new_project/$0'    |
| chaset     | 指定文本文件的输出编码,默认是 utf8     | charset: 'gbk'    |
| useHash     | 文件是否携带 md5 戳     | useHash: true    |
| domain     | 给文件 URL 设置 domain 信息     | domain: 'http://cdn.baidu.com/'    |
| rExt     | 设置最终文件产出后的后缀     | rExt: '.sass'    |
| useMap     | 文件信息是否添加到 map.json     | useMap: true    |
| isMod     | 标示文件是否为组件化文件     | isMod:'true'    |
| extras     | 在[静态资源映射表][]中的附加数据，用于扩展[静态资源映射表][]表的功能     | extras:{ isPage: true }    |
|requires|  默认依赖的资源id表    | requires:[ 'static/lib/jquery.js' ]    |
| useSameNameRequire     | 开启同名依赖,模板会依赖同名css、js；js 会依赖同名 css，不需要显式引用     | useSameNameRequire: true    |
| isJsLike     | 指定对文件进行 js 相关语言能力处理，值类型：bool     |     |
| isCssLike     | 指定对文件进行 css 相关语言能力处理，值类型：bool     |     |
| isHtmlLike     | 指定对文件进行 html 相关语言能力处理，值类型：string     |     |
<br>

<h6 id="插件属性">插件属性</h6>

**lint**
启用 lint 插件进行代码检查,[更多插件](http://npmsearch.com/?q=fis-lint%20fis3-lint)
```javascript
fis.match('*.js', {
  lint: fis.plugin('js', {

  })
})
```
<br>

**parser**
启用 parser 插件对文件进行处理，[更多插件](http://npmsearch.com/?q=fis-parser%20fis3-parser)
```javascript
fis.match('*.sass', {
  parser: fis.plugin('sass'), //启用fis-parser-sass插件
  rExt: '.css'
});
```
<br>

**preprocessor**
标准化前处理,[更多插件](http://npmsearch.com/?q=fis-preprocessor%20fis3-preprocessor)
```javascript
fis.match('*.{css,less}', {
  paser: fis.plugin('image-set')
});
```
<br>

**standard**
自定义标准化，可以自定义 uri、embed、require 等三种能力，可自定义三种语言能力的语法，[更多插件](http://npmsearch.com/?q=fis-standard%20fis3-standard)
<br>

**postprocessor**
标准化后处理,[更多插件](http://npmsearch.com/?q=fis-postprocessor%20fis3-postprocessor)
```javascript
fis.match('*.{js,tpl}', {
   postprocessor: fis.plugin('require-async')
});
```
<br>

**optimizer**
启用优化处理插件，并配置其属性,[更多插件](http://npmsearch.com/?q=fis-optimizer%20fis3-optimizer)
```javascript
fis.match('*.css', {
    optimizer: fis.plugin('clean-css')
});
```
<br>


<h6 id="打包阶段插件">打包阶段插件</h6>
打包阶段插件设置时必须分配给所有文件，设置时必须 match ::package，不然不做处理。
```javascript
fis.match('::package', {
    packager: fis.plugin('map'),
    spriter: fis.plugin('csssprites')
});
```
<br>

**prepackager**
打包预处理插件
```javascript
fis.match('::package', {
    prepackager: fis.plugin('plugin-name')
})
```
<br>

**packager**
打包插件
```javascript
//当在 prod 状态下进行打包
fis.media('prod').match('::package', {
      packager: fis.plugin('map')
});
```
<br>

**spriter**
打包后处理csssprite的插件
```javascript
//当在 prod 状态下进行 csssprites 处理
fis.media('prod').match('::package', {
    spriter: fis.plugin('csssprites')
});
```
<br>

**postpackager**
打包后处理插件
```javascript
//当在 prod 状态下调用打包后处理插件
fis.media('prod').match('::package', {
    postpackager: fis.plugin('plugin-name')
});
```
<br>

**deploy**
设置项目发布方式
> 编译打包后，新增发布阶段，这个阶段主要决定了资源的发布方式，而这些方式都是以插件的方式提供的。比如你想一键部署到远端或者是把文件打包到 Tar/Zip 又或者是直接进行 Git 提交，都可以通过设置此属性，调用相应的插件即可。

```javascript
fis.match('**', {
    deploy: fis.plugin('http-push', {
        receiver: 'http://target-host/receiver.php', // 接收端
        to: '/home/work/www' // 将部署到服务器的这个目录下
    })
})
```
`常用插件`
- [local-deliver](https://github.com/fex-team/fis3-deploy-local-deliver)
- [http-pus](https://github.com/fex-team/fis3-deploy-http-push)
- [replace](https://github.com/fex-team/fis3-deploy-replace)
- [encoding](https://github.com/fex-team/fis3-deploy-encoding)
<br>


<h6 id="服务器使用">服务器使用</h6>
<table>
  <tbody>
    <tr>
      <td>fis3 server start/stop</td>
      <td>启动/关闭服务器</td>
    </tr>
    <tr>
      <td>fis3 server open</td>
      <td>打开服务器目录</td>
    </tr>s
    <tr>
      <td>fis3 release</td>
      <td>在服务器内创建当前目录下的工程</td>
    </tr>
  </tbody>
</table>
<br>
