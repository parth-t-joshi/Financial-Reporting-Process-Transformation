# DMAIC Phase 4: Improve Phase Report & Implementation Verification

**Process:** Travel & Entertainment (T&E) reporting within SG&A / FP&A  
**Project-owner-confirmed production go-live:** July 1, 2026; deployment records not independently verified  
**Status:** Engineering changes documented; performance verification and Control-phase acceptance pending  
**Editorial revision:** October 6, 2026

## 1. Phase context and implementation scope

The documented manual workflow required file collection, cross-month split-week handling, repeated Excel lookups, manual column alignment, and report aggregation. The Improve phase addresses those activities through Power Query ingestion and transformation, with a centralized Power BI model for reporting.

The project owner confirmed production go-live as July 1, 2026; deployment records have not been independently verified. Conflicting workbook dates and measurement boundaries prevent acceptance of the previous 91-day before/after claims. This report separates implementation documentation, provisional source results, and the evidence still needed for performance verification.

## 2. Engineering changes documented

### Folder ingestion and parameterization

The project documentation describes Power Query M pipelines using a shared path parameter to discover, transform, and append transaction files from historical (`2025/`) and active (`2026/`) monthly and weekly directories. Parameterization reduces repeated path editing and supports additional reporting files within the defined folder structure. The actual PBIX queries have not been inspected; verify file filters and transformation steps before treating these descriptions as implementation evidence.

The `Folder.Files` example in [[DMAIC Report]] enumerates files recursively. It does not demonstrate the transaction-file selection, workbook transformation, enrichment, or append steps. Supply representative actual M queries showing those behaviors, including exclusion of reference workbooks and temporary files.

The implementation should preserve monthly accounting overrides when combining weekly and closed-month records, including weeks that span month-end. Validation must show that overlap handling avoids duplicate records and superseded provisional amounts.

### Schema normalization and exception handling

The transformation design replaces repeated manual column alignment with explicit column mapping and type conversion. Employee, department, GL, and other reference data support transaction classification and model relationships.

Exception handling must retain traceable outcomes for missing columns, invalid types, unmapped identifiers, and employee-status changes. Verify identifier formats, monetary precision and rounding, and the treatment of department transfers: retained employee IDs do not establish transaction-date organizational attribution. Automation alone does not demonstrate that all accounting or ingestion exceptions are eliminated.

### Power BI model and refresh workflow

The documented reporting model consolidates transformed transactions and reference data for report visuals and variance analysis. Power BI Desktop refresh is documented in [[SOP]]. Validate the actual calendar relationships, transaction and budget grains, weekly/monthly period alignment, and year-to-date definition. Supply an actual model diagram, actual DAX measures, and report screenshots with a worked monetary budget-versus-actual example before presenting these as verified portfolio implementation artifacts.

Scheduled refresh and automated notifications through Power BI Service are **proposed controls pending deployment evidence**. They require confirmation of the published semantic model, credentials, applicable gateway configuration, refresh history, and notification mechanism. “Scheduled dashboard publishing” is not used as a substitute for verified data refresh.

## 3. Evidence status and provisional results

> [!important] Source records require reconciliation
> Workbook/source summaries are pending chronology and measurement-boundary verification. A workbook “post” label does not establish that an observation belongs to the production period beginning July 1, 2026. Exact workbook references and duplicate records are documented in [[Evidence Reconciliation|Evidence Reconciliation]].

| Evidence group | Use in this report |
| --- | --- |
| Mixed 91-row legacy “pre” summary | Historical calculation requiring reconciliation; excluded from a validated baseline comparison |
| Phase-tagged pre-labelled source group: 78 observations | Provisional source group; chronology and measurement scope unresolved |
| Phase-tagged post-labelled source group: 91 observations | Descriptive source summaries only; not a verified 91-day production audit |
| Separate 13-row post-labelled segment | Contains repeated records; excluded from additional independent observation counts |

### Source statistics and measurement boundary

Source ranges in [[Six Sigma Green Belt reports/Historical Data Analysis.xlsx]] are `'91Days pre implementation data'!A2:C79` and `'91Days post implementation data'!A2:C92`. The post-labelled dates run April 2–July 1, 2026 and conflict with a production validation window beginning July 1; source dates are preserved.

[[Statistical Baselining & Continual Improvement Framework#4. Provisional source summaries|Framework source summaries]] is the authoritative location for the full descriptive statistics, units, and threshold counts. These summaries describe source-labelled groups; no percentage reduction is asserted because an eligible baseline and comparable production measurement have not been established.

## 4. Target results and interpretation

| Comparison within the 91 post-labelled source observations | Recorded result | Interpretation |
| --- | ---: | --- |
| Duration $>2\text{ min}$ | $3$ observations: two at $0.035\text{ h}$ and one at $0.034\text{ h}$ | Source exceedances of the primary proposed under-two-minute refresh target; production acceptance is unverified |
| Duration $>0.029\text{ h}$ | $8$ observations, at $0.030$–$0.035\text{ h}$ | Exceedances of the sample-derived historical threshold, not a second operating target |
| Duration $>1.005\text{ h}$ | $0$ observations | Exceedances of an unvalidated inherited internal benchmark |
| Observed maximum | $0.035\text{ h}$ ($2.10\text{ min}$) | Source maximum, not a UCL, contractual limit, or guaranteed maximum |

The $1.005\text{ h}$ value was calculated as $P_{25}$ of the mixed 91-record range; its operational validity and baseline applicability remain unverified. It is not an established customer USL or defect criterion. The $0.029\text{ h}$ historical threshold is retained for source reconciliation; its exceedance count must not be replaced with the zero count against $1.005\text{ h}$.

The primary proposed refresh-duration target is **under two minutes**, subject to approval and an agreed measurement definition. Three of the 91 source observations exceed two minutes; these records cannot establish production attainment because their chronology and measurement scope remain unresolved. A run exactly equal to two minutes would also fail the strict target; no such value is recorded in this source group.

The source summaries do not verify financial reporting accuracy, a population failure rate of zero, a sigma level, or statistical stability. Attributing longer observations to normal network/gateway variation requires supporting logs and remains unverified. Defect metrics and capability interpretations are addressed in [[Statistical Baselining & Continual Improvement Framework]].

## 5. Verification requirements and Control handoff

The project requires documented acceptance evidence before declaring Improve targets verified or Control-phase monitoring implemented. The October 6 editorial revision records corrections to the notes; it is not process-owner approval.

| Verification or handoff item | Required evidence / next action |
| --- | --- |
| Source chronology | Resolve phase-label/date conflicts against original records; preserve source dates without shifting or synthesizing observations |
| Measurement boundary | Define manual effort, refresh duration, reporting lead time, and labor effort separately |
| Comparable audit windows | Establish eligible baseline and production records, excluding duplicate observations |
| Folder and schema behavior | Provide actual M queries and input/output evidence for recursive file filters, monthly/weekly overlap handling, identifier preservation, amount precision, and traceable exceptions |
| Model and reporting evidence | Provide the actual model diagram, relationship settings, calendar and actual/budget grains, actual DAX measures, report screenshots, and a worked monetary variance analysis |
| Historical employee attribution | Confirm transaction-date versus current-hierarchy department attribution and demonstrate transfer/status-change behavior |
| Financial reconciliation | Identify an independent closed-GL actuals export or Accounting control-total source and provide a worked reconciliation for the same period, currency, and scope; account reference data alone is insufficient |
| Operating targets | Record approval and measurement rules for the proposed under-two-minute refresh target; retain $0.029\text{ h}$ as a historical source threshold |
| SPC monitoring | Implement and review the proposed I–MR method in [[Statistical Process Control (SPC)]]; the current figure is a provisional run chart |
| Service refresh and notifications | Verify configuration and execution evidence before marking these controls implemented |
| Ownership and acceptance | Record process-owner review, unresolved exceptions, monitoring responsibilities, and handoff decision |

The SOP, proposed monitoring plan, and engineering documentation support the handoff. They do not replace production verification records.

## Appendix A. Source-summary reconciliation

The duplicate segment is `'91Days pre implementation data'!A80:C92`, repeating `'91Days post implementation data'!A2:C14`; it is excluded from additional independent observation counts.

The earlier mixed “pre” calculation blocks are retained in [[Evidence Reconciliation|Evidence Reconciliation]] as legacy calculations requiring reconciliation, not accepted baseline performance.

The formerly stated pre range of $0.890$–$1.420\text{ h}$ is incompatible with that standard deviation and with other documented timing values. Before/after reductions derived from those summaries are withheld rather than recalculated against an unverified baseline.

The full descriptive source statistics are retained in [[Statistical Baselining & Continual Improvement Framework]]. Source references, duplicate-record handling, chronology discrepancies, and calculation lineage are in [[Evidence Reconciliation|Evidence Reconciliation]].

## Appendix B. Proposed monitoring artifact

![[Images/Statistical Process Control (SPC) Chart.png]]

This observation-index run chart separates source-labelled groups. Calendar go-live placement, numeric control limits, and production capability claims require the verification work described in [[Statistical Process Control (SPC)]].
