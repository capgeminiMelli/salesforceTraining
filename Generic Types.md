## Working with the Generic sObject Data Type

Typically, you use the specific sObject data type, such as Account for a standard object or Book__c for a custom object called Book, when working with sObjects. However, when you don’t know the type of sObject your method is handling, you can use the generic sObject data type.

Variables that are declared with the generic sObject data type can reference any Salesforce record, whether it is a standard or custom object record.

![A generic sObject variable can point to any Salesforce record](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/apex_database/apex_database_sobjects/images/00cce42fb16c55ee922914d4b2383235_apex_database_sobject_generic.png)

This example shows how the generic sObject variable can be assigned to any Salesforce object: an account and a custom object called Book__c.

```java
sObject sobj1 = new Account(Name='Trailhead');
sObject sobj2 = new Book__c(Name='Workbook 1');
```

Copy

In contrast, variables that are declared with the specific sObject data type can reference only the Salesforce records of the same type.

![A specific sObject variable can point to the Salesforce record of the same type only](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/apex_database/apex_database_sobjects/images/ba372555470a67811e17c68936f39cf4_apex_database_sobject_specific.png)

### Casting Generic sObjects to Specific sObject Types

When you’re dealing with generic sObjects, you sometimes need to cast your sObject variable to a specific sObject type. One of the benefits of doing so is to be able to access fields using dot notation, which is not available on the generic sObject. Since sObject is a parent type for all specific sObject types, you can cast a generic sObject to a specific sObject. This example shows how to cast a generic sObject to Account.

```java
// Cast a generic sObject to an Account
Account acct = (Account)myGenericSObject;
// Now, you can use the dot notation to access fields on Account
String name = acct.Name;
String phone = acct.Phone;
```

Copy

### Tell Me More...

Unlike specific sObjects types, generic sObjects can be created only through the newSObject() method. Also, the fields of a generic sObject can be accessed only through the put() and get() methods.

In this unit, you’ve learned what sObjects are and how to use them. However, creating an sObject doesn’t persist it as a record in the database. To save the sObject as a record, and do other things with it, use the Data Manipulation Language (DML). To retrieve a record, use the Salesforce Object Query Language (SOQL). Check out later units to learn about DML and SOQL.