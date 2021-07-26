# Triggers and Order of Execution 

When you save a record with an insert update or upsert statment, Salesfore performs the following events in order

On the server, Salesforce:

1.  Loads the original record from the database or initializes the record for an upsert statement.
2.  Loads the new record field values from the request and overwrites the old values.
    
    If the request came from a standard UI edit page, Salesforce runs system validation to check the record for:
    
    -   Compliance with layout-specific rules
    -   Required values at the layout level and field-definition level
    -   Valid field formats
    -   Maximum field length
    
    When the request comes from other sources, such as an Apex application or a SOAP API call, Salesforce validates only the foreign keys. Before executing a trigger, Salesforce verifies that any custom foreign keys do not refer to the object itself.
    
    Salesforce runs custom validation rules if multiline items were created, such as quote line items and opportunity line items.
    
3.  Executes record-triggered flows that are configured to run before the record is saved.
4.  Executes all before triggers.
5.  Runs most system validation steps again, such as verifying that all required fields have a non-null value, and runs any custom validation rules. The only system validation that Salesforce doesn't run a second time (when the request comes from a standard UI edit page) is the enforcement of layout-specific rules.
6.  Executes duplicate rules. If the duplicate rule identifies the record as a duplicate and uses the block action, the record is not saved and no further steps, such as after triggers and workflow rules, are taken.
7.  Saves the record to the database, but doesn't commit yet.
8.  Executes all after triggers.
9.  Executes assignment rules.
10.  Executes auto-response rules.
11.  Executes workflow rules. If there are workflow field updates:
    1.  Updates the record again.
    2.  Runs system validations again. Custom validation rules, flows, duplicate rules, processes, and escalation rules are not run again.
    3.  Executes before update triggers and after update triggers, regardless of the record operation (insert or update), one more time (and only one more time)
12.  Executes escalation rules.
13.  Executes the following Salesforce Flow automations, but not in a guaranteed order.
    
    -   Processes
    -   Flows launched by processes
    -   Flows launched by workflow rules (flow trigger workflow actions pilot)
    
    When a process or flow executes a DML operation, the affected record goes through the save procedure.
    
14.  Executes entitlement rules.
15.  Executes record-triggered flows that are configured to run after the record is saved.
16.  If the record contains a roll-up summary field or is part of a cross-object workflow, performs calculations and updates the roll-up summary field in the parent record. Parent record goes through save procedure.
17.  If the parent record is updated, and a grandparent record contains a roll-up summary field or is part of a cross-object workflow, performs calculations and updates the roll-up summary field in the grandparent record. Grandparent record goes through save procedure.
18.  Executes Criteria Based Sharing evaluation.
19.  Commits all DML operations to the database.
20.  After the changes are committed to the database, executes post-commit logic such as sending email and executing enqueued asynchronous Apex jobs, including queueable jobs and future methods.