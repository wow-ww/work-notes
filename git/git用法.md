- 查看远程仓库详细信息
	`git remote -v`
- 删除xxx仓库
	`git remote remove xxx`
- 重新添加远程仓库地址
	`git remote add origin 仓库地址`
- 提交到远程仓库的xxx主干
	`git push -u origin xxx`

##### 提交到远程仓库流程
- `git init`
	初始化本地仓库
- `git add -a -m xxx`
	把xxx文件夹添加到本地仓库
- `git commit -a -m "xxxxx"`
	把代码提交到本地仓库，并备注信息
- `git remote add origin 仓库地址`
	本地git仓库与远程仓库关联
- `git push -u origin xxx`
	将项目推送到远程仓库