## Why Do You Need a Schema Definition?

Whether or not you’re the one who ends up creating a schema definition for your External Services registration, it’s helpful to understand its purpose and how it’s used. Already familiar with defining a schema from a REST-based API? Go ahead and skip to the next section **And... What Makes a For a Supported Schema?**

Remember our earlier examples —the REST-based API external web service from a payroll app and credit service? Although we have a REST-based bank API, we still need a common, standardized format to describe the structure of our bank’s REST-based API. Enter the API schema definition. Salesforce uses the commonly adopted [OpenAPI specification](https://swagger.io/resources/open-api/) for the description format. 

Your schema definition contains what types of inputs and outputs you can include in the calls, or requests, that your org makes to the external web service. For example, your calls might include ID as numerical input or name as text output.

It also contains the endpoint information and authentication parameters for the REST-based API web services that you can access. (Remember that the endpoint exposes the web services resources that External Services interacts with.) For example, this schema from a fictional bank includes methods for adding and deleting accounts. [https://th-external-services.herokuapp.com/accounts/schema](https://th-external-services.herokuapp.com/accounts/schema)

## And...What Makes for a Valid and Supported Schema?

So now we know what a schema, or more precisely, a schema definition, is all about. But what do we mean by a valid and supported schema? 

There are general schema validation requirements that the OpenAPI specification defines and there are specific External Services schema requirements. External Services can properly support your schema and call your web service when both of these criteria are met.  

**A Primer on Schema Validation**

Although a schema is human-readable, it must also be machine-readable. It needs to follow a logical structure so that External Services can easily consume it. An incorrectly structured schema means that the external web service can’t communicate (returns error and exception messages) and, ultimately, External Services can’t ingest it. Meeting structural, logical and syntax restrictions is a necessary first-pass of schema validation. The OpenAPI specification defines these general rules and takes the guesswork out of calling an external web service.

**Supported External Services Schema** 

In addition to general OpenAPI guidelines for schema validation, there are also schema limitations that are specific to External Services. You’ll want to review these requirements before you register your schema with External Services. A supported schema in External Services means that your schema is valid according to the OpenAPI specification and it also adheres to the specific External Service requirements.



#### Futher Reading

[[ External Objects ]]