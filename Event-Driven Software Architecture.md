## Components of Event-Driven Systems

Before we go any further, let’s define some terms.

**Event**  
A change in state that is meaningful in a business process. For example, placement of a purchase order is a meaningful event, because the order fulfillment center expects to receive a notification before processing an order.  
  
**Event message**  
A message that contains data about the event. Also known as an event notification. For example, an event message can be a notification about an order placement containing information about the order.  
  
**Event producer**  
The publisher of an event message. For example, an order placement app.  
  
**Event channel**  
A stream of events on which an event producer sends event messages and event consumers read those messages. For platform events, the channel is for one platform event and groups all event messages for that platform event.  
  
**Event consumer**  
A subscriber to a channel that receives messages from the channel. For example, an order fulfillment app that is notified of new orders.

  

**Event bus**

A communication and storage service that enables event streaming using the publish-subscribe model. The event bus enables the retrieval of stored event messages at any time during the retention window.  
  

The following diagram illustrates an event-based software architecture.

![A diagram showing components of event-based systems: event producers, which feed information into the event bus, which sends messages to the event consumers](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/platform_events_basics/platform_events_architecture/images/9d0edf028a3e0056757e93a3244a43de_salesforce-event-bus.png)  
Unlike request-response communication models, software architecture built on an event-driven model decouples event producers from event consumers, thereby simplifying the communication model in connected systems. No requests need to be made to a server to obtain information about a certain state. Instead, a system subscribes to an event channel and is notified whenever new states occur. Any number of consumers can receive and react to the same events. When an event occurs, systems obtain this information and can react to it in near-real time. Systems that send events and others that receive the events don’t have dependencies on each other, except for the semantics of the message content.

The Salesforce enterprise messaging platform offers the benefits of event-driven software architecture. Platform events are the event messages that your apps send and receive. They simplify the process of communicating changes and responding to them without requiring you to write complex logic. Publishers and subscribers communicate with each other through platform events. One or more subscribers can listen to the same event and carry out actions.

Say a news agency called Cloud News sends events to subscribed clients with the latest breaking news about traffic and road conditions in a mountain retreat destination. The contents of those events are not just the news items themselves but also related details such as whether a piece of news is urgent, and the location of the incident. Subscribers can receive these events and determine what actions to take based on the urgency of the news.

All this sounds good, but what are some real-world cases when you can use platform events? Of course, the use of platform events isn’t restricted to a news agency. Following are a few useful applications.