## 安装、使用sass&compass



#### 安装
> 使用cmd命令前先安装[ruby(windows版)](http://rubyinstaller.org/downloads/)

cmd命令|说明
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

