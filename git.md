# git
## 项目流程管理
	1. 先收集需求， 确定需求内容 和方案， 分支名称；
	2. 创建分支， 需求实现；
	3. 创建MR， 合并的目标分支: master;
	4. 项目负责人 review代码， 直到完结；
	5. 分支代码， 集成测试
	6. 合并到master, 升级到正式版本， deploy;
	7. 打tag
	
* 分支不应该以确认的版本号来命名, 理由是: 因为当前版本号基本是上一个版本号的延伸，如果当前的分支开发任务比较大，这时突然有一个小的需求要实现，那么为这个小需求创建分支的命名就比较麻烦了, 尤其是打tag的时候, 因为tag一般是需要具体的版本好的, 所以分支可以是有意的字符标识, 在打tag的时候再采用版本号来命名, 或者可以用majorVersion.minorVerison.x的方式

## 常用命令
### git tag
		
		// 创建tag
		git tag -a 'xxx' -m ‘xxx'
		// 推送tag到服务端
		git push origin xxx
		
### git branch 
		// 创建分支
		git branch ${branch_name}
		// 推送分支到服务端
		git push origin ${branch_name}
		
		// 删除本地分支
		git branch -d ${branch_name}
		// 删除对应的远程分支
		git push origin :branch-name
		
		// 查看所有的分支
		git branch -a
		
		// 修改分支名称(本地和远程)
		// 重命名远程分支对应的本地分支
		git branch -m old-local-branch-name new-local-branch-name
		// 上传新命名的本地分支
		git push origin  new-local-branch-name
		//  删除远程分支
		git push origin  :old-local-branch-name
				
### others

		// 查看当前git repository的git url
		git config --get remote.origin.url
		
		//清除无用的远程分支 
		git remote prune origin