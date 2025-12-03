# SQL_Projects
## 📦 SQL Project1: Logistics Database Management

This project demonstrates proficiency in **Relational Database Management Systems (RDBMS)** using SQL to model, manage, and analyze a logistics company's operations data.

---

## 🎯 Project Objective

To design and implement a robust database schema for a logistics company to efficiently track and manage all core operations—including shipments, employee assignments, customer memberships, and payment details. The ultimate goal is to create a Single Source of Truth (SSOT) for accurate reporting and data-driven operational decisions.

---

## 🏗️ Schema Design Overview

The database was structured using **7 normalized tables** with established **Primary Key (PK)** and **Foreign Key (FK)** constraints to ensure data integrity and define clear relationships. 

| Table Name | Primary Key | Key Columns | Purpose |
| :--- | :--- | :--- | :--- |
| **Employee\_Details** | `Emp_ID` | `Emp_name`, `Emp_branch`, `Emp_designation` | Employee information and branch assignment. |
| **Membership** | `M_ID` | `M_TYPE`, `Start_Date`, `End_Date` | Defines customer membership status and duration. |
| **Customer** | `Cust_ID` | `Cust_name`, `Cust_TYPE`, `M_ID (FK)` | Customer demographics and links to their membership status. |
| **Shipment\_Details** | `SH_ID` | `SH_CONTENT`, `SH_WEIGHT`, `EMP_ID (FK)` | Records details of each shipment and the assigned employee. |
| **Payment\_Details** | `P\_ID` | `P\_TYPE`, `AMOUNT`, `SH\_ID (FK)` | Tracks payment methods and amounts for shipments. |
| **Branch\_Details** | `B\_ID` | `B\_NAME`, `B\_ADDR` | Information on each operational branch. |
| **Shipment\_Assignment** | *Composite PK* | `SH_ID (FK)`, `EMP_ID (FK)` | Maps shipments to the employees responsible for them. |

### Key Technical Milestones

1.  **Data Preprocessing:** Used `STR_TO_DATE` and `ALTER TABLE` commands to convert text-based date columns into the proper `DATE` format, crucial for time-based analysis.
2.  **Single Source of Truth (SSOT):** Created a consolidated view (`logistics_Emp`) by joining all necessary tables, simplifying subsequent analytical queries.

---

## 📈 Key Exploratory Data Analysis (EDA) Insights

The analytical queries performed on the SSOT provided actionable operational insights:

| Insight Type | Finding | SQL Technique Demonstrated |
| :--- | :--- | :--- |
| **Customer Analysis** | Identified customers who have maintained a membership for over one year (long-term loyalty). | Date functions (`DATEDIFF`, `NOW()`) and filtering (`WHERE`). |
| **Operational Efficiency** | Determined the **most preferred service type** by volume, guiding resource allocation and investment decisions. | `GROUP BY`, `COUNT()`, and `ORDER BY`. |
| **Data Quality & Maintenance** | Successfully **updated the branch location** from 'NY' (New York) to 'NJ' (New Jersey) due to a temporary shutdown. | `UPDATE` statement with `WHERE` clause. |
| **Business Reporting** | Calculated the **percentage contribution of each customer type** to the total customer base. | Variables (`SET @total_count`), `COUNT()`, and arithmetic operations. |
| **Advanced Filtering** | Found shipment IDs and contents where the **shipment weight exceeds the overall average weight**, flagging heavy-load logistics. | Subqueries (`WHERE SH_WEIGHT > (SELECT AVG(SH_WEIGHT)...)`). |
| **Financial Tracking** | Created a **VIEW** to easily monitor all customers who have not yet cleared their payments. | `CREATE VIEW` for simplified recurring reporting. |

---

## ✅ Conclusion

This project successfully demonstrates end-to-end expertise in SQL, covering database architecture, data cleaning, complex querying, and deriving business intelligence from raw operational data. It is a solid foundation showcasing the ability to manage and query large relational datasets effectively.

**Files Included:**
* `project.sql` (Full schema creation, data insertion, and all analytical queries)
* `SQL Project Solution.pdf` (Detailed documentation and solved steps)

