## Manipulate Records with DML

Create and modify records in Salesforce by using the Data Manipulation Language, abbreviated as DML. DML provides a straightforward way to manage records by providing simple statements to insert, update, merge, delete, and restore records.

Because Apex is a data-focused language and is saved on the Lightning Platform, it has direct access to your data in Salesforce. Unlike other programming languages that require additional setup to connect to data sources, with Apex DML, managing records is made easy! By calling DML statements, you can quickly perform operations on your Salesforce records.

This example adds the Acme account to Salesforce. An account sObject is created first and then passed as an argument to the insert statement, which persists the record in Salesforce.

```java
// Create the account sObject 
Account acct = new Account(Name='Acme', Phone='(415)555-1212', NumberOfEmployees=100);
// Insert the account by using DML
insert acct;
```


### DML Statements

The following DML statements are available.

-   insert
-   update
-   upsert
-   delete
-   undelete
-   merge

Each DML statement accepts either a single sObject or a list (or array) of sObjects. Operating on a list of sObjects is a more efficient way for processing records.

All those statements, except a couple, are familiar database operations. The upsert and merge statements are particular to Salesforce and can be quite handy.

The upsert DML operation creates new records and updates sObject records within a single statement, using a specified field to determine the presence of existing objects, or the ID field if no field is specified.

The merge statement merges up to three records of the same sObject type into one of the records, deleting the others, and re-parenting any related records.

### ID Field Auto-Assigned to New Records

When inserting records, the system assigns an ID for each record. In addition to persisting the ID value in the database, the ID value is also autopopulated on the sObject variable that you used as an argument in the DML call.

This example shows how to get the ID on the sObject that corresponds to the inserted account.

```java
// Create the account sObject 
Account acct = new Account(Name='Acme', Phone='(415)555-1212', NumberOfEmployees=100);
// Insert the account by using DML
insert acct;
// Get the new ID on the inserted sObject argument
ID acctID = acct.Id;
// Display this ID in the debug log
System.debug('ID = ' + acctID);
// Debug log result (the ID will be different in your case)
// DEBUG|ID = 001D000000JmKkeIAF
```



#### Beyond the Basics

Because the sObject variable in the example contains the ID after the DML call, you can reuse this sObject variable to perform further DML operations, such as updates, as the system will be able to map the sObject variable to its corresponding record by matching the ID.

You can retrieve a record from the database to obtain its fields, including the ID field, but this can’t be done with DML. You’ll need to write a query by using SOQL. You’ll learn about SOQL in another unit.

### Bulk DML

You can perform DML operations either on a single sObject, or in bulk on a list of sObjects. Performing bulk DML operations is the recommended way because it helps avoid hitting governor limits, **such as the DML limit of 150 statements per Apex transaction**. This limit is in place to ensure fair access to shared resources in the Lightning Platform. Performing a DML operation on a list of sObjects counts as one DML statement, not as one statement for each sObject.

This example inserts contacts in bulk by inserting a list of contacts in one call. The sample then updates those contacts in bulk too.

1.  Execute this snippet in the Developer Console using Anonymous Apex.
    
    ```java
    // Create a list of contacts
    List<Contact> conList = new List<Contact> {
        new Contact(FirstName='Joe',LastName='Smith',Department='Finance'),
            new Contact(FirstName='Kathy',LastName='Smith',Department='Technology'),
            new Contact(FirstName='Caroline',LastName='Roth',Department='Finance'),
            new Contact(FirstName='Kim',LastName='Shain',Department='Education')};
                
    // Bulk insert all contacts with one DML call
    insert conList;
    // List to hold the new contacts to update
    List<Contact> listToUpdate = new List<Contact>();
    // Iterate through the list and add a title only
    //   if the department is Finance
    for(Contact con : conList) {
        if (con.Department == 'Finance') {
            con.Title = 'Financial analyst';
            // Add updated contact sObject to the list.
            listToUpdate.add(con);
        }
    }
    // Bulk update all contacts with one DML call
    update listToUpdate;
    ```
    
    Copy
    
2.  Inspect the contacts recently created in your org.
    
    Two of the contacts who are in the Finance department should have their titles populated with Financial analyst.
    

### Upserting Records

If you have a list containing a mix of new and existing records, you can process insertions and updates to all records in the list by using the upsert statement. Upsert helps avoid the creation of duplicate records and can save you time as you don’t have to determine which records exist first.

The upsert statement matches the sObjects with existing records by comparing values of one field. If you don’t specify a field when calling this statement, the upsert statement uses the sObject’s ID to match the sObject with existing records in Salesforce. Alternatively, you can specify a field to use for matching. For custom objects, specify a custom field marked as external ID. For standard objects, you can specify any field that has the idLookup property set to true. For example, the Email field of Contact or User has the idLookup property set. To check a field’s property, see the [Object Reference for Salesforce and Lightning Platform](https://developer.salesforce.com/docs/atlas.en-us.224.0.object_reference.meta/object_reference/ "HTML (New Window)").

**Upsert Syntax**

upsert sObject | sObject[]

upsert sObject | sObject[]​​ field

The optional field is a field token. For example, to specify the MyExternalID field, the statement is:

```java
upsert sObjectList Account.Fields.MyExternalId;
```

Copy

Upsert uses the sObject record's primary key (the ID), an idLookup field, or an external ID field to determine whether it should create a new record or update an existing one:

-   If the key is not matched, a new object record is created.
-   If the key is matched once, the existing object record is updated.
-   If the key is matched multiple times, an error is generated and the object record is neither inserted or updated.

This example shows how upsert updates an existing contact record and inserts a new contact in one call. This upsert call updates the existing Josh contact and inserts a new contact, Kathy.

![Note](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/apex_database/apex_database_dml/images/c4d9ef0c272016519cf3740a5172d683_icon_note.png)

#### Note

The upsert call uses the ID to match the first contact. The josh variable is being reused for the upsert call. This variable has already been populated with the record ID from the previous insert call, so the ID doesn’t need to be set explicitly in this example.

1.  Execute this snippet in the Execute Anonymous window of the Developer Console.
    
    ```java
    // Insert the Josh contact
    Contact josh = new Contact(FirstName='Josh',LastName='Kaplan',Department='Finance');       
    insert josh;
    // Josh's record has been inserted
    //   so the variable josh has now an ID
    //   which will be used to match the records by upsert
    josh.Description = 'Josh\'s record has been updated by the upsert operation.';
    // Create the Kathy contact, but don't persist it in the database
    Contact kathy = new Contact(FirstName='Kathy',LastName='Brown',Department='Technology');
    // List to hold the new contacts to upsert
    List<Contact> contacts = new List<Contact> { josh, kathy };
    // Call upsert
    upsert contacts;
    // Result: Josh is updated and Kathy is created.
    ```
    
    Copy
    
2.  Inspect all contacts in your org.
    
    Your org will have only one Josh Kaplan record, not two, because the upsert operation found the existing record and updated it instead of creating a new contact record. One Kathy Brown contact record will be there too.