# Evidence Reconciliation

Production go-live is recorded as **July 1, 2026**, based on project-owner confirmation retained in the October 6 documentation. Deployment records were not independently inspected. That recorded event is distinct from the workbook's stored April 2 phase-transition label. The workbook dates have not been reconciled to valid production observation dates.

> [!warning] Scope of the available evidence
> The calculations below describe records grouped by their workbook phase labels. They do not establish a valid production before/after comparison. The workbook chronology and measurement start/end boundaries remain unresolved. Consequently, headline improvement percentages, demonstrated stability, sigma levels and process-capability claims are withheld.

## 1. Source and verification method

- Source: [[Six Sigma Green Belt reports/Historical Data Analysis.xlsx]].
- Verification: read the original XLSX worksheet XML without changing or recalculating the workbook; inspect its saved formulas and cached values; independently calculate descriptive statistics from the numeric latency values.
- Statistical convention: arithmetic mean, inclusive interpolated percentiles and **sample standard deviation** $s$ with denominator $n-1$. Latency values are in hours.
- Source columns: A = stored date; B = Daily_Reporting_Latency_Hours; C = Operational_Phase; D = the workbook's existing classification. Column D is retained as source evidence, not used as a comparable classification across cohorts.
- Source file last modified: **2026-07-27 14:31:47 UTC**. This file timestamp does not establish the observation dates.
- SHA-256: eaf660989e35f117fa122ce430bee6a4a562b6d2f25710036ab7ba499ec68322. The source workbook is preserved unchanged.

## 2. Production event and stored chronology

| Evidence | Source reference | Finding |
| --- | --- | --- |
| Recorded production go-live | Project-owner confirmation retained in the October 6 documentation; deployment records not inspected | **2026-07-01** |
| First post-labelled source record | `91Days post implementation data!A2:C2` | Stored date **2026-04-02**, latency 0.035 h, label “Post-Implementation Control (Go-Live)” |
| Same phase-transition record in the pre tab | `91Days pre implementation data!A80:C80` | Stored date **2026-04-02**, latency 0.035 h, same post go-live label |
| Post tab's full stored date window | `91Days post implementation data!A2:A92` | **2026-04-02–2026-07-01**, 91 records |
| Last post-labelled source record | `91Days post implementation data!A92:C92` | Stored date **2026-07-01**, label “Post-Implementation Control (Current)” |

The post-labelled window mostly predates the confirmed production deployment. Keep the original dates intact until dated run logs or another authoritative record establishes the intended chronology. Do not shift the dates or substitute April 2 as the production go-live date.

## 3. Provisional cohorts and duplicate exclusion

| Source-labelled cohort | Source range | Count | Stored date window |
| --- | --- | ---: | --- |
| Historical Baseline Run-Rate | `91Days pre implementation data!A2:C69` | 68 | 2026-01-14–2026-03-22 |
| Pre-Implementation Crisis Spike | `91Days pre implementation data!A70:C79` | 10 | 2026-03-23–2026-04-01 |
| Combined pre-labelled subset | `91Days pre implementation data!A2:C79` | **78** | 2026-01-14–2026-04-01 |
| Post-labelled observations | `91Days post implementation data!A2:C92` | **91** | 2026-04-02–2026-07-01 |
| Duplicated post records in the pre tab | `91Days pre implementation data!A80:C92` | **13** | 2026-04-02–2026-04-14 |

The 13 duplicated records match `91Days post implementation data!A2:C14` in stored date, latency and phase label. Exclude them from the derived pre cohort, retain them in the original workbook and use the post tab once for the 91 post-labelled records. The derived chart therefore contains **169 source observations: 78 pre-labelled + 91 post-labelled**.

The resulting stored windows do not overlap, but their relationship to the confirmed production event remains unverified.

## 4. Provisional descriptive statistics

These independently calculated source summaries describe the workbook labels only. They are not validated production baselines or verified implementation outcomes.

| Source range for latency values | $n$ | Mean (h) | Median (h) | $P_{25}$ (h) | Sample SD $s$ (h) | Min–max (h) |
| --- | ---: | ---: | ---: | ---: | ---: | --- |
| Pre-labelled subset, `pre!B2:B79` | 78 | 1.309615385 | 1.185 | 1.0925 | 0.422006470 | 0.890–2.700 |
| Post-labelled subset, `post!B2:B92` | 91 | 0.029180220 | 0.029 | 0.029 | 0.001376487 | 0.023–0.035 |
| Original mixed “pre” range, `pre!B2:B92` | 91 | 1.126890110 | 1.140 | 1.005 | 0.595755029 | 0.023–2.700 |

Here, `pre` means **91Days pre implementation data** and `post` means **91Days post implementation data**.

The original 91-record “pre” summary combines 68 historical records, 10 crisis records and 13 post-labelled records. Its mean, median, percentile and spread cannot serve as a purely pre-implementation baseline. Source summary `pre!G2` uses `PERCENTILE(B2:B92,0.5)`; `pre!G3` uses `PERCENTILE(B2:B92,0.25)`. Their cached values match the independent calculations for that **mixed** range.

## 5. Threshold definitions and measurement boundaries

| Threshold | Origin and status | Provisional count |
| --- | --- | --- |
| **1.005 h inherited benchmark** | Cached `pre!G3`; derived from the mixed 91-record range. **Unvalidated** as a production requirement or approved specification. | 68 of the 78 pre-labelled values exceed it; 0 of the 91 post-labelled values exceed it. |
| **0.029 h historical threshold** | Cached `post!G3`; the post-labelled sample's $P_{25}$, equivalent to 1.74 minutes. It is not an approved operating specification. | **8 of 91** post-labelled values exceed it, spanning **0.030–0.035 h**. |
| **Under two minutes proposed refresh goal** | $2/60$ hours; separate from the sample-derived 1.74-minute threshold. Production attainment remains unverified. | **3 of 91** post-labelled values exceed two minutes: `post!B2=0.035`, `B11=0.035`, `B13=0.034` hours. |

The eight historical-threshold exceedances are `post!B2, B5, B6, B9, B10, B11, B13, B14`. The last value is 0.030 h; describing all eight as 0.031–0.035 h omits that record. These are strict exceedance counts. The proposed goal is **less than** two minutes; the source group contains no observation exactly equal to two minutes, so its exceedance and goal-nonattainment counts coincide.

Post `D2:D92` applies `IF(B2>$G$3,"NC","C")` down the column. Its saved classification therefore uses **0.029 h**. Existing `post!G7=8` reflects that threshold; claims of zero against **1.005 h** answer a different question. Label these counts **threshold exceedances** and name the threshold. Neither threshold's statistical origin alone establishes a customer defect specification.

The `50-50 Pre Post Data` tab contains **90 records, split 45 pre-labelled + 45 post-labelled** (`A2:E91`). Its classification column links to source-tab statuses that use different thresholds, so `H7:H11` cannot be treated as a single comparable defect or capability result. Saved yield-to-Z formulas do not demonstrate a validated capability level.

Before a production comparison, document one consistent start event, end event, unit, run population and treatment of waiting time. Existing material refers to manual active analyst time, automated refresh duration, 36/48-hour elapsed reporting windows and 42 recorded task hours. These measures have different boundaries. The column name “Daily_Reporting_Latency_Hours” does not reconcile them.

## 6. Chart interpretation

### Provisional observation-index run chart

![[Images/Statistical Process Control (SPC) Chart.png]]

The chart preserves source order within the two source-labelled cohorts and uses an **observation index**, not a calendar axis. The boundary identifies **workbook phase labels**, not the production deployment event. The lower panel expands the 91 post-labelled latency values. The dashed reference is the **inherited 1.005 h benchmark (unvalidated)**. This is a **run chart**; it contains no calculated control limits and does not establish statistical control or capability.

### Recorded task-hour Pareto

![[Images/Process Pareto Chart.png]]

The Pareto input is the recorded breakdown in [[copilot/projects/FP&A Green Belt/outputs/github/Six Sigma Green Belt reports/Process Optimization Bottlenecks (Pareto Chart)]]: **20, 11, 6, 3 and 2 hours**, totaling **42 recorded task hours (basis unverified)**. Independently calculated cumulative shares are **47.6%, 73.8%, 88.1%, 95.2% and 100.0%**. These are shares of recorded task hours, not measured percentages of elapsed reporting delay or realized savings.

## 7. Reconciliation needed before headline results

1. Reconcile stored observation dates to authoritative production run records without altering the original workbook.
2. Confirm a consistent measurement start/end definition and distinguish analyst effort, refresh duration and elapsed reporting lead time.
3. Confirm the intended population, production observation windows and duplicate treatment.
4. Establish the approved operational target or specification and record its owner, rationale and effective date.
5. Recalculate any production comparison and, if required, choose and document an appropriate control-chart method after the measurement basis is confirmed.

Support files in this project's `outputs/` retain source sheet/row references, original stored dates, source values and the independently calculated summaries.

## 8. Corrected Analysis Companion and Superseded Workbook Claims

[[Historical Timing Analysis - Source Summary.xlsx]] is the primary portfolio timing-analysis view. It preserves all 169 selected source records and their original dates, values, phase/classification labels and worksheet/row lineage. It provides descriptive calculations and applies the same thresholds to both source-labelled groups. It does not inherit the original workbook's sigma/capability or industry-benchmark conclusions.

The original workbook remains unchanged. Its saved narratives include “raise process capability from 1.3537 sigma” in `post!F15`, a “demonstrated performance threshold” in `post!F23`, and “≥6.00σ capability” in `'50-50 Pre Post Data'!G15`. The sigma and DPMO summaries and industry/world-class benchmark blocks are superseded analysis, not current project findings. A yield-equivalent inverse-normal calculation alone does not demonstrate process capability.

Use [[ARCHIVE NOTICE]] for the status of original notes and diagrams. A corrected analysis companion improves source interpretation; it does not resolve chronology, supply missing production logs, or verify the Power BI implementation.
