# Airline Data Analysis: United Airlines vs. Competitors

This project analyzes U.S. domestic flight performance data to benchmark **United Airlines (UA)** against other major carriers, with a focus on flight volume, route overlap, and delay patterns. The analysis combines a Python/Jupyter notebook for exploratory data analysis with an interactive Tableau dashboard for deeper visual drill-down.

## Contents

| File | Description |
|---|---|
| `Airline_Data_Analysis.ipynb` | Jupyter/Colab notebook that loads the flight dataset, computes per-airline metrics, and compares United (UA) against American Airlines (AA). |
| `United_Airline_Analysis.twbx` | Packaged Tableau workbook with interactive worksheets exploring United's delay patterns in detail. |

## Notebook: `Airline_Data_Analysis.ipynb`

Built to run in Google Colab (reads data from Google Drive). It:

- Loads a flight-level dataset (`Total_Data.csv`) containing carrier, origin/destination, distance, and departure delay fields.
- Constructs a `ROUTE` identifier from origin and destination airport IDs.
- Aggregates per-carrier metrics: total flights, average distance, average departure delay, share of flights delayed 15+ minutes (`DEP_DEL15` rate), and number of unique origin airports.
- Calculates route overlap between United and every other carrier (shared routes with UA).
- Prints a formatted comparison table of all carriers against a UA baseline, and highlights the direct comparison between **UA and AA**.

**Key finding from the notebook:** UA and AA are close competitors — both serve around 119 unique origin airports, with similar flight volumes (UA ~1,193 vs. AA ~993 in the sampled comparison) and comparable route footprints.

### Requirements
- Python 3
- `pandas`, `numpy`
- Data file `Total_Data.csv` (not included in this repo; update the file path in the notebook to point to your own copy of the dataset)

## Tableau Workbook: `United_Airline_Analysis.twbx`

An interactive Tableau workbook focused specifically on United Airlines delay behavior, built from `Final_Airline_Data.csv`. It includes four worksheets:

- **UA: Delay Rate by Time of Day** — how UA's delay rate varies across departure time blocks.
- **UA: Delay by Cause** — breakdown of delay minutes by cause (carrier, weather, NAS, security, late aircraft).
- **UA: Delayed Flights** — detail view of individual delayed flights.
- **UA: Heatmap** — heatmap visualization of delay patterns (e.g., by route or time).

The workbook draws on fields such as `DEP_DELAY`, `ARR_DELAY`, `TAXI_OUT`/`TAXI_IN`, `AIR_TIME`, `DISTANCE`, and the individual delay-cause columns (`CARRIER_DELAY`, `WEATHER_DELAY`, `NAS_DELAY`, `SECURITY_DELAY`, `LATE_AIRCRAFT_DELAY`).

To view it, open `United_Airline_Analysis.twbx` in [Tableau Desktop](https://www.tableau.com/products/desktop) or [Tableau Public](https://public.tableau.com/).

## Data

Both files reference U.S. domestic on-time performance flight data (fields consistent with the BTS Airline On-Time Performance dataset). The raw CSVs are not included in this repository — supply your own copy and update the file paths in the notebook / re-point the Tableau data connection as needed.

## Summary

Together, the notebook and dashboard tell a two-part story: the notebook establishes that UA and AA are comparably sized competitors on similar route networks, while the Tableau workbook zooms in on *when*, *why*, and *how often* United's flights are delayed.
