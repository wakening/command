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
* <a href="#Python">Python</a>

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

    git reset --hard origin/<branch_name>

#### 重置远程分支到指定的提交点，提交点后的所有提交将消失，慎用
    git reset --hard <commit_id>
    git push origin HEAD --force

#### 查看用户名、邮箱
    git config user.name
    git config user.email

#### 修改用户名、邮箱
    git config user.name <new_user_name>
    git config user.email <new_user_email>

#### 拉取远程分支到本地
    git checkout -b <local_branch_name> origin/<origin_branch_name>

#### 更新当前分支代码
    git fetch
    
    拉取并合并到本地，pull = fetch + merge
    git pull
    
    

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

<a name="Java"></a>

# Python

#### 创建虚拟环境，激活虚拟环境
    python -m venv .venv
    .\.venv\Scripts\activate
    # 不激活环境，直接使用虚拟环境执行脚本
    .\.venv\Scripts\python.exe main.py

#### 查看依赖包列表
    pip list

#### 根据文件安装依赖，指定镜像源
    pip install -r requirements.txt
    pip install --upgrade -r requirements.txt
    python -m pip install requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple

#### 安装指定版本的依赖
    pip install <package_name>==<version>
    # win虚拟环境若执行失败，可使用这个命令
    python -m pip install <package_name>==<version>

#### 卸载依赖
    pip uninstall <package_name>
