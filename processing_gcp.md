
# Computing and Processing Using GCP Components


### Understanding the compute options

GCP provides various compute options to deploy your application and to use the actual Google infrastructure to run your applications.

The options available are as follows:

- Infrastructure as a Service (IaaS)
- Containers
- Platform as a Service (PaaS)


All compute options communicate with other GCP services and products, like storage, networking, Stackdriver, security, and the big data product suite. Based on a given application's need, an appropriate compute option is selected from the Compute Engine, Kubernetes Engine, App Engine, and Cloud Functions.

Google compute options help you to run virtual machines of multiple sizes on Google infrastructure and to customize them. It enables you to run containerized applications, and you can directly deploy your code on the engines if you don't have to take care of infrastructure-related items. So based on your needs, Google provides multiple options to use compute power, expedite the development effort, and reduce the time to market.


Next, we will discuss the following compute options in detail:

- Compute Engine
- App Engine

- Cloud Functions
- Kubernetes Engine


#### Compute Engine

Compute Engine is the IaaS provided by Google Cloud; it is a virtual machine running in the Google infrastructure.

Compute Engine is available across all the zones and regions provided by Google Cloud. It comes with a storage option of persistent disk and local Solid-State Drives (SSDs).SSDs are internally built with the integrated circuits on chips, and do not contain any spinning heads or disk drives for reading data. The SSDs are more durable and provide faster read times compared to hard disk drives. A persistent disk is a network storage that can be extended up to 64 TB, while the local SSD is the encrypted drive, which is actually attached to the server and can extend up to 3 TB.

