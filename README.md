# CST8915 Lab 7: CST8915 Full-stack Cloud-native Development: Introduction to Kubernetes Basics

**Student Name**: Joshua Chen

**Student ID**: 041280453

**Course**: CST8915 Full-stack Cloud-native Development

**Semester**: Winter 2026

---

## Demo Video

https://youtu.be/W_z5dqSRD4g

---

## Technical Explanations

RabbitMQ is a stateless application, this means that it doesn't have persistent storage. So any data added to ts queue will be removed when RabbitMQ stops 
As such when the RabbitMQ pod is deleted or restarted  all the data within it is cleared and when a new pod is created none of the previous data is there. 

RabbitMQ can be configured to have persistent storage using either Streams, Quorum Queues or classic queues. To do so you must set durable to True, and the delivery mode to 2. The Consumer would then have to send an acknolwedgement that it as recieved the message.  
This will have RabbitMQ to write the message to the disk as well. 

Some potential solutions to this is finding another software that does provide persistent storage. This can be something like Azure Storage Bus, which is a messaging broker service offered by Azure. Another option is to add a persistent database pod, and have another container or microservice within the pod to save the RabbitMQ messages to the database. This way if the RabbitMQ pod does go down it can read and load the information from the database if the other container in the pod can do that. A similar solution without the container would be to configure RabbitMQ to handle persistent storage. This is done using either Streams, Quorum Queues or Classical Queues. To do so you have to set the durable to True and delivery mode to 2, while the consumer must send an acknolwedgement when it recieves the message. THis will have RabbitMQ save the message to the disk or to another stateful storage container. 

Azure Service Bus solves the issue identified by the RabbitMQ Configuration as the different tires of it will store the data within an Azure SQL Database. 
As such the data can be retrieved later if Azure Service Bus is restarted or stopped

- 


---