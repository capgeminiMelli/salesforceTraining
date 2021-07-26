## Get Data from a Service

It’s time to put your new HTTP knowledge to use with some Apex callouts. This example sends a GET request to a web service to get a list of woodland creatures. The service sends the response in JSON format. JSON is essentially a string, so the built-in JSONParser class converts it to an object. We can then use that object to write the name of each animal to the debug log.

Before you run the examples in this unit, you’ll need to authorize the endpoint URL of the callout, https://th-apex-http-callout.herokuapp.com, using the steps from the [Authorize Endpoint Addresses](https://trailhead.salesforce.com/apex_integration_services/apex_integration_callouts.htm#apex_integration_callouts_authorizing "HTML (New Window)") section.

1.  Open the Developer Console from the Setup gear (![Setup gear icon](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/apex_integration_services/apex_integration_rest_callouts/images/d53c37ae7a304569f11b01c79f4df2ee_lightning-setup-gear-2.png)).
2.  In the Developer Console, select **Debug** | **Open Execute Anonymous Window**.
3.  Delete the existing code and insert the following snippet.
    
    ```java
    Http http = new Http();
    HttpRequest request = new HttpRequest();
    request.setEndpoint('https://th-apex-http-callout.herokuapp.com/animals');
    request.setMethod('GET');
    HttpResponse response = http.send(request);
    // If the request is successful, parse the JSON response.
    if (response.getStatusCode() == 200) {
        // Deserialize the JSON string into collections of primitive data types.
        Map<String, Object> results = (Map<String, Object>) JSON.deserializeUntyped(response.getBody());
        // Cast the values in the 'animals' key as a list
        List<Object> animals = (List<Object>) results.get('animals');
        System.debug('Received the following animals:');
        for (Object animal: animals) {
            System.debug(animal);
        }
    }
    ```
    
    
4.  Select **Open Log**, and then click **Execute**.
5.  After the debug log opens, select **Debug Only** to view the output of the System.debug statements. The names of the animals are displayed.

The JSON for our example is fairly simple and easy to parse. For more complex JSON structures, you can use [JSON2Apex](https://json2apex.herokuapp.com/ "HTML (New Window)"). This tool generates strongly typed Apex code for parsing a JSON structure. You simply paste in the JSON, and the tool generates the necessary Apex code for you. Brilliant!

## Send Data to a Service

Another common use case for HTTP callouts is sending data to a service. For instance, when you buy the latest Justin Bieber album or comment on your favorite “Cat in a Shark Costume Chases a Duck While Riding a Roomba” video, your browser is making a POST request to submit data. Let’s see how we send data in Apex.

This example sends a POST request to the web service to add an animal name. The new name is added to the request body as a JSON string. The request Content-Type header is set to let the service know that the sent data is in JSON format so that it can process the data appropriately. The service responds by sending a status code and a list of all animals, including the one you added. If the request was processed successfully, the status code returns 201, because a resource has been created. The response is sent to the debug log when anything other than 201 is returned.

1.  Open the Developer Console from the Setup gear (![Setup gear icon](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/apex_integration_services/apex_integration_rest_callouts/images/d53c37ae7a304569f11b01c79f4df2ee_lightning-setup-gear-2.png)).
2.  In the Developer Console, select **Debug** | **Open Execute Anonymous Window**.
3.  Delete any existing code and insert the following snippet.
    
    ```java
    Http http = new Http();
    HttpRequest request = new HttpRequest();
    request.setEndpoint('https://th-apex-http-callout.herokuapp.com/animals');
    request.setMethod('POST');
    request.setHeader('Content-Type', 'application/json;charset=UTF-8');
    // Set the body as a JSON object
    request.setBody('{"name":"mighty moose"}');
    HttpResponse response = http.send(request);
    // Parse the JSON response
    if (response.getStatusCode() != 201) {
        System.debug('The status code returned was not expected: ' +
            response.getStatusCode() + ' ' + response.getStatus());
    } else {
        System.debug(response.getBody());
    }
    ```

    
4.  Select **Open Log**, and then click **Execute**.
5.  When the debug log opens, select **Debug Only** to view the output of the System.debug statement. The last item in the list of animals is "mighty moose".