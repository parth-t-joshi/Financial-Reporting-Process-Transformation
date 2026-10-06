# Run Chart and SPC Monitoring Plan

**Process:** Travel & Entertainment (T&E) reporting within SG&A / FP&A  
**Project-owner-confirmed production go-live:** July 1, 2026; deployment records not independently verified  
**Editorial revision:** October 6, 2026  
**Status:** Provisional source visualization; formal SPC implementation and performance acceptance pending verification

## 1. Source scope and chronology

The project owner confirmed production go-live as July 1, 2026; deployment records have not been independently verified. Workbook phase labels and calendar dates conflict with that date. The source-labelled groups therefore cannot yet be presented as a chronological production before/after comparison.

The provisional run chart uses **observation index**, with **78 pre-labelled source observations** followed by **91 post-labelled source observations**. The grouping boundary indicates workbook labels, not an inferred calendar go-live date. Sources in [[Six Sigma Green Belt reports/Historical Data Analysis.xlsx]] are `'91Days pre implementation data'!A2:C79` and `'91Days post implementation data'!A2:C92`. The pre sheet's post-labelled `A80:C92` segment repeats the post sheet's `A2:C14` and is excluded from this sequence.

The post-labelled source dates span April 2–July 1, 2026, conflicting with a production validation window beginning July 1. No dates are shifted.

![[Images/Statistical Process Control (SPC) Chart.png]]

> [!note] How to read this chart
> This is a provisional run chart, not an implemented I–MR control chart. It has no validated calendar timeline, UCL, or LCL. Source groups show different reported durations, but statistical stability, causal attribution, and production improvement remain unverified. Exact references and discrepancies are in [[Evidence Reconciliation|Evidence Reconciliation]].

## 2. Source-labelled observations

The earlier mixed 91-row “pre-implementation” summary must not be used as a baseline. Its inclusion of post-labelled records changes the comparison. The workbook's phase-tagged pre group and post group are retained separately, pending chronology and measurement-boundary verification.

The full descriptive statistics are maintained in [[Statistical Baselining & Continual Improvement Framework#4. Provisional source summaries|Framework source summaries]]. They are workbook/source summaries, not a validated 91-day production audit. Before/after reduction percentages are withheld. The source-labelled sequence is useful for inspecting recorded durations; it does not establish a production timeline or statistical stability.

The earlier ledger’s late-June/early-July calendar assignments remain unreconciled. The reported ledger below retains the supplied chronology alongside stored workbook dates for traceability; it does not reinstate those assignments as verified production observations.

## 📅 Chronological Data Verification Ledger

The lists below preserve the dates, durations and phase descriptions in the supplied ledger. Each entry also identifies the matching workbook date and source row so the reported chronology can be checked.

> [!warning] Reported chronology and legacy labels remain unverified
> Every supplied ledger date is **90 days later** than its matching stored workbook date. The reported June/July dates are retained as claims for reconciliation, not verified production run dates. Cross/check icons and quoted labels reproduce the legacy presentation; they do not establish statistical control, stability, causal effects or target compliance. No workbook dates have been shifted. See [[Evidence Reconciliation|Evidence Reconciliation]].

**Source key:** `pre` = `91Days pre implementation data`; `post` = `91Days post implementation data` in [[Six Sigma Green Belt reports/Historical Data Analysis.xlsx]]. Row references identify the stored date in column A and duration in column B.

### ⚠️ Pre-Implementation Crisis Spike (Late June — reported chronology)

- **2026-06-24:** $2.46\text{ h}$ ❌ _Legacy label: “Out of Control”_. Stored date: **2026-03-26**; source: `pre!A73:B73`.
- **2026-06-25:** $2.21\text{ h}$ ❌ _Legacy label: “Out of Control”_. Stored date: **2026-03-27**; source: `pre!A74:B74`.
- **2026-06-26:** $2.47\text{ h}$ ❌ _Legacy label: “Critical Bottleneck Peak”_. Stored date: **2026-03-28**; source: `pre!A75:B75`.
- **2026-06-27:** $2.70\text{ h}$ ❌ _Legacy label: “Critical Bottleneck Peak”_. Stored date: **2026-03-29**; source: `pre!A76:B76`.
- **2026-06-28:** $2.37\text{ h}$ ❌ _Legacy label: “Out of Control”_. Stored date: **2026-03-30**; source: `pre!A77:B77`.
- **2026-06-29:** $1.72\text{ h}$ ❌ _Legacy label: “Out of Control”_. Stored date: **2026-03-31**; source: `pre!A78:B78`.
- **2026-06-30:** $2.30\text{ h}$ ❌ _Legacy label: “Critical Bottleneck Peak (Eve of Go-Live)”_. Stored date: **2026-04-01**; source: `pre!A79:B79`.

### ✨ Post-Implementation Control Phase (July 1–13 — reported chronology)

The heading is the supplied phase description. Its production-phase membership and control status are unresolved. Minute values are calculated from the matched durations using $\text{minutes}=60\times\text{hours}$.

- **2026-07-01:** **$0.035\text{ h}$ ($2.10\text{ min}$)** ✅ _Legacy label: “Go-Live: Automated Run Rate”_. Stored date: **2026-04-02**; source: `post!A2:B2`.
- **2026-07-02:** **$0.023\text{ h}$ ($1.38\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-03**; source: `post!A3:B3`.
- **2026-07-03:** **$0.029\text{ h}$ ($1.74\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-04**; source: `post!A4:B4`.
- **2026-07-04:** **$0.031\text{ h}$ ($1.86\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-05**; source: `post!A5:B5`.
- **2026-07-05:** **$0.033\text{ h}$ ($1.98\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-06**; source: `post!A6:B6`.
- **2026-07-06:** **$0.027\text{ h}$ ($1.62\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-07**; source: `post!A7:B7`.
- **2026-07-07:** **$0.028\text{ h}$ ($1.68\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-08**; source: `post!A8:B8`.
- **2026-07-08:** **$0.032\text{ h}$ ($1.92\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-09**; source: `post!A9:B9`.
- **2026-07-09:** **$0.031\text{ h}$ ($1.86\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-10**; source: `post!A10:B10`.
- **2026-07-10:** **$0.035\text{ h}$ ($2.10\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-11**; source: `post!A11:B11`.
- **2026-07-11:** **$0.029\text{ h}$ ($1.74\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-12**; source: `post!A12:B12`.
- **2026-07-12:** **$0.034\text{ h}$ ($2.04\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-13**; source: `post!A13:B13`.
- **2026-07-13:** **$0.030\text{ h}$ ($1.80\text{ min}$)** ✅ _Legacy label: “Stable Automated State”_. Stored date: **2026-04-14**; source: `post!A14:B14`.

**Timing interpretation:** The reported July 1 and July 10 entries are **2.10 minutes**, and the reported July 12 entry is **2.04 minutes**. These durations exceed the proposed under-two-minute goal even though their legacy presentation uses a check mark. This ledger is a 20-entry excerpt; the 13 post entries also occur in the pre sheet and are counted once in the derived analysis. Validate original run/deployment records before accepting the reported chronology or phase labels.

## 3. Targets, observed maximum, and control limits

| Threshold or statistic               | Interpretation                                                                                                                                                |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Under $2\text{ min}$                 | Primary proposed refresh-duration target; three of 91 post-labelled source observations exceed two minutes; approval and production validation remain pending |
| $1.005\text{ h}$                     | Calculated $P_{25}$ of the mixed 91-record range; operational validity and baseline applicability remain unverified; not an established USL                   |
| $0.029\text{ h}$                     | Sample-derived historical threshold; eight post-labelled observations exceed it, at $0.030$–$0.035\text{ h}$; not a second proposed operating target          |
| $0.035\text{ h}$ ($2.10\text{ min}$) | Maximum in the post-labelled source group; not a UCL                                                                                                          |

The source group has zero observations exceeding $1.005\text{ h}$, but that does not establish customer compliance or a population defect rate of zero. Three recorded durations exceed two minutes (two at $0.035\text{ h}$ and one at $0.034\text{ h}$). These source-only counts do not establish production acceptance. A run exactly equal to two minutes would also fail the proposed strict target; the source group has no such observations.

A control limit measures statistically estimated process behavior; a specification or operating target states a requirement. Neither should be assigned by copying an observed maximum. Claims that the longer source runs are normal gateway/network variation require supporting logs and remain unverified.

## 4. Proposed SPC monitoring method

A formal **Individuals and Moving Range (I–MR)** chart is proposed for comparable individual refresh-duration observations after the measurement system and chronology are reconciled. It has not been established by the present run chart.

1. Define the monitored duration, start and completion events, time precision, and treatment of failures, retries, and missing runs.
2. Preserve original timestamps and deployment records, and select a justified production study window.
3. Review observations in chronological order; investigate changes in operating conditions before combining periods.
4. Calculate and document the individuals center line and moving ranges, then review both charts for agreed statistical signals.
5. Approve a response procedure, monitoring owner, and review frequency before operational use.

For adjacent observations:

$$
MR_i=|x_i-x_{i-1}|
$$

The standard moving-range approach gives:

$$
CL_I=\bar{x}, \qquad
UCL_I=\bar{x}+3\frac{\overline{MR}}{1.128}, \qquad
LCL_I=\bar{x}-3\frac{\overline{MR}}{1.128}
$$

These formulas describe the proposed method; no numeric control limits are asserted here. Document the moving-range chart alongside the individuals chart. [NIST: Individuals Control Charts](https://www.itl.nist.gov/div898/handbook/pmc/section3/pmc322.htm).

## 5. Monitoring and response responsibilities

| Monitoring item                        | Evidence and response needed                                                                          |
| -------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Refresh failure or timeout             | Record error details, credentials/gateway status where applicable, and resolution; use [[SOP]]        |
| Performance target exceedance          | Record the agreed target, duration, and operational impact; investigate separately from an SPC signal |
| Statistical signal                     | Apply the approved I–MR rules once implemented and document the investigation                         |
| Financial data discrepancy             | Reconcile model and transaction totals with an independent closed-GL actuals source for the same period, currency, and scope; this control remains proposed until source and worked reconciliation evidence are supplied |
| Power BI Service scheduling and alerts | Proposed control; verify service deployment, settings, alert mechanism, and notification evidence     |

Scheduling, automated notifications, and gateway-related explanations require implementation evidence. Their inclusion in a plan does not show that they are configured.

## 6. Relationship to business reporting measures

The reported **48-hour weekly** and **36-hour monthly** figures must be reconciled as elapsed lead time or labor effort. Daily manual work and automated refresh duration cannot be assumed to share that boundary or to sum directly to those reporting-cycle figures.

[[Statistical Baselining & Continual Improvement Framework]] defines the measurement distinctions. [[DMAIC Phase 4 - Improve Phase Report & Implementation Verification]] records the engineering changes and outstanding acceptance evidence.
