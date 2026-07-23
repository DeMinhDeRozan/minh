____________________________Reminding You - My Bro v.1.0.0____________________________
This is my fun serverless project using AWS services and html+css+js elements.


To try this, just type what you will have to do later(I mean in next hour or next minutes), and JUST 1 TASK please! More than 2 tasks at the same time costs too many tokens, and sometimes the model becomes a fool. Then just wait for the alert.


Overall, this static website is hosted on S3, connected to AWS services through API Gateway. While Lambda calls Bedrock( I use Claude Sonnet 4.5) to process the messages and save them in DynamoDB.


The data includes ID, AlertTime, TimeCreated, Status, and TotalToken. The important attributes are AlertTime(time to remind), Status(check if already reminded) and TotalToken.


To prevent the abuse of token, I put a rule in Lambda function to check if the total number of used tokens reaches the set limit. Once it reaches, any subsequent requests from users will be refused until the next day. However, as I said the number of free daily token is limited, so some users may be refused to use this reminder again.


Every 1 minute, AWS EventBridge will trigger Lambda to query the DynamoDB database to check which record is ready for alerting. Once ready, Lambda will send the alert through API Gateway to the S3 website again, the message will appear on the page with a funny Aussie sound.


Transformation to serverless to real server(on EC2) may be conducted soon, together with monitoring tools and DevOps use.


Thanks for trying. 


DeMinh DeRozan
