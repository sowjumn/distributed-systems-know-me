# Installing Kafka

## Installing JVM, Zookeeper & Kafka

Kafka needs JVM, Zookeeper 

* `brew cask install caskroom/versions/java8`

* `brew install kafka` 

## Starting the Zookeeper server
* `zookeeper-server-start /usr/local/etc/kafka/zookeeper.properties`

* `kafka-server-start /usr/local/etc/kafka/server.properties`

* zookeeper by default binds on port port 0.0.0.0/0.0.0.0:2181


## Using Kafka 

### Create a KAFKA TOPIC

Create a Kafka Topic named 'tictoe' with a single partition and single replica. 

`kafka-topics --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic tictoe`


### List the current Topics

`kafka-topics --list --zookeeper localhost:2181`
`kafka-topics --describe --topic tictoe --zookeeper localhost:2181`


### Send messages to the Kafka Cluster using the Producer

kafka-console-producer: reads from a file or standard input and publishes it to the kafka cluster

	* the topic, broker-list are required fields for a Kafka producer

`kafka-console-producer --topic tictoe --broker-list localhost:9092`


### Consume messages from Kafka

kafka-console-consumer: consumes messages based on the offset

`kafka-console-consumer --bootstrap-server localhost:9092 --topic tictoe --from-beginning`

`kafka-console-consumer --offset 'earliest' --bootstrap-server localhost:9092 --topic tictoe --partition 1`


### List the consumer groups 

`kafka-consumer-groups --bootstrap-server localhost:9092 --list`

### List more details about a consumer group: partitions, offset

`kafka-consumer-groups --bootstrap-server localhost:9092 --group console-consumer-95278 --describe`

### Setup a Multi broker cluster:








