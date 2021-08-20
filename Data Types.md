### List of Data Types Available for Custom Fields
```
1.) Geolocation

2.) Number

3.) Percent

4.) Phone

5.) Picklist

6.) Picklist (Multi)

7.) Text

8.) Text Area (255 characters)

9.) Text Area (Long) [131,072 characters]

10.) Text Area (Rich) 

11.) Text Encrypted

12.) Time

13.) URL

```

### Data Loss between types

![[Pasted image 20210819145909.png]]

### Dependent Fields

**Dependent picklist**: allows the values in one picklist to be filtered by the values in another picklist or checkbox field. The picklist or checkbox that drives the filtering is called the controlling field. the picklist that has its values filtered by the value selected in the controlling field is called the dependent field. 

- MULTI-SELECT CAN BE DEPENDENT BUT NOT CONTROLLING
- Standard picklist fields can be controlling but NOT BE DEPENDENT FIELDS


### Formula fields

These fields are read-only that automatically calculate a value based on the other fields or a formula

Simple formula allows selection of merge fields and operators
advanced formula allows the use of merge fields, operators, and a range of functions to define the formula. 


## Deleting Fields
Deleted custom fields count against custom field allocation within **15 days after deletion. **

Fields can be restored after 15 days of deletion. 

If a field is restored, it needs to be manually added back to the page layouts and marked as requried / unique. After a field is restored, field history is available again. 

### External Ids

There can be up to 25 external IDs on an object.

They are fields that contain a unique identifer from a system outside of salesforce. 

## Custom Objects 
Up to 200 custom objects can be created in enterprise edition and up to 2000 in unlimited and performance edition.

Relationship fields can be used to define relationships between objects . 
