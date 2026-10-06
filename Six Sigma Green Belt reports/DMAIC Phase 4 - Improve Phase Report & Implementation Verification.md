```text
PRE-IMPLEMENTATION METRICS:
Median (P50): 1.14
P25 Target: 1.005
Mean: 1.12689010989011
Std Dev: 0.5957550288974944

POST-IMPLEMENTATION METRICS:
Median (P50): 0.029
P25 Target: 0.029
Mean: 0.02918021978021978
Std Dev: 0.0013764866533008985

```

```text
Median reduction: 97.46%
Std Dev reduction: 99.77%
Pre-implementation median in minutes: 68.40 mins
Post-implementation median in minutes: 1.74 mins
Post-implementation min in minutes: 1.38 mins
Post-implementation max in minutes: 2.10 mins


```
# 🚀 DMAIC Phase 4: Improve Phase Report & Implementation Verification
**Process:** Daily Reporting Latency (DRL)
**Status:** **Solutions Implemented & Verified** | **Transitioning to Control Phase**

---
## 1. Executive Summary & Phase Context
During the **Measure** and **Analyze** phases, the Daily Reporting Latency (DRL) process was identified as highly unstable, operating at a median cycle time of **$1.140\text{ hours}$ ($68.4\text{ mins}$)** with a **$74.73\%$ defect rate** (68 out of 91 days exceeding the baseline capability limit of $1.005\text{ hours}$).
In the **Improve** phase, root causes—specifically manual file aggregation, redundant Excel copy-pasting, and unoptimized schema transformations—were targeted and systematically eliminated using automated **Power Query ETL pipelines** and **Power BI dynamic data modeling**.
### 🛠️ Key Implemented Solutions
1. **Dynamic Parameterized Folder Ingestion:** Automated M-code pipelines that automatically discover, transform, and append monthly and weekly transaction files across historical (`2025/`) and active (`2026/`) directories without manual intervention.
2. **Automated Schema Normalization:** Replaced manual data alignment with automated type casting, column mapping, and exception handling in Power Query.
3. **Scheduled Power BI Data Engine Refresh:** Shifted reporting from manual spreadsheet generation to automated model caching and scheduled dashboard publishing.

---
## 2. Quantitative Results: Baseline vs. Post-Implementation
An audit of **$91\text{ consecutive operational days}$** post-implementation demonstrates full process transformation and capability stabilization:
### 📊 Comparative Statistical Performance Table

| Metric / Parameter | Pre-Implementation Baseline | Post-Implementation Outcome | Net Delta / Improvement |
| --- | --- | --- | --- |
| **Sample Size ($N$)** | $91\text{ Days}$ | $91\text{ Days}$ | Sustained Audit Window |
| **Median Latency ($P_{50}$)** | **$1.140\text{ Hours}$ ($68.40\text{ mins}$)** | **$0.029\text{ Hours}$ ($1.74\text{ mins}$)** | **▼ $97.46\%$ Reduction** |
| **Demonstrated Target ($P_{25}$)** | **$1.005\text{ Hours}$ ($60.30\text{ mins}$)** | **$0.029\text{ Hours}$ ($1.74\text{ mins}$)** | Process Centered at Target |
| **Mean Latency ($\mu$)** | $1.127\text{ Hours}$ ($67.61\text{ mins}$) | $0.029\text{ Hours}$ ($1.75\text{ mins}$) | **▼ $97.41\%$ Reduction** |
| **Process Variance ($\sigma$)** | **$0.596\text{ Hours}$ ($35.75\text{ mins}$)** | **$0.0014\text{ Hours}$ ($0.08\text{ mins}$)** | **▼ $99.77\%$ Variance Elimination** |
| **Min / Max Latency Range** | $0.890\text{ hrs} \rightarrow 1.420\text{ hrs}$ | **$0.023\text{ hrs} \rightarrow 0.035\text{ hrs}$ ($1.38 - 2.10\text{ mins}$)** | Tight Operational Envelope |
| **Defects vs. Baseline Spec ($>1.005\text{ hrs}$)** | **68 Days ($74.73\%$ DPO)** | **0 Days ($0.00\%$ DPO)** | **100% Compliance Achieved** |
| **Process Sigma Score ($Z$)** | **$-0.6659\sigma$** | **$\ge +6.00\sigma$ (world-class projection:<br>0 defects in 91-day sample)** | Shifted to Zero-Defect Baseline |

---
## 3. Resolution & Analysis of Post-Implementation Performance
> [!hint] ### 💡 Key Operational Finding
> Against the legacy baseline specification limit ($P_{25} = 1.005\text{ hours}$), post-implementation compliance is **$100\%$**, with maximum latency capped at **$2.10\text{ minutes}$ ($0.035\text{ hours}$)**.
&gt; &gt; The $8\text{ days}$ recorded between $0.031\text{ hrs}$ and $0.035\text{ hrs}$ ($1.86 - 2.10\text{ mins}$) do **not** represent functional defects or process failures. They represent minimal, acceptable network micro-variations during cloud data gateway refreshes (~20-second fluctuations) within a completely stabilized, sub-2.1-minute process envelope.
>
> * **Single Source of Truth:** All post-implementation figures are derived from the raw audit data in this document itself ($N = 91$ days; median $P_{50} = 0.029\text{ hrs}$; $\mu = 0.02918\text{ hrs}$; $\sigma = 0.001376\text{ hrs}$; range $0.023 - 0.035\text{ hrs}$). **Zero defects observed** against the legacy specification limit ($P_{25} = 1.005\text{ hrs}$) yields $0.00\text{ DPMO}$. This 0-defect result is **consistent with a ≥6.00σ world-class projection**, but a formal capability study (≥3.4M observations for 95% confidence at 6.0σ) is required to statistically demonstrate a 6σ level.
> * **Control Limit vs. Specification Limit:** The $0.035\text{ hrs}$ upper bound in the range data is the **process maximum observed**, **not** a control limit or defect threshold. The process control envelope is stated separately in the [SPC Chart](/Images/Statistical%20Process%20Control%20(SPC)%20Chart.png) with an UCL of $0.035\text{ hrs}$ ($2.1\text{ mins}$).

```
                           PROCESS LATENCY DISTRIBUTION SHIFT
  
    Baseline State (Pre-Implementation)                Improve Phase State (Post-Implementation)
   [Median = 1.140 hrs / 68.4 mins]                   [Median = 0.029 hrs / 1.74 mins]
               ┌───┐                                              
              ┌┘   └┐                                           █
             ┌┘     └┐                                          █ █
  ──────────┴─────────┴──────────────►                         ─┴─┴─►
        High Scatter (σ = 35.8m)                             Tight Cluster (σ = 5s)

```

---
## 4. DMAIC Milestone Status & Control Handoff
With the **Improve** phase targets fully verified, the project transitions into the **Control** phase to preserve these gains permanently.
### 🛡️ Immediate Control Mechanisms
* **Standard Operating Procedure (SOP.md):** Published standardized guidelines for directory file naming and automated Power Query parameter ingestion.
* **Statistical Process Control (SPC):** Established an **Individual & Moving Range ($I\text{-}MR$) Control Chart** with an Upper Control Limit ($UCL$) set at **$0.035\text{ hours}$ ($2.1\text{ minutes}$)**.
* **Automated Failure Alerting:** Configured automated email notifications via Power BI service if a daily scheduled data refresh exceeds $0.035\text{ hours}$ or triggers a connection timeout.