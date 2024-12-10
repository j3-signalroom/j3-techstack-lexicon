# Snowflake Glossary

## Database
In **Snowflake**, a **database** is a logical structure used to organize and store data. It acts as a container for schemas, which in turn hold tables, views, and other database objects. Databases help structure data for easy management and accessibility in Snowflake’s cloud-based data warehouse.

### Key Features of a Snowflake Database:

1. **Organizational Unit**:
   - A database is used to group related schemas and objects.
   - Each database can hold multiple schemas, which further organize tables, views, functions, and more.

2. **Multi-Cloud and Multi-Region**:
   - Databases in Snowflake are abstracted from the physical storage layer, so they are seamlessly available across different cloud providers and regions (if set up accordingly).

3. **Isolation**:
   - Different databases in Snowflake are isolated from each other. This means operations on one database do not impact others.

4. **Security and Access Control**:
   - Permissions and access to databases can be tightly controlled using Snowflake’s role-based access control (RBAC).

5. **Data Sharing**:
   - Databases in Snowflake can be shared across accounts using **secure data sharing**, enabling data collaboration without copying data.

6. **Support for Various Data Types**:
   - Databases can store structured, semi-structured (e.g., JSON, Parquet, Avro), and unstructured data.

---

### **Database Structure**

1. **Database**  
   - The highest level of the hierarchy.
   - Example: `SALES_DATABASE`.

2. **Schema**  
   - Sub-division of a database for organizing database objects.
   - Example: `PUBLIC` schema in `SALES_DATABASE`.

3. **Objects within Schemas**:
   - **Tables**: Store raw data.
   - **Views**: Provide a virtual representation of data.
   - **Stored Procedures/Functions**: Allow complex operations and business logic.
   - **Stages**: Store files for data loading/unloading.
   - **File Formats**: Define the format for loading or querying external files.

---

### **Key Features of Databases in Snowflake**

1. **Time Travel**:
   - Databases include **time travel** capabilities, allowing you to query and restore data from previous states (up to 90 days, depending on the account).

2. **Cloning**:
   - Databases can be cloned instantly without duplicating the underlying storage, enabling testing and development workflows.

3. **Replication**:
   - Databases can be replicated across regions or cloud providers for high availability and disaster recovery.

4. **Data Retention**:
   - Databases support data retention policies for managing historical data and optimizing storage.

## Schema
In **Snowflake**, a **schema** is a logical container within a **database** that organizes and groups database objects such as tables, views, stages, file formats, sequences, functions, and more. Schemas help maintain a clear structure within a database and provide a means of managing data and access control at a granular level.

---

### Key Features of a Schema in Snowflake

1. **Logical Grouping**:
   - A schema is used to organize objects within a database logically, allowing for better management and data organization.

2. **Namespace Separation**:
   - Objects in one schema are distinct from those in other schemas, even if they share the same name. For example, `SALES.PUBLIC.CUSTOMERS` and `MARKETING.PUBLIC.CUSTOMERS` are separate entities.

3. **Access Control**:
   - Permissions can be granted at the schema level, controlling access to all objects within the schema.

4. **Isolation**:
   - Changes or operations in one schema do not affect objects in another schema.

5. **Support for Development Environments**:
   - Schemas are often used to separate environments (e.g., `DEV`, `TEST`, and `PROD`) within the same database.

---

### **Schema Structure**

1. **Database**:
   - The parent container for schemas.
   - Example: `SALES_DATABASE`.

2. **Schema**:
   - A subdivision of the database.
   - Example: `PUBLIC` schema in `SALES_DATABASE`.

3. **Objects within the Schema**:
   - **Tables**: Store structured data.
   - **Views**: Virtual representations of data.
   - **Stages**: Store files for loading/unloading data.
   - **File Formats**: Define the format for external files.
   - **Sequences**: Generate unique numbers.
   - **Functions/Procedures**: For custom operations and logic.

---

### **Common Use Cases for Schemas**

1. **Environment Separation**:
   - Use schemas to represent development, testing, and production environments.
     Example:
     - `MY_DATABASE.DEV`
     - `MY_DATABASE.TEST`
     - `MY_DATABASE.PROD`

2. **Departmental Organization**:
   - Group objects based on departments.
     Example:
     - `CORPORATE.HR`
     - `CORPORATE.FINANCE`

3. **Data Management**:
   - Use schemas to organize different types of data (e.g., raw, curated, and analytics-ready data).
     Example:
     - `DATA_LAKE.RAW`
     - `DATA_LAKE.CLEANSED`
     - `DATA_LAKE.ANALYTICS`

4. **Access Control**:
   - Schemas provide a granular level of access control, allowing you to grant specific roles permissions to subsets of the data.

## Warehouse
In **Snowflake**, a **warehouse** (often referred to as a "virtual warehouse") is a computational engine responsible for executing queries, loading data, and performing all data processing operations. It provides the compute resources required for tasks, independent of data storage.

---

### Key Characteristics of a Snowflake Warehouse

1. **Compute Engine**:
   - A warehouse provides the computational power needed to perform operations like querying, loading, and transforming data.

2. **Scalability**:
   - Snowflake warehouses can be scaled **up** or **down** by changing their size to meet performance requirements.
   - They can also scale **out** by increasing the number of clusters to handle concurrent workloads (multi-cluster warehouses).

3. **Pay-for-Use**:
   - Warehouses consume Snowflake credits based on their size and runtime. You only pay for the time a warehouse is active.

4. **Independent from Storage**:
   - Warehouses are decoupled from data storage, enabling flexible scaling and cost management.

5. **Concurrency and Isolation**:
   - Multiple warehouses can access the same data simultaneously without impacting each other, ensuring high performance and workload isolation.

---

### **Warehouse Sizes**

Warehouses come in different sizes, determining their computational capacity:
- **X-Small (XS)**: Minimal capacity for small workloads.
- **Small (S)**: Moderate capacity for small to medium workloads.
- **Medium (M)**: Suitable for larger datasets and more complex queries.
- **Large (L)**: Ideal for heavy workloads and concurrent operations.
- **XLarge (XL), 2XL, 3XL, 4XL**: Incrementally larger sizes for massive workloads.

The size of a warehouse determines the number of compute nodes Snowflake uses, with each size being a multiple of the smallest (`X-Small`).

---

### **Multi-Cluster Warehouses**

Multi-cluster warehouses allow Snowflake to handle varying levels of concurrent query workloads by automatically adding or removing compute clusters based on demand.

#### Key Features:
- **Auto-Scaling**:
  - Automatically adjusts the number of active clusters based on workload.
- **Concurrency Management**:
  - Prevents queries from being queued during peak demand.

---

### **Warehouse States**

- **Active**: A running warehouse consuming credits.
- **Suspended**: A paused warehouse not consuming credits. It can be resumed instantly when needed.

### **Example Workflow**

1. **Querying Data**:
   - A user runs a SQL query. The assigned warehouse provides the compute resources to execute the query.

2. **Loading Data**:
   - Data is loaded into Snowflake using a warehouse. Larger warehouses are recommended for faster ingestion.

3. **Transforming Data**:
   - ELT (Extract, Load, Transform) workflows use the warehouse for transformations.

---

### **Best Practices for Warehouses**

1. **Size Appropriately**:
   - Use smaller warehouses for lightweight tasks and larger ones for heavy or concurrent workloads.

2. **Enable Auto-Suspend**:
   - Save costs by suspending warehouses after a period of inactivity.

3. **Use Separate Warehouses**:
   - Assign different warehouses for distinct workloads (e.g., ETL jobs vs. ad-hoc queries) to avoid resource contention.

4. **Monitor Usage**:
   - Regularly review warehouse usage using Snowflake’s **account usage views** to optimize costs.
