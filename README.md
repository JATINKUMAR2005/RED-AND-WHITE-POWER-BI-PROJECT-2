# 📊 Power BI Data Modeling Project – Star Schema Implementation

## 📌 Project Objective
The objective of this project is to design and validate a clean, efficient, and ambiguity-free data model in Power BI using best practices such as Star Schema, proper relationship management, inactive relationships, and matrix-based validation.

This project focuses strictly on data modeling, not dashboard design.

---

## 📂 Dataset Overview
The project uses the following datasets:

- Sales_Fact.xlsx – Main transactional sales data  
- Customer_Dim.xlsx – Customer attributes and segmentation  
- Product_Dim.xlsx – Product details and categories  
- Region_Dim.xlsx – Geographic information  
- Date_Dim.xlsx – Calendar and fiscal date attributes  
- Returns_Fact.xlsx – Product return transactions  

---

## 🔹 Step 1: Data Import
- Imported all Excel files into Power BI using Get Data
- Opened Power Query Editor for data preparation

---

## 🔹 Step 2: Data Cleaning (Power Query)
- Verified correct data types:
  - IDs → Whole Number  
  - Revenue → Decimal / Currency  
  - Dates → Date  
- Removed blank rows and null key values
- Ensured consistent and clean column names

---

## 🔹 Step 3: Identifying Keys
- Identified Primary Keys in all dimension tables
- Verified Foreign Keys in fact tables
- Ensured referential integrity

---

## 🔹 Step 4: Data Model Design
- Implemented Star Schema design
- Sales_Fact used as the central fact table
- Dimension tables connected directly to Sales_Fact
- Returns_Fact modeled as a secondary fact table

---

## 🔹 Step 5: Relationship Creation

| From Table | To Table | Cardinality | Filter Direction | Status |
|-----------|----------|-------------|-----------------|--------|
| Customer_Dim | Sales_Fact | 1 : * | Single | Active |
| Product_Dim | Sales_Fact | 1 : * | Single | Active |
| Region_Dim | Sales_Fact | 1 : * | Single | Active |
| Date_Dim | Sales_Fact | 1 : * | Single | Active |
| Sales_Fact | Returns_Fact | 1 : * | Single | Active |
| Date_Dim | Returns_Fact | 1 : * | Single | Inactive |

---

## 🔹 Step 6: Handling Inactive Relationship
- ReturnDateKey relationship kept inactive
- Prevented ambiguity caused by multiple date paths
- Maintained accurate time-based analysis

---

## 🔹 Step 7: Hierarchy Creation

### Date_Dim
Year → Quarter → Month → Date

### Region_Dim
Country → State → City

### Product_Dim
Category → Subcategory → ProductName

---

## 🔹 Step 8: Data Categorization
- Country → Country
- State → State or Province
- City → City
- Date → Date

---

## 🔹 Step 9: Model Validation Using Matrix Visuals

### Matrix 1
Rows: Product Category  
Columns: Region  
Values: Revenue  

### Matrix 2
Rows: Fiscal Year  
Columns: Return Reason  
Values: Count of Returns  

### Matrix 3
Rows: Customer Segment  
Values: Revenue  

---

## 🔹 Step 10: Ambiguity Prevention
- Used single-direction filtering
- Avoided many-to-many relationships
- Maintained one active date relationship per fact table
- Separated Sales and Returns into different fact tables

---

## ✅ Final Outcome
- Clean and scalable Star Schema
- Accurate filter propagation
- No circular dependencies
- Enterprise-ready Power BI data model

---

## 🏁 Conclusion
This project demonstrates strong understanding of Power BI data modeling concepts including star schema design, relationship handling, inactive relationships, and validation techniques without using DAX or calculated columns.
