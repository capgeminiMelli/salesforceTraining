## Get Started with Flow Builder

You may have heard several terms used interchangeably when referring to flows. As a reminder, the official terms are:

-   **Salesforce Flow**—the product that encompasses building, managing, and running flows and processes.
-   **Flow Builder**—a point-and-click tool for building flows.
-   **Flow**—an application that automates a business process by collecting data and doing something in your Salesforce org or an external system.
![[Pasted image 20210623144638.png]]


In short, the Salesforce Flow product includes a couple of tools. One of them, Flow Builder, lets you create flows.


**Logic** 

Control the flow of... well, your flow. Create branches, update data, loop over sets of data, or wait for a particular time. 

  

**Actions** 

Do something in Salesforce when you have the necessary information (perhaps collected from the user via a screen). Flows can look up, create, update, and delete Salesforce records. They can also create Chatter posts, submit records for approval, and send emails. If your action isn’t possible out of the box, call Apex code from the flow. 

  

**Integrations** 

Connect your flow to an external database by using core actions or Apex actions. Core actions let you make requests without going through the Salesforce server. Flow Builder also has a couple of tie-ins to platform events. Publish platform event messages with a Create Records element. Subscribe to platform events with a Pause element.