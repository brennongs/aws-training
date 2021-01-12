# MODULE 5
*Objectives*
- Summarize the basic concept of storage and databases
- Describe the benefits of Amazon Elastic Block Store (EBS)
- Describe the benefits of Amazon Simple Storage Service (S3)
- Describe the benefits of Amazon Elastic File System (EFS)
- Summarize various storage solutions
- Describe the benefits of Amazon Relational Database Service (RDS)
- Describe the benefits of Amazon DynamoDB
- Summarize various database services

## Instance stores and EBS

### Instance stores
Block-level storage volumes behave like physical hard drives. An *instance store* provides temporary block-level storage for an EC2 instance. Because it is a physical drive attached to the instance, when the instance is terminated, we lose the data.

*EBS* allows you to persist data that is saved in instance stores, but interact with it in the same way. We can back up EBS data using *EBS Snapshots*.

## S3
*Object storage* is a storage strategy in which each object consists of data, metadata, and a key. The data might be an image, video, text, or file. Metadata contains information about what the data is, how it is used, the object size, etc. The key is a unique identifier.

S3 provides object-level storage. We upload any type of file to S3 (images, videos, text, etc), and set permissions to control visability and access, and Amazon handles keeping that object safe and secure.

### Storage clases
As with all AWS services, we only pay for what we use. S3 offers a range of storage classes to fit our business needs.

When selecting a class, consider the following
- How often will we retrieve our data?
- how available does our data need to be?

These are the available classes:
1. S3 Standard
- desigend for frequently used data
- stores data in a minimum of three AZs

S3 Standard offers high availability and comes with 11 nines of durability (99.999999999% probability that data will remain intact over after a year). It is the most expensive of the classes

2. S3 Standard-IA
- ideal for infrequently accessed data
- similar to S3 Standard but has a lower storage price and higher retrieval price

Because of it's lower storage price, this is useful for data that needs infrequent usage, but high availability for when it is used. It offers the same availability as S3 Standard.

3. S3 One Zone-IA
- stores data in a single AZ
- Has a lower storage price than S3 Standard-IA

Because of the single AZ (compared to three AZs in the standard classes), this is a strong consideration if we want to save costs on storage and we can easily reproduce the data.

4. S3 Intelligent-Tiering
- ideal for data with unknown or changing access pattern
- requires a small monthly monitoring and automation fee per object

S3 will monitor your objects' usage patterns. If you haven't accessed an object for 30 days, S3 automatically moves it to S3 Standard-IA. If you access an object in the inrequent access tier, S3 automatically moes it to S3 Standard.

5. S3 Glacier
- low-cost storage designed for data archiving
- able to retrive objects within a few minutes to hours

S3 Glacier is a low-cost storage class that is ideal for data archiving.

6. S3 Glacier Deep Archive
- lowest-cost object storage class ideal for archiving
- able to retrieve objects within 12 hours

Good for very long term storage, like audit documents. Very cheap, but very long retrieval time.

### Comparing EBS and S3
S3 is great for web apps that require high amounts of persisted storage. The example they use in the video is a photo analysis site that finds animals in photos that are uploaded by users. The training data for this could be housed in S3 -- millions of animal pictures that all need to be indexed and viewed by thousands of people at once.

EBS is useful for on board processing that gets interrupted. Their example is an 80GB video file that you're making edit corrections on. When you make an edit to one scene in the film and save that change, the engine only updates the blocks where those bits live. If we used S3 for this, then S3 would save the _entire file_ every time an edit was made and saved.

## EFS
*File storage* is a storage strategy where multiple clients can access data that is stored in shared file folders through file paths -- like through smb.

*EFS* is a scalable file system used with AWS Cloud services and on-prem resources. As you add and remove files, EFS grows and shrinks automatically -- up to petabytes.

### Comparing EBS and EFS
EBS works in a single AZ -- in order to attach an EC2 instance to an EBS volume, they must be in the same AZ

EFS is a regional service. It stores data in and across multiple AZs. This allows you to access data concurrently from all the AZs in the region where a file system is located. Additionally, on-prem servers can access EFS using AWS Direct Connect.

## RDS
*Relational databases* store data in a way that relates it to other pices of data. They use SQL to store and query data, allowing data to be stored in an easily understandable, consistent, and scalable way.

*RDS* is a service that allows you to run managed relational databases in the cloud, meaning that we don't have to bother with upgrades, hardware provisioning, setup, patching or backups.

*Aurora* is an enterprise-class relational database. It is compatible with MySQL and PostgreSQL. It operates much faster than both, and it cuts costs by reducing unnecessary IO operations while retaining high availability. It also replicates six copies of our data across three AZs and backs up to S3 continuously.

## DynamoDB
*Nonrelational databases* store data in tables, often in the form of key-value sets like JSON or Redis. 

*DynamoDB* is akey-value database service that offers single-digit milisecond performance at any scale. It is serverless and auto-scaling.

### Comparing RDS and DynamoDB
RDS works well for any business analytics problem because of complex relational joins.

DynamoDB works for well for everything else. Contact lists, lookup tables, anything that doesn't need the relational connections. Even for a social media site, unless you are trying to discover trends in who friends whom, relational database is overkill because of it's complexity and overhead.

## Redshift
When data complexity breaks out of the capabilities of traditional relational databases, you need a data warehouse. This is when you're storing dissimilar data across multiple databases, and you want to run a join across those databases to find connections. Data warehouses are good for analyzing historical data. Once the data has been set and used, it moves into a data warehouse.

*Redshift* is a managed, autoscaling data warehouse solution. Too much info for this course to handle.

## DMS
*AWS Database Migration Service (DMS)* enables you to migrate relational databses, nonrelational databases, and other types of data stores to other sources.

## Additional database services
1. Amazon DocumentDB - supports MongoDB workloads
2. Amazon Neptune - graph database service
3. Amazon Quantum Ledger Database (QLDB) - ledger database
4. Amazon Managed Blockchain - decentralized ledger database
5. Amazon ElastiCache - adds caching layers on top of your databases to improve the read times of common requests. works with Redis and Memcached
6. Amazon DynamoDB Accelerator (DAX) - in memory cache for DynamoDB.