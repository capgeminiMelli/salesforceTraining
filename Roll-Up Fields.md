## Introduction to Roll-Up Summary Fields

While formula fields calculate values using fields within a single record, roll-up summary fields calculate values from a set of related records, such as those in a related list. You can create roll-up summary fields that automatically display a value on a master record based on the values of records in a detail record. These detail records must be directly related to the master through a master-detail relationship.

You can perform different types of calculations with roll-up summary fields. You can count the number of detail records related to a master record, or calculate the sum, minimum value, or maximum value of a field in the detail records. For example, you might want:

-   A custom account field that calculates the total of all related pending opportunities.
-   A custom order field that sums the unit prices of products that contain a description you specify.


## Defining a Roll-Up Summary Field

Since roll-up summary fields are based on master-detail relationships, it’s useful to review object relationships before creating a roll-up summary field.

There are a few different types of summaries you can use.

- count
- sum
- min 
- max