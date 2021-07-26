## Learning Objectives

After completing this module, you will be able to:

-   Describe the differences between web service and HTTP callouts.
-   Authorize an external site with remote site settings.

## Make Callouts to External Services from Apex

An Apex callout enables you to tightly integrate your Apex code with an external service. The callout makes a call to an external web service or sends an HTTP request from Apex code, and then receives the response.

Apex callouts come in two flavors.

-   Web service callouts to SOAP web services use XML, and typically require a WSDL document for code generation.
-   HTTP callouts to services typically use REST with JSON.

These two types of callouts are similar in terms of sending a request to a service and receiving a response. But while WSDL-based callouts apply to SOAP Web services, HTTP callouts can be used with any HTTP service, either SOAP or REST.

So you are probably asking yourself right now, “Which one should I use?” Whenever possible, use an HTTP service. These services are typically easier to interact with, require much less code, and utilize easily readable JSON. All the “cool kids” have been switching to REST services over the last couple of years, but that’s not to say that SOAP Web services are bad. They’ve been around forever (in Internet years) and are commonly used for enterprise applications. They are not going away anytime soon. You’ll probably use SOAP mostly when integrating with legacy applications or for transactions that require a formal exchange format or stateful operations. In this module we’ll touch on SOAP, but will spend most of our time on REST


[[REST]]