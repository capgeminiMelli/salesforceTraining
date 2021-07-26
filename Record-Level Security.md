## Record-Level Security

To control data access precisely, you can allow particular users to view specific fields in a specific object, but then restrict the individual records they're allowed to see.

Record access determines which individual records users can view and edit in each object they have access to in their profile. First ask yourself these questions:

-   Should your users have open access to every record, or just a subset?
-   If it’s a subset, what rules should determine whether the user can access them?

Let’s say you create a new profile called Recruiter to give recruiters the object-level permissions they need. You restrict the power to delete recruiting-related objects, so recruiters will never be able to delete these objects. However, granting recruiters permission to create, read, or edit recruiting objects does not necessarily mean recruiters can read or edit every record in the recruiting object. This is a consequence of two important concepts:

-   The permissions on a record are always evaluated according to a combination of object-level, field-level, and record-level permissions.
-   When object-level permissions conflict with record-level permissions, the most restrictive settings win.

That means even if you grant a profile create, read, and edit permissions on the recruiting objects, if the record-level permissions for an individual recruiting record are more restrictive, those are the rules that define what a recruiter can access.

  

You control record-level access in four ways. They’re listed in order of increasing access. You use org-wide defaults to lock down your data to the most restrictive level, and then use the other record-level security tools to grant access to selected users, as required.

-   **Org-wide defaults** specify the default level of access users have to each other’s records.
-   **Role hierarchies** ensure managers have access to the same records as their subordinates. Each role in the hierarchy represents a level of data access that a user or group of users needs.
-   **Sharing rules** are automatic exceptions to org-wide defaults for particular groups of users, to give them access to records they don’t own or can’t normally see.
-   **Manual sharing** lets record owners give read and edit permissions to users who might not have access to the record any other way.


![[Pasted image 20210623094453.png]]


## Set Your Org-Wide Sharing Defaults
Use org-wide defaults to specify the baseline level of access that the most restricted user should have.

1.  In Setup, use the Quick Find box to find **Sharing Settings**.
2.  Click **Edit** in the Organization-Wide Defaults area.
3.  1.  For each object, select the default access you want to give everyone.
2.  To disable automatic access using your hierarchies, deselect **Grant Access Using Hierarchies** for any custom object that does not have a default access of Controlled by Parent.

By default, a role hierarchy automatically grants access to records for users above the record owner in the hierarchy. Setting an object to **Private** makes those records visible _only_ to record owners and those above them in the role hierarchy. Use the **Grant Access Using Hierarchies**checkbox to disable access to records to users above the record owner in the hierarchy for custom objects. If you deselect this checkbox for a custom object, only the record owner and users granted access by the org-wide defaults receive access to the records.

Even if **Grant Access Using Hierarchies** is deselected, some users—such as those with the “View All” and “Modify All” object permissions and the “View All Data” and “Modify All Data” system permissions—can still access records they don’t own.