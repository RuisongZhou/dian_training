# dian培训学习记录

标签（空格分隔）： 笔记

---

### 11.28学习记录
>* 学习了cmd markdown的使用（吃老本）
>* 安装了VMware虚拟机，正再装Ubuntu，明天开始学习Linux。
>* 在github上创建了新的库，希望能督促我每天的学习。

---

### 11.29学习记录
>* 学习git的基本操作。
   1. git config --list查看配置信息
   2. git diff --cached(staged)查看没有暂存起来的差异
   3. git commit -a 可以跳过已跟踪文件
   4. git rm --cached <file>移除跟踪但不删除文件
 5. git mv file_from          file_to文件更改
   6. git log回顾提交历史
   git log -p -2 // -p展开显示每次提交的差异 -2仅显示最近两次更新
   还有-stat仅显示简要的增改行数统计，--pretty=format见progit第24页
  git log --since=2.weeks显示最近两周提交
 7. git commit --amend重新提交
 8. git reset HEAD<file>取消暂存
 
  >* 学习Linux
  1. [root@localhost~]#
  其中root：当前登入用户
  localhost：主机名
  ~：当前所在目录（家目录）
  \#：超级用户提示符
  普通用户提示符是$
  2. 命令格式
  命令 [选项] [参数]
  有多个选项时，可以写在一起
  -a等于--all
  3. ls [选项] [文件或目录]
  作用：显示当前目录
  选项：
  -a显示所有文件，包括隐藏文件
  -l 显示详细信息(konglist)
  -d 查看目录属性
  -h 人性化显示文件大小
  -i 显示inode
  4. 文件类型（第一位）
  -普通文件
  d目录文件 
  l软链接文件
  5. mkdir -p [目录名]  创建目录 
  -p 递归创建
  6. cd [目录]   切换目录
  cd~ 进入家目录
  cd- 进入上次所在目录
  cd .. 进入上一级目录
  7.  CTRL+L 清屏xshell
 
  
#### 文件权限
  |rw-     | r--     | r--|
  |--------|---------|---|
 | u所有者 |g所属组| o其他人|
 
  其中 r读 w写 x执行
  ---
  
  
  
 
  