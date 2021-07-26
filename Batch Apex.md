## Batch Apex

Batch Apex is used to run large jobs (think thousands or millions of records!) that would exceed normal processing limits. Using Batch Apex, you can process records asynchronously in batches (hence the name, “Batch Apex”) to stay within platform limits. If you have a lot of records to process, for example, data cleansing or archiving, Batch Apex is probably your best solution.

Here’s how Batch Apex works under the hood. Let’s say you want to process 1 million records using Batch Apex. The execution logic of the batch class is called once for each batch of records you are processing. Each time you invoke a batch class, the job is placed on the Apex job queue and is executed as a discrete transaction. This functionality has two awesome advantages:

-   Every transaction starts with a new set of governor limits, making it easier to ensure that your code stays within the governor execution limits.
-   If one batch fails to process successfully, all other successful batch transactions aren’t rolled back.

## Batch Apex Syntax

To write a Batch Apex class, your class must implement the Database.Batchable interface and include the following three methods:

**start**

Used to collect the records or objects to be passed to the interface method execute for processing. This method is called once at the beginning of a Batch Apex job and returns either a Database.QueryLocator object or an Iterable that contains the records or objects passed to the job.

Most of the time a QueryLocator does the trick with a simple SOQL query to generate the scope of objects in the batch job. But if you need to do something crazy like loop through the results of an API call or pre-process records before being passed to the execute method, you might want to check out the Custom Iterators link in the Resources section.

With the QueryLocator object, the governor limit for the total number of records retrieved by SOQL queries is bypassed and you can query up to 50 million records. However, with an Iterable, the governor limit for the total number of records retrieved by SOQL queries is still enforced.

**execute**

Performs the actual processing for each chunk or “batch” of data passed to the method. The default batch size is 200 records. Batches of records are not guaranteed to execute in the order they are received from the start method.

This method takes the following:

-   A reference to the Database.BatchableContext object.
-   A list of sObjects, such as List<sObject>, or a list of parameterized types. If you are using a Database.QueryLocator, use the returned list.

**finish**  
Used to execute post-processing operations (for example, sending an email) and is called once after all batches are processed.

  
Here’s what the skeleton of a Batch Apex class looks like:

```java
public class MyBatchClass implements Database.Batchable<sObject> {
    public (Database.QueryLocator | Iterable<sObject>) start(Database.BatchableContext bc) {
        // collect the batches of records or objects to be passed to execute
    }
    public void execute(Database.BatchableContext bc, List<P> records){
        // process each batch of records
    }
    public void finish(Database.BatchableContext bc){
        // execute any post-processing operations
    }
}
```



## Invoking a Batch Class

To invoke a batch class, simply instantiate it and then call Database.executeBatch with the instance:

```java
MyBatchClass myBatchObject = new MyBatchClass();
Id batchId = Database.executeBatch(myBatchObject);
```



You can also optionally pass a second scope parameter to specify the number of records that should be passed into the execute method for each batch. Pro tip: you might want to limit this batch size if you are running into governor limits.

```java
Id batchId = Database.executeBatch(myBatchObject, 100);
```



Each batch Apex invocation creates an AsyncApexJob record so that you can track the job’s progress. You can view the progress via SOQL or manage your job in the Apex Job Queue. We’ll talk about the Job Queue shortly.

```java
AsyncApexJob job = [SELECT Id, Status, JobItemsProcessed, TotalJobItems, NumberOfErrors FROM AsyncApexJob WHERE ID = :batchId ];
```



## Using State in Batch Apex

Batch Apex is typically stateless. Each execution of a batch Apex job is considered a discrete transaction. For example, a batch Apex job that contains 1,000 records and uses the default batch size is considered five transactions of 200 records each.

If you specify Database.Stateful in the class definition, you can maintain state across all transactions. When using Database.Stateful, only instance member variables retain their values between transactions. Maintaining state is useful for counting or summarizing records as they’re processed. In our next example, we’ll be updating contact records in our batch job and want to keep track of the total records affected so we can include it in the notification email.