## What Is SOSL?

In the last unit you were introduced to [[SOQL]], and you learned how you can use it to query data in sObjects and their related tables. To perform text-based queries across multiple sObjects, you can use SOSL (Salesforce Object Search Language), Salesforce’s option for full-text searching.

As a .NET developer, you might be familiar with the full-text searching capabilities available with Microsoft SQL Server (MS FTS). You might also be familiar with a popular search engine library called Lucene.Net, which was ported from the original Java version to C#.

The good and bad news here is that SOSL is different from those full-text search alternatives. The biggest differences have to do with what is required to set up and maintain the indexes. Salesforce uses the open-source search and indexing engine Lucene to power SOSL, but it’s been set up so that you don’t have to worry about installing and configuring anything. You’re also not responsible for maintaining indexes. In fact, for the most part, you don’t have much control over how search indexes are used, which is good news because it means that writing SOSL queries is easy.

However, as a .NET developer you love to tweak and fine-tune your code. So hearing out that you have little control over the configuration and indexes might make you feel a tad uncomfortable. We want to reassure you that even though you have less control, you can still do things that improve query performance, for both SOSL and SOQL queries. Shortly, we’ll be covering these methods quite extensively, but for now, let’s go over how SOSL syntax differs.

## Write SOSL Queries

Salesforce Object Search Language (SOSL) is a Salesforce search language **that is used to perform text searches in records.** Use SOSL to search fields across multiple standard and custom object records in Salesforce. SOSL is similar to Apache Lucene.

Adding SOSL queries to Apex is simple—you can embed SOSL queries directly in your Apex code. When SOSL is embedded in Apex, it is referred to as inline SOSL.

This is an example of a SOSL query that searches for accounts and contacts that have any fields with the word 'SFDC'.

```java
List<List<SObject>> searchList = [FIND 'SFDC' IN ALL FIELDS 
                                      RETURNING Account(Name), Contact(FirstName,LastName)];
```

Copy

### Differences and Similarities Between [[SOQL]] and SOSL

Like SOQL, SOSL allows you to search your organization’s records for specific information. Unlike SOQL, which can only query one standard or custom object at a time, a single SOSL query can search all objects.

Another difference is that SOSL matches fields based on a word match while SOQL performs an exact match by default (when not using wildcards). For example, searching for 'Digital' in SOSL returns records whose field values are 'Digital' or 'The Digital Company', but SOQL returns only records with field values of 'Digital'.

[[SOQL]] and SOSL are two separate languages with different syntax. Each language has a distinct use case:

-   Use SOQL to retrieve records for a single object.
-   Use SOSL to search fields across multiple objects. SOSL queries can search most text fields on an object.

### Prerequisites

Some queries in this unit expect the org to have accounts and contacts. If you haven’t created the sample data in the SOQL unit, create sample data in this unit. Otherwise, you can skip creating the sample data in this section.

1.  In the Developer Console, open the Execute Anonymous window from the **Debug** menu.
2.  Insert the below snippet in the window and click **Execute**.

```java
// Add account and related contact
Account acct = new Account(
    Name='SFDC Computing',
    Phone='(415)555-1212',
    NumberOfEmployees=50,
    BillingCity='San Francisco');
insert acct;
// Once the account is inserted, the sObject will be 
// populated with an ID.
// Get this ID.
ID acctID = acct.ID;
// Add a contact to this account.
Contact con = new Contact(
    FirstName='Carol',
    LastName='Ruiz',
    Phone='(415)555-1212',
    Department='Wingo',
    AccountId=acctID);
insert con;
// Add account with no contact
Account acct2 = new Account(
    Name='The SFDC Query Man',
    Phone='(310)555-1213',
    NumberOfEmployees=50,
    BillingCity='Los Angeles',
    Description='Expert in wing technologies.');
insert acct2;
```

Copy


### Basic SOSL Syntax

SOSL allows you to specify the following search criteria:

-   Text expression (single word or a phrase) to search for
-   Scope of fields to search
-   List of objects and fields to retrieve
-   Conditions for selecting rows in the source objects

This is the syntax of a basic SOSL query:

```java
FIND 'SearchQuery' [IN SearchGroup] [RETURNING ObjectsAndFields]
```

Copy

SearchQuery is the text to search for (a single word or a phrase). Search terms can be grouped with logical operators (AND, OR) and parentheses. Also, search terms can include wildcard characters (*, ?). The * wildcard matches zero or more characters at the middle or end of the search term. The ? wildcard matches only one character at the middle or end of the search term.

Text searches are case-insensitive. For example, searching for Customer, customer, or CUSTOMER all return the same results.

SearchGroup is optional. It is the scope of the fields to search. If not specified, the default search scope is all fields. SearchGroup can take one of the following values.

-   ALL FIELDS
-   NAME FIELDS
-   EMAIL FIELDS
-   PHONE FIELDS
-   SIDEBAR FIELDS

ObjectsAndFields is optional. It is the information to return in the search result—a list of one or more sObjects and, within each sObject, list of one or more fields, with optional values to filter against. If not specified, the search results contain the IDs of all objects found.

### Single Words and Phrases

A SearchQuery contains two types of text:

-   **Single Word**— single word, such as test or hello. Words in the SearchQuery are delimited by spaces, punctuation, and changes from letters to digits (and vice-versa). Words are always case insensitive.
-   **Phrase**— collection of words and spaces surrounded by double quotes such as "john smith". Multiple words can be combined together with logic and grouping operators to form a more complex query.


## Building a SOSL Query

If you’re familiar with MS FTS, you know that you need to write SELECT queries that use a CONTAINS or FREETEXT statement. The powerful CONTAINS search, which has many variations, allows you to search for exact or fuzzy matches, as well as search for words that are close to another word.

SOSL uses a simpler search syntax that doesn’t use the SOQL SELECT keyword. Instead, it uses the FIND keyword. A basic query looks like the following:

```java
FIND {"grand*"} IN ALL FIELDS RETURNING Account(Name), Contact(LastName, FirstName, Email)
```

Copy

Breaking this down, we see that it has three parts.

### [](https://trailhead.salesforce.com/content/learn/modules/database_basics_dotnet/sosl_queries#find-clause-with-search-term)FIND Clause with Search Term

The FIND clause is required. It’s what makes the SOSL search unique. FIND is followed by whatever search term you’re looking for, whether it’s a single word or phrase. In this case, it’s the word “grand.” You can also include wildcard characters, which our example does, such as these two:

```java
* matches zero or more characters at the middle or end of the search term
? matches only one character at the middle or end of the search term
```

Copy

We talk more about wildcards in the next unit. But in the meantime, be aware that just because you can use a wildcard in both the middle and end of the search term, doesn’t mean you should. In fact, as a best practice, it’s not a good idea, because it can seriously impact query performance.

### [](https://trailhead.salesforce.com/content/learn/modules/database_basics_dotnet/sosl_queries#in-clause)IN Clause

Use the IN clause to specify a search group. It tells Salesforce which fields to search. But we have a really big thing that you need to be aware of here, so bear with us a bit.

In the example above, we specified ALL FIELDS. One might take this literally and think that all fields will be searched, but depending on which object you specify in the RETURNING clause, only certain text-based fields are included. Say what?

Like we said, bear with us here. You see, if the object you’re returning is an article, document, feed comment, feed item, file, product, or solution, ALL fields are searched because these are the types of objects where you would want to search all fields.

But if you’re searching through most standard or custom objects, which include all sorts of crazy non-text based fields, it makes sense to only search through the name, email, phone, and sidebar fields. By the way, this is the default behavior.

So let’s say that instead of specifying ALL FIELDS, you want to search only name fields. Then you would use NAME FIELDS. To search only phone fields, use PHONE FIELDS. See how this works?

### [](https://trailhead.salesforce.com/content/learn/modules/database_basics_dotnet/sosl_queries#returning-clause)RETURNING Clause

You use the RETURNING clause to specify which data to return and which objects to search. In the example above, we returned the Name field from Account and the Lastname, FirstName and Email fields from Contact. The search looked through all searchable fields on both objects, but the returned results only include those fields listed in parenthesis.

If you specify an object name without a field name in parenthesis, the search return only the ID for that object if a match is found.

The SOSL syntax has other optional clauses that you might be interested in, Check out the [official docs](https://developer.salesforce.com/docs/atlas.en-us.soql_sosl.meta/soql_sosl/sforce_api_calls_sosl_syntax.htm) to learn more about them.

Ok, so now you’re wondering how does SOSL compare to other full-text search engines when it comes to fuzzy matches. Other than the LIKE keyword that you can use in a SOQL query and the wildcards that you can use in the SOSL query, Salesforce provides only a synonym search to look for nicknames.





# Build Search for Common Use Cases
## Search Within a Single Object

Cloud Kicks is a growing startup, and marketing is working hard to get the word out. They’ve started several campaigns and have tracked them through Salesforce. Marketing and sales have requested a way to search only campaigns on the internal product website that you’re working on. Single object searches are best used when users need a quick way to search through one record type because they don’t want to be bogged down sifting through records that don’t apply to them.

To search within a single object using SOSL, simply specify that object in the request. It’s just that easy.

```java
FIND {term} RETURNING ObjectTypeName
```

Copy

In the example, term is what the user enters. ObjectTypeName limits search results to include only the sObject specified. So if the user wants to find the March 2016 email campaign, the request looks like:

```java
FIND {march 2016 email} RETURNING Campaign
```

Copy

We’ll get into all the cool stuff you can do with RETURNING and how to refine your search for the best results in the next unit.

## Search Within Multiple Objects

Cloud Kicks loves its customers. It wants to build a one-stop-shop for users to ask questions and share information on its website. There are multiple types of information included: videos, articles, questions, and PDFs. But users don’t really care what type of content is presented. They only care that they get the information they need—and fast. That’s what makes the multiple object search beneficial: You get to search through multiple objects at the same time because the type of record doesn’t matter to the user. Or, perhaps the user actually wants to see multiple object types in results.

Luckily, adding another object is super simple in SOSL. Just add a comma-separated list.

```java
FIND {term} RETURNING ObjectTypeName1, ObjectTypeName2, ObjectTypeNameYouGetTheIdea
```

Copy

Going back to our scenario, a Cloud Kicks customer is wondering if any shoes are made of recycled materials. You set up the online knowledge base search so that multiple objects matching the terms are returned in the results.

```java
FIND {recycled materials} RETURNING Product2, ContentVersion, FeedItem
```

Copy

Remember, if you don’t specify an object in the RETURNING element, it doesn’t show up in the results.

## Search Within Custom Objects

Salesforce includes numerous standard objects available to customers. But Cloud Kicks is all about custom shoes, so it makes sense that it also needs custom objects. Of specific interest to you is the newest custom object, Merchandise. This object contains information about the style, ID, color, materials, name, and price of all that Cloud Kicks has to offer. Many people inside Cloud Kicks need to access this information, including support, sales, and shipping.

For the internal product website you’re building, you’re adding a search box that only searches the Merchandise custom object. There’s no fancy way to specify custom objects in a SOSL search. Include the sObject name like any other standard object, and append a __c suffix.

```java
FIND {pink hi\-top} RETURNING Merchandise__c
```


### Further Reading

[[Best Practice Queiries]]