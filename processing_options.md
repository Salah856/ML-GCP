

# Understanding the processing options for ML in GCP

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


## Cloud Dataproc

Cloud Dataproc is a fully managed Hadoop and Spark cluster that can be spun within a few seconds. Cloud Dataproc is an auto scaling cluster and can be used to run Hadoop, Spark, and AI and ML applications very effectively. At peak hours, nodes can be added to the cluster based on usage, and it can scale down when there are lower requirements.

Beneath a Dataproc cluster Google actually runs compute instances. Users can choose from a wide range of machine configurations to build the cluster or if existing machine configurations are not sufficing the needs, users can build a cluster with a custom machine configuration as well. One very important thing to note here is the use of preemptive instances with the Dataproc cluster. This can work wonders with the pricing of the cluster.

Preemptive instances come at much lower prices, approximately at 20% of the actual instance with the same configuration, with the catch that Google can take the instance back with notification of 30 seconds.

With a Dataproc cluster, preemptive instances can be used as data nodes because generally a Dataproc cluster will be used for compute purpose and all data will be saved in Cloud Storage. So in this case, even if a preemptive instance goes down, that job will be shifted to another node and there will be no impact. Cloud Dataproc cluster pricing varies with instances, but it has very competitive pricing.


## Cloud Dataproc and AI applications

Cloud Dataproc can serve various AI and ML use cases using Apache Spark, Hadoop, and other tools. Consider Dataproc as a fully managed cloud Hadoop and Spark cluster. All the AI and ML use cases that can be built on Hadoop and Spark can be built on the Cloud Dataproc cluster.


## Cloud Dataflow

Cloud Dataflow is a fully managed service for running both batch and streaming applications, and has rich integration for running AI and ML jobs. It is a serverless service provided by Google and is built on top of Apache Beam, and, because of this, both the batch and streaming code can be used with each other. Cloud Dataflow applications can be built in Java and Python in a very simplified way.


Cloud Dataflow is integrated with other GCP services such as Cloud Pub/Sub, Cloud Machine Learning, Stackdriver, BigQuery, and Bigtable, which makes it very easy to build Cloud Dataflow jobs. Beneath Cloud Dataflow, App Engine is running, and because of that the user has unlimited capacity to scale their jobs.

Cloud Dataflow auto scales on its own based on the requirements of the job.


Cloud Dataflow pricing is mostly the same for batch and stream jobs, apart from the pricing for data processed. It charges on the basis of VCPU, RAM, persistent storage, and amount of data processed.


## Cloud Dataflow and AI applications

Cloud Dataflow can serve various AL and ML use cases in integration with Cloud Machine Learning. Fraud detection is a classic use case, which can be implemented with Cloud Dataflow and Cloud Machine Learning for streaming jobs.

So far, we have learned the essentials of GCP that will help us to use the platform in an efficient way, make the right choices, and build effective pipelines. You now have knowledge of all available compute, storage, and processing options on GCP. 

