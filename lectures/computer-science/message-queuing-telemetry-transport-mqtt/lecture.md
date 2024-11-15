# Message Queuing Telemetry Transport (MQTT)

MQTT is a lightweight messaging protocol used for machine to machine (M2M) communication and in the Internet of Things (IoT) space. It uses a publish/subscribe model and works on top of the TCP/IP protocol.

## MQTT Architecture

The main components of MQTT are:

- **Publisher**: Sends messages categorized by topics.
- **Broker**: Server that receives messages from publishers and sends them to subscribers.
- **Subscriber**: Receives messages based on topics they are subscribed to.

## MQTT Topics

Topics are UTF-8 strings used by the broker to filter messages for each connected client. For example, a topic could be `home/livingroom/temperature`.

## Quality of Service (QoS)

MQTT has three levels of QoS:

- **QoS 0 (At most once)**: The message is delivered at most once, or it may not be delivered at all. Delivery across network connections is not confirmed. 
- **QoS 1 (At least once)**: The message is always delivered, but there may be duplicates.
- **QoS 2 (Exactly once)**: The message is always delivered exactly once. This is the safest but slowest level of QoS.

## MQTT with Python

Python's `paho-mqtt` library is a popular choice when working with MQTT. Here's a simple example of a publisher and subscriber:

```python
# Publisher
import paho.mqtt.client as mqtt

client = mqtt.Client("publisher")
client.connect("broker.hivemq.com", 1883)

client.publish("home/livingroom/temperature", "22.5")
```

```python
# Subscriber
import paho.mqtt.client as mqtt

def on_message(client, userdata, message):
    print(f"Received message: {message.payload.decode()} on topic {message.topic}")

client = mqtt.Client("subscriber")
client.connect("broker.hivemq.com", 1883)

client.subscribe("home/livingroom/temperature")
client.on_message = on_message

client.loop_start()
```

In this example, the publisher sends a message "22.5" on the topic "home/livingroom/temperature". The subscriber, who is subscribed to the same topic, will receive the message and print it.

## Conclusion

MQTT is a powerful protocol for IoT and M2M communication due to its lightweight nature and flexibility. Its ability to categorize messages into topics and offer different levels of QoS makes it a reliable choice for real-time data transmission.