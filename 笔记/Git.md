```
apt-get install git
git --version
git config --global user.name "runoob"
git config --global user.email test@runoob.com
```

- 长期存储密码  git config --global credential.helper store
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
git pull <远程主机名> <远程分支>:<本地分支>
git push <远程主机名> <本地分支>:<远程分支>
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



git rebase -i HEAD~2   将本地的多次提交合并为一个，以简化提交历史。

git rebase master 将master最新的分支同步到本地



```git
#当代码未提交时，用stash先暂时存储
git stash
git stash pop

#回退到代码分支位置，加入分支代码
git fetch
git rebase origin/master
```



```
#修改密码后无法push
git config --system --unset credential.helper
git config --global credential.helper store
```



查看连接关系

git remote show origin



```bash
#查看所有分支
git branch -a

#创建并切换到本地某分支，跟踪远程某分支
git checkout -b 本地新建的分支名 origin/线上分支名

#查看当前本地分支
git branch

#本地分支间切换
git checkout <分支名>

#本地分支连接远程分支
git branch --set-upstream-to=origin/name

#建立本地test并连接远程分支
git branch --track test origin/master
```



```bash
#git拉取其他分支并且合并代码

1.先提交一波  为后续切分支准备
(xxx1为自己的分支  xxx2为想要拉取的分支)
git add .
git commit -m 'yyy'
git push origin xxx1

2.然后git切换到你所要拉取的分支xxx2  拉取该分支代码
git checkout xxx2
git pull origin xxx2 或者git fetch origin xxx2

3.切回自己的分支
git checkout xxx1
git merge xxx2
```



```
#在本地移除远程已删除的分支
git remote prune
```

```
#提示unrelated-histories
git pull origin master --allow-unrelated-histories
git merge origin master --allow-unrelated-histories
```

```
#配置meld
git config --global merge.tool meld
git config --global mergetool.meld.path "d:/Meld/Meld.exe"
git mergetool
```



```bash
#合并分支
#利用Merge Requests，有冲突时会提示方法.实例如下
#Step 1. Fetch and check out the branch for this merge request
git fetch origin
git checkout -b development origin/development
#Step 2. Review the changes locally
#Step 3. Merge the branch and fix any conflicts that come up
git fetch origin
git checkout origin/development
git merge --no-ff feature/ui (--allow-unrelated-histories)
#Step 4. Push the result of the merge to GitLab
git push origin HEAD:development
```



##### git merge和git merge --no-ff的区别：

git merge --ff ：fast-forward，git reset HEAD^ --hard 回退时退到merge分支

git merge --no-ff ：git reset HEAD^ --hard回退时退到主分支



**git  rebase**

Git rebase 的中文名是变基，就是改变一次提交记录的base。可以使合并后的记录更简洁，问题搁置。



### Tag

`git tag` 查看本地tag

`git tag -a  -m`  #打标签

```
#删除本地tag，同步远程
git tag -l | xargs git tag -d
git fetch origin --prune
git fetch origin --tags
```

