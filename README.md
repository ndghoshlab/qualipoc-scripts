# qualipoc-scripts
Scripts and documentation for QualiPoc data processing.

# Raw Data:
- `DL/UL Modulation`, `Avg Layers` removed from `Radio` tables.
    - `DL/UL Modulation` is not the exact modulation, rather the most used modulation in `PDSCH/PUSCH`. More detailed KPIs pertaining to modulation are added onto the `PDSCH/PUSCH` tables.
    - `Avg Layers` only shows MCG group average; SCG has a separate KPI.
        - Addded `DL/UL Layer Summary` instead for comprehensive layer counts across MCG & SCG.
        - **Note:** Layer summary values (e.g., "2 Layers MCG, 4 Layers SCG") are upper bounds. Actual layer usage may be lower (minimum 1 layer).
- 