## What Does Salesforce Identity Do?

Salesforce Identity lets you give the right people the right access to the right resources at the right time. You control who can access your orgs and who can use apps running on the Salesforce Platform, on-premises, in other clouds, and on mobile devices.

You can probably see how controlling access helps you improve your org’s security. But did you know that you can increase security while also making it easier for your users to get to the apps and services they need to do their jobs? Well, you totally can!

When users can sign in once to access all the apps that they need, everyone benefits.

-   Users don’t have to remember lots of usernames and passwords.
-   Admins spend less time dealing with user login woes.
-   Developers build web and mobile applications that work seamlessly with existing business processes.
-   CIOs strengthen security and trust while harnessing their authentication investment.
-   Customers collaborate and get their questions answered without hassle.
-   Partners integrate their solutions with your Salesforce org, making it a big win for everyone.

With Salesforce Identity, you log in once to access many connected apps.

![Salesforce and Other Connected Apps](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/identity_basics/identity_basics_product/images/35081230882b3f8fe464c26ca0c572ab_identity-overview.png)

## What Does “Identity” Mean Anyway?

In the tech industry, identity is a loaded term and has different meanings depending on the context. But generally, identity has come to mean that identity providers ensure that people are who they say they are.

At Salesforce, we’re talking about digital information about users, like who the user is and what the user can do in a particular context. It can also include attributes about the user, such as first and last names, contact information, maybe even a job title.

## What Features Does Salesforce Identity Provide?

Identity management is a huge administrative area, and Salesforce Identity offers features to address many aspects of it. A well-designed Salesforce Identity implementation begins with determining which features are right for your org and prioritizing them. Start out by introducing one or two features. Then add more features over time.

Check out this list of the main features of Salesforce Identity. Then scroll down to learn about each one in more detail.

-   Single sign-on
-   Connected apps
-   Social sign-on
-   Multi-factor authentication
-   My Domain
-   Centralized user account management
-   User provisioning
-   Identity Connect
-   App Launcher


## Multi-Factor Authentication

Sound like a mathematical equation? Nope. It’s not. Multi-factor authentication (MFA) is just a Salesforce Identity feature that we highly recommend that you implement. By configuring a couple of settings, you can make your org login process, you got it, _multiple times_ more secure.

Until now, we’ve been talking about features that make it easier for your users to access the orgs and apps they need to do their jobs. Initially, multi-factor authentication makes access a little more difficult, but this simple yet powerful tool strengthens user account security.

When you enable multi-factor authentication, users have to provide two or more pieces of evidence—or factors—when they log in. One factor is the user’s username and password combination. The requirement for additional factors is satisfied through the use of a verification method that the user has in their possession, such as an authenticator app or a Universal Second Factor (U2F) security key. 

With the newest version of the Salesforce Authenticator app, the second factor can be a response to a push notification on the user’s mobile device.

Multi-factor authentication helps ensure that even if an attacker acquires a user’s password, the attacker can’t log in and do harm. So while you’re expanding your authentication options with other Salesforce Identity features, be sure to secure individual access to your org with multi-factor authentication.

You learn how to set up multi-factor authentication in a later module. It’s simple, we promise.


## Single Sign-On

[[ Single Sign-On ]]
With a My Domain login URL, you make it easy for employees to log in to your Salesforce org with a secure, easy-to-remember URL. 

Do you want to make it even easier so that they don’t have to log in at all? Then set up single sign-on (SSO).

 
SSO has lots of advantages.

-   You spend less time managing passwords.
-   Your employees save time when they don’t have to manually log in to Salesforce. Did you know that users take 5–20 seconds to log in to an online application? Those seconds add up.
-   More people use Salesforce. Users can send out links to Salesforce records and reports, and their recipients can open them in a single click.
-   You can manage access to sensitive information from one place.

In this unit, we show you how to set up _inbound_ SSO—users log in somewhere else, like an on-premises app, and then access Salesforce without logging in. You can also set up outbound SSO in which users log in to Salesforce and then access other services without logging in again. We’ll save that topic for another module.


## [[ Identity Connect ]]

Salesforce Identity Connect synchronizes users and their attributes from Active Directory (AD) to Salesforce. When a user is created in AD, that same user account can also be created automatically in Salesforce. When a user is deleted from AD, the user account in Salesforce is deactivated at the same time.

With Identity Connect, you can let users sign in to Salesforce using their AD username and password. In some circumstances, you can configure Identity Connect to automatically sign users in to Salesforce. Yup—users can click a bookmark or link to Salesforce and they’re authenticated and taken to Salesforce without even seeing a login page. Users _love_ this!

A future module helps you decide whether Identity Connect is right for you.


## A Fully Integrated Solution

Let’s look at Salesforce Identity features again and see how they fit together.

Remember that diagram of a Salesforce org at the beginning of this unit? Let’s take another look at it. But this time, we’ll add a few more details. This diagram shows where all your identity information is stored in the “back office” of your Salesforce org. With a centralized identity management system, you go to one place to configure identities.

![Salesforce Identity features diagram](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/identity_basics/identity_basics_product/images/42d22912b199b62f3393101d15ff9c73_identity-highlevel-pieces.png)

Users can go from their desktop to mobile with the same login credentials. Their identity is safely shared across many places. Admins can keep user information secure, up to date, and in one place. You can see how powerful Salesforce Identity is when several features are combined.


[[Password Policy]]

# Futher Reading

### Security protocols
[[ SAML ]]

[[ OAuth 2.0 ]]

