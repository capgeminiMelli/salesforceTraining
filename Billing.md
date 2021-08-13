## Salesforce Billing
We discuss why later in this unit. But it’s important to first identify some of the higher-level benefits.

-   **Recurring Business/Recurring Revenue**. Many companies are moving to a recurring business model. This means there’s a healthy appetite to add services or subscriptions to what they offer. Think of a manufacturing company also selling warranties, or a software company offering subscriptions. Many traditional, siloed systems do not have the functionality to manage the complexities that go along with a recurring business, such as how to treat the concept of time, contract amendments, and proration. This is where Salesforce Billing shines.
-   **True Cross-Team Collaboration**. This is a little more abstract than recurring business, but bear with us. When you’re on a single platform, working off of a single toolset, you have the ability to work more closely with teams that may have been siloed in the past. Think about introducing a new product or subscription. It’s more than just adding a line item to an order. There’s a whole process from selling to billing that you have to think through and then execute. This is the promise of our platform.

Both of these concepts come into play throughout this module. So keep them top of mind

## Finance’s Seat at the Table

It’s important to understand that even though it’s used by Sales, Salesforce CPQ really is the first stop for the Finance team, which is partly why Salesforce Billing is an add-on as opposed to a stand-alone or siloed system. 

Salesforce CPQ generates the contract, where the terms and commitments influence the way you recognize revenue. (What are our obligations and did we deliver on them in time?) It’s also where the order originates, which is key to tracking bookings and generating the invoice. Ultimately, it’s important to get these right so that Salesforce Billing can take this information and continue the process in a seamless manner through invoice to accounts receivable.

First, let’s discuss the opportunities this type of platform offers.

-   True automation can be achieved, since data can easily flow through quotes, contracts, and orders into invoicing. There is no need for recalculation, no need to reconcile differences between systems, and you can be as hands-free or as hands-on as you wish.
-   The Sales-to-Finance gap is virtually eliminated. When you think about introducing a new product or business model, or changes to processes, both teams can quickly adapt since you are on the same platform working with the same toolset—closer knit by design.

**In the end, all of these features are about giving your customers flexibility to do business with you, adding to that business on their schedule, and making sure they get what they need when they need it. And you have the flexibility to meet their demands in the fastest, most seamless way possible.**

## Invoice Execution

Let’s take a look at the generation of invoices and see how this concept applies. With Salesforce Billing, there are a lot of things at your fingertips that enable you to bill customers appropriately, at the right time. Here are some of our favorites.![[Pasted image 20210806132927.png]]

![[Pasted image 20210806133125.png]]


## Billing Dates

Salesforce Billing drives the invoicing process by evaluating the order product’s Next Billing Date field and the invoice’s Target Date field. As you’ve learned, when a user, workflow, or invoice scheduler invoices an order, the invoice includes active order products with a next billing date on or before the invoice record’s target date.

Salesforce Billing uses the order product’s Charge Type, Billing Type, and Billing Frequency fields to calculate the order product’s next billing date and invoice’s target date. Admins define the time fields on the product. Quote lines inherit these field values from the product, and order products inherit the field values from the quote line. (If you update the billing type or billing frequency after invoicing, Salesforce Billing updates the order product’s next billing date and billable unit price accordingly.)

The order and order product’s Start Date fields and the order’s Billing Day of Month field are also used to calculate the next billing date of the order product.

Order Start Date Salesforce CPQ (Configure, Price, Quote) admins use CPQ package settings to control when orders start: on the day the order record is created, on the start date of the order’s parent quote, or on a date determined by an order management plug-in. Order Product Start Date

-   For one-time order products, the order product’s start date equals the order’s start date plus the difference between the quote’s start date and the quote line’s start date.
-   For recurring order products, the order product’s start date equals the quote line’s start date by default. Billing admins can change the order product’s start date to a later date.

Billing Day of Month If **Align Billing Day of Month to Order Start Date** is enabled (in Salesforce Billing package settings), then your billing day of month matches the day of your order start date by default, though sales reps can also edit it on unactivated orders. Otherwise, sales reps must set the billing day of month when they order from a quote.