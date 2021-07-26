## Create and Edit Roles

A role hierarchy works together with sharing settings to determine the levels of access users have to your Salesforce data. Users can access the data of all the users directly below them in the hierarchy.

  

Users who need to see a lot of data (such as the CEO, executives, or other management) often appear near the top of the hierarchy. But role hierarchies don't have to match your org chart. Each role in the hierarchy just represents a level of data access that a user or group of users needs.

-   A manager always has access to the same data as his or her employees, regardless of the org-wide default settings.
-   Users who tend to need access to the same types of records can be grouped together. We'll use these groups later when we talk about sharing rules.

Depending on your sharing settings, roles can control the level of visibility that users have into your Salesforce data. Users at any given role level can view, edit, and report on all data owned by or shared with users below them in the role hierarchy, unless your sharing model for an object specifies otherwise. Specifically, in the Organization-Wide Defaults related list, if the **Grant Access Using Hierarchies** option is disabled for a custom object, only the record owner and users granted access by the org-wide defaults receive access to the object's records.

Beyond setting the org-wide sharing defaults for each object, you can specify whether users have access to the data owned by or shared with their subordinates in the hierarchy. For example, the role hierarchy automatically grants record access to users above the record owner in the hierarchy. By default, the **Grant Access Using Hierarchies** option is enabled for all objects. It can only be changed for custom objects.

To control sharing access using hierarchies for any custom object, enter Sharing Settings in the Quick Find box and select **Sharing Settings**. In the Organization Wide Defaults section, click **Edit**. Deselect **Grant Access Using Hierarchies** if you want to prevent users from gaining automatic access to data owned by or shared with their subordinates in the hierarchies



# Role Solgan

Roles control what a user can see. Should be built on the principle of "who needs to see what"

