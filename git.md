# git
## 项目流程管理
	1. 先收集需求， 确定需求内容 和方案， 分支名称；
	2. 创建分支， 需求实现；
	3. 创建MR， 合并的目标分支: master;
	4. 项目负责人 review代码， 直到完结；
	5. 分支代码， 集成测试
	6. 合并到master, 升级到正式版本， deploy;
	7. 打tag
	
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
		
### others

		// 查看当前git repository的git url
		git config --get remote.origin.url