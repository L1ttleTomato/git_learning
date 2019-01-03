# GitHub的使用 #
## 1.环境配置-安装Git ##
在电脑上安装Git
## 2.上传GitHub项目 ##
###1. 配置公钥

首先，需要创建我们自己的电脑和github上远程仓库的一个连接，本地Git仓库和Github仓库之间的传输是通过SSH加密的，所以连接时需要配置一下加密的公钥和密钥。先看一下你C盘用户目录下有没有.ssh目录，有的话看下里面有没有id_rsa和id_rsa.pub这两个文件，没有就通过下面命令创建：

直接在桌面右击-git bash，输入命令行语句 
> ssh-keygen -t rsa -C "注册github的邮箱地址"

然后在C:\Users\student（你的用户名）下会找到一个.ssh文件夹，点击进入，会有id_rsa和id_rsa.pub这两个文件，右击记事本打开id_rsa.pub，复制里面的全部内容，登录Github，找到右上角的图标，打开点进里面的Settings，再选中里面的SSH and GPG KEYS，点击右上角的New SSH key，然后Title里面随便填，再把刚才id_rsa.pub里面的内容复制到Title下面的Key内容框里面，最后点击Add SSH key。至此，你的计算机和github账户就建立了一个连接，换电脑需要重新添加公钥。

###2.git上传项目到github账户
进入你需要上传的项目的根目录（必须是要上传的项目的根目录下），右击-git bash，以下是一系列的命令行语句：

> git config --global user.name "你的github用户名"  
> git config --global user.email "你的github账户邮箱"

（末尾添加两个空格用于换行）
> git init （会生成一个.git隐藏文件夹）  
> git add .（添加你需要上传的文件，后面跟指定文件名，. 代表该文件夹下全部文件）  
> git commit -m "提交时的注释信息"（这个操作是将文件提交到本地仓库）

你的github页面右上角有一个加号，点击加号，new repository新建一个公开的仓库，（私有的要钱）：  
一般同时要生成一个README.md文件，也就是描述你的项目用的。  
点击项目界面的右侧clone or download，复制.git结尾的仓库地址  
> git remote add origin 仓库地址

将本地仓库和远程仓库绑定到一起
> git pull --rebase origin master  

这个操作是把你github项目上的文件拉到本地，如果github上的文件本地没有，本地文件是无法push上去的，现在你的仓库里有一个README文件，所以要先下拉到本地才能执行上传操作，执行完以后你本地应该是有一个README.md的）

> git push origin master

**先PULL再PUSH**
###3.Github删除文件
如果直接在项目里删除不需要的或者误上传的文件，然后执行git add， git commit，git push一系列的操作，但是结果会是上传失败，为什么呢？原因和之前我们需要进行pull操作是一个，因为github仓库上的文件你本地没有，他就会让你进行pull操作，但是删掉的文件就又会被pull下来，白删了，删文件也是需要用命令行语句删的：

> git rm "需要删除的文件名"  
> git push origin master

###4.Github更新文件
比如你修改了一些文件，  
> git status （查看文件状态，这时下面会出现红色的提示  modified 你修改了的文件）  

> git add "你修改了的文件名"（这时你再git status就会发现之前红色的字变成了绿色）  

> git commit  -m "注释信息"  

> git push origin master  
