## Configure Inbound SSO with a Third-Party Identity Provider

Let’s start configuring inbound SSO with a third-party identity provider.

The head of your IT department, Sean Sollo, tells you to set up Salesforce users with SSO so that they can log in to your Salesforce org with their Jedeye network credentials. Here, we walk you through the steps to set up SSO for Jedeye Tech’s new employee, Sia Thripio. You’ll set up inbound SSO using the [Axiom Heroku web app](http://axiomsso.herokuapp.com/Home.action) as the identity provider.

Is this starting to sound difficult? It’s not, really. Let’s break it down into simple steps.

1.  Create a Federation ID for each user.
2.  Set up SSO settings in Salesforce.
3.  Set up Salesforce settings in the SSO provider.
4.  Make sure it all works.

Remember what the prerequisite is for SSO? That’s right, a My Domain. Because you’ve already completed the unit to customize your login page with My Domain login policies, you’re ready to go


## Step 1: Create a Federation ID

When setting up SSO, you use a unique attribute to identify each user. This attribute is the link that associates the Salesforce user with the third-party identity provider. You can use a username, user ID, or a Federation ID. We’re going to use a Federation ID.

No, a Federation ID isn’t owned by an interstellar shipping organization with nefarious designs. It’s basically a term that the identity industry uses to refer to a unique user ID.

Typically, you assign a Federation ID when setting up a user account. When you set up SSO on your production environment, you can assign the Federation ID for many users at once with tools like the Salesforce Data Loader. For now, let’s set up an account for Jedeye Tech’s new employee, Sia Thripio.

1.  From Setup, enter Users in the Quick Find box, then select **Users**.
2.  Click **Edit** next to Sia’s name.
3.  Under Single Sign On Information, enter the Federation ID: sia@jedeye-tech.com. **Tip** : A Federation ID must be unique for each user in an org. That’s why the username is handy. But if the user belongs to multiple orgs, use the same Federation ID for the user in each org.


## Step 2: Set Up Your SSO Provider in Salesforce

Your service provider needs to know about your identity provider and vice versa. In this step, you’re on the Salesforce side providing information about the identity provider, in this case, Axiom. In the next step, you give Axiom information about Salesforce.

On the Salesforce side, we configure SAML settings. SAML is the protocol that Salesforce Identity uses to implement SSO.

**Tip** : You’re going to work in both your Salesforce Dev org and the Axiom app. Keep them open in separate browser windows so that you can copy and paste between the two.

1.  In a new browser window, go to [http://axiomsso.herokuapp.com](http://axiomsso.herokuapp.com/Home.action).
2.  Click **SAML Identity Provider & Tester**.
3.  Click **Download the Identity Provider Certificate**. You upload this certificate later to your Salesforce org, so remember where you save it.
4.  In your Salesforce org, from Setup, enter Single in the Quick Find box, and then select **Single Sign-On Settings**.
5.  Click **Edit**.
6.  Select **SAML Enabled**.
7.  Click **Save**.
8.  In SAML Single Sign-On Settings:
    1.  Click **New**.
    2.  Enter the following values.
        -   Name: Axiom Test App
        -   Issuer: http://axiomsso.herokuapp.com
        -   Identity Provider Certificate: Choose the file you downloaded in step 3.
        -   Request Signature Method: Select **RSA-SHA1**.
        -   SAML Identity Type: Select **Assertion contains the Federation ID from the User object**.
        -   SAML Identity Location: Select **Identity is in the NameIdentifier element of the Subject statement**.
        -   Service Provider Initiated Request Binding: Select **HTTP Redirect**.
        -   Entity ID: Enter your My Domain URL, which is displayed on your org's My Domain Setup page. Make sure that entity ID includes "https" and references the Salesforce domain. It should look something like this: https://mydomain-dev-ed.my.salesforce.com.


## Step 3: Link Your Identity Provider to Salesforce

Now that you’ve configured Salesforce to know about the identity provider (Axiom), you teach your identity provider about your service provider (Salesforce).

You fill in a few fields in the following Axiom form. Easy peasy. Because you’re supplying Salesforce SSO settings, keep two browser windows open, one for Salesforce and one for Axiom.

1.  Return to the Axiom web app. If you don’t have the app open in a browser window, go to [http://axiomsso.herokuapp.com](http://axiomsso.herokuapp.com/Home.action).
2.  Click **SAML Identity Provider & Tester**.
3.  Click **generate a SAML response**.
4.  Enter the following values. Leave the other fields as is.


## Further reading


[[ MyDomain ]]