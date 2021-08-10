*When you design your product rules, consider what kind of experience your want for your sales reps. Then, get their feedback after they pilot the new rules. Being responsive to feedback leads to sales reps adopting CPQ faster, which is a great goal to aim for. - A wise man once said*

## Product Rules

CPQ product rules help ensure sales reps are putting together the right products and bundles every single time. You don’t have to worry about checking whether products and options are compatible with one another, or whether a specific SKU is appropriate for your customer’s business size and use case. We do that busy work so you can move quickly to deliver on the high expectations your customers hold for their buying experience. Increasing accuracy and customer satisfaction at the same time? That's a win-win situation if we ever saw one.


### There are four kinds of product rules: validation rules, selection rules, filter rules, and alert rules.
![[Pasted image 20210622102107.png]]


## Configuring a Product rule
When configuring a product rule, add Conditions on the rule. To do this, go to the `Error Condition` related list on the Product Rule object. 


#### Product Configuration vs Quote Line Editor

Sales reps who use CPQ to create quotes spend a lot of time on three pages.

-   Product Selection: where they choose which products to add to the quote
-   Product Configuration: where they configure bundles
-   Quote Line Editor: where they see pricing and apply discounts (among other things)

![Diagram of page flow from Product Selection to Quote Line Editor](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/product-rules-in-salesforce-cpq/decide-when-rules-evaluate/images/8275c61c3b80023f0a3f79e97cdc8236_7085-d-1-cf-2924-49-d-8-adbe-16-bbffe-7-e-044.jpeg)

A product rule can run on either the Product Configuration page or on the Quote Line Editor, but not both! It’s rare that the same business logic needs to be in both places, but if you find yourself in that situation, you have to create two separate rules.

The Scope field on the product rule record tells CPQ where the rule should run.

As you might guess, a scope of “Product” means the rule will run during product configuration, and a scope of “Quote” will make it run on the Quote Line Editor.

## Summary Variable

The product rule you want to create really just tests to see if there are no microphone-related options selected. So you need to know how many _are_ actually selected. You could use that information in the error condition, triggering the rule if the number is zero. Thankfully, CPQ has a tool for counting options based on some criteria, and that tool is called a summary variable.

The job of a summary variable is simple: Look at a set of data, and summarize it down to a single numeric value. For example, you can:

-   Count the number of all “WiFi Access Point” assets on an account.
-   Find the maximum discount percent across all lines on a quote.
-   Sum the quantity of selected options that have a product code that ends in “MIC” within a bundle.


## Limits of Testing Product Option Fields

When you create an error condition for a bundle-specific rule you can test summary variables, configuration attributes, and product option fields. For example, you could check the product option field of Quantity to see if it’s greater than 10. The way CPQ handles tests involving product option fields is to cycle through each selected option, performing every test against the option as if it were the only one that exists. This method holds within it two important caveats to remember when making bundle-specific error conditions.

First, CPQ only tests _selected_ options, ignoring anything that’s unchecked. That means it’s impossible to test for something that _isn’t_ selected. That’s why you created a summary variable in the beginning of this unit, so that you could discover if zero microphones were selected. If you didn’t have the summary variable, and you just tried to test if the Product Code field does not contain “MIC” then you would’ve got a bunch of false positives. For example, the keyboard option doesn’t contain “MIC” so the condition would be true, and the rule would fire, even if an actual microphone option was selected.

The second caveat involves testing two separate options in the same rule. For example, imagine you want to test a coffee bundle to see if both “Cream” and “Sugar” options are selected, using these conditions.

-   Product Code = Cream
-   Product Code = Sugar

Because you want both to be true, you need to use “All” for the Conditions Met field. When CPQ gets to the Cream option and performs the tests, the Sugar test will fail. It’s impossible for a single option to be both Cream and Sugar, so the rule will never run.

The workaround is to use a summary variable to count one of the options, such as Sugar. That would give you these two tests.

-   Product Code = Cream
-   Sum of Sugar Options > 0

Now when CPQ gets to the Cream option, both tests can pass, and the rule can fire.

Creating good logic for product rules is sometimes a challenge, so the most important thing you can do after creating a rule is to thoroughly test it. Try testing when you expect the rule to fire, as well as scenarios when it shouldn’t.

Now that you’ve seen how rules work in the context of bundles, in the next unit you investigate selection rules, which are used heavily (but not exclusively) in bundles as well.

## Selection Rules
What if there was a kind of rule that took action to automatically make necessary selections on product bundles to avoid configuration issues in the first place?


![[Pasted image 20210804163617.png]]

Selection rules use action records to tell CPQ how to change options during a configuration. In the previous unit, each of your rules acted on just one product. But what if you needed to perform the same action on multiple products? For example, imagine you’re a barista and you know that your customer is lactose intolerant (thanks to information on their profile). You would want to disable all dairy options in your coffee bundle so that you can’t accidentally include skim milk, 2% milk, whole milk, or cream.

As you create the selection rule you can create a separate action to disable each product. Unfortunately, later when you get a new dairy product that needs the same treatment, you have to go back to the rule and create another action. Overall, one product per action is not fun to maintain.

Thankfully there’s another option as long as you have a way of identifying which products contain dairy. For example, you can make a checkbox named Dairy__c on the product record, then check each dairy product.

Then, you would create a single action for your rule. Instead of filling in the product lookup, you’d use the fields in the Filter Information section to look for any products where Dairy__c equals true.

![Action record using filter fields](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/product-rules-in-salesforce-cpq/discover-other-ways-to-use-selection-rules/images/68aa778b2d6b1eb18b6141a7c772c18c_0-c-525-fb-2-d-950-43-e-5-ac-54-4-a-3-a-0-c-6-d-6-ec-2.png)

That’s all there is to it. No dairy products allowed, no upset tummies for your lactose intolerant customers. Later when you add another dairy option to the bundle, you just need to make sure your Dairy__c flag is properly set on the product, and the existing rule automatically disables it.

In this example your custom Dairy__c field is conveniently in the Filter Field picklist. When you create your own rules that use fields not on the picklist, you need to update the picklist to include the API name of those fields.

Finally, notice that you didn’t use the Product lookup field on the action record. If you use both lookup and filter information, only the lookup product is affected. Just leave it blank if you use a filter.


#### Further Reading
- [[Product Bundles]]