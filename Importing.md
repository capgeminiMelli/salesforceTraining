## Importing Data into [[Salesforce]]

Salesforce offers two main methods for importing data.

-   **Data Import Wizard**—this tool, accessible through the Setup menu, lets you import data in common standard objects, such as contacts, leads, accounts, as well as data in custom objects. It can import up to 50,000 records at a time. It provides a simple interface to specify the configuration parameters, data sources, and the field mappings that map the field names in your import file with the field names in Salesforce.
-   **Data Loader**—this is a client application that can import up to five million records at a time, of any data type, either from files or a database connection. It can be operated either through the user interface or the command line. In the latter case, you need to specify data sources, field mappings, and other parameters via configuration files. This makes it possible to automate the import process, using API calls.

## Use the Data Import Wizard When:

-  **You need to load less than 50,000 records.**
-   The objects you need to import are supported by the wizard.
-   You don’t need the import process to be automated.

## Use Data Loader When:

-   You need to load 50,000 to five million records. If you need to load more than 5 million records, we recommend you work with a Salesforce partner or visit the [AppExchange](http://appexchange.salesforce.com/) for a suitable partner product.
-   You need to load into an object that is not supported by the Data Import Wizard.
-   You want to schedule regular data loads, such as nightly imports.