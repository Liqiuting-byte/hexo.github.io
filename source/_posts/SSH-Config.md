---
title: 使用 SSH Config 实现认证分离
date: 2025-09-22
description: 迁移
tags:
  - 技术
  - 思考
  - 日记
  - 博客
  - 教程
category: 日记
published: false
---
### 使用 SSH Config 实现认证分离

#### 为每个账户生成独立的 SSH 密钥

假设有两个账户：个人 personal (GitHub) 和工作 work (公司 GitLab)

1. 打开 Git Bash 或任何终端
    
2. **生成个人账户的 SSH 密钥**：
    
    codeBash
    
    ```
    # -f 指定了密钥文件的名称，避免覆盖默认的 id_rsa
    ssh-keygen -t rsa -C "your_personal_email@example.com" -f ~/.ssh/id_rsa_personal
    ```
    
    一路按回车即可，可以不设置密码。这会生成 id_rsa_personal (私钥) 和 id_rsa_personal.pub (公钥) 两个文件
    
3. **生成工作账户的 SSH 密钥**：
    
    codeBash
    
    ```
    ssh-keygen -t rsa -C "your_work_email@company.com" -f ~/.ssh/id_rsa_work
    ```
    
    这会生成 id_rsa_work 和 id_rsa_work.pub
    

#### 将公钥添加到对应的 Git 平台上

1. **个人 GitHub**：
    
    - 复制个人公钥的内容：cat ~/.ssh/id_rsa_personal.pub
        
    - 登录 GitHub，进入 Settings -> SSH and GPG keys -> New SSH key，将公钥内容粘贴进去。
        
2. **公司 GitLab**：
    
    - 复制工作公钥的内容：cat ~/.ssh/id_rsa_work.pub
        
    - 登录公司的 GitLab，在类似的 SSH 密钥设置页面，添加这个公钥
    

#### 创建并配置 SSH config 文件（核心步骤）



1. 在 ~/.ssh/ 目录下（如果不存在就创建一个），创建一个名为 config 的文件（没有后缀名）
    
2. 用文本编辑器打开这个 config 文件，并写入以下内容：
    
    codeCode
    
    ```
    # 个人 GitHub 账户配置
    Host github.com-personal  # 这是一个自定义的别名，之后会用到
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_personal
    
    # 工作 GitLab 账户配置
    Host gitlab.company.com-work # 自定义别名
    HostName gitlab.company.com    # 公司的 GitLab 域名
    User git
    IdentityFile ~/.ssh/id_rsa_work
    ```
    
    - Host: 自定义的别名，用于在 git clone 或 git remote 时区分不同账户
        
    - HostName: 真实的 Git 服务器域名
        
    - IdentityFile: 指定该 Host 使用的私钥文件路径
        

#### 使用新的别名克隆或修改仓库

现在，当操作仓库时，需要使用刚刚定义的 Host 别名

- **克隆一个新仓库**：
    
    - **个人项目**：git clone git@github.com-personal:your-username/your-repo.git
        
    - **工作项目**：git clone git@gitlab.company.com-work:your-group/your-project.git  
        注意：我们将原始的 git@github.com 替换为了 git@github.com-personal。
        
- **修改一个已存在的仓库**：  
    进入仓库目录，运行 git remote -v 查看当前的远程地址。然后用 set-url 修改它
    
    codeBash
    
    ```
    # 例如，修改一个个人项目
    git remote set-url origin git@github.com-personal:your-username/your-repo.git
    ```
    

当向 github.com-personal 推送时，SSH 会自动加载 id_rsa_personal 密钥，反之亦然

### 常用命令速查表

|                    |               |
| ------------------ | ------------- |
| 命令                 | 作用            |
| git status         | 查看当前仓库的状态     |
| git add .          | 将所有更改添加到暂存区   |
| git commit -m "说明" | 将暂存区的更改提交到本地  |
| git pull           | 从远程仓库拉取最新版本   |
| git push           | 将本地的提交推送到远程仓库 |
