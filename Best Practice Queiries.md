## Best Practices

We know .NET developers love to think about best practices. You love to challenge yourself and always look for the best way of doing things. We get that. So we thought you would love to learn which best practices to use to build fast and efficient search queries.

### [](https://trailhead.salesforce.com/content/learn/modules/database_basics_dotnet/writing_efficient_queries#building-selective-queries)Building Selective Queries

In the first unit we covered SOQL statements and how you can apply filters using the WHERE clause. You can even combine multiple fields using AND and OR clauses.

Well, and we know you won’t be surprised to hear this, having more fields in your WHERE clause is a good thing. Obviously, the less data that your query returns, the better. But what you might not know is that not all fields are the same. Some fields are what you can think of as "power" fields. If you use these power fields in the WHERE clause, your queries are super-duper fast.

And what makes these power fields so powerful? Indexes, of course.

For all standard and custom tables, certain fields are automatically flagged to be indexed. These fields include the following:

Indexed Field

Description

Id

Unique 18-character field that is system generated. This is the primary key for the object.

Name

Text-based field.

OwnerId

Reference to the owner of the object.

CreatedDate

Date and time when the record was created.

SystemModStamp

Read-only field that contains the last date that the record was updated. This field is indexed where the similar LastModifiedDate is not, so consider using this one in your queries.

RecordType

Id of the RecordType. RecordTypes are used to offer different UI results to certain users.

Master-Detail Fields

Foreign key field used to indicate a master-detail relationship

Lookup Fields

Foreign key field used to indicate a lookup relationship

Unique Fields

Custom fields can be marked as unique when they are created, and this will automatically make them indexed.

External ID Fields

Like unique fields, these custom fields can be marked as an External Id and are mainly used for integration purposes.

Anytime you use one of these indexed fields in your query’s WHERE clause, you’re increasing the chance that your query is considered selective and an index used as opposed to a full table scan. We can’t stress enough how important this is when you’re dealing with large databases.

**Note**: It’s possible for Salesforce customers to request a custom index from Salesforce Support by creating a support case and including the SOQL query with the indexed field.

### [](https://trailhead.salesforce.com/content/learn/modules/database_basics_dotnet/writing_efficient_queries#index-selectivity-exceptions)Index Selectivity Exceptions

Using an indexed field in your query doesn’t always make it golden. You can do things in your queries to make them non-selective and thus prone to the dreaded full table scan. When building your queries always strive to avoid these things.

-   **Querying for null rows**—Queries that look for records in which the field is empty or null. For example:
    
    ```java
    SELECT Id, Name FROM Account WHERE Custom_Field__c = null
    ```
    
    Copy
    
-   **Negative filter operators**—Using operators such as !=, NOT LIKE, or EXCLUDES in your queries. For example:
    
    ```java
    SELECT CaseNumber FROM Case WHERE Status != ‘New’
    ```
    
    Copy
    
-   **Leading wildcards**—Queries that use a leading wildcard, such as this:
    
    ```java
    SELECT Id, LastName, FirstName FROM Contact WHERE LastName LIKE ‘%smi%’
    ```
    
    Copy
    
-   **Text fields with comparison operators**—Using comparison operators, such as >, <, >=, or <=, with text-based fields. For example:
    
    ```java
    SELECT AccountId, Amount FROM Opportunity WHERE Order_Number__c > 10
    ```
    
    Copy
    

## [](https://trailhead.salesforce.com/content/learn/modules/database_basics_dotnet/writing_efficient_queries#query-plan-tool)Query Plan Tool

Our friend the Developer Console contains a neat little tool to speed up your queries. It gives you a behind-the-scenes peek into how the Query Optimizer works. The Query Plan tool isn’t enabled by default. Enable it by doing the following.

1.  From Setup, select _Your Name_ > **Developer Console** to open Developer Console.
2.  In theDeveloper Console, select **Help > Preferences**.
3.  Select **Enable Query Plan** and make sure that it’s set to true.
4.  Click **Save**.
5.  In the Query Editor tab, confirm that the Query Plan button is now next to the Execute button.

Now that the Query Plan tool is enabled, you can use it to evaluate queries. Let’s start by using it to evaluate a poorly performing query.

1.  In Developer Console, click the **Query Editor** tab in the bottom pane.
    
2.  Delete the existing code, and insert the following snippet:
    
    ```java
    SELECT Id, CaseNumber FROM Case WHERE Status != 'New'
    ```
    
    Copy
    
3.  Click **Query Plan**.
    

The Query Plan dialog displays a table that lists the cost of the query and that it will be doing a TableScan. This is not a good thing. Check out the notes in the bottom pane, which further explain the results.

Now let’s look at another query that gets the same results as the first query.

1.  Click the **Query Editor** tab in the bottom pane.
    
2.  Delete the existing code, and insert the following snippet:
    
    ```java
    SELECT Id, CaseNumber FROM Case WHERE IsClosed = true
    ```
    
    Copy
    
3.  Click **Query Plan**.
    

The Query Plan dialog displays a table that lists the cost of the queries, but this time you see another row displayed indicating that it’s possible to use an index.

Both the queries that we ran through Query Plan retrieved the same number of rows, yet the execution plans varied quite a bit because of the fields and operators we chose. These differences seem small because of the tiny amount of data you have in your development org, but when you start comparing queries in orgs with millions of records, these differences can be game-changing.

For more information about what each column in the Query Plan tool reveals, see the link about the Query Plan tool in Resources.

## [](https://trailhead.salesforce.com/content/learn/modules/database_basics_dotnet/writing_efficient_queries#tell-me-more)Tell Me More

Always strive to avoid creating queries with non-deterministic formula fields. Formula fields are custom fields that allow you to dynamically calculate a field’s value at runtime. These types of fields tend to be popular in most orgs and can easily be overused. A formula field is considered non-deterministic when its value varies over time. Check the link in Resources about SOQL best practices: Nulls and Formula Fields for more info. <>

Unfortunately, you can’t use the Query Plan tool to evaluate SOSL queries, but that doesn’t meant that you don’t consider performance with those types of queries. Learn more about what to avoid when writing SOSL queries by referring to the Best Practices and Performance Tips links referenced in Resources. >


## Optimize SOSL

Now let’s talk search results. Yes, users think they want to see ALL THE RESULTS! But if you have thousands of records, it’s time to reconsider that stance. Think about how you could limit the results or at least break them up into smaller, easier-to-digest chunks.

Again, turning to SOSL, you can use `RETURNING FieldSpec` to specify which data is returned. We used it in the last unit, but let’s talk about the more advanced (read: awesome) elements it includes.

-   ObjectTypeName—Specifies the object to return.
-   FieldList—Specifies the fields to return.
-   ORDER By—Specifies which fields to order the results by. You can also specify ascending or descending order.
-   LIMIT n—Sets the maximum number of records returned for the given object.
-   OFFSET n—Sets the starting row offset into the result set returned by your query.

That’s a lot to take in. Let’s go through it step-by-step.