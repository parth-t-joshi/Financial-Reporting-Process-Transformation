# Statistical Baselining & Continual Improvement Framework

**Process:** Travel & Entertainment (T&E) reporting within SG&A / FP&A  
**Working metric:** Daily Reporting Latency (DRL); measurement boundaries require reconciliation  
**Project-owner-confirmed production go-live:** July 1, 2026; deployment records not independently verified  
**Editorial revision:** October 6, 2026  
**Evidence status:** Workbook/source summaries pending chronology and measurement-boundary verification

> [!important] Evidence boundary
> The project owner confirmed production go-live as July 1, 2026; deployment records have not been independently verified. Workbook dates and phase labels conflict with that date. Source-labelled groups are retained for reconciliation; they are not validated pre- and post-go-live audit windows. See [[Evidence Reconciliation|Evidence Reconciliation]] for workbook references, duplicate records, and unresolved discrepancies.

## 1. Improvement principles and statistical terminology

### Continuous and continual improvement

Continuous improvement is ongoing improvement through incremental changes and breakthrough changes. “Continual” is often used interchangeably; some practitioners use it as a broader term encompassing discontinuous changes. Neither term guarantees a linear or exponential path to perfection. This project combines automation changes with repeated measurement and review. [ASQ: Continuous Improvement](https://asq.org/quality-resources/continuous-improvement).

### Process consistency and target attainment

**Process consistency** concerns variation between comparable reporting runs. **Target attainment** concerns whether runs meet an agreed performance requirement. These concepts should be evaluated separately from resource efficiency and from the accuracy of reported financial amounts.

Statistical stability requires evidence from an appropriate chronological control chart. A smaller standard deviation or an absence of target exceedances alone does not establish stability. Verify stability and distribution assumptions before interpreting a formal capability index. [NIST: Process Capability](https://www.itl.nist.gov/div898/handbook/pmc/section1/pmc16.htm).

### Median, mean, standard deviation, and variance

- **Median ($P_{50}$):** A robust measure of central tendency, particularly useful when durations are skewed. With repeated values, it does not imply exactly half the observations are strictly above and half strictly below.
- **Sample mean ($\bar{x}$):** The arithmetic average of the observed durations; retain it alongside the median to show the effect of longer runs.
- **Sample standard deviation ($s$):** Dispersion expressed in the same units as the observations, here hours or seconds.
- **Sample variance ($s^2$):** Dispersion expressed in squared units, here hours². A reduction in standard deviation must not be labelled “variance elimination.”

## 2. Measurement definitions to reconcile

Manual analyst effort, automated refresh duration, elapsed reporting lead time, and cumulative labor effort describe different aspects of performance.

| Measure | Required definition before comparison |
| --- | --- |
| Daily manual processing effort | Start/stop events, analyst scope, troubleshooting included, and whether time is elapsed or hands-on |
| Automated refresh duration | Refresh start to successful completion, including the specified query/model steps |
| Weekly or monthly reporting lead time | Data-ready start event to approved report availability, including any waiting and review |
| Labor effort | Summed person-hours, with the reporting cycle and contributors identified |

The reported 48-hour weekly and 36-hour monthly figures must retain their original scope until supporting records establish whether they represent lead time or labor effort. They cannot be directly divided by a refresh duration to calculate a validated project improvement.

## 3. Targets and benchmark interpretation

### Historical percentile as a candidate benchmark

Using an earlier $P_{25}$ as a candidate future median can help set an improvement hypothesis for a duration metric. It is a planning heuristic, not a statistical guarantee that the faster quarter of runs can become the new average.

The inherited $1.005\text{ h}$ benchmark was calculated as $P_{25}$ of the mixed 91-row legacy range. Its calculation origin is established; operational validity and baseline applicability remain unverified. That group is not a valid pre-go-live baseline. Retain the value as an **unvalidated internal benchmark**, not a customer specification, USL, or approved defect criterion.

### Proposed operating target and historical source thresholds

| Value | Meaning | Current interpretation |
| --- | --- | --- |
| Under $2\text{ min}$ | Primary proposed refresh-duration target | Approval, measurement definition, and production acceptance remain pending; three of 91 post-labelled source observations exceed two minutes |
| $1.005\text{ h}$ ($60.30\text{ min}$) | Inherited internal benchmark | Calculated from the mixed 91-record range; operational validity and baseline applicability remain unverified |
| $0.029\text{ h}$ ($1.74\text{ min}$) | Sample-derived historical threshold, formerly called a target | Eight post-labelled source observations exceed it; it is not a second proposed operating target |
| $0.035\text{ h}$ ($2.10\text{ min}$) | Post-labelled source maximum | Descriptive maximum; it is not a control limit or performance guarantee |

## 4. Provisional source summaries

The workbook's phase-tagged groups contain **78 pre-labelled observations** and **91 post-labelled observations**. Source references in [[Six Sigma Green Belt reports/Historical Data Analysis.xlsx]] are:

- Pre-labelled group: `'91Days pre implementation data'!A2:C79`.
- Post-labelled group: `'91Days post implementation data'!A2:C92`.
- Duplicate segment: `'91Days pre implementation data'!A80:C92`, repeating the post sheet's `A2:C14`; excluded from additional independent observation counts.

The post-labelled source dates span April 2–July 1, 2026, conflicting with a production validation window beginning July 1. No source dates are shifted. Exact calculations and chronology issues are recorded in [[Evidence Reconciliation|Evidence Reconciliation]].

These are descriptive statistics for source-labelled groups, not validated production phase performance:

| Statistic | Pre-labelled source group | Post-labelled source group |
| --- | ---: | ---: |
| Observation count ($n$) | $78$ | $91$ |
| Median ($P_{50}$) | $1.185\text{ h}$ | $0.029\text{ h}$ ($1.74\text{ min}$) |
| 25th percentile ($P_{25}$) | $1.0925\text{ h}$ | $0.029\text{ h}$ |
| Mean ($\bar{x}$) | $1.30961538\text{ h}$ | $0.02918022\text{ h}$ (approximately $1.751\text{ min}$) |
| Sample standard deviation ($s$) | $0.42200647\text{ h}$ | $0.00137649\text{ h}$ (approximately $4.96\text{ s}$) |
| Minimum / maximum | $0.890$ / $2.700\text{ h}$ | $0.023$ / $0.035\text{ h}$ ($1.38$ / $2.10\text{ min}$) |

Within the 91 post-labelled source observations, **three** exceed $2\text{ min}$ (two at $0.035\text{ h}$ and one at $0.034\text{ h}$), **eight** exceed $0.029\text{ h}$, at recorded values of $0.030$–$0.035\text{ h}$, and **zero** exceed $1.005\text{ h}$.

These counts concern different thresholds and unresolved source-labelled observations. They do not establish production acceptance, measure transaction-data accuracy, or establish the elimination of lookup, copy-paste, or accounting-reconciliation errors. For the proposed strict target of **under two minutes**, a run equal to two minutes would also fail acceptance; the recorded source values contain no exact two-minute observations.

## 5. Defect metrics and capability reporting

A defect calculation requires an approved requirement, an explicit unit, a defined number of opportunities per unit, and verified eligible observations. Once those definitions are agreed:

$$
DPO=\frac{D}{n\times O}, \qquad DPMO=DPO\times1{,}000{,}000
$$

where $D$ is the defect count and $O$ is the defined number of opportunities per unit. Until then, report **threshold exceedance counts** for the source groups.

Zero observed failures cannot establish a zero population failure rate. For an independent, representative binomial sample with zero failures in $n$ observations, the one-sided exact 95% upper bound is $1-0.05^{1/n}$. At $n=91$, that is approximately $3.24\%$. This is a methodological illustration, not a confidence claim for the unresolved workbook chronology. [NIST: Exact Binomial Confidence Limits](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/exacbino.htm).

Withhold project sigma levels, capability indices, industry-average comparisons, and before/after improvement percentages until the baseline, specification, measurement boundaries, and chronological samples are reconciled.

## 6. Project statements and verification sequence

**Problem statement:** The documented reporting workflow involves manual file collection, cross-month split-week handling, lookup maintenance, and repeated aggregation. Existing timing records use conflicting dates and scopes, preventing a defensible baseline comparison.

**Goal statement:** Use Power Query ingestion, schema normalization, and Power BI modeling to reduce manual effort and reporting delays. Assess the primary proposed under-two-minute refresh-duration target with an agreed measure, and track financial reconciliation and exception handling separately.

The next verification steps are to reconcile source chronology without shifting dates, define comparable measurements, approve operational targets, establish an eligible baseline and production window, and then calculate improvements and control-chart parameters. Related implementation and monitoring detail is in [[DMAIC Phase 4 - Improve Phase Report & Implementation Verification]] and [[Statistical Process Control (SPC)]].
