# hadoop-command

some useful command

---
Table of Contents

* [Kafka](/kafka.md)
* <a href="#Git">Git</a>
* <a href="#Linux">Linux</a>
* <a href="#Yarn">Yarn</a>
* <a href="#HBase">HBase</a>
* <a href="#Java">Java</a>

---

```
tips:
<???> is variable param
```

---

<a name="Git"></a>

# Git

#### 重置本地分支到指定的提交点，用于快速回退本地代码、清理不要的commit和本地修改记录
    git reset --hard <commit_id>

    e.g.: git reset --hard 7172e0d27fccc7da1ad4d77e3699ce7ef27c3fb6

#### 重置远程分支到指定的提交点，提交点后的所有提交将消失，慎用
    git reset --hard <commit_id>
    git push origin HEAD --force

#### 查看用户名、邮箱
    git config user.name
    git config user.email

#### 修改用户名、邮箱
    git config user.name <new_user_name>
    git config user.email <new_user_email>


---

<a name="Linux"></a>

# Linux

#### 查找文件，过滤掉无权限的警告信息
    find / -name <file_regex> 2>/dev/null

    e.g.: find / -name *.log 2>/dev/null

#### 获取当前时间戳，秒
    date +%s

#### 时间戳(秒)转日期
    date -d @<timestamp_seconds>

    e.g.: date -d @1586701561

---

<a name="Yarn"></a>

# Yarn

#### 查看任务列表
    yarn application -list

#### 查看正在跑任务
    yarn application -list –appStates running

#### 杀任务
    yarn application -kill application_1437456051228_1725

#### 查看任务日志，保存到指定文件内
    yarn logs -applicationId <your_application_id> > 123.log

    e.g.: yarn logs -applicationId application_1437456051228_1725 > 123.log

---

<a name="HBase"></a>

# HBase

#### 转义列值里的中文，在linux窗口里执行
    echo -e <column_value>

---

<a name="Java"></a>

# Java

#### jvm
    jmap -heap pid
    top -Hp pid
