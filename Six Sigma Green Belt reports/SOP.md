# Standard Operating Procedure (SOP)

**Process Name:** SG&A (T&E) Variance Reporting and Data Maintenance  
**Version:** 1.4  
**Effective Date Recorded in Original SOP:** July 11, 2026  
**Documentation Revision Date:** October 6, 2026  
**Review Cycle:** Semi-annual  
**Process Owner Role:** FP&A Manager / FP&A Team

> [!note] Revision status
> Version 1.4 is an editorial and control-documentation revision. It preserves the original effective date and does not assert process-owner approval, verified role appointments, deployed alerting, or verified performance. Evidence issues are tracked in [[Evidence Reconciliation|Evidence Reconciliation]].

## 1. Purpose and Scope

This procedure covers weekly and monthly Travel and Entertainment (T&E) expense inputs within SG&A reporting: extraction, transaction filing, reference-data maintenance, path configuration, Power BI refresh, reconciliation, exception handling, and release review.

The documented system uses Power Query and `Variance Analysis.pbix`, with reference data in `Company Data.xlsx`. This SOP describes the operator workflow and is the authoritative home for the control matrix. The PBIX and service configuration have not been inspected in this documentation revision; verify the named tables, measures, and checks in the deployed model before relying on them.

## 2. Roles and Responsibilities

- **Accounting Clerks / Expense Admins:** Extract credit-card transaction files and place them in the maintained folders without changing the approved source schema.
- **FP&A Analyst / Process Operator:** Maintain reference records, refresh the model, inspect input coverage and exceptions, reconcile actuals, and retain run evidence.
- **Data Architect:** Review intentional schema changes, maintain queries and model relationships, and resolve technical exceptions.
- **FP&A Manager:** Review unresolved anomalies, reconciliation exceptions, and report-release decisions; maintain budget targets.

These are documented operating roles; verified appointments and approval records are not supplied. Finance leadership (Finance Director / FP&A Lead) is the sponsor role described in [[Project Charter]].

## 3. Prerequisites

1. Use the team's supported Power BI Desktop version and Microsoft Excel. Record the software version when collecting refresh timings.
2. Confirm required read/write access to the working Financial-Reporting-Process-Transformation/ folders.
3. Confirm the approved source export layout, current reference workbook, expected input periods, and reporting cutoff.
4. If a deployed model uses a scheduled refresh, verify its credentials, accessible source path, and relevant configuration separately. Scheduled execution is not assumed by this desktop procedure.
5. Identify an independent closed-GL actuals export or control-total source for the proposed reconciliation, with matching period, currency, accounts and scope. The available inventory does not identify this source; `General Ledger` reference mappings are not GL actual balances.

## 4. Operational Workflow

### 4.1 Extract and File Transaction Inputs

1. Extract the weekly or monthly credit-card actuals from the ERP or banking platform.
2. Preserve the raw export. Do not rename headers, inject formulas, delete rows, or change types to bypass an exception. Retain the original file if a corrected export is needed.
3. Use the maintained year and reporting-interval folders. Examples for 2026:
   - Weekly work-in-progress: `Variance Analysis/2026/Weekly/`
   - Closed-month actuals: `Variance Analysis/2026/Monthly/`
1. Follow the documented filename convention: `Credit_Cards_Data - 01 January.xlsx` for monthly files and `Credit_Cards_Data - Week 01 - January.xlsx` for weekly files. Split weeks may have separate month-labelled files; preserve that distinction and validate their date coverage.
2. Check expected periods and source-file coverage. Confirm how closed-month actuals supersede weekly work-in-progress for the same period before release. Do not append overlapping files without checking duplicates and the model's precedence rule.

See [[Brief Overview of the reporting process]] for naming examples and source inventory.

### 4.2 Maintain Reference Data (`Company Data.xlsx`)

Update reference data before refreshing:

- **Employees:** Append new employee records to Employee Data. Record departures using the maintained status value (the documented value is Resigned); retain historical employee rows and keys.
- **Departments and GL accounts:** Add new codes to Department List or General Ledger, with their maintained hierarchy mappings.
- **P&L groups and reporting leaders:** Keep department-to-leader mappings current in the documented reference source.
- **Budgets:** Update the relevant weekly/monthly budget records using the approved period and reporting scope.

Check for duplicate keys, missing mappings, and unintended historical changes. Escalate intentional structural changes to the data architect.

Retaining employee rows and keys does not establish historical department/hierarchy reporting. Confirm whether reports use transaction-date assignments or current assignments before changing mappings; the existing policy and any effective-date handling are unverified. Record budget version, calendar and comparison grain; do not sum weekly and monthly targets for the same scope without an approved rule.

The documented transaction fields are `Unique Id` (Text), `Amount spent` (Decimal Number), `Spend date` (Date), and `GL Numbers` (Integer). Their presence and types in the PBIX remain unverified. Confirm what `Unique Id` identifies, its uniqueness grain and null/duplicate rules before using it as a transaction or employee key. Preserve GL identifiers as supplied; verify leading-zero or alphanumeric requirements before approving any numeric conversion. Document currency, stored precision and rounding for amounts: Decimal Number uses floating point, whereas Fixed Decimal Number is exact to four decimal places. This is a validation requirement, not a change to the documented PBIX schema. [Microsoft Power Query data types](https://learn.microsoft.com/en-us/power-query/data-types).

### 4.3 Configure the Source Path and Refresh

1. Open `Variance Analysis.pbix` in Power BI Desktop.
2. When the working folder or workstation changes, open **Home → Transform Data → Edit Parameters**. In the Power Query Editor, the equivalent configuration is under **Manage Parameters**.
3. Set FolderPath to the local Variance Analysis folder, for example:

   ~~~text
   C:\Users\YourName\Documents\GitHub\Financial-Reporting-Process-Transformation\Variance Analysis
   ~~~

4. Confirm/apply the parameter change and verify source access.
5. Record the refresh start time, click **Refresh**, and record successful completion or the error. Include input volume and environment when measuring duration.
6. Inspect source coverage, mapping exceptions, and relevant reporting totals before reconciliation. A completed refresh alone does not authorize release.

The proposed refresh target is **less than 2 minutes**. The **0.029-hour (1.74-minute) workbook-derived reference** is a sample-derived historical threshold, not a second operating target. It is not an approved release threshold, statistical control limit or verified service level.

## 5. Reconciliation and Report Review

1. Check source-to-model totals, input completeness and mappings for every reporting run. For the proposed month-end GL control, obtain independent closed-GL actuals for the same period, currency, accounts and scope. Record any differences in credit-card versus GL coverage, including accounting adjustments. Availability of this GL source and implementation of the control remain unverified.
2. Use the documented **Reconciliation Summary** and `[GL_Reconciliation_Gap]` measure only if present, verified and based on that independent source. Otherwise retain an explicit comparison and escalate the missing control to the data architect. A chart-of-accounts join is not a balance reconciliation.
3. The proposed release target is a **$0.00 reconciliation gap**, evaluated using documented amount precision and rounding. Retain the comparison, source identifiers and exception resolution. Inspect unresolved records, duplicates and unmapped employee/account/department keys as well: an aggregate zero gap does not establish record accuracy, and missing GL evidence does not count as a passed reconciliation.
4. If a gap exists, examine the actuals and reference mappings, source period coverage, and monthly-versus-weekly precedence. Retain the investigation and correction record.
5. Hold release while material input, mapping, refresh, or reconciliation exceptions remain unresolved. The FP&A manager reviews exceptions and the release decision.

## 6. Exception Handling and Release Decision

~~~mermaid
flowchart TB
    A["Refresh failure or data exception"] --> B{"Path error?"}
    B -- Yes --> C["Correct FolderPath and verify source access"]
    B -- No --> D{"Schema error?"}
    D -- Yes --> E["Restore approved export schema; escalate intentional changes"]
    D -- No --> F{"Data-type mismatch?"}
    F -- Yes --> G["Request corrected source data; retain original export"]
    F -- No --> H["Escalate unclassified exception to data architect"]
    C --> I["Refresh, inspect coverage and mappings, and reconcile"]
    E --> I
    G --> I
    H --> J["Resolve and document correction or approved change"]
    J --> I
    I --> K{"Refresh and required checks pass?"}
    K -- Yes --> L["FP&A review and release; retain evidence"]
    K -- No --> M["Hold release and escalate unresolved issue"]
    M --> H
~~~

- **Path exceptions (DataSource.Error):** Repeat the path setup in §4.3 and check source access.
- **Schema exceptions (Expression.Error, missing column):** First restore the approved source export layout. If a source-system change is intentional, the data architect reviews mapping changes and validates affected outputs before use; update this SOP after approval. Operators should not edit query mappings simply to bypass an error.
- **Data-type mismatches:** Trace the error to the source field and request an authorized correction or corrected export. Preserve the raw export and document the change; do not coerce malformed values merely to obtain a successful refresh.
- **Missing keys, duplicate records, or reconciliation gaps:** Compare source coverage and mappings, investigate closed-month/weekly overlaps, and retain the resolution. Escalate unresolved issues to the FP&A manager and data architect.
- **Timing above target:** Record duration and investigate input volume, source access, or query changes. Exceeding the proposed timing target does not alone establish statistical instability.

## 7. Control Matrix

This matrix owns operational monitoring. Targets express intended behavior; this revision does not assert that each check or named measure has been deployed and validated.

| Process step | Control and target | Check and retained evidence | Frequency | Responsible role | Corrective response |
| --- | --- | --- | --- | --- | --- |
| Source access | FolderPath resolves to the maintained Variance Analysis folder | Parameter value and source-access/refresh result | Before first refresh; after path changes | FP&A analyst | Correct path and permissions; retry and verify |
| Input filing | Correct year/interval folder and expected period coverage | Source inventory, filenames, reporting cutoff, and duplicate check | Every input drop and before release | Expense admin / FP&A analyst | Restore filing convention, obtain missing inputs, investigate overlaps |
| Schema integrity | Validate the four documented fields, key meanings, identifier formats and amount precision in §4.2 | Required-column/type check, key review and exception record | Every refresh; schema review after changes | FP&A analyst / data architect | Restore approved export; route intentional schema/type changes for review and validation |
| Reference mappings | No unresolved employee, department or GL keys; historical hierarchy policy confirmed before mapping changes | Key uniqueness, unmatched-record review and applicable assignment policy | Reference changes and every reporting run | FP&A analyst | Retain identity keys; confirm historical treatment; escalate unresolved records |
| Actuals and GL reconciliation | Proposed $0.00 gap for the same closed period, currency and scope at documented precision | Independent GL export/control totals, verified `[GL_Reconciliation_Gap]` or explicit comparison, and exception resolution | Monthly close and relevant corrections | FP&A analyst; manager review | Hold unresolved releases; obtain missing GL evidence, investigate and reconcile again |
| Refresh duration | Proposed target less than 2 minutes; 0.029-hour reference pending target review | Refresh start/end, successful result, input volume, and environment | Every measured reporting refresh | FP&A analyst | Record overrun and investigate; do not substitute target for a statistical limit |
| Report release | Required checks complete; unresolved material exceptions held | Check results, exception status, reviewer, and release decision | Every reporting output | FP&A manager / analyst | Hold and escalate; release after required checks pass |
| Statistical monitoring | Method and control limits derived from verified comparable measurements | Validated measurement window, calculations, chart, and signal-response record | Frequency to be set with the validated monitoring method | Data architect / FP&A process owner | Follow [[Statistical Process Control (SPC)]] once validated; retain operational checks meanwhile |

The inherited **1.005-hour internal benchmark** comes from a mixed source range and is unvalidated. It is not a release specification or control limit. See [[Project Charter]] for CTQ targets and [[Statistical Baselining & Continual Improvement Framework]] for measurement definitions.

## 8. Records and Review

Retain source identifiers, reporting period, refresh timings, software/environment details, exceptions, reconciliation results, and release decisions with the reporting record. Preserve the original historical timing workbook; record chronology corrections as an evidence reconciliation rather than inventing replacement observations.

Review this SOP semi-annually and when an approved schema, path, model, or reporting-scope change affects the workflow. Version 1.4 clarifies input/key definitions, monetary precision, historical-mapping policy and required independent GL evidence; it does not assert owner approval or deployment of these controls.
