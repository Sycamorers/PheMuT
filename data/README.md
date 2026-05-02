# Processed Tabular Data

This directory contains processed tabular data for the GNV strawberry yield
forecasting experiments. Raw RGB imagery, processed image frames, model weights,
weather embeddings, and experiment outputs are not versioned in this repository.

## Included Seasons

- `2324_GNV_processed/`: 2023-2024 season, with observation dates from
  `240108` through `240227` and weather records from January 1, 2024 through
  April 30, 2024.
- `2425_GNV_processed/`: 2024-2025 season, with observation dates from
  `250107` through `250305` and weather records from January 1, 2025 through
  June 30, 2025.

## File Layout

```
data/
  2324_GNV_processed/
    2324_weather.csv
    240108/
      consolidated_summary_with_yield.csv
    ...
    counting_yield/
      240108.csv
      ...
  2425_GNV_processed/
    2425_weather.csv
    250107/
      consolidated_summary_with_yield.csv
    ...
    counting_yield/
      250107.csv
      ...
```

## File Descriptions

- `*_weather.csv`: 15-minute weather observations from station `250`. Columns
  include timestamp, soil temperature, air temperature at multiple heights,
  relative humidity, dew point, rainfall, wind speed, wind direction, and solar
  radiation. Units are included in the column names.
- `<YYMMDD>/consolidated_summary_with_yield.csv`: per-date processed feature
  tables. Rows include flower and fruit stage counts
  (`strawberry_flower`, `strawberry_green`, `strawberry_white`,
  `strawberry_pink`, `strawberry_red`), harvested yield in grams, and canopy
  geometry summaries (`Area`, `Depth`, `Volume`). Columns are plot identifiers
  such as `B11` through `B55` and `M11` through `M55`.
- `counting_yield/<YYMMDD>.csv`: manual counting and yield tables for the same
  dates. Rows use abbreviated phenology labels: `FL` for flower, `G` for green,
  `W` for white, `P` for pink, `R` for red, and `Yield (g)` for harvested
  yield in grams.

## Notes

- Date folder names use `YYMMDD` format.
- The 2024-2025 consolidated files use lowercase plot labels in the header;
  they correspond to the same plot naming scheme as the uppercase labels.
- Blank rows in some counting files are export artifacts and should be ignored
  during analysis.
