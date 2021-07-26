## Concept: Actions

In Visualforce, an action is a controller method that returns a PageReference at the end of it. Usually attached to a button or a link, an action represents work the user wants the app to do, followed by navigating to a next or results page, or maybe just back “home.” For example, an edit button calls an action method that loads data for a record, and then navigates to a page with an edit form.

![Ladder!](https://trailmaker-assets.s3.amazonaws.com/imagese12eba32410a08a074ee32d9403f12ed.png) Aura component actions are similar.** Actions are functions you write in JavaScript and attach to user interface elements. _Ladder time at last!_**

But wait. There are important differences, and if you miss them you’ll be chuting down instead of laddering up.

First, realize that actions aren’t direct method or function calls, in either Visualforce or Aura components. _You_ don’t call them, the _framework_ invokes them when appropriate. So far the same.

However, in Visualforce your actions are methods defined on an Apex class. You get some language infrastructure around your method, like instance variables, and class and instance methods.

```java
({ myAction : function(component, event, helper) { 
	// add code for the action 
	}, 
})
```