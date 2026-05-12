# Reflection  
## Modul 9 - Azzahra Anjelika Borselano (2406419663)

a. How much data your publisher program will send to the message broker in one run?  
The publisher sends 5 messages to the message broker in a single run. Each message is a UserCreatedEventMessage containing a user_id and user_name, for Amir, Budi, Cica, Dira, and Emir respectively. All messages are published to the same queue named user_created.  

b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?  
Since both the publisher and subscriber use the same URL amqp://guest:guest@localhost:5672, it means they are connecting to the same message broker — a RabbitMQ instance running on the same machine (localhost), on the same port (5672), with the same credentials.
This is the core idea of the message broker pattern: the publisher and subscriber do not talk to each other directly. Instead, both go through the same broker (RabbitMQ). The publisher pushes messages into the queue, and the subscriber consumes messages from that same queue. As long as both use the same URL, they will be properly connected through the broker.

### RabbitMQ screen
![Running RabbitMQ](screenshots/Running_rabbitmq.png)

### Sending and processing event
![Sending and processing event](screenshots/Sending_and_processing_event.png)
When the publisher is run, it sends 5 UserCreatedEventMessage events to the RabbitMQ message broker via the user_created queue. The subscriber, which is continuously listening to that queue, receives and processes each event as it arrives, printing the message contents to the console. This demonstrates the event-driven communication pattern where the publisher and subscriber are decoupled — they do not interact directly, but instead communicate through the message broker.

### Monitoring chart based on publisher
![Monitoring chart based on publisher](screenshots/Monitoring_chart_based_on_publisher.png)
The spikes visible in the RabbitMQ message rates chart correspond to the moments when the publisher is run. Each time the publisher is executed, it sends 5 messages at once to the message broker, causing a sudden surge in the message rate which appears as a spike on the chart. Once all 5 messages have been sent and consumed by the subscriber, the rate drops back to zero until the publisher is run again.