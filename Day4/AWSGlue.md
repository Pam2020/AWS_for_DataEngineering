## Data Ingestion Lab

### Systen Design

![SystemDesign](https://github.com/Pam2020/AWS_for_DataEngineering/blob/main/Day4/SystemDesign_AWSGlue.png)

#### Reverse engineering: Analysis of the system design

The goal is to ingest data using AWS Glue (ETL tool by AWS). To ingest data we use the Glue crawler to crawl the files and create a reference table. Here is the reverse engineering process:

1. In order to crawl data stored in S3, we create a crawler that can access the S3 buckets and store the schema in a reference table that can be used for easy querying in athena or perform transformations using Glue jobs.
2. Before that for the crawler to be able to access data in S3 buckets, we create an IAM Service role that Glue can use. We attach the AWSGLUESERVICEROLE policy and a custom policy that provides access to the particular S3 buckets.
3. Before this, we create S3 buckets and add files from our local machine into AWS Cloud.

#### JSON version of the Policy expalined

![JSON](https://github.com/Pam2020/AWS_for_DataEngineering/blob/main/Day4/JSON.png)

1. Version: Gives the version of the policy, different versions are stored in aws for version control

2. Statement: This is the main element of the policy, this contains multiple sets of (action, resource and effect...generally written in the form "Statement": [{...},{...},{...}]) which gives the effect/permission for the given actions on the given reosurce

- Action: Action key value contains all the actions that are allowed to be performed by the Service that is using the policy
- Resouce: This key value gives the arn information of the sources that can be accessed by the service/role
- Effect: This is the permission - allow or deny
