#第一步：吧代码放在Github作版本控制
## 1: 在本地创建仓库（在终端进入项目文件夹，输入如下指令）
`git init`
## 2: 查看文件夹中未追踪到的文件
`git status`
## 3: 记录所有文件并准备将其上传
`git add *`
## 4: commit 所有文件：
`git commit -m "first commit"`
## 关联远程仓库（需知晓远程仓库的路径url）：
 `git remote add origin url`
 `git rmeot -v`  查看关联情况
## 5: 上传
`git push -u origin master`
## 6: 查看 git 日志
`git log`
## 7:每次更新项目代码后记得要git最新版本的项目代码到github仓库
`git add *`
`git commit -m "date or n-th commit"`
`git push -u origin master`
