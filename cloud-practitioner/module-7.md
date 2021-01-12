# MODULE 7
*Objectives*
- Summarize approaches to monitoring your AWS environment
- Describe the benefits of Amazon CloudWatch
- Describe the benefits of AWS CloudTrail
- Describe the benefits of AWS Trusted Advisor

## Amazon CloudWatch
*Monitoring*: observing systems, collecting metrics, and then using data to make decisions

*CloudWatch* is a web service that enables you to monitor and manage various metrics and configure alarm actions based on data from those metrics. CloudWatch integrates with most AWS services, and with custom alarms, you can set off actions such as triggering a Lambda or sending a text message. 

## AWS CloudTrail
API-powered auditing tool. Every request gets logged in the CloudTrail engine: what happened? who made the request? when? how was the request made? what was the response? did anything change? Then filter the logs to assist with operational analysis and troubleshooting.

## AWS Trusted Advisor
Web service that inspects your AWS environment and provides real-time recommendations in accordance with AWS best practices. Five pilars:
1. cost optimazion
2. performance
3. security
4. fault tolerance
5. service limits

basically another thing like Bridgecrew but checks more than just security.