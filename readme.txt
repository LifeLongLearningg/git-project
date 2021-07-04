==================Git=====================
Git介绍 分布式版本控制工具 vs 集中式版本控制工具
Git安装
Git分支 分子特性 代码合并冲突解决等
==================GitHub==================
创建远程库
代码推送
代码拉取
代码克隆
SSSH免密登录
idea继承github
=================Gitee码云================
国内版本的gitbub
=================GitLab===================
基于局域网的代码的管理中心
idea集成GitLab


集中式和分布式的介绍:

集中式:将所有代码交给服务器集中进行版本控制,多态计算机在服务器上调取项目,并求改再回传给服务器
分布式:每个程序员的电脑做版本控制,然后不用服务器存储项目,而是使用远程库(GitHub,码云等等)
       来存储以及调用项目代码


=================git常用命令==================
账号A:
 head文件指向了现在是哪个分支 底层就是运用指针
   命令                              功能
 要先设置username和email 然后在用户路径下会生成一个.config的文件
 git init                       是初始化本地仓库
 ll                             查看文件
 vim hello.txt                  在当前目录新建一个hello.txt的文档
 cat hello.txt                  查看hello.txt的数据
 wq                             写完后输入来保存文件
 Esc                            进入粘贴复制状态
 yy                             复制
 p                              粘贴
 tail -n 1 xxx.txt              查看xxx.txt的尾部倒数第一行的1数据是什么
 git add   xxx.txt              添加xxx.txt文件到暂存区
 git rm --cached xxx.txt        清楚暂存区的xxx.txt文件
 git commit -m "版本信息" xxx.txt 提交xxx.txt到本地库作为一个版本 ""里的名字自定义
 git reflog                     查看提交本版信息
 git log                        查看更完整的提交后的版本信息
 vim xxx.txt -> i               进入xxx.txt后按i修改它
 git reset --hard xxxxx         会到之前版本号为xxxxx的版本
 4a83af0 (HEAD -> master) HEAD@{0}: commit (initial): first commit
 4a83af0就是版本号              可以跳转到任意版本
 git branch -v                  查看所有分支
 git branch hot-fix             添加一个hot-fix分支
 git checkout hot-fix           切换当前分支为hot-fix
 git merge hot-fix              把hot-fix分支合并到当前分支上
                                合并分支冲突的时候需要手动合并
                                提交本地库时不能加文件名 不然报错
 git remote -v                   查看别名
 git remote add git-demo https://github.com/LifeLongLearningg/git-demo.git
                                这个就是为这个远程github仓库添加一个别名
				                不然每次添加到这个远程仓库都要输入绝对地址
 git push git-demo master       推送master分支下的代码到git-demo远程库(github)
 git pull git-demo matser       拉取git-demo远程库的代码到master分支下

 账号B:
                                拉取动作自动提交本地库
 账号B克隆账号A上面远程仓库的代码步骤:
 在之前账号A里要在settings-manage access里把账号B邀请进来自己的组织
 账号B在网页登录账号A生成的邀请链接,并加入
 git clone https://github.com/LifeLongLearningg/git-demo.git
                                 账号B克隆账号A的远程仓库代码
				 地址为A的仓库的地址

  团队外的人要修改代码:
  先在gihub进入账号A给的项目仓库的链接,点击右上角的fork把账号A的项目插到自己的账号下
  拉取代码修改改进好后再把他上传到自己的本地仓库
  如何让账号A看到我修改后的项目呢:
  点击Pull Request -> create pull request 可以修改项目名字 还可以加留言
  再点击pull request就提交了代码
  现在再去账号A里刷新 点击Pull Request 就看到刚才提交的项目了
  确认预览无误后点击 Merge pull request->confirm merge 项目就修改好了

  SSH协议
  ssh-keygen -t rsa -C snowsky071031@qq.com
   添加公钥,可以免密登录,以后上传代码到远程仓库就不用反复登录账号

  Idea集成git
  ①:在c盘自己的用户目录新建一个git.ignore文件,把要忽略的文件后缀加到文件中
  ②:把配置好的git.ignore路径加入到.config文件中  要把\换成/
  ③:idea中 settings->version control->Git->添加F:\GitTools\Git\bin\git.exe
  ④:VCS->import into Version Control->Create Git Repository..

  写的文件右击->Git->add 加入本地缓存中

  右下角master标志点击 -> 添加分支/合并分支都有
b
  集成github
    settings->version control->github可以使用口令登录

  VCS->Import into versionControl->Share Project on Github

  提交过后每次只需要在VCS->Git->push就可以提交到远程库了