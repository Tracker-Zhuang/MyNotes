# Git版本管理
## Git本质
Git里面最重要的是commit，commit是历史快照，里面记录作者、时间、提交记录等，branch是指向某个commit的移动指针。每次有的新的提交后，分支都会指向新的提交。
![示例2](images\Git.png)

```bash
main->C
```
上面命令行代表main分支指向commit C。

```bash
git commit -m "C1"
git commit -m "C2"
git commit -m "C3"
```
上面命令行分别创建了三个commit节点对象。

## 分支相关
### 切换分支
```bash
git checkout 分支名
```

## 新建分支
```bash
git branch dev
```

### 新建并切换分支
```bash
git checkout -b dev
```

### 列出本地所有分支
```bash
git branch
```

### 查看远程仓库的所有分支
```bash
git branch -r
```
输出：
```bash
origin/HEAD -> origin/main
origin/main
```
其中origin/main代表远程仓库中的main分支，origin代表远程仓库名称\
origin/HEAD -> origin/main代表远程仓库默认指向的主分支是main，在Git中HEAD代表当前位置的指针

### 查看所有分支（包括本地和远程）
```bash
git branch -a
```

### .git文件
记录整个项目的历史，本地仓库就是项目目录

## 版本管理方法
善用分支开发，关键commit打tag等。

### 1. 不要直接开发main
```bash
git check -b develop/track
```
\
上面命令等价于:
```bash
git branch develop/track
git checkout develop/track
```
现在:
```bash
HEAD -> develop/track
```

### 2. 开始开发
修改了track.py和loss.py，查看修改
```bash
git status
```
上传文件至暂存区
```bash
git add track.py loss.py
或者 git add .
```
然后上传到本地仓库
```bash
git commit -m "v1"
```

### 3. 小步提交
再次优化后 git add . 和git commit -m "v2" \
发现实验效果很好，打tag，版本号命名为v0.1。
```bash
git tag -a v0.1 -m "first stable version" 
```
或者:
```bash
git tag stable_track
```
现在：
```bash
stable_track->v2
```

### 4. 继续乱改实验
乱调代码之后代码炸了，由于之前打了tag，可快速回退
```bash
git checkout stable_track
```
即可快速回到v2

### 5. 新分支继续开发
```bash
git checkout -b recover_branch
```
这样：
```bash
recover_branch->v2
```

### 6. 功能完成后合并到main
回到main
```bash
git checkout main
```
合并功能
```bash
git merge develop/track
```

### 7. 推送到远程
推送main
```bash
git push origin main
```

推送功能分支
```bash
git push origin develop/track.py
```

推送tag，tag默认不会上传
```bash
git push origin stable_track
```
或者
```bash
git push --tags
```


