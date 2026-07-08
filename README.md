# \# Financial Reporting Process Transformation (Lean Six Sigma Green Belt)

# 

# \## 🚀 Executive Summary \& ROI

# An enterprise-grade optimization project integrating \*\*Lean Six Sigma methodologies\*\* with \*\*FP\&A workflows\*\* to automate the Travel \& Expense (T\&E) reporting pipeline. By architecting an automated ETL pipeline using \*\*Power Query\*\* and \*\*Power BI\*\*, this project completely eliminated manual data manipulation.

# 

# \* \*\*Weekly Reporting Cycle Time:\*\* Reduced from \*\*48 Hours\*\* to \*\*Fully Automated (<5 mins refresh)\*\*

# \* \*\*Monthly Reporting Cycle Time:\*\* Reduced from \*\*36 Hours\*\* to \*\*Fully Automated\*\*

# \* \*\*Defect Rate:\*\* Dropped to \*\*0%\*\* by eliminating manual copy-paste errors, broken `VLOOKUP`/`XLOOKUP` formulas, and split-week structural anomalies.

# 

# \---

# 

# \## 📈 Core Skills Demonstrated

# \* \*\*Process Improvement:\*\* Lean Six Sigma DMAIC Framework, Root Cause Analysis, SIPOC Mapping, Control Plans.

# \* \*\*Corporate Finance / FP\&A:\*\* Month-End Close Adjustments, Accrual Dynamics, OPEX \& T\&E Control Frameworks, Variance Analysis.

# \* \*\*Data Engineering:\*\* Power Query (M-Code), Star Schema Relational Data Modeling, Dynamic Parameterization.

# \* \*\*Business Intelligence:\*\* Power BI Dashboard Design, Advanced DAX Measures.

# 

# \---

# 

# \## 🛠️ The Problem vs. The Solution

# \### The "As-Is" Manual Process (Muda/Waste)

# Previously, the process required manually extracting and consolidating data from 6 fragmented enterprise datasets. It involved heavy reliance on volatile Excel functions (`SUMIFS`, `VLOOKUPs`) and manual layout adjustments. 

# \* \*\*The Obsolete Data Challenge:\*\* Weekly reporting during month-end overlaps became highly complex because historical weeks became obsolete once books of accounts were officially closed and adjusted monthly.

# 

# \### The "To-Be" Automated Pipeline

# Developed a dynamic Power Query architecture that ingests expanding year-to-date folders, normalizes conflicting split-week schemas, handles month-end accounting overrides, and pipes clean data directly into a centralized Power BI model (`Variance Analysis.pbix`).

# 

# \---

# 

# \## 📂 Repository Architecture

# (Your clean folder tree layout goes here so recruiters can see your professional organization)

# 

# \---

# \## 🛠️ How to Run This Model (Dynamic Path Configuration)

# 

# This model uses \*\*Power Query Parameters\*\* to manage file paths globally. If you download this repository to review the data pipelines, you do not need to change individual query steps. You can update the source path globally in under 60 seconds:

# 

# \### Step-by-Step Path Setup:

# 1\. Download the files or clone this repository to your local drive.

# 2\. Open `Variance Analysis.pbix` in \*\*Power BI Desktop\*\*.

# 3\. On the \*\*Home\*\* tab of the ribbon, click the dropdown arrow under \*\*Transform Data\*\* and select \*\*Edit Parameters\*\*.

# &#x20;  \*(Alternatively, click \*\*Transform Data\*\* to open the Power Query Editor, and click \*\*Manage Parameters\*\* in the Home ribbon).\*

# 4\. Update the value of the path parameter (e.g., `File\_Source\_Directory`) to match the local folder path where you saved this repository on your computer.

# 5\. Click \*\*OK\*\*, then click \*\*Apply Changes\*\* on the yellow warning bar. The entire ETL pipeline will automatically refresh against your local data copies without breaking any steps!

