## Future Apex

Future Apex is used to run processes in a separate thread, at a later time when system resources become available.

Note: Technically, you use the @future annotation to identify methods that run asynchronously. However, because "methods identified with the @future annotation" is laborious, they are commonly referred to as "future methods" and that’s how we’ll reference them for the remainder of this module.

When using synchronous processing, all method calls are made from the same thread that is executing the Apex code, and no additional processing can occur until the process is complete. You can use future methods for any operation you’d like to run asynchronously in its own thread. This provides the benefits of not blocking the user from performing other operations and providing higher governor and execution limits for the process. Everyone’s a winner with asynchronous processing.

Future methods are typically used for:

-   Callouts to external Web services. If you are making callouts from a trigger or after performing a DML operation, you must use a future or queueable method. A callout in a trigger would hold the database connection open for the lifetime of the callout and that is a "no-no" in a multitenant environment.
-   Operations you want to run in their own thread, when time permits such as some sort of resource-intensive calculation or processing of records.
-   Isolating DML operations on different sObject types to prevent the mixed DML error. This is somewhat of an edge-case but you may occasionally run across this issue. See [sObjects That Cannot Be Used Together in DML Operations](https://developer.salesforce.com/docs/atlas.en-us.224.0.apexcode.meta/apexcode/apex_dml_non_mix_sobjects.htm) for more details.

## Future Method Syntax

Future methods must be static methods, and can only return a void type. The specified parameters must be primitive data types, arrays of primitive data types, or collections of primitive data types. Notably, future methods can’t take standard or custom objects as arguments. A common pattern is to pass the method a List of record IDs that you want to process asynchronously.

```java
global class SomeClass {
  @future
  public static void someFutureMethod(List<Id> recordIds) {
    List<Account> accounts = [Select Id, Name from Account Where Id IN :recordIds];
    // process account records to do awesome stuff
  }
}
```

Copy

![Note](https://res.cloudinary.com/hy4kyit2a/image/upload/doc/trailhead/en-usb473bb5ea1b7e61dfb07e6a7e547de6b.gif)

The reason why objects can’t be passed as arguments to future methods is because the object can change between the time you call the method and the time that it actually executes. Remember, future methods are executed when system resources become available. In this case, the future method may have an old object value when it actually executes, which can cause all sorts of bad things to happen.


## Best Practices

Since every future method invocation adds one request to the asynchronous queue, avoid design patterns that add large numbers of future requests over a short period of time. If your design has the potential to add 2000 or more requests at a time, requests could get delayed due to flow control. Here are some best practices you want to keep in mind:

-   Ensure that future methods execute as fast as possible.
-   If using Web service callouts, try to bundle all callouts together from the same future method, rather than using a separate future method for each callout.
-   Conduct thorough testing at scale. Test that a trigger enqueuing the @future calls is able to handle a trigger collection of 200 records. This helps determine if delays may occur given the design at current and future volumes.
-   Consider using Batch Apex instead of future methods to process large number of records asynchronously. This is more efficient than creating a future request for each record.

## Things to Remember

Future methods are a great tool, but with great power comes great responsibility. Here are some things to keep in mind when using them:

-   Methods with the future annotation must be static methods, and can only return a void type.
-   The specified parameters must be primitive data types, arrays of primitive data types, or collections of primitive data types; future methods can’t take objects as arguments.
-   Future methods won’t necessarily execute in the same order they are called. In addition, it’s possible that two future methods could run concurrently, which could result in record locking if the two methods were updating the same record.
-   Future methods can’t be used in Visualforce controllers in getMethodName(), setMethodName(), nor in the constructor.
-   You can’t call a future method from a future method. Nor can you invoke a trigger that calls a future method while running a future method. See the link in the Resources for preventing recursive future method calls.
-   The getContent() and getContentAsPDF() methods can’t be used in methods with the future annotation.
-   You’re limited to 50 future calls per Apex invocation, and there’s an additional limit on the number of calls in a 24-hour period. For more information on limits, see the link below.