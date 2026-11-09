# Data Dictionary

The processed dataset contains 215 experimental observations and nine columns.

## Columns

| Column | Unit | Origin | Modeling role | Description |
|---|---:|---|---|---|
| `test_id` | – | measured | Metadata only | Experiment number used for traceability. Do not use it as a model input. |
| `temperature_C` | °C | measured | Input | Reactor temperature. |
| `CO2_pct` | vol.% | measured | EDA only | CO₂ percentage in the inlet gas. Redundant when `H2_CO2_ratio` and `Ar_pct` are used. |
| `H2_pct` | vol.% | measured | EDA only | H₂ percentage in the inlet gas. Redundant when `H2_CO2_ratio` and `Ar_pct` are used. |
| `Ar_pct` | vol.% | measured | Input | Argon percentage, representing inlet-gas dilution. |
| `GHSV_h-1` | h⁻¹ | measured | Input | Gas hourly space velocity, representing gas flow relative to catalyst volume and therefore contact time. |
| `flowrate_NmL_min` | NmL/min | measured | EDA only | Total inlet flow at normal conditions. Exclude it from the model because it is almost perfectly correlated with GHSV. |
| `CH4_yield_pct` | % | measured | Target | Experimental methane yield to predict. |
| `H2_CO2_ratio` | mol/mol | derived | Input | Reactive-feed ratio, calculated as `H2_pct / CO2_pct`. |

## Recommended modeling variables


```python
features = [
    "temperature_C",
    "GHSV_h-1",
    "H2_CO2_ratio",
    "Ar_pct",
]

target = "CH4_yield_pct"
```

## Redundancy notes

GHSV and total flow rate contain nearly identical information for this fixed
reactor and catalyst volume. GHSV is retained as the model input because it is
the more physically meaningful measure of contact time.

The inlet composition satisfies approximately:

```text
CO2_pct + H2_pct + Ar_pct = 100
```

Only two composition variables are therefore independent. The combination of
`H2_CO2_ratio` and `Ar_pct` describes reactive-feed stoichiometry and dilution
without including all three constrained gas percentages.
