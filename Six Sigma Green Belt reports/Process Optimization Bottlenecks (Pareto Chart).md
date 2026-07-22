# 📊 Pareto Chart: Process Optimization Bottlenecks

This Pareto analysis proves that manual column alignment and cross-month split-week reconciliation represent the primary operational bottlenecks slowing down the SG&A reporting cycle.

## 📝 Process Friction Breakdown Matrix

Integrate this matrix directly into your **Measure/Analyze Phase** documentation to demonstrate a calculated, data-driven automation strategy:

|   Rank    | Manual Reporting Process Step                                                                                   | Hours Spent Per Cycle | Individual % | Cumulative % | Six Sigma Optimization Target                                       |
| :-------: | :-------------------------------------------------------------------------------------------------------------- | :-------------------: | :----------: | :----------: | :------------------------------------------------------------------ |
|   **1**   | **Manual VLOOKUP & Data Alignment** (Cross-referencing transactions against 4 dimension tables)[cite: 10]       |       20 Hours        |    47.6%     |    47.6%     | **Vital Few** (Eliminated via Star Schema Relationships)[cite: 10]  |
|   **2**   | **Handling Split-Week Overlaps** (Manually calculating mid-week calendar month-end transitions)[cite: 10]       |       11 Hours        |    26.2%     |    73.8%     | **Vital Few** (Eliminated via Power Query M-Code Logic)[cite: 10]   |
|   **3**   | **Error Correction / Exceptions** (Troubleshooting lookups for resigned/terminated employees)[cite: 10]         |        6 Hours        |    14.3%     |    88.1%     | **Vital Few** (Automated via Conditional Merge Schema)[cite: 10]    |
|   **4**   | **Manual Pivot Aggregation & Formatting** (Rebuilding charts and variance formatting for L1 managers)[cite: 10] |        3 Hours        |     7.1%     |    95.2%     | **Useful Many** (Replaced by Power BI Interactive Canvas)[cite: 10] |
|   **5**   | **File Collection from Split Folders** (Opening separate 2025/2026 subfolders to copy datasets)[cite: 10]       |        2 Hours        |     4.8%     |    100.0%    | **Useful Many** (Replaced by Folder Ingestion Parameter)[cite: 10]  |
| **Total** | **Cumulative Monthly Processing Friction**[cite: 10]                                                            |     **42 Hours**      |  **100.0%**  |  **100.0%**  | **Targeted for 100% Pipeline Automation**                           |

![Pareto Chart](Images/Process%20Pareto%20Chart.png)

---

## 🎯 Strategic Takeaways

Instead of categorizing friction by generic financial department themes, this time-and-motion study maps the exact **procedural steps and technical friction points** where operational bandwidth is wasted.

By mapping the process steps in this hierarchy, you visually demonstrate to Lean Six Sigma auditors and executive leadership that targeting the top two procedural mechanics eliminates **73.8%** of reporting delays—and addressing the top three eliminates **88.1%** of total process lead time.