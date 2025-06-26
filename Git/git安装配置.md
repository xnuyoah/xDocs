## **Git 安装、配置**

### 安装

> Windows: 前往 [Git 官网](https://git-scm.com/) 下载最新版本，默认选项安装即可

```bash
# Ubuntu 22.04
sudo apt update
sudo apt install git
```

### 设置用户/邮箱

```bash
# 查看 git 配置项
git config --list
git config --global user.name "username"
git config --global user.email "email"
```

### 生成 `ssh` 密钥

```bash
ssh-keygen -t rsa -b 4096 -C "email"

# 按三下回车, 得到 id_rsa, id_rsa.pub 文件
# 路径: home/[user]/.ssh 或 c:/User/[user]/.ssh
```

#### 多个密钥

```bash
ssh-keygen -t rsa -C "email" -f /path/to/.ssh/id_rsa_<后缀>
```

- `config` 配置

  ```bash
  # 配置 Github
  Host github.com
      HostName ssh.github.com
      IdentityFile /path/to/.ssh/id_rsa_github
      PreferredAuthentications publickey
      User <username>
  
  # 配置 gitee
  Host gitee.com
      HostName gitee.com
      IdentityFile /path/to/.ssh/id_rsa_gitee
      PreferredAuthentications publickey
      User <username>
  ```
  
- 校验

  ```bash
  ssh -T git@github.com
  ssh -T git@gitee.com
  ```

### `Git` 三个区域

- 工作区 -> 开发者编写及修改代码区域
- 暂存区 -> 临时存放文件的修改，工作区的文件提交及回滚交互
- 本地仓库 -> 存放代码及数据位置，包含所有提交版本。`HEAD` 指向最新提交版本
- 远程仓库 -> 与本地仓库链接的 `git` 仓库，用于代码交换

### `Git` 常用命令

#### 配置相关

- 查看配置

  ```bash
  # 全局
  git config --global --list
  
  # 非全局
  git config --list
  ```

- 添加/删除配置

  ```bash
  # 添加
  # 全局
  git config --global user.name "username"
  # 非全局
  git config user.name "username"
  
  # 删除
  # 全局
  git config --global --unset user.name
  # 非全局
  git config --unset user.name
  ```

#### 本地仓库相关

- 创建本地仓库

  ```bash
  git init
  ```

- 克隆远程仓库

  ```bash
  git clone xxx.git
  ```

- 查看当前仓库状态

  ```bash
  git status
  ```

- 将修改从工作区提交到暂存区

  ```bash
  # 单文件
  git add 文件名
  
  # 所有
  git add .
  
  # 文件在工作区被删除, 同步到暂存区
  git rm 文件名
  ```

- 将修改提交到仓库

  ```bash
  git commit 文件名 -m "提交信息"
  
  # 修改提交信息
  git commit --amend -m "新的提交信息"
  ```

#### 提交记录

- 查看提交记录

  ```bash
  git log
  ```

#### 远程仓库

- 添加远程仓库

  ```bash
  git remote add origin xxx.git
  ```

- 显示当前远程仓库信息

  ```bash
  git remote -v
  ```

- 删除已绑定的远程仓库

  ```bash
  git remote rm origin
  ```

- 切换远程仓库地址

  ```bash
  git remote set-url origin xxx.git
  ```

- 拉取远程分支到本地

  ```bash
  git checkout -b 分支名 origin/分支名
  ```

- 关联本地和远程分支

  ```bash
  git branch --set-upstream-to=origin/分支名 分支名
  ```

#### 分支相关

- 查看所有分支

  ```bash
  git branch -l
  ```

- 查看当前分支

  ```bash
  git branch
  ```

- 创建分支

  ```bash
  git branch 分支名
  ```

- 切换分支

  ```bash
  git checkout 分支名
  ```

- 创建并切换分支

  ```bash
  git checkout -b 分支名
  ```

- 删除分支

  ```bash
  git branch -d 分支名
  # 分支没有合并的提交, 推荐使用 -D
  ```

### **使用 `access_token` 拉取项目**

```bash
# 1. 访问 Gitlab
# 2. settings >> access token
# 3. create personal access token
# 添加全局
git config --global url."https://oauth2:<access_token>@xxx.xxx.com".insteadof "https://xxx.xxx.com"
```

### 取消 `ssl` 验证

```bash
git config --global http.sslverify false
```

