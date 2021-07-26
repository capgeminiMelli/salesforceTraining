## Apex Unit Tests

The Apex testing framework enables you to write and execute tests for your Apex classes and triggers on the Lightning Platform. Apex unit tests ensure high quality for your Apex code and let you meet requirements for deploying Apex.

Testing is the key to successful long-term development and is a critical component of the development process. The Apex testing framework makes it easy to test your Apex code. Apex code can only be written in a sandbox environment or a Developer org, not in production. Apex code can be deployed to a production org from a sandbox. Also, app developers can distribute Apex code to customers from their Developer orgs by uploading packages to the Lightning Platform​ AppExchange. In addition to being critical for quality assurance, Apex unit tests are also requirements for deploying and distributing Apex. The following are the benefits of Apex unit tests.

### Test Method Syntax

Test methods take no arguments and have the following syntax:

```java
@isTest static void testName() {
    // code_block
}
```

Copy

Alternatively, a test method can have this syntax:

```java
static testMethod void testName() {
    // code_block
}
```

Copy

Using the isTest annotation instead of the testMethod keyword is more flexible as you can specify parameters in the annotation. We’ll cover one such parameter later.

The visibility of a test method doesn’t matter, so declaring a test method as public or private doesn’t make a difference as the testing framework is always able to access test methods. For this reason, the access modifiers are omitted in the syntax.

Test methods must be defined in test classes, which are classes annotated with isTest. This sample class shows a definition of a test class with one test method.

```java
@isTest
private class MyTestClass {
    @isTest static void myTest() {
        // code_block
    }
}
```

Copy

Test classes can be either private or public. If you’re using a test class for unit testing only, declare it as private. Public test classes are typically used for test data factory classes, which are covered later.




### Creating Test Data

Salesforce records that are created in test methods aren’t committed to the database. They’re rolled back when the test finishes execution. This rollback behavior is handy for testing because you don’t have to clean up your test data after the test executes.

By default, Apex tests don’t have access to pre-existing data in the org, except for access to setup and metadata objects, such as the User or Profile objects. Set up test data for your tests. Creating test data makes your tests more robust and prevents failures that are caused by missing or changed data in the org. You can create test data directly in your test method, or by using a utility test class as you’ll find out later.

![Note](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/apex_testing/apex_testing_intro/images/c4d9ef0c272016519cf3740a5172d683_icon_note.png)

#### Note

Even though it is not a best practice to do so, there are times when a test method needs access to pre-existing data. To access org data, annotate the test method with @isTest(SeeAllData=true). The test method examples in this unit don’t access org data and therefore don’t use the SeeAllData parameter.

### Tell Me More...

-   You can save up to 6 MB of Apex code in each org. Test classes annotated with @isTest don’t count toward this limit.
-   Even though test data rolls back, no separate database is used for testing. As a result, for some sObjects that have fields with unique constraints, inserting duplicate sObject records results in an error.
-   Test methods don’t send emails.
-   Test methods can’t make callouts to external services. You can use mock callouts in tests.
-   SOSL searches performed in a test return empty results. To ensure predictable results, use Test.setFixedSearchResults() to define the records to be returned by the search.