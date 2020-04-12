# linux等常用命令

#### 重置本地分支到指定的提交点，用于快速回退代码、清理不要的commit和本地修改记录
    git reset -hard commitId

#### 查找文件，过滤掉无权限的警告信息
    find / -name xxx 2>/dev/null
    
#### 获取当前时间戳，秒
    date +%s
    
#### 时间戳(秒)转日期
    date -d @1586701561