IBM Watson Conversation Service
=====================

[toc]

---
## Workspace

### Intent
An *intent* is a purpose or goal expressed in a customer's input, such as answering a question or processing a bill payment. By recognizing the intent expressed in a customer's input, Conversation can choose the correct dialog flow for responding to it.

#### example
Gather as many **actual customer questions, commands, or other inputs** as possible. Using input from real users gives a better picture of the expected input than having experts create lists of possible utterances. Remember that customers might phrase the same kind of request in many different ways. For example, the following examples all represent requests for weather information:

* Tell me the current weather conditions.
* Is it raining?
* What's it like outside?
#### counterexample
*Counterexamples* are examples that have been marked as irrelevant input.
### Entity

#### value

#### synonym

### Dialog

#### node

##### condition

##### response

##### context


## Problems and Solutions
### Problem 1: Invalid Request Body, Code: 400
Got  error message **Invalid Request Body, Code: 400** when used *conversation.create_intent*


```python
from watson_developer_cloud import ConversationV1
intent="Henry Testing"
create_intent=conversation.create_intent(
              workspace_id=workspace_viola,
              intent=intent)
print create_intent
```
>raise WatsonException(error_message)
Watson_developer_cloud.watson_developer_cloud_service.WatsonException: Error: Invalid Request Body, Code: 400

### Solution 1: Check if the *intent* is valid
*Intent* cannot include space, for example, "Henry Test" is invalid while "HenryTest" is valid.

### Problem 2: Dialog can't go to the correct node.
WCS(Watson Conversation Service) have detected the correct intent and entity, but didn't go to the correct node.

### Solution 2: Check the sequence of sibling nodes.
Because *Conversation* will check if the condition is satisfied from top to bottom, the node with stricter condition should be placed above the looser node, otherwise the stricter one cannot be checked.
