## Some basics

### 1. OLAP vs OLTP
   
OLAP and OLTP are two types of data management systems that are used for storing and analyzing data. Both are used to query existing data and store new data. 

### OLAP:

OLAP stands for Online analytical processing that is optimized for complex data analysis and reporting. It is used to analyze aggregated data. For example, OLAP systems are used to generate reports, perform complex data analysis and identify trends for business. 

- Data formatting: OLAP systems store data in multidimensional data models where the different dimensions represent different attributes of the data and the values represent measures for intersection the dimensions. 

- Data architecture: Data read is prioritized over data write as the main purpose is analytics. Availability is also of not great importance. 

- Performance: Longer processing times - minutes to hours, data updates occur daily, weekly or monthly, depending on the system.

- Storage and computer requirements: Acts as a centralized data store, storage requirements range from terabytes to petabytes. Compute-intensive data reads. 

- OLAP is used to analyze data collected through OLTP. For example, popular products are identified and used for inventory budgeting.  

