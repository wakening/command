# yarn常用命令

#### 查看任务列表
    yarn application -list

#### 查看正在跑任务
    yarn application -list –appStates running

#### 杀任务
    yarn application -kill application_1437456051228_1725

#### 查看任务日志，保存到指定文件内
    yarn logs -applicationId application_1437456051228_1725 > 123.log