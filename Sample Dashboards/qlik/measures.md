# KPI definitions (Qlik master measures)

Use these on the department pages. Add `{<Shift_IsCurrentWeek={1}>}` or `{<Shift_IsPreviousWeek={1}>}` (or the matching flag for each table) to switch between this week and last week.

## Production and productivity

| KPI | Expression |
|---|---|
| Cases produced | `Sum(Rec_Signed_Cases)` |
| Planned cases | `Sum(Planned_Cases)` |
| Cases vs plan % | `Sum(Rec_Signed_Cases) / Sum(Planned_Cases)` |
| Recovered hours | `Sum(Recovered_Hours)` |
| Worked hours | `Sum(Worked_Hours)` |
| Discounted hours | `Sum(Discounted_Hours)` |
| **Productivity %** | `Sum(Recovered_Hours) / (Sum(Worked_Hours) - Sum(Discounted_Hours))` |
| Agency share % | `Sum(Agency_Hours) / Sum(Worked_Hours)` |
| Orders awaiting close | `Sum(Order_Awaiting_Close)` |

## Waste and yield

| KPI | Expression |
|---|---|
| Actual waste cost | `Sum(Actual_Waste_Cost)` |
| Waste variance value | `Sum(Waste_Variance_Value)` |
| Waste % of production value | `Sum(Actual_Waste_Cost) / Sum(Rec_Std_Value)` |
| Yield variance (£) | `Sum(Yield_Variance_GBP)` |
| Average yield vs standard | `Avg(Yield_Actual_Pct) - Avg(Yield_Std_Pct)` |
| Giveaway (£) | `Sum(Giveaway_Var_GBP)` |

## Quality

| KPI | Expression |
|---|---|
| NCRs raised | `Count(DISTINCT NCR_No)` |
| Open NCRs | `Count({<NCR_State={'OPEN'}>} DISTINCT NCR_No)` |
| Value on hold (£) | `Sum(NCR_Inventory_Value)` |
| Manufacturing-caused NCRs | `Count({<NCR_Manufacturing={'YES'}>} DISTINCT NCR_No)` |

## Health and safety

| KPI | Expression |
|---|---|
| Incidents | `Count(DISTINCT Inc_No)` |
| Injuries | `Sum(Inc_Is_Injury)` |
| Lost-time incidents | `Sum(Inc_Is_Lost_Time)` |
| Days since last injury | `$(vToday) - Max({<Inc_Is_Injury={1}>} Inc_Date)` |

## Engineering, stock and governance

| KPI | Expression |
|---|---|
| Breakdown minutes | `Sum(Eng_Breakdown_Mins)` |
| PPMs completed | `Sum(Eng_PPMs_Completed)` |
| Stock value in location (£) | `Sum(Stock_Value)` |
| Open actions | `Count({<Act_Status-={'CLOSED'}>} Act_ID)` |
| Overdue actions | `Sum(Act_Is_Overdue)` |
| Actions closed on time % | `Sum(Act_Closed_On_Time) / Count({<Act_Status={'CLOSED'}>} Act_ID)` |
| Average audit score | `Avg(Audit_Score)` |

## Scorecard colours

| Status | Rule (example: productivity) |
|---|---|
| Green | 90% and above |
| Amber | 80–90% |
| Red | Below 80% |
