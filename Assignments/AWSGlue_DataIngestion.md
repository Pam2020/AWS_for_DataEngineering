# Data Ingestion Lab

## System Design

![SystemDesign](https://github.com/Pam2020/AWS_for_DataEngineering/blob/c35e4d3cc0d699abb2e3f2037be6217396a6dccd/Images/SystemDesign_AWSGlue.png)

### Reverse engineering: Analysis of the system design

The goal is to ingest data using AWS Glue (ETL tool by AWS). To ingest data we use the Glue crawler to crawl the files and create a reference table. Here is the reverse engineering process:

1. In order to crawl data stored in S3, we create a crawler that can access the S3 buckets and store the schema in a reference table that can be used for easy querying in athena or perform transformations using Glue jobs. When creating the crawler, we give a name, add the S3 location that needs to be crawled, attact the role and the target database. We can run the crawler on demand or we can schedule it daily, weekly, monthly or customize it.
   
2. Before that for the crawler to be able to access data in S3 buckets, we create an IAM Service role that Glue can use. We attach the AWSGLUESERVICEROLE policy and a custom policy that provides access to the particular S3 buckets. In the custom plocy, we edit the policy permissions JSON file by giving access to the particular S3 bucket location.
  
3. Before this, we create S3 buckets and add files from our local machine into AWS Cloud.

### JSON version of the Policy expalined

![JSON](https://github.com/Pam2020/AWS_for_DataEngineering/blob/78f77e1cc9e9cc570278b48f7d5fa1867ab7f970/Images/JSONnew.png)

1. **Version**: Gives the version of the policy, different versions are stored in aws for version control

2. **Statement**: This is the main element of the policy, this contains multiple sets of (action, resource and effect...generally written in the form "Statement": [{...},{...},{...}]) which gives the effect/permission for the given actions on the given reosurce

- **Action**: Action key value contains all the actions that are allowed to be performed by the Service that is using the policy
- **Resouce**: This key value gives the arn information of the sources that can be accessed by the service/role
- **Effect**: This is the permission - allow or deny
