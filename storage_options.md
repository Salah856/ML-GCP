
### Diving into the storage options

GCP provides various storage options to store your application data. Different applications have different storage needs, and depending on the application, performance improves.

Looking at the GCP storage options, it is very clear that it can support various storage needs like NoSQL, Document DB, Object Storage, Relational Database Management System (RDBMS), and so on. You can use Google's managed services for your storage needs, or you can use the Google infrastructure and install services that you need.

Choosing the right storage option for your application is important. Based on the available storage options in Google, the following chart will help you to identify the right storage option:


![1](https://user-images.githubusercontent.com/23625821/122635361-bbb09e80-d0e3-11eb-9570-5d05cda51873.png)


Next, we will discuss the following storage options in detail:

- Cloud Bigtable
- Cloud Datastore
- Cloud Firestore

- Cloud SQL
- Cloud Spanner
- Cloud Memorystore

## Cloud Bigtable and AI applications

Cloud Bigtable can act as storage in various AI and ML use cases. Most of the big data migration or modern data platforms use cloud Bigtable to build their NoSQL Database. For example, a streaming ML application can use Bigtable very well as a backend.


## Cloud Datastore and AI applications

Cloud Datastore can act as storage in AI and ML use cases for large web applications. Any e-commerce website hosted on GCP can use Datastore to save data, and using this data, ML models can be trained and can provide required recommendations to the user and in turn can increase customer satisfaction.


## Cloud Firestore and AI applications

Cloud Firestore can act as storage in AI and ML use cases for applications that are hosted on mobile and web devices. Any application hosted on GCP with both website and mobile applications can save the data in Firestore, and using this data, ML models can be trained and can provide required recommendations to users on both their mobile devices and website applications.


## Cloud SQL and AI applications

Cloud SQL can serve all the AI and ML use cases for large and complex structured data. Another service named Cloud Spanner can serve similar use cases, which can be served by Cloud SQL, but on a very large scale.


## Cloud Spanner and AI applications

Cloud Spanner can serve all the AI and ML use cases which are suitable for MySQL and PostgreSQL. Cloud SQL is right for serving AI and ML use cases that require up to 10 TB of structured data; for example, a machine learning use case requires data preparation, which involves complex SQL joins and can increase the efficiency of the process.

## Cloud Memorystore and AI applications

Cloud Memorystore can serve various AL and ML use cases using Redis ML modules. Redis ML has various ML modules as built-in data types. Cloud Memorystore can serve machine learning modules for linear and logistic regression, decision tree matrix calculations, and so on.

