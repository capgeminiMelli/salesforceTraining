## Price rules

### Overview
![Diagram of Price Rule related records](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/price-rules-in-salesforce-cpq/get-started-with-salesforce-cpq-price-rules/images/a41b4e35ad7df6eda99aac3784d9ffdc_1433528-e-70-ea-41-d-9-8-c-90-76-d-3-e-0-dcc-9-b-7.png)

At the top is the **Price Rule** record itself. It contains some basic information about how the price rule operates, but it leaves the bulk of the work to the two other records.

The **Price Condition** record is the IF portion of the if/then combo. The price condition looks at the quote and its related records to decide IF the rule needs to run. It’s like a test that can only pass or fail. If it passes, then CPQ springs into action.

The **Price Action** is the THEN portion of the if/then combo. It tells CPQ exactly which field needs to change, and how to change it.


## Details
Price rules have an evaluation scope. 
- on quote line editor load 
- on calculate (as the quote price is caluclated)
- after calculate

Evalution event
- Save
- edit

A price rule can have multiple price actions. the order of that price rule will determine which order the actions are executed. 

#### which price to use?
So far you’ve only made price rules that target List Price. It may surprise you to learn this, but we recommend that you target only one other price field: Special Price. You should leave Original Price alone so that it can act as a reference point, to compare against other prices to trigger approvals and validations, or to simply calculate margins correctly.

As for Regular Price, Customer Price, Partner Price, and Net Price, those are all prorated prices. Accounting for the prorate multiplier is problematic. The calculations quickly become complicated, and it’s very easy to introduce rounding errors. So, although it’s technically possible to target those fields, you really shouldn’t. Instead, stick to List Price and Special Price.
