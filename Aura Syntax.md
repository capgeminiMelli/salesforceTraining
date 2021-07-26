## Component Attributes

If you need to access the value in an expression in your component markup, use a component attribute. A component attribute is declared like this.

```java
<aura:attribute name="myAttribute" type="Integer"/>
```

Copy

Component attributes require, at a minimum, a name and a data type. (There are optional attributes for defaults and so on.) Reference the attribute in markup using standard expression syntax.

```java
{!v.myAttribute}
```

Copy

(We’ll have more to say about expressions and expression syntax in the next module.)

Get and set the attribute value in your controller JavaScript code using (surprise!) the get and set methods.![Use get and set functions to get and set component attribute values](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/lex_dev_lc_vf_concepts/lex_dev_lc_vf_concepts_code/images/488cf41c77baa58b51842f2563022111_lex-dev-lc-vf-concepts-snippet-get-set.png)

The get and set methods are functions available on the component parameter passed into the myAction action handler function.

```java
({
    myAction : function(component, event, helper) {
        var counter = component.get("v.myAttribute");
        counter++;
        component.set("v.myAttribute", counter);
    },
})
```

Copy

Here get (line 3) retrieves the value of the myAttribute component attribute and assigns the value to the local counter variable. counter gets incremented, and then set (line 5) updates the component attribute.

If other components shouldn’t fiddle with the value of your component’s attribute, make the attribute private. Otherwise, the attribute becomes part of your component’s public API.