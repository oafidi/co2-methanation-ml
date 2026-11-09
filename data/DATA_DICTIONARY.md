# Data Dictionary


| Column | Unit | Type | Description |
|---|---:|---|---|
| `test_id` | – | measured | Experiment number |
| `temperature_C` | °C | measured | Reactor temperature |
| `CO2_pct` | vol.% | measured | CO₂ percentage in the inlet gas |
| `H2_pct` | vol.% | measured | H₂ percentage in the inlet gas |
| `Ar_pct` | vol.% | measured | Argon percentage in the inlet gas |
| `GHSV_h-1` | h⁻¹ | measured | Gas hourly space velocity |
| `flowrate_NmL_min` | NmL/min | measured | Total inlet flow rate at normal conditions |
| `CH4_yield_pct` | % | measured target | Experimental methane yield |
| `H2_CO2_ratio` | mol/mol | derived | `H2_pct / CO2_pct` |
| `CO2_flow_NmL_min` | NmL/min | derived | Total flow multiplied by the CO₂ fraction |
| `CO2_partial_pressure_bar` | bar | derived | 3 bar multiplied by the CO₂ fraction |
| `H2_flow_NmL_min` | NmL/min | derived | Total flow multiplied by the H₂ fraction |
| `H2_partial_pressure_bar` | bar | derived | 3 bar multiplied by the H₂ fraction |
| `Ar_flow_NmL_min` | NmL/min | derived | Total flow multiplied by the Ar fraction |
| `Ar_partial_pressure_bar` | bar | derived | 3 bar multiplied by the Ar fraction |
| `pressure_bar` | bar absolute | experimental constant | Total pressure, fixed at 3 bar in the study |
