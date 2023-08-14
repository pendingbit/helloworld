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


