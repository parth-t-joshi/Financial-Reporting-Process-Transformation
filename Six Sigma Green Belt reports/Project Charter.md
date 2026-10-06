# Executive Project Charter

**Project Name:** SG&A (T&E) Variance Reporting Process Transformation  
**Methodology:** Lean Six Sigma DMAIC  
**Project Sponsor Role:** Finance leadership (Finance Director / FP&A Lead)  
**Process Owner Role:** FP&A Manager / FP&A Team  
**Production Go-Live:** July 1, 2026 — confirmed by the project owner  
**Documentation Revision:** October 6, 2026

## 1. Business Case and Background

The FP&A team prepares weekly and monthly budget-versus-actual reporting for Selling, General, and Administrative (SG&A) expenses, with a focus on Travel and Entertainment (T&E). The documented legacy workflow manually combined credit-card transaction files with employee, department, account and P&L-group reference mappings, plus weekly/monthly budget inputs.

Split weeks at month-end, changes in employee status, and repeated lookup and formatting work create preparation and reconciliation demands. This project applies Power Query transformations and a Power BI reporting model to reduce repetitive work and improve maintainability. Financial ROI and quantified time savings require verified costs and comparable time studies.

## 2. Problem and Goal Statements

### 2.1 Problem Statement

The current SG&A expense reporting process exhibits severe operational instability and excessive cycle time variance across 6 linked data sources: Employee Master, Chart of Accounts, Department Catalogs, P&L Group hierarchies, and various Target Budgets. Over a 91-day baseline audit, Daily Reporting Latency exceeded the demonstrated capability target of $P_{25} = 1.005\text{ hours}$ on **68 out of 91 days** (process median $P_{50} = 1.140\text{ hours}$), resulting in a **74.73% Non-Compliance (NC) rate**. At its peak crisis window in late June, daily friction spiked to $2.70\text{ hours}$ of active error correction. These daily friction points compound into a cumulative batch lead time of **36 to 48 operational hours** per reporting cycle. Statistically, the baseline process operates at **747,252.75 DPMO** with a **Process Sigma Score of -0.6659σ**, severely underperforming industry standard benchmarks (50,000 DPMO / +2.0σ to +3.0σ).

### 2.2 Goal Statement

Automate the documented transaction-ingestion and transformation steps, maintain usable historical employee/account mappings, and produce a maintainable SG&A budget-versus-actual model. Retain reconciliation and review before report delivery.

The proposed model-refresh target is **less than 2 minutes**. The **0.029-hour (1.74-minute) workbook-derived reference** is a sample-derived historical threshold, not a second operating target; it is not an approved release threshold or achieved service level. The inherited **1.005-hour benchmark**, derived from a mixed 91-row range, is unvalidated and is not an upper specification limit.

Financial acceptance requires matched budget/actual period, grain, currency and budget version, with an explicit expense-variance sign convention. The proposed GL control requires an independent closed-GL actuals export or control-total source, not the chart of accounts. That source and the reconciliation implementation are not verified in the available inventory.

No percentage reduction, sigma level, DPMO capability result, or claim of error-free reporting is established by this charter.

## 3. Project Scope

| In scope | Out of scope |
| --- | --- |
| Integrating documented 2025–2026 credit-card transaction inputs | Changing upstream ERP/accounting transaction entries |
| Mapping employee, department, GL-account, and P&L-group reference data | Strategic budget reforecasting decisions |
| Automating weekly/monthly budget-versus-actual transformations | Automated email-distribution infrastructure, including Power Automate |
| Parameterizing the data-source path for model portability | Managing non-SG&A expenditure streams such as CAPEX |
| Defining filing, reconciliation, exception, and monitoring procedures | Claiming deployed scheduled refresh or alerting without configuration evidence |

## 4. Process Boundaries (SIPOC)

- **Suppliers:** Accounting/ERP team, HR data owners, and FP&A budget owners.
- **Inputs:** Weekly/monthly credit-card actuals, Employee Master, Chart of Accounts, department/P&L mappings and weekly/monthly budgets; independent closed-GL actuals/control totals are required for the proposed reconciliation and remain to be identified.
- **Process:** Extract inputs → validate and file → transform and map in Power Query → refresh Power BI → reconcile and review → deliver outputs.
- **Documented outputs:** Variance Analysis.pbix, expense aggregates, budget variances, year-to-date views and managerial reports; direct model/measure inspection and retained review evidence remain pending.
- **Customers:** Department managers (L1/L2), FP&A leadership, and corporate finance leadership.

See [[Brief Overview of the reporting process]] for the source inventory and [[DMAIC Report]] for the phase narrative.

## 5. Critical-to-Quality Measures and Targets

| Measure | Definition | Target | Evidence required |
| --- | --- | --- | --- |
| Model-refresh duration | Start of refresh to successful model-refresh completion | Less than 2 minutes; 0.029-hour workbook reference pending target review | Dated start/end records, environment, input volume, and successful completion |
| End-to-end reporting lead time | Receipt of required inputs to delivery of the reconciled and reviewed report | To be set after a comparable baseline is established | Input-receipt, reconciliation, review, and delivery timestamps |
| GL reconciliation gap | Model actuals minus independent closed-GL actuals for the same period, currency, accounts and scope | Proposed $0.00 gap at documented amount precision and rounding | Independent GL export/control totals, comparison and resolved exceptions; the source and implementation remain unverified, and a zero total gap alone does not prove record accuracy |
| Input completeness and mapping | Expected source coverage, required fields, and usable employee/account/department keys | No unresolved missing files, duplicate transactions, or unmapped keys at release | Source inventory, exception logs, and reviewed resolution |
| Path configuration | Configure the maintained FolderPath and verify it resolves to the local Variance Analysis folder | Less than 1 minute | Setup timing and a successful source-access check |

The numerical targets above are proposed operational targets. They do not establish achieved performance or statistical control limits. [[SOP#7. Control Matrix|SOP Control Matrix]] owns ongoing monitoring and corrective responses.

## 6. Project Milestones and Status

| DMAIC phase | Documented deliverable | Status and date evidence |
| --- | --- | --- |
| Define | Charter, scope, SIPOC, and proposed targets | Documented; formal approval date not recorded here |
| Measure | Source inventory and historical timing workbook | Available; chronology and measurement definitions require reconciliation |
| Analyze | Fishbone hypotheses and Pareto activity allocation | Documented; causal validation and timing basis require verification |
| Improve | Documented Power Query changes and Power BI model | Production go-live confirmed **July 1, 2026**; implementation inspection and comparable outcome validation remain pending |
| Control | SOP, control matrix, operational records, and statistical monitoring method | Documentation revised **October 6, 2026**; deployment evidence and formal approval are not asserted |

The historical workbook remains unchanged. Its recorded dates must be reconciled rather than replaced to match the confirmed production date. Numerical verification belongs in [[DMAIC Phase 4 - Improve Phase Report & Implementation Verification]], supported by [[Evidence Reconciliation|Evidence Reconciliation]].

## 7. Project Team Roles and Responsibilities

- **Project Lead — Parth Joshi:** Process scoping, source mapping, Power Query transformation design, Power BI model design documentation and technical change review. This describes project contribution, rather than a verified job title or certification.
- **Project Sponsor Role — Finance leadership (Finance Director / FP&A Lead):** Business-requirement review, validation priorities and approval of material changes.
- **FP&A Analyst / Process Operator:** Transaction filing, reference-data maintenance, refresh execution, reconciliation, and retained run evidence.
- **FP&A Manager:** Review of reporting exceptions, reconciliations, and release decisions.
- **Department Managers (L1/L2):** Consumers of expense and variance reporting for their departments.

These are documented role responsibilities; appointments, professional credentials and approval records are not verified by this revision.
