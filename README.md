# Healthcare Prior Authorization Leakage & Utilization Intelligence Platform

## Industry
**Health Insurance / Payer Analytics**

---

## Project Title
**Healthcare Prior Authorization Leakage & Utilization Intelligence Platform**

---

## Project Overview

Healthcare payers can experience financial leakage when medical services billed by providers do not match the services that were approved through the prior authorization process. Excess utilization, unauthorized services, high-cost providers, and claim-authorization mismatches can increase financial exposure and create opportunities for investigation.

This project develops a **Healthcare Prior Authorization Leakage & Utilization Intelligence Platform** using **SQL, Power Query, DAX, and Power BI**.

The solution analyzes authorization requests, claims, provider utilization, approved amounts, billed amounts, paid amounts, and potential leakage. The final Power BI solution provides two interactive dashboards that help users monitor overall performance and prioritize high-risk cases for investigation.

---

# Business Problem

Health insurers lose money when medical services are billed differently from what was approved.

The project focuses on identifying:

- Unauthorized or mismatched services
- Excess healthcare utilization
- High-cost providers
- Potential financial leakage
- Authorization and claim mismatches
- High-risk claims and members
- Providers with unusually high utilization
- Cases requiring investigation

The objective is to convert healthcare transaction data into actionable intelligence for payer operations, financial control, and investigation teams.

---

# Business Questions

The project answers the following business questions:

1. How many authorization requests are approved, denied, or pending?
2. How much money is approved, billed, and actually paid?
3. How much potential financial leakage is occurring?
4. Which claims do not match the approved authorization?
5. Which providers have unusually high utilization?
6. Which procedures have the highest authorization and claim volume?
7. Which providers generate the highest potential leakage?
8. Which members have unusually high healthcare utilization?
9. What are the main reasons for authorization or claim mismatches?
10. Which cases should be prioritized for investigation?

---

# Project Objectives

- Analyze prior authorization volume and status.
- Compare approved, billed, and paid amounts.
- Identify potential financial leakage.
- Detect authorization-to-claim mismatches.
- Analyze provider utilization patterns.
- Identify high-cost and high-leakage providers.
- Analyze procedure-level authorization and claim volume.
- Identify members with unusually high utilization.
- Classify high-risk claims and investigation cases.
- Provide interactive dashboards for business users.
- Support data-driven healthcare payer decisions.

---

# Tools & Technologies

| Tool / Technology | Purpose |
|---|---|
| **SQL** | Data extraction, joins, filtering, aggregation, and business analysis |
| **Power Query** | ETL, data cleaning, transformation, duplicate handling, and data preparation |
| **Power BI** | Interactive dashboards and visualization |
| **DAX** | KPI calculations, leakage metrics, utilization measures, and business logic |
| **Excel** | Data validation and supporting analysis |
| **GitHub** | Repository management and version control |

---

# Dataset Description

The project uses healthcare payer-related data containing information required to analyze authorization, claims, utilization, provider activity, and financial exposure.

The dataset may contain fields related to:

- Member information
- Authorization requests
- Authorization status
- Provider information
- Procedure information
- Claim information
- Approved amount
- Billed amount
- Paid amount
- Service dates
- Utilization
- Claim status
- Authorization and claim mismatch indicators
- Leakage-related fields
- Investigation and risk indicators

## Data Quality Preparation

Before dashboard development, the dataset is processed through ETL activities including:

- Data type validation
- Missing-value handling
- Duplicate identification
- Duplicate record removal where appropriate
- Conflicting record identification
- Date transformation
- Financial field validation
- Status standardization
- Data consistency checks

---

# SQL Analysis

SQL is used as the initial analytical layer to prepare and analyze the healthcare data.

Key SQL activities include:

- Extracting required healthcare records
- Joining relevant tables
- Filtering invalid or irrelevant records
- Identifying duplicate records
- Aggregating authorization and claim data
- Calculating financial totals
- Comparing approved, billed, and paid amounts
- Identifying authorization and claim mismatches
- Analyzing provider utilization
- Identifying high-value claims
- Supporting leakage analysis
- Creating datasets required for Power BI

---

# Power Query / ETL

Power Query is used to transform the SQL output into a clean analytical dataset.

The ETL process includes:

1. Load data from SQL.
2. Review column names and data types.
3. Standardize date fields.
4. Clean text and status fields.
5. Handle missing values.
6. Identify duplicate Member IDs and duplicate records.
7. Review conflicting records.
8. Retain the appropriate record when duplicates are identical.
9. Validate financial columns.
10. Create required transformation columns.
11. Load the cleaned data into Power BI.

---

# Power BI Dashboard

The Power BI solution contains **two dashboard pages**.

## Page 1 – Executive Dashboard

The Executive Dashboard provides a high-level view of authorization activity, financial performance, leakage, providers, and procedures.

### Key Visuals

- Authorization volume and status
- Approved vs Billed vs Paid Amount
- Potential Leakage
- Leakage by Reason
- Top Providers
- Top Procedures

### Purpose

This page is designed for management and business users who need a quick understanding of:

- Authorization performance
- Financial exposure
- Potential leakage
- Major providers
- Major procedures
- Areas requiring attention

---

# Page 2 – Investigation Dashboard

The Investigation Dashboard focuses on detailed analysis and prioritization of potentially high-risk cases.

### Key Visuals

- Provider Utilization
- Provider vs Peer Benchmark
- Authorization vs Actual Claim
- Risk Claims
- Leakage Amount
- Investigation Priority

### Purpose

This page supports investigation teams by helping them identify:

- Providers with unusually high utilization
- Claims exceeding authorization
- High-value leakage cases
- High-risk claims
- Members or providers requiring deeper review
- Cases that should be investigated first

---

# Key KPIs

The dashboard includes the following key performance indicators:

- **Authorization Volume**
- **Approved Authorization Count**
- **Denied Authorization Count**
- **Pending Authorization Count**
- **Approved Amount**
- **Billed Amount**
- **Paid Amount**
- **Potential Leakage Amount**
- **Leakage Rate**
- **Claim Volume**
- **Provider Utilization**
- **High-Risk Claim Count**
- **Investigation Amount**
- **Investigation Priority**

---

# Key Insights

The platform is designed to provide insights such as:

- The distribution of authorization requests across approved, denied, and pending statuses.
- The difference between approved, billed, and paid amounts.
- The total potential financial leakage.
- The primary reasons contributing to leakage.
- Providers generating unusually high utilization or leakage.
- Procedures with high authorization and claim volume.
- Claims where actual services do not match the approved authorization.
- Members with unusually high utilization.
- High-risk claims requiring investigation.
- Cases that should receive higher investigation priority.

---

# Leakage Analysis

Potential leakage is analyzed by comparing authorization and claim information.

Examples of potential leakage scenarios include:

- Claim amount exceeding the approved amount.
- Service not covered by the approved authorization.
- Procedure mismatch between authorization and claim.
- Quantity exceeding the approved quantity.
- Unauthorized service utilization.
- Unusual provider utilization.
- Other authorization or claim mismatch reasons.

The dashboard groups leakage by reason and provider to help identify the largest areas of financial exposure.

---

# Investigation Priority

Investigation cases can be prioritized based on factors such as:

- Leakage amount
- Claim amount
- Authorization mismatch
- Provider utilization
- Member utilization
- Risk indicators
- Frequency of unusual activity

High-value and high-risk cases can therefore be reviewed before lower-impact cases.

---

# Project Workflow

```text
Raw Healthcare Data
        ↓
SQL Data Extraction
        ↓
SQL Analysis
        ↓
Power Query / ETL
        ↓
Data Cleaning & Validation
        ↓
Duplicate & Conflict Handling
        ↓
Power BI Data Model
        ↓
DAX Measures & KPIs
        ↓
Executive Dashboard
        ↓
Investigation Dashboard
        ↓
Leakage & Utilization Insights
```

---

# Repository Structure

```text
Healthcare-Prior-Authorization-Intelligence/
│
├── README.md
│
├── Dataset/
│   ├── raw_data/
│   └── cleaned_data/
│
├── SQL/
│   ├── data_extraction.sql
│   ├── data_cleaning.sql
│   ├── duplicate_analysis.sql
│   └── business_analysis.sql
│
├── Power_Query/
│   └── ETL_Transformation.pq
│
├── PowerBI/
│   ├── Healthcare_Analytics.pbix
│   └── DAX_Measures.txt
│
├── Screenshots/
│   ├── executive_dashboard.png
│   └── investigation_dashboard.png
│
└── Documentation/
    └── Project_Documentation.md
```

---

# Dashboard Screenshots

## Page 1 – Executive Dashboard

<img width="898" height="480" alt="Executive Overview Dashboard" src="https://github.com/user-attachments/assets/b8c41d0a-7c59-4100-8360-42fef0fd1b4c" />


## Page 2 – Investigation Dashboard

<img width="975" height="522" alt="Investigation   Leakage Analysis Dashboard" src="https://github.com/user-attachments/assets/e5b5f4f9-ed09-408d-8c4c-42d4ecbc7553" />


---

# How to Run the Project

## Prerequisites

Install or have access to:

- SQL Server or compatible SQL environment
- Power BI Desktop
- Microsoft Excel (optional)
- Git

## Steps

### 1. Clone the Repository

```bash
git clone <repository-url>
```

### 2. Prepare the Dataset

Place the raw healthcare dataset in the appropriate `Dataset/raw_data/` folder.

### 3. Run SQL Analysis

Execute the SQL scripts in the `SQL/` folder to prepare and analyze the healthcare data.

### 4. Perform ETL

Open Power BI Desktop and select:

**Home → Transform Data**

Apply the Power Query transformations and validate the cleaned dataset.

### 5. Load the Data Model

Load the transformed data into the Power BI data model.

### 6. Verify DAX Measures

Check the KPI and analytical measures used for:

- Approved Amount
- Billed Amount
- Paid Amount
- Potential Leakage
- Leakage Rate
- Utilization
- Investigation Amount
- Risk and priority calculations

### 7. Refresh the Dashboard

Refresh the Power BI report after the data model and measures are validated.

### 8. Explore the Dashboard

Use the two dashboard pages:

- **Executive Dashboard** – overall business and financial view
- **Investigation Dashboard** – detailed leakage and risk investigation

---

# Dashboard Navigation

## Executive Dashboard

Provides an overview of:

**Authorization → Financials → Leakage → Providers → Procedures**

## Investigation Dashboard

Provides detailed analysis of:

**Utilization → Benchmark → Claim vs Authorization → Risk → Leakage → Investigation Priority**

---

# Project Outcome

The final solution provides a centralized healthcare payer analytics platform that transforms raw healthcare data into actionable business intelligence.

It enables users to:

- Monitor authorization performance.
- Compare approved, billed, and paid amounts.
- Identify potential financial leakage.
- Detect authorization and claim mismatches.
- Monitor provider and member utilization.
- Identify high-risk claims.
- Prioritize investigations.
- Support data-driven financial and operational decisions.

---

# Author

**Kumaresan V**
**BE - Computer Science & Engineering**
**AF ID:**AF05254165
**Course:** ANP-D3676 – Data and Business Analyst with AI
**Training Organization:** Anudip Foundation

**Skills Used**
MySQL
SQL
Power BI
DAX
Power Query
ETL
Data Cleaning
Data Visualization
Business Intelligence
Data Analytics

---

## Disclaimer

This project is developed for **analytics, learning, and portfolio purposes**. The leakage and risk indicators represent analytical signals that may require further business or clinical validation before being used for actual healthcare payment or investigation decisions.
