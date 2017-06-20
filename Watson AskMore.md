
##Chatbot mechanism
```sequence
Salesforce->Heroku: Question
Heroku->Professional Watson: Question
Professional Watson->Heroku: Answer
Heroku-->Chitchat Watson: Question (if no match answer)
Chitchat Watson-->Heroku: Chitchat response
Heroku->Salesforce: Response
```







---








##How to deal with unclear question?
```flow
start=>start: Conversation Start
end=>end: Response to User
greeting=>operation: Chatbot :May I help you?
Q1=>operation: User :(Question)
Ans=>operation: Find an appropriate answer
AskMore=>operation: Chatbot :Which product?
AnsProduct=>operation: User :(Product)

cond=>condition: contains 
product name?

AddProduct=>inputoutput: Make a new question 
by adding product name

start->greeting->Q1->cond
cond(yes)->Ans->end
cond(no)->AskMore()->AnsProduct->AddProduct(right)->cond
```