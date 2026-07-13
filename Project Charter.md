Here is a complete, enterprise-grade **Executive Project Charter** tailored specifically to Lean Six Sigma + FP&A automation project. It formally frames manual data consolidation challenges as process "defects" and highlights Power Query/Power BI implementation as the optimal "Improve" phase breakthrough.
# 📋 Executive Project Charter
**Project Name:** Automated SG&A Expenses (T&E) Reporting Process Transformation;
**Methodology:** Lean Six Sigma (DMAIC Framework);
**Project Sponsor:** Director Level Management / CFO;
**Process Owner:** FP&A Team;
## 1. Business Case & Project Background
In corporate Financial Planning & Analysis (FP&A), managing and reporting Selling, General, and Administrative (SG&A) expenses—specifically Travel & Entertainment (T&E)—is critical for cost control and variance management. Historically, the compilation of these reports relied entirely on manual extraction, alignment, and formatting across multiple disparate datasets.
As the volume of weekly transactions and monthly book-closes scales throughout the fiscal year, this manual mechanism presents a severe operational bottleneck. It delays decision-making, introduces data-integrity risks, and prevents the finance team from performing higher-value predictive analytics. Transitioning to an automated, parameterized ETL pipeline is essential to guarantee corporate agility and reporting scalability.
## 2. Problem & Goal Statements
### 🚨 Problem Statement
The current manual T&E expense data consolidation process requires cross-referencing six independent data sources (Employee Master, Chart of Accounts, Department Catalogs, P&L Group hierarchies, and various Target Budgets).
- **Defects (Cycle Time):** Gathering, transforming, and pushing these data fragments into legacy spreadsheet reports generates a cycle time of **36 to 48 operational hours** per reporting cycle.
- **Defects (Quality):** Manual copy-pasting creates frequent human errors, broken lookups, and reconciliation mismatches, causing data latency that renders weekly insights outdated by the time they reach department directors.
### 🎯 Goal Statement
To reduce the end-to-end reporting cycle time from **48 hours to near-instantaneous (under 2 minutes)** via an automated Power Query ETL pipeline and an interactive Power BI dashboard by the end of the implementation cycle. The goal is to eliminate 100% of manual data manipulation defects, establish data-refresh capabilities, and achieve a stable process capability index ($C_p$) for data integrity.
## 3. Project Scope

|**In-Scope (What is Included)**|**Out-of-Scope (What is Excluded)**|
|---|---|
|• Integration of multi-year operational credit card data (2025–2026 Actuals).|• Modifying upstream ERP/Accounting system transaction entries.|
|• Consolidation of Master Data sets (Employees, Departments, GL Accounts).|• Strategic budgeting re-forecasting logic (handled by management).|
|• Automation of both Weekly and Monthly budget-variance calculations.|• Automated email distribution infrastructure (e.g., Power Automate).|
|• Parameterization of the data source path for global model portability.|• Managing non-SG&A corporate expenditure streams (e.g., CAPEX).|
## 4. Process Boundaries (SIPOC Framework)
- **Suppliers:** Accounting/ERP Team, HR Department, PMO/Finance Budget Owners.
- **Inputs:** 2025/2026 Weekly & Monthly Actuals (Credit Card Sheets), Master Employee List, Chart of Accounts (GL List), Department Hierarchies, Weekly/Monthly Target Budgets.
- **Process:** Extract raw transaction and target matrices $\rightarrow$ Apply M-Code schema transformations in Power Query $\rightarrow$ Formulate dynamic relationship mappings $\rightarrow$ Generate automated variance visualizations.
- **Outputs:** Interactive Power BI Star-Schema Model (`Variance Analysis.pbix`), Automated Budget Variances, YTD Expenditures, and Dynamic Managerial Dashboards.
- **Customers:** Director-Level Managers (L1/L2), FP&A Leadership, Corporate Executive Teams.
## 5. Critical to Quality (CTQ) Metrics
To track process capability, the project measures success against three vital metrics:
1. **Cycle Time:** The absolute duration elapsed from receiving data inputs to delivering finalized reports to stakeholders. (Target: $<5$ minutes).
2. **Data Accuracy:** Zero variance between aggregated pipeline actuals and the finalized General Ledger accounting records. (Target: 100%).
3. **Portability / Maintainability:** Ability for external users to alter global directories through centralized parameter keys without code disruption. (Target: $<1$ minute).
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
## 7. Project Team Roles & Responsibilities
- **Six Sigma Green Belt / Data Architect:** _[PARTH JOSHI]_ — Responsible for process scoping, data modeling, Power Query pipeline engineering, and dashboard development.
- **Project Sponsor:** Finance Director / FP&A Lead — Responsible for approving business requirements, validating variance calculations, and auditing model outputs against corporate financial parameters.
- **Key Stakeholders:** Department Directors (L1) — End-users who consume data visualizations to manage operational expenditure targets.