# Data Mesh 

![System Design](https://github.com/Pam2020/AWS_for_DataEngineering/blob/dda8067b18a4311e54a58e4619a829ff731810b1/Images/BDB-2091-image001.png)


Data mesh is based on 4 main principles:

1. Domain ownership: Data management is organized around business functions or domains 
2. Data as a product: Consumers beyond the domain level conusme the analytical data after being handled by domain teams - other domain teams. Domain teams are responsible for getting data ready for other teams.
3. Self-serve data infrastructure: Domain teams take responsibility of their data - domain drived distributed architecture
4. Federated data governance: Security as a shared responsibility - leadership determines global standards and policies that apply across domains

Building a data mesh:

1. Analyze data: Identify different business domains and analyze what data goes in what domain with effective correlation of data
2. Implement global data governance policies: central IT/data team needs to identify reporting, authentication and compliance standards for the data mesh
3. Build your self-serve data platform: build user friendly data platforms (self-serve) that can be used by domain teams to handle their data - hide underlying technical complexity - include capabilities like data encryption, data product schema, governance and access control, data product logging and monitoring, caching for improved performance
4. Choose right technologies: Shift use of data warehouses/data lakes into multiple decentralized data repositories - distributed data product ownership over central data platform architecture 

References:
1. https://aws.amazon.com/blogs/big-data/build-a-modern-data-architecture-and-data-mesh-pattern-at-scale-using-aws-lake-formation-tag-based-access-control/
2. https://aws.amazon.com/what-is/data-mesh/
