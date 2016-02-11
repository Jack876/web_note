## 安装、使用sass&compass


#### 安装
> 使用cmd指令前先安装[ruby(windows版)](http://rubyinstaller.org/downloads/)

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


#### 使用
> 指定目录下打开cmd窗口使用指令

cmd指令 | 说明
-----|-----
compass create 文件名 | 在指定文件夹创建compass目录
sass main.cscc main.css | 转译scss文件（scss/sass文件目录下使用）
compass watch | 实时监听scss文件，自动转译（compass根目录下）
compass compile | 输出css,配置在config.rb中（例压缩模式：13行中添加output_style = :compressed）


---
## sass语法


###### 声明变量

`$width:500px;`

###### 声明默认变量

`$width:500px !default;`

> 默认变量用来设置默认变量，根据需求覆盖，覆盖时重新声明默认变量即可

###### 语法嵌套

```
a {
  	Color：red;
      	&:before {
     	Content:””
  	}
  	Body & {
		Color:blue;
  	}
}
````
