```java
private | public | global 
[virtual | abstract | with sharing | without sharing] 
class ClassName [implements InterfaceNameList] [extends ClassName] 
{ 
	// The body of the class 
}
```

#### List

A list in an ordered collection of elements that works much the same as a traditional array. In fact, arrays in Apex are synonymous with lists, and you can use them interchangeably. For example, the following is one way to declare a variable as a list of strings.
	`List<String> myStrings = new List<String>();`
	

```java
List<String> myStrings = new List<String>();
myStrings.add('String1');
myStrings.add('String2');
myStrings.add('String3'); 
```

You’ll probably create a lot of list variables in your Apex development, because the output of every SOQL query is a list. For example, you could create a list of Accounts using code such as the following:

```java
List<Account> myAccounts = [SELECT Id, Name FROM Account];
```

#### Map

A map is a collection of key-value pairs. Each key maps to a single value. A map is useful when you need to quickly find something by a key. The key values must be unique, so you could have a map that contained ID values for the key and then mapped to an sObject. For example, you could use the following code to declare a map variable named accountMap that contains all Accounts mapped to their IDs.

```java
Map<Id, Account> accountMap = new Map<Id, Account>([SELECT Id, Name FROM Account]);
```

You could then access a specific Account record using the get method and code similar to the following.

```java
Id accId = '001d000000BOaHSAA1';
Account account = accountMap.get(accId);
```

Check out the [official docs](https://developer.salesforce.com/docs/atlas.en-us.198.0.apexcode.meta/apexcode/langCon_apex_data_types.htm) to learn more about the data types that Apex supports.