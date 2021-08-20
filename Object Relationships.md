## Learning Objectives

After completing this unit, you’ll be able to:

-   Define the different types of object relationships and their typical use cases.
-   Create or modify a lookup relationship.
-   Create or modify a master-detail relationship.

## What Are Object Relationships?

Now that we’re comfortable with objects and fields, it’s time to take things to the next level with object relationships. Object relationships are a special field type that connects two objects together.

Let’s think about a standard object like Account. If a sales rep opens an account, they’ve probably been talking to a few people at that account’s company. They’ve probably made contacts like executives or IT managers and stored those contacts’ information in Salesforce.

It makes sense, then, that there should be a relationship between the Account object and the Contact object. And there is!

When you look at an account record in Salesforce, you can see that there’s a section for contacts on the Related tab. You can also see that there’s a button that lets you quickly add a contact to an account.

## The Wide World of Object Relationships

There are two main types of object relationships: lookup and master-detail.

**Lookup Relationships**

In our Account to Contact example above, the relationship between the two objects is a **lookup relationship**. A lookup relationship essentially links two objects together so that you can “look up” one object from the related items on another object.

Lookup relationships can be one-to-one or one-to-many. The Account to Contact relationship is one-to-many because a single account can have many related contacts. For our DreamHouse scenario, you could create a one-to-one relationship between the Property object and a Home Seller object.

Can be one-to-one, one-to-many, self, external, indirect, or hierarchial

**Master-Detail Relationships**

While lookup relationships are fairly casual, **master-detail relationships** are a bit tighter. In this type of relationship, one object is the master and another is the detail. The master object controls certain behaviors of the detail object, like who can view the detail’s data.

Can be one-to-one, one-to-many ,or many-to-many

**Standard Objects must be the parent, if related to custom objects. **

## Create a **Lookup Relationship**

We’re going to create two custom relationship fields on the Favorite object. First, let’s create a lookup relationship that lists the users who select **Favorite** for a property.

1.  From Setup, go to **Object Manager** | **Favorite**.
2.  On the sidebar, click **Fields & Relationships**.
3.  Click **New**.
4.  Choose **Lookup Relationship** and click **Next**.
5.  For Related To, choose **Contact**. For the purposes of DreamHouse, contacts represent potential home buyers.
6.  Click **Next**.
7.  For Field Name, enter Contact, then click **Next**.
8.  Click **Next**, **Next**, and **Save**.

## Create a Master-Detail Relationship

Now, we’re going to create a second relationship field. We want a master-detail relationship where Property is the master and Favorite is the detail.

1.  On the Object Manager page for the custom object, click **Fields & Relationships**.
2.  Click **New**.
3.  Select **Master-Detail Relationship** and click **Next**.
4.  For Related To, choose **Property**.
5.  Click **Next**.
6.  For Field Name, enter `Property` and click **Next**.
7.  Click **Next**, **Next**, and **Save**.

Now, if you look at a Property record, you’ll see Favorites listed in the related tab.


![[Pasted image 20210622151838.png]]

