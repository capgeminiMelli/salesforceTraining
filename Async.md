![[Pasted image 20210720143358.png]]

## How Asynchronous Processing Works

Asynchronous processing, in a multi-tenant environment, presents some challenges:

**Ensure fairness of processing**

Make sure every customer gets a fair share of processing resources.

**Ensure fault tolerance**

Make sure no asynchronous requests are lost due to equipment or software failures.

  
The platform uses a queue-based asynchronous processing framework. This framework is used to manage asynchronous requests for multiple organizations within each instance. The request lifecycle is made up of three parts:

**Enqueue**

The request gets put into the queue. This could be an Apex batch request, future Apex request or one of many others. The platform will enqueue requests along with the appropriate data to process that request.

**Persistence**

The enqueued request is persisted. Requests are stored in persistent storage for failure recovery and to provide transactional capabilities.

**Dequeue**

The enqueued request is removed from the queue and processed. Transaction management occurs in this step to assure messages are not lost if there is a processing failure.

  
Each request is processed by a handler. The handler is the code that performs functions for a specific request type. Handlers are executed by a finite number worker threads on each of the application servers that make up an instance. The threads request work from the queuing framework and when received, start a specific handler to do the work.

[[Future Method]]

[[Batch Apex]]

[[Queueable Apex]]

[[Scheduled Apex]]

# How to monitor Asynchronous Jobs

The great thing about async jobs is that they work silently in the background. The tough thing about async jobs is that they work silently in the background. Luckily there are a few ways to monitor what is going on with your jobs under the covers.

You can monitor the status of all jobs in the Salesforce user interface. From **Setup**, enter Jobs in the Quick Find box, then select **Apex Jobs**.

The Apex Jobs page shows all asynchronous Apex jobs with information about each job’s execution. The following screenshot shows one future method job and two completed batch jobs for the same Batch Apex class.

![Apex Jobs](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/asynchronous_apex/async_apex_monitoring/images/03df8e5201b1451295d19fcf7560441d_apex-jobs-page.png)

If you have many batch jobs, use the Batch Jobs page to view only batch jobs. To open the Apex Batch Jobs page, click the link at the top of the Apex Jobs page. Use the slider in the Apex Batch Jobs page to select a specific date range and narrow down the list of batch jobs displayed. You can view past jobs that haven’t been deleted yet. The Batch Jobs page groups jobs by the batch class.

## Monitoring Queued Jobs with SOQL

To query information about your submitted job, perform a SOQL query on AsyncApexJob by filtering on the job ID that the System.enqueueJob method returns.

```java
AsyncApexJob jobInfo = [SELECT Status, NumberOfErrors
    FROM AsyncApexJob WHERE Id = :jobID];
```

## Monitoring Queue Jobs with the Flex Queue

The Apex Flex queue enables you to submit up to 100 batch jobs for execution. Any jobs that are submitted for execution are in holding status and are placed in the Apex Flex queue. Up to 100 batch jobs can be in the holding status.

Jobs are processed first-in first-out—in the order in which they’re submitted. You can look at the current queue order and shuffle the queue, so that you could move an important job to the front, or less important ones to the back.

When system resources become available, the system picks up the next job from the top of the Apex Flex queue and moves it to the batch job queue. The system can process up to five queued or active jobs simultaneously for each organization. The status of these moved jobs changes from Holding to Queued. Queued jobs get executed when the system is ready to process new jobs. Like other jobs, you can monitor queued jobs in the Apex Jobs page.