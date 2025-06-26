## 1.**`skopeo` 命令行工具查看镜像版本**

### 安装 `skopeo`

```bash
# Ubuntu/Debian
# sudo apt-get install skopeo
sudo apt install skopeo
# CentOS
sudo yum install skopeo
```

### 查询镜像标签列表

> 注意：若仓库为私有，需添加 --creds <用户名>:<密码> 参数

```bash
skopeo list-tags docker://registry.cn-hangzhou.aliyuncs.com/xeliauk/jupyterlab-uv
```

### 输出示例

```bash
{
  "Repository": "registry.cn-hangzhou.aliyuncs.com/xeliauk/jupyterlab-uv",
  "Tags": ["v1"]
}
```

## 2.**安装 `SSH` 服务**

```bash
# 更新软件包列表
sudo apt update

# 安装 OpenSSH 服务器
sudo apt install openssh-server -y

# 验证 SSH 服务是否正在运行
sudo systemctl status ssh

# 输出应显示 "Active: active (running)"

# 启用开机自动启动（默认已启用）
sudo systemctl enable ssh

# 确认启用状态（显示 "enabled" 表示成功）
sudo systemctl is-enabled ssh


# 允许 SSH 端口（默认 22）
sudo ufw allow ssh

# 或指定自定义端口（示例端口：2222）
sudo ufw allow 2222/tcp
```

## 3.`nvm` 安装

```bash
# installs nvm (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
# download and install Node.js (you may need to restart the terminal)
nvm install 22
# verifies the right Node.js version is in the environment
node -v # should print `v22.11.0`
# verifies the right npm version is in the environment
npm -v # should print `10.9.0`
```

## 4.安装`Startship`

```bash
# Linux
curl -sS https://starship.rs/install.sh | sh

# macOS
brew install starship

# Windows
# 在 https://github.com/starship/starship/releases/ 选择合适的msi包，或者通过包管理器安装
winget install --id Starship.Starship
scoop install starship
```

### 初始化

```bash
# zsh
echo 'eval "$(starship init zsh)"' >> ~/.zshrc

# Bash
echo 'eval "$(starship init bash)"' >> ~/.bashrc

# fish
echo 'starship init fish | source' >> ~/.config/fish/config.fish

# Powershell
echo 'Invoke-Expression (&starship init powershell)' >> $PROFILE
# Powershell 5 好像还不支持这种重定向？可能需要手动添加
```

### 配置 `Startship`

```bash
starship preset nerd-font-symbols -o ~/.config/starship.toml
```



