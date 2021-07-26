### Writing Parent-to-Children Queries

Parent-to-children queries also use the relationship name, but they use it in what is called a nested select query. As with the last query type, it’s better to explain this by showing you an example.

This time we’ll write a query from the parent Account object and have it include a nested query that also returns information about each associated contact.

1.  In Developer Console, click the **Query Editor** tab in the bottom pane.
2.  Delete the existing code, and insert the following snippet:
    
    ```java
    SELECT Name, (Select FirstName, LastName FROM Contacts) FROM Account
    ```
    
    Copy
    

The relationship name inside the nested query uses the plural name Contacts, as opposed to Contact. This detail is important to understand, and it’s the part that usually trips people up. When working with relationship queries, the parent-to-child relationship name must be a plural name.

**When working with custom objects, the relationship name is not only plural, but it is appended with two underscores and an r. For example, the relationship name for the custom object My_Object__c is My_Objects__r.**

1.  Click **Execute**.
2.  The query results include two columns. Notice in the following image how the results under the Contacts column are displayed. Because each account is typically associated with multiple contacts, the first and last names are displayed in JSON format.

![SOQL Query Results displayed in Developer Console](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/database_basics_dotnet/sql_to_soql/images/197101a1dbfd2a92e03343d4f51b5944_image_0.png)

Once again, let’s look at how that same query is written in SQL. For this query, the SQL equivalent is a left outer join similar to the following:

```java
    SELECT a.Name, c.FirstName, c.LastName
    FROM Account a
    LEFT JOIN Contact c ON (a.Id = c.AccountId)
```

Copy

The SQL query gets all Account records and any contacts associated with those accounts. The output returned in SQL isn’t formatted as JSON. Other than that, the SQL and SOQL queries produce the same results.

At this point, you might be wondering whether SOQL supports aliasing. It does, but not how you’re used to working with it in SQL. SOQL has no AS keyword. You can use aliases to represent object names in SOQL queries, but for field names, aliasing works only for aggregate queries, which we’ll be covering next.

Remember, to dive deeper into this topic, check out the hands-on training video link in the Resources section.


### Write a Child-to-Parent Query

Let’s say that you wanted to write a query that returns Account and Contact information. Your first option is to write a child-to-parent query. This relationship query uses "dot notation" to access data from the parent, that is, a period separates the relationship name from the name of the field being queried.

To see how this works, we’ll walk through writing a relationship query that returns a list of contacts, including the name of the associated account. But this time, instead of using Workbench, we’ll use the Query Editor tab in Developer Console.

1.  In your DE org, select _Your Name_ > **Developer Console** to open Developer Console.
2.  In Developer Console, click the **Query Editor** tab in the bottom pane.
3.  Delete the existing code, and insert the following snippet:
    
    ```java
    SELECT FirstName, LastName, Account.Name FROM Contact
    ```
    
    Copy
    
4.  Click **Execute**.
    
5.  The query results include three columns. Scroll through the results. Some results under the Account.name field are null because not all contacts are related to an account.
    

Because we know you’re probably still thinking in SQL terms, imagine this scenario. If you had two SQL tables named Account and Contact with a one-to-many relationship between the tables, how would you go about writing a SQL query that returned this same information?

You would use a join, of course. But in this case, you need a right outer join, because you want an equivalent query that returns all contacts, even those not related to an account. And that might look something like the following:

```java
    SELECT c.FirstName, c.LastName, a.Name FROM Account a
    RIGHT JOIN Contact c ON (c.AccountId = a.Id)
```

Copy

So now we want you to go back and look at the equivalent SOQL query, which was, in case you don’t remember:

```java
    SELECT FirstName, LastName, Account.Name FROM Contact
```

Copy

The SOQL query looks much simpler, don’t you think?

To be honest, relationship queries can get a little tricky sometimes, especially when figuring out what the relationship name is for custom objects. To learn more about converting SQL queries into SOQL queries, check out this [hands-on training video](https://www.salesforce.com/video/308034/).

One super important thing to be aware of with these types of queries is that you can traverse five levels up with the dot notation. So you can go from the child to the parent to the grandparent to the great grandparent, and so on.