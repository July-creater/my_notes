<span style="font-family: hack, kaiti;">

# Git常用

## 1. git 配置本地仓库和远程仓库

### 1. 初始化本地仓库

如果你还没有本地仓库，首先要在你的计算机上创建一个新的 Git 仓库。在你希望创建仓库的目录中，打开终端并运行以下命令：

```bash
git init
```

### 2. 将文件添加到本地仓库

```bash 
git add .
```

### 3. 提交文件到仓库

```bash 
git commit -m "Initial commit"
```

### 4. 配置远程仓库

在 GitHub 或其他 Git 托管服务上创建一个远程仓库。然后，将远程仓库的 URL 添加到本地仓库中，使用以下命令：

```bash 
git remote add origin <remote_repository_URL>

# 将远程仓库中可能生成的license等拉到本地目录
git pull origin master --allow-unrelated-histories

```

### 5. 将本地更改推送到远程仓库

```bash 
git push -u origin master
```

## 2. git 配置作者，邮箱

当你在Git中提交代码时，会将提交者的姓名和邮箱地址作为作者信息记录在提交历史中。下面是设置Git作者姓名和邮箱的步骤：

### 1. 配置全局作者信息

运行以下命令来配置全局作者姓名和邮箱：

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```
将 "Your Name" 替换为你的姓名，"your.email@example.com" 替换为你的邮箱地址。

### 2. 配置单个仓库的作者信息

如果你想针对某个特定的Git仓库设置不同的作者信息，可以在该仓库的目录中运行类似的命令，但去掉 --global 参数：

```bash
git config user.name "Your Name"
git config user.email "your.email@example.com"
```

### 3. 检查配置信息

你可以使用以下命令检查已配置的作者信息：

``` bash
git config user.name
git config user.email
```













</span>