# Operations study: changeovers and capacity

All records, observations and quotes in this study are invented for the Lakeview workshop. Source family OP. This is a supplemental fictional study, not a correction to the original workbook.

## OP01 | Study scope | September 4, 2026
Jules Mercer, Production planning, and the maintenance lead reviewed 18 selected changeovers in the Production resource pool between August 24 and September 4. This is a selected event study, not all shop downtime. F17 handles one repeat frame family. F12 handles a different frame family and provides context rather than a matched control. Study cell and crew labels are local anonymous identifiers, not employee IDs or customer IDs.

For F17, six pairs each compare two runs of the same family with the same crew on the same date. One run uses the shared kit arrangement. The other uses a borrowed trolley with dedicated, pre-staged locator blocks and clamps. Shared came first in P01, P03 and P05. Staged came first in the other pairs. All six crews are established workers. These are practical trial observations with six pairs, not randomized proof or a company-wide forecast.

## OP02 | Event log
One row is one changeover. All minute fields measure elapsed cell time. The four component intervals are mutually exclusive and exhaust elapsed_min. Do not add elapsed_min to the component minutes. Standard time is a planning reference. It is not a technical acceptance limit. All recorded release checks completed. This statement alone does not establish longer-term defect performance.

| event_id | date | pair_id | shift | crew | fixture | kit | standard_min | find_kit_min | fit_adjust_min | release_check_min | other_wait_min | elapsed_min |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| OC01 | 2026-08-24 | P01 | Day | D1 | F17 | Shared | 30 | 26 | 16 | 24 | 6 | 72 |
| OC02 | 2026-08-24 | P01 | Day | D1 | F17 | Staged | 30 | 4 | 2 | 24 | 2 | 32 |
| OC03 | 2026-08-25 | P02 | Evening | E1 | F17 | Shared | 30 | 30 | 14 | 24 | 4 | 72 |
| OC04 | 2026-08-25 | P02 | Evening | E1 | F17 | Staged | 30 | 6 | 2 | 24 | 2 | 34 |
| OC05 | 2026-08-27 | P03 | Day | D2 | F17 | Shared | 30 | 28 | 18 | 24 | 2 | 72 |
| OC06 | 2026-08-27 | P03 | Day | D2 | F17 | Staged | 30 | 4 | 4 | 24 | 2 | 34 |
| OC07 | 2026-08-28 | P04 | Evening | E2 | F17 | Shared | 30 | 24 | 16 | 24 | 4 | 68 |
| OC08 | 2026-08-28 | P04 | Evening | E2 | F17 | Staged | 30 | 2 | 2 | 24 | 2 | 30 |
| OC09 | 2026-09-02 | P05 | Day | D3 | F17 | Shared | 30 | 32 | 12 | 24 | 2 | 70 |
| OC10 | 2026-09-02 | P05 | Day | D3 | F17 | Staged | 30 | 4 | 2 | 24 | 0 | 30 |
| OC11 | 2026-09-04 | P06 | Evening | E3 | F17 | Shared | 30 | 28 | 14 | 24 | 4 | 70 |
| OC12 | 2026-09-04 | P06 | Evening | E3 | F17 | Staged | 30 | 4 | 2 | 24 | 2 | 32 |
| OC13 | 2026-08-24 | - | Day | C1 | F12 | Shared | 30 | 4 | 4 | 24 | 2 | 34 |
| OC14 | 2026-08-25 | - | Evening | C2 | F12 | Shared | 30 | 6 | 4 | 24 | 2 | 36 |
| OC15 | 2026-08-27 | - | Day | C3 | F12 | Shared | 30 | 2 | 4 | 24 | 2 | 32 |
| OC16 | 2026-08-28 | - | Evening | C4 | F12 | Shared | 30 | 6 | 6 | 24 | 2 | 38 |
| OC17 | 2026-09-02 | - | Day | C5 | F12 | Shared | 30 | 4 | 6 | 24 | 2 | 36 |
| OC18 | 2026-09-04 | - | Evening | C6 | F12 | Shared | 30 | 4 | 4 | 24 | 2 | 34 |

## OP03 | Floor observations | September 4, 2026
On the shared F17 arrangement, the correct locator blocks and clamps travel between two stations. Crews search the shared bin or wait for the other station to release them. Several visually similar locator blocks require removal and refitting before they match the setup sheet. The borrowed trolley trial put a complete labeled set beside F17 before the changeover. Crews used the same released drawings and setup sheets in both conditions. F12 uses a different, simpler kit and does not draw from the F17 bin.

The trial did not change welding parameters, technical acceptance requirements, staffing levels or the first-piece release procedure. It does not establish the effects of overtime, the full backlog, or all sources of margin leakage.

## OP04 | Planning assumptions and purchase estimate | September 4, 2026
- OP-A1: Planning expects 20 comparable F17 changeovers per week during the next four weeks. This is an assumption for testing the proposal, not a historical count from this sample.
- OP-A2: For a sensitivity estimate, assume 50% to 100% of the observed average reduction carries over to ordinary production. Show both ends. This range is a scenario assumption, not a statistical confidence interval.
- OP-Q1: Superseded by OP06 for the current workshop purchase decision. The earlier $1,800 loose-kit/trolley estimate is not a complete-fixture duplication quote. Maintenance's three-hour kit-preparation estimate is also not a complete-fixture installation estimate. No labor dollar rate is supplied.
- OP-A3: Released cell time can create usable capacity only if the next work, material and operator availability align. Hours released are not automatically cash savings, incremental sales or booked capacity. No overtime reduction or labor saving has been authorized or measured.

## OP05 | Process and ownership boundaries
Maintenance can prepare and label the kit. Operations owns the trial and standard work. Quality retains control of first-piece release under PR02. Production planning must approve any change to the capacity schedule. The September capacity table has not incorporated a potential wider rollout of this trial. Do not add all event minutes to capacity or multiply a selected sample into plant-wide losses. There are no machine sensor streams or automatic control connections in the supplied data.

## Source connections
The study resource_pool is Production, matching capacity.csv. Event IDs identify observations, not orders. The events do not join to order_history by date and must not be treated as closed-job cost entries. Use the original company background, capability register and controlled procedures for company claims and operating constraints.


## OP06 | Workshop decision amendment | September 8, 2026
These are fictional scenario assumptions added for the executive exercise, not additional measured trial results.
- The proposed full duplication option requires two complete fixtures at $50,000 each: $100,000 purchase cost, excluding relocation and installation.
- Two additional fixtures cannot fit in the current production layout without relocating existing equipment or storage. Exact footprint, suitable relocation area, relocation cost and installation time are not supplied. Teams must investigate or label planning assumptions and hold points.
- The observed staged trial used borrowed equipment and a prepared kit. Its six pairs establish a bundled practical comparison, not proof that a $100,000 purchase is necessary or sufficient. Do not infer full-fixture installation effects from that trial.
- Alternatives remain improved shared-tool identification/preparation and explicit scheduling/turnaround allowances. Their labor, coordination and flexibility costs must be accepted and estimated transparently; no zero-cost alternative is established.
- The event log does not separate search from waiting for the other station. No previous-run finish, release, repack, transfer or next-required timestamps are supplied. Scheduling remains a competing hypothesis.
- OP04's 20-changeover assumption and 50%-100% carryover remain conditional short-term scenarios, not 90-day forecasts or cash savings. PR02 release and planning authorization still apply.
