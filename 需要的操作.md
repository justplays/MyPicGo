# First

**拉取仓库中master分支中的所有资源**

鼠标右键打开“**Git Bash Here**”

**输入：**

```bash
#进入本地版本管理库文件夹
cd /e/myGitHub
#拉取仓库中的所有资源到本地
git pull origin master
```

# Second

**之后Windows资源管理器中进行文件的更改**

# END

**最后推送更新后的文件夹即可**

鼠标右键打开“**Git Bash Here**”

**输入：**

```bash
#将没有被管理的文件加入git进行管理
git add .
#提交新版本到版本库，生成对应的版本记录信息
git commit -m update
#强制推送所有版本库中的资源到仓库
git push --all -f
```

