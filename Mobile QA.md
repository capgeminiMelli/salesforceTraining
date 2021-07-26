# [[Quick Actions]]

## The Beauty of Quick Actions

So what are quick actions? Well, you can think of them as shortcuts. They offer a fast way for mobile users to launch a specific workflow in the Salesforce mobile app, like creating records, logging calls, or sharing files.

The Salesforce mobile app comes with some handy built-in actions, and they live in the action bar and action menu ( ![Action Menu icon](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/salesforce1_mobile_app/salesforce1_mobile_app_actions_global/images/ca24c1ccc50a6a6adaaeb0f4e24203c8_s-1-actionbar-ellipsis-icon.png)) at the top of the screen. The action bar is visible on most pages, so quick actions are just one tap away for your mobile users.

![[Pasted image 20210622155631.png]]

## The Types of Quick Actions

Now that you understand what actions are, we’re going to throw a curveball at you. There are two types of actions: global and object-specific.

**[[Object-specific actions]]** let users create or update records in the context of a particular object. In the Salesforce mobile app, object-specific actions show up on record detail pages. So for example, an action associated with the opportunity object is only available when a user is looking at an opportunity.

**[[Global actions]]** let users create records, but the new record has no relationship with other records. And they’re called _global actions_ because they can be put anywhere actions are supported—on record detail pages, but also places like the feed or Chatter groups.

Clear as mud? Don’t worry, you’ll feel more comfortable with both kinds of actions after creating a few yourself. We tackle global actions first.

## Our Use Case for Global Actions

Here’s a way to think about global actions: They’re things that users want to do quickly, but not necessarily completely. And that’s exactly how D’Angelo Cunningham will use global actions to make his brokers’ lives a little easier. Let’s look at DreamHouse Realty’s first mobile use case.

DreamHouse Realty uses the contact object to keep track of their prospective home buyers. Imagine that one of the DreamHouse brokers is out hosting an open house, and she meets a prospective buyer. She needs an efficient way to add the person as a contact without navigating to a specific page or associating the person with other information. That’s what a global action is for—quick things that users can follow up with later.



## Create an Object-Specific Action

Whew, you made it through your homework assignment. Now that all the pieces are in place, you can enjoy your reward—helping D’Angelo create an awesome object-specific action.

Here’s what we need to do. D’Angelo wants to create a New Showing quick action and make it available on the contact detail page in the Salesforce mobile app. That way, when a broker schedules a new showing, it’s automatically associated with the record for the prospective buyer. So in this step, we create an object-specific action for contacts.

1.  From the Object Manager, enter Contact in the Quick Find box, then select **Contact** .
2.  From the Contact object management settings, go to Buttons, Links, and Actions and click **New Action** .
3.  Verify that the action type is **Create a Record** .Actions can do more than just create records. To learn more about the other options, read the [Object-Specific Actions](https://help.salesforce.com/articleView?id=actions_overview_object_specific.htm&language=en_US) article in Salesforce Help.
4.  In the Target Object dropdown list, select **Event** .
5.  In the Record Type dropdown, click **Showing** .
6.  Enter New Showing in the Label field.
7.  Click **Save** .
8.  In the layout editor, remove the following fields: Related To, Assigned To, and Name.
9.  Add the Property field to the layout and make it required. You can double-click the field to edit its settings.
10.  Remove any extra spaces and arrange the fields in a single column.
11.  Click **Save** .
12.  Click **Yes** to acknowledge the warning. Even though it’s required, it’s fine to remove the Assigned To field from the layout because it defaults to the current user.![Note](https://res.cloudinary.com/hy4kyit2a/image/upload/doc/trailhead/en-usb473bb5ea1b7e61dfb07e6a7e547de6b.gif)Don’t remove a required field from the layout unless:
    
    -   The field has a default value.
    -   You specify a predefined field value for the action.
    -   The field already contains data. For example, if the action updates a record, the user entered the required information when they initially created the record.
    
      
13.  Now let’s save the brokers some time by prepopulating the Subject field. In the Predefined Values related list, click **New** .
14.  In the Field Name dropdown list, select **Subject** .
15.  In the Specify New Field Value field, enter "Showing". Be sure to put the quotation marks around the word.

### Further Readings

[[Salesforce1]]