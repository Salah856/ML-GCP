
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



