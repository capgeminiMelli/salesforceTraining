## SAML Protocol

When you want users to move seamlessly between Salesforce orgs and applications without logging in repeatedly, you set up single sign-on (SSO). Security Assertion Markup Language (SAML) is the protocol that makes it happen.

Here are a couple of examples of SAML in action.

-   When you’re logged in to Salesforce and then click the App Launcher to get directly to your Gmail inbox, that’s SAML in action.
-   When users who are already logged in to another app can access their Salesforce org without logging in again, that’s also SAML in action.

## SAML Assertion

This is how SAML works. A user tries to access a service. The service provider sends out a request to the identity provider basically asking, “Hey, is it okay if this user accesses my service?” The identity provider makes sure that users are who they say they are by checking its database and then returning a response—an assertion—saying, “Yes, this user is authorized, and here’s some information about the user.”

Wait a minute. What’s the difference between an identity provider and a service provider? Basically, the identity provider is the one authenticating the user. The service provider is asking for the authenticated identity. We’ll talk more about identity and service providers later on in this unit.

The assertion is the information being sent. An assertion can carry detailed information about a user. It can also contain attributes about the user, like first and last names, contact information, maybe even the job title.

SAML happens in the background. Your users don’t see any of it. They just click an icon or link and open another app without having to provide additional information or log in again. Sometimes their destination already knows something about them (those user attributes) when they get there.

## SAML and XML

SAML is an XML-based protocol, which means that the packages of information being exchanged are written in XML. XML is supposed to be (almost) human-readable so that you can get some idea of what’s going on. That’s good news when you’re trying to figure out if things are working correctly.

The following diagram illustrates a portion of a SAML assertion. Does it look like gibberish? Look again and you can see that it doesn’t look all that bad. It contains information about a user’s username, phone number, and first name.

![SAML assertion](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/identity_basics/identity_basics_protocols/images/b179ddd084041a9ade955f6adfd2954e_identity-saml-assertion.png)

In this example, the Salesforce org passes the user’s information to another application. The application can use that information to authorize the user and personalize the user’s experience. But most importantly, the user doesn’t have to sign in again to access the application.