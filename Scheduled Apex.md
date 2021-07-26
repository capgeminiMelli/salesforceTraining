## Scheduled Apex

The Apex Scheduler lets you delay execution so that you can run Apex classes at a specified time. This is ideal for daily or weekly maintenance tasks using Batch Apex. To take advantage of the scheduler, write an Apex class that implements the Schedulable interface, and then schedule it for execution on a specific schedule.

## Scheduled Apex Syntax

To invoke Apex classes to run at specific times, first implement the Schedulable interface for the class. Then, schedule an instance of the class to run at a specific time using the System.schedule method.

```java
global class SomeClass implements Schedulable {
    global void execute(SchedulableContext ctx) {
        // awesome code here
    }
}
```


The class implements the Schedulable interface and must implement the only method that this interface contains, which is the execute method.

## Sample Code

This class queries for open opportunities that should have closed by the current date, and creates a task on each one to remind the owner to update the opportunity.

```java
global class RemindOpptyOwners implements Schedulable {
    global void execute(SchedulableContext ctx) {
        List<Opportunity> opptys = [SELECT Id, Name, OwnerId, CloseDate
            FROM Opportunity
            WHERE IsClosed = False AND
            CloseDate < TODAY];
        // Create a task for each opportunity in the list
        TaskUtils.remindOwners(opptys);
    }
}
```

You can schedule your class to run either programmatically or from the Apex Scheduler UI.

The System.Schedule method takes three arguments: a name for the job, a CRON expression used to represent the time and date the job is scheduled to run, and the name of the class.

```java
RemindOpptyOwners reminder = new RemindOpptyOwners();
// Seconds Minutes Hours Day_of_month Month Day_of_week optional_year
String sch = '20 30 8 10 2 ?';
String jobID = System.schedule('Remind Opp Owners', sch, reminder);
```


For more information on the CRON expression used for scheduling, see the “Using the System.Schedule Method” section in [Apex Scheduler](https://developer.salesforce.com/docs/atlas.en-us.224.0.apexcode.meta/apexcode/apex_scheduler.htm).


## Things to Remember

Scheduled Apex has a number of items you need to be aware of (see Apex Scheduler in the Resources section for a complete list when you have time), but in general:

-   You can only have 100 scheduled Apex jobs at one time and there are maximum number of scheduled Apex executions per a 24-hour period. See Execution Governors and Limits in the Resources section for details.
-   Use extreme care if you’re planning to schedule a class from a trigger. You must be able to guarantee that the trigger won’t add more scheduled jobs than the limit.
-   Synchronous Web service callouts are not supported from scheduled Apex. To be able to make callouts, make an asynchronous callout by placing the callout in a method annotated with @future(callout=true) and call this method from scheduled Apex. However, if your scheduled Apex executes a batch job, callouts are supported from the batch class.