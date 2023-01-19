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
##### 本地git与github账户关联
- `git config --global user.name "用户名"`
- `git  config --global user.email "github账号注册用的邮箱"`
- `ssh-keygen -t rsa -C "邮箱地址"`
	以上完成ssh密钥的创建
- `ls -al ~/.ssh`
	查看本机是否有密钥文件
- `cd ~/.ssh`
- `ls`
- `cat id_rsa.pub`
	查看本地的公钥
- `cat id_rsa`
	查看本地的私钥
- 进入github，左上角头像下拉列表，进入settings
	![[Pasted image 20230119103507.png]]
- 找到SSH and GPG keys
	![[Pasted image 20230119103619.png]]
- New SSH key
	![[Pasted image 20230119103757.png]]