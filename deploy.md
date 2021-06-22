
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

## Deploying models and their version

The Google Cloud AI Platform uses model and version resources to organize your trained models. An AI Platform is a container for the models of your learning machine. In the AI Platform, you create a database resource to deploy a model, construct a model version, and then connect the model version to the model file that is stored in cloud storage. You can use the gcloud console to build a default tool for your product versions, filling out your preferred model name without the enclosed brackets, as shown here:


```bash

gcloud ai-platform models create "[YOUR-MODEL-NAME]"

```


By example, a model version with the Cloud ML Service Agent Identity and Access Management (IAM) function has permissions from the Google-managed service account.
For most situations, this default service account is adequate. However, if you are using a custom prediction routine and need to have a different set of permissions in your model version, you can add another service account for your use. For example, if your model version needs access to a cloud storage bucket from a specific Google Cloud project, a service account with reading authorization from that bucket can be defined. The sample Python code to create a service account is shown in the following code block:


```py

import os

from google.oauth2 import service_account
import googleapiclient.discovery


def create_service_account(project_id, name, display_name):

  """Creates a service account."""
  credentials=service_account.Credentials.from_service_account_file(filename=os.environ['GOOGLE_APPLICATION_CREDENTIALS'],
      scopes['https://www.googleapis.com/auth/ cloud-platform'])

  service = googleapiclient.discovery.build('iam', 'v1', credentials=credentials)

  my_service_account = service.projects().serviceAccounts().create( name='projects/' + project_id, 
        body={ 'accountId': name,'serviceAccount': {'displayName':display_name}}
      ).execute()

  print('Created service account: ' + my_service_account['email'])
  
  return my_service_account


```

