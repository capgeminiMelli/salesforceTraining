# Empower Your Users with Quick Actions

## Learning Objectives

After completing this unit, you’ll be able to:

-   Describe how actions help your users.
-   Describe the difference between object-specific and global actions.
-   Create an action and add it to a page layout.

## Quick Actions

You know the saying that you should judge someone only by their actions? That’s true in Salesforce, and your users will judge you favorably when you give them access to awesome customized actions.

Actions let your users quickly do tasks, such as create records, log calls, send emails, and more. With custom actions, you can make your users’ navigation and workflow as smooth as possible by giving them quick access to information that’s most important.



## Object Specific Quick Action
- Automatically associated with related records
- Can be found on the record detail page of a specific object
- Create Actions, Log a call, update actions, custom Actions.
- 


## Global Quick Actions
- Global actions are actions that can be added to any page that supports actions.
	-	Record Creation (Creation of object records)
	-	Object relationship (THis is no automatic relationship between the record and any other record)
	-	available from the home page, chatter, object pages, and lightning app pages
	-	global actions are defined in setup > Global Actions
	-	Create a record, send email, log a call, custom visualforce, custom canvas, and custom ligntning component. 


## Add an Object-Specific Action to a [[Page Layouts]]

To make the New Energy Audit action available to users from an account record, Maria must add the action to the Account page layout.

1.  Click **Page Layouts**.
2.  Click **Account Layout**.  
    There are two actions sections on a page layout. The Quick Actions in the Salesforce Classic Publisher section controls which actions appear on record pages in the Salesforce Classic UI. The Salesforce Mobile and Lightning Experience Actions section controls which actions appear on record pages in both Lightning Experience and in the Salesforce mobile app. If you don’t customize the action sections of a page layout, then the actions you see in the Salesforce app and Lightning Experience come from a set of default actions defined by Salesforce.
3.  In the Salesforce Mobile and Lightning Experience Actions section, click ![override global publisher layout](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/lex_customization/lex_customization_actions/images/e24246df40ee696c414ba97cd94248ab_quick-actions-wrench-2.png) to override the defaults.  
    The actions you see when you override the defaults are a combination of the default actions for the object, plus any custom and standard buttons on the page layout. When the Salesforce Mobile and Lightning Experience Actions section isn’t customized, the Lightning page for the object takes the custom and standard buttons from their respective button sections on the layout to display on the page. However, once you override the defaults, any standard and custom buttons you want to appear on your Lightning page must be included in the Salesforce Mobile and Lightning Experience Actions section as actions.
4.  Select **Mobile & Lightning Actions** in the palette and then drag the **New Energy Audit** action to the Salesforce Mobile and Lightning Experience Actions section.


## Create a Global Action

The Sales team has asked Maria to create an action that lets users create a campaign no matter where they are in Salesforce. A global action is an ideal way to do this, because the global actions menu appears at the top of every page.

Creating a global action looks a lot like creating an object-specific action except you start on a different page in Setup.

1.  From Setup, click the **Home** tab.
2.  Enter `Global Actions` in the Quick Find box and click **Global Actions**.
3.  Click **New Action**.
4.  Select **Create a Record** for the action type.
5.  Select **Campaign** for the target object.
6.  Enter `New Campaign` as the label for the action.


## Add a Global Action to the Global Actions Menu

As we mentioned earlier in the unit, global actions live on a special layout of their own, known as the global publisher layout. The global publisher layout populates the global actions menu.

Adding an action to the global actions menu is a lot like adding an action to a record page. You simply drag an action from the palette onto the global publisher layout.

1.  You’re already in the right place in Setup, so click **Publisher Layouts**.
2.  Click **Edit** next to Global Layout.
3.  If the Salesforce Mobile and Lightning Experience Actions section isn’t customized, click ![override global publisher layout](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/lex_customization/lex_customization_actions/images/e24246df40ee696c414ba97cd94248ab_quick-actions-wrench-2.png) to override it.
4.  Click the **Mobile & Lightning Actions** category in the palette.
5.  Drag **New Campaign** from the palette into the Salesforce Mobile and Lightning Experience Actions section and save the layout.
6.  Refresh the browser, then click ![global actions menu icon](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/lex_customization/lex_customization_actions/images/fc45affa42c191a1af96f3be425ba7e6_lex-global-actions-menu-icon-2.png) to check out the global actions menu