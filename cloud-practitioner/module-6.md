# MODULE 6
*Objectives*
- Explain the benefits of the shared responsibility model
- Describe multi-factor authentication (MFA)
- Differentiate between the AWS Identity and Access Management (IAM) security levels
- Explain the main benefits of AWS Organizations
- Describe security policies at a basic level
- Summarize the benefits of compliance with AWS
- Explain additional AWS security services at a basic level

## Shared Responsibility Model
The *shared responsibility model* is how AWS separates responsibilities between itself as the service provider, and the customer as the developer of applications and platforms. It dictates that AWS is responsibility of the security _of_ the cloud -- the global infrastructure and foundation services -- while the customer is responsibile for security _in_ the cloud -- their own platforms and app data, operating systems, firewalls, encryption etc.

Like a house, the builder is resonsible for building walls that are sturdy and a door that can keep us safe, but it is our job as the home owner to close and lock the doors and windows.

**AWS** handles the physical layer, the network and the hypervisors. **Customer** handles the OS, applications and data.

## User permissions and access
*Principle of least privilege*: A user is granted access only to what they need, and nothing more

*Multi-factor authentication (MFA)*: Using more than one method to authenticate a user, for example a username/password and a text code

***DON'T USE THE ROOT USER***

*AWS Identity and Access Management* or *IAM* enables you to manage access to AWS services and resources securely. All IAM users start life with zero permissions, according to the principle of least privlage. We have to explicitely grant premissions to every account. 

This is why policies and groups are so nice. We can set up policies for groups of things we want to allow, and then attach them to groups, thereby allowing a group certain permissions. Then, whenever a new person joins the organization, rather than explicitly allowing them all the necessary permissions one by one, we just add them to whatever group they ought to belong to.

IAM roles are cool, they are like users but have no authentication. They have associated permissions which can be allowed or denied, and can be assigned for temporary periods of time that allow temporary permissions. Good for managing permissions of bots. When a user assumes a role, all their previous permissions are forgotten for the duration of that role, and are only given the permissions of the role until they doff the role again.

Can also federate users into your AWS Org, wherein employees would use their company credentials to access AWS.

## AWS Organizations
*AWS Organizations*: A central location to manage multiple AWS accounts

### Organizational Units
In AWS Organizations you can group accounts into organizational units (OUs) to manage accounts with similar requirements. They're like super groups. Organization -> Account, OU -> Group, Account -> User.

In AWS Organizations you can centraly control permissions for the accounts in your org by using *service control policies* or *SCP*s, which enable you to place restrictions on the AWS services, resources, and actions that users and roles in each account can access.

## Compliance
*AWS Artifact* is a service that provides on-demand access to AWS security and compliance reports and select online agreements. There are two parts to what Artifact offers.
1. Agreements - If our company needs to sign an agreement with AWS regarding our use of certain tkypes of information throughout AWS, we can find the agreement through Artifact Agreements.
2. Reports - third-party audits of AWS services. We can provide these reports to our auditors, though they only cover the physical, network and hypervisor pieces of our infrastructure. What we build is still up to us, and it's still up to us to make sure that our OS, applications, and data remain compliant if necessary.

### Customer Compliance Center
The *customer compliance center* contains resources to help y ou learn more about AWS compliance as well as any relevant whitepapers. They also provide an *auditor learning path*, designed fro individuals in auditing, compliance, or legal roles who want to learn more about acheiving compliance using AWS.

## Denial-of-service attacks
A well architected system built on AWS is already protected against DDoS attacks. ELB works on the regional level and distributes web traffic to available resources. Security groups only allow proper traffic, working at the network level, effectively staggering the attack across the entire AWS Region.

For really sofisticated attacks, AWS offers *Shield with WAF*. Using machine learning, it recognizes bad actors and automatically blacklists them.

### AWS Shield
A service that protects agains DDoS attacks with two levels of security.
1. Standard - a free service that automatically protects all AWS customers at no cost. It protects from the most common types of DDoS -- in real time.
2. Advanced - a paid service which provides attack diagnostics and detection of sophsticated DDoS attacks. It also integrates with other services (CloudFront, Route 53, ELB). Can also be combined with AWS WAF by writing custom rules to mitigate complex DDoS attacks.

## Additional security services
*Encryption*: Securing a message or data in a way that only authorized parties can access it

- AWS Key Management Service (KMS) - enables you to perform encription operations through tthe use of crypto keys. Can use KMS to create, manage, and use keys, as well as control rules for their usage "across a wide range of services"
- AWS WAF - web application firewall which lets you monitor network requests; works together with CloudFront and ALB. Works in a similar way to network ACLs, but on the web level to protect your AWS resources. Looks like a smart IP whitelist
- Amazon Inspector - essentially BridgeCrew but for AWS only; runs automated security assessments and provides us with a list of security findings prioritized by security level and offers recommendations for fixing it
- Amazon GuardDuty - provides intelligent threat detection for our AWS infrastructure and resources
