## Point Users in the Right Direction

If you’ve ever been at an airport, you’ve likely seen large signposts that help you get your bearings and find your way to certain locations, like baggage claim or a specific gate number.

Well, we need visual cues to find our way in apps, too. And that’s what the mobile navigation menu is: a signpost. Your users rely on it to get from place to place in the Salesforce mobile app as efficiently as possible.

With the new mobile app, the navigation items that your users see depend on which part of the Salesforce mobile app they’re in—a Lightning app or the special Mobile Only app. And depending on which part they’re in, you can customize their navigation items in different ways.

So let’s take a look and talk about how you can customize navigation items to meet your users’ needs. Because after all, a signpost is only effective if it points people to places they actually want to go.

## The Mobile Navigation Bar and Menu

Before we jump into the customization options, let’s get familiar with the new navigation bar and the updated navigation menu.

The thumb-friendly navigation bar lives at the bottom of your screen. It puts important navigation items in easy reach while users get work done. We’ll talk more about the navigation bar soon.

Go to the navigation menu by tapping **Menu** . This is where users can access all the objects, apps, and items available to them.

**There are two navigation experiences:** one for users who’ve logged in to the new mobile app for the first time, and one for users who’ve switched to a Lightning app using the mobile App Launcher.

The first time users log in to the new Salesforce mobile app, they see the navigation menu for the Mobile Only “app.” We call it an app, but it’s basically just the default set of navigation items.

You can customize the Mobile Only navigation items in Setup.

![[Pasted image 20210622154921.png]]


## Notes About Mobile Navigation

As you customize the mobile navigation menu, here are some important things to keep in mind.

-   You can’t set different menu configurations for different types of users. But users in Lightning apps with the right permissions can change their navigation tabs on desktop, and those changes are reflected in the Lightning app’s mobile navigation menu and navigation bar.
-   Before you set up navigation items for the Mobile Only app, make sure you read about Smart Search Items. The short explanation is that Smart Search Items adds a dynamic list of recently accessed objects to the navigation menu. Anything you put below Smart Search Items appears after that list of recent items. If Smart Search Items is one of the first four items in the navigation menu, some recent items also appear in the navigation bar at the bottom of the screen.
-   If you want to include Visualforce pages, Lightning Pages, or Lightning components in the mobile navigation menu, you have to create tabs for them.
-   Before adding a page to the Salesforce mobile app, make sure the page is enabled for mobile. Thoroughly test your Visualforce pages in the Salesforce mobile app because they don’t always work the same as they do on desktop. See the resources section for more information.


## Test Your Changes in the Salesforce Mobile App

You know the drill! Let’s see how the improved Mobile Only navigation menu looks in the mobile app.

1.  Open Salesforce on your mobile device.
2.  Tap ![Navigation Menu Icon](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/salesforce1_mobile_app/salesforce1_mobile_app_navigation/images/985d9f3c6679e2f3da26116587173b70_s-1-customization-navigation-menu-icon.png) to open the navigation menu. If you’re not in the Mobile Only app, use the App Launcher to switch to it.
3.  Pull down to refresh.

All of our little adjustments are reflected in the menu. And with that final piece of customization, we’ve completed our mobile mission! D’Angelo can confidently roll out the Salesforce app to the DreamHouse brokers, and soon they’ll be enjoying all the productivity gains that mobility has to offer.

## Next Steps

Well, that’s good news for D’Angelo. But what about your org? How do you translate your newfound knowledge into action? Now that you’re comfortable with the mobile customization tools, here’s what to do next.

1.  Check out the [Salesforce Mobile App Rollout](https://trailhead.salesforce.com/trails/salesforce1_mgmt/modules/salesforce1_rollout) module. Start developing your mobile use cases and planning your mobile launch.
2.  Read about [Salesforce Mobile App Security and Compliance](https://trailhead.salesforce.com/trails/salesforce1_mgmt/modules/salesforce1_security) so you can make sure your company’s data is safe when accessed from mobile devices.
3.  Roll out the Salesforce mobile app to your users.
4.  Get your [Mobile Strategy Development](https://trailhead.salesforce.com/trails/salesforce1_mgmt/modules/mobile_strategy) badge to find out how Salesforce fits into your company’s overall mobile strategy.

That’s enough mobile goodness to keep you busy for a while. Now go forth and implement your own awesome use cases in the Salesforce mobile app. Happy customizing!

## Resources

-   Salesforce Help: [Customize the Salesforce Mobile App Navigation Menu and Navigation Bar](https://help.salesforce.com/articleView?id=salesforce_app_customize_nav_menu.htm&language=en_US)
-   Salesforce Help: [Personalize the Navigation Bar in Lightning Experience](https://help.salesforce.com/articleView?id=user_userdisplay_tabs_lex.htm&language=en_US)