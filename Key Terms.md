## Key Terms

We've thrown many terms at you as we've described the background information you need to get started adding users. Here are some key terms you should know and their definitions.

**Usernames**

Each user has both a username and an email address. The username must be formatted like an email address and must be unique across all Salesforce organizations. It can be the user's email address, so long as it is unique.

**User Licenses**

A user license determines which features the user can access in Salesforce. For example, you can allow users access to standard Salesforce features and Chatter with the standard Salesforce license. But, if you want to grant a user access to only some features in Salesforce, you have a host of licenses to choose from. For example, if you have to grant a user access to Chatter without allowing them to see any data in Salesforce, you can give them a Chatter Free license.

**Profiles**

Profiles determine what users can do in Salesforce. They come with a set of permissions which grant access to particular objects, fields, tabs, and records. Each user can have only one profile. Select profiles based on a user’s job function (the Standard User profile is the best choice for most users). Don’t give a user a profile with more access than the user needs to do their job. You can grant access to more items the user needs with a permission set.

**Roles**

Roles determine what users can see in Salesforce based on where they are located in the role hierarchy. Users at the top of the hierarchy can see all the data owned by users below them. Users at lower levels can't see data owned by users above them, or in other branches, unless sharing rules grant them access. Roles are optional but each user can have only one.

If you have an org with many users, you may find it easier to assign roles when adding users. However, you can set up a role hierarchy and assign roles to users at any time. Roles are only available in Professional, Enterprise, Unlimited, Performance, and Developer editions of Salesforce.

**Alias**

An alias is a short name to identify the user on list pages, reports, or other places where their entire name doesn't fit. By default, the alias is the first letter of the user's first name and the first four letters of their last name.

## Levels of Data Access

You can configure access to data in Salesforce at four main levels.

**Organization**

At the highest level, you can secure access to your organization by maintaining a list of authorized users, setting password policies, and limiting login access to certain hours and certain locations.

**Objects**

Object–level security provides the simplest way to control which users have access to which data. By setting permissions on a particular type of object, you can prevent a group of users from creating, viewing, editing, or deleting any records of that object. For example, you can use object permissions to ensure that interviewers can view positions and job applications but not edit or delete them.

**Fields**

You can use field–level security to restrict access to certain fields, even for objects a user has access to. For example, you can make the salary field in a position object invisible to interviewers but visible to hiring managers and recruiters.

**Records**

To control data with greater precision, you can allow particular users to view an object, but then restrict the individual object records they're allowed to see. For example, record–level access allows interviewers to see and edit their own reviews, without exposing the reviews of other interviewers. You can manage record–level access in the following ways.

-   **Organization–wide defaults** specify the default level of access users have to each others' records. You use organization–wide sharing settings to lock down your data to the most restrictive level, and then use the other sharing tools to selectively give access to other users. For example, you can give all employees access to an object called Candidate to allow anyone to add a candidate to the database. But you can restrict access to Positions so that anyone can see the jobs available but only the employees with the proper permissions can edit them.
-   **Role hierarchies** open up access to those higher in the hierarchy so they inherit access to all records owned by users below them in the hierarchy. Role hierarchies don't have to match your organization chart exactly. Instead, each role in the hierarchy represents a level of data access that a user or group of users needs. For example, you can restrict access to Candidates by setting the organization–wide default to Private, but allow recruiters to view and edit the candidate records that they own. Recruiters can't see candidate records they don't own because recruiters are all at the same level in the role hierarchy. However, hiring managers can be given read/write access to all candidate records because they are at a higher level in the role hierarchy than recruiters.
-   **Sharing rules** enable you to make automatic exceptions to organization–wide defaults for particular groups of users, to give them access to records they don't own or can't normally see. Sharing rules, like role hierarchies, are only used to give more users access to records—they can't be stricter than your organization–wide default settings. For example, you can allow all employees to view Positions, but use sharing rules to grant full editing access to employees in a role or group called Hiring Managers.
-   **Manual sharing** allows owners of particular records to share them with other users. Although manual sharing isn't automated like organization–wide sharing settings, role hierarchies, or sharing rules, it can be useful in some situations, for example, if a recruiter going on vacation needs to temporarily assign ownership of a job application to another employee.