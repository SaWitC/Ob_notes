#net #questions
### 1. <span style="color:#fdd052">Message Broker </span> 
it is a system that enable application, system and services to communicate with each other by translating messages between services
### 2. <span style="color:#fdd052">RabbitMq </span>
RabbitMQ is an open-source message broker that implements the advanced message queuing protocol AMQP . it acts as an intermediary for messaging, handling sending receiving and queuing messages
### 3. <span style="color:#fdd052">Queue </span>  
Queue is a data structure that holds messages in RabbitMQ queue stores messages that are received from message publisher until they are consumed by message consumer.
### 4. <span style="color:#fdd052">Queue types </span> 
- Standard queue (default type)
- Priority queue (allows prioritizing certain messages over others)
- Exclusive queue (Used by only one connection and deleted when that connection is closed)
- Durable queue (Survive broker restarts)
- Transient queue (Do not survive broker restarts)
### 5. <span style="color:#fdd052">Exchange </span> 
- Direct exchange (routes messages with a specific routing key to the queue are bound to)
- Topic exchange (Routes messages between ) 
- Fanout Exchange:** Routes messages to all the queues bound to it.
- **Headers Exchange:** Uses message header attributes for routing.
### 6. <span style="color:#fdd052">Bindings </span> 
Bindings are rules that exchanges use to route messages to queues. A binding defines the relationship between an exchange and a queue.
### 7.  <span style="color:#fdd052">MassTransit </span> 
MassTransit is library that we can use to work with different message brokers
Reasons to use MassTransit
- Reduce complexity
- We can easly change message broker

### <span style="color:#d9c07a">QUESTIONS </span> 
1. What for we can use message brokers
2. Wen it is better to use http/https instead of any message broker
3. how to use massTransit
4. tell about Queue types