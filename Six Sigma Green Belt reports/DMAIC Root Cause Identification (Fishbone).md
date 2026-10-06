# DMAIC Root Cause Identification: Fishbone Diagram Summary

**Process:** SG&A (T&E) variance reporting.  
**Documentation revision:** October 6, 2026.

The source documentation reports legacy weekly and monthly reporting timings of 48 and 36 hours respectively. These are reported estimates with an unverified measurement basis: elapsed lead time and summed analyst effort have not been separated. The fishbone identifies cause hypotheses for investigation; it does not prove causal effects or quantified savings.

## 1. Cause Hypotheses and Process Risks

| Category    | Documented cause hypotheses                                                                                                                     | Relevant Lean waste or risk                                                    | Verification needed                                                                                                                                                                                                   |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Process     | Fragmented file collection; manual transformation; split-week and month-end overlaps; manually maintained Excel lookups and pivots.             | Searching, overprocessing, waiting and potential duplicate or missing records. | Map each task, inspect transaction coverage, and verify month/week precedence and duplicate handling.                                                                                                                 |
| Data        | Inconsistent source schemas; employee-status changes; GL and department reference changes.                                                      | Rework and potential mapping errors.                                           | Check approved schemas, unmatched keys, and employee retention. Verify transaction-date versus current-hierarchy department attribution. Distinguish Excel lookup errors from Power Query errors and unmatched joins. |
| Technology  | Disconnected reference spreadsheets; manual joins; source paths not parameterized in the legacy workflow.                                       | Repeated preparation and portability risk.                                     | Inspect documented Power Query transformations and path parameters in the actual model.                                                                                                                               |
| People      | Manual preparation workload; inconsistent file naming; key-person dependency.                                                                   | Underused analyst capacity and handover risk.                                  | Record task-level analyst effort and verify operating instructions. An analyst-effort percentage has not been substantiated.                                                                                          |
| Measurement | Incomplete timing definitions; effort and elapsed time combined; data accuracy checked after report preparation; source freshness not measured. | Weak evidence for performance and timeliness claims.                           | Define start/stop events, units, sample windows and reconciliation checks before estimating benefits.                                                                                                                 |
| Environment | Distributed ownership across Accounting, HR and FP&A; data silos; month-end and quarter-end pressure.                                           | Waiting, coordination delays and rework.                                       | Check export availability, ownership, handoffs and close-period exceptions.                                                                                                                                           |

The 42 task-hours in [[Process Optimization Bottlenecks (Pareto Chart)]] support prioritization within that recorded breakdown. They do not establish a monthly labor baseline, elapsed reporting lead time, or financial ROI.

## 2. Fishbone Diagram: Potential Causes of Weekly and Monthly Reporting Delays

![[Images/Fishbone Diagram.png]]

The diagram uses the same six categories and labels the legacy timings as reported estimates. Its causes remain hypotheses until verified against process records and reconciled financial outputs.

## 3. Link to DMAIC and Control

Use [[DMAIC Report]] for the Define–Measure–Analyze–Improve–Control narrative and [[SOP]] for source-schema checks, reconciliation and escalation. The project owner confirmed production go-live as July 1, 2026; deployment records have not been independently verified. The workbook's conflicting chronology is documented in [[Evidence Reconciliation|Evidence Reconciliation]]. No statistical stability, data-error elimination, or ROI conclusion is inferred from this fishbone.
