# Event-Driven Architecture

Event-Driven Architecture (EDA) is a model where the flow of the program is determined by events such as user actions, sensor outputs, or messages from other programs.

In EDA, there are three main components: Event Creators, Event Managers, and Event Consumers.

1. **Event Creators**: They generate events and publish them to the Event Manager. An event could be a simple JavaScript click event:

```javascript
button.addEventListener('click', event => {
  // This is where you'd put the code for the event
});
```
This code snippet attaches an event listener to a button, and when the button is clicked, an event is created.

2. **Event Managers**: They receive events and route them to the appropriate event consumers. For instance, an event bus can act as an event manager:

```javascript
class EventBus {
  constructor() {
    this.subscriptions = {};
  }

  subscribe(eventType, callback) {
    this.subscriptions[eventType] = callback;
  }

  publish(event) {
    this.subscriptions[event.type](event.data);
  }
}
```
This `EventBus` class can subscribe to events and execute the appropriate callbacks when an event is published.

3. **Event Consumers**: They are parts of the system that are interested in the events and react to them. Following on from our EventBus example:

```javascript
const eventBus = new EventBus();
eventBus.subscribe('click', data => console.log(`Button clicked with data: ${data}`));
```
Here, we subscribe to the 'click' event and log a message when the event occurs.

EDA allows for loose coupling, as event creators do not need to know about event consumers, and vice versa. This makes the system more flexible and scalable. However, it can be challenging to understand the overall flow of the system due to the asynchronous nature of events.