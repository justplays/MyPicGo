# 一、前期准备

**在windows下安装Git工具**

Git下载地址：https://git-scm.com/download/win

# 二、配置Git环境

## 1.进入Git Bash

点击 "Git Bash" 打开 Git 命令控制台

## 2.生成秘钥文件

```sh
ssh-keygen -t rsa -C "myMailbox@163.com"
#在控制台输入上面指令并连续敲 3 次回车即可
```

> "myMailbox@163.com" 是你的邮箱地址

## 3.查看生成的密钥

```sh
cat .ssh/id_rsa.pub
```

## 4.配置SSH keys

进入GitHub，登录用户，点击用户头像指示的三角图标选择 "**Settings**"，然后选择 "**SSH and GPG keys**"，点击右侧 "SSH keys" 栏中的 "**New SSH key**" 按钮进行配置（其中 Title 可以自己随意起一个名字，而 Key 的内容就是将 "id_rsa.pub" 文件中的内容全部复制过来即可），点击 "**Add SSH key**" 按钮完成操作，此时在你填写的邮箱中会收到一封确认的邮件可以不用管它。

## 5.验证是否配置成功

```sh
ssh -T git@github.com
```

> 1. 当提示输入（yes/no）? 时，在后面输入 yes 回车即可，如果看到欢迎语 "Hi xxx! You've successfully authenticated, but GitHub does not provide shell access" 则表示配置成功。
>
> 2. 如果提示类似 `ssh: Could not resolve hostname \342\200\223t: Name or service not known` 的错误，解决办法是执行命令：ssh -t -p 22 git@github.com（其中 -p 表示修改服务器端口为22）。

## 6.配置身份标识

```sh
git config --global user.name "userName"
git config --global user.email "myMailbox@163.com"
```

> "userName" 和 "myMailbox@163.com" 分别是你自己的用户名和邮箱。

# 三、创建本地管理仓库

## 1.创建本地管理仓库

```sh
mkdir /e/myGitHub
```

## 2.初始化本地管理仓库

```sh
cd /e/myGitHub
git init
```

> 初始化必须进入到本地管理仓库的根目录下面。

## 3.添加远程仓库管理

```sh
git remote add origin git@github.com:UserName/Repository
```

> 其中 `UserName/Repository` 是我们 GitHub 中项目仓库地址，"UserName" 是我们在 GitHub 网站上注册时使用的用户名，"Repository" 是我们为这个项目建立的仓库名。

# 四、拉取

> 每次需要修改GitHub仓库中文件时先进性操作

```sh
#进入本地版本管理库文件夹
cd /e/myGitHub
#拉取仓库中的所有资源到本地
git pull origin master
```

> 执行如上命令成功后在将会在本地仓库的根目录下生成从远程仓库同步下来的所有文件。

# 五、Windows操作

**Windows资源管理器中进行文件的更改**

# 六、上传

![](https://cdn.jsdelivr.net/gh/justplays/MyPicGo/img/202208051511384.png)

## 1.添加当前更改或新增

```sh
git add .
```

> "add" 后面加点意思就是将本地管理仓库中的所有内容添加到工作空间中。

## 2.提交当前工作空间

```sh
git commit -m "update"
```

> "update" 是提示信息，可以是任何内容。此提示信息是一定要写的，不仅是规则，同时也方便我们记录此次操作的是什么内容。

## 3.推送到远程仓库

```sh
git push --all -f
```

> 强推，即利用覆盖方式将你本地的代码替代 GitHub 仓库内的内容
