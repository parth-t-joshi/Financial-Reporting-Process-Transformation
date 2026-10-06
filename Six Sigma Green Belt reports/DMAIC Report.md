# Lean Six Sigma DMAIC Project Case Study

**Project Title:** SG&A (T&E) Variance Reporting Process Transformation  
**Methodology:** Lean Six Sigma DMAIC  
**Business Domain:** Financial Planning & Analysis (FP&A)  
**Production Go-Live:** July 1, 2026 — confirmed by the project owner  
**Documentation Revision:** October 6, 2026

> [!important] Evidence status
> The project owner confirmed production go-live as July 1, 2026; deployment records have not been independently verified. The dates and phase labels in Historical Data Analysis.xlsx conflict with that chronology. The original workbook is retained, and its numerical summaries are provisional until the measurement definitions and phase membership are reconciled. See [[Evidence Reconciliation|Evidence Reconciliation]].

## 1. Define Phase

### 1.1 Project Background and Business Case

The FP&A team prepares weekly and monthly budget-versus-actual reporting for Selling, General, and Administrative (SG&A) expenses, focusing on Travel and Entertainment (T&E). The documented legacy process used manual consolidation, lookups, and formatting across transaction workbooks and reference datasets. Cross-month weeks and employee-status changes added reconciliation work before reports could be reviewed by department managers.

The business case is to reduce repetitive preparation work and improve the traceability of expense reporting through Power Query transformations and a Power BI model. Financial return on investment has not been established by the available evidence.

### 1.2 Problem Statement

The legacy T&E reporting mechanism required manual collection and relational mapping across 6 unlinked data systems (Employee Catalog, Chart of Accounts/GL Master, Department Master List, P&L hierarchy maps, and multiple Target Budgets).

- **Cycle Time Defect:** Manual extraction, restructuring, and report formulation generated a total batch lead time of **36 to 48 business hours** per reporting iteration.
- **Daily Ingestion Friction:** Over a 91-day baseline evaluation, Daily Reporting Latency exceeded the demonstrated capability threshold ($P_{25} = 1.005\text{ hours}$) on **68 out of 91 days** (process median $P_{50} = 1.140\text{ hours}$), reaching a peak spike of **2.70 hours** in late June.
- **Quality & Capability Defect:** Manual operations generated a **74.73% Non-Compliance (NC) rate**, translating to **747,252.75 DPMO** and a **Baseline Process Sigma Score of -0.6659σ**, indicating an out-of-control operational state. In other words, performance is lower than statistical goal. i.e. NC = 74.73%; with DPMO value of 747,252.75 and sigma score of -0.6659.

### 1.3 Project Goal Statement

To execute a leftward distribution shift in Daily Reporting Latency, transitioning the process median from $P_{50} = 1.140\text{ hours}$ to the demonstrated benchmark of $P_{25} = 1.005\text{ hours}$—and ultimately to $<0.03\text{ hours}$ ($<1.8\text{ minutes}$) via an automated Power Query ETL engine and interactive Star-Schema data model in Power BI. The objective includes reducing batch cycle time from **48 hours to under 2 minutes**, maintaining 100% data integrity, eliminating human-reconciliation defects ($0\text{ DPMO}$), and elevating overall process capability to **≥ 6.00σ**.

### 1.4 Process Boundaries (SIPOC)

- **Suppliers:** Accounting/ERP administrators, HR data owners, and FP&A budget owners.
- **Inputs:** Weekly and monthly credit-card transactions, Employee Master, Chart of Accounts, department/P&L mappings, and weekly/monthly budgets.
- **Process:** Extract transactions → validate inputs → transform and map data in Power Query → refresh the Power BI model → reconcile and review → deliver the reporting output.
- **Outputs:** Variance Analysis.pbix, expense aggregates, budget-versus-actual views, and reviewed reporting outputs.
- **Customers:** Department managers (L1/L2), FP&A leadership, and corporate finance leadership.

See [[Project Charter]] for scope, roles, and targets.

## 2. Measure Phase

### 2.1 Legacy Process Map

~~~text
Raw Inputs Received → Manual Validation → Excel Lookups → Static Pivot Build → Review and Email to L1/L2
~~~

This is the documented legacy workflow. The refreshed model is one step in the redesigned reporting process; its execution time does not cover every step above.

### 2.2 Source and Folder Inventory

The documented transaction layout separates year, month, and week:

- `Variance Analysis/2025/Monthly/` and `Variance Analysis/2025/Weekly/` hold prior-year transactions.
- `Variance Analysis/2026/Monthly/` and `Variance Analysis/2026/Weekly/` hold current-year transactions.
- `Company Data.xlsx` contains the documented General Ledger account reference (chart of accounts), Department List, Employee Data, and budget records. A chart of accounts does not establish closed-period GL actuals or control totals.
- P&L-group mappings connect departments and reporting leaders; their source must be included in the maintained inventory.
- An independent closed-GL actuals export or Accounting control-total source is still required for the proposed reconciliation control; record its owner, period, currency, scope, and adjustment treatment.

[[Brief Overview of the reporting process]] owns the source inventory and naming examples. [[SOP]] owns the operational filing and maintenance rules.

### 2.3 Measurement Definitions and Evidence Boundaries

| Measure | Existing source statement | Verification needed |
| --- | --- | --- |
| Weekly reporting timing | Reported estimate: 48 hours | Start/end events, elapsed versus labor time, participants, and reporting period |
| Monthly reporting timing | Reported estimate: 36 hours | Same timing basis as weekly reporting; review and delivery coverage |
| Manual activity breakdown | Pareto table totals 42 hours across five activities | Measurement period, labor versus elapsed time, sampling, and overlaps |
| Daily Reporting Latency (DRL) | Workbook timing records and existing calculation summaries | Recorded dates, production phase, units, start/end events, and whether manual effort or refresh execution is measured |
| Model-refresh duration | Proposed target: less than 2 minutes | Consistent refresh start/completion records; input volume and environment |
| Reporting lead time | Input receipt to reviewed output delivery | Separate time study covering ingestion, reconciliation, review, and distribution |

Neither the 42-hour activity total nor the 36/48-hour estimates establishes a validated baseline for refresh execution. No before-and-after reduction percentage is reported here.

### 2.4 Statistical Measurement Approach

Use the median ($P_{50}$) to summarize timing data when outliers or skew affect the mean, and report the mean, quartiles, sample standard deviation ($s$), sample count, and measurement window alongside it. Consistency and performance against an agreed target should be assessed separately. A low spread alone does not establish reporting accuracy.

The inherited $P_{25} = 1.005\text{ hours}$ is an internal improvement benchmark calculated from a mixed source range, with unverified baseline applicability. Historical percentiles can inform proposed targets, but they do not establish customer specifications or guarantee future performance. Retain $0.029\text{ h}$ as a sample-derived historical threshold; distinguish it from the proposed under-two-minute operating target and from statistical control limits.

After the dates and timing definitions are reconciled, calculate summaries for explicitly defined pre- and post-go-live groups using the confirmed **July 1, 2026** boundary. Do not relabel or replace recorded source dates to obtain a desired result. See [[Statistical Baselining & Continual Improvement Framework]] for definitions and [[Evidence Reconciliation|Evidence Reconciliation]] for source issues.

## 3. Analyze Phase

### 3.1 Root-Cause Hypotheses and Lean Waste

The project documentation identifies the following mechanisms for investigation:

1. **Overprocessing:** Repeating lookups, text transformations, and pivot formatting when new credit-card files arrive.
2. **Motion and searching:** Opening separate year/month/week workbooks, including split-week files such as Week 31 - July and Week 31 - August.
3. **Defects and rework:** Lookup exceptions, missing mappings, and duplicate-transaction risks that require correction before report release.

[[DMAIC Root Cause Identification (Fishbone)]] presents the causal hypotheses. [[Process Optimization Bottlenecks (Pareto Chart)]] presents the reported 20/11/6/3/2-hour activity allocation. That allocation prioritizes investigation; it does not prove the amount of lead time removed by automation.

### 3.2 Process Friction Points and Edge Cases

- **Cross-month transactions:** Weekly files can span calendar months. Actuals for closed months and weekly work-in-progress must be combined using an explicit precedence rule to avoid double counting.
- **Employee lifecycle changes:** Historical expense transactions must retain their employee mapping after resignation or termination. Verify whether department attribution uses the transaction-date assignment or the current hierarchy; retaining employee IDs alone does not preserve historical department assignments. Missing mappings should be investigated rather than silently excluded.
- **Schema variation:** A changed source header or data type can interrupt transformations. Approved source schemas and controlled mapping changes are required.
- **Portability:** Hardcoded drive paths make refreshes dependent on a workstation; a maintained source-path parameter reduces that dependency.

## 4. Improve Phase

### 4.1 Documented Power Query Changes

The existing project documentation describes these engineering changes:

- **Folder ingestion:** Queries read file metadata, exclude temporary files, and append transaction rows from the maintained directories.
- **Schema normalization:** The documented core fields are Unique Id, Amount spent, Spend date, and GL Numbers. Verify identifier formats before selecting types: employee and GL identifiers must retain significant leading zeros and alphanumeric characters. Document amount precision and rounding separately from display formatting.
- **Data enrichment:** Transactions are mapped to employee, department, and account reference data, including employee-status handling.
- **Path parameterization:** A FolderPath parameter points to the local Variance Analysis folder so source paths can be configured centrally.

Illustrative M syntax for file enumeration only:

~~~powerquery
let
    Source = Folder.Files(FolderPath)
in
    Source
~~~

`Folder.Files` enumerates files in the selected folder and its subfolders; this example does not demonstrate file filtering, workbook transformation, enrichment, or row combination. [Microsoft: Folder.Files](https://learn.microsoft.com/en-us/powerquery-m/folder-files). The actual implementation must show transaction-only inclusion rules for the year/month/week layout and exclusion of reference workbooks, temporary files, and other unrelated content.

These are documented features. The PBIX queries and deployed environment have not been inspected as part of this documentation reconciliation. Provide representative actual M queries and a refresh demonstration before describing the pipeline as verified implementation evidence.

### 4.2 Conceptual Data Model

The documented design uses actuals and budget facts with dimension tables. The diagram below is conceptual and shows shared dimensions, including a proposed calendar for review; it is not a verified rendering of the PBIX relationships or evidence that the actual model lacks time relationships. Additional dimensions and relationship cardinalities depend on the grain of the actual and budget data.

~~~mermaid
flowchart TB
    D["dim_Department"] --> A["fact_CreditCardActuals"]
    D --> B["fact_BudgetTargets"]
    G["dim_GeneralLedger"] --> A
    G --> B
    E["dim_Employee"] --> A
    T["Calendar (proposed; verify actual design)"] -.-> A
    T -.-> B
~~~

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

Validate keys, grain, unmatched records, relationship direction, and cardinality in the actual model. Record the row grain of transactions and each weekly/monthly budget input, the reporting calendar and year-to-date definition, and how periods align. Demonstrate cross-month week handling and prevent a budget from appearing at employee or transaction detail unless a documented allocation supports that comparison. Budget facts should connect through applicable shared dimensions; the conceptual diagram does not directly join actuals to budgets. [Microsoft: Star schema guidance](https://learn.microsoft.com/en-us/power-bi/guidance/star-schema).

Supply a screenshot or exported diagram of the actual model, the actual DAX measures used for budget-versus-actual analysis, and report screenshots with a worked financial example. Label proposed designs separately from inspected implementation artifacts.

[[Variance Analysis/Power BI Implementation Evidence]] records the implementation artifacts required for review. [[FP&A Analysis and Reconciliation]] defines the proposed financial presentation and independent reconciliation evidence.

### 4.3 Implementation Verification and Results

**The project owner confirmed production go-live as July 1, 2026.** Deployment records have not been independently verified. The current workbook chronology conflicts with that date, so the source summaries cannot yet establish validated pre- and post-implementation windows.

[[Statistical Baselining & Continual Improvement Framework]] owns the full descriptive source summaries and measurement definitions. [[DMAIC Phase 4 - Improve Phase Report & Implementation Verification]] owns implementation acceptance and handoff evidence. Percentage reductions, validated 91-day pre/post comparisons, process capability scores, and claims of eliminated reporting errors are withheld pending reconciliation.

Verification must establish:

1. Recorded timing dates and phase membership, with the original workbook preserved.
2. Comparable timing definitions and environments across the measurement groups.
3. Input completeness, duplicate handling, historical department attribution, and an independently sourced actual-versus-GL reconciliation for the same period and scope.
4. Representative actual M queries, DAX measures, model relationships and budget/time grains, report outputs, and any deployed refresh or notification settings against the documented design.

## 5. Control Phase

### 5.1 Operational Monitoring

[[SOP#7. Control Matrix|SOP Control Matrix]] is the authoritative control plan. It specifies source-path, filing, schema, completeness, reconciliation, and refresh-duration checks, with frequencies, owners, and corrective responses. Record each run's date, input period, source files, refresh start/end, exceptions, reconciliation result, and release decision.

### 5.2 Statistical Monitoring and Response

[[Statistical Process Control (SPC)]] owns the statistical chart methodology. Control limits must be calculated from validated measurements and documented with the applicable window; an observed maximum or an operational target must not be substituted for a calculated limit.

Until that method is established, use the SOP's operational checks and agreed targets. A failed refresh, unresolved mapping, duplicate issue, or reconciliation gap triggers correction or escalation before release. Timing above the proposed target prompts investigation; it does not by itself establish statistical instability or a reporting defect.

### 5.3 Maintenance and Ownership

The FP&A analyst maintains transaction filing, reference data, and run records. The data architect handles intentional schema and query changes; the FP&A manager reviews unresolved exceptions and report-release decisions. Follow [[SOP#6. Exception Handling and Release Decision|SOP exception handling]] and the semi-annual SOP review cycle. These are documented operating responsibilities, not proof of individual appointments or approvals. The project owner confirmed production go-live; completion or formal approval of all Control deliverables is not asserted here.
