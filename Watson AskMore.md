##Chatbot mechanism
```sequence
Salesforce->Heroku: Question
Heroku->Watson: Question
Watson->Heroku: Answer
Heroku-->Chitchat: if detect chitchat
Chitchat-->Heroku: Chitchat response
Heroku->Salesforce: Response
```


##How to deal with unclear question?
```flow
st=>start: Conversation Start
e=>end: Response
greeting=>operation: Chatbot :May I help you?
Q1=>operation: User :(Question)
Ans=>operation: Find an appropriate answer
AskMore=>operation: Chatbot :Which product?
AnsProduct=>operation: User :(Product)
cond=>condition: contains 
product name?
AddProduct=>inputoutput: Make a new question 
by adding product name
st->greeting->Q1->cond
cond(yes)->Ans->e
cond(no)->AskMore()->AnsProduct->AddProduct(right)->cond
```