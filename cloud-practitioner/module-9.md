# MODULE 9
*Objectives*
- Understand migration and innovation in the AWS Cloud
- Summarize the AWS Cloud Adoption Framework (CAF)
- Summarize the six key factors of a cloud migration strategy
- Describe the benefits of AWS data migration solutions, such as AWS Snowcone, AWS Snowball, and AWS Snowmobile
- Summarize the broad scope of innovative solutions that AWS offers

## AWS Cloud Adoption Framework
**Six core perspectives of the CAF**
1. Business - ensures that IT aligns with business needs and that IT investments link to key business results. Create a strong business case for cloud adoption and prioritize cloud adoption initiatives. Ensure that our business strategies and goals align with our IT strategies and goals.
2. People - supports development of an organization-wide change management strategy for successful cloud adoption. Evaluate organization structures and roles, new skill and process requirements, and identify gaps. Prioritize training, staffing, and organizational changes.
3. Governance - focuses on the skills and processes to align IT strategy with business strategy. Understand how to update the staff skills and processes necessary to ensure business governance in the cloud. Manage and measure cloud investments to evaluate business outcomes.
4. Platform - includes principles and patterns for implementing new solutions on the cloud, and migrating on-prem workloads to the cloud. Use a variety of architectural models to understand and communicate the structure of IT systems and their relationships. Describe the architecture of the target state environment in detail.
5. Security - ensures that the organization meets security objectives for visibility, auditability, control, and agility. Use the CAF to structure the selection and implementation of security controls that meet the organization's needs.
6. Operations - helps to enable, run, use, operate, and recover IT workloads to the level agreed upon with your business stakeholders. Define how day-to-day, quarter-to-quarter, and year-to-year business is conducted. Align with and support the operations of the business. The CAF helps these stakeholders define current operating procedures and identify the process changes and training needed to implement successful cloud adoption.

## Migration strategies

### the 6 R's of migration
1. Rehosting (lift and shift) - just migrate, no optimization
2. Replatforming (lift, tinker, and shift) - make only some cloud optimization
3. Refactoring - rewrite the new code in the cloud and optimize
4. Repuchasing - end old contracts and replacing them, typically in favor of cloud implementations
5. Retaining - don't change them, maybe the end of life is soon. Only migrate what makes sense for your business
6. Retiring - destroy it if it's unnecessary

## AWS Snow Family
Physical devices that allow us to migrate data quicker - skipping the bandwidth problem.
### Snowcone
Small, rugged, and secure edge computing and data transfer device. 2 CPUs, 4GB of memory, and 8TB of usable storage.

### Snowball
Two types of devices:
1. Snowball Edge Storage Optimized - large-scale data migrations and recurring transfer workflows. 80TB of HDD capacity for block volumes and Amazon S3 compatible object storage, and 1TB of SATA SSD for block volumes. 40 vCPUs, and 80GiB memory to support EC2 sbe1 instances.
2. Snowball Edge Compute Optimized - powerful computing resources for machine learning, full m otion video analysis, analytics. 42-TB usable HDD capacity for S3 compatible object storage or EBS compatible block volumes and 7.68TB of usable NVMe SSD capacity for EBS compatible block volumes. 52 vCPUs, 208 GiB memory, and an optional NVIDIA Tesla V100 GPU. Devises run EC2 sbe-c and sbe-g instances.

### Snowmobile
Exabyte-scale data transfer service used to move large amounts of data to AWS. Can transfer up to 100PB of data per Snowmobile. 45-foot long ruggedized shipping container, pulled by a semi truck.

## Innovation with AWS
Lots of other services in AWS that haven't been mentioned yet. We can build basically whatever we want, but we need to nail down what it is we actually want to build. Ask ourselves:
- The current state
- The desired state
- Theh problems you are trying to solve
