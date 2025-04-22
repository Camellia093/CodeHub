# Git_GitHub

![](.\git.jpg)

## 一、Git 基础

### 1.1 什么是 Git？

  - Git 是个记录文件变化、管理软件版本的工具。在软件开发时，代码会不断修改，Git 能精准记住每个文件的改动，还能给不同版本的代码做好标记，方便你了解代码的演变过程。
  - 它的优势很明显：
    - **本地仓库**：就像你电脑里的私人小仓库，可离线操作，随意做代码实验，不影响他人。
    - **分支管理**：类似游戏支线任务，可从主线代码分出多个分支独立开发，互不干扰，完成后再合并。
    - **高效合并**：能快速准确地将不同分支代码合并，还可处理冲突，保证代码正常运行。

### 1.2 安装与配置

#### 安装命令

| 系统    | 安装命令                                                |
| ------- | :------------------------------------------------------ |
| Windows | 下载[Git for Windows](https://git-scm.com/download/win) |
| macOS   | brew install git                                        |
| Linux   | sudo apt-get install git (Debian 系)                    |

#### 基础配置

```
# 设置用户名（全局/本地）  --global 选项的作用是把配置应用到全局层面
git config --global user.name <你的用户名>
git config user.name <你的项目名>

# 设置邮箱
git config --global user.email <你的邮箱地址>

# 查看配置
git config --list
```

## 二、Git 常用命令速查表

### 2.1 仓库初始化

| 命令            | 说明               |
| --------------- | ------------------ |
| git init        | 初始化本地仓库     |
| git clone [url] | 克隆远程仓库到本地 |

### 2.2 文件操作

| 命令               | 说明                                                  |
| ------------------ | ----------------------------------------------------- |
| git status         | 查看文件状态(<u>未跟踪、已修改、已暂存、已提交等</u>) |
| git add <file>     | 添加单个文件到暂存区                                  |
| git add .          | 添加所有文件到暂存区                                  |
| git rm <file>      | 从仓库删除文件（同时删除本地文件）                    |
| git mv <old> <new> | 重命名文件                                            |

### 2.3 提交操作

```
# 标准提交格式
git commit -m "feat: 添加用户登录功能"   # 规范commit message

# 修正最近一次提交，将新的更改合并到最近一次提交中
git commit --amend -m "fix: 修复登录逻辑"
```

### 2.4 分支管理

```
# 查看分支
git branch          # 本地分支
git branch -r       # 远程分支
git branch -a       # 所有分支
```

![branch](.\branch.jpg)

```
# 操作分支
git branch new-feature		# 创建分支
git branch -m master main	# 将本地 master 分支重命名为 main 分支
git checkout new-feature	# 切换分支
git checkout -b new-feature	# 创建并切换分支

# 合并分支（在目标分支执行）
git merge new-feature

# 删除分支
git branch -d new-feature  # 删除本地分支
git push origin --delete new-feature  # 删除远程分支
```

### 2.5 远程仓库操作

```
# 关联远程仓库
git remote add origin <远程仓库url>

# 拉取/推送代码 以main分支为例
git pull origin main       # 拉取最新代码			远程 --> 本地
git push origin main       # 推送本地代码到远程		本地 --> 远程

# 查看远程仓库信息
git remote -v
```

![push](F:\CodeHub\git\push.jpg)



### 2.6 版本控制

```
# 查看提交历史
git log --oneline  # 简洁模式
git log -p        # 显示变更细节

# 版本回退（修改了代码并已 git commit）
git reset --hard HEAD^    # 回退到上一个版本
git reset --hard <commit-id>  # 回退到指定版本

# 恢复已删除的提交（需要知道commit-id）
git reflog		#查看本地变更历史
git reset --hard <commit-id>
```



### 2.7 撤销代码修改

```
# 修改了代码但还未 git add 到暂存区
git checkout -- <file>  	# <file> 是你想要撤销修改的文件名
git checkout -- .       	# 撤销所有文件的修改

# 修改了代码并已 git add 到暂存区，但还未 git commit
git reset HEAD <file>    # 将暂存区的修改撤销到工作目录
git reset HEAD .  		# 要撤销所有文件的暂存状态
```

## 三、GitHub 使用指南

### 3.1 注册与仓库创建

1. 访问[GitHub](https://github.com/)注册账号

1. 点击右上角 "New repository" 创建仓库

1. 填写仓库信息（名称、描述、是否公开）

1. 根据提示选择初始化设置（README/LICENSE/.gitignore）

### 3.2 本地仓库关联 GitHub

```
# 已有本地仓库
git remote add origin <远程仓库url>
git push -u origin main  # 首次推送并关联分支  -u 合并冲突项

# 新建仓库同步
echo "# my-project" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin <远程仓库url>
git push -u origin main
```

### 3.3 协作开发流程

#### 贡献者流程：

1. Fork 目标仓库到自己账号

1. 克隆自己的 Fork 仓库：git clone https://github.com/yourname/repo.git

1. 创建功能分支：git checkout -b feature-login

1. 提交代码并推送到自己的仓库：git push origin feature-login

1. 在 GitHub 上发起 Pull Request（PR）

1. 等待维护者审核合并

#### 维护者流程：

1. 查看收到的 PR，进行代码审查

1. 评论讨论修改点，要求贡献者修正

1. 确认无误后点击 "Merge Pull Request" 合并

1. 合并后删除已合并分支

### 3.4 项目管理

- **Issues**：用于跟踪 bug、功能请求、任务

- 标签分类：bug/feature/docs

- 里程碑管理版本计划

- **Projects**：可视化项目进度

- 看板模式：To Do/In Progress/Done

- **Wiki**：编写项目文档和使用说明

## 四、常见问题与解决方案

### 4.1 解决合并冲突

```
# 合并时出现冲突
git merge feature-branch	#把 feature-branch 分支上的修改合并到当前所在的分支

# 手动编辑冲突文件（标记<<<<<<< HEAD 和 ======= 之间为本地修改，>>>>>>> 为远程修改）

# 解决后添加并提交
git add conflict-file.txt
git commit -m "解决合并冲突"
```

### 4.2 忘记添加文件到暂存区

```
# 方法1：重新添加并修正提交
git add missed-file.txt
git commit --amend --no-edit  # --no-edit 选项表示保持上一次提交时使用的提交信息不变（保持原commit message）

# 方法2：单独提交
git add missed-file.txt
git commit -m "fix: 补充遗漏文件"
```

### 4.3 远程分支与本地不同步

```
# 删除本地过时分支
git branch -D old-branch  # -D 强制删除分支

# 重新拉取远程分支
git fetch origin
git checkout -b new-branch origin/new-branch	#-b 选项表示创建一个新的本地分支
#在本地创建一个名为 new-branch 的分支，并将其与远程仓库中的 origin/new-branch 分支关联起来，同时切换到这个新创建的本地分支。
```

## 五、最佳实践

### 5.1 Commit Message 规范

采用 Angular 规范：

```
<类型>(<作用域>): <描述>

<可选正文>

<可选脚注>
```

- 类型：feat/fix/docs/style/refactor/test/chore

- 作用域：如 login/signup/api 等模块名

- 示例：fix(login): 修复密码输入框校验逻辑

### 5.2 分支命名规范

```
# 功能分支
feature/add-login

# bug修复分支
fix/input-error

# 热修复分支
hotfix/production-bug

# 文档分支
docs/update-readme
```

### 5.3 安全设置

- 启用 2FA（两步验证）

- 设置仓库访问权限（Collaborators/Teams）

- 使用 Dependabot 管理依赖安全
