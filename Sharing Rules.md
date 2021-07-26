## Extend Access with Sharing Rules

Your org-wide default sharing settings give you a (relatively restrictive) baseline level of access for each object. If you have org-wide sharing defaults of Public Read Only or Private, you can open access back up for some users with sharing rules. This enables you to make automatic exceptions to your org-wide sharing settings for selected sets of users.

  

Sharing rules can be based on who owns the record or on the values of fields in the record. For example, use sharing rules to extend sharing access to users in public groups or roles. As with role hierarchies, sharing rules can never be stricter than your org-wide default settings. They just allow greater access for particular users.

  

Each sharing rule has three components.

**Share which records?**

You can share records owned by certain users or meeting certain criteria. Criteria-based sharing rules determine what records to share based on field values other than ownership.

## Define a Public Group

Before creating a sharing rule, it’s important to set up the appropriate public group. A public group is a collection of individual users, other groups, individual roles or territories, and/or roles or territories with their subordinates that all have a function in common. For example, users with the Recruiter profile as well as users in the SW Dev Manager role both review job applications.

Using a public group when defining a sharing rule makes the rule easier to create and, more important, easier to understand later, especially if it's one of many sharing rules that you're trying to maintain in a large organization. Create a public group if you want to define a sharing rule that encompasses more than one or two groups or roles, or any individual.

#publicGroup
## Define a Sharing Rule

You can define a sharing rule for a single public group, role, or territory. You can also define a sharing rule for a role plus its subordinates or for a territory plus its subordinates.


1.  In Setup, use the Quick Find box to find **Sharing Settings**. This is the same page used to define org-wide defaults.
2.  In the **Manage sharing settings for** drop-down list, choose the object for which to create the sharing rule. Choosing an object in this drop-down list allows you to focus in on the org-wide defaults and sharing rules for a single object at a time rather than looking at all of them in a long page—a useful thing if you've got a large org with multiple custom objects.
3.  In the Sharing Rules area, click **New** and give your rule a label. The **Rule Name** text box populates automatically when you click it.
4.  For the rule type, you can choose whether the sharing rule is based on the owner or based on criteria that records must match to be included. For this sharing rule, select **Based on record owner**.
5.  For **Select which records to be shared**, select a category from the first dropdown list, and a set of users from the second dropdown list or lookup field.
6.  For **Select users to share with**, specify the users who get access to the data.
7.  Select a sharing access setting.
8.  Click **Save**.