# Git学习


# git笔记

> **参考：** [Git实战丨看故事学git，这可能是我听过最好的课程了_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1uD4y1V77L/?spm_id_from=333.999.0.0&vd_source=5f0bf3640ba8c352c125361326de018c)

## git基本流程

- 创建文件夹
  
  ```bash
  mkdir test
  cd test
  ```

- 初始化git
  
  ```bash
  git init
  # 会生成一个 .git文件夹
  ```

- 添加文件到git
  
  ```bash
  git add 文件名
  git add .
  ```

- 查看状态
  
  ```bash
  git status
  # 红色：未添加
  # 绿色：添加完成
  ```
- 提交
  
  ```bash
  git commit -m '描述信息'
  ```
- 生成版本
  
  ```bash
  git tag -a 版本号（例如：v1） -m "描述信息"
  ```

## git功能

### 信息配置

- 个人信息配置：用户名、邮箱
  
  ```bash
  git config --global user.email "you@email.com"
  git config --global user.name "your name"    
  ```

### 记录回滚

- 查看记录
  
  ```bash
  git log
  git log --graph 
  #以详细内容的树结构查看记录
  git log --graph --pretty=format:"%h %s"
  #以简洁内容的树结构查看记录
  ```

- 回滚之前版本
  
  ```bash
  git log
  git reset --hard 版本号
  ```

- 回滚之后的版本
  
  ```bash
  git reflog 
  # 查看所有的log
  git reset --hard
  ```

### 分支使用

- 创建分支
  
  ```bash
  git branch 分支名
  ```

- 查看分支
  
  ```bash
  git branch
  ```

- 切换分支
  
  ```bash
  git checkout 分支名
  ```

- 合并分支
  
  ```bash
  git merge 分支名
  # 切换到想要最终合并的分支上例如：master 
  # git merge bug 就是将bug的内容合并到master
  # 合并后可能存在需要手动修改的文件的情况
  ```

- 删除分支
  
  ```bash
  git branch -d 分支名
  ```

### 线上仓库

- 取仓库别名
  
  ```bash
  git remote add origin 仓库地址
  # origin为仓库别名
  ```

- 克隆代码
  
  ```bash
  git clone 仓库地址
  ```

- 发布代码
  
  ```bash
  git push -u origin 分支名
  ```

- 下拉代码
  
  ```bash
  git pull origin 分支名
  #       ||
  git fetch origin 
  #        +
  git merge orgin/分支名
  ```

### rebase的使用

- 将太多的commit压缩成一个commit
  
  ```bash
  git rebase -i HEAD-3
  # 当前开始的三条记录 HEAD-加数字
  # 不要把上传过仓库的commit进行rebase
  ```

- 二

- 三

### 版本生成

- 生成版本
  
  ```bash
  git tag -a 版本号（例如：v1） -m "描述信息"
  ```

- 推送版本
  
  ```bash
  git push origin --tags
  ```

## git工作流

### 个人

> 将分支分为三个分别为：**master**,**dev**,**bug**

- **master** 分支主要用于发布版本

- **dev** 分支用于进行代码开发

- **bug** 分支用于修复master发布产生的bug 

### 团队（了解）

> 将分支分为三个分别为：**master**,**test**,**dev**,**bug**

- **master** 分支用于发布版本

- **test** 分支用于测试**dev**分支开发的代码

- **bug** 分支用于修复**test**分支产生的bug

## git 四大区域

> 基本了解： 工作区 git add . -> 暂存区 git commit -> 本地仓库 git commit -> 远程仓库 

<img src="https://m1.im5i.com/2023/01/31/UGPkmX.png" title="" alt="UGPkmX.png" data-align="center">

## 配置

### 配置文件

> 优先级：项目 > 全局 > 系统

- 项目配置文件：项目/.git/config
  
  ```bash
  git config --local user.name "you name"
  git config --local user.email "you@email.com"
  ```

- 全局配置文件：~/.gitconfig
  
  ```bash
  git config --glocal user.name "you name"
  git config --glocal user.email "you@email.com"
  ```

- 系统配置文件：/etc/.gitconfig
  
  ```bash
  git config --system user.name "you name"
  git config --system user.email "you@email.com"
  # 需要root文件
  ```

### 免密码登录

- URL中体现
  
  ```bash
  原来的地址：htttps://github.com/NAME/project.git
  修改的地址：htttps://用户名:密码@github.com/NAME/project.git
  ```

- SSH实现
  
  1. 生成公钥和私钥（默认放在~/.ssh目录下，id_rsa.pub公钥、id_rsa私钥）
     
     ```bash
     ssh-keygen
     ```
  
  2. 拷贝公钥内容，并设置到**github**中
  
  3. 在git本地配置ssh地址
     
     ```bash
     git remote add origin git@github.com:NAME/project.git
     ```

- git自动管理凭证

### 忽略文件

> [.gitignore文件参考](https://github.com/github/gitignore)

-  .gitignore文件内容
  
  ```bash
  file.txt
  # 忽略该文件
  flie/
  # 忽略文件夹
  *.h
  !a.h
  # 除了a.h文件以外的.h文件都会被忽略
  ```



