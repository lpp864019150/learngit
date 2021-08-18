##### 0、
1. [参考文档](https://blog.csdn.net/weixin_42152081/article/details/80558282)
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
```
git reset --hard HEAD^ // 回退到上一版本 HEAD^^(上两个版本)
git reset --hard 0455g // 指定版本，一般取commit id的前5位

git reset HEAD filename // 把暂存区的某个文件撤销
git restore --staged filename // 把暂存区的某个文件撤销
git restore filename // 把工作区的某个文件撤销
```



##### 3、



##### 4、



##### 5、



