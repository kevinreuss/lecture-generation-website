# Kafka and RabbitMQ Messaging Systems

## Kafka 

Apache Kafka is a distributed, partitioned, and replicated commit log service. It provides the functionality of a messaging system, with a unique design.

```java
// Producer
Properties props = new Properties();
props.put("bootstrap.servers", "localhost:9092");
props.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");
props.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");

Producer<String, String> producer = new KafkaProducer<>(props);
producer.send(new ProducerRecord<String, String>("my-topic", "key", "value"));
producer.close();
```

In the above Kafka Producer example, we are sending a message ("value") with a key ("key") to a Kafka topic ("my-topic").

```java
// Consumer
Properties props = new Properties();
props.put("bootstrap.servers", "localhost:9092");
props.put("group.id", "test");
props.put("key.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");
props.put("value.deserializer", "org.apache.kafka.common.serialization.StringDeserializer");

KafkaConsumer<String, String> consumer = new KafkaConsumer<>(props);
consumer.subscribe(Arrays.asList("my-topic"));
while (true) {
    ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(100));
    for (ConsumerRecord<String, String> record : records)
        System.out.printf("offset = %d, key = %s, value = %s%n", record.offset(), record.key(), record.value());
}
```
In the Kafka Consumer example, we are subscribing to the same Kafka topic ("my-topic") and continuously polling for new messages.

## RabbitMQ

RabbitMQ is a robust yet easy to use messaging system running over the Advanced Message Queuing Protocol (AMQP).

```python
# Producer
import pika

connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()
channel.queue_declare(queue='hello')
channel.basic_publish(exchange='', routing_key='hello', body='Hello World!')
connection.close()
```

In the RabbitMQ Producer example, we are sending a message ("Hello World!") to a queue ("hello").

```python
# Consumer
import pika

def callback(ch, method, properties, body):
    print("Received %r" % body)

connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()
channel.queue_declare(queue='hello')
channel.basic_consume(queue='hello', auto_ack=True, on_message_callback=callback)
channel.start_consuming()
```
In the RabbitMQ Consumer example, we are consuming messages from the same queue ("hello") and printing them out.

Kafka is optimized for high throughput of distributed data streams, while RabbitMQ is optimized for high throughput of individual messages. Choose according to your use case.