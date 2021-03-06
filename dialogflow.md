
# Smart Conversational Applications Using DialogFlow

Artificial intelligence (AI) is continuously changing the way we search for and do stuff, and chatbots are the true illustration of people's desire to get rid of things that theydo not want to do by themselves. AI-powered chatbots can do amazing things without involving humans.


A chatbot is a smart chat program. It should be able to convincingly simulate a person. When it is combined with AI technologies, it is called an intelligent chatbot. The most common instance of a chatbot is the client support system that some companies use. It has developed so that 70–80% of the conversation is conducted without an actual person from the company engaging the customer in conversation.

The banking and financial market is already making significant use of chatbots to deal with client requests and rapidly assist them in their bank transactions. For precisely the same reason, chatbot platforms are being provided by cloud providers to reduce time to market.

In this article, we will learn how to build conversational applications using a Google Cloud Platform (GCP) service named DialogFlow. DialogFlow provides an easy way for building conversational applications for businesses and can greatly save operational costs.


## Introduction to DialogFlow

Before we start with DialogFlow, we need to understand at a high level how different technologies are used to empower an intelligent chatbot system. Most chatbots are a kind of interface for emails or dialog where bots respond to your text instead of people. These chatbots operate within the context of the containing application.

However, the catch centers around the user interface layer that you communicate with. The conversations that humans have with bots is driven by machine learning (ML) algorithms that break your messages down into natural human language with natural language understanding (NLU) methods and answer queries in a manner that is comparable to what any human, on the other side, can expect.

### Understanding the building blocks of DialogFlow

Let's learn about the various building blocks of a conversational application by looking at the high-level architecture of DialogFlow. The following diagram represents the different components of any chatbot application at a high level:


![1](https://user-images.githubusercontent.com/23625821/122715357-09a2df00-d269-11eb-802c-cdc67616f40f.png)


The building blocks and interfaces of DialogFlow: 


- DialogFlow agent: This component, in a nutshell, is similar to a human agent who needs to be trained to handle calls from the users. For example, a call center employee for a bank needs to understand some of the fundamental workflows, terminologies, and common scenarios that they are going to encounter while attending the customer calls; however, the training cannot cater to all the possible questions and conversational branches. The agent needs to understand the intent within the context and respond with the best possible option or a leading question if the information is insufficient to satisfy the customer's queries. Similar to the human agent, a DialogFlow agent is a module that replicates the human agent and understands the natural language with a certain level of fuzziness. As
a DialogFlow application developer, we need to design and develop the DialogFlow agent for handling the conversations within the context of the intended application.

- DialogFlow intent: Once the agent converts the text into segments, certain keywords are marked and tagged to understand the intent within the agent's
context. As in the case of human conversation, the DialogFlow agent and the human user on the other end take turns in the conversation in order for it to be
meaningful dialog. The information gathered from the person in one turn is called the end user expression. The DialogFlow agent needs to be trained to match the end user expression to a preconfigured intent—this process is called intent classification. As an example, if we are designing a DialogFlow agent for
handling restaurant reservations, the agent needs to respond to the user's questions and queries related to the menu, timings, and reservations. This is called the context of the conversation, and the agent needs to classify the user's intent within the context of restaurant reservations. Based on the intent
classification, the agent either responds by seeking additional information from the user or queries the application's backend to find the answer to the question.
it consists of trainging phrases, action, parameters, responses. 

- DialogFlow entity: When the agent extracts intent from the end user conversation, it is mapped to an entity. The entity associates a semantic meaning
to the keyword. DialogFlow provides a set of system entities that are common conversational entities across various contexts—for example, amounts and units,
date and time, and so on. DialogFlow also provides an interface for defining developer entities. These are the context-specific, custom entities that the
application developer can create for the agent to understand the conversation within the context of the application. For example, the restaurant reservation
agent can be trained with developer entities that map to the specific menu item served by the restaurant.

- DialogFlow context: Similar to human interaction, the DialogFlow conversation happens within a context. The application caters to a specific business scenario
and so the keywords need to be understood within the context of the application. It is important to correctly match the intent with the context of the application for the conversation to be meaningful. With the use of context, the conversation can be structured in a particular direction (input and output context).

- Follow-up intents: We can use follow-up intents to set the context for various intents. There is a parent–child relationship between a parent intent and the
follow-up intent. It is possible to create a nested hierarchy of follow-up intents within the context of the conversation. DialogFlow provides a set of predefined
follow-up intents that represent a majority of the expressions used during a conversation. The platform also provides a way to define custom follow-up intents for more granular control and conversation flows.

- DialogFlow events: Using DialogFlow events, the agent can trigger conversation flows in response to external events. The external events are referred to as the
nonconversational inputs within the context. For example, the receipt of an email, social media message, or a phone call to a particular number can be configured as an external event. DialogFlow agents can be configured to listen to such events and take a conversational path based on the specific event. There are some predefined platform events available on DialogFlow. These are the events that occur on the integrated platform.


- DialogFlow fulfillment: There are times when the conversation requires data from external sources in order to serve the user's desired information. In such
cases, DialogFlow provides a fulfillment interface to fork the request to external sources, such as databases and APIs, and request specific data points. Once the data is received from the external services, DialogFlow integrates the data into the intent and context of the conversation and provides the response to the caller. A fulfillment setting can be enabled for each intent. If there is no fulfillment defined, DialogFlow uses a static response defined within the intent. Interaction with the fulfillment agent is enabled via a webhook service. A webhook makes it easy to integrate two heterogeneous applications. DialogFlow serializes the context and intent data over to the webhook service. The webhook service, in turn, calls the external API endpoint or accesses the database for the requested information. Here is the workflow that defines the life cycle of a DialogFlow request that requires the use of external source data via a fulfillment service:

![1](https://user-images.githubusercontent.com/23625821/122716754-f5f87800-d26a-11eb-8140-f44c688d93c5.png)


### Building a DialogFlow agent

As a generic GCP principle, any service exists within a GCP project. One GCP project can contain one DialogFlow agent. If we want to have multiple DialogFlow agents, they need to be managed under a different project. A project organizes all the resources required by the DialogFlow agent. As a prerequisite, we need to enable APIs, monitoring tools, and billing information.

We need to provide access to user accounts for the project and set access controls at a granular level so that the user has access to a minimum service footprint.

We will work from the DialogFlow console by navigating to https://dialogflow.cloud.google.com/#/getStarted . 

Let's build a DialogFlow agent for a bookstore. Once you navigate to the console, click on the Create Agent button on the side menu or the console landing page. Select the agent name based on the context of the application along with the default language and the timezone. The DialogFlow console provides an option to use an existing GCP project as well as the creation of a new project during the agent creation workflow from the console. The following screenshot shows the agent creation screen in the DialogFlow console:




We will create a new Google project from the DialogFlow console. Click on the Create button in the top-right corner. Once the agent is created, we are taken to the intents screen. DialogFlow provides two default intents for every agent. These are preconfigured intents that are typically required by any application:

![1](https://user-images.githubusercontent.com/23625821/122731336-78893380-d27b-11eb-98f1-042039b7ffb1.png)


- Welcome intents: This is a default intent for beginning the conversation. As a best practice, the agent needs to greet the user and match the overall user style of the greeting. It is also recommended that the welcome intent should reply with the domain-specific capabilities the agent provides. For example, in the case of the bookstore agent, the agent needs to greet the user and talk briefly about the bookstore. 

- Fallback intent: This is a default intent that is invoked when the agent cannot match the user expression with any of the configured intents.

All the intents are configured with contexts, events, training phrases, actions and parameters, responses, and fulfillments. Let's look at the default welcome intent. The welcome intent can be configured and modified for engaging the user based on the application context:


![1](https://user-images.githubusercontent.com/23625821/122731524-b0907680-d27b-11eb-8b5f-81a1dc255601.png)

The default welcome intent is configured with a set of training phrases and responses. Let's modify the default welcome intent to suit our bookstore agent. We can add a new response(s) as well as delete the default responses provided by DialogFlow.


The following screenshot illustrates the configuration of the welcome intent:

![1](https://user-images.githubusercontent.com/23625821/122731727-df0e5180-d27b-11eb-8caf-85d3e62c9c39.png)

The DialogFlow console provides an easy way to quickly test the configured responses. On the right pane, DialogFlow provides a way to provide audio as well as text input and simulates the response from the DialogFlow agent based on the configured intent. Here is a screenshot that illustrates the response from the welcome intent:


![1](https://user-images.githubusercontent.com/23625821/122732197-5512b880-d27c-11eb-8005-77264b6a72da.png)


Let's create a couple of custom intents to help the MyBookStore DialogFlow agent to continue a conversation with the caller beyond the  welcome intent. We want
the agent to perform the following two tasks:

- Mention a list of new arrivals in the current month.
- Reserve a copy of the book for the user to pick up.


We need to create two intents in this case. Let's create our first intent, which informs users about the latest arrivals at the bookstore in the current month. For example, when the user says 'I want to know about the latest arrivals', the agent should respond with 'Here is a list of new books that have arrived this month. Book - 1, Author, Publication'. The following screenshot shows the process of the creation of a new custom intent:


![1](https://user-images.githubusercontent.com/23625821/122732444-92774600-d27c-11eb-9e06-e66bb0d37761.png)


As seen from the preceding screenshot, we perform the following steps:

1. Click on the Create Intent button in the DialogFlow console.
2. Provide a name for the custom intent. In this case, we are naming it New Arrivals.

3. Click on the Save button.
4. As a basic configuration, configure the various training phrases that the agent can respond to within the current intent.


The following screenshot shows the process of configuring training phrases and the agent's response within the New Arrivals intent:


![1](https://user-images.githubusercontent.com/23625821/122732626-c18db780-d27c-11eb-91da-dfc9dea86ca3.png)


Add multiple variations of possible user phrases within a specific custom intent. When we use natural language for communication, there are numerous ways in which we can express a particular thing. The more training phrases we configure, the more DialogFlow is able to train the model to accurately handle various ways of communicating. Internally, DialogFlow leverages ML algorithms that get better with more training data.


It is recommended that the intent needs to be configured with at least 10 combinations of the training phrases:

1. DialogFlow provides a training tool for the implementation of a feedback loop and improves the accuracy of the agent. Once the DialogFlow agent is deployed
and the users start communicating with the agent, there are phrases and utterances from the user that get logged in DialogFlow. We need to enable the settings to log interactions to DialogFlow. The settings can be found on the General tab on the agent settings page. The following screenshot shows the general settings for the DialogFlow agent:

![1](https://user-images.githubusercontent.com/23625821/122733055-1c271380-d27d-11eb-9cfe-8c80b6d7d83a.png)


2. Add various responses for the New Arrivals intent. Within the context of this intent, all the variations of the input expressions expect a response from the
agent to mention the list of new arrivals at the bookstore. Similar to what we did with the default welcome intent, we can configure multiple responses that
provide information about new arrivals to the caller. DialogFlow randomly chooses a specific instance of the configured responses for each user expression that matches the configured training phrases within the intent.


3. The agent configuration can be tested with a set of training phrases.
 
4. DialogFlow shows the user expression that was interpreted and matched with the intent.

5. The agent's response based on the intent configuration.


