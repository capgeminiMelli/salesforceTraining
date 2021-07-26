## Why External Services?

In today’s world, customers expect a seamless customer experience - no matter if that experience consists of behind the scenes business solutions and services that reside on a single platform or across multiple off-platform hosts. It’s this interaction between Salesforce and outside services where External Services shines. External Services smooths the way for this exchange by letting you declaratively (no coding!) integrate with externally hosted services that perform a variety of business actions or computations for use in your Salesforce org. So what kind of valuable third-party services can be integrated into a Salesforce org? Here are a few examples:

  

-   Credit scoring service function for your Salesforce Account detail page
-   An eligibility verification service for discounts
-   Flexible digital payment services
-   COVID-19 Return-To-Work services
-   Mapping services with visualization tools
-   Real-time order notification in Slack
-   Identification: Fraud prevention service
-   Integration of separate omnichannel retailing services
-   Google services
-   Government and international institutions services
    -   Air quality index (AirNow)
    -   Citizen services
    -   Centers for Disease Control and Prevention (CDC)
    -   The World Bank

![[Pasted image 20210623154143.png]]


## What Actually Is External Services?

Do you know your external web service from your External Services? Let’s start with some handy definitions. 

**External Services—**  Salesforce integration product that encompasses (1) registering an external web service that you submit as an OpenAPI schema defining the web service, and (2) magically (well, almost!) bringing the operations of your external web service into the Salesforce platform (see invocable actions) for use with point-and-click tools like Flow Builder. In a nutshell, it declaratively connects external REST APIs using OpenAPI standards.

  

**external web service****—**  Also referred to as external services (lowercase). Any type of function, action or process that’s developed and hosted outside of the Salesforce platform. For an external web service to be consumable by External Services, it must be a REST-based API that typically uses the HTTP(s) protocol to navigate the web. (If you don’t know what REST is, that’s OK.)

  

**API schema specification—** Also referred to as API specification, schema definition, or description format. It’s a common language or standard for defining what an API can do that is readable by both humans and machines. It defines the basics for the naming, order and contents of objects and ensures clear interactions with a REST API. External Services adheres to a JSON-based OpenAPI specification format. See [OpenAPI Specification](https://swagger.io/resources/open-api/).

  

**invocable actions (in the context of External Services)—**  Represent the declarative building blocks available from a growing number of Salesforce platform tools like Flow Builder. Invocable actions assist admins and developers by providing a way to implement and use any type of action in a consistent manner. In the External Services ecosystem, once you register your external web service with External Services, you can access the resulting invocable actions from, for example, the Flow Builder tool.

  

**Flow Builder—** A point-and-click tool for building flows. 

  

**Flow—**  A flow is the part of Lightning Flow that collects data and performs actions in your Salesforce org or in an external system. Lighting Flow includes flows (built with Flow Builder) and processes (built with Process Builder).  

_But wait, there’s more._   
  
While these terms—OpenAPI specification, API, and Schema—are geared toward developers, External Services helps bridge the gap between the coding of web services, and automating the access to them. Later on, we have a simple application use case that walks you through a schema definition of a web service, registers the schema definition, and uses Flow Builder to drag-and-drop the newly available actions into a flow.

It’s time to take a step back and look at the whole picture to understand the interconnected building blocks of External Services. While we’re looking, though, notice that much of the work to register an external web service of your own is done declaratively via the External Services registration page. Once registered, you can use tools like Flow Builder to build a flow from the invocable actions of your web service.

## Use the External Services Wizard to Register Your Web Service

Now we get to register the web service. Because we have a valid schema (a real-world example would additionally set the authentication protocol in Named Credential), this part is simple. Adding our Acme bank external service in External Services tells Salesforce how it will interact.  

1.  From Setup, enter External Services in the Quick Find box, then select **External Services**.
2.  Click **Add an External Service**.
3.  For External Service Name, enter BankService (no space).
4.  For Select a Named Credential, select **Bank**.
[[5.  Select **Service Schema Relative URL**, and enter /accounts/schema  The full URL from our service provider is located here: [https://th-external-services.herokuapp.com/accounts/schema](https://th-external-services.herokuapp.com/accounts/schema).
6.  Click **Save & Next**.
7.  Select operations.
8.  Click **Next**. Take a look at the External Service Actions and when you’re ready, click **Done**.

A list of your External Service actions appears. Use the scrollbar to view them all.

[[ External Schema ]]


### Data loader + External ID

[[External Schema]]