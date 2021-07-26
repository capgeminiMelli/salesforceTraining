## Trigger Essentials

Before learning more about the execution context, let’s take a step back to introduce you to the world of database triggers. Similar to triggers in SQL Server, Apex database triggers execute programming logic before or after events to records in Salesforce. When defining the trigger, you can specify more than one of the following events:

-   before insert
-   before update
-   before delete
-   after insert
-   after update
-   after delete
-   after undelete

The basic syntax for a trigger looks like the following:

```java
trigger TriggerName on ObjectName (trigger_events) {
   // code_block
}
```

Copy

Now we know how much .NET developers love to solve problems with code, but we have a super big productivity tip for you here. **You only want to resort to using a trigger when you are absolutely sure that the same thing cannot be accomplished with one of our point-and-click automation tools.**

To make your life easier, Salesforce platform includes several automation tools, such as Lightning Process Builder and Lightning Flow Builder, for managing business logic without writing code. In most cases, tasks that could once upon a time only be accomplished with a trigger are now better suited for one of the automation tools.


### Best Practices
It's considered a best practice to use only one trigger per object. By adopting this practice, you can aboid the common pitfalls that new developers fall into. 


## Example

This simple trigger fires before you insert an account and writes a message to the debug log.

1.  In the Developer Console, click **File** | **New** | **Apex Trigger**.
2.  Enter HelloWorldTrigger for the trigger name, and then select Account for the sObject. Click **Submit**.
3.  Replace the default code with the following.
    
    ```java
    trigger HelloWorldTrigger on Account (before insert) {
    	System.debug('Hello World!');
    }
    ```
    
    Copy
    
4.  To save, press **Ctrl+S**.
5.  To test the trigger, create an account.
    1.  Click **Debug** | **Open Execute Anonymous Window**.
    2.  In the new window, add the following and then click **Execute**.
        
        ```java
        Account a = new Account(Name='Test Trigger');
        insert a;
        ```
        
        Copy
        
6.  In the debug log, find the Hello World! statement. The log also shows that the trigger has been executed.

### Types of Triggers

There are two types of triggers.

-   Before triggers are used to update or validate record values before they’re saved to the database.
-   After triggers are used to access field values that are set by the system (such as a record's Id or LastModifiedDate field), and to affect changes in other records. The records that fire the _after trigger_ are read-only.

### Using Context Variables

To access the records that caused the trigger to fire, use context variables. For example, Trigger.New contains all the records that were inserted in insert or update triggers. Trigger.Old provides the old version of sObjects before they were updated in update triggers, or a list of deleted sObjects in delete triggers. Triggers can fire when one record is inserted, or when many records are inserted in bulk via the API or Apex. Therefore, context variables, such as Trigger.New, can contain only one record or multiple records. You can iterate over Trigger.New to get each individual sObject.

This example is a modified version of the HelloWorldTrigger example trigger. It iterates over each account in a for loop and updates the Description field for each.

```java
trigger HelloWorldTrigger on Account (before insert) {
    for(Account a : Trigger.New) {
        a.Description = 'New description';
    }   
}
```



#### Futher Reading

[[Bulk Triggers]]

[[Trigger Order of Execution]]