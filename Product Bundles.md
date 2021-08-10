*Options are the glue that holds together the lead product with all of the followers, like the laser printer and its accessories.*

## Bundles of All Shapes and Sizes

Creating a quote means choosing products, and some products must be sold with other products. This fact brings us to a central concept in Salesforce CPQ: the bundle. A bundle is simply a group of products we know should be sold together. When the sales rep chooses to sell the bundle, all the related products come along for the ride. There are three types of bundles. We use a food analogy to describe each type.

-   **Static bundle**: These bundles always have the same products together, in the same quantities, with no changes allowed. Imagine a BLT sandwich. We always need bacon, lettuce, tomato, and two slices of toast. Otherwise, it’s not a BLT anymore!
-   **Configurable bundle**: This bundle can be customized to your liking, with some limits to prevent impossible configurations. It’s like a build-your-own burrito. You choose the type of beans you want, the heat of the salsa, and if you want sour cream or not. Each customer gets a burrito with just the right fillings, which are probably different from the fillings chosen by the next customer.
-   **Nested bundle**: This is a bundle inside another bundle. You might have a configurable hamburger bundle nested inside a combo meal bundle. In Salesforce CPQ, you can nest bundles as much as you want, but we recommend only going one or two levels deep.


## Multiple Bundles

Sometimes a sales rep chooses two bundles from the product selection page, and both bundles need to be configured. When this happens, the configuration page shows an expandable bar on the left. When expanded, the panel displays a list of configurable bundles. By default, clicking a bundle from the sidebar shows just that one bundle.

![Configure Products page](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/cpq-product-configuration/control-the-configuration-experience/images/ebf61552c51596213c492d178ce664e9_cjju-7-m-3-tw-00020-ua-59857-zsb-1.png)

However, you can see all bundles at once by changing the Multiple Bundles View package level setting to Classic. With this mode, the sidebar acts more like a bookmark bar, scrolling the page to the selected bundle. Find package level settings in Setup by entering Installed Packages in the Quick Find box, then click **Installed Packages**. Next to Salesforce CPQ, click **Configure**.

## Visualize Product Hierarchy

To make bundles easier to distinguish in the Quote Line Editor, set the Visualize Product Hierarchy package level setting to True. This setting indents product names in quote lines that represent options, so that you can easily see that they’re related to the lead product. If you signed up for the special Developer Edition org with Salesforce CPQ, you can see this setting in action.

![Quote Line Editor page](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/cpq-product-configuration/control-the-configuration-experience/images/10fd2f6ef186db0bb102e4e83f5ea115_screen-shot-2019-01-30-at-6-08-37-pm.png)

If you don’t want product names to be indented, just uncheck that setting. The quote lines for the options still have an icon next to them, and hovering over the icon tells you which quote line is the lead product.


#### How to make product bundles?
Simply add 'options' to an existing product


## Option Type

When you build a bundle, one of the most important things to decide is how to handle option quantity while on the Quote Line Editor. Sales reps can typically change quantity on the Quote Line Editor, but if you’re trying to control quantities within the bundle you may not want them to make changes. The Option Type field on the option tells Salesforce CPQ exactly what to do with quantity.

In the table, you can see that even though the quantity of the option is always 2, and the quantity of the bundle is always 3, the quantity of the quote line behaves differently for every Option Type.



## Configured Code

#### Introduction

Sometimes bundles have special product codes that represent how they’ve been configured. For example, you can give a special code, LAP-P28-R16-H512, to a laptop with a 2.8GHz processor, 16GB RAM, and 512GB hard drive, so that other teams in your business, like order fulfillment, can get configuration information at a glance. Since CPQ knows how the laptop is configured, it can use that information to generate the special code automatically and put it into an out-of-the-box quote line field, Package Product Code.

#### Creating a Configured Code

How does CPQ know to use “-P28” when a rep selects the 2.8GHz processor, and how does it know to put it after “LAP” in the code? Three fields work together to construct the Package Product Code.