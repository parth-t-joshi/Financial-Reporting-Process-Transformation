# FP&A Analysis and Reconciliation

**Project:** T&E expense variance reporting within SG&A  
**Documentation revision:** October 6, 2026  
**Status:** Financial-analysis definitions and evidence requirements; monetary results not supplied in the reviewed sources

## 1. Business Questions

The reporting design supports department/account review of actual T&E spend against the applicable budget. A completed analysis should identify the amount and direction of the variance, explain an evidenced driver and state the resulting management action or investigation. Timing improvements alone do not demonstrate this financial-analysis skill.

## 2. Proposed Variance Presentation

For expenses:

$$
\text{Variance amount}=\text{Actual expense}-\text{Budget expense}
$$

$$
\text{Variance percentage}=\frac{\text{Actual expense}-\text{Budget expense}}{\text{Budget expense}}
$$

With positive expense amounts and a positive budget, a positive variance indicates overspend/unfavourable performance; a negative variance indicates underspend/favourable performance. Interpret refunds, reversals and negative budgets explicitly rather than assigning a colour solely from the sign.

These are proposed presentation definitions, not verified definitions of the existing PBIX measures. If budget is zero, display the monetary variance and mark the percentage **not applicable (zero budget)**; if budget is missing, label it **budget unavailable**. Keep missing input distinct from a genuine zero. DAX `DIVIDE` can return BLANK for a zero denominator, but the report should explain the resulting status. [Microsoft DIVIDE documentation](https://learn.microsoft.com/en-us/dax/divide-function-dax).

## 3. Comparable Reporting Scope

| Required attribute | Definition to retain with the analysis |
| --- | --- |
| Period | Reporting month/week, year, fiscal calendar and reporting cutoff |
| Actuals status | Provisional weekly actuals or closed-month actuals; identify accounting overrides |
| Budget | Approved version, period, currency and department/account grain |
| Currency | Same currency on both sides, with exchange-rate treatment identified if applicable |
| Scope | Comparable T&E accounts and departments; identify excluded or unmapped transactions |
| Hierarchy | Transaction-date organizational assignment or current hierarchy; disclose any restatement |

Compare at the grain supported by both actuals and budget. A monthly department budget does not automatically provide an employee/day budget. If a lower-grain comparison is required, document an approved allocation; otherwise leave unsupported budget/variance drilldowns unavailable. Weekly and monthly budgets must have an explicit selection or alignment rule rather than being summed as overlapping targets. [Microsoft higher-grain fact guidance](https://learn.microsoft.com/en-us/power-bi/guidance/relationships-many-to-many#relate-higher-grain-facts).

## 4. Independent GL Reconciliation

The current source inventory identifies a chart of accounts, which provides account classifications. An independent closed-GL actuals export or approved control total is still required to demonstrate monetary reconciliation.

For a matching period, currency, accounts and scope:

$$
\text{Reconciliation gap}=\text{Model actuals}-\text{Independent closed-GL actuals}
$$

The proposed release target is a $0.00 gap after approved precision and rounding rules. Retain both totals, the independent source identifier/cutoff, the comparison and any reconciling items. Separately check input completeness, duplicate transactions and unmapped identifiers: offsetting errors can produce a zero aggregate gap.

[[SOP#5. Reconciliation and Report Review]] owns the operating procedure. A named measure or report page is not sufficient evidence unless its inputs and calculations are verified.

## 5. Evidence for a Completed Portfolio Example

A monetary case has not been supplied for this documentation revision. Complete one public-safe reporting example from actual project evidence or an explicitly identified demonstration dataset, retaining:

1. Period, department/account scope, currency, budget version and closed/provisional status.
2. Actual and budget totals traced to their inputs; amount/percentage variance under the stated convention.
3. A driver explanation supported by transaction or approved contextual evidence. Distinguish timing effects from sustained spend changes.
4. A proposed action, responsible role and follow-up period; describe an action as implemented only with evidence.
5. A report screenshot and independent source-to-model/GL reconciliation for the same scope.

The existing documents establish a reporting-process design. A worked financial decision example remains the evidence needed to demonstrate its analytical use.
