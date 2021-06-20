
# Building ML Pipeline In GCP

Let's go through a detailed example where we will build an end-to-end pipeline, right from loading the data into Cloud Storage, creating BigQuery datasets over it, training the model using BigQuery ML, and testing it. In this use case, we will use a logistic regression model for finding the lead conversion probability.

The leads data contains various attributes about prospective customers. BigQuery ML has built-in functionality where we can directly train the model over any dataset. We can predict the output variable and the conversion probability. BigQuery provides an SQL interface to train and evaluate the machine learning model. This model can be deployed on the platform for consumption.


We have two datasets: leads training data and test data, where the training data is 80% of the actual overall data and the test data is 20%. Once the model is trained using the training data, we will evaluate the model on the test data and find the leads conversion probability for each prospect in the following categories:

- Junk lead
- Qualified

- Interested
- Closed

- Not interested
- Not eligible
- Unreachable

## Understanding the flow design

The following chart represents the end-to-end process of loading data into Cloud Storage and BigQuery, and training a model and testing it using the leads data. You can choose a dataset of your choice:


![1](https://user-images.githubusercontent.com/23625821/122663342-fa089500-d199-11eb-9326-7d415d44bfa8.png)

From the preceding diagram, we can see the following:

1. We have loaded the training and test dataset for leads into Cloud Storage buckets.

2. After loading data into Cloud Storage, we will create the leads dataset into BigQuery with two tables, namely, leads_training and leads_test .

3. Once the dataset is created, we will use the leads_training table to train our model and the leads_test table to test the model.

### Loading data into Cloud Storage

Let's discuss the step-by-step process to load data into Cloud Storage:

1. You should have the training and test data.
2. Create a training and test bucket in Cloud Storage.

3. From the GCP Console, click on the navigation menu in the top left, and from the storage section click on Storage (Cloud Storage).
4. Click on Create a bucket at the top. You will see the following screen:

![1](https://user-images.githubusercontent.com/23625821/122663377-405df400-d19a-11eb-83ba-1f08a8c74592.png)

5. Give a globally unique name to the bucket.
6. Choose a regional bucket for your use case.

7. Select the Location where you want to create the bucket.

