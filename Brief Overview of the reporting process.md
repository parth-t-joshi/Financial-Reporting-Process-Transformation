We are incorporating the SG&A expenses (Sales general & Administration expense) KAC process. I have attempted to standardize it by introducing consistent reports that you will receive weekly and monthly via email. To improve efficiency, I have leveraged Power Query to eliminate repetitive manual steps involved in generating these reports.
## Data Sources:
All data flowing through Power Query is sourced from the following datasets:
1. Master list of all employees
2. List of GL numbers with GL Title, GL Subcategory, US GAAP Category, Group (P&L / Balance Sheet); in short chart of accounts
3. Departments list & department codes with its reporting director level managers (with their emp IDs, email IDs, & their director level designations)
4. PNLgroups – P&L group details, including department codes and leaders
5. Monthly budget
6. Weekly budget

---
## File Structure and Data Flow
Each month and each week, the following files will be maintained:
1. In monthly folder, `Credit_Cards_Data - 01 January.xlsx`, `Credit_Cards_Data - 02 February.xlsx`, `…`, till `Credit_Cards_Data - 12 December.xlsx`
2. In weekly folder, `Credit_Cards_Data - Week 01 - January.xlsx`, `Credit_Cards_Data - Week 02 - January.xlsx`, `…`, `Credit_Cards_Data - Week 06 - February.xlsx`, `…`, `Credit_Cards_Data - Week 14 - March.xlsx`, `Credit_Cards_Data - Week 14 - April.xlsx`, `…`, `Credit_Cards_Data - Week 31 - July.xlsx`, `Credit_Cards_Data - Week 31 - August.xlsx`, `…`, Till `Credit_Cards_Data - Week 53 - December.xlsx`

Here, the above files names are from year 2025, 2026 weekly files names may vary.
Data flows from the datasets mentioned above and, Weekly and monthly files into `Variance Analysis.pbix`.
From the weekly and monthly files, data flows via Power Query into the `Variance Analysis.pbix` file.

---
## Folder Structure
### For 2025, we currently maintain the following folders:
#### 📂 Monthly
`Credit_Cards_Data - 01 January.xlsx`
`Credit_Cards_Data - 02 February.xlsx`
…
Till `Credit_Cards_Data - 12 December.xlsx`
#### 📂 Weekly
`Credit_Cards_Data - Week 01 - January.xlsx`
`Credit_Cards_Data - Week 02 - January.xlsx`
…
`Credit_Cards_Data - Week 14 - March.xlsx`
`Credit_Cards_Data - Week 14 - April.xlsx`
…
`Credit_Cards_Data - Week 31 - July.xlsx`
`Credit_Cards_Data - Week 31 - August.xlsx`
…
Till `Credit_Cards_Data - Week 53 - December.xlsx`
### For year 2026, we have following folders:
#### 📂 Monthly
`Credit_Cards_Data - 01 January.xlsx`
`Credit_Cards_Data - 02 February.xlsx`
`Credit_Cards_Data - 03 March.xlsx`
`Credit_Cards_Data - 04 April.xlsx`
`Credit_Cards_Data - 05 May.xlsx`
`Credit_Cards_Data - 06 June.xlsx`
`Credit_Cards_Data - 07 July.xlsx`
#### 📂 Weekly
`Credit_Cards_Data - Week 01 - January.xlsx`
`Credit_Cards_Data - Week 02 - January.xlsx`
…
`Credit_Cards_Data - Week 14 - March.xlsx`
`Credit_Cards_Data - Week 14 - April.xlsx`
…
`Credit_Cards_Data - Week 18 - April.xlsx`
`Credit_Cards_Data - Week 18 - May.xlsx`
…
`Credit_Cards_Data - Week 28 - June.xlsx`
`Credit_Cards_Data - Week 28 - July.xlsx`
…
Till `Credit_Cards_Data - Week 32 - July.xlsx`

Additionally, the number of weekly and monthly xlsx files will continue to increase as we progress through the year.