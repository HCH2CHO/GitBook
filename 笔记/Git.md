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



生成密钥

```
ssh-keygen -t rsa -C "251955986@qq.com"
```



新建分支

```
git branch -a
git checkout ParkMap
GUI里需先create branch，再checkout branch
```

### .gitignore文件

<https://github.com/github/gitignore>

.gitignore不起作用时：

```bash
git rm -r --cached .
git add .
git commit -m 'update .gitignore'
```

或删除已进入当前缓冲区的文件

### Linux

```
git gui
```



### 升级技巧

```
git clone  -b <branch> --depth=10  <ssh>  #clone某branch,10个版本记录
```

配置meld

```
git config --global merge.tool meld
git config --global mergetool.meld.path "/c/Program Files (x86)/Meld/Meld.exe"
```



git  主分支修改时，子分支从主分支拉取命令。

无代码冲突时：

```
git pull <远程主机名> <远程分支名>:<本地分支名>
```

有冲突时：

```
切换到master，先git pull origin master
再local merge
利用meld修改冲突
git commit之前use local version
```



冲突符号讲解：

```
<<<<<<< HEAD
b789
=======
b45678910
>>>>>>> 6853e5ff961e684d3a6c02d4d06183b5ff330dcc

head 到 =======里面的b789是本地上传的commit的内容
=========到 >>>>68的是下拉的内容
```



更新同步分支

```
git reset --hard origin/planning
```



```git
#当代码未提交时，用stash先暂时存储
git stash
git stash pop

#回退到代码分支位置，加入分支代码
git fetch
git rebase origin/master
```



