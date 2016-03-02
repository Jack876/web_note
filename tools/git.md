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

<h3 id="基本操作">1.基本操作</h3>

<h6 id="安装git" >安装git</h6>
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

<h6 id="创建版本库">创建版本库</h6>
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

<h6 id="检索">检索</h6>
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

<h6 id="版本回退">版本回退</h6>
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

<h6 id="撤销修改">撤销修改</h6>
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

<h6 id="删除文件">删除文件</h6>
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

<h3 id="远程仓库">2.远程仓库</h3>
<table>
	<tbody>
		<tr>
			<td>$ ssh-keygen -t rsa -C "youremail@example.com"</td>
			<td>创建SSH KEY，在用户主目录里找到.ssh目录</td>
		</tr>
		<tr>
			<td>id_rsa私钥不能泄露，id_rsa.pub公钥可以告诉任何人</td>
		</tr>
	</tbody>
</table>
> 登陆GitHub，用户设置-SSH Keys页面，自定义title，Key文本框里粘贴id_rsa.pub

<h6 id="远程仓库">远程仓库</h6>
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>

<h6 id="添加远程库">添加远程库</h6>
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>

<h6 id="从远程克隆库">从远程克隆库</h6>
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>


<h3 id="分支管理">3.分支管理</h3>

<h6 id="创建与合并分支">创建与合并分支</h6>
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>

<h6 id="解决冲突">解决冲突</h6>
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>

<h6 id="分支管理">分支管理</h6>
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>

<h6 id="bug分支">bug分支</h6>
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>


<h3 id="标签管理">4.标签管理</h3>

<h6 id="创建标签">创建标签</h6>
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>

<h6 id="操作标签">操作标签</h6>
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>


<h3 id="自定义git">5.自定义git</h3>

<h6 id="忽略特殊文件">忽略特殊文件</h6>
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>

<h6 id="配置别名">配置别名</h6>
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
	</tbody>
</table>
