# 20260511 (jpalathi):
- Removed all SmartAnalytics default tabs from the workspace; defaults still available in the L1->UE Radio workspace.
- Redid all tables to include the new KPIs introduced in SmartAnalytics v26.

## Notes:
- `DL/UL Modulation`, `Avg Layers` removed from `Radio` tables.
    - `DL/UL Modulation` is not the exact modulation, rather the most used modulation in `PDSCH/PUSCH`. More detailed KPIs pertaining to modulation are added onto the `PDSCH/PUSCH` tables.
    - `Avg Layers` only shows MCG group average; SCG has a separate KPI.
        - Addded `DL/UL Layer Summary` instead for comprehensive layer counts across MCG & SCG.
        - **Note:** Layer summary values (e.g., "2 Layers MCG, 4 Layers SCG") are upper bounds. Actual layer usage may be lower (minimum 1 layer).
        - Also, `Max PDSCH Layers` in LTE/NR tells total #layers for that specific technology (LTE/NR), while `DL Layer Summary` sum is for LTE and NR combined.
- `Cell ID` for LTE/NR and `eNB ID` for LTE are empty in `Radio Neig/Beam` reports.
- `Cell Type` is empty for `LTE Radio Neig`.
- `Enabled256QAM` (in LTE): I'm not sure if different carriers at a time can differ in enabling/disabling this. 
    - For LTE per-carrier, parameter shows up in multiple scopes (unlike NR). 
    - For now, I have selected the scope as per the table definition. 
- `Transfer Blocks` in LTE is the #TBs. 
- LTE/NR `PDSCH_Agg` doesn't have `Band Number`, instead it has `PCell`, `PSCell` band number.
    - Reason: if PCell is "LTE E-UTRA 66", NR `PDSCH_Agg` `Band Number` would show n77, which is incorrect as PSCell is n77, not PCell.
- Added PCell and PSCell bands explicitly in `PUSCH` as there is no `PUSCH_Agg` table. In PDSCH, this was not needed in per-carrier.

## Unresolved Questions:
- What is `DL Layer Summary` if actual #layers are different (which is the case as `Max PDSCH Layers` and `Avg PDSCH Layers` are different).