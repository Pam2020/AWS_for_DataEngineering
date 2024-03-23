## Some basics

### 1. OLAP vs OLTP
   
OLAP and OLTP are two types of data management systems that are used for storing and analyzing data. Both are used to query existing data and store new data. Businesses use both OLAP and OLTP systems together to manage transactions as well as analytics/reporting needs. 

### OLAP:

OLAP stands for Online analytical processing that is optimized for complex data analysis and reporting. It is used to analyze aggregated data. For example, OLAP systems are used to generate reports, perform complex data analysis and identify trends for business. 

- **Data formatting**: OLAP systems store data in **multidimensional** data models where the different dimensions represent different attributes of the data and the values represent measures for intersection the dimensions. 

- **Data architecture**: **Data read** is prioritized over data write as the main purpose is analytics. Availability is also of not great importance. 

- **Performance**: Longer processing times - **minutes to hours**, data updates occur daily, weekly or monthly, depending on the system.

- **Storage and computer requirements**: Acts as a centralized data store, storage requirements range from terabytes to petabytes. Compute-intensive data reads. 

- OLAP is used to analyze data collected through OLTP. For example, popular products are identified and used for inventory budgeting.

### OLTP:

OLTP stands for Online transaction processing which is optimized for transactional data processing and real-time updates in data. It is used to process database transactions. OLTP systems are used to process orders, manage customer accounts and update inventory etc. 

- **Data formatting**: OLTP systems are **unidimensional**. Data is stored in a relational database where each row represents an instance and each column represents an attribute. 

- **Data architecture**: Prioritizes **data write** operations and handles high-frequency, high-volume transactional data without compromising data integrity. For example, if two customers buy the same product at the same time, the chronological order is considered and the first ordered customer is given priority when the product is the last in stock. Availability is important and is achieved by keeping multiple data backups. 

- **Performance**: Faster processing times - **milliseconds or less**, updates occur in real-time.

- **Storage and computer requirements**: Storage requirements are in GBs as data can be cleared after transferring into an OLAP system. Compute-intensive as well.  

- Examples include, OLTP is used to process transactions in real-time, update inventory levels, manage rewards and returns of customer accounts etc. 

### 2. Differences between OLAP and OLTP

| OLTP | OLAP |
|:-----|:-----|
|                                                                                    OLTP:
**Purpose:** OLAP helps analyze large volumes of data for data analytics                     Process transactions
**Source:**  Historical and aggregated data from multiple sources                            Real-time and transactional data from a single source
**Structure** Multidimensional/relational databases                                          Relational databases



