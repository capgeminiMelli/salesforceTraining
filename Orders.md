# Orders
An order, whether it’s for supreme pizzas or solar panels, is a promise by a company to provide specific goods or services to a customer, at an agreed time and price. This helps with both order fulfillment and reporting on bookings—two critical responsibilities for every company. Sales Operations teams track such commitments to their customers using Order and Order Product records.


### Orders in CPQ
Salesforce CPQ makes creating quotes easy, so it’s common for sales reps to make quotes that don’t actually result in a deal. For example, the sales rep might make four different quotes for a single opportunity, and only one is approved by all parties. The other three should not be turned into orders. To make sure the right quote is used for order generation, Salesforce CPQ checks two things:

First, Salesforce CPQ only creates an order from a quote if the quote’s Primary checkbox is checked. Only one quote related to an opportunity can be flagged as Primary. Making a second quote Primary automatically unchecks the Primary checkbox of the first quote. In this way, Salesforce CPQ only generates an order from a single quote related to an opportunity.

Optionally, admins can configure Salesforce CPQ so that orders are only generated if the Status field of the primary quote is set to Approved (not Draft). This ensures that the quote completes the approval process before Sales Ops can kick off order generation. If the quote isn’t first approved and Sales Ops attempts to generate an order, they’ll get an error message.


**Click the order checkbox on a quote to automatically generate an order**

CPQ automatically transposes the QuoteLineItems into orderlineitems. 

CPQ automatically creates subscriptions on account objects 

### Multiple Orders from a single Quote
The Create Order button (on a quote object) allows you to specify things such as the start date and exactly which quote lines to include as order products. Meanwhile, Salesforce CPQ still copies over critical information, such as quantities and prices.


## Further Reading

- [[Subscriptions]]