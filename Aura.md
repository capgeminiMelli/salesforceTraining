

## Aura Concepts
 #### [[Controllers]]
 #### [[Actions]]
 
 #### [[Aura Syntax]]


## Concept: Page vs. Bundle

Before we tackle some of the abstract concepts, let’s look at something that’s fairly concrete: how an individual page or component is stored on Salesforce.

Visualforce pages (and Visualforce components, but let’s set those aside for now) are stored on Salesforce as a single entity, an ApexPage. When you use Salesforce Extensions for Visual Studio Code or another tool to copy your Visualforce pages to your local storage to work on them, an individual Visualforce page is represented as two files in the metadata/pages directory:

-   **yourPageName.page**
-   **yourPageName.page-meta.xml**

The first is the code for the page, and the second is the page metadata (API version, mobile settings, and so on).

Although your page might have dependencies on other artifacts, like an Apex controller or extension, static resources, and so on, they are separate from the page. Your page _references_ them, but doesn’t _include_ them.

An Aura component has more to it than a single code artifact plus metadata, with up to **eight** code artifacts plus metadata today (nine total). For this reason, an individual component is stored in a bundle that includes resources. This bundle is represented as a folder of files when you save it to your local storage. A complex component might look like this:![An example component bundle](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/lex_dev_lc_vf_concepts/lex_dev_lc_vf_concepts_basics/images/c1669611ed7c9548fe8f6d1340df0e76_map-component-package-manager.png)

We’ll talk about the most important resources in the component bundle throughout the rest of this module. For the remainder, see the details in [Component Bundles](https://developer.salesforce.com/docs/atlas.en-us.224.0.lightning.meta/lightning/components_bundle.htm) and elsewhere in the [Lightning Aura Components Developer Guide](https://developer.salesforce.com/docs/atlas.en-us.224.0.lightning.meta/lightning/) .


## Concept: Server-Side vs. Client-Side

This is one of the two “obvious” biggies. Except, actually, what’s obvious about it? Let’s be clear about what this means, and then make sure some of the implications are clear, too.

Classic Visualforce runs “on the server side.” That is, when a page is requested, a Salesforce server processes the markup, and then the resulting HTML is sent to the requesting user’s browser for display. If the page has an expression (those things inside “ {! }” delimiters), it’s evaluated by the server. References to global variables are resolved on the server. If the page accesses a controller property, that’s processed on the server. And so on. For the purposes of this conversation, all of the “framework processing” happens **on the server**. (Note that we’re setting aside using Visualforce + JavaScript remoting as a mere container for your JavaScript app. But then you’re not really using Visualforce, except as a web server.)

The process for Aura components is the opposite. When a component is requested, the component’s resources are packaged up and sent to the requesting user’s browser. Most of this is JavaScript, with some markup providing structure. The browser runs that JavaScript, which renders the resulting HTML and inserts it into the existing “page.” (We’ll explain those quotation marks shortly.) Expression evaluation, global variables, controller properties—those are all resolved **on the client**.

Visualforce Request Cycle

Aura Components Request Cycle

![Visualforce request lifecycle](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/lex_dev_lc_vf_concepts/lex_dev_lc_vf_concepts_basics/images/154dfaa40ed15a09f8313ad559562667_request-lifecycle-vf.png)

![Lightning component request lifecycle](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/lex_dev_lc_vf_concepts/lex_dev_lc_vf_concepts_basics/images/6853df0f60f95ceba9d50c5ead03c6e1_request-lifecycle-lc.png)

1.  User requests a page
2.  The server executes the page’s underlying code and sends the resulting HTML to the browser
3.  The browser displays the HTML
4.  When the user interacts with the page, return to step one

1.  The user requests an application or a component
2.  The application or component bundle is returned to the client
3.  The browser loads the bundle
4.  The JavaScript application generates the UI
5.  When the user interacts with the page, the JavaScript application modifies the user interface as needed (return to previous step)

This major architectural difference has major consequences. For example, your component can interact with a user without requiring a new server request, but if your component needs to save or load new data, that _does_ require a server request.

That sounds straightforward, or even obvious. But keep in mind, with classic Visualforce that interaction would come with a new, visible page request and reload. With an Aura component, the user’s interaction with client-side JavaScript feels more “live,” more responsive, so when the time comes to load new data, the latency of a server request can suddenly feel slow to the user—even if the overall experience takes less time than a Visualforce request!

You’ll find that Aura components perform well overall. However, without careful design of your server requests and how they affect the user experience, your users might very well think an app is “slow.”

We cover additional aspects of this divide in upcoming topics, but you need to keep the client-vs-server-side thing clear in your head when thinking about how the frameworks behave.

## Concept: Properties vs. Attributes vs. “Expandos”

Apex properties are (effectively) instance variables with custom logic behind them. When you define them in a Visualforce controller or extension, expressions on a page can use them. While getting and setting a controller property isn’t supposed to have side effects (the computer science term is idempotent), properties can call helper methods to share or abstract the logic behind them. Properties are really useful—and common—in Visualforce controllers.

While you might want to create similar properties in your Aura component JavaScript controller file, you can’t. You can try to add them to the helper, which might appear to work. However, the helper is a singleton, shared across all instances of your component. It’s more like a class static variable, so you can’t use it to save the state of an individual component.

So, what do you do?

# Learn Architectural Concepts

## Learning Objectives

After completing this unit, you’ll be able to:

-   Describe how the Visualforce page paradigm and the Aura component paradigm are different.
-   Explain the concept of different containers, and how you insert an Aura app or component into a container.



Visual Force makes the original salesforce experience (Multiple pages)

Aura uses "Single-Page-Applications" or **SPAs** 
- SPAs load a single page and a whole lot of JavaScript
- Instead of navigating form page to page users navigate from state to state. 


An Aura component is different. A “large” Aura component can be composed of dozens or even hundreds of smaller components, which themselves can be composed of many even smaller components. The Aura programming model is designed to handle _thousands_ of components assembled together into a single app.

**Custom Visualforce components are less powerful, less functional than custom Aura components.**

**Lightning Experience is the application container that runs aura**

You might have guessed that at least one additional container is the Salesforce Classic container. Here’s a (not necessarily complete) list of distinct containers where your code might run.

-   Salesforce Classic
-   Visualforce
-   Salesforce App
-   Lightning Experience
-   Lightning App Builder (LAB)
-   Lightning console apps
-   Communities
-   Lightning Components for Visualforce (LC4VF)
-   Lightning Out
-   Lightning for Outlook and Lightning for Gmail
-   Stand-alone my.app

You’re probably thinking two things after reading this list.

1.  That’s a lot of containers. What’s the difference? **Why do I care?** (The short answer: container services.)
2.  Wait a minute. Aren’t some of these the same thing? Aren’t LAB pages just Lightning Experience? Why is Visualforce its own container, and how is it different from LC4VF? (The short answer: Russian dolls.)
