Here is a complete, enterprise-grade **Executive Project Charter** tailored specifically to Lean Six Sigma + FP&A automation project. It formally frames manual data consolidation challenges as process "defects" and highlights Power Query/Power BI implementation as the optimal "Improve" phase breakthrough.
# 📋 Executive Project Charter
**Project Name:** Automated SG&A Expenses (T&E) Reporting Process Transformation
**Methodology:** Lean Six Sigma (DMAIC Framework)
**Project Sponsor:** Director Level Management / CFO
**Process Owner:** FP&A Team
## 1. Business Case & Project Background
In corporate Financial Planning & Analysis (FP&A), managing and reporting Selling, General, and Administrative (SG&A) expenses—specifically Travel & Entertainment (T&E)—is critical for cost control and variance management. Historically, the compilation of these reports relied entirely on manual extraction, alignment, and formatting across multiple disparate datasets.
As the volume of weekly transactions and monthly book-closes scales throughout the fiscal year, this manual mechanism presents a severe operational bottleneck. It delays decision-making, introduces data-integrity risks, and prevents the finance team from performing higher-value predictive analytics. Transitioning to an automated, parameterized ETL pipeline is essential to guarantee corporate agility and reporting scalability.
## 2. Problem & Goal Statements
### 🚨 Problem Statement
The current SG&A expense reporting process exhibits severe operational instability and excessive cycle time variance across 6 unlinked data sources: Employee Master, Chart of Accounts, Department Catalogs, P&L Group hierarchies, and various Target Budgets.
Over a 91-day baseline audit, Daily Reporting Latency exceeded the demonstrated capability target of $P_{25} = 1.005\text{ hours}$ on **68 out of 91 days** (process median $P_{50} = 1.140\text{ hours}$), resulting in a **74.73% Non-Compliance (NC) rate**. At its peak crisis window in late June, daily friction spiked to $2.70\text{ hours}$ of active error correction. 
These daily friction points compound into a cumulative batch lead time of **36 to 48 operational hours** per reporting cycle. Statistically, the baseline process operates at **747,252.75 DPMO** with a **Process Sigma Score of -0.6659σ**, severely underperforming industry standard benchmarks (50,000 DPMO / +2.0σ to +3.0σ).
### 🎯 Goal Statement
To execute a leftward distribution shift in Daily Reporting Latency, transitioning the process median from $P_{50} = 1.140\text{ hours}$ to the demonstrated capability limit of $P_{25} = 1.005\text{ hours}$—and ultimately to $<0.03\text{ hours}$ ($<1.8\text{ minutes}$) via an automated Power Query ETL pipeline and Power BI dashboard. 
The objective is to reduce total batch lead time from **48 hours to < 2 minutes**, eliminate 100% of human-reconciliation errors, reduce DPMO from **747,252.75 to 0**, and elevate the Process Sigma Score from **-0.6659σ to ≥ 6.00σ**.
## 3. Project Scope
| **In-Scope (What is Included)**                                               | **Out-of-Scope (What is Excluded)**                                   |
| ----------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| • Integration of multi-year operational credit card data (2025–2026 Actuals). | • Modifying upstream ERP/Accounting system transaction entries.       |
| • Consolidation of Master Data sets (Employees, Departments, GL Accounts).    | • Strategic budgeting re-forecasting logic (handled by management).   |
| • Automation of both Weekly and Monthly budget-variance calculations.         | • Automated email distribution infrastructure (e.g., Power Automate). |
| • Parameterization of the data source path for global model portability.      | • Managing non-SG&A corporate expenditure streams (e.g., CAPEX).      |
## 4. Process Boundaries (SIPOC Framework)
- **Suppliers:** Accounting/ERP Team, HR Department, PMO/Finance Budget Owners.
- **Inputs:** 2025/2026 Weekly & Monthly Actuals (Credit Card Sheets), Master Employee List, Chart of Accounts (GL List), Department Hierarchies, Weekly/Monthly Target Budgets.
- **Process:** Extract raw transaction and target matrices $\rightarrow$ Apply M-Code schema transformations in Power Query $\rightarrow$ Formulate dynamic relationship mappings $\rightarrow$ Generate automated variance visualizations.
- **Outputs:** Interactive Power BI Star-Schema Model (`Variance Analysis.pbix`), Automated Budget Variances, YTD Expenditures, and Dynamic Managerial Dashboards.
- **Customers:** Director-Level Managers (L1/L2), FP&A Leadership, Corporate Executive Teams.
## 5. Critical to Quality (CTQ) Metrics
To track process capability, the project measures success against three vital metrics:
1. **Cycle Time:** The absolute duration elapsed from receiving data inputs to delivering finalized reports to stakeholders (Target: **$< 2$ minutes**).
2. **Data Accuracy:** Zero variance between aggregated pipeline actuals and finalized General Ledger accounting records (Target: **100% Accuracy / 0 DPMO**).
3. **Portability / Maintainability:** Ability for external users to alter global directories through centralized parameter keys without code disruption (Target: **$< 1$ minute parameter setup**).
## 6. Project Milestones & Timeline (DMAIC)
```
[Define] ───► [Measure] ───► [Analyze] ───► [Improve] ───► [Control]
 Formalize     Quantify       Isolate Process   Build ETL    Parameterize &
 Charter &     Baseline       Bottlenecks &    Pipeline &    Deploy Standard
 Scope         Defects        Error Sources    Dashboards    Operating Procedure
```
- **Define:** Establish the charter, baseline problem scopes, and document process stakeholders (Completed).
- **Measure:** Map legacy folder dependencies, catalog the 6 source schemas, and record manual calculation cycle times (Completed).
- **Analyze:** Isolate structural breakages caused by manual reconciliations and find the root causes behind data pipeline latencies (Completed).
- **Improve:** Engineer a parameterized ETL framework inside the Power Query engine and design a relational Star-Schema dashboard in Power BI (Completed).
- **Control:** Deploy a unified global path parameter framework to decouple model execution from local workstation paths; draft standard operating documentation to guarantee sustainability (In-Progress).
### 📈 Post-Implementation Performance Update (As of July 2026)
Following the July 1st Power BI Go-Live, the daily active latency was successfully crushed to 0.03 hours ($\approx 1.8$ minutes). Consequently, the total cumulative batch cycle time dropped from 48 hours down to an on-demand, single-click refresh, permanently eliminating the end-of-period bottleneck. The project is now concluding its final Control Phase documentation.
## 7. Project Team Roles & Responsibilities
- **Six Sigma Green Belt / Data Architect:** _[PARTH JOSHI]_ — Responsible for process scoping, data modeling, Power Query pipeline engineering, and dashboard development.
- **Project Sponsor:** Finance Director / FP&A Lead — Responsible for approving business requirements, validating variance calculations, and auditing model outputs against corporate financial parameters.
- **Key Stakeholders:** Department Directors (L1) — End-users who consume data visualizations to manage operational expenditure targets.