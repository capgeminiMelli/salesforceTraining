### Examining the Execution Log

Notice that the first line in the execution log marks the EXECUTION_STARTED event and that the last line is the EXECUTION_FINISHED event. Everything in between is the execution context.

Let’s take a closer look at what happens. A CODE_UNIT_STARTED event marks when the code from the Execute Anonymous window was kicked off. This line is highlighted in red in the image below.

### Working in Bulk

Many developers fall into a common trap of designing their code to work with a single record. They quickly learn that on the Lightning Platform this can be a huge mistake.

Apex triggers can receive up to 200 objects at once. Currently, the synchronous limit for the total number of SOQL queries is 100, and 150 for the total number of DML statements issued So, if you have a trigger that performs a SOQL query or DML statement inside of a loop and that trigger was fired for a bulk operation, guess what?