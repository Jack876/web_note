**`目录`**

- [1.基本操作](#基本操作)
	+ [安装git](#安装git)
	+ [创建版本库](#创建版本库)
	+ [检索](#检索)
	+ [版本回退](#版本回退)
	+ [撤销修改](#撤销修改)
	+ [删除文件](#删除文件)
- [2.远程仓库](#远程仓库)
	+ [远程仓库](#远程仓库)
	+ [添加远程库](#添加远程库)
	+ [从远程克隆库](#从远程克隆库)
- [3.分支管理](#分支管理)
	+ [创建与合并分支](#创建与合并分支)
	+ [解决冲突](#解决冲突)
	+ [分支管理](#分支管理)
	+ [bug分支](#bug分支)
- [4.标签管理](#标签管理)
	+ [创建标签](#创建标签)
	+ [操作标签](#操作标签)
- [5.自定义git](#自定义git)
	+ [忽略特殊文件](#忽略特殊文件)
	+ [配置别名](#配置别名)

---

<h3 id="基本操作">1.基本操作</h3>

<h6 id="安装git" >·安装git</h6>
<table>
	<tbody>
		<tr>
			<td>git config --global user.name "Your Name"</td>
			<td>设置用户名</td>
		</tr>
		<tr width="100%">
			<td>git config --global user.email "email@example.com"</td>
			<td>设置邮箱</td>
		</tr>
	</tbody>
</table>
<br>

<h6 id="创建版本库">·创建版本库</h6>
<table>
	<tbody>
		<tr>
			<td>git init</td>
			<td>把当前目录变成git管理仓库</td>
		</tr>
		<tr>
			<td>git add readme.txt</td>
			<td>添加readme.txt文件</td>
		</tr>
		<tr>
			<td>git commit -m "上传文字说明"</td>
			<td>上传文件</td>
		</tr>
	</tbody>
</table>
<br>

<h6 id="检索">·检索</h6>
<table>
	<tbody>
		<tr>
			<td>git status</td>
			<td>查看仓库当前状态</td>
		</tr>
		<tr>
			<td>git diff</td>
			<td>查看具体差异改动</td>
		</tr>
		<tr>
			<td>git diff HEAD -- readme.txt</td>
			<td>查看工作区和最新版的区别</td>
		</tr>
	</tbody>
</table>
<br>

<h6 id="版本回退">·版本回退</h6>
<table>
	<tbody>
		<tr>
			<td>git log</td>
			<td>查看历史版本记录</td>
		</tr>
		<tr>
			<td>git log --pretty=oneline</td>
			<td>查看历史版本记录(简洁版)</td>
		</tr>
		<tr>
			<td>git reset --hard HEAD^</td>
			<td>返回至上一个老版本，head可以写成head~1</td>
		</tr>
		<tr>
			<td>git reset --hard id号</td>
			<td>git reflog</td>
		</tr>
		<tr>
			<td>回退至某个新版本</td>
			<td>查看之前每一次命令</td>
		</tr>
	</tbody>
</table>
<br>

<h6 id="撤销修改">·撤销修改</h6>
<table>
	<tbody>
		<tr>
			<td>git checkout -- readme.txt</td>
			<td>让这个文件回到最近一次git commit或git add时的状态</td>
		</tr>
		<tr>
			<td>git reset HEAD readme.txt</td>
			<td>把暂存区的修改撤销掉，重新放回工作区</td>
		</tr>
	</tbody>
</table>
<br>

<h6 id="删除文件">·删除文件</h6>
<table>
	<tbody>
		<tr>
			<td>rm readme.txt</td>
			<td>删除文件，也可手动删除</td>
		</tr>
		<tr>
			<td>git rm readme.txt</td>
			<td>从版本库中删除</td>
		</tr>
	</tbody>
</table>
<br>

<h3 id="远程仓库">2.远程仓库</h3>


<h6 id="远程仓库">·远程仓库</h6>
<table>
	<tbody>
		<tr>
			<td>$ ssh-keygen -t rsa -C "youremail@example.com"</td>
			<td>创建SSH KEY，在用户主目录里找到.ssh目录</td>
		</tr>
		<tr>
			<td></td>
			<td>id_rsa私钥不能泄露，id_rsa.pub公钥可以告诉任何人</td>
		</tr>
	</tbody>
</table>
> 登陆GitHub，用户设置-SSH Keys页面，自定义title，Key文本框里粘贴id_rsa.pub

<br>

<h6 id="添加远程库">·添加远程库</h6>
> 登陆GitHub，右上角-Create a new repo，输入name创建一个新的仓库

<table>
	<tbody>
		<tr>
			<td>git remote add origin git@github.com:Gil2015/learngit.git</td>
			<td>关联远程库，origin为远程库名字，@后为库地址</td>
		</tr>
		<tr>
			<td>git push -u origin master</td>
			<td>本地库内容推送到远程库，-u以后可以不加</td>
		</tr>
		<tr>
			<td></td>
			<td>如出现错误的主要原因是github中的README.md文件不在本地代码目录中,可以通过如下命令进行代码合并</td>
		</tr>
		<tr>
			<td>git pull --rebase origin master</td>
			<td>pull=fetch+merge</td>
		</tr>
	</tbody>
</table>
<br>

<h6 id="从远程克隆库">·从远程克隆库</h6>
<table>
	<tbody>
		<tr>
			<td>git clone git@github.com:Gil2015/gitskills.git</td>
			<td>克隆一个库,@后为库地址</td>
		</tr>
	</tbody>
</table>
<br>


<h3 id="分支管理">3.分支管理</h3>

<h6 id="创建与合并分支">·创建与合并分支</h6>
<table>
	<tbody>
		<tr>
			<td>git branch</td>
			<td>查看分支</td>
		</tr>
		<tr>
			<td>git branch -b [name] </td>
			<td>创建并切换到分支</td>
		</tr>
		<tr>
			<td>git branch [name]</td>
			<td>创建分支</td>
		</tr>
		<tr>
			<td>git checkout [name]</td>
			<td>切换分支</td>
		</tr>
		<tr>
			<td>git merge [name]</td>
			<td>合并某分支到当前分支</td>
		</tr>
		<tr>
			<td>git branch -d [name]</td>
			<td>删除分支</td>
		</tr>
		<tr>
			<td>git branch -D [name]</td>
			<td>强制删除分支</td>
		</tr>
	</tbody>
</table>
<br>

<h6 id="解决冲突">·解决冲突</h6>
<table>
	<tbody>
		<tr>
			<td>git log --graph</td>
			<td>查看分支合并图</td>
		</tr>
		<tr>
			<td>git log --graph --pretty=oneline --abbrev-commit</td>
			<td>查看分支合并图简略版</td>
		</tr>
	</tbody>
</table>
<br>

<h6 id="分支管理">·分支管理</h6>
<table>
	<tbody>
		<tr>
			<td>git merge --no-ff -m "文字信息" [name]</td>
			<td>强制禁用Fast forward模式合并master分支仅限发布，不应开发在分支dev上研发，并使用--no-ff避免dev分支信息消失</td>
		</tr>
	</tbody>
</table>
<br>

<h6 id="bug分支">·bug分支</h6>
<table>
	<tbody>
		<tr>
			<td>git stash</td>
			<td>将当前工作现场“储藏”起来</td>
		</tr>
		<tr>
			<td>git stash list</td>
			<td>查看之前存储的工作现场</td>
		</tr>
		<tr>
			<td>git stash apply</td>
			<td>恢复工作现场</td>
		</tr>
		<tr>
			<td>git stash drop</td>
			<td>删除工作现场</td>
		</tr>
		<tr>
			<td>git stash pop</td>
			<td>恢复同时删除</td>
		</tr>
	</tbody>
</table>
<br>


<h3 id="标签管理">4.标签管理</h3>

<h6 id="创建标签">·创建标签</h6>
<table>
	<tbody>
		<tr>
			<td>git tag 标签名</td>
			<td>当前分支上打标签(git tag v1.0)</td>
		</tr>
		<tr>
			<td>git tag</td>
			<td>查看所有标签</td>
		</tr>
		<tr>
			<td>git tag 标签名 id号</td>
			<td>对应历史ID版本打标签</td>
		</tr>
		<tr>
			<td>git show v1.0</td>
			<td>查看标签信息</td>
		</tr>
		<tr>
			<td>git tag -a v1.0 -m "文字说明" id号</td>
			<td>创建带说明的标签名,-a 指定标签名,-m 指定说明文字</td>
		</tr>
		<tr>
			<td>git tag -s v0.2 -m "文字说明" id号</td>
			<td>采用PGP签名，必须安装gpg（GnuPG），否则报错</td>
		</tr>
	</tbody>
</table>
<br>

<h6 id="操作标签">·操作标签</h6>
<table>
	<tbody>
		<tr>
			<td>git tag -d 标签名</td>
			<td>删除标签名</td>
		</tr>
		<tr>
			<td>git push origin 标签名</td>
			<td>推送标签到远程</td>
		</tr>
		<tr>
			<td>git push origin --tags</td>
			<td>一次推送所有标签</td>
		</tr>
	</tbody>
</table>
<table>
	<thead>
		<tr>
			<td>远程删除标签</td>
			<td></td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>git tag -d 标签名</td>
			<td>先本地删除标签名</td>
		</tr>
		<tr>
			<td>git push origin :refs/tags/标签名</td>
			<td>再远程删除</td>
		</tr>
	</tbody>
</table>
<br>


<h3 id="自定义git">5.自定义git</h3>

<h6 id="忽略特殊文件">·忽略特殊文件</h6>
> git工作区下新建一个xx.gitignore文件,把忽略的文件名填进去，不同项目配置。[参考](https://github.com/github/gitignore)

<br>

<h6 id="配置别名">·配置别名</h6>
<table>
	<tbody>
		<tr>
			<td>git config --global alias.别名 "原名多词"</td>
			<td>global是全局参数,命令在这台电脑的所有Git仓库下都有用</td>
		</tr>
	</tbody>
</table>
实用配置，带颜色的查看分支

`git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"`

> Git配置文件放在.git/config文件中,别名就在[alias]后面，要删除别名，对应的行删掉即可
