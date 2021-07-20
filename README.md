# KafkaSpringBoot
Apache Kafka with Spring Boot


Change Directory 	D:
Kafka home	cd kafka_2.13-2.7.1\bin\windows

Start Zookeeper:	zookeeper-server-start.bat ..\..\config\zookeeper.properties

Configure Kafka 	listeners=PLAINTEXT://localhost:9092
server.properties.	auto.create.topics.enable=false
(One Time only)

Start Kafka 	kafka-server-start.bat ..\..\config\server.properties

Start Cluster
kafka-server-start.bat ..\..\config\server.properties	Cluster	Broker 0
kafka-server-start.bat ..\..\config\server-1.properties	Cluster	Broker 1
kafka-server-start.bat ..\..\config\server-2.properties	Cluster	Broker 2


//Create Topics
kafka-topics.bat --create --topic topicA -zookeeper localhost:2181 --replication-factor 1 --partitions 4
kafka-topics.bat --create --topic cluster_topic -zookeeper localhost:2181 --replication-factor 3 --partitions 3
kafka-topics.bat --create --topic cluster_topicA -zookeeper localhost:2181 --replication-factor 3 --partitions 3

// Start Producer
kafka-console-producer.bat --broker-list localhost:9092 --topic topicA
kafka-console-producer.bat --broker-list localhost:9092 --topic topicA --property "key.separator=-" --property "parse.key=true"


//Start Consumer
kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic topicA --from-beginning
kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic topicA
kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic topicA --from-beginning -property "key.separator= - " --property "print.key=true"
kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic topicA --group groupA
kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic topicA --from-beginning
kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic library-events


kafka-topics.bat --zookeeper localhost:2181 --list
kafka-topics.bat --zookeeper localhost:2181 --describe
kafka-topics.bat --zookeeper localhost:2181 --describe --topic cluster_topic
