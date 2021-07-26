## Apex

Use Apex when you need more functionality than is available in Flow Builder. Build the more complex functionality as invocable Apex methods. Then call the resulting Apex as an Apex action in the process or as an Apex action element in the flow.

## Get Started with Apex

Apex is a programming language that uses Java-like syntax and acts like database stored procedures. Apex enables developers to add business logic to system events, such as button clicks, updates of related records, and Visualforce pages.

As a language, Apex is:

-   Hosted—Apex is saved, compiled, and executed on the server—the Lightning Platform.
-   Object oriented—Apex supports classes, interfaces, and inheritance.
-   Strongly typed—Apex validates references to objects at compile time.
-   Multitenant aware—Because Apex runs in a multitenant platform, it guards closely against runaway code by enforcing limits, which prevent code from monopolizing shared resources.
-   Integrated with the database—It is straightforward to access and manipulate records. Apex provides direct access to records and their fields, and provides statements and query languages to manipulate those records.
-   Data focused—Apex provides transactional access to the database, allowing you to roll back operations.
-   Easy to use—Apex is based on familiar Java idioms.
-   Easy to test—Apex provides built-in support for unit test creation, execution, and code coverage. Salesforce ensures that all custom Apex code works as expected by executing all unit tests prior to any platform upgrades.
-   Versioned—Custom Apex code can be saved against different versions of the API.
## Features of Apex

There are primitive types, such as Integer, Double, Long, Date, .... There is also an **ID datatype** that is used for any valid 18 character lightning platform record identifier assigned by the system.

*All variables are initalized to null by default*

Besides primitives, supported data types include **sObjects**, either as a generic sObject or a specific one, such as an Account or Contact. Remember, an sObject is just a Salesforce object.

### Apex and Database are Tightly Coupled

Apex code and the Lightning Platform database are tightly coupled to the point where they are sometimes indistinguishable. Each standard or custom object in the database has a "mystical" representation via an Apex class that provides all sorts of functionality to make interacting with the database a snap. The class and its underlying object are essentially a mirror image of one another that is constantly in sync. For instance, whenever you create a new field in an object, a class member is automatically surfaced to reference the values in the database. It's also impossible to add a reference in your Apex code to a field that doesn't exist; the compiler will return an error and simply not save your code. The platform works hard to ensure these dependencies and won't let the database schema and your code become out of sync. Therefore, if you attempt to delete a custom object or a field that is referenced by Apex code, the platform will raise an error and disallow the action.

## What Is Execution Context?

For ASP.NET applications, code is executed in the context of an application domain. In the Lightning Platform world, code executes within an execution context. In a nutshell, this context represents the time between when the code is executed and when it ends. The important thing for you to understand is that the Apex code you write is not always the only code that is executing.

To understand how this works, you need to know all the ways Apex code can be executed on the platform.

#### Methods of Invoking Apex


**Database Trigger**

- Invoked for a specific event on a custom or standard object.

**Anonymous Apex**

- Code snippets executed on the fly in Dev Console & other tools.

**Asynchronous Apex**

- Occurs when executing a future or queueable Apex, running a batch job, or scheduling Apex to run at a specified interval.

**Web Services**

- Code that is exposed via SOAP or REST web services.

**Email Services**

 - Code that is set up to process inbound email.

**Visualforce or Lightning Pages**

- Visualforce controllers and Lightning components can execute Apex code automatically or when a user initiates an action, such as clicking a button. Lightning components can also be executed by Lightning processes and flows.

Besides invoking Apex code, actions, such as creating a new task, sending an email, performing a field update, or sending an outbound message, can all be triggered by one of the declarative platform features. These actions also run within an execution context.


Another important consideration is the contect of the user executing the Apex code. By default, APex executes in the system context. 




## Special Text
-  **@InvocableMethod** annotation. It has a label attribute that allows other tools like Process Builder to execute the method.


### Further Reading
[[Triggers]]

[[Generic Types]]

[[DML]]

[[ SOSL Queries]]

[[Parent to CHildern Queries]]

[[Apex Unit Test]]

[[Async]]

[[Integrations]]