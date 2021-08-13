## How Salesforce Organizes Your Data

Salesforce organizes your data into objects and records. Think of an object as a tab on a spreadsheet, and a record like a single row of data.
![[Pasted image 20210621130007.png]]

# Navigation

![[Pasted image 20210621130729.png]]

## Best Practices for Managing Accounts and Contacts

Establish naming conventions for accounts

If you don’t already have standards for account names, now is a great time to establish some. It’s important to consider how best to record an account’s name, and how you can use naming to denote relationships between accounts. For example, if you work with multiple franchises, you might need to use names that make sense in a hierarchy but also help you differentiate between two stores with the same name in a similar geographic area.

**Don’t allow orphan contacts**
Always associate contacts with an account. Contacts without accounts—private contacts—are like a forgotten boat adrift at sea. They’re hidden from all users except their owner and system administrators, which makes them easy to forget, hard to find, and useless to colleagues.

Audit your accounts and contacts

Use exception reporting in Salesforce to find accounts and contacts without activities in the last 30, 60, or 90 days.

Or create an “inactive” checkbox field on your account and contact objects, and use mass update to denote inactive accounts. Set up an automated process to mark accounts and contacts inactive for you, based on criteria you specify.

Handle inactive accounts and contacts

After you’ve located inactive accounts and contacts, you can handle them in many different ways. For example,

-   Organize an outreach campaign to re-engage with them.
-   Exclude them from list views, reports, automated processes, campaigns, and more so you can focus marketing, sales, and service efforts on active customers .

Maintain active ownership

It’s hard to actively manage an account if it’s assigned to someone who isn’t using Salesforce. When an employee moves to a different position or leaves your company, assign that person’s accounts and contacts to new owners.

Keep your records updated

Use features like Social Accounts, Contacts, and Leads, and Data.com to gather up-to-date information. Make it a policy that all updated data is entered into Salesforce.

[[ Organization Settings]]