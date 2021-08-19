##### 0、参考文档
1. [Git教程（完整）](https://blog.csdn.net/weixin_42152081/article/details/80558282)
2. [Git版本恢复命令reset和revert](https://blog.csdn.net/xybelieve1990/article/details/62885292)
3. [github官方指引](https://guides.github.com/activities/hello-world/)
##### 1、创建项目
0. 安装Git
```
sudo apt -get install git

// 设置用户名，邮箱
git config --global user.name=username
git config --global user.email=email
```

1. 创建一个空目录，作为项目的根目录
```
mkdir learngit
```

2. 初始化，设置为一个git仓库
```
cd learngit
git init
```

3. 创建完毕

##### 2、客户端使用
0. 与SVN的差异
- 以本地作为一个仓库，修改提交都在本地生效，只有最后的推送到远程才是代码上交合并；SVN的每次修改提交都是最终的代码上交合并
- 本地仓库存在工作区、暂存区、仓库三个概念，所有需要提交的必须先放入暂存区，所有的提交都仅仅是把暂存区放入仓库，工作区依然可以存在差异；SVN没有暂存区的概念，提交则提交当前工作区
- 
1. 添加文件
```
git add filename // 指定文件
git add . // 当前目录所有
```
2. 提交到仓库
```
git commit -m "备注信息" // 把stage里的内容提交到仓库
git commit -a -m "备注信息" // 把modified、deleted放入stage并提交到仓库，Untracked files则不生效，慎用
```
- 只有放入了stage缓存区的内容才会被提交
- 缓存区需要执行```git add```才会被放入
- ```git commit -a```会把变动的文件(新文件不生效)放入stage并提交到仓库，慎用
3. 查看状态，差异
```
git status // 查看状态
# nothing to commit, working tree clean 当前没有需要提交的修改，而且，工作目录是干净的。
# Changes to be commited 将要被提交的文件
# Changes not staged for commit 没有文件将要被提交

git diff // 查看当前具体变动内容
```
4. 查看日志
```
git log --pretty=oneline
```
5. 回退版本，撤销修改
- 本地回退，未进入stage
```
git checkout --filename // 直接checkout文件即可
git checkout . // 本地所有回退

// 或使用restore
git restore filename // 把工作区的某个文件撤销
git restore . // 放弃所有修改
```
- 已提交到stage
```
git restore --staged filename // 把暂存区的某个文件撤销

// 或者使用reset
git rest HEAD filename // 指定文件撤回
git rest HEAD . // 放弃所有缓存
```
- 已commit
```
git reset --hard HEAD^ // 回退到上一版本 HEAD^^(上两个版本)
git reset --hard 0455g // 指定版本，一般取commit id的前5位
```
- 已提交到remote，需要回退版本
```
git revert commit-id // 回滚到某个提交
git commit -a -m "重新提交回滚后的内容即可回到之前版本"
git push origin master
```
- reset与revert的区别
>第一:上面我们说的如果你已经push到线上代码库, reset 删除指定commit以后,你git push可能导致一大堆冲突.但是revert 并不会.

>第二:如果在日后现有分支和历史分支需要合并的时候,reset 恢复部分的代码依然会出现在历史分支里.但是revert 方向提交的commit 并不会出现在历史分支里.

>第三:reset 是在正常的commit历史中,删除了指定的commit,这时 HEAD 是向后移动了,而 revert 是在正常的commit历史中再commit一次,只不过是反向提交,他的 HEAD 是一直向前的.


6. 拉取
```
git fetch // 获取
git merge // 合并

// 也可合并使用
git pull
```
7. 分支
```
查看各个分支当前所指的对象   git log --oneline --decorate

项目分叉历史  git log --oneline --decorate --graph --all

分支创建  git branch testing

分支切换  git checkout testing

创建加切换 git checkout -b testing

分支都会向前移动一步  git commit -m "A"  (ABCD....)

创建分支 git checkout dev

代表切换分支   git checkout -b  dev 

查看当前分支 git branch

提交分支 git add readme.txt 

创建分支下的分支  git commit -m "d"      (git commit -m “branch test”)

把分支移到主分支上 git checkout master

合并分支   git merge dev

删除分支  git branch -d dev
————————————————
版权声明：本文为CSDN博主「bobob_」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/dubo_csdn/article/details/81743495
```


##### 3、github
1. SSH
> github拉代码需要ssh验证

> git是分布式的代码管理工具，远程的代码管理是基于ssh的，所以要使用远程的git则需要ssh的配置。
- 1. 生成秘钥
```
ssh-keygen -t rsa -C "github邮箱"
按3个回车，密码为空这里一般不使用密钥。
最后得到了两个文件：id_rsa和id_rsa.pub
```
- 2. 在github上配置
```
Account>settings>SSH and GPG keys>添加sshkey
在github上添加ssh密钥，这要添加的是“id_rsa.pub”里面的公钥
```
- 3. 测试是否成功
```
ssh -T git@github.com
回复yes，若出现了你github的昵称则设置成功
```

2. 上传到github
- 在项目里设置remote地址
```
git remote add origin git@github.com:lpp864019150/learngit.git
```
- 上传
```
git push -u origin master
```
3. clone
```
git clone -b branches git@github.com:lpp864019150/learngit.git dirname // 可以设置本地目录名，默认为远程同名
// 可以使用-b指定clone的分支，默认为master
```
4. create pull request 
```
git pull
git push
```


##### 4、



##### 5、



