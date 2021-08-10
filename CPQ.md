

## So, What Does CPQ Actually Do?

With Salesforce CPQ, you and your sales team can create quotes quickly, with minimal effort and minimal error. Here’s a little rhyme to introduce you to the wonders of CPQ:

The C is for configure. You pick out what they’ll buy.

The P is for price. We add it up, easy as pie.

The Q is for quote: A nice PDF for you.

And that’s what you get with Salesforce CPQ.

Now let’s spell it out in detail.


![An overview of the CPQ and Billing data flow.](https://resources.help.salesforce.com/images/bb04ee7d9f9922958836f4b43c4f5cf5.png)
### C Is for Configure

You start by answering a few simple questions about your customer and what they’re looking for. For example, is your customer a commercial, government, or academic institution? Based on your answer to this and other questions specific to your sales process at Infinity Solutions, you see a tailored list of products. Salesforce CPQ uses smart rules to make sure you and your reps sell related products together \[1\] and to prevent incompatible products from ending up on the same quote.

Can also create [[Product Rules]]

### P Is for Price

You have to find the right price for the products you’re selling, and Salesforce CPQ serves as the pricing source of truth. You and your reps can apply discretionary discounts \[1\] while Salesforce CPQ handles the rest, including the math \[2\]. Yes, Salesforce CPQ does all the math, automatically. You focus on your customers, not your calculator.

### Q Is for [[Quote]]

In no time, you’re ready to generate a PDF with all quote details and send it to your customer with just one click. Because you can customize the look of your company’s quotes, they appear professional, and when the whole team uses Salesforce CPQ, every quote looks consistent with the rest. The quote is dynamic too, so if your quote requires special terms, they appear automatically. Add e-signature integration, and you’ll be closing deals faster than ever.


**Note**: that you can create as many quotes as you want on a given opportunity. In fact, reps often create multiple quotes because sales is an iterative process. You might want one quote for the fully decked-out proposal and a second quote that’s more conservative. You can use quotes as a tool during negotiation because they let you present many options to your customer, all under a single opportunity.

![[Pasted image 20210622094904.png]]


### Attaches to a [[Opportunity]] in [[Salesforce]].

## When One Contract Ends, Another Begins (AKA [[Renewals]])


Consider the [[Lead-to-Cash]] Lifecycle

Salesforce CPG pricing method  for products:
- Cost Plus Markup


The price of a product on your quote can be affected by:
- Discount Schedules
- Manual Discounts by the sales rep
- Price Rules.

## How Salesforce CPQ Treats Time
Salesforce CPQ may be the only CPQ solution on the market with the concept of time built in. In the Product and Price Rules unit, you learned how our multi-dimensional quoting feature lets reps apply different quantities and discounts over time to ramp the deal. This is ideal for use cases such as subscriptions or other similar recurring sales models.

In the Advanced Approvals and Advanced Order Management unit, you learned how Salesforce CPQ allows you to split orders off of a single quote so products and services are delivered across that same time period you set up.

There's one more area where this concept of time is critical: renewal opportunities and quotes. Salesforce CPQ enables you to automate these as well. When renewals are in play, Salesforce CPQ automatically creates a renewal opportunity and quote so reps don't have to. On top of that, Salesforce sends the team a reminder when the renewal is coming up. All they have to do is jump into the new opportunity, ensure the data is correct (data is carried over from the original opportunity and quote), and then execute.


### Further Reading
- [[Orders]]
- [[Plugins]]
- [[Calculator Plugin]]