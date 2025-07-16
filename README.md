# AI学习笔记

## 首先自学python基础——常用库——机器学习——深度学习

### 25.07.15安装合适软件记录学习笔记（Github+Typora）

### 1. 安装了Git

### 2. 学习了Git初始化 : 

1. 初始化Git：cd 文件夹路径 或 在目标文件夹空白处按住 `Shift + 右键` → 选择 **“在此处打开 PowerShell 窗口”**

2. 输入：`git init` 

    输出：`Initialized empty Git repository in D:/xxx/.git/`

3. 验证仓库状态：输入：`git status` 

    输出：`No commits yet `（前提是新仓库，连readme.md都没有）

### 2. 安装了 **Visual Studio Code（VS Code）**（需重启装到Path里）  

### 3. 安装了Typora

1. 用Typora创建笔记
2. 将文件夹拖拽到Typora打开，新建文件命名为*README.md*
3. 输入一些内容并保存（Ctrl+S）

### 4. 将笔记提交到本地Git

1. 在命令行打开学习笔记文件夹路径后，输入`git add .`  （添加所有文件到暂存区）

   【Tips】若电脑提示*** Please tell me who you are.说明你需要告诉电脑你是谁。

   输入：`git config --global user.email "你的邮箱@example.com"`

   `git config --global user.name "你的名字"`

   若想确认一下是否保存，可以输入：`git config --global --list`

   会输出：`user.email=你的邮箱 user.name=你的名字`  

   之后继续提交就可以啦

2. 提交记录版本，输入：`git commit -m "第一次提交：创建README笔记"`  （双引号内的内容是给人提醒用的，便于定位历史版本）

3. 查看状态，输入：`git status`

4. 本地仓库提交历史查看：输入：`git log`  

   （举例）输出：`commit d3b7a1f9 (HEAD -> main)  `

   `Author: Your Name <your@email.com>
   Date:   Mon Jul 1 12:00:00 2024 +0800`

   `第一次提交：创建README笔记`(这就是双引号的内容)

### 25.07.16将笔记和Github远程连线+学习记笔记的语法+python第一课

### 1. 将昨天的笔记提交到Github

1. **先创建SSH密钥**

   用行命令打开笔记文件路径后输入：`ssh-keygen -t ed25519 -C "your_email@example.com"`(-t ed25519：指定密钥类型；-C“邮箱”：建议用GitHub绑定邮箱)

   会输出以下内容：

   ```
   Generating public/private ed25519 key pair.
   Enter file in which to save the key (/c/Users/you/.ssh/id_ed25519):  # 直接回车（默认路径）
   Enter passphrase (empty for no passphrase):  # 直接回车（不设密码）
   Enter same passphrase again:  # 再次回车
   ```

   成功后会输出：

   ```
   Your identification has been saved in /c/Users/you/.ssh/id_ed25519
   Your public key has been saved in /c/Users/you/.ssh/id_ed25519.pub
   ```

   在文件管理器中搜索：*%USERPROFILE%\\.ssh，会出现两个文件：

   `id_ed25519`（私钥，**切勿泄露**）

   `id_ed25519.pub`（公钥，txt打开，可粘贴到 GitHub）

2. **添加SSH公钥至GitHub：**[GitHub SSH Keys 设置页](https://github.com/settings/keys)  

   点击 **New SSH key**

   - **Title**: 填设备名（如 `My-Laptop`）
   - **Key type**: 保持默认 `Authentication Key`
   - **Key**: 粘贴刚刚复制的完整公钥内容

3. 测试连接输入：`ssh -T git@github.com`

   若出现：`D:\AI learning>git push -u origin main The authenticity of host 'github.com (20.205.243.166)' can't be established. ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU. This key is not known by any other names. Are you sure you want to continue connecting (yes/no/[fingerprint])?`说明是 **SSH 首次连接 GitHub 时的正常安全验证**，说明你的 SSH 配置已生效！

   此时应该比对终端显示的指纹与[GitHub官方的指纹](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints)  匹配才说明是真正的GitHub服务器，应该输入：yes

4. **远程连接GitHub仓库：**用行命令打开笔记文件路径后输入：`git remote add origin git@github.com:Liang-Jane/Learning-AI-Note.git`  别的github仓库记得改仓库路径

5. **推送笔记内容：**`git push -u origin main

## 2. 学习Markdown语法，并整理这两天的学习笔记

[Markdown 引用语法 | Markdown 教程](https://markdown.com.cn/basic-syntax/blockquotes.html)



## 3. Python基础入门

