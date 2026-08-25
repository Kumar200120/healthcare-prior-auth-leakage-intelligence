# Healthcare Prior Authorization Leakage & Utilization Intelligence Platform

> **Health Insurance / Payer Analytics \| SQL \| Power Query \| Power BI
> \| DAX**

A portfolio analytics project designed to identify **prior-authorization
leakage, utilization anomalies, authorization-to-claim mismatches, and
investigation priorities** in healthcare payer data.

The solution combines **20,000 prior authorizations** with a cleaned
population of **30,000 claims** and presents the results through two
interactive Power BI pages:

1.  **Executive Overview Dashboard**
2.  **Investigation & Leakage Analysis Dashboard**

------------------------------------------------------------------------

## Project Overview

Healthcare payers can experience financial leakage when the services
ultimately billed by providers differ from what was authorized. Examples
include excess utilization, procedure or provider mismatches, services
outside the approved authorization window, and claims with financial
exposure requiring investigation.

This project builds an analytical workflow that:

-   validates authorization and claims data;
-   removes duplicate claim records;
-   compares authorization and claim activity;
-   measures utilization and financial exposure;
-   identifies potential leakage signals;
-   highlights providers, procedures, and claims requiring review; and
-   presents executive and investigation-level insights in Power BI.

> **Important:** Leakage and risk indicators in this portfolio project
> are analytical signals for review. They are not proof of fraud and
> would require business and/or clinical validation in a production
> environment.

------------------------------------------------------------------------

## Business Problem

A payer needs a reliable way to answer three operational questions:

**What was authorized?**\
How many requests were approved, denied, pending, or expired, and what
utilization was permitted?

**What was actually billed and paid?**\
How much claim activity occurred, which providers and procedures drove
it, and how did actual utilization compare with authorization?

**Where should investigators focus?**\
Which claims contain mismatch, excess-utilization, timing, provider,
procedure, or other leakage signals that warrant deeper review?

The objective is to convert transaction-level healthcare data into
actionable intelligence for **payer operations, financial control,
utilization management, and investigation teams**.

------------------------------------------------------------------------

## Dataset Validation

The supplied source files were validated against the dashboard totals.

  ---------------------------------------------------------------------------
  Validation Item      Source Result  Dashboard Result         Status
  ---------------- ----------------- ----------------- ----------------------
  Authorization               20,000            20,000           ✅
  records                                              

  Approved                    15,200            15,200           ✅
  authorizations                                       

  Approval rate               76.00%            76.00%           ✅

  Raw claim rows              30,050               ---          ---

  Exact duplicate                 50    Removed during           ✅
  claim rows                                  cleaning 

  Clean claim                 30,000            30,000           ✅
  records                                              

  Total billed          ₹335.0251 Cr        ₹335.03 Cr           ✅
  amount after                                         
  duplicate                                            
  removal                                              

  Total paid           ₹279.70668 Cr        ₹279.71 Cr           ✅
  amount after                                         
  duplicate                                            
  removal                                              

  Average paid            ₹93,235.56           ₹93.24K           ✅
  claim cost                                           
  ---------------------------------------------------------------------------

### Data-quality findings

**Authorizations** - 20,000 rows and 12 columns - 20,000 unique
`Authorization_ID` values - Missing values detected in: - `Member_ID`:
200 - `Provider_ID`: 150 - `Procedure`: 100 - No exact duplicate
authorization rows detected

**Claims** - 30,050 raw rows and 10 columns - 30,000 unique `Claim_ID`
values - 50 exact duplicate rows detected - Missing values detected
in: - `Member_ID`: 388 - `Provider_ID`: 217 - `Procedure`: 238 - All
claim `Authorization_ID` values map to an authorization record -
Removing the 50 exact duplicates reconciles the claims count and
financial totals shown in Power BI

This reconciliation confirms that the headline dashboard totals for
**claim volume, billed amount, paid amount, approval count, approval
rate, and average paid claim cost** are consistent with the supplied
data after duplicate removal.

------------------------------------------------------------------------

## Core Business Questions

1.  How many authorization requests were approved, denied, pending, or
    expired?
2.  What is the authorization approval rate?
3.  What are total billed and paid claim amounts?
4.  How much potential leakage has been identified by the analytical
    rules?
5.  What is the leakage rate trend over time?
6.  Which leakage reasons contribute the greatest financial exposure?
7.  Which providers generate the highest leakage amount?
8.  Which procedures generate the highest leakage amount?
9.  Which claims should enter the investigation queue?
10. How does leakage vary by risk level and month?
11. How many claims indicate excess utilization?
12. How many services occurred outside the approved authorization
    window?

------------------------------------------------------------------------

## Dashboard 1 --- Executive Overview

The **Executive Overview Dashboard** provides management with a
consolidated view of authorization performance, claims, financial
exposure, utilization, and leakage.

### Headline KPIs

  KPI                           Dashboard Value
  --------------------------- -----------------
  Total Authorizations               **20,000**
  Approved Authorizations            **15,200**
  Approval Rate                      **76.00%**
  Total Claims                       **30,000**
  Total Billed Amount            **₹335.03 Cr**
  Total Paid Amount              **₹279.71 Cr**
  Mismatch Rate                      **59.29%**
  Investigation Amount            **₹33.10 Cr**
  Excess Utilization Claims           **5,859**
  Out-of-Window Claims                  **300**
  Average Claim Cost (Paid)         **₹93.24K**

### Executive visuals

-   Authorization trend by month
-   Authorization status distribution
-   Potential leakage and leakage-rate trend
-   Executive KPI cards
-   Date, authorization status, claim status, provider, and procedure
    filters

### Management value

This page allows business users to quickly assess:

-   authorization throughput and approval performance;
-   overall claims and payment exposure;
-   potential leakage magnitude;
-   mismatch and utilization indicators;
-   changes in leakage over time; and
-   areas requiring investigation.

![Executive Overview Dashboard](Screenshots/executive_dashboard.png)

------------------------------------------------------------------------

## Dashboard 2 --- Investigation & Leakage Analysis

The **Investigation & Leakage Analysis Dashboard** moves from executive
monitoring to case prioritization and root-cause analysis.

### Investigation visuals

-   Leakage reason distribution
-   Leakage amount by reason
-   Top 10 providers by leakage amount
-   Risk claims investigation queue
-   Potential leakage KPI
-   Leakage amount by risk level
-   Monthly leakage trend
-   Top 10 procedures by leakage amount

### Investigation queue

The detailed claim table surfaces fields such as:

-   `Claim_ID`
-   `Member_ID`
-   `Procedure`
-   `Leakage_Reason`
-   `Potential_Leakage`
-   `Risk_Score`
-   `Risk_Level`
-   `Investigation_Flag`
-   `Utilization_Status`

This design helps investigators move from an aggregated leakage signal
to the individual claims that require review.

![Investigation & Leakage Analysis
Dashboard](Screenshots/investigation_dashboard.png)

------------------------------------------------------------------------

## Leakage & Utilization Logic

The project evaluates authorization-to-claim relationships for
analytical signals such as:

-   **Excess utilization** --- billed utilization exceeds authorized
    utilization
-   **Procedure mismatch** --- claimed procedure differs from the
    authorization
-   **Provider mismatch** --- claim provider differs from the authorized
    provider
-   **Out-of-window service** --- service occurs outside the approved
    authorization dates
-   **No/invalid authorization relationship** --- claim activity does
    not satisfy the expected authorization condition
-   **Financial variance** --- claim financial activity creates exposure
    relative to authorization rules
-   **Other mismatch conditions** --- business-rule exceptions requiring
    investigation

The dashboard groups these signals into leakage reasons and uses them to
analyze **potential leakage amount, risk, provider concentration,
procedure concentration, and investigation priority**.

------------------------------------------------------------------------

## Analytical Workflow

``` text
Raw Authorization Data + Raw Claims Data
                    │
                    ▼
             Data Validation
                    │
                    ▼
       Duplicate / Missing-Value Review
                    │
                    ▼
             SQL Analysis Layer
                    │
                    ▼
          Power Query Transformation
                    │
                    ▼
        Authorization–Claim Comparison
                    │
                    ▼
       Leakage & Utilization Rule Logic
                    │
                    ▼
            Power BI Data Model
                    │
                    ▼
              DAX Measures
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
 Executive Overview     Investigation &
     Dashboard           Leakage Analysis
```

------------------------------------------------------------------------

## Tools & Technologies

  -----------------------------------------------------------------------
  Technology                          Project Use
  ----------------------------------- -----------------------------------
  **SQL**                             Data extraction, joins, validation,
                                      aggregation, mismatch analysis, and
                                      business queries

  **Power Query**                     Data cleaning, type handling,
                                      duplicate removal, transformations,
                                      and preparation

  **Power BI**                        Data modeling, interactive
                                      dashboard design, filtering, and
                                      visualization

  **DAX**                             KPI measures, rates, financial
                                      calculations, leakage metrics, and
                                      analytical logic

  **Excel / CSV**                     Source-data validation and
                                      supporting checks

  **Git & GitHub**                    Version control, repository
                                      management, and portfolio
                                      presentation
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## Suggested Data Model

A production-style model can organize the project around:

-   **Authorizations** --- authorization-level facts and approved
    utilization
-   **Claims** --- claim-level billed and paid utilization
-   **Date** --- calendar attributes for trend analysis
-   **Provider** --- provider-level slicing and concentration analysis
-   **Member** --- member-level utilization analysis
-   **Procedure** --- procedure-level analysis

`Authorization_ID` provides the principal link for comparing claim
activity with the corresponding prior authorization.

------------------------------------------------------------------------

## Key Measures & KPIs

Core measures used by the report include:

-   Total Authorizations
-   Approved Authorizations
-   Approval Rate
-   Total Claims
-   Total Billed Amount
-   Total Paid Amount
-   Average Paid Claim Cost
-   Potential Leakage Amount
-   Leakage Rate
-   Mismatch Rate
-   Excess Utilization Claims
-   Out-of-Window Claims
-   Investigation Amount
-   Leakage by Provider
-   Leakage by Procedure
-   Leakage by Risk Level
-   Monthly Leakage Trend

------------------------------------------------------------------------

## Key Insights Demonstrated by the Dashboard

-   **76.00%** of authorization records are approved.
-   After removing **50 exact duplicate claim rows**, the analytical
    claim population is **30,000**.
-   Clean claims contain approximately **₹335.03 Cr billed** and
    **₹279.71 Cr paid**.
-   Average paid claim cost is approximately **₹93.24K**.
-   The dashboard identifies **₹33.10 Cr** as potential
    leakage/investigation exposure under the project's analytical rules.
-   **5,859** claims are flagged for excess utilization in the
    dashboard.
-   **300** claims are identified as occurring outside the authorization
    window.
-   The investigation page enables leakage to be traced by **reason,
    provider, procedure, risk level, month, and individual claim**.

------------------------------------------------------------------------

## Dashboard Navigation & Filters

Both pages provide interactive filtering to support focused analysis.

**Available slicers** - Date Range - Authorization Status - Claims
Status - Provider ID - Procedure

**Navigation** - `Executive Overview` → high-level operational and
financial monitoring - `Leakage & Investigation` → root-cause analysis
and claim investigation queue

------------------------------------------------------------------------

## Repository Structure

``` text
Healthcare-Prior-Authorization-Intelligence/
│
├── README.md
│
├── Dataset/
│   ├── raw_data/
│   │   ├── Authorizations.csv
│   │   └── Claims.csv
│   └── cleaned_data/
│
├── SQL/
│   ├── data_validation.sql
│   ├── data_cleaning.sql
│   ├── authorization_claim_analysis.sql
│   └── business_analysis.sql
│
├── Power_Query/
│   └── ETL_Transformation.pq
│
├── PowerBI/
│   ├── Healthcare_Prior_Authorization_Intelligence.pbix
│   └── DAX_Measures.txt
│
├── Screenshots/
│   ├── executive_dashboard.png
│   └── investigation_dashboard.png
│
└── Documentation/
    └── Project_Documentation.md
```

> Adjust the repository tree to match the files actually committed to
> GitHub.

------------------------------------------------------------------------

## How to Run the Project

### Prerequisites

-   SQL Server, MySQL, or another compatible SQL environment
-   Power BI Desktop
-   Git
-   Excel or another CSV viewer for optional source validation

### Steps

1.  Clone or download the repository.
2.  Load `Authorizations.csv` and `Claims.csv` into the SQL environment.
3.  Validate row counts, IDs, missing values, and duplicate records.
4.  Remove the 50 exact duplicate claim rows as part of the cleaning
    workflow.
5.  Execute the SQL analysis used for authorization-to-claim comparison.
6.  Load the prepared data into Power BI.
7.  Apply Power Query transformations and verify data types and
    relationships.
8.  Validate the DAX measures against source totals.
9.  Refresh the report.
10. Use the Executive Overview page for monitoring and the Investigation
    page for detailed leakage analysis.

------------------------------------------------------------------------

## Validation Notes

The supplied dashboard screenshots and datasets were cross-checked
during README preparation.

Confirmed reconciliations include:

-   `20,000` authorization rows → **20,000 Total Authorizations**
-   `15,200` approved authorization rows → **15,200 Approved
    Authorizations**
-   `15,200 / 20,000` → **76.00% Approval Rate**
-   `30,050` raw claim rows minus `50` exact duplicates → **30,000 Total
    Claims**
-   cleaned billed total `₹3,350,251,000` → **₹335.03 Cr**
-   cleaned paid total `₹2,797,066,800` → **₹279.71 Cr**
-   cleaned average paid amount `₹93,235.56` → **₹93.24K**

Dashboard-specific leakage, mismatch, utilization, risk, and
investigation metrics should be interpreted according to the DAX/Power
Query business rules implemented in the Power BI model.

------------------------------------------------------------------------

## Project Outcome

The completed solution demonstrates an end-to-end analytics workflow for
healthcare payer operations:

**Data Validation → SQL Analysis → ETL → Data Modeling → DAX →
Visualization → Investigation**

It enables stakeholders to monitor authorization performance, reconcile
claims and payments, identify utilization anomalies, quantify potential
leakage, locate concentration by provider or procedure, and prioritize
claims for investigation.

For a data analytics portfolio, the project demonstrates practical
capability in:

-   healthcare business understanding;
-   data-quality validation;
-   relational analysis;
-   SQL;
-   Power Query;
-   DAX;
-   Power BI dashboard development;
-   KPI design;
-   root-cause analysis; and
-   translating transaction data into actionable business intelligence.

------------------------------------------------------------------------

## Author

**Kumaresan V.**

**Project:** Healthcare Prior Authorization Leakage & Utilization
Intelligence Platform\
**Industry:** Health Insurance / Payer Analytics\
**Technology:** SQL \| Power Query \| Power BI \| DAX \| Excel \| GitHub

------------------------------------------------------------------------

## Disclaimer

This project is developed for **learning, analytics, and portfolio
demonstration purposes**. The data and analytical indicators should not
be interpreted as real healthcare payment determinations, clinical
decisions, or confirmed fraud findings. Potential leakage and risk flags
represent analytical signals that require appropriate business and
clinical review before operational use.
