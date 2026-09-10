# Data dictionary

Fictional workshop data. All companies, people, communications and figures are invented.

Scenario snapshot: September 8, 2026 at 08:00 Central. Dates are ISO 8601; money is nominal USD; fractions represent percentages. CSV files use UTF-8 with BOM. Empty numeric values mean unknown, not zero. IDs are text. All rows are synthetic; no real Miller data or real market estimates are embedded.

## Joins

Accounts join contacts, opportunities, history, claims and receivables on account_id. Opportunities and history join services on service_id. Services.resource_pool joins capacity.resource_pool. Accounts.state maps to territories.states (semicolon-separated). Quality lots join employees on employee_id and accounts/service IDs. Evidence IDs identify communications and notes. Names are display labels, not safe join keys. Core challenge packets are views of this same data.

## Source authority

Controlled procedures and capability register govern approved scope and process. Finance governs credit clearance; Production planning governs capacity; territory memo governs current ownership. Customer messages govern stated customer intent and named contact changes; they do not authorize internal credit release. CRM is a historical system snapshot. Observations support hypotheses, not automatic causal conclusions.

## Intentional data limitations

A blank account on EM08 must be resolved. A004 CRM owner and contact lag newer evidence. O001/O007 repeat the same RFQ. Market and competitor claims have explicit uncertainty. Quality_lots is a selected sample, not company-wide quality performance. All such issues are for participants to reconcile.

## accounts.csv

24 records. Grain: One bill-to/customer site; names are not keys. Source: CRM export, August 31. Keys: account_id.

| Field | Type / meaning |

| --- | --- |

| account_id | text. Stable customer/site ID. Blank in notes or messages means general or identity unresolved. Join accounts.account_id. |

| account_name | text. Account name. Source value; consult table grain and dated evidence before interpreting. |

| segment | text. Segment. Source value; consult table grain and dated evidence before interpreting. |

| city | text. City. Source value; consult table grain and dated evidence before interpreting. |

| state | text. State. Source value; consult table grain and dated evidence before interpreting. |

| crm_owner | text. Crm owner. Source value; consult table grain and dated evidence before interpreting. |

| relationship | text. Relationship. Source value; consult table grain and dated evidence before interpreting. |

| crm_updated_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| domain | text. Domain. Source value; consult table grain and dated evidence before interpreting. |

## account_aliases.csv

4 records. Grain: One observed source alias. Source: Sales operations crosswalk, September 4. Keys: alias_id; account_id nullable.

| Field | Type / meaning |

| --- | --- |

| alias_id | text. Stable record identifier within this table; use in citations. |

| raw_name | text. Raw name. Source value; consult table grain and dated evidence before interpreting. |

| account_id | text. Stable customer/site ID. Blank in notes or messages means general or identity unresolved. Join accounts.account_id. |

| evidence | text. Evidence. Source value; consult table grain and dated evidence before interpreting. |

## contacts.csv

25 records. Grain: One contact record; CRM can lag customer messages. Source: CRM plus September 4 intake. Keys: contact_id; account_id.

| Field | Type / meaning |

| --- | --- |

| contact_id | text. Stable record identifier within this table; use in citations. |

| account_id | text. Stable customer/site ID. Blank in notes or messages means general or identity unresolved. Join accounts.account_id. |

| name | text. Name. Source value; consult table grain and dated evidence before interpreting. |

| role | text. Role. Source value; consult table grain and dated evidence before interpreting. |

| email | text. Email. Source value; consult table grain and dated evidence before interpreting. |

| status | text. Status. Source value; consult table grain and dated evidence before interpreting. |

| updated_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

## services.csv

3 records. Grain: One sellable service family; lead times are planning estimates after scope/material release. Source: Approved capabilities register, September 3. Keys: service_id.

| Field | Type / meaning |

| --- | --- |

| service_id | text. Approved service family. Join services.service_id; service fit still requires scope review. |

| offering | text. Offering. Source value; consult table grain and dated evidence before interpreting. |

| buyer_use | text. Buyer use. Source value; consult table grain and dated evidence before interpreting. |

| in_scope | text. In scope. Source value; consult table grain and dated evidence before interpreting. |

| out_of_scope | text. Out of scope. Source value; consult table grain and dated evidence before interpreting. |

| lead_time_weeks | number. Lead time weeks. Source value; consult table grain and dated evidence before interpreting. |

| planning_margin_floor_pct | number. Planning gross margin floor as decimal fraction; exceptions require GM approval. |

| resource_pool | text. Resource pool. Source value; consult table grain and dated evidence before interpreting. |

| evidence_id | text. Stable record identifier within this table; use in citations. |

## opportunities.csv

36 records. Grain: One raw CRM record; repeated RFQs can represent the same demand. Source: CRM export, August 31. Keys: opportunity_id; account_id; service_id.

| Field | Type / meaning |

| --- | --- |

| opportunity_id | text. Stable record identifier within this table; use in citations. |

| account_id | text. Stable customer/site ID. Blank in notes or messages means general or identity unresolved. Join accounts.account_id. |

| service_id | text. Approved service family. Join services.service_id; service fit still requires scope review. |

| customer_rfq | text. Customer-issued request identifier. Same account and RFQ can identify duplicate CRM demand. |

| title | text. Title. Source value; consult table grain and dated evidence before interpreting. |

| amount_usd | number. Raw CRM estimated scope value in USD. Not booked revenue. Duplicate RFQs and conditional phases must not be added blindly. |

| estimated_gross_margin_pct | number. CRM estimated gross profit / quoted revenue, decimal fraction. Not realized margin. |

| stage | text. Stage. Source value; consult table grain and dated evidence before interpreting. |

| crm_probability | number. Stale CRM stage probability, decimal fraction. Not validated forecast confidence. |

| expected_close_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| requested_ship_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| estimated_pool_hours | number. Estimated hours across the full opportunity in the service resource pool. Not weekly hours; requires scheduling confirmation. |

| updated_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

## order_history.csv

192 records. Grain: One invoiced completed job; job cost already includes rework; revenue is net of credits. Source: ERP closed jobs, January-August 2026. Keys: order_id; account_id; service_id.

| Field | Type / meaning |

| --- | --- |

| order_id | text. Stable record identifier within this table; use in citations. |

| account_id | text. Stable customer/site ID. Blank in notes or messages means general or identity unresolved. Join accounts.account_id. |

| service_id | text. Approved service family. Join services.service_id; service fit still requires scope review. |

| invoice_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| invoice_revenue_usd | number. Recognized invoice revenue net of credits, USD, for this completed job. |

| job_cost_usd | number. Completed-job cost in USD including rework. Do not subtract rework again. |

| promised_ship_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| actual_ship_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| rework_cost_usd | number. Rework portion of job cost in USD; already included in job_cost_usd. |

| source | text. Source. Source value; consult table grain and dated evidence before interpreting. |

## employees.csv

75 records. Grain: One fictional current employee; cohort is hire timing, not measured skill. Source: HR and training snapshot, September 4. Keys: employee_id.

| Field | Type / meaning |

| --- | --- |

| employee_id | text. Synthetic employee key. Join employees.employee_id. |

| role | text. Role. Source value; consult table grain and dated evidence before interpreting. |

| shift | text. Shift. Source value; consult table grain and dated evidence before interpreting. |

| hire_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| cohort | text. Cohort. Source value; consult table grain and dated evidence before interpreting. |

| orientation_completed_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| observed_job_signoff_date | text. Recorded observed-job check date. Blank means no signoff recorded, not proven inability. |

## quality_lots.csv

80 records. Grain: One first-inspection lot, 50 unique fabricated units; one primary rejection reason per rejected unit; selected service-family sample across 16 accounts, not all production. Source: QMS sample, weeks June 15-August 31. Keys: lot_id; account_id; service_id; employee_id.

| Field | Type / meaning |

| --- | --- |

| lot_id | text. Stable record identifier within this table; use in citations. |

| week_start | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| account_id | text. Stable customer/site ID. Blank in notes or messages means general or identity unresolved. Join accounts.account_id. |

| service_id | text. Approved service family. Join services.service_id; service fit still requires scope review. |

| employee_id | text. Synthetic employee key. Join employees.employee_id. |

| shift | text. Shift. Source value; consult table grain and dated evidence before interpreting. |

| cohort | text. Cohort. Source value; consult table grain and dated evidence before interpreting. |

| fixture | text. Fixture. Source value; consult table grain and dated evidence before interpreting. |

| drawing_revision | text. Drawing revision. Source value; consult table grain and dated evidence before interpreting. |

| traveler_revision | text. Traveler revision. Source value; consult table grain and dated evidence before interpreting. |

| first_inspected_units | number. Unique units receiving their first inspection in a sampled lot; denominator. |

| first_rejected_units | number. Units rejected at first inspection. Equals the sum of four mutually exclusive primary reason columns. |

| dimensional_units | number. Rejected units with dimensional condition as the primary reason. Counts do not prove root cause. |

| missing_weld_units | number. Rejected units with missing weld as primary reason; no technical acceptance thresholds supplied. |

| porosity_units | number. Rejected units with porosity as primary reason; not welding parameter guidance. |

| incomplete_record_units | number. Units held at first inspection primarily for incomplete documentation. |

| rework_hours | number. Hours, decimal values allowed. |

| inspection_method | text. Inspection method. Source value; consult table grain and dated evidence before interpreting. |

| source | text. Source. Source value; consult table grain and dated evidence before interpreting. |

## capacity.csv

15 records. Grain: One resource pool per week; hours include all shifts; uncommitted = available - committed - reserve. Source: Production planning, September 4. Keys: capacity_id; resource_pool links services.

| Field | Type / meaning |

| --- | --- |

| capacity_id | text. Stable record identifier within this table; use in citations. |

| week_start | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| resource_pool | text. Resource pool. Source value; consult table grain and dated evidence before interpreting. |

| available_hours | number. Resource-pool weekly capacity across all shifts before existing commitments and reserve. |

| committed_hours | number. Hours already assigned to backlog in that pool/week. |

| recovery_reserve_hours | number. Additional protected hours beyond committed_hours; subtract both to calculate uncommitted hours. |

| updated_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| notes | text. Notes. Source value; consult table grain and dated evidence before interpreting. |

## receivables.csv

3 records. Grain: One open invoice in the six-account exercise scope; absence means no open invoice in this extract. Source: Finance open AR, September 4. Keys: invoice_id; account_id.

| Field | Type / meaning |

| --- | --- |

| invoice_id | text. Stable record identifier within this table; use in citations. |

| account_id | text. Stable customer/site ID. Blank in notes or messages means general or identity unresolved. Join accounts.account_id. |

| open_balance_usd | number. Open invoice amount including any disputed portion. |

| due_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| disputed_usd | number. Disputed subset of open balance; do not add to balance. |

| credit_status | text. Credit status. Source value; consult table grain and dated evidence before interpreting. |

| updated_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

## territories.csv

3 records. Grain: One territory assignment effective September 1. Source: Sales director approved territory memo. Keys: territory_id; states to accounts.state.

| Field | Type / meaning |

| --- | --- |

| territory_id | text. Stable record identifier within this table; use in citations. |

| states | text. States. Source value; consult table grain and dated evidence before interpreting. |

| owner | text. Owner. Source value; consult table grain and dated evidence before interpreting. |

| effective_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| handoff | text. Handoff. Source value; consult table grain and dated evidence before interpreting. |

## quality_claims.csv

2 records. Grain: One customer claim; exposure is not incremental revenue and can overlap disputed AR. Source: Quality register, September 4. Keys: claim_id; account_id.

| Field | Type / meaning |

| --- | --- |

| claim_id | text. Stable record identifier within this table; use in citations. |

| account_id | text. Stable customer/site ID. Blank in notes or messages means general or identity unresolved. Join accounts.account_id. |

| opened_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| issue | text. Issue. Source value; consult table grain and dated evidence before interpreting. |

| status | text. Status. Source value; consult table grain and dated evidence before interpreting. |

| owner | text. Owner. Source value; consult table grain and dated evidence before interpreting. |

| next_due_date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| commercial_exposure_usd | number. Estimated claim exposure, may overlap disputed AR; not revenue or approved credit. |

| related_lot_ids | text. Semicolon-separated QMS lot IDs when supplied. Blank means not in this sample. |

| evidence_id | text. Stable record identifier within this table; use in citations. |

## market_research.csv

3 records. Grain: One synthetic segment estimate; reachable named sites, not national TAM; survey respondents not representative. Source: Fictional agency discovery memo, August 26; scenario assumptions, not real market research. Keys: market_id.

| Field | Type / meaning |

| --- | --- |

| market_id | text. Stable record identifier within this table; use in citations. |

| segment | text. Segment. Source value; consult table grain and dated evidence before interpreting. |

| reachable_accounts | number. Synthetic count of reachable customer sites in four-state segment list. Not national market size. |

| annual_outsourced_spend_low_usd | number. Synthetic low annual customer/site spend estimate; total outsourced scope may exceed Lakeview fit. |

| annual_outsourced_spend_high_usd | number. Synthetic high annual customer/site spend estimate; not achievable Lakeview revenue. |

| buyer_interviews | number. Buyer interviews. Source value; consult table grain and dated evidence before interpreting. |

| respondents_with_trigger | number. Interviewees reporting the stated trigger; not a market-wide conversion rate. |

| trigger | text. Trigger. Source value; consult table grain and dated evidence before interpreting. |

| sales_cycle_months_low | number. Sales cycle months low. Source value; consult table grain and dated evidence before interpreting. |

| sales_cycle_months_high | number. Sales cycle months high. Source value; consult table grain and dated evidence before interpreting. |

| fit | text. Fit. Source value; consult table grain and dated evidence before interpreting. |

| confidence | text. Confidence. Source value; consult table grain and dated evidence before interpreting. |

## competitors.csv

3 records. Grain: One fictional competitor snapshot; claims are attributed, not verified facts. Source: Synthetic agency research, August 26. Keys: competitor_id.

| Field | Type / meaning |

| --- | --- |

| competitor_id | text. Stable record identifier within this table; use in citations. |

| name | text. Name. Source value; consult table grain and dated evidence before interpreting. |

| positioning | text. Positioning. Source value; consult table grain and dated evidence before interpreting. |

| quoted_lead_time | text. Quoted lead time. Source value; consult table grain and dated evidence before interpreting. |

| buyer_perception | text. Buyer perception. Source value; consult table grain and dated evidence before interpreting. |

| gap | text. Gap. Source value; consult table grain and dated evidence before interpreting. |

| evidence | text. Evidence. Source value; consult table grain and dated evidence before interpreting. |

## channel_history.csv

3 records. Grain: One channel cohort; leads deduplicated within channel, cross-channel overlap unknown; revenue is part of ERP total. Source: Marketing attribution snapshot, September 4. Keys: channel_id.

| Field | Type / meaning |

| --- | --- |

| channel_id | text. Stable record identifier within this table; use in citations. |

| channel | text. Channel. Source value; consult table grain and dated evidence before interpreting. |

| period | text. Period. Source value; consult table grain and dated evidence before interpreting. |

| spend_usd | number. Nominal USD amount, not thousands. |

| leads | number. Leads. Source value; consult table grain and dated evidence before interpreting. |

| qualified_meetings | number. Qualified meetings. Source value; consult table grain and dated evidence before interpreting. |

| rfqs | number. Rfqs. Source value; consult table grain and dated evidence before interpreting. |

| won_jobs | number. Won jobs. Source value; consult table grain and dated evidence before interpreting. |

| attributed_revenue_usd | number. Channel-attributed won revenue, included in ERP history. Never add to ERP total. |

## campaign_costs.csv

7 records. Grain: One optional campaign cost assumption; unused items need not be purchased. Source: Fictional vendor planning rates, September 4. Keys: cost_id.

| Field | Type / meaning |

| --- | --- |

| cost_id | text. Stable record identifier within this table; use in citations. |

| item | text. Item. Source value; consult table grain and dated evidence before interpreting. |

| unit | text. Unit. Source value; consult table grain and dated evidence before interpreting. |

| cost_usd | number. Nominal USD amount, not thousands. |

## communications.csv

14 records. Grain: One message; account_id blank means unconfirmed identity or cross-company note. Source: Synthetic exported email corpus through September 4. Keys: evidence_id; account_id nullable.

| Field | Type / meaning |

| --- | --- |

| evidence_id | text. Stable record identifier within this table; use in citations. |

| date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| account_id | text. Stable customer/site ID. Blank in notes or messages means general or identity unresolved. Join accounts.account_id. |

| sender | text. Sender. Source value; consult table grain and dated evidence before interpreting. |

| recipient | text. Recipient. Source value; consult table grain and dated evidence before interpreting. |

| subject | text. Subject. Source value; consult table grain and dated evidence before interpreting. |

| body | text. Body. Source value; consult table grain and dated evidence before interpreting. |

## supervisor_account_notes.csv

10 records. Grain: One dated observation or management instruction; observations are not proven causes. Source: Synthetic notes through September 4. Keys: evidence_id; account_id nullable.

| Field | Type / meaning |

| --- | --- |

| evidence_id | text. Stable record identifier within this table; use in citations. |

| date | text. ISO calendar date; blank means not known or not applicable. Historical source date does not establish current truth. |

| account_id | text. Stable customer/site ID. Blank in notes or messages means general or identity unresolved. Join accounts.account_id. |

| author | text. Author. Source value; consult table grain and dated evidence before interpreting. |

| subject | text. Subject. Source value; consult table grain and dated evidence before interpreting. |

| body | text. Body. Source value; consult table grain and dated evidence before interpreting. |

## quality_summary.csv

6 records. Grain: One period-shift-cohort summary derived from quality_lots; subset sample only. Source: Calculated from quality_lots; sum counts before dividing. Keys: period + shift + cohort.

| Field | Type / meaning |

| --- | --- |

| period | text. Period. Source value; consult table grain and dated evidence before interpreting. |

| shift | text. Shift. Source value; consult table grain and dated evidence before interpreting. |

| cohort | text. Cohort. Source value; consult table grain and dated evidence before interpreting. |

| inspected | number. Inspected. Source value; consult table grain and dated evidence before interpreting. |

| rejected | number. Rejected. Source value; consult table grain and dated evidence before interpreting. |

| rejection_pct | number. First rejected units / first inspected units as decimal fraction. |

| first_pass_yield_pct | number. 1 - rejection_pct. Lot sample only. |

## segment_history.csv

6 records. Grain: One customer segment, January-August 2026; derived from accounts and order_history; rework already in job cost. Source: Calculated source summary, not a forecast. Keys: segment.

| Field | Type / meaning |

| --- | --- |

| segment | text. Segment. Source value; consult table grain and dated evidence before interpreting. |

| accounts | number. Accounts. Source value; consult table grain and dated evidence before interpreting. |

| jobs | number. Jobs. Source value; consult table grain and dated evidence before interpreting. |

| revenue_usd | number. Nominal USD amount, not thousands. |

| gross_profit_usd | number. Nominal USD amount, not thousands. |

| gross_margin_pct | number. Gross profit / revenue as decimal fraction, calculated from source totals. |

| on_time_jobs | number. On time jobs. Source value; consult table grain and dated evidence before interpreting. |

| rework_cost_usd | number. Rework portion of job cost in USD; already included in job_cost_usd. |
