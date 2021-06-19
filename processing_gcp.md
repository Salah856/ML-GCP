
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


While spinning up the instance, the user can either select one of the predefined compute options or go with a customized configuration. Compute Engine can be launched with either a Linux or Windows operating system. These instances can be launched with a CPU, GPU, and TPU, and since the infrastructure is provided by Google, users can do operating system-level customization.


Users can create managed and unmanaged instance groups in Compute Engine:

- A managed instance group will always contain identical virtual machines and support auto scaling, high availability, rolling updates, and more.
- An unmanaged instance group can contain machines with different configurations. Users can use instance templates while creating a managed instance group but not with an unmanaged instance group.

- It is suggested to select a managed and uniform instance group until there is a very specific need for machines of different configurations in the same pool.

Let's quickly talk about an option that will help to reduce the pricing. If it is possible, use preemptible machines. The preemptible virtual machines are short-lived and low-cost options that can be utilized when the workloads are known and expected to finish within 24 hours. These virtual machines provide a significant cost advantage and result in a cost saving of up to 80% compared with regular instances. Preemptible machines will save up to 80% of the cost but there is a catch: Google can always take that instance back from you with 30 seconds, notice. Google charges per second and gives sustainable user discounts.


#### Compute Engine and AI applications

While training models for AI (ML) applications, there is always a need for powerful machines to increase the efficiency of the model by providing ample training data and reducing the time to train the model. Google Compute Engine has multiple options to spin up powerful compute instances and groups that can train and run the model over it. For training and running models, you should use the power of CPUs and GPUs. For TensorFlow applications, there are machines with TPUs that should be used.


#### App Engine

App Engine is the PaaS provided by Google Cloud; it is a fully managed serverless application platform. App Engine is available in most of the regions covered by Google Cloud. You can consider App Engine a deployment-ready infrastructure; the developer just has to focus on building the application and deploying it on App Engine, and everything else will be taken care of.

App Engine comes with great features like auto-scaling, traffic splitting, application security, monitoring, and debugging—all these features are essential for deploying, securing, and scaling any application. Using tools like Cloud SDK and IntelliJ IDEA, developers can directly connect to App Engine and perform operations like debugging source code and running the API backend. One limitation of App Engine is that its operating system cannot be customized.

