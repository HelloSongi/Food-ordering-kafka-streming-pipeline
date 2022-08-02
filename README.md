![kafka_pipeline_design](https://user-images.githubusercontent.com/69304233/182486101-9e1cf3a0-bf98-4e35-858c-54c27de9bdd3.PNG)

In this project design and implementa highly scalable data pipeline system for a food ordering app. The system is event driven - such as an order being placed and an order being confirmed. 

These events/messegea/data are writen to Apache Kafka which is a central hub for all moving data. Other systems bothproducers and consumers, such as the transaction system or the email system, will be built on top of Apache Kafka architecture. Consumers will subscribe to different Kafka topics that they are concerned with, and process in real time as these messages are written to Kafka and producers will write events to topics contained in the kafka hub. 


The system should be highly scalable. Given the decoupled nature, you can scale up or down individual components as required. These individual components can either be microservices or some stream processing jobs or just plain Python files like I do here. 

The system is also very extensible because of the nature of Apache Kafka. The messages for a given topic can be retained within Kafka. That means, if you were to build a new component, you could replay all the messages of a topic from the beginning and make the component process all messages from the beginning of the topic. 

Similarly, given the persistence of Kafka, if there is an issue with any downstream or upstream system, you won't suffer from any data loss. 


A real simulation of the working pipeline is show bellow:
1. an order is simulated in the apps backend and it written to kafka
2. transction hub reads the event from kafka, then confirms the order to kfka
3. once the the confired orders are writen to kafka, both the email and analytics micro-services read the data from kafka decoupled

![decouped_microservise](https://user-images.githubusercontent.com/69304233/182487412-364cfb1e-3b4f-4083-87f5-7a0562293ae0.PNG)
