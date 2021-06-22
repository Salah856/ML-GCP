
# Deploying the models on GCP

To deploy your machine learning models after you have exported them, you have to deploy exported models. The first step of deploying your models is to store them on a Google Cloud Storage bucket. In general, a dedicated cloud storage bucket is easier to use for the same project for the Google Cloud AI Platform. If you use a bucket from a different project, you need to make sure you have access to your cloud storage model in your Google Cloud AI Platform service account. Your attempt to build a Google Cloud AI Platform model version will fail without the required permissions.

Let's begin by looking into how to create a Google Cloud Storage bucket. An existing bucket can be used, but it must be in the same area where you plan to work on the Google Cloud AI Platform. The following code can help you create a new bucket:

```bash

BUCKET_NAME="google_cloud_ai_platform_your_bucket_name"

PROJECT_ID=$(gcloud config list project --format "value(core.project)")

BUCKET_NAME=${PROJECT_ID}-mlengine

echo $BUCKET_NAME

REGION=us-east2

gsutil mb -l $REGION gs://$BUCKET_NAME


```


## Uploading saved models to a Google Cloud Storage bucket

The next step is that you upload your models to a Google Cloud Storage bucket. If you are using Tensorflow SavedModels, then you can use the following code to upload your models:


```bash

SAVED_MODEL_DIR=$(ls ./your-export-dir-base | tail -1)
gsutil cp -r $SAVED_MODEL_DIR gs://your-bucket

```

If you have exported your model using scikit-learn or XGBoost, then you can use the following code to export your models in the .joblib , *.pk1 , or *.bst formats:

```bash

gsutil cp ./model.joblib gs://your-bucket/model.joblib
gsutil cp ./model.pkl gs://your-bucket/model.pkl
gsutil cp ./model.bst gs://your-bucket/model.bst

```

