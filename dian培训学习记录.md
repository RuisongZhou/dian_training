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
 5. git mv file_from          file_to文件名更改
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
  
### 11.30学习记录
  >* 学习Linux
 1. .mv [选项] 源文件或目录 目录或多个源文件 
  作用：移动或重命名文件
  -b  覆盖前做备份
-f  如存在不询问而强制覆盖
-i  如存在则询问是否覆盖
-u  较新才覆盖
-t  将多个源文件移动到统一目录下，目录参数在前，文件参数在后
2. cp [选项] 源文件或目录 目录或多个源文件 
作用：将源文件复制至目标文件，或将多个源文件复制至目标目录。
-r -R 递归复制该目录及其子目录内容
-p  连同档案属性一起复制过去
-f  不询问而强制复制
-s  生成快捷方式
-a  将档案的所有特性都一起复制
 3. scp [参数] [原路径] [目标路径]
 作用：在Linux服务器之间复制文件和目录
 -v  详细显示输出的具体情况
-r  递归复制整个目录
4. rm [选项] 文件 | 删除文件
 -r  删除文件夹
-f  删除不提示
-i  删除提示
-v  详细显示进行步骤
5. touch [选项] 文件
作用：创建空文件或更新文件时间
-a  只修改存取时间
-m  值修改变动时间
-r  eg:touch -r a b ,使b的时间和a相同
-t  指定特定的时间 eg:touch -t 201211142234.50 log.log 
    -t time [[CC]YY]MMDDhhmm[.SS],C:年前两位
6. mkdir [选项] 目录
作用：创建新目录
-p  递归创建目录，若父目录不存在则依次创建
-m  自定义创建目录的权限  eg:mkdir -m 777 hehe
-v  显示创建目录的详细信息
7. rm [选项] 文件
作用：一个或多个文件或目录
-f  忽略不存在的文件，不给出提示
-i  交互式删除
-r  将列出的目录及其子目录递归删除
-v  列出详细信息
8.echo 作用：显示内容
-n  输出后不换行
-e  遇到转义字符特殊处理
  
  ---
  
### 12.1 学习记录

>* 学习Linux
1. 学习了date，cal（日历），bc（计算器）,nano(文本编辑器）等
2. who 查看目前在线
netstat -a 网络联机状态
ps -aux 后台执行程序
3. 关机步骤
sync 将数据同步写入硬盘
shutdown 关机命令（-r重启 -c取消 必须加时间）
重启 reboot
4. init 切换执行等级
5. man[选项] [参数]
-a：在所有的man帮助手册中搜索
-f：等价于whatis指令，显示给定关键字的简短描述信息
-P：指定内容时使用分页程序
-M：指定man手册搜索的路径
6. more
作用：按页查看文章内容，从前向后读取文件，因此在启动时就加载整个文件
+n  从第n行开始显示
-n  每次查看n行数据
+/String    搜寻String字符串位置，从其前两行开始查看
-c  清屏再显示
-p  换页时清屏
7. nl [选项] [文件]
作用：将输出内容自动加上行号
-b a 不论是否有空行，都列出行号
-b t 空行则不列行号（默认） 
-n 有ln rn rz三个参数，分别为再最左方显示，最右方显示不加0，最右方显示加0
8. head [参数] [文件]
作用：-v  显示文件名
-c number   显示前number个字符,若number为负数,则显示除最后number个字符的所有内容
-number/n (+)number     显示前number行内容，
-n number   若number为负数，则显示除最后number行数据的所有内容显示档案开头，默认开头10行 

  ---
  
### 12.2 学习记录

>* 学习git
1. 查看远程仓库
git push [remote-name] [branch-name] 推送数据
git remote show [remote-name] 查看仓库详细信息 
git remote rename [原名字] [新名字] 更改远程仓库名
git remote rm [repository] 移除仓库
2. 打标签
git tag 查看标签
git tag -1 'name' 查看标签
git tag -a 版本 -m 'new tag'新建标签
git show [版本] 查看版本信息
3. 分支
git branch 查看分支
git branch [new branch] 建立新分支newbranch
git checkout [branch] 转换分支
git branch -b [newbranch] 创建并切换到该分支
git branch -d [branch] 删除分支
git merge [branch] 合并分支（提前切换到master分支）
git branch -v 查看各分支最后一次commit信息
>* vim
1. 基础--------------
hjkl移动光标
q!强制退出
wq保存退出
i插入操作
A添加操作
2. 删除与撤销--------
dw删除一个单词
d$删除一句话
2w 使光标前移两个单词
3e使光标前移到第三个单词末尾
d2w 删除两个字母
dd删除整行
u撤销修改
U恢复该行原有状态
CTRL+R 重做被撤销的指令

