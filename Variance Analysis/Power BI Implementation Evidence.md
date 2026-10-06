# Power BI Implementation Evidence

**Project:** T&E expense variance reporting  
**Documentation revision:** October 6, 2026  
**Status:** Implementation-evidence register; PBIX, M/DAX and service deployment not inspected

## 1. Documented Design and Available Evidence

| Capability described | Available evidence | Artifact needed to substantiate implementation |
| --- | --- | --- |
| Folder ingestion and shared `FolderPath` | Workflow description and an illustrative enumeration expression in [[copilot/projects/FP&A Green Belt/outputs/github/Six Sigma Green Belt reports/DMAIC Report]] | Actual M query with folder, extension, temporary-file and reference-file filters; representative source-to-output trace |
| Schema normalization and enrichment | Documented fields and mapping requirements | Actual mapping/type-conversion steps; unmatched-key and invalid-value handling |
| Weekly/monthly precedence | Accounting-overlap requirement | Implemented source-selection or transaction precedence logic; duplicate and split-week examples |
| Actual/budget model | Conceptual shared-dimension diagram | PBIX model screenshot; keys, grains, cardinality, filter direction and reporting-calendar relationships |
| Variance and YTD reporting | Intended outputs in the charter | Actual DAX definitions, financial sign/zero-budget policy and report screenshots for matching periods |
| Reconciliation and release controls | Proposed controls in [[copilot/projects/FP&A Green Belt/outputs/github/Six Sigma Green Belt reports/SOP]] | Independent closed-GL source, verified calculation and retained reconciliation/release record |
| Scheduled refresh and notifications | Proposed service controls | Published semantic model, credentials/applicable gateway, refresh history and notification evidence |

## 2. File Selection and Transformation

`Folder.Files(FolderPath)` returns file metadata for the folder and its subfolders. It does not itself combine workbook contents or normalize transaction schemas. The documented root also contains reference and model files, so implementation review must verify which files are selected before parsing. [Microsoft Folder.Files documentation](https://learn.microsoft.com/en-us/powerquery-m/folder-files).

Retain actual M excerpts for transaction-path and file-type selection, temporary-file exclusion, content extraction, column mapping, types and joins. Identify transform errors and unmatched keys rather than silently dropping them. Excerpts should be labelled implemented only when obtained from the model.

## 3. Model Grain and Calendar

Document what one row represents in each actual and budget fact table. Verify the date/calendar implementation supporting reporting weeks, months and YTD, plus the applicable shared employee/account/department dimensions. The source notes' diagram is conceptual; its omissions do not prove that a table is absent from the PBIX.

Confirm relationship keys, cardinalities and filter direction. Explain treatment of missing keys, department transfers and historical organizational attribution. Keep a budget comparison at a supported grain or disclose an approved allocation policy. [Microsoft star-schema guidance](https://learn.microsoft.com/en-us/power-bi/guidance/star-schema).

## 4. Field Semantics and Financial Precision

| Documented raw field | Meaning or rule to verify |
| --- | --- |
| `Unique Id` | Identify whether this is a transaction, employee or another identifier; define uniqueness and any composite transaction key |
| `Amount spent` | Currency, source precision, stored numeric type, rounding and treatment of refunds/reversals |
| `Spend date` | Transaction/spend date versus posting date; mapping to the reporting calendar |
| `GL Numbers` | Account identifier format, leading zeros/alphanumeric values and consistency with the account dimension |

Raw headers and the documented schema are retained; this revision does not change the PBIX. Formatting monetary values to two decimals does not establish stored precision. Define arithmetic and reconciliation rounding independently of display formatting. [Microsoft Power Query data types](https://learn.microsoft.com/en-us/power-query/data-types).

## 5. Reproduction and Reporting Evidence

Use [[copilot/projects/FP&A Green Belt/outputs/github/Six Sigma Green Belt reports/SOP]] for the documented Desktop workflow. Record the PBIX/version, source paths, source inventory, input coverage and environment for a reproducible run. The documentation export contains diagrams and timing evidence; the actual finance/model inputs are still needed to refresh and validate the reporting solution.

Use **report** or **report page** for PBIX/Power BI Desktop outputs. Describe a service dashboard only when its deployment is demonstrated. [Microsoft dashboards and reports](https://learn.microsoft.com/en-us/power-bi/create-reports/service-dashboards).

A useful implementation review should cover normal refresh, an empty input folder, unexpected/reference files, a changed header, invalid amounts, missing keys, duplicate transactions, a cross-month week, a closed-month override, a department transfer and zero/missing budget. Retain outcomes as evidence only after running the applicable checks in the actual implementation.
