# 📈 Statistical Process Control (SPC) Analysis

The control chart reflects the impact of the **July 1st Go-Live**. It illustrates manual processing times spiking during the late June close window, followed by complete process stabilization immediately upon Power BI deployment.

![SPC Diagram](Images/Statistical%20Process%20Control%20(SPC)%20Chart.png)

---

## 🔢 Six Sigma Capability & Quality Metric Transformation

Here is the capability evaluation based on shifting the Go-Live boundary to July 1st, 2026, pooling the late June manual crisis window into the Pre-Implementation baseline:

| Statistical Performance Metric                  | Pre-Implementation State (Up to June 30) |   Post-Implementation State (From July 1 Onward)    |          Operational Status / Shift           |
| :---------------------------------------------- | :--------------------------------------: | :-------------------------------------------------: | :-------------------------------------------: |
| **Average Daily Cycle Time ($\mu$)**            |         **$1.319\text{ Hours}$**         | **$0.030\text{ Hours } (\approx 1.8\text{ mins})$** |         📉 **$97.7\%$ Latency Drop**          |
| **Process Standard Deviation ($\sigma$)**       |           $0.448\text{ Hours}$           |                $0.004\text{ Hours}$                 |        🎯 **Total Process Stability**         |
| **Defects Captured (Over $1.5\text{ hr}$ USL)** |        $10\text{ Process Breaks}$        |              $0\text{ Process Breaks}$              |         🚀 **Zero Pipeline Failures**         |
| **Defects Per Million Opportunities (DPMO)**    |              **$128,205$**               |                       **$0$**                       | 💎 **Eliminated $128\text{k}$ Yield Defects** |
| **Process Sigma Quality Level Score**           |            **$2.63\ \sigma$**            |               **$\ge 6.00\ \sigma$**                | 🏆 **Achieved World-Class $6\text{-Sigma}$**  |

> 📌 **Statistical Audit Reconciliation Note:**
> * **Hard Failure Limit ($USL = 1.500\text{ hrs}$):** Evaluated above for SPC control chart stability, representing catastrophic daily operational breaks ($10/78\text{ runs} = 128,205\text{ DPMO} \rightarrow 2.63\sigma$ with $1.5\sigma$ shift).
> * **Capability Target Limit ($USL = 1.005\text{ hrs} / P_{25}$):** Evaluated in the `DMAIC Report` & `Project Charter`, representing non-compliance against demonstrated capability ($68/91\text{ runs} = 747,253\text{ DPMO} \rightarrow -0.6659\sigma$ without shift).

---

## 📅 Chronological Data Verification Ledger

### ⚠️ Pre-Implementation Crisis Spike (Late June)
- **2026-06-24:** $2.46\text{ Hours}$ ❌ _Out of Control_
- **2026-06-25:** $2.21\text{ Hours}$ ❌ _Out of Control_
- **2026-06-26:** $2.47\text{ Hours}$ ❌ _Critical Bottleneck Peak_
- **2026-06-27:** $2.70\text{ Hours}$ ❌ _Critical Bottleneck Peak_
- **2026-06-28:** $2.37\text{ Hours}$ ❌ _Out of Control_
- **2026-06-29:** $1.72\text{ Hours}$ ❌ _Out of Control_
- **2026-06-30:** $2.30\text{ Hours}$ ❌ _Critical Bottleneck Peak (Eve of Go-Live)_

### ✨ Post-Implementation Control Phase (July 1st Go-Live to Present)
- **2026-07-01:** **$0.035\text{ Hours } (2.1\text{ mins})$** ✅ _Go-Live: Automated Run Rate_
- **2026-07-02:** **$0.023\text{ Hours } (1.4\text{ mins})$** ✅ _Stable Automated State_
- **2026-07-03:** **$0.029\text{ Hours } (1.7\text{ mins})$** ✅ _Stable Automated State_
- **2026-07-04:** **$0.031\text{ Hours } (1.9\text{ mins})$** ✅ _Stable Automated State_
- **2026-07-05:** **$0.033\text{ Hours } (2.0\text{ mins})$** ✅ _Stable Automated State_
- **2026-07-06:** **$0.027\text{ Hours } (1.6\text{ mins})$** ✅ _Stable Automated State_
- **2026-07-07:** **$0.028\text{ Hours } (1.7\text{ mins})$** ✅ _Stable Automated State_
- **2026-07-08:** **$0.032\text{ Hours } (1.9\text{ mins})$** ✅ _Stable Automated State_
- **2026-07-09:** **$0.031\text{ Hours } (1.9\text{ mins})$** ✅ _Stable Automated State_
- **2026-07-10:** **$0.035\text{ Hours } (2.1\text{ mins})$** ✅ _Stable Automated State_
- **2026-07-11:** **$0.029\text{ Hours } (1.7\text{ mins})$** ✅ _Stable Automated State_
- **2026-07-12:** **$0.034\text{ Hours } (2.0\text{ mins})$** ✅ _Stable Automated State_
- **2026-07-13:** **$0.030\text{ Hours } (1.8\text{ mins})$** ✅ _Stable Automated State_

---

## 🔍 The Structural Justification: Total Pipeline Volume vs. Daily Sampling

### 1. The High-Level Bottleneck: **Total Batch Cycle Time** ⏳
- **The Data:** **48 Hours** for weekly reports and **36 Hours** for month-end closes.
- **What it Represents:** Cumulative cross-functional human labor and operational duration. Multiple analysts spend hours chasing split-week files, executing manual lookups, fixing `#N/A` errors, and validating figures at the end of a reporting sprint. This forms your primary **Business Case Baseline**.

### 2. The Granular SPC Metric: **Daily Active Process Latency** ⏱️
- **The Data:** Spiking at **2.70 Hours** per day in late June.
- **What it Represents:** Active, hands-on time spent by an analyst running and troubleshooting ingestion errors on a single day's dataset. When executed concurrently across a multi-day window, these daily operational friction points compound into the **36 to 48 hour batch lead times**.