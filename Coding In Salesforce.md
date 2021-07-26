## Basics in Salesforce

Platform relies on metadata-driven architecture. Everything, including the code, configuration, and apps, is specifed as metadata. Apex is saved, compiled, and executed directly on the Lightning Platform. It's Object oriented. 

[[Syntax Basics]]

[[Debugging]]

[[Event-Driven Software Architecture]]
## Get to Know Your Options

There are three core programmatic technologies to learn about as a Salesforce developer.

-   [[Lightning Component Framework]]: A UI development framework similar to AngularJS or React.
-   [[Apex]]: Salesforce’s proprietary programming language with Java-like syntax.
-   [[Visualforce]]: A markup language that lets you create custom Salesforce pages with code that looks a lot like HTML, and optionally can use a powerful combination of Apex and JavaScript.

Let’s do a quick overview of each of these technologies and see what they look like in our DreamHouse app.

# API Management
SOAP API
- Integrate your org’s data with other applications using standard SOAP protocols.

REST API
- Access objects in your org using standard REST protocols.

Metadata API
- Manage customizations in your org and build tools that manage your metadata model.

Tooling API
- Build custom development tools for platform applications.

Marketing Cloud API
- Expose Marketing Cloud capabilities with the REST API and get comprehensive access to most email functionality with the SOAP API.

Bulk API
- Load, delete, and perform asynchronous queries on large data sets.

Streaming API
- Send and receive notifications securely and efficiently. Notifications can reflect data changes in your org, or custom events.

Connect REST API
- Build UI for Commerce, CMS-Managed Content, Experience Cloud Sites, Files, Notifications, Topics, and more.

Mobile SDK
- While it’s technically a software development kit, it’s worth including here. Integrate Native or Hybrid mobile apps directly with Salesforce.




# Learn More?

**There is no such thing as an application or session variable in the Lightning Platform.** If you need data to persist between classes, you do have static variables, but keep in mind that static variables in the Lightning Platform don’t work the same as they do in .NET. In the Lightning Platform world, a static variable can only persist information within a single execution context, although other options for maintaining data across trigger invocations are available. Check out the Advanced Apex links in Internet Resources to learn more.



#SalesforceDevPortal


### Deeper Dive
[[Aura]]