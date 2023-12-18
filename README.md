Setting up Kafka for Windows
----------------------------
**step1:**
Go to https://kafka.apache.org/downloads

Extract: tar -xvf

open server.properties and add the below 

broker.id=1
port=9093
logs.dirs=/tmp/kafka-logs-1
listeners=PLAINTEXT://:9092

Ready to start the server :  
Launch command Prompt from go to the kafka/bin/windows
and run kafka-server-start.bat



**step2:**
download zookeeper from https://www.apache.org/dyn/closer.lua/zookeeper/zookeeper-3.8.3/apache-zookeeper-3.8.3-bin.tar.gz

copy config file and rename it zoo.cfg and the below
------------
tickTime=2000
dataDir=(create directory named data and add the path here)
clientPort=2181
initLimit=5
syncLimit=2

start server zkServer.cmd # for windows

**step 3**
create Topic
-------
kafka-topics.bat --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test
Created topic test.

**step 4**
Run producer
--------
kafka-console-producer.bat --broker-list localhost:9092 --topic test


**step 5**
Run Consumer
--------
kafka-console-consumer.bat --bootstrap-server localhost:9092 -topic test --from-beginning

Type something in producer console it will be received at consumer side


**step 6 **
Creating Producer application, source code from https://github.com/YasminNoorjahan/KafkaProducer_SB and run the application
creating consumer application, source code from https://github.com/YasminNoorjahan/KafkaConsumer_SB and run the application
and hit the request from postman, and check it in the consumer consoler and we are good :) 
http://localhost:{producer application port}/user
{"name":"noor"}





For setting up 3 brokers in single node
--------------------


>kafka-server-start.bat server.properties

>kafka-server-start.bat serverOne.properties

>kafka-server-start.bat serverTwo.properties
