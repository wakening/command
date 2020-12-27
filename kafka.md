# kafka常用命令

````
Tips:
test: test topic
zoo: zookeeper ip or hostname
kafka: kafka ip or hostname
testGroupId: consumer group id
kafka版本为0.10, 其他版本基本通用
````

### 创建topic, 2分区1副本
    kafka-topics.sh --zookeeper zoo:2181 --create --topic test --partitions 2 --replication-factor 1

### 修改topic, 分区数为3
    kafka-topics.sh --zookeeper zoo:2181 --alter --topic test --partitions 3

### topic列表
    kafka-topics.sh --zookeeper zoo:2181 --list
    kafka-topics.sh --bootstrap-server kafka:9092 --list

### topic详情
    kafka-topics.sh --zookeeper zoo:2181 --topic test --describe

### 生产者(producer)命令行
    kafka-console-producer.sh --broker-list kafka:9092 --topic test

### 消费者(consumer)命令行
    # 默认, 从末尾开始消费,
    kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic test
    kafka-console-consumer.sh --zookeeper zoo:2181 --topic test
    # 从起点开始消费
    kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic test --from-beginning
    kafka-console-consumer.sh --zookeeper zoo:2181 --topic test --from-beginning
    # 指定groupId消费
    kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic test --consumer-property group.id=testGroupId
    # 显示message key (显示时间戳 print.timestamp)
    kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic test --property print.key=true

### 查看消费者组(group.id)列表 (实测仅显示使用命令行的消费者组名)
    # Note: This will only show information about consumers that use the Java consumer API (non-ZooKeeper-based consumers).
    kafka-consumer-groups.sh --new-consumer --bootstrap-server kafka:9092 --list
    # Note: This will only show information about consumers that use ZooKeeper (not those using the Java consumer API).
    kafka-consumer-groups.sh --zookeeper zoo:2181 --list

### 查看topic各分区偏移量(offset), 指定消费者组(group.id)
    kafka-consumer-groups.sh --new-consumer --bootstrap-server kafka:9092 --group testGroupId --describe
    kafka-consumer-groups.sh --zookeeper zoo:2181 --group testGroupId --describe

### 查看topic各分区最大偏移量(offset)
    kafka-run-class.sh kafka.tools.GetOffsetShell --broker-list kafka:9092 --topic test --time -1


## kafka2.4

### 查看kafka消费者组详情: GROUP,CONSUMER-ID,HOST,CLIENT-ID,#PARTITIONS
    #指定group id
    kafka-consumer-groups.sh --bootstrap-server kafka:9092 --group myGroupId --members --describe
    #所有组
    kafka-consumer-groups.sh --bootstrap-server kafka:9092 --all-groups --members --describe

##### Contributors
* [@wakening](https://github.com/wakening)
