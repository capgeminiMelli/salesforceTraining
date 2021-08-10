# Quote calculator Plugin
CPQ has a custom script object that comes standard with Salesforce CPQ, just put the Javascript code into the salesforce `Customer Script` object. 
### Uses 3 components
- **Promise**: Built in javascript object that allows for asynchronous programming in the browser. 
- **JSForce**: 3rd party library that provides a unifed way to perform queries, execute apex rest calls, use the metadata api or make HTTP requests remotely
- **Models**: The JavaScript calculator represents Quote_C and QuoteLine__C objects as quotemodel and quotelinemodel objects respectively


### Configuring settings
To use the quote calculator plugin, Go to the `Installed Packages` Setting and then add the  `Plugins` tab and add the custom script object name under the `Quote Calculator plugin`.


![[Pasted image 20210805161337.png]]


### Additional Resources
[JS Website](https://jsforce.github.io/)

[Github Repository](https://github.com/samcheck/thdx-gcp-rest)