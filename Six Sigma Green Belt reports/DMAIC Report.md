# 📊 Lean Six Sigma DMAIC Project Case Study

**Project Title:** SG&A (T&E Expense) Financial Reporting Process Automation
**Methodology:** Lean Six Sigma DMAIC Framework
**Business Domain:** Financial Planning & Analysis (FP&A)
## 1. DEFINE PHASE
### 1.1 Project Background & Business Case
In corporate Financial Planning & Analysis (FP&A), tracking Selling, General, and Administrative (SG&A) expenditures—specifically Travel & Entertainment (T&E)—is critical for cost containment and operational margin management. Historically, the processing, consolidation, and distribution of weekly and monthly expense variance reviews to Director-level managers relied on manual, highly fragmentation-prone operations across disparate data silos. As transaction frequencies and volumes scale, this processing latency represents a severe operational bottleneck.
### 1.2 Problem Statement
The legacy T&E reporting mechanism required manual collection and relational mapping across 6 unlinked data systems (Employee Catalog, Chart of Accounts/GL Master, Department Master List, P&L hierarchy maps, and multiple Target Budgets).
- **Cycle Time Defect:** Manual extraction, restructuring, and report formulation generated a total batch lead time of **36 to 48 business hours** per reporting iteration.
- **Daily Ingestion Friction:** Over a 91-day baseline evaluation, Daily Reporting Latency exceeded the demonstrated capability threshold ($P_{25} = 1.005\text{ hours}$) on **68 out of 91 days** (process median $P_{50} = 1.140\text{ hours}$), reaching a peak spike of **2.70 hours** in late June.
- **Quality & Capability Defect:** Manual operations generated a **74.73% Non-Compliance (NC) rate**, translating to **747,252.75 DPMO** and a **Baseline Process Sigma Score of -0.6659σ**, indicating an out-of-control operational state.
In other words, performance is lower than statistical goal. i.e. NC = 74.72%; with DPMO value of 747252.7 and sigma score of -0.66587
### 1.3 Project Goal Statement
To execute a leftward distribution shift in Daily Reporting Latency, transitioning the process median from $P_{50} = 1.140\text{ hours}$ to the demonstrated benchmark of $P_{25} = 1.005\text{ hours}$—and ultimately to $<0.03\text{ hours}$ ($<1.8\text{ minutes}$) via an automated Power Query ETL engine and interactive Star-Schema data model in Power BI. The objective includes reducing batch cycle time from **48 hours to under 2 minutes**, maintaining 100% data integrity, eliminating human-reconciliation defects ($0\text{ DPMO}$), and elevating overall process capability to **≥ 6.00σ**.
### 1.4 Process Boundaries (SIPOC Framework)
- **Suppliers:** Accounting/ERP Systems Admin, Human Resources Data Team, Corporate FP&A Budget Owners.
- **Inputs:** Raw Credit Card monthly and weekly transactional workbooks, Master Employee Lists, Chart of Accounts (GL catalog), Department Code lists, and corresponding Weekly/Monthly Budget Targets.
- **Process:** Extract raw ledger records $\rightarrow$ Apply M-Code query normalization schema $\rightarrow$ Establish multi-dimensional relationship matrices $\rightarrow$ Refresh interactive dashboard views.
- **Outputs:** Parameterized relational Star-Schema analytics file (`Variance Analysis.pbix`), budget vs. actual variance visual matrices, and automated transactional aggregations.
- **Customers:** L1 and L2 Director-level Department Managers, Corporate Finance leadership, CFO.
## 2. MEASURE PHASE
### 2.1 Process Mapping & Structural Baselining
The initial step involved auditing and cataloging the physical architecture of the data incoming from the operational pipeline. Over a multi-year footprint (2025–2026), data arrived through split multi-frequency reporting paths.
```
[Raw Inputs Recieved] ──► [Manual Validation] ──► [Cross-Table VLOOKUPs] ──► [Static Pivot Build] ──► [Email to L1/L2]
```
### 2.2 Data Ingestion Complexity Audit
The process currently ingests data spread continuously across various separate files and spreadsheets:
1. **Dynamic Transaction Repositories:**
    - **`2025/Monthly/`:** 12 separate workbooks (`Credit_Cards_Data - 01 January.xlsx` through `12 December.xlsx`).
    - **`2025/Weekly/`:** 53 standalone cross-sectional operational week files.
    - **`2026/Monthly/` & `2026/Weekly/`:** Ongoing current fiscal year runs (e.g., active months January–July).
2. **Master Dimensional Registries (`Company Data.xlsx`):**
    - `General Ledger` (Chart of Accounts outlining GL Numbers, US GAAP categorizations).
    - `Department List` (Department codes linked to L1/Director identifiers and email endpoints).
    - `Employee Data` (Unique Employee IDs, corporate rank classifications, organizational statuses).
    - `Monthly Budget` & `Weekly Budget (2025/2026)` target distribution sheets.
### 2.3 Time-Study Baselining
Time tracking on the baseline process showed that manual column mapping, data scrubbing to resolve termination-date blanks, and VLOOKUP alignments required **an average of 42 hours per month**, rendering the process completely unscalable.
	*Historically, the manual reporting process resulted in a massive cumulative bottleneck, consuming **48 hours** for weekly compilations and **36 hours** for monthly closes. To monitor this variation on a daily operational level, we tracked the **Daily Ingestion & Sync Time**. At its peak crisis window in late June, the daily friction spiked to **2.70 hours of active error-correction on a single day's data load**.*
### 2.4 Statistical Baselining & Continual Improvement Methodology
#### A. Precision Before Accuracy & The Median Rationale
In Lean Six Sigma, process optimization follows a natural continual improvement curve: establishing **precision (consistency)** precedes driving **accuracy (target achievement)**. To establish a realistic operational baseline without distortion from outlier processing spikes, **Median ($P_{50}$)** was selected over standard Mean:
- **Current Process Median ($P_{50}$):** $1.140\text{ Hours}$ (50% of daily runs took longer than 1.14 hrs, 50% took less).
#### B. Demonstrated Capability Target Setting ($P_{25} \rightarrow P_{50}$)
Rather than setting an arbitrary, unvalidated stretch target, the baseline target was anchored on the process's **demonstrated performance threshold**:
- **25th Percentile Target ($P_{25}$):** $1.005\text{ Hours}$.
- **Rationale:** Historically, the legacy process achieved a latency of $\le 1.005\text{ hours}$ on $25\%$ of evaluated days. Because the system demonstrated the ability to reach $1.005\text{ hours}$ under existing conditions, making **today's $P_{25}$ become tomorrow's $P_{50}$** represents a natural, achievable **Left Shift** in the performance bell curve.
#### C. Pre-Implementation Statistical Defect Metric
Evaluating all 91 historical sample days against the $1.005\text{-hour}$ specification limit ($USL$) yields:
- **Non-Compliance (NC) Count:** 68 Days ($> 1.005\text{ hrs}$).
- **Defects Per Opportunity (DPO):** $\frac{68}{91} = 0.74725\ (74.73\%)$.
- **DPMO:** $0.74725 \times 1,000,000 = \mathbf{747,252.75}$.
- **Baseline Sigma Score ($Z$):** $\Phi^{-1}(1 - 0.74725) = \mathbf{-0.6659\sigma}$.
Compared to the global industry average benchmark of $\approx 50,000\text{ DPMO}$ ($+2.0\sigma\text{ to }+3.0\sigma$) and best-in-class targets ($<6,000\text{ DPMO}$, $>+4.5\sigma$), the baseline legacy process was statistically out of control, quantitatively establishing the need for automated ETL transformation.

> **Statistical Baseline Justification:** To account for operational skewness and extreme outliers in daily reporting performance, the **Median ($P_{50} = 1.140\text{ hrs}$)** was selected over the mean ($\mu$) to establish central tendency. The **25th Percentile ($P_{25} = 1.005\text{ hrs}$)** was designated as the **Upper Specification Limit ($USL$)**, grounding future targets in proven operational capability.

| Baseline Parameter / Metric                   | Variable Notation | Formula / Logic                | Baseline Value           |
| --------------------------------------------- | ----------------- | ------------------------------ | ------------------------ |
| **Total Evaluation Sample**                   | $N$               | Sample Count                   | **91 Days**              |
| **Current Process Median**                    | $P_{50}$          | `=PERCENTILE(Data, 0.50)`      | **$1.140\text{ Hours}$** |
| **Demonstrated Target Limit**                 | $USL\ (P_{25})$   | `=PERCENTILE(Data, 0.25)`      | **$1.005\text{ Hours}$** |
| **Non-Compliant Runs ($> 1.005\text{ hrs}$)** | $NC$              | `COUNTIF(Data, ">1.005")`      | **$68\text{ Days}$**     |
| **Defects Per Opportunity**                   | $DPO$             | $\frac{NC}{N} = \frac{68}{91}$ | **$0.7473\ (74.73\%)$**  |
| **Defects Per Million Opportunities**         | $DPMO$            | $DPO \times 1,000,000$         | **$747,252.75$**         |
| **Baseline Process Sigma**                    | $Z$               | $\Phi^{-1}(1 - DPO)$           | **$-0.6659\sigma$**      |
## 3. ANALYZE PHASE
### 3.1 Root Cause Analysis (Lean Waste Identification)
Applying Lean methodologies helped isolate three major process wastes (_Muda_):
1. **Overprocessing:** Re-writing the same lookup and string manipulations every week to append new credit card actuals onto historical records.
2. **Motion / Searching:** Manually opening multiple sub-folders to access individual weekly workbooks distributed across overlapping monthly bounds (e.g., cross-month transition spans like `Week 31 - July` and `Week 31 - August`).
3. **Defects (Data Latency):** Delays in data synthesis meant that decision-makers received actual spend updates up to two weeks late, preventing real-time control over budget overruns.
### 3.2 Methodological Principles (Precision & Capability Shifting)
- **Precision Before Accuracy:** Optimization efforts focused first on eliminating process variance (achieving tight repeatable consistency) before re-centering the operational mean toward near-zero execution times.
- **Operational Axiom ("Today's $P_{25}$ becomes Tomorrow's $P_{50}$"):** Rather than imposing unverified stretch goals, the project targeted converting the historical 25th percentile performance ($1.005\text{ hours}$) into the new standard operational baseline through structural automation.
### 3.2 Process Friction Points & Edge Cases
- **Cross-Month Fragmentation:** Weekly records occasionally overlapped calendar months, creating data double-counting risks in legacy pivot structures.
- **Employee Lifecycle Exceptions:** Standard lookups failed for employee rows marked as _Resigned_ or _Terminated_ when processing historical transactions, generating lookup breaks (`#N/A`) that broke the reporting layer.
## 4. IMPROVE PHASE
### 4.1 Automated ETL Pipeline Engineering (Power Query)
To remove manual consolidation steps, an automated ETL pipeline was constructed within the Power Query engine using advanced M-Code scripts.
- **Dynamic Folder Ingestion:** Replaced single-file workbooks with a folder query routine that scans directories, reads raw metadata, filters out temporary file instances, and appends rows into a single table.
- **Schema Standardization:** Standardized raw transactions across inconsistent columns, forcing data alignment by data types: `Unique Id` (Text), `Amount spent` (Decimal Number), `Spend date` (Date), and `GL Numbers` (Integer).
- **Automated Data Enrichment:** Developed structural transformations to handle lifecycle flags seamlessly without stopping query execution or generating missing lookup errors.
### 4.2 Data Model Architecture (Star Schema)
The flat, unlinked sheets were converted into a fully integrated relational **Star Schema** within Power BI to support lightning-fast filtering and multi-dimensional analysis.
```
       ┌────────────────────────┐         ┌────────────────────────┐
       │   dim_GeneralLedger    │         │      dim_Employee      │
       └───────────┬────────────┘         └───────────┬────────────┘
                   │                                  │
                   │  1:N                        1:N  │
             ┌─────▼──────────────────────────────────▼─────┐
             │              fact_CreditCardActuals          │
             └─────▲──────────────────────────────────▲─────┘
                   │  N:1                        N:1  │
                   │                                  │
       ┌───────────┴────────────┐         ┌───────────┴────────────┐
       │     dim_Department     │         │     fact_BudgetTargets │
       └────────────────────────┘         └────────────────────────┘
```
- **Dimension Tables (Lookup Tables):** Isolated master records into pure structural catalogs (`dim_Employee`, `dim_Department`, `dim_GeneralLedger`).
- **Fact Tables (Data Tables):** Aggregated operational spending instances into transactional tables, joined to dimension tables using clean, validated **1:Many ($1:\!*$) relationships** to ensure strict referential integrity.
## 5. CONTROL PHASE
### 5.1 Global Portability Parameterization
To decouple the relational model from hardcoded local computer drives, a global string parameter path (`FolderPath`) was configured inside the Power Query engine.
```code
// Example Power Query Parameterization M-Code
let
    Source = Folder.Files(FolderPath)
in
    Source
```
This ensures that external users, auditors, or executives can update the root path globally via a single parameter input box in Power BI without needing to modify individual queries.
### 5.2 Process Capability Gains & Results
**Following the July 1st Power BI Go-Live, the daily active latency was crushed to 0.03 hours ($\approx 1.8$ minutes). Consequently, the total cumulative batch cycle time dropped from 48 hours down to an on-demand, single-click refresh, permanently eliminating the end-of-period bottleneck.**
The implementation of the new data solution delivered major quantifiable improvements across key performance indicators:

| **Performance Metric**                 | **Legacy Baseline State (N=91)** | **Automated State (Power BI)**          | **Quantitative Improvement** |
| -------------------------------------- | -------------------------------- | --------------------------------------- | ---------------------------- |
| **Data Processing Cycle Time**         | $36 - 48\text{ Hours}$           | $< 2\text{ Minutes}$                    | **> 99.9% Reduction**        |
| **Process Median Latency ($P_{50}$)**  | $1.140\text{ Hours}$             | $0.030\text{ Hours}\ (1.8\text{ mins})$ | **97.4% Latency Shift**      |
| **Defect Rate ($> 1.005\text{ hrs}$)** | $68\text{ Days}\ (74.73\%)$      | $0\text{ Days}\ (0.00\%)$               | **100% Elimination**         |
| **Defects Per Million ($DPMO$)**       | $747,252.75$                     | $0.00$                                  | **747k DPMO Eradicated**     |
| **Process Sigma Level Score ($Z$)**    | **$-0.6659\sigma$**              | **$\ge +6.00\sigma$**                   | **Achieved 6-Sigma Level**   |
| **Human Ingestion Defects**            | Frequent (Lookup breaks)         | $0\text{ (Automated System)}$           | **100% Elimination**         |
| **Data Update Latency**                | $7 - 14\text{ Days}$             | On-Demand Refresh                       | **Real-Time Capability**     |
### 5.3 Sustainability Plan & Standard Operating Procedures (SOP)
To maintain the process improvements long-term:
1. **Source File Rule:** All new credit card transaction outputs must be dropped directly into their respective structured directories (`Year\Monthly\` or `Year\Weekly\`) using consistent names without changing column configurations.
2. **Master Data Review:** Any adjustments to corporate hierarchies, new cost center adds, or employee off-boardings must be updated in the central reference spreadsheet (`Company Data.xlsx`) to prevent data dropping during scheduled refreshes.