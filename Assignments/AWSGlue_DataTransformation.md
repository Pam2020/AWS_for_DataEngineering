## Data Transformation Lab

### Work Flow:

**Step 1**: 

Store the data files in S3 buckets: We have two csv files. Store both these files in different folders in an S3 bucket. 

**Step 2**:

Set S3 bucket access permissions for the IAM Glue Service role that we created before. 

**Step 3**: 

Create two different crawlers to crawl the two different s3 locations where these two files are stored. We use the same IAM role for both.
The crawled data is stored in two different tables in the same database.

**Step 4**: 

Create a visual Glue job as follows:
- Choose the reference tables in the Data catalog (created with the help of crawlers), we have two different sources for the two different files.

![](https://github.com/Pam2020/AWS_for_DataEngineering/blob/ceb0012dc7de2913978671d14d4de1782afd3aaa/Images/Source_join.png)


- Use a JOIN transformation to join these two tables, choose inner join as the type of join and choose the primary key equal to right primary key as the join condition.

![](https://github.com/Pam2020/AWS_for_DataEngineering/blob/353c59a5fdb5e51fb17b7a9ab0966ec2d047f097/Images/Join_conditions.png)


- When joining, as the two tables have common columns, the columns of one of the tables are tagged using the change schema transformation - right resolve the table.

- To remove null fields the remove null rows transform was used, but this only removes rows with all fields null.

![](https://github.com/Pam2020/AWS_for_DataEngineering/blob/3801d6398e396dc37669adb12b35d426d3e85cd0/Images/Join_nullrows.png)


- Now, the conditional router is used to split the resultant dataset into two different tables based on the condition year < 2000.

![](https://github.com/Pam2020/AWS_for_DataEngineering/blob/cf43857afc9e222587ca068b95864dcd1497bf00/Images/DefiningCR.png)

- The output data and default data are stored in two seperate folders in S3 as parquet files, the data catalog is also updated with the new tables.

![](https://github.com/Pam2020/AWS_for_DataEngineering/blob/c3f8181bb33e8f0ff0730adf06580ce885c42e6e/Images/ConditionalRouter.png)

- These tables are queried in athena to check if the transformations and conditions are applied correctly.

**Resultant table - Year greater than 2000**

![Greater than 2000](https://github.com/Pam2020/AWS_for_DataEngineering/blob/e0d8e67320a8c71d1b04fe94de8d4ba189668255/Images/Result_greaterthan.png)

**Resultant table - Year lesser than or equal to 2000**

![Lesser than 2000](https://github.com/Pam2020/AWS_for_DataEngineering/blob/81bad4d38f20a8b72a4f810238514093f48e66d2/Images/Result_lesserthan.png)
