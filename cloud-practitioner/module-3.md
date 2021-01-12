# MODULE 3
*Objectives*
- Summarize the benefits of the AWS Global Infrastructure
- Describe the basic comcept of Availability Zones
- Describe the benefits of Amazon CloudFront and edge locations
- Compaire different methods for provisioning AWS services

## Introduction
AWS's global infrastructure allows us to acheive extremely high availability at an infintismally small fraction of the cost.

## AWS Global Infrastructure
When you provision resources in AWS, the first decision we must make is which *region* we will run our instances in.

A *region* is a geographical area where lots of traffic occurs (Paris, New York, Tokyo, London, etc). They are labeled in this format: `<region>-<area>-<number>` (for example, `us-east-1`, which refers to the Pacific Northwest of the United States, or `ap-northeast-1`, which refers to Tokyo).

There are a few considerations to make when choosing a region in which to operate.

1. Compliance: if our business depends on certain compliances, then we have to follow them to stay in business. If one of our compliances is that we have to operate in a specific geographical area - like a country, for example - then our region choices are limited to those in that area.
2. Proximity: latency is still a thing, so we should pick a region closer to your consumer base.
3. Feature Availibility: not all regions are created equal. Features are rolled out as fast as possible, but AWS can't guarantee feature parity across all regions.
4. Pricing: taxes make some regions cost more or less than other regions.

Each region is made up of multiple *availability zones*, or *AZ*'s. An availablity zone is one or more data centers which each house lots of resources. AZs are built far apart so that in the event of a natural disaster or other unpredicted calamity, we have a better chance of remaining available.

It is important to note that some resoureces work on a region level and some work on the AZ level. If a resource is on the region level, it is accessible to all AZs in the region.

## Edge Locations
*CloudFront*: AWS CDN provider

An edge location is a physical site that uses Amazon CloudFront to store cached copies of your content closer to your customer for faster delivery.

## How to manage and provision resources
There are three ways to interact with AWS

### AWS Console
Point and click in the UI offered at https://console.aws.com.

### AWS CLI
```shell
$ brew install aws-cli
```
Can be used to write scripts that provision resources for you based on triggers, but for the most part is still a manual interaction.

### AWS SDKs
Work with AWS in your language of choice.
```shell
$ npm i aws-sdk
```

### Infrastructure as Code
*Elastic Beanstalk*: deploys AWS resources ased on configuration settings

*CloudFormation*: AWS version of Terraform

The safest (fault tolerant) and easiest way to interact with AWS is through config files fed to either AWS directly or to something like Harness.io. Reasons for this are many. To list a few:
- easier to debug
- easier to learn/reason about
- easier to test
- easier to share