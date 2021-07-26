## OAuth 2.0 Protocol

OAuth 2.0 is an open protocol used to allow secure data sharing between applications. The user works in one app but sees the data from another. For example, you’re logged in to your Salesforce mobile app and see your data from your Salesforce org.

Behind the scenes, the apps perform a kind of handshake and then ask the user to authorize this data sharing. When developers want to integrate their app with Salesforce, they use OAuth APIs.

Here are a couple of examples.

-   A mobile app that pulls contacts from a Salesforce org uses OAuth.
-   A Salesforce org gets contacts from another service also uses OAuth.

The following is an example of an app asking the user for permission to access information using OAuth 2.0.

## OpenID Connect Protocol

The OpenID Connect protocol adds an authentication layer on top of OAuth 2.0 to enable secure exchange of user information. Like SAML, OpenID Connect sends identity information from one service to another. Unlike SAML, OpenID Connect is built for today’s world of social networks. Have you ever installed a new app and come across a prompt like "Log in with your Google account"? That app is using the OpenID Connect protocol. When you sign in with Google, you’re not creating an account and another password. Only Google holds that information.