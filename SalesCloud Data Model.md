## What’s a Data Model?

All your sales data needs a home in Sales Cloud. A data model determines how the info you track relates to individual users and your business. It also defines the relationships between different sets of data.

We know that looking at all your data at once can seem overwhelming. That’s why it’s important to organize how you collect, categorize, store, and display that data. Having a set structure for your data makes it easier to understand, present to your teams, and act on.

That’s the basic idea behind data modeling. **In Sales Cloud, your data models rely on two essential elements: objects and fields. These objects and fields store and organize data**.

## 

What’s a Standard Object?

An object is a home for your data. Think of an object as a form you’d use to collect and store crucial info on a specific topic that is relevant and actionable for your business. Standard objects are a set of objects that come already set up for you in Sales Cloud. (We talk more about a few of these objects are in the next unit.) 

One of the many magical aspects of Sales Cloud is how different sets of data can connect to each other through [object relationships](https://trailhead.salesforce.com/en/content/learn/modules/data_modeling/object_relationships). This means you can, for instance, take a customer’s contact info and connect it to all the deals you’ve closed with them.



### [What’s a Standard Field?](https://trailhead.salesforce.com/content/learn/modules/sales-cloud-configuration-basics/topic-title)

Objects are made up of fields. Fields are essential for your objects to do their job. If you think of the object as a form, fields are the specific information that must be filled in on that form (for example, First Name). Standard fields are a set of fields that come already set up for you in Sales Cloud.

Having a field for each piece of data your objects contain allows your sales teams to have a consistent, clear experience every time they add new info. For instance, if they want to create a new contact, they’ll have data for the same fields as all existing contacts (for example, Name, Phone Number, Company).

## Standard Objects in Sales Cloud

Let’s take a look at four essential objects in Sales Cloud that help sales users keep track of the information they need to maintain business relationships and close deals: Leads, Accounts, Contacts and Opportunities. 

As you set up the fields for your objects, you determine the information that will be collected each time a sales rep logs a new **record** related to an object. (For instance, when they identify a new lead.)

**Leads** represent potential sales opportunities or new customers. They can come from a wide range of sources—the web, a list of conference attendees, the business cards your team accumulates, research, and so forth. Leads contain the basic customer contact info your team needs to follow up. Your team determines at what point a lead is qualified and ready to be converted into an active deal.

**Accounts** represent the companies you do business with. They’re the heart of your business data. They’ll be at the center of your object relationships as you do more business with a customer over time.

**Contacts** represent the people your team keeps in touch with. They’re the names and faces of your business relationships. Contacts can come from Leads or other sources, and they’re a great way to track individualized info that helps your business relationships flourish.

**Opportunities** represent the qualified deals your sales team is working on. They help you track key info, like the deal amount and the expected close date. As your deals move along in your sales process, Opportunities help you see exactly what stage your deals are in, allowing you to have real-time insights into your team’s progress.

*In Salesforce, we think about database tables as **objects**, we think about columns as **fields**, and rows as **records**. So instead of an account spreadsheet or table, we have an Account object with fields and a bunch of identically structured records.*


## Get to Know Objects

Salesforce supports several different types of objects. There are standard objects, custom objects, external objects, platform events, and BigObjects. In this module, we focus on the two most common types of objects: standard and custom.

**Standard objects** are objects that are included with Salesforce. Common business objects like Account, Contact, Lead, and Opportunity are all standard objects.

**Custom objects** are objects that you create to store information that’s specific to your company or industry. For DreamHouse, D’Angelo wants to build a custom Property object that stores information about the homes his company is selling.

Objects are containers for your information, but they also give you special functionality. For example, when you create a custom object, the platform automatically builds things like the page layout for the user interface.