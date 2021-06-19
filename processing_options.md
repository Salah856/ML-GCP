

# Understanding the processing options 

Apart from the IaaS option, which you can use for building your own AI and ML pipeline using compute options, Google provides a few managed services that can be used to process your data and build AI and ML pipelines. The following are the fully managed processing options:

- BigQuery
- Dataproc
- Cloud Dataflow

All the managed processing options are integrated with other Google Cloud Services such as networking, identity and access management, Stackdriver, and so on. These make it easy to track activities and tighten security for applications.

BigQuery can be used for offloading the existing data warehouse and creating a new one, and with the BigQuery ML options you can build an ML pipeline.

Dataproc can be used for migrating an existing Hadoop project on GCP and running AI and ML pipelines over it. Cloud Dataflow can be used for building completely new pipelines on GCP.


## BigQuery

BigQuery is a cloud data warehouse for GCP and comes in a machine learning flavor (BigQuery ML). It is a very powerful tool that can process petabytes of data, and gives you readily available models that you can use in SQL programming for building your machine learning pipeline.

BigQuery is fast, scalable, and serverless. You can build BigQuery datasets in just a few clicks and start loading the data into them. BigQuery uses Colossus to store data in native tables in a columnar format, and the data is compressed. This makes data retrieval very fast. Apart from storage, BigQuery uses the following tools and network components to make it fast, reliable, and efficient:

- The Jupyter network for shuffling the data
- The Dremel engine for processing
- Borg for cluster management

In other words, it uses Google's great infrastructure and best service, making it fast, highly available, and scalable. BigQuery comes with additional features such as data and query sharing, saving required queries; it is ANSI 2011-compliant and integrated with native as well as outside tools including Informatica, Talend, and so on. All the data that is saved in BigQuery is encrypted.

It is federated and can query data from other services such as Cloud Storage and Bigtable. BigQuery also supports real-time analytics with BigQuery Streaming.
BigQuery has a friendly user interface from where users can perform all the operations, and it has a command-line tool, bqclient , which can be used to connect to BigQuery.

BigQuery comes in two pricing models: "pay as you go," which costs users $5 per TB of query processing, and "flat rate pricing," which is approximately $40,000 per month, for which the user gets 2,000 dedicated slots for processing. For storage, it is $0.02 per GB a month; for short-term storage and for long-term storage, it is $0.01 per GB a month.



## BigQuery and AI applications

BigQuery ML is the BigQuery machine learning flavor that has a few built-in algorithms that can be directly used in SQL queries for training models and predicting output. BigQuery ML currently has support for linear regression, binary logistic regression, and multiclass logistic regression for classification models.

