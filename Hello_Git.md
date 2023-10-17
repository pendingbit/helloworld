# Git 基础

## 初始化一个新的仓库  
>`$ mkdir myproject`  
>`$ cd ./myproject`  
>`$ git init`



## 克隆已有仓库helloworld  
>`$ git clone https://gitee.com/pending_bit/helloworld`  

## 克隆已有仓库helloworld并重命名为myworld  
>`$ git clone https://gitee.com/pending_bit/helloworld myworld`  



## 文件状态  
git管理的文件分为`tracked`和`untracked`两类，也就是被追溯和未被追溯两种区分。  

`tracked`被追溯文件会有三种状态：  
|——`unmodified` 代表文件与上次提交保持一致  
|——`modified`   代表文件与上次提交不一致  
|——`Staged`     代表文件已经修改且被暂存


![git file](./pic/git_record_change.jpg "git file status")


## 查看文件状态
>$ git status  
>$ git status -s //精简显示 -s：short

## 暂存已修改文件或者新的文件
>$ git add file-modifed file-new  

## 配置ignore文件
创建名为`.gitignore`的文件用来忽略不想加入管控的文件  
>$cat .gitignore  
>`#`忽略所有.o 和.a 结尾的文件  
>*.[oa]  
>
>`#`追溯特定lib.a文件，即使之前设定忽略所有.a  
>!lib.a  
>   
>`#`忽略所有~结尾的文件  
>*.~  
>  
>`#`仅忽略当前目录下的todo文件，非子目录下的todo文件  
>/todo  
>
> `#`忽略build目录下的所有文件，包含所有子目录  
> bulid/  
>
> `#`仅忽略doc目录下所有.txt文件，非子目录下的.txt文件  
> doc/*.txt  
>
> `#`忽略doc目录下所有.pdf文件，包含所有子目录  
> doc/**/*.pdf  
>

## 查看代码差异
>$ git diff   #查看工作区与暂存区的文件差异  
>$ git diff --staged  #查看暂存区与上一次提交记录的文件差异  
>$ git diff HEAD^ HEAD #查看上次提交记录与其前一次提交记录的差异  
>$ git diff commit-ID1 commit-ID2 #查看提交记录1到提交记录2的差异  

`TIP:`   
1.HEAD代表最新一次提交记录，即上一次提交记录  
2.HEAD^代表倒数第二次提交记录，即上上次计较记录  
3.git diff --staged 与 git diff --cached 作用相同  
4.commit-ID通过git log查看提交记录获得，本质是一串哈希值


## 提交修改
>$ git commit -m "commit log" #提交暂存区的文件，生成新的提交记录  
>$ git commit -a -m "commit log" #add与commit步骤合并为一步

## 删除文件
>$ git rm file #删除file文件并停止追溯，相当于`rm file | git add file`  
>$ git rm --cached file #保留file文件并停止追溯，用于本来ignore的文件被不小心提交了  
>
>$ git rm log/\*.log #删除log目录下所有.log文件并停止追溯  
>$ git rm \*~ #删除所有~结尾的文件并停止追溯  
>#通配符星号前面的反斜杠是必须的，遵循git要求

## 重命名文件
>$ git mv file_from file_to #重命名file_from为file_to,相当于`rm file_from file_to | git rm file_from | git add file_to`  

## 查看提交记录
>$ git log #查看所有提交记录  
>$ git log branchname #查看指定分支的log  
>$ git log -2 #查看最近两次提交记录  
>$ git log -p #查看所有提交记录，并显示详细diff  
>$ git log -p -2 #查看最近2次提交记录，并显示详细diff  
>$ git log --stat #查看所有提交记录，并简要显示文件修改数量  
>$ git log -- files #查看所有和files相关的提交记录  
>$ git log -S function_name #查看所有代码中和`function_name`字符串相关的提交记录  
>$ git log --grep string #查看所有提交日志中包含`string`的提交记录  
>$ git log --pretty=oneline #查看所有提交记录，每条记录用一行简要显示  
>$ git log --pretty=short #查看所有提交记录，`short`模式显示  
>$ git log --pretty=full  #查看所有提交记录，`full`模式显示  
>$ git log --pretty=fuller  #查看所有提交记录，`fuller`模式显示  
>$ git log --pretty= oneline --graph #ascii码图像化commit过程  
>$ git log --pretty=format:"%h -%an ，$ar : %s"  #按照{缩略哈希值-作者名字，作者相对时间：日志log}格式输出log    

--pretty=format支持的百分符号如下：
|百分符号|描述|
|-----|-----|
|%H|哈希值|
|%h|简要哈希值|
|%T|树哈希值|
|%t|简要树哈希值|
|%P|父哈希值|
|%p|简要父哈希值|
|%an|作者名字|
|%ae|作者邮箱|
|%ad|作者日期|
|%ar|作者相对日期|
|%cn|提交者名字|
|%ce|提交者邮箱|
|%cd|提交者日期|
|%cr|提交者相对日期|
|%s|日志log|

## 撤回
>$ git commit --amend  #对上一次提交进行修正， 一般用来修正忘记添加的文件，或者修改上次提交的日志内容  
>$ git restore --staged file  #撤销之前add操作的file文件  
>$ git restore file  #撤销工作区的任何修改  

## 远程仓库
远程仓库是用于和其他协作者分享你的工作，相当于是多方维护的一个共享仓库。

### 查看远程仓库
>$ git remote #显示远程仓库的shortname， clone后远程仓库默认为`origin`  
>$ git remote -v #显示远程仓库的shortname以及完整URL信息  

### 增加远程仓库
>$ git remote add pb `https://github.com/pendingbit/helloworld`

### 从远程仓库获取数据
>$ git fetch <remote>
>$ git pull <remote>

### 推送数据到远程仓库
>$ git push <remote> <branch>

### 检阅一个远程仓库
>$ git remote show <remote>

### 重命名远程仓库
>$ git remote rename oldname newname

### 删除远程仓库
>$ git remote remove name

## TAG
### 查看tag
>$ git tag  #查看所有打上tag软件版本  
>$ git tag -l "v1.8.5* #查看所有匹配v1.8.5开头的tag  
>$ git show v1.4 #查看某一个具体的tag信息

### 创建tag
>$ git tag -a v1.4 -m "my version 1.4"  #annotated tag   
>$ git tag v1.4-lw #lightweight tag  
>$ git tag -a v1.2 9fce02 #对之前的某一次提交打tag  

### 分享tag
>$ git push origin `tagname` #推送某一个tag  
>$ git push --tags #推送所有tag  

### 删除tag
>$ `git tag -d v1.4-lw`

### checkout tag
>$ git checkout v1.4-lw #注意此时detached HEAD 状态 ， 在此基础上修改无法提交  


## 重命名
>$ git config --global alias.co checkout  
>$ git config --global alias.br branch  
>$ git config --global alias.ci commit  
>$ git config --global alias.st status
>$ git config --global alias.unstage 'reset HEAD --'  
>$ git config --global alias.last 'log -1 HEAD'  

# GIT Branch
## 创建分支
当前状态
![branch 1](./pic/branch_1.jpg "current status")
>$ `git branch testing` #创建testing分支  
> 新创建的分支本质就是创建了新命名的指针指向当前commit；HEAD是个特殊指针，永远指向当前所处的commit

![branch 2](./pic/branch_2.jpg "create testing branch")

## 切换分支
>$ `git checkout testing` #切换到testing分支;HEAD指向testing;并且工作区所有内容会重置为分支版本;`切换分支前clean working state`  
>$ `git switch testing` #同上  
>$ `git checkout -b newbranchname` #创建并切换到新的分支  
>$ `git switch -c newbranchname`  #同上  
>$ `git switch -` #切换回上一个分支

创建testing分支
![branch 3](./pic/branch_3.jpg "switch branch")
在不同的分支上进行各自开发和commit  
![branch 4](./pic/branch_4.jpg "separate branch")

## branching and Merging

![simple commit history](./pic/simple_commit_history.jpg "simple commit history")
一个简单的commit，c0->c1->c2  
此时需要开发#53号特性，创建`iss53`分支
>$ `git checkout -b iss53`   
>$ `git branch iss53 | git checkout iss53` #功能同上  
![create a new branch pointer](./pic/create_a_new_branch_pointer.jpg "create a new branch pointer")  

在iss53分支上进行了提交
>$ ***do some job***  
>$ `git commit -a -m "new function in [issue 53]"`  
![work forward in iss53](./pic/work_forward_in_iss53.jpg "work forward in iss53")  

在master分支c2版本发现了一个bug，创建hotfix分支来解决  
>$ `git checkout master`  
>$ `git checkout -b hotfix`  
>$ ***do some fix***  
>$ `git commit -a -m "fix bug"`  
![hotfix branch based on master](./pic/hotfix_branch_based_on_master.jpg "hotfix branch based on master")  

bug修复完毕，需要合并到master分支去
>$ `git checkout master`  
>$ `git merge hotfix`  #快速前进合并fast-forward  
![master is fast-forwarded to hotfix](./pic/master_is_fast_forwarded_to_hotfix.jpg "master is fast-forwarded to hotfix")  

hotfix分支已经无意义，将其删除,切换到iss53分支继续工作 
>$ `git branch -d hotfix`  
>$ `git checkout iss53`  
>$ ***do some job***  
>$ `git commit -a -m "finish function [issue53]"`  
![delete hotfix and continues on iss53](./pic/delete_hotfix_and_continues_on_iss53.jpg "delete hotfix and continues on iss53")  

iss53分支工作完成，合并到master分支并删除iss53分支     
>$ `git checkout master`  
>$ `git merge iss53`  #没有冲突的情况下，git merge自动创建合并commit  
>$ `git branch -d iss53`
![merge commit](./pic/merge_commit.jpg "merge commit")  

通过三个快照进行合并，`master iss53` 以及他们的公共祖先快照`c2`  
![three snapshots used in a typical merge](./pic/three_snapshots_used_in_a_typical_merge.jpg "three snapshots used in a typical merge")

## 合并冲突基础
如果iss53分支和hotfix分支都修改某个文件的同一部分，那么将出现合并冲突问题
>$ `git merge iss53`  
>Auto-merging test.c  
>CONFILCT(content):Merge conflict in test.c  
>Automatic merge failed; fix conflicts and then commit the result.  

使用git status查看冲突的文件  
>$ `git status`  
>On branch master  
>You have unmerged paths.  
>  (fix conflicts and run "git commit")  
>Unmerged paths:  
>  (use "git add <file>..." to mark resolution)  
>  both modified: index.html  
>no changes added to commit (use "git add" and/or "git commit -a")  

git将自动添加两个版本内容到冲突文件中，格式如下
>`<<<<<<< HEAD:test.c`  
> abcdefg  = 1;  
>`=======`  
> abcdeft = 2;  
>`>>>>>>> iss53:index.html`  

使用编辑工具进行修改，其中`<<<<<<< HEAD:test.c` , `=======` , `>>>>>>> iss53:index.html`都是辅助表示，需要删除。

修改完毕后，通过add/commit 操作完成此次合并。

## 分支管理
### 查看branch
>$ `git branch` #查看所有分支（仅显示分支名） 
>$ `git branch -v` #查看所有分支(显示分支名和提交信息)  
>$ `git branch -vv` #查看所有分支（显示哪些关联远程）
>$ `git branch --all` #查看所有分支（包括远程和本地）
>$ `git branch --merged` #查看已经合并到HEAD的分支   
>$ `git branch --no-merged` #查看未合并到HEAD的分支  
>$ `git branch --merged [branchname]` #查看已经合并到指定分支的分支  
>$ `git branch --no-merged [branchname]` #查看未合并到指定分支的分支  

## 删除branch  
>$ `git branch -d [branchname]` #删除指定分支，如果指定分支尚未合并则删除操作失败。  
>$ `git branch -D [branchname]` #删除指定尚未合并的分支

## 修改branch名  
**禁止修改其他贡献者正在使用的分支名字**  
**禁止修改其他贡献者正在使用的分支名字**  
**禁止修改其他贡献者正在使用的分支名字**  
>$ `git branch --move bad-branch-name corrected-branch-name`  #在本地修改分支名字  
>$ `git push --set-upstream origin corrected-branch-name` #推送正确名字的分支到远程  
>$ `git push origin --delete bad-branch-name` #删除错误名字的分支到远程  

## 分支工作流程  
git可以很方便的进行分支合并，所以在开发一个复杂的项目的时候，往往使用多个分支来维护项目的不同周期。  
**举个例子：**  
master分支是稳定版本，用于release  
develop分支是开发分支  
topic分支可能是某个feature或者issue  

### Long-running 分支 线性视图
![linear view](./pic/linear_view_of_progressive_stability_branching.jpg "linear view of progressive-stability branching")

### Long-running 分支 发射筒视图
![silo view](./pic/silo_view_of_progressive_stability_branching.jpg "silo view of progressive-stability branching")

### Topic分支  
Topic分支是一种为了开发某个feature、解决某个issue、修改某个bug等等创建的临时分支。  （因为branch的开销非常低，所以善用branch进行阶段性的开发、合并，可以帮助开发者有效管理开发之路。）  

**举个例子:**
master分支是主版本  
iss91分支是解决#91 issue所创建的分支  
iss91v2分支是解决#91 issue所创建的第二种方案  
dumbidea分支是突然出现的灵感，可能没有什么意义，可能是绝佳的设计  

![multiple topic branches](./pic/multiple_topic_branches.jpg "multiple topic branches")


最终合并dumbidea 和 iss91v2两个分支到master，同时删除iss91分支
![merging dumbidea and iss91v2 deleate iss91](./pic/merging_dumbidea_and_iss91v2_deleate_iss91.jpg "merging dumbidea and iss91v2 deleate iss91")


## 远程分支  
远程分支是远程仓库所包含的分支，可以通过一下命令查看特定远程仓库的分支、标签等信息。  
>$ `git ls-remote <remotename>`  
>$ `git remote show <remotename>`  

### remote-tracking 分支  
remote-tracking分支是远程服务器分支的一个标记，由`remote/branch` 显示。`origin/iss53`代表origin远程仓库的iss53分支。每次和远程仓库通信， remote-tracking状态都会被更新。  

**举个例子**  
master这个分支你在local开发， 别人也开发了并推送到remote
  
![local and remote](./pic/local_and_remote_work_can_diverge.jpg "local and remote")

此时可以通过`git fetch remotename`命令来同步remote-track分支的最新数据。  
![git fetch](./pic/git_fetch_update_remote_tracking_branches.jpg "git fetch")   

### 推送分支  
>$ `git push remotename branchname` #将本地分支推送到远程仓库  
>$ `git push remotename branchname:newname` #将本地分支推送到远程仓库，该分支在远程仓库重命名未  
>$ `git fetch remotename` #从远程仓库获得最新remote-tracking分支  
>通过`get fetch`获得的remote-tracking分支的时候，比如`origin/iss53`,该分支在本地并不可以编辑开发。  
>如果想要将`origin/iss53`合并到自己分支，可以使用`git merge origin/iss53`命令  
>如果想要一个自己继续开发的iss53分支，可以使用`git checkout -b iss53 origin/iss53`命令

### 追踪分支  
>$ `git checkout -b [branch] [romote]/[branch]` #从远程仓库拉取某个分支，用于自己开发  
>$ `git checkout --track origin/serverfix` #从远程仓库拉去serverfix分支用于开发，这里使用`--track`参数   
>$ `git checkout serverfix` #如果本地没有serverfix，远程仓库有唯一serverfix，那么也可直接`git checkout`来拉去远程分支  
>$ `git checkout -b sf origin/serverfix` #从远程仓库origin拉取serverfix分支，并重命名为sf  
>$ `git branch -u origin/serverfix` #设置本地分支关联到远程origin仓库的serverfix分支，或者修改本地分支关联的远程仓库分支  
> `-u` 或者 `--set-upstream-to` 选项用于`git branch`命令关联本地分支与远程分支  
> 

TIP:
> 已经关联远程分支,可以使用`@{u}`或者`@{upstream}` 来代表远程分支  
> 举个例子：  
> $ `git checkout master`
> $ `git merge @{u}`  #作用如下  
> $ `git merge origin/master`  

查看本地和远程分支关联信息  
>$ `git branch -vv` #查看所有本地分支，并显示相关联的原程分支，以及commit提交差异信息  
    iss53 7e424c3 [origin/iss53: ahead 2] Add forgotten brackets  
    master 1ae2a45 [origin/master] Deploy index fix    
    serverfix f8674d9 [teamone/server-fix-good: ahead 3, behind 1] This should do it  
    testing 5ea463a Try something new  
`ahead 3`代表本地比远程分支多3次未推送的commit  
`behind 1`代表本地比远程分支少同步1次commit  
>$ `git fetch -all`;`git branch -vv` #在查看前先从拉去远程仓库最新数据，这样可以确保数据及时性  

### Pulling  
使用`git fetch`命令获取服务器数据时并不会修改本地数据，获得数据可以理解为只读数据，你需要通过`git merge`命令自行合并。  
`git pull`命令等同于 `git fetch` + `git merge`  ，如合`git pull`不确定100%成功，建议分布执行`fetch` 和 `merge`  

### 删除远程分支  
>$ `git push origin --delete serverfix` #删除远程仓库origin 的 serverix分支  

## Rebasing 
**rebasing和merge一样都是将一个分支合并到另一个分支。** 


>merge是将一个分支的末次commit合并到另一个分支去。  
>$ `git checkout master`  
>$ `git merge experiment`  
![merging](./pic/merging.jpg "git merge")   

>rebase是将一个分支的所有commit移动到另一个分支去，整个分支作为另一个分支线性工作的一部分。  
>rebase 会使整个工作过程变得线性、整洁(删除原来的分支commit信息)。  
>**!!!切记!!!**   Do not rebase commits that exist outside your repository and that people may have based work on.  
>**!!!切记!!!**   Do not rebase commits that exist outside your repository and that people may have based work on.  
>**!!!切记!!!**   Do not rebase commits that exist outside your repository and that people may have based work on.  
>$ `git checkout experiment`  
>$ `git rebase master`  
>$ `git checkout master`  
>$ `git merge experiment`
![rebasing](./pic/rebasing.jpg "git rebase")   
![fast_forwarding_after_rebase](./pic/fast_forwarding_after_rebase.jpg "git rebase")   


### 强大的rebase
rebase可以跨分支移动。举个例子：  


>现在有如下三个分支，其中client分支基于server分支创建
![before_rebase](./pic/before_rebase.jpg "before rebase")   

>将client分支rebase到master分支  
>$ `git checkout client`  
>$ `git rebase --onto master server client`  
![after rebase client](./pic/after_rebase_client.jpg "after rebase client")   


>快速合并master 
>$ `git checkout master`  
>$ `git merge client`  
![after forward](./pic/after_forward.jpg "after forward")   


>将server分支rebase到master分支  
>$ `git checkout server`  
>$ `git rebase master server `  
![after rebase server](./pic/after_rebase_server.jpg "after rebase server")   


>快速合并master，并删除server client分支  
>$ `git checkout master`  
>$ `git merge server`    
>$ `git branch -d server`  
>$ `git branch -d client`  
![final_commit](./pic/final_commit.jpg "final_commit")   


# ***rebase local changes before pushing to clean up your work, but never rebase anything that you’ve pushed somewhere.***


















