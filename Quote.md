# Why do we need quotes?
-   Your customers want a summary and details about products and services that they’re considering.
-   Your customers want a breakdown of prices and totals of those items.
-   Capgemini wants to provide accurate information to your customers, and wants to give them that information quickly in a standard format.
-   Capgemini wants your customer to sign the quote electronically for a faster sales cycle.

A typical PDF quote contains 
- a list of products and services you’re quoting \[1\]
- the prices and discounts on those items \[2\]. 
- If prices and discounts also have totals and subtotals \[3\], they display in summary below the list of products and services.

### Sending Quotes
Then you choose one of several ways to share the quote with your customer. Here’s a simple method: With the click of a button, send the quote as an email attachment using a standard Salesforce email template.

Just remember: Salesforce CPQ can dynamically display several different pieces of information about your quote, quickly and easily, in a PDF document. And you can email that PDF to your customer like you would any other email attachment.

### Quote Documents

Quote documents can be previewed on indiviual quotes

You can enable
- custom logo to the header
- Watermark's on the image
- Add additional documents

### Quote Templates
A template can be divided into individual sections and can print fields. 
- **Line Columns** can be used to print individual columns. 
	- use the `Conditional Print Field` Column option field to display information on the quote pdf. 

### Quote Terms
A `Quote Term` Object is an object that can be related to a Quote Template. It allows the quote to specify the terms of the contract. 


## Further Reading
- [[Pricing Options]]
- [[Subscriptions]]
- [[price rules]]
