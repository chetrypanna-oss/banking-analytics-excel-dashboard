# 🏦 Banking Analytics Dashboard — Excel

An end-to-end banking analytics project built entirely in **Microsoft Excel** to analyze customer behavior, transactions, investments, regional profitability, and branch performance.

The project covers the complete analytics workflow:

**Data Cleaning → Data Validation → Data Modeling → Analysis → Dashboard → Business Insights**

---

## Project Overview

This project analyzes banking data across customers, transactions, and bank branches to identify meaningful business patterns and performance indicators.

The final deliverable is an interactive **Excel Banking Analytics Dashboard** designed to provide a high-level overview of:

- Customer base
- Transaction activity
- Investment behavior
- Account types
- Customer demographics
- Regional financial performance
- Branch profitability

---

## Business Objectives

The analysis focuses on:

* Customer demographics and segmentation
* Transaction activity and trends
* Investment behavior
* Account-type performance
* Regional revenue, expenses, and profitability
* Branch performance
* Key banking KPIs


---

## Tools & Technologies

**Microsoft Excel** | Data analysis and dashboard development |
**Power Query** | Data cleaning and transformation |
**Excel Tables** | Structured data management |
**PivotTables** | Aggregation and analysis |
**PivotCharts** | Data visualization |
**Excel Data Model** | Connecting related tables |
**Slicers** | Interactive dashboard filtering |
**Excel Formulas** | Calculations and validation |

---

## Dataset Structure

The project contains three main tables:

### 1. Customers Table

Contains customer-level information such as:

- Customer ID
- Branch ID
- Region
- Account Type
- Age and demographic information

### 2. Transactions Table

Contains transaction-level information such as:

- Transaction ID
- Customer ID
- Transaction Date
- Transaction Amount
- Investment Type
- Investment Amount
- Account Type

### 3. Bank Table

Contains branch-level financial information such as:

- Branch ID
- Region
- Revenue
- Expenses
- Calculated Profit

Additional time fields were created:

* Transaction_Year
* Transaction_Month
* Transaction_Month_Number
* Profit_Calculated
* Profit_Margin_Calculated
* Status
* Age_Group

----

### Data Cleaning & Validation


## Customer Table

The Customer table was cleaned using **Power Query**.

Key data-quality decisions:

* Checked Customer_ID duplicates — **no duplicates identified**
* **500 missing Age values** were replaced with the median age of **49**
* **500 missing Customer_Type values** were replaced with **Unknown**
* **500 missing City values** were replaced with **Unknown**
* Region, Bank_Name, and Branch_ID were checked for missing values

### Missing Age Treatment

Median imputation was used because the median is less sensitive to extreme values than the mean and allowed all customer records to be retained.

### Categorical Missing Values

Customer_Type and City were assigned **Unknown** where the correct value could not be reliably inferred, rather than introducing unsupported classifications.


----


### Bank Table

The Bank table was validated using Excel formulas and data-quality checks.

* Checked Branch_ID uniqueness — **no duplicates identified**
* Checked missing Firm_Revenue values
* Missing revenue was replaced using the **median revenue of the corresponding region**
* Regional median calculations excluded blank revenue values

### Regional Median Revenue

| Region | Median Revenue |
| ------ | -------------: |
| East   |        535,416 |
| North  |      501,100.5 |
| West   |        492,158 |
| South  |        526,771 |

### Profit Validation

The source **Profit_Margin** did not reconcile with Revenue and Expenses.

Instead of overwriting the source field, new validated analytical columns were created:

* `Profit_Calculated`
* `Profit_Margin_Calculated`
* `Status`

This preserved the original source information while allowing the analysis to use corrected profitability measures.

---

## Transaction Table

Transaction data was checked for:

* Duplicate Transaction_IDs
* Missing values
* Negative values
* Zero values
* Minimum and maximum values
* Future transaction dates

### Validation Results

* Total transactions: **10,000**
* Duplicate Transaction_IDs: **0**
* Missing Transaction_IDs: **0**
* Negative Transaction Amounts: **0**
* Zero Transaction Amounts: **0**
* Future transaction dates: **0**
* Date range: **21-03-2022 to 20-03-2025**

Transaction Amount values were rounded to **2 decimal places**.

---


# Excel Data Model

The cleaned datasets were added to the **Excel Data Model** and connected using relationships.

BANK TABLE
Branch_ID
    │
    ▼
CUSTOMERS TABLE
Branch_ID
Customer_ID
    │
    ▼
TRANSACTIONS TABLE
Customer_ID
```

### Relationships

`Cleaned_Bank[Branch_ID]` → `Cleaned_Customers[Branch_ID]`

`Cleaned_Customers[Customer_ID]` → `Cleaned_Transactions[Customer_ID]`

This enabled related banking information to be analyzed without unnecessarily duplicating fields across tables.


---


## Data Analysis

The following analyses were performed using Excel PivotTables and PivotCharts.

### Customer Analysis

* Customer Distribution by Age Group
* Customer Distribution by Region
* Customer Distribution by Account Type

### Transaction Analysis

* Annual Transaction Value
* Monthly Transaction Trend
* Account Type vs Transaction Value
* Average Transaction Amount

### Investment Analysis

* Investment Type vs Investment Value

### Financial Analysis

* Regional Revenue
* Regional Expenses
* Calculated Profit by Region
* Calculated Profit Margin
* Profitability Status

### Branch Analysis

* Top 5 Branches by Profit


---

# Dashboard

The final Excel dashboard combines key KPIs and visualizations into a single interactive reporting page.

### Key Performance Indicators

- **Total Customers:** 10,000
- **Total Transactions:** 10,000
- **Total Transaction Value:** ₹2.54 Cr
- **Total Investment:** ₹25.55 Cr

### Dashboard Visualizations

* Yearly Transaction Trend
* Customer Distribution by Age
* Investment Type vs Investment Value
* Account Type vs Transaction Value
* Regional Revenue, Expenses & Profit
* Top 5 Branches by Profit

### Interactive Filters

Slicers were added for:

* Transaction Year
* Region
* Account Type

---

# Key Business Insights

### Regional Performance

**East** generated the highest total profit at approximately **₹6.77 Cr**.

**South** generated approximately **₹6.67 Cr** and achieved the highest profit margin at approximately **49.30%**.

### Investment Behavior

**Recurring Deposit** had the highest investment value at approximately **₹8.60 Cr**, followed by Mutual Fund and Fixed Deposit.

### Account Activity

The analysis compares transaction value and average transaction size across:

- Business
- Current
- Savings

This helps identify differences between overall transaction activity and typical transaction size.

### Branch Performance

The Top 5 Branch analysis identifies the branches contributing the highest calculated profit and provides a management-oriented view of branch performance.

---
