﻿## git和github

### 1. git : 工具

    	版本控制工具
    	
    		SVN:集成式版本控制工具
    		
    			SVN要联网并且依靠中央服务器进行版本控制
    		
    		git:分布式的版本控制工具
    		
    			git在本地就可以进行版本控制

### 2. github : 最大的程序员交友(基友)网站

		1.可以去参与别人开源的项目
		
		2.学习的途径
		
		3.自己的私人博客(自己免费的网站)|远程仓库
		
		4.项目分发

### 3. 安装git

### 4. 创建github账号 (邮箱确认)

### 5. 捆绑(git与github)

		(1) 获取秘钥
		
			ssh-keygen -t rsa -C "注册邮箱"
		
		(2) 将秘钥添加到github上
		
			github -> settings -> SSH and GPG keys -> new ssh key
		
		(3) 设置作者信息
		
			git config --global user.name "你的账户名"
			
			git config --global user.email "你的邮箱"
			
	    	查看:
	    	
	    		git config --global user.name
	    		
	    		git config --global user.email
	    		
	    		能看到设置的作者信息
			
		(4) 查看测试有没有绑定成功,Hi!xxx
		
			ssh -T git@github.com
		
		命令:
			进入目录:
			
				cd c:
				
			查看目录:
			
				ll || ls
			
			tab
			
				补全命令
			
			方向键:
			
				↑上:回到前一次输入命名
				
				↓下:回到后一次输入命名
			
			退回:
			
				cd ..
			
			清屏:
			
				clear

### 6. 创建项目

		1.点击New repository创建项目
		
		2.填写项目名称,项目的描述,public,勾选README

### 7. 项目放到本地

		打开控制台，进入要存放项目的目录
		
		github上复制克隆地址
		
		通过git clone 项目地址 回车
		
		删除项目：进入项目 -> settings -> Delete this repository(按钮) -> 输入删除的项目名称 -> 确定

### 8. 上传

		1. git add .
		
		2. git commit -m "注释"
		
		3. git push origin master

### 9. git的三大区域
   
		工作区（开发人员开发的环境）
		
		暂存区
		
			作为过渡层
			避免误操作
			保护工作区和版本区
			分支处理
			
		版本区（库）当项目开发完成时保存当前项目进度的一个仓库

### 10. 查看状态

		git status
		
		当项目提交到版本区的时候，查看状态为“空”会出现git push等字样
		
		这个时候版本为最近一次提交的代码。

### 11. 工作区到暂存区

		git add 文件名
		
		快捷批量操作：
		
			git add .

### 12. 暂存区到版本区

		git commit -m "注释"  就是给当前的项目取一个容易识别的名字，以便以后去查找

### 13. 快捷方式

		直接从工作区到版本区的命令（只针对提交过的代码起效，新创建的文件无效）
		
			git commit -a -m "注释"
			
		当代码放到版本区的时候，暂存区的代码与版本区的代码一致

### 14. 查看版本号

		git log		->		退回 q


### 15. 对比

		查看工作区与暂存区的区别：
		
			git diff 
		
		查看暂存区与版本区的区别:
		
			git diff --cached
			
		查看工作区与版本区的区别：
			
			git diff master(一般为master分支)

### 16. 撤销

		把暂存区的代码撤销回工作区：
		
			git reset HEAD 文件名
			
		如果工作区的代码已经放到了暂存区，并且又修改了工作区的代码，
		运行了撤销操作，那么这个时候**工作区修改的代码任然会保留**。
		
		如果**撤销想还原之前在暂存区或者版本区的代码**，
		那么可以使用 git checkout -- 文件名来还原。
		
		
		如果暂存区有代码，优先还原暂存区的代码，如果没有，还原成版本区的代码。
		***如果3区都有不同，使用了一次撤销，那么再次撤销无效。
		
		
		如果有2个以上文件，一个提交到版本库了，另一个忘记提交，可以先将没提交的文件拉到暂存区，
		然后通过git commit -m “注释” --amend 撤销回来，
		最后自动一次性提交暂存区中的文件和撤销回来的版本形成一个新的版本，
		撤销回来的版本就销毁了，git log查看是否提交成功。

### 17. 删除

		当某个（些）文件已经提交且在工作区手动删除，那么会出现红色
		
		    deleted: xxxx
		
		解决方案：
		
			1.使用checkout还原
			
			2.手动删除之后也想删除git中的信息，git rm xxx
		
		注意：
		
			如果要删除的文件已经在版本区了，并且没有修改这个要删除的
			文件，那么使用git rm xxx会把这个文件彻底删除（所有区都删除）
			
			**如果修改了要删除的文件，又使用git rm xxx，那么是不可取的。
		
		
		使用命令去删除本地文件和git信息：
		
			git rm -f xxx
		
		删除整个文件夹 git rm -rf 文件夹名字

### 18. 恢复（回滚）

		回滚指定的文件：
		
			git checkout 版本记录  回滚的文件名。
			
		回滚指定的版本：
		
			git reset --hard 版本记录。
			
		如果回滚的次数很多，有些时候会发现git log中没有想恢复的版本信息，那这个时候就可以使用git reflog 来查找操作信息。

### 19. 设置多人开发的权限

		1.进入项目
		
		2.点击settings
		
		3.在最左边第二个列表，collaboration，可以添加协同开发人员
		
		4.输入用户名即可
		
		5.被邀请的人要确认才能合作开发这个项目。

### 20. 上传失败解决方法

> 在修改完项目之后要push到远程仓库，如果传不上去，出现了error...git pull等字样

> 说明当前版本与远程仓库的代码有冲突，需要把冲突解决完才能成功push。

    	解决：
    	
	    	1.需要把远程仓库的代码拉取到本地，然后进行对比。
	    	
	    		git fetch 
	    		
	    	2.查看冲突
	    	
	    		git diff master origin/master
	    		
	    	3.合并冲突
	    	
	    		git merge origin/master
	    		
	    	4.手动修改冲突
	    	
	    	5.再提交一次
	    	
	    	6.push
		
		小技巧：
		
			在于远程仓库合并代码的时候，先把本地的代码拷贝一份，避免合并之后本地的代码直接被远程仓库的代码给覆盖。

### 21. 参与他人项目

> 当没有权限还想参与别人的项目时

		1.先找到想参与的项目，fork
		
		2.把fork的项目克隆到本地
		
		3.去修改项目文件
		
		4.提交
		
		5.点击 Pull requests
		
		6.点击new Pull request
		
		7.点击create Pull request
		
		8.在留言板下点击create Pull request
		
		9.等待别人的回复

> 当你收到了修改通知的时候

		1.进入项目
		
		2.点击files changed 查看修改的记录
		
		3.如果同意点击 merge Pull request
		
		4.点击Confirm  merge

### 22. 分支

    	查看分支：
    	
    		git branch
    		
    	新建分支：
    	
    		git branch 分支名
    		
    	切换分支：
    	
    		git checkout 分支名
    		
    	快捷方式（快速新建并切换）：
    	
    		git checkout -b 分支名

> 注意：新建分支的时候一定要看清楚，当前分支在哪里，如果不为复制模板，切换到复制主体上。

		删除分支（已合并的）
			
			git branch -d 分支名
			
		强行删除分支（未合并的）
			
			git branch -D 分支名
			
		查看未合并的分支：
			
			git branch --no-merged
			
		查看已合并的分支：
			
			git branch --merged
			
		合并分支：
			
			git merge 分支名

> 注意：在合并的时候，有可能会发生冲突，那么需要解决冲突

		1.将主干和分支都提交到版本库；
		
		2.合并（git merge 分支名）；
		
		3.git status (查看冲突)；
		
		4.手动解决；
		
		5.如果需要，可以把合并之后的分支删除

### git本地创建远程仓库分支

		1.本地创建分支zyh
		
			$ git branch zyh
		
		2.本地分支提交至远程仓库
		
			$ git push origin zyh
		
		3:查看一下远程仓库有几个分支
		
			$ git branch -a
			master
			*zyh    *号代表你现在所在的分支
			remotes/origin/HEAD -> origin/master
			remotes/origin/zyh  远程仓库zyh分支
			remotes/origin/master  远程仓库master分支

### 密码

		设置记住密码（默认15分钟）：
		
			git config --global credential.helper cache
		
		如果想自己设置时间，可以这样做：
		
			git config credential.helper 'cache --timeout=3600'
			这样就设置一个小时之后失效
		
		长期存储密码：
				
			git config --global credential.helper store

### tag操作

		查看标签：

			git tag

		创建轻量标签：

			git tag <tagname>

		创建带备注标签(推荐)：

			git tag -a <tagname> -m "这是备注信息"

		针对特定commit版本SHA创建标签：

			git tag -a <tagname> <SHA值> -m "这是备注信息"

		删除标签(本地)：

			git tag -d <tagname>

		将本地标签发布到远程仓库：

			git push origin --tags

		指定版本发送：

			git push origin <tagname>

		删除远程分支：

			git push origin --delete <branchName>

		删除tag：

			git push origin --delete tag <tagname>

### git强制推送（谨慎使用）

> git push -f origin master    -f为force，意为：强行、强制
