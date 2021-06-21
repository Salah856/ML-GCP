
# Performing audio sentiment analysis using DialogFlow

DialogFlow provides a feature for performing sentiment analysis on each of the user expressions. This feature is useful in the context of a call center when the users of a product or service call for assistance. DialogFlow leverages the sentiment analysis engine from Cloud Natural Language. The sentiment analysis can be enabled from the DialogFlow settings menu by navigating to the Advanced settings and clicking Enable sentiment analysis for the current query.


This feature is available in the Enterprise Edition of DialogFlow. DialogFlow also provides integration with the Cloud Natural Language engine for performing sentiment analysis. Each user conversation is a stateful interaction and is uniquely identified by session_id within DialogFlow. It is recommended that you use the same session ID within the API calls for continuous conversation. Here is a code snippet for using the DialogFlow API for performing sentiment analysis based on the user expressions in the conversation:


```py

import dialogflow_v2 as dialogflow

def get_sentiment(PROJECT_ID, SESSION_ID, text,language_code):

  session_client = dialogflow.SessionsClient()
  session_path = session_client.session_path(project_id, session_id)
  
  text_input = dialogflow.types.TextInput(text=text, language_code=language_code)
  query_input = dialogflow.types.QueryInput(text=text_input)
  
  sentiment_config = dialogflow.types.SentimentAnalysisRequestConfig(analyze_query_text_sentiment=True)
  query_params = dialogflow.types.QueryParameters(sentiment_analysis_request_config=sentiment_config)
  
  response = session_client.detect_intent(session=session_path, query_input=query_input, query_params=query_params)

```

