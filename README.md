<h1 align="center">🚀 Reminding You - My Bro v.1.0.0 🚀</h1>

<p align="center">
  <img src="./asset/icons8-aws.svg" width="45" title="Amazon Web Services" alt="AWS" /> &nbsp;&nbsp;
  <img src="./asset/Lambda.svg" width="45" title="Amazon Lambda" alt="Lambda" /> &nbsp;&nbsp;
  <img src="./asset/DynamoDB.svg" width="45" title="Amazon DynamoDB" alt="DynamoDB" /> &nbsp;&nbsp;
  <img src="./asset/EventBridge.svg" width="45" title="Amazon EventBridge" alt="EventBridge" /> &nbsp;&nbsp;
  <img src="./asset/Simple Storage Service.svg" width="45" title="Amazon S3" alt="S3" /> &nbsp;&nbsp;
  <img src="./asset/API Gateway.svg" width="45" title="Amazon API Gateway" alt="API Gateway" /> &nbsp;&nbsp;
  <img src="./asset/aws-bedrock-icon.svg" width="45" title="Amazon Bedrock" alt="Bedrock" />
  <img src="./asset/claude-color.svg" width="45" title="Claude Sonnet 4.5" alt="Claude" />
</p>

---

This is my fun serverless project using AWS services and html+css+js elements.

To try this, just type what you will have to do later (I mean in next hour or next minutes), and **JUST 1 TASK** please! More than 2 tasks at the same time costs too many tokens, and sometimes the model becomes a fool. Then just wait for the alert.

---

### 🏗️ Architecture Overview

Overall, this static website is hosted on S3, connected to AWS services through API Gateway. While Lambda calls Bedrock (I use Claude Sonnet 4.5) to process the messages and save them in DynamoDB.

The data includes `ID`, `AlertTime`, `TimeCreated`, `Status`, and `TotalToken`. The important attributes are `AlertTime` (time to remind), `Status` (check if already reminded) and `TotalToken`.

---

### 🛡️ Cost Control & Automation

To prevent the abuse of token, I put a rule in Lambda function to check if the total number of used tokens reaches the set limit. Once it reaches, any subsequent requests from users will be refused until the next day. However, as I said the number of free daily token is limited, so some users may be refused to use this reminder again.

Every 1 minute, AWS EventBridge will trigger Lambda to query the DynamoDB database to check which record is ready for alerting. Once ready, Lambda will send the alert through API Gateway to the S3 website again, the message will appear on the page with a funny Aussie sound.

---

### 🔮 Future Roadmap

Transformation to serverless to real server (on EC2) may be conducted soon, together with monitoring tools and DevOps use.

Thanks for trying. 

<div align="right">
  <b>DeMinh DeRozan</b>
</div>
