# MODULE 8
*Objectives*
- Describe AWS pricing and support models
- Describe the AWS Free Tier
- Describe key benefits of AWS Organizations and consolidated billing
- Explain the benefits of AWS Budgets
- Explain the benefits of AWS Cost Explorer
- Explain the primary benefits of the AWS Pricing Calculator
- Distinguish between the various AWS Support Plans
- Describe the benefits of AWS Marketplace

## AWS Free Tier
Three types of free offers
1. Always free - never costs money
2. 12 months free - free for 12 months
3. Trials - free for a limited amount of time

## AWS pricing concepts

### How AWS pricing works
- pay for what we use
- pay less when we reserve - some services offer reservation options that provide a significant discount compared to On-Demand Instance pricing
- pay less with volum-based discounts when we use more - some services offer tiered pricing, so the per-unit cost is incrementally lower with increased usage

The *AWS Pricing Calculator* lets you explore AWS services and create an estimate for the cost of your use cases on AWS.

### Examples
**Lambda**

We can save on AWS Lambda costs by signing up for a Compute Savings Plan, which offers lower compute costs in exchange for committing to a consistent amount of usage over a 1-year or 3-year term. This is an example of *paying less when you reserve*

**EC2**

We can significantly reduce Amazon EC2 costs by using Spot Instances. If a job can withstand interruption, using a Spot Instance would provide us with up to 90% savings while still meeting the availability requirements of the workload.

**S3**

For amazon S3 pricing, consider the following cost components:
1. Storage - we pay for the storage we use based on the objects' size, storage classes, and duration of storage time
2. Requests and retrievals - we pay for requests made to the objects and buckets
3. Data transfer - there is no cost to transfer data between different S3 buckets or from S3 to other services within the same region. However, we pay for data that we transfer into and out of S3, with a few exceptions.
4. Management and replication - we pay for the storage management features that we ahve enabled on our account's S3 buckets.

## Consolidated billing
When you set up an AWS Organization, you allow each department in the company to manage their own resources, but at the end of each month the company just gets one bill rather than however many departments have their own AWS account. Also, with an organization, we get bulk discount pricing - one account in the org might not have anough usage to qualify for discount pricing, but as an org it might push them over the line, as well as everyone else in the org. Thanks engineering.

## AWS Budgets
We can create budgets to plan our service usage, service costs, and instance reservation.

## AWS Cost Explorer
We can visualize, understand and manage our AWS costs and usage over time (12 months of data).

## AWS Support plans
Four tiers of support plans
- Basic - free, everyone gets this automatically. includes 24/7 customer service, docs, whitepapers, support forums, Trusted Advisor and AWS Personal Health Dashboard
- Developer - can email customer support directly with 24 hour response time, or 12 hours if your systems are impaired
- Business - Trusted Advisor provides full set of best practice checks, direct phone access to cloud support engineers with a 4 hour response SLA if systems imparied, and 1 hour for systems down, infrastructure event management assistance available for an extra fee
- Enterprise - 15 minute SLA for business critical workloads, dedicated Technical Account Manager (TAM), and Concierge Support team access.

a *TAM* proactively monitors our environment and assists with optimization and coordinates access to programs and AWS experts. They also provide Well-Architected Reviews.

Well-Architected Reviews are reviews to see if our systems stand up to the Well-Architected Framework, based on five pillars:
1. Operational Excellence
2. Security
3. Reliability
4. Performance Efficiency
5. Cost Optimization

## AWS Marketplace
Curated digital catalog that included thousands of software listings from independent software vendors.