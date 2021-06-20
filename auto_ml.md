
# Overview of Cloud AutoML

Supervised machine learning models follow a consistent life cycle. Supervised learning is dependent on historical data. Based on the historical data, the model is trained. Model training is simply building a hypothesis function that is capable of predicting output or dependent variables based on the input or independent variables.

For example, in the case of a sales forecasting model for a retail store, historical sales data is used for training. The data can be horizontally spread across a large number of factors that impact sales. The training data is randomly split into a training dataset and evaluation dataset. Typically, there is an 80-20 split between training and evaluation data respectively.


![1](https://user-images.githubusercontent.com/23625821/122669242-a8253680-d1bc-11eb-9bc4-7b971c28f18c.png)


Traditionally, in a non-cloud environment, this process needs to be fully managed by the data scientist. GCP Cloud AutoML is a fully managed environment that takes care of all of the operational processes, infrastructure, and model management. GCP Cloud AutoML provides interfaces for the models related to Natural Language Processing (NLP) and Computer Vision (CV).


The advantages of Cloud AutoML are as follows:

- Ease of use
- High performance
- Speed & agility

## The workings of AutoML

AutoML simplifies the supervised learning process by creating a high-level abstraction over the training, evaluation, and deployment of machine learning models. The following diagram shows the workings of AutoML:

![1](https://user-images.githubusercontent.com/23625821/122669306-fdf9de80-d1bc-11eb-8ac3-f7d78a38041e.png)


## Document classification using AutoML Natural Language

Document classification is a very important use case that primarily deals with analyzing the contents of a document or a large archive of documents (for example, legal documents). At times, manual classification requires a lot of effort and may not be feasible.

GCP provides an easy-to-use natural language interface, which can be custom trained for document classification based on AutoML. Let's understand the classification process with a publicly available dataset of 20 newsgroups.

The dataset is available at http://qwone.com/~jason/20Newsgroups/ for download. This is a collection of approximately 20,000 newsgroup documents, partitioned evenly across 20 different newsgroups. These newsgroups correspond to a different topic. The goal is to train a model based on the training data, evaluate the model, and eventually use it for document classification.


### Navigating to the AutoML Natural Language interface

Log in to https://console.cloud.google.com with your GCP credentials. On the navigation menu, go to the ARTIFICIAL INTELLIGENCE section and click on the Natural
Language submenu:

![1](https://user-images.githubusercontent.com/23625821/122669505-07377b00-d1be-11eb-80e2-5ccd909dfbb4.png)

### Creating the dataset

To create a new dataset, click on the New Dataset button in the title bar:

![1](https://user-images.githubusercontent.com/23625821/122669542-32ba6580-d1be-11eb-946c-fb285f43dad6.png)


Provide a unique name for the dataset (in this case, newsgroups ). GCP provides the following options for uploading datasets:

- Upload a CSV file from a computer
- Upload text items from a computer
- Select a CSV on cloud storage



