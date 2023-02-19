# Week 0 — Billing and Architecture
## Required Homework/Tasks
- I have applied all the configurations in github that allow me to use the aws cli and verified that it works. <br />
- created and configured AWS credentials with necessary security settings like MFA. <br />
- recreated the logic diagram in Lucid, please see screenshot and link below for your reference  <br />
![logical diagram](/journal/assets/Logical-diagram.PNG) <br />

[Lucid charts share link for your reference](https://lucid.app/lucidchart/99c9e132-611f-4a56-bbfd-ff81e87b42b6/edit?viewport_loc=-380%2C-688%2C2220%2C1088%2C0_0&invitationId=inv_1b8bb36b-e9d0-4fc0-9674-17aefc62979b) <br />

- I recreated the conceptual diagram in napkin, please see screenshot below for your reference <br />
![Conceptual napkin diagram](/journal/assets/Conceptual-napkin-diagram.PNG)<br />

- I set up a Billing alarm and Budget based on what I think I can afford to pay, please see screenshot below for your reference. <br />
![Budgets](/journal/assets/Budgets.PNG) <br />
![Billing-Alert](/journal/assets/Billing_Alert.PNG) <br />

## Example of referencing a file in the codebase
[An example of the reference file in my repo](/aws/json/budget-notifications-with-subscribers.json) aws/json/budget-notifications-with-subscribers.json <br />

##The command I used for SNS subscription
```sns
!--- This command returns TopicArn
aws sns create-topic --name Billing_Alart 
!--- Then run the following commands
aws sns subscribe \
    --topic-arn="arn:aws:sns:us-east-1:403838582332:Billing_Alart" \
    --protocol=email \
    --notification-endpoint=damtewyoseph@gmail.com
!--- Finally run the following command
aws cloudwatch put-metric-alarm --cli-input-json file://aws/json/alarm-config.json
```
## To creat a aws budget and budget notification
```buget
aws budgets create-budget \
    --account-id 403838582332 \
    --budget file://aws/json/budget.json \
    --notifications-with-subscribers file://aws/json/budget-notifications-with-subscribers.json
```
## To get caller identity
```
aws sts get-caller-identity
```
## To export AWS_ACCESS_KEY and AWS_SECRET_ACCESS_KEY
```
export AWS_ACCESS_KEY_ID="xxxxx"
export AWS_SECRET_ACCESS_KEY="yyyy"
export AWS_DEFAULT_REGION="us-east-1"
export AWS_ACCOUNT_ID="123456789102"
...
gp env AWS_ACCESS_KEY_ID="xxxxx"
gp env AWS_SECRET_ACCESS_KEY="yyyy"
gp env AWS_DEFAULT_REGION="us-east-1"
gp env AWS_ACCOUNT_ID="123456789102"
```



