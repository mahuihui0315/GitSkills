# GitHub

## 安装Git
1. 链接
> https://git-scm.com/downloads

2. 初始化user.name/email
> git config --global user.name "#"
> git config --global user.email "#"

### 修改主目录路径
+ 新建用户环境变量
> 名称：Home, 值：希望更改的目标路径

## 基本操作
+ 进入文件夹: cd directoryname
+ 退出文件夹：cd ..
+ 新建文件夹: mkdir 文件夹名称
+ 打印当前文件夹: pwd

## 创建repository
1. 将文件夹初始化为repository: git init
2. 向repository中添加文件
   1. 文件夹下新建文件
   2. git add 文件名
   3. git commit -m "文件描述"
   
## 文件管理

+ git status：查看当前状态
> 有文件修改会提示, 查看修改详情git diff

### 版本回退

#### git log：查看修改记录
```
commit c959b513bbe84fcbf2e93a6ae3f11e2524389011 (HEAD -> master)
Author: mahuihui0315 <mhhmhhmhh@outlook.com>
Date:   Mon Mar 11 20:43:56 2019 +0800
add GPL
```
+ commit id是由SHA1计算出来的16进制数字
+ HEAD表示当前版本
+ add GPL表示提交时的说明
+ q：退出log界面

#### 通过HEAD回退
回退操作只是将HEAD指针指向不同版本，因此速度很快

+ 回退上个版本: git reset --hard HEAD^
+ 回退上上个版本: git reset --hard HEAD^^
+ 回退100个版本: git reset --hard HEAD~100

#### 通过commit id回退
+ git reset --hard <commit id>
+ id不需要写全，Git会自动匹配
+ 查询所有操作记录来寻找commit id: git reflog

## 工作区和版本库

### 工作区
自己建立的文件夹，例如learngit

### 版本库repository
工作区下的.git文件夹
+ stage暂存区：暂时存放git add添加进来的数据
+ master: Git创建的唯一master分支，接收git commit提交的数据

## 文件修改
1. 管理修改

> Git跟踪并管理的是修改而非文件   
若同一文件修改两次，只有第一次进行add操作，则提交时只会由一次修改记录。即，只有add进stage的修改才会被commit

2. 撤销修改
> 撤销工作区的修改: git checkout -- <filename>   
> 撤销stage中的add: git reset HEAD <filename>

3. 删除文件
> 删除: git rm <filename>   
> 提交: git commit -m ""
4. 撤销删除
> git checkout -- <filename>

## 远程仓库
1. 生成密钥

`ssh -keygen -t rsa -C "email address"`   

主目录下.ssh文件夹
+ id_rsa：私钥
+ id_rsa.pub：公钥

2. GitHub添加公钥

为了让GItHub可以识别本地主机, 
可以提交多个不同主机的公钥

3. 与GItHub上的repository建立连接

进入需要建立连接的本地repository文件夹,

`git remote add origin git@github.com:mahuihui0315/hello-world.git`

4. 推送本地文件到GitHub
+ 第一次推送

`git push -u origin master`

会弹出警告框，输入yes继续
+ 非第一次推送

`git push origin 分支名`

5. 克隆远程repository

进入放置克隆repository的目的文件夹

`git clone <SSH>`