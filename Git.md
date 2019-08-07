```
apt-get install git
git --version
git config --global user.name "runoob"
git config --global user.email test@runoob.com
```

- 提交、创建新版本  `git commit`
- 建立远程分支   `git clone`
- 从远程获取数据，更新本地的远程分支  `git fetch`
- 获取、合并fetch、merge  `git pull`
- 上传、更新远程仓库  `git push`


```
git init  初始化
git remote rm origin
git remote add origin https://github.com/HCH2CHO/CreativeWriting.git  定义远程仓库
git add .  该目录下文件全部加入缓存。.可换成文件or文件夹
git commit -m "update"  提交
git pull origin master  下拉同步
git push origin master 上传修改
git stash恢复到上次提交的内容
git status  查看仓库状态
```

https://blog.csdn.net/u012501054/article/details/79098991

