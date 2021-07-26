# [[Salesforce]] Visualizations

![[Pasted image 20210621160232.png]]

## What is a report?

A report is a list of records that meet the criteria you define. It’s displayed in Salesforce in rows and columns, and can be filtered, grouped, or displayed in a graphical chart.

Every report is stored in a folder. Folders can be public, hidden, or shared, and can be set to read-only or read/write. You control who has access to the contents of the folder based on roles, permissions, public groups, and license types. You can make a folder available to your entire organization, or make it private so that only the owner has access.

# Report Formats
There are 3 formats:
[[Tabular]], [[Summary]], and [[Matrix]]
![[Pasted image 20210622165521.png]]

## What is a dashboard?


Like reports, dashboards are stored in folders, which control who has access. If you have access to a folder, you can view its dashboards. However, to view the dashboard components, you need access to the underlying reports as well. You can also follow a dashboard in Chatter to get updates about the dashboard posted to your feed.

Each dashboard has a running user, whose security settings determine which data to display in a dashboard. If the running user is a specific user, all dashboard viewers see data based on the security settings of that user—regardless of their own personal security settings. For this reason, you’ll want to choose the running user wisely, so as not to open up too much visibility. For example, set the Sales Manager as the running user for a leaderboard for her team. This allows her team members to view the leaderboard for their individual team, but not other teams.

Dynamic dashboards are dashboards for which the running user is always the logged-in user. This way, each user sees the dashboard according to his or her own access level. If you’re concerned about too much access, dynamic dashboards might be the way to go.


Create reports with [[Report Builder]]

## What is a report type?

A report type is like a template which makes reporting easier. The report type determines which fields and records are available for use when creating a report. This is based on the relationships between a primary object and its related objects. For example, with the ‘Contacts and Accounts’ report type, ‘Contacts’ is the primary object and ‘Accounts’ is the related object.

Reports display only records that meet the criteria defined in the report type. Out of the box, Salesforce provides a set of predefined standard report types. Don’t see all the fields you want? You might need to create a custom report type.

For example, an administrator can create a report type that shows only job applications that have an associated resume; applications without resumes won't show up in reports using that type. An administrator can also show records that may have related records—for example, applications with or without resumes. In this case, all applications, whether or not they have resumes, are available to reports using that type. An administrator can also add fields from a related object by creating a lookup relationship to that object, allowing for even more reporting possibilities.

**How many filter can you have on a report?**

 	Maximum Filter amount: 20 

**How many components can yo uhave on a dashboard?**

	Maxium component amount: 20
	
#filter
