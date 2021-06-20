
# Building ML Pipeline In GCP

Let's go through a detailed example where we will build an end-to-end pipeline, right from loading the data into Cloud Storage, creating BigQuery datasets over it, training the model using BigQuery ML, and testing it. In this use case, we will use a logistic regression model for finding the lead conversion probability.

The leads data contains various attributes about prospective customers. BigQuery ML has built-in functionality where we can directly train the model over any dataset. We can predict the output variable and the conversion probability. BigQuery provides an SQL interface to train and evaluate the machine learning model. This model can be deployed on the platform for consumption.


We have two datasets: leads training data and test data, where the training data is 80% of the actual overall data and the test data is 20%. Once the model is trained using the training data, we will evaluate the model on the test data and find the leads conversion probability for each prospect in the following categories:

- Junk lead
- Qualified

- Interested
- Closed

