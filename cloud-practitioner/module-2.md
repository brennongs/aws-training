# MODULE 2
*Objectives*
- Describe the benefits of Amazon EC2 at a basic level
- Identify the different Amazon EC2 instance types
- Differentiate between the various billing options for Amazon EC2
- Summarize the benefits of Amazon EC2 Auto Scaling
- Summarize the benefits of Elastic Load Balancing
- Give an example of the uses for Elastic Load Balancing
- Summarize the differences between Amazon Simple Notification Service (SNS) and Amazon Simple Queue Service (SQS)
- Summarize additional AWS compute options

## Introduction
*Elastic Compute Cloud*, or *EC2* is AWS's bread and butter. Pretty much everything offered by AWS is built on EC2. This is the service that we use to gain access to virtual servers in AWS.

## EC2 Instance Types

### General Purpose
Balanceed for compute, memory, and networking resources. Good for application servers, gaming servers, enterprise web servers, and small/medium databases

### Compute Optimized
High performance processors, good for batch computing or threading (probably?)

### Memory Optimized
Works like it sounds, good for memory-focused computing like preprocessing data, and memory-based dbs like Redis

### Accelerated Compute
Comes with hardware accelerators, or coprocessors. Good for heavy arithmatic and scientific computing, as well as graphics processing

### Storage Optimized
focused on high IOPS (input/output operations per secont). Good for transaction processing, data warehouses, and distributed file systems

## Pricing

### On-Demand
"Ideal for short-term, irregular workloads that cannot be interrupted." these instances will run until we stop them, and we will be billed for all the uptime

### EC2 Savings Plan
"Up to 72%" cheaper than ON-Demand. Requires a 1-year or 3-year commitment for a specified amount o usage. All compute usage up to the usage commitment will be charged at the discount price. Everything over that is charged On-Demand pricing.

### Reserved Instances (RI)
Billing discount on On-Demand instances. We purchase (outright?) reserved instances for 1 or 3 years. At the end of the term, we continue paying On-Demand prices until we terminate the instance or purchase a matching plan

#### RI Types:
- Standard: Big discount (up to 72% off On-Demand prices)
- Convertible: Smaller discount (up to 54%), but can be upgraded
- Scheduled: Available to launch in the time windows you reserve

### Spot Instances
"Ideal for workloads with flexible start and end times, or that can withstand interruptions." Up to 90% cheaper than On-Demand. Spot instances slurp up whatever leftover resources it can find. If there are no available resoureces, it waits to start until some open up.

### Dedicated Hosts
Most expensive option, only really useful for compliance purposes.

## Scaling
*Scalability*: the ability to begin with only the resources you need and resopnd to changing demand by adding or removing resources to meet usage or save money

*Auto Scaling*: being able to scale automatically without manually managing resources

AWS offers two types of auto scaling: *dynamic scaling* and *predictive scaling*.

- *dynamic scaling* responds to changing demand.
- *predictive scaling* preemptively schedules the right number of resources based on predicted demand.

When setting up an **auto scaling group** you can define parameters. *Minimum* sets the minimum number of resources that should always be running. *Desired* is an optional parameter that dictates how many instances should be running at a given time (if not set, *minimum* is used). *Maximum* sets the upper bound -- there will never be more than <*maximum*> instances running, even if all instances are totally maxed out. With these three parameters, AWS will automatically add or remove instances up to maximum and down to minimum or desired.

## Elastic Load Balancing
*Elastic Load Balancer* or *ELB* automatically distributes incoming traffic across multiple sources. It acts as a single point of contact for all incoming web traffic to our auto acaling group. Auto scaling groups and ELB are technically separate services, but they work together to keep things running smoothly; as the auto scaling group adds more instances, ELB will automatically add them to the queue of available resourcesa nd start sending them traffic.

## Messaging and Queuing
*Monolith*: an application with tightly coupled architecture, usually all housed on a single server

*Microservices*: design pattern wherein you break apart your application into compmletely separate and independant components

*pub/sub*: subscribers subscribe to publishers. when publishers detect a change, they push a notification to their entire subscriber list. this is useful for when many entities in the system need to keep tabs on changes

*message queue*: publishers add messages or tasks to a queue when they need them done. When subscribers become free, they grab the next message or task off the queue and finishes it. This is useful for asynchronous task processing

*Simple Notification Service*: pub/sub service (SNS)

*Simple Queue Service*: message gueuing service (SQS)

The main problem of monoliths is that they aren't very effective to scale. In order to scale them up, you have to add another instance of the _entire application_ - even if only one piece of the aplication is the bottleneck. 

This is where microservices shine. If there is a specific piece of the application which is holding everything up, you can add more of _just that part_ until usage dies back down.

However, microservices need to be constantly communicating in order to stay in sync with each other. That's where services like SQS and SNS come in.

## Additional Services
*Serverless*: code runs on servers that you don't have to maintain

### Lambda
Lets us run code without provisioning servers. We pay only for the compute time we consume.

upload code to lambda -> set up triger -> function runs when triggered -> we pay for invocation time

### Containers
- Elastic container Service - Docker
- Elastic Kubernetes Service - K8s
- Fargate - Compute engine for ECS and EKS
