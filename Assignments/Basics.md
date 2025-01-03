## Some basics

### 1. OLAP vs OLTP
   
OLAP and OLTP are two types of data management systems that are used for storing and analyzing data. Both are used to query existing data and store new data. Businesses use both OLAP and OLTP systems together to manage transactions as well as analytics/reporting needs. 

### OLAP:

OLAP stands for Online analytical processing that is optimized for complex data analysis and reporting. It is used to analyze aggregated data. For example, OLAP systems are used to generate reports, perform complex data analysis and identify trends for business. 

- **Data formatting**: OLAP systems store data in **multidimensional** data models where the different dimensions represent different attributes of the data and the values represent measures for intersection the dimensions. 

- **Data architecture**: **Data read** is prioritized over data write as the main purpose is analytics. Availability is also of not great importance. 

- **Performance**: Longer processing times - **minutes to hours**, data updates occur daily, weekly or monthly, depending on the system.

- **Storage and computer requirements**: Acts as a centralized data store, storage requirements range from terabytes to petabytes. Compute-intensive data reads. 

- OLAP is used to analyze data collected through OLTP. For example, popular products are identified and used for inventory budgeting, predict customer behaviour based on purchase trends  etc.

### OLTP:

OLTP stands for Online transaction processing which is optimized for transactional data processing and real-time updates in data. It is used to process database transactions. OLTP systems are used to process orders, manage customer accounts and update inventory etc. 

- **Data formatting**: OLTP systems are **unidimensional**. Data is stored in a relational database where each row represents an instance and each column represents an attribute. 

- **Data architecture**: Prioritizes **data write** operations and handles high-frequency, high-volume transactional data without compromising data integrity. For example, if two customers buy the same product at the same time, the chronological order is considered and the first ordered customer is given priority when the product is the last in stock. Availability is important and is achieved by keeping multiple data backups. 

- **Performance**: Faster processing times - **milliseconds or less**, updates occur in real-time.

- **Storage and computer requirements**: Storage requirements are in GBs as data can be cleared after transferring into an OLAP system. Compute-intensive as well.  

- Examples include, OLTP is used to process transactions in real-time, update inventory levels, manage rewards and returns of customer accounts etc. 

### 2. Differences between OLAP and OLTP

|      | OLAP | OLTP |
|:-----|:-----|:-----|                                                                              
|**Purpose**| OLAP helps analyze large volumes of data for data analytics | Process transactions |
|**Source** | Historical and aggregated data from multiple sources | Real-time and transactional data from a single source |
|**Structure** | Multidimensional/relational databases | Relational databases |
|**Model**|star or snowflake schema - datawarehouse schemas| Normalized/Denormalized models |
|**Volume of data**|TBs or PBs| GBs |
|**Response times**| seconds or minutes | milliseconds | 

   
### 3. Normal Forms:

Normalization is the process of segregating data into different tables(entities) and related them using unique identifiers. This is important to protect data from insertion, update and deletion anamolies. Ensures data integrity and data consistency. There are 4 normal forms (NFs):

 **1st NF**:
   - Attributes/column values have to be single valued - atomic - no repeating groups
   - values have to be of same type
   - attributes must be unique
   - order must not matter
   - each row must be uniquely identifiable - primary key required
     
 **2nd NF**:
   - it has to be in 1st NF and
   - each non-key attribute must depend on the entire primary key (if primary key is composite) - **no partial dependency**
     
 **3rd NF**:
   - it has to be in 1st and 2nd NF
   - non of the non-key attributes must depend on other non-key attributes - **no transitive dependency**
   - **Boyce-Codd Normal Form**: It is a higher version of 3rd NF. Every attribute in a table should depend on the key, the whole key, and nothing but the key
     
 **4th NF**:
   - it has to be in 1st, 2nd , 3rd and BCNF.
   - it should not have any multivalued dependencies - in the below example, Sid->Cid, Sname-> Cid, Sname->Cname are multi-valued dependencies

   |Sid|Sname|Cid|Cname|
   |:--|:----|:--|:----|
   |S1 |A | C1 |C|
   |S1 |A |C2| D|
   |S2| B| C1| C|
   |S2| B| C2|D|

### 4. Dimension vs Fact Tables

**Dimension Table**: Dimesions are different entities that make up the data such as customer, orders, time, products etc. Tables that represent each of the entities are called dimension tables.

**Fact Table**: Facts are measures that can be derived from these dimensions. These are stored in the fact table. 

There can be multiple dimesion tables but there can be only one fact table. 

**Types of dimesions**:
1. Slowly changing dimension:
This is a dimension table that slowly changes over time but not very frequently like everyday. For eaxmple, the address of a customer might change in future. There are 3 types of SCDs - SCD Type 1 (no history saved), Type 2 (complete history is mainained with start_date and end_date to know if the record is valid or not) and Type3 (only limited history is stored - current & previous record for example).

2. Conformed dimension:
A dimension that can be used for multiple fact tables - for example, place or time dimension.

3. Degenerate dimension:
A dimension that is found in the fact table (not as a foregin key of a dimesion table) then it is called a degenerate dimension.

4. Junk dimension:
Unrelated small dimesions that can be put together into a single dimension.

5. Static dimension:
This is a dimension that doesn't change over time. Example includes gender and status. 

### 5. Snowflake vs Star Schemas


**Star Schema**: It resembles a star and it is the simplest type of data warehouse schema. In this schema, there is a fact table that is surrounded by dimension tables. A single join can retrieve data from the dimesion and the fact tables. Here dimension tables might not be normalized. 

**Snowflake Schema**: It builds on the star schema by adding more dimesions to the existing dimesions thereby resebling a snowflake structure. In this schema, there is a fact table surrounded by dimension tables which are again surrounded by dimension tables. Here multiple joins are required to get data from dimensions and fact tables. Basically, the dimension tables in this schema are normalized and thereby split into multiple dimension tables. 

### References:
1. https://aws.amazon.com/compare/the-difference-between-olap-and-oltp/#:~:text=OLAP%20vs.%20OLTP-,Online%20analytical%20processing%20(OLAP)%20and%20online%20transaction%20processing%20(OLTP,processing%20and%20real%2Dtime%20updates.
2. https://www.geeksforgeeks.org/multidimensional-data-model/
3. https://abhimarichi.medium.com/types-of-dimension-tables-in-a-data-warehouse-bf6b48daf166
4. https://www.studytonight.com/dbms/database-normalization.php
5. https://www.guru99.com/star-snowflake-data-warehousing.html




