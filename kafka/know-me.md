# Notes from the Internet

Original Use Case:
The original use case for Kafka was to be able to rebuild a user activity tracking pipeline as a set of real-time publish-subscribe feeds. This means site activity (page views, searches, or other actions users may take) is published to central topics with one topic per activity type. These feeds are available for subscription for a range of use cases including real-time processing, real-time monitoring, and loading into Hadoop or offline data warehousing systems for offline processing and reporting.

Kafka is great for building event driven systems. Apache kafka uses a distributed log. The log-structured approach is itself a simple idea: A collection of messages, appended sequentially to a file. when a service wants to read messages from kafka it 'seeks' to the position of the last message it read, then scans sequentially, reading messages in order, while periodically recording its new position in log. When you read messages from Kafka data is directly imported from disk buffer to network buffer. Kafka operates on batched sequential reads. This makes it efficient. If a service has some form of outage and doesnt read messages for a long time, the backlog wont cause the infrastructure to slow significantly. A common problem with traditional brokers, which have a tendency to slow down as they get full. Being log-structured also makes kafka well suited to performing the role of an Eventstore.

A log is an efficient data structure for messaging work loads. But Kafka is really many logs. Kafka routes messages from producers to consumers reliably, replicating for fault tolerance and handling failure. 

When you read and write to a topic, you will be typically reading and writing to all of them, sharding your data over all the machines you have at your disposal. scaling is pretty simple. Add new machines and rebalance. 

Kafka is highly scalable. Messages that require relative ordering need to send to the same partition. This is managed for you when you supply the same key for all messages that require a relative ordering. 

Some jargon:

TOPIC
RETRY
SHARD KEY

Kafka provides durability through replication. 
Producers: Producers publish data to the topics of their choice. The producer is responsible for chosing which record to assign to which partition within the topic. It could be done via round robin or semantic via key based system. 
