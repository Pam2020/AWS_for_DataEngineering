# Data Transformation Lab

## Work Flow:

1. Store the data files in S3 buckets: We have two csv files. Store both these files in different folders in an S3 bucket. 
2. Set S3 bucket access permissions for the IAM Glue Service role that we created before. 
3. Create two different crawlers to crawl the two different s3 locations where these two files are stored. We use the same IAM role for both.
The crawled data is stored in two different tables in the same database. 
3. Create a visual Glue job as follows:
- Choose the reference tables in the Data catalog (created with the help of crawlers), we have two different sources for the two different files.
- Use a JOIN transformation to join these two tables, choose inner join as the type of join and choose the primary key equal to right primary key as the join condition. 
- When joining, as the two tables have common columns, the columns of one of the tables are tagged using the change schema transformation - right resolve the table.
