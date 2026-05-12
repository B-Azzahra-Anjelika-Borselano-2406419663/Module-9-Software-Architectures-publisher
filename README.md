# Reflection  
## Modul 9 - Azzahra Anjelika Borselano (2406419663)

a. How much data your publisher program will send to the message broker in one run?  
The publisher sends 5 messages to the message broker in a single run. Each message is a UserCreatedEventMessage containing a user_id and user_name, for Amir, Budi, Cica, Dira, and Emir respectively. All messages are published to the same queue named user_created.  

b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?  
Since both the publisher and subscriber use the same URL amqp://guest:guest@localhost:5672, it means they are connecting to the same message broker — a RabbitMQ instance running on the same machine (localhost), on the same port (5672), with the same credentials.
This is the core idea of the message broker pattern: the publisher and subscriber do not talk to each other directly. Instead, both go through the same broker (RabbitMQ). The publisher pushes messages into the queue, and the subscriber consumes messages from that same queue. As long as both use the same URL, they will be properly connected through the broker.

### RabbitMQ screen
![Running RabbitMQ](screenshots/Running_rabbitmq.png)