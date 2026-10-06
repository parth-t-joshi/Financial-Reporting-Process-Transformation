# Pareto Chart: Recorded Reporting Task Effort

This Pareto breakdown identifies the largest recorded effort categories in the source documentation for SG&A (T&E) reporting. It supports improvement prioritization, rather than proving root causes or realized savings.

**Documentation revision:** October 6, 2026.

## 1. Recorded Task Breakdown

The five source values total 42 hours. The underlying time-study log, number of reporting cycles, staff coverage and treatment of parallel work are not supplied. These are recorded task-hours with an unverified measurement basis; do not present the total as verified monthly labor-hours or elapsed cycle time.

| Rank | Reporting task | Recorded hours | Share of total | Cumulative share | Documented improvement approach |
| --- | --- | ---: | ---: | ---: | --- |
| 1 | Manual VLOOKUP and data alignment across reference datasets | 20 | 47.6% | 47.6% | Power Query enrichment and dimension relationships. |
| 2 | Handling split-week and calendar-month overlaps | 11 | 26.2% | 73.8% | Explicit overlap, accounting-precedence and duplicate-handling logic. |
| 3 | Error correction and employee-status exceptions | 6 | 14.3% | 88.1% | Retain employee keys, check unmatched joins, and verify historical department attribution. |
| 4 | Manual pivot aggregation and formatting | 3 | 7.1% | 95.2% | Reusable Power BI reporting views. |
| 5 | File collection across folders | 2 | 4.8% | 100.0% | Parameterized folder ingestion. |
| **Total** | **Recorded task breakdown** | **42** | **100.0%** | **100.0%** | **Verify post-change effort separately.** |

Each share is task hours divided by 42; cumulative shares use unrounded values and are displayed to one decimal place. Missing citation placeholders in the original table have been removed. The figures are transcribed from supplied project documentation, not an independently verified time-study dataset.

## 2. Pareto Chart

![[Images/Process Pareto Chart.png]]

The bars show recorded task-hours and the line shows cumulative share. The 80% reference line is a prioritization aid, not a specification or control limit. The first three categories cross that reference line.

## 3. Interpretation and Verification

The top two categories account for 31 of the 42 recorded hours (73.8%). The top three account for 37 hours (88.1%). These proportions do not demonstrate that automation eliminated the same share of elapsed reporting delays.

Verify realized savings with comparable task-level observations before and after implementation. Define reporting frequency, analyst coverage and start/stop events, and measure financial accuracy separately through reconciliation. A reduction in preparation effort does not itself establish fewer transaction errors or a financial ROI.

See [[DMAIC Root Cause Identification (Fishbone)]] for cause hypotheses, [[DMAIC Report]] for the project narrative, and [[SOP]] for operating controls. The project owner confirmed production go-live as July 1, 2026; deployment records have not been independently verified. Workbook chronology and statistical evidence limitations are recorded in [[Evidence Reconciliation|Evidence Reconciliation]].
