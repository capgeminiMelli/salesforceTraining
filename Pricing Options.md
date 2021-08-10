## Pricing Options
In salesforce, products can be priced in a variety of ways. This is because different products can be paired, ordered, and used in multiple ways. Below is a list of all the pricing methods salesforce can use:


### Block Pricing
Block pricing envolves selling items in bulk. For example, a customer can buy 1 - 10 items for a fixed price... 10 - 20 items for a different fixed price.... etc

It is also possible to configure a block that handles over flow, for example if a user were to order 40 items. 


### Option Pricing
Option pricing allows admins to define an override price for a product when it’s sold as part of a bundle, or in some cases make the option entirely free. You’ve probably seen this strategy last time you went out for lunch. If you buy a sandwich, then soup can be added for $1.00, but if you buy soup on its own, you pay $2.25.

##### Multicurrency Limitations

Option pricing is a great way to override the price book price for options in a bundle. However, it has one significant limitation worth mentioning. **Option pricing does not support multicurrency**, so it’s only possible to define the override price in a single currency. This is fine if you only use one currency for your org, but presents a problem if you use two or more.

If you need to adjust prices of options while supporting multicurrency, you can use option discounting. Learn about option discounting in the [Discounting Tools in Salesforce CPQ](https://trailhead.salesforce.com/content/learn/modules/discounting-tools-in-salesforce-cpq) Trailhead module.


### Markup Pricing
Cost plus markup pricing is a straightforward way of giving sales reps some pricing control. Instead of a product getting priced automatically by Salesforce CPQ, a product starts with a base price (its cost) and then the sales rep adjusts that by an amount or a percent. This is similar to what happens when you buy a car—the sales rep starts with the price the dealer paid, then marks up the price for better commission.

``` The Markup Price is stored on the 'Special Price' field ``` 

### Account-Based Contract Pricing
Using a Contracted Pricing tool, administrators can create records related to the account for pricing exceptions like the toner example above. Then, whenever a sales rep adds a quote line to a quote, CPQ automatically looks to these exceptions to see if any prices should be adjusted

` Store the discounted Price in a 'Contracted Price' related object on the account object`
##### Account-wide Discount for Multiple Products

- A single Contracted Price record can apply a discount to a number of products instead of simply overriding the price for one. The trick is to create a contracted price that uses a product filter instead of specifying a single product. Also, you set a value for discount, instead of a unit price, since it’s unlikely that every miscellaneous product is the same price.

- So for example, AW Computing has many products with a product family of miscellaneous. These are things like phone chargers and USB cables. GenePoint can be given a 5% discount on all of these products by creating a single Contracted Price record that looks like this:


## Discount Schedules

Buying in bulk is a good way to save money if you’re OK with buying a lot of something at one time. Why get a single roll of paper towels when you can get 40 at a nice discount? Businesses offer these quantity-based discounts to encourage larger deals, but it can be a challenge for sales reps to keep track of how much they should discount for given quantities. Salesforce CPQ can automatically apply the right volume-based discount for each specific deal by using a tool called Discount Schedules. You can think of a discount schedule as a table of quantities and percentages.

![[Pasted image 20210805100617.png]]

In this example there is no discount for buying 29 of an item, but 30 qualify for the 10% discount, and 60 qualify for 20% off. **There is no upper bound for the 90+ range because we want to give a 30% discount for any number of units above 90, whether it’s 100 or 1,000.**

Notice that the discount schedule uses 60 for both the upper quantity of the first tier and the lower quantity of the second. This can seem odd, but it makes sure there are no gaps for fractional quantities to fall through. If the upper quantity of the first tier was 59, then 59.5 would fall through the cracks and no discount would be applied. So, with discount schedules it’s understood that the upper quantity of a tier is NOT included, which is why buying 60 units qualifies for a 20% discount.

#### Setting up Discount Schedules
- Create a `Discount Schedule` Object
- Edit the tiers on the `Discount Schedule` Object
- Edit an Individual Product Object
	- In the edit menu, look for CPQ pricing and `Discount Schedule` lookup field.


## Manual Overrides
The custom pricing method becomes available when a product is flagged as Pricing Method Editable. This allows the sales rep to manually change the customer unit price and overrides every pricing tool we’ve discussed throughout this module. It even overrides discounting methods seen in the [Discounting Tool in Salesforce CPQ](https://trailhead.salesforce.com/content/learn/modules/discounting-tools-in-salesforce-cpq) Trailhead module. As such, use caution when making pricing methods editable.


## Channel Discounts

Partners and distributors often get extra discounts when they sell products on your behalf, separate from the discounts meant for the customer. These kinds of discounts are referred to as channel discounts. Salesforce CPQ accounts for channel discounts by keeping track of them in separate quote line fields: Partner Discount and Distributor Discount.
![[Pasted image 20210805110940.png]]