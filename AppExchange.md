[[Salesforce]]

## What Is AppExchange?

You’re probably comfortable with the idea of app stores. Whether you’re downloading apps on your phone, tablet, computer, or other device, you have to download and install apps to make the most of your technology.

Salesforce is the same way. Earlier, we mentioned the enterprise ecosystem. Salesforce has a community of partners that use the flexibility of the Salesforce platform to build amazing apps and other solutions that anyone can use. These offerings are available (some for free, some at a cost) for installation on AppExchange.


When building [[Report Builder]] a common strategy is to clone an existing report and modify it to meet your needs. 


## Install Your First App

While AppExchange resembles a traditional app store like you can find on your phone or tablet, it’s important to remember that your Salesforce org is a complicated environment. You can’t just install an app because it has a cool logo or a convincing catchphrase.

So what’s the right way to install an app? We’ll show you!

Let’s say you find this great app on [AppExchange](https://appexchange.salesforce.com/) that gives you a fancy set of dashboards for your org.

To install the app, click **Get It Now**. This button takes you to the installation wizard that guides you through the steps. Here are two key questions you need to answer during the installation process:

-   Where do I install the app, production or sandbox? In general, it’s a best practice to first install apps in a nonproduction environment like a sandbox or Developer Edition org. Testing the app first helps you avoid conflicts in production with things like object names.
-   Should I give app permissions to admins only, all users, or specific profiles? That depends on who the app is for. If you want to limit access to a particular set of users, plan to modify those user profiles before you install the app

## Where’d My App Go?

Congratulations! You’ve installed your first app. Now, if only you could find it…

Apps are installed using something called a package. To find the package:

1.  From Setup, search and select Installed Packages in the Quick Find box.
2.  Click the name of the package you installed. It will be the same name from the AppExchange download page.
3.  Click **View Components** to see more information about the package. The Package Details page shows you all the components, including custom fields, custom objects, and Apex classes in the package. This information helps you determine whether you have any conflicts in your own customizations.


## Develop an AppExchange Strategy

We admit that strategizing doesn’t sound heroic. But a little thinking up front goes a long way toward finding a listing that makes you and your users happy. To develop an AppExchange strategy, ask yourself these questions.

-   **Solution type**—Are you looking for something that plugs into Salesforce without much fuss? If yes, a solution, such as a Lightning component, is probably your best bet. Or do you want help building a custom solution for a complex business problem? In that case, a consultant is the better fit.
-   **Functionality**—What does the solution need to do? Which of these features are must-haves and which are nice-to-haves?
-   **Budget**—Are you open to paying for the right solution, or does it need to be free? For paid listings, what is your preferred pricing model? AppExchange supports both one-time payments and subscriptions.
-   **Stakeholder needs**—Who is using the solution? Make sure that you meet with these stakeholders to understand their needs, expectations, and timelines.
-   **Testing**—Do you have somewhere you can test everything first? Before installing a solution in a production org, we always recommend testing in a Developer Edition org or a sandbox.
-   **Technical considerations**—Does the solution need to be compatible with a specific Salesforce edition or feature? What about Lightning Experience or the Salesforce app? Think about what’s unique to your org, and take note of those items.