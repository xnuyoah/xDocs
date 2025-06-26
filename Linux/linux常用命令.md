### **一、文件与目录操作**

| **命令** | **功能**                   | **示例**                                                     |
| :------- | :------------------------- | :----------------------------------------------------------- |
| `ls`     | 列出目录内容               | `ls -l`（详细列表） `ls -a`（含隐藏文件）                    |
| `cd`     | 切换目录                   | `cd /home`（进入 home 目录）                                 |
| `pwd`    | 显示当前工作目录           | `pwd`                                                        |
| `mkdir`  | 创建目录                   | `mkdir new_dir`                                              |
| `rmdir`  | 删除**空**目录             | `rmdir empty_dir`                                            |
| `touch`  | 创建空文件或更新文件时间戳 | `touch file.txt`                                             |
| `cp`     | 复制文件/目录              | `cp file1.txt file2.txt` `cp -r dir1/ dir2/`（递归复制目录） |
| `mv`     | 移动/重命名文件或目录      | `mv old.txt new.txt`（重命名） `mv file.txt ~/Documents/`（移动） |
| `rm`     | 删除文件/目录              | `rm file.txt` `rm -rf dir/`（强制递归删除）⚠️ **慎用**        |
| `find`   | 搜索文件                   | `find /home -name "*.log"`（按名称搜索）                     |

------

### **二、文件内容查看与处理**

| **命令**        | **功能**                    | **示例**                                                     |
| :-------------- | :-------------------------- | :----------------------------------------------------------- |
| `cat`           | 显示文件全部内容            | `cat file.txt`                                               |
| `less` / `more` | 分页查看文件（推荐 `less`） | `less large.log`（支持上下翻页）                             |
| `head`          | 显示文件开头部分            | `head -n 10 file.log`（前10行）                              |
| `tail`          | 显示文件结尾部分            | `tail -f app.log`（实时跟踪日志）                            |
| `grep`          | 文本搜索工具                | `grep "error" /var/log/syslog` `grep -r "pattern" /dir/`（递归搜索） |
| `sed`           | 流编辑器（文本替换/处理）   | `sed 's/old/new/g' file.txt`（全局替换）                     |
| `awk`           | 文本分析/处理语言           | `awk '{print $1}' file.txt`（打印第一列）                    |

------

### **三、系统信息与监控**

| **命令**       | **功能**                      | **示例**                       |
| :------------- | :---------------------------- | :----------------------------- |
| `top` / `htop` | 实时进程监控（`htop` 更强大） | `htop`（需安装）               |
| `ps`           | 查看进程状态                  | `ps aux`（显示所有进程）       |
| `free`         | 查看内存使用                  | `free -h`（人类可读格式）      |
| `df`           | 磁盘空间使用情况              | `df -h`（显示挂载点使用率）    |
| `du`           | 目录/文件大小                 | `du -sh /dir/`（汇总目录大小） |
| `uname`        | 系统信息                      | `uname -a`（内核/系统详情）    |
| `lscpu`        | CPU 信息                      | `lscpu`                        |
| `uptime`       | 系统运行时间与负载            | `uptime`                       |

------

### **四、权限管理**

| **命令** | **功能**               | **示例**                                              |
| :------- | :--------------------- | :---------------------------------------------------- |
| `chmod`  | 修改文件权限           | `chmod 755 script.sh` `chmod +x file`（添加执行权限） |
| `chown`  | 修改文件所有者         | `chown user:group file.txt`                           |
| `sudo`   | 以超级用户权限执行命令 | `sudo apt update`                                     |
| `passwd` | 修改用户密码           | `passwd`（当前用户）                                  |

------

### **五、网络操作**

| **命令**          | **功能**                   | **示例**                                           |
| :---------------- | :------------------------- | :------------------------------------------------- |
| `ping`            | 测试网络连通性             | `ping google.com`                                  |
| `curl`            | 数据传输工具（HTTP/FTP等） | `curl -O https://example.com/file.zip`（下载文件） |
| `wget`            | 网络下载工具               | `wget http://example.com/file.iso`                 |
| `ssh`             | 远程登录                   | `ssh user@192.168.1.100`                           |
| `scp`             | 安全复制文件               | `scp file.txt user@remote:/path/`                  |
| `netstat`         | 网络连接/端口信息          | `netstat -tuln`（监听中的端口）                    |
| `ifconfig` / `ip` | 网络接口配置               | `ip addr show`（显示IP地址）                       |

------

### **六、压缩与解压**

| **命令**          | **功能**       | **示例**                                                     |
| :---------------- | :------------- | :----------------------------------------------------------- |
| `tar`             | 打包/解包文件  | `tar -cvf archive.tar dir/`（打包） `tar -xvf archive.tar`（解包） |
| `gzip` / `gunzip` | GZIP 压缩/解压 | `gzip file.txt` → `file.txt.gz`                              |
| `zip` / `unzip`   | ZIP 压缩/解压  | `zip archive.zip file1 file2` `unzip archive.zip`            |

------

### **七、包管理（常见发行版）**

| **系统**      | **安装软件**               | **更新系统**                          |
| :------------ | :------------------------- | :------------------------------------ |
| Debian/Ubuntu | `sudo apt install package` | `sudo apt update && sudo apt upgrade` |
| CentOS/RHEL   | `sudo yum install package` | `sudo yum update`                     |
| Arch/Manjaro  | `sudo pacman -S package`   | `sudo pacman -Syu`                    |

------

### **八、进阶工具**

| **命令**           | **功能**                |                           |
| :----------------- | :---------------------- | ------------------------- |
| `cron` / `crontab` | 定时任务管理            |                           |
| `systemctl`        | 管理系统服务（systemd） | `systemctl start nginx`   |
| `journalctl`       | 查看系统日志（systemd） | `journalctl -u nginx`     |
| `rsync`            | 高效文件同步            | `rsync -av source/ dest/` |
| `lsof`             | 查看打开的文件/端口     | `lsof -i :80`             |

### **九、学习资源推荐**

1. **官方文档**
   - `man <命令>`：查看命令手册（如 `man ls`）
   - `tldr <命令>`：简化版手册（需安装 `tldr` 工具）
2. **在线指南**
   - [Linux Command Library](https://linuxcommandlibrary.com/)（命令速查）
   - [ExplainShell](https://explainshell.com/)（命令解析工具）

**提示**：

- 使用 `Ctrl + C` 终止当前命令，`Ctrl + D` 退出终端。
- 谨慎使用 `rm -rf /` 或 `sudo` 命令，避免系统损坏。
- 组合命令：`|`（管道）、`>`（输出重定向）、`>>`（追加输出）。