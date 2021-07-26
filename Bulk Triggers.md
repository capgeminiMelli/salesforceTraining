## Bulk Trigger Design Patterns

Apex triggers are optimized to operate in bulk. We recommend using bulk design patterns for processing records in triggers. When you use bulk design patterns, your triggers have better performance, consume less server resources, and are less likely to exceed platform limits.

The benefit of bulkifying your code is that bulkified code can process large numbers of records efficiently and run within governor limits on the Lightning Platform. These governor limits are in place to ensure that runaway code doesn’t monopolize resources on the multitenant platform.

The following sections demonstrate the main ways of bulkifying your Apex code in triggers: operating on all records in the trigger, and performing SOQL and DML on collections of sObjects instead of single sObjects at a time. The SOQL and DML bulk best practices apply to any Apex code, including SOQL and DML in classes. The examples given are based on triggers and use the Trigger.New context variable.

### Operating on Record Sets

Let’s first look at the most basic bulk design concept in triggers. Bulkified triggers operate on all sObjects in the trigger context. Typically, triggers operate on one record if the action that fired the trigger originates from the user interface. But if the origin of the action was bulk DML or the API, the trigger operates on a record set rather than one record. For example, when you import many records via the API, triggers operate on the full record set. Therefore, a good programming practice is to always assume that the trigger operates on a collection of records so that it works in all circumstances.

The following trigger assumes that only one record caused the trigger to fire. This trigger doesn’t work on a full record set when multiple records are inserted in the same transaction. A bulkified version is shown in the next example.

```java
trigger MyTriggerNotBulk on Account(before insert) {
    Account a = Trigger.New[0];
    a.Description = 'New description';
}
```

Copy

This example is a modified version of MyTrigger. It uses a for loop to iterate over all available sObjects. This loop works if Trigger.New contains one sObject or many sObjects.

```java
trigger MyTriggerBulk on Account(before insert) {
    for(Account a : Trigger.New) {
        a.Description = 'New description';
    }
}
```

Copy

### Performing Bulk SOQL

SOQL queries can be powerful. You can retrieve related records and check a combination of multiple conditions in one query. By using SOQL features, you can write less code and make fewer queries to the database. Making fewer database queries helps you avoid hitting query limits, which are 100 SOQL queries for synchronous Apex or 200 for asynchronous Apex.

The following trigger shows a SOQL query pattern to avoid. The example makes a SOQL query inside a for loop to get the related opportunities for each account, which runs once for each Account sObject in Trigger.New. If you have a large list of accounts, a SOQL query inside a for loop could result in too many SOQL queries. The next example shows the recommended approach.

```java
trigger SoqlTriggerNotBulk on Account(after update) {   
    for(Account a : Trigger.New) {
        // Get child records for each account
        // Inefficient SOQL query as it runs once for each account!
        Opportunity[] opps = [SELECT Id,Name,CloseDate 
                             FROM Opportunity WHERE AccountId=:a.Id];
        
        // Do some other processing
    }
}
```

Copy

This example is a modified version of the previous one and shows a best practice for running SOQL queries. The SOQL query does the heavy lifting and is called once outside the main loop.

-   The SOQL query uses an inner query—(SELECT Id FROM Opportunities)—to get related opportunities of accounts.
-   The SOQL query is connected to the trigger context records by using the IN clause and binding the Trigger.New variable in the WHERE clause—WHERE Id IN :Trigger.New. This WHERE condition filters the accounts to only those records that fired this trigger.

Combining the two parts in the query results in the records we want in one call: the accounts in this trigger with the related opportunities of each account.