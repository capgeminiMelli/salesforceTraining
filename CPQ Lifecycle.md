

## [[Quote]]

Create a quote, Configure a pricebook, and select products to put on the quote. 

Individual quoted products are saved as *quote Lines* they are saved in a master detail relationship. 

#### Key Attributes on Product Objects
- **Non-discountable** (checkbox): this checkbox determines if a discount can be added to the selected product. 
- **SortOrder** (number): sort order will determine where the productline will appear in the quote. 
- For more info about CPQ product objects check out [this article](https://help.salesforce.com/articleView?id=sf.cpq_product_fields.htm&type=5)

#### Product Options
- pretty much sets the access level of a product. With product options, you can specify whether or not the quantity of the product is edittable or if the product is required along with the order. 
- can specify the type of product the item is:
	- Component: component is required item for a product (like a processor for a laptop)
	- Accessory: 
	- Related Product: freely edit the quantity of the object in the product bundle. 
## [[Subscription]]

- Subscription Pricing (Picklist): 
	- None, Fixed Price, Percent of total.
- Subscription Term: how long the contract is in months. 

## Custom Actions
Custom actions are of three types: Seperator, buttons, menus.

Seperators: space between actions
Buttons: a button a user can click
Menus: buttons within buttons. 

Custom Actions are objects within salesforce. 
