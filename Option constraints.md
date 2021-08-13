### Option Contraints

`Enable or disable a product option for selection relative to another product option.` 

You may find it useful to show a product option in your bundle but prevent your sales rep from choosing it until they’ve selected another option. This way, they don’t sell it to a customer without the original option that makes use of it. Once Salesforce CPQ enables the option for selection, your rep can choose whether to select it based on the customer’s needs. You can also disable one option from selection relative to another option. For example, sales reps could not select American power cables in a bundle as long as they’ve selected hardware that requires European power cables.

#### Review the following fields when using option constraints.

**Check Prior Purchases**
- By default, Salesforce CPQ evaluates constraining options only on the quote you’re editing. When you select this field, Salesforce CPQ also evaluates previously purchased units of the constraining option on the quote’s parent account. These units must be assets, or subscriptions in active contracts.

**Constrained Option**
- Lookup to the option that Salesforce CPQ enables or disables.

**Constraining Option**
- Lookup to the option that determines whether Salesforce CPQ enables or disables the Constrained Option.

**Configured SKU**
- (Required) SKU number of the bundle that includes this option. This field is completed automatically if you created this feature from the bundle product’s detail page.

**Option Constraint Group**
- Use this field if you have multiple constraints targeting a constrained option and want to require the selection of all their constraining options. In this case, Salesforce CPQ selects the constraining options of all constraint records where the Option Constraining Group has the same value. This feature is useful if you want to require or exclude options based on combinations of other options. The value can be any text string, but we recommend making it descriptive and easy to remember.

**Type**
- Choose the behavior for this constraint.
	-   Dependency: Selecting the **Constraining Option** causes Salesforce CPQ to enable the **Constrained Option** for selection
	-   Exclusion: Users can’t select the **Constrained Option** if they’ve selected the **Constraining Option**.