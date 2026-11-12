# Tidytuesday Data Extraction

This repository has pulled several datasets from TidyTuesday to make them more accessible to introdoctory statistics students.  They will be hosted in Github.  

## Usage

```r
source("extract_tidytuesday.R")

# Export all datasets from Tidytuesday 2018 week 1 to data/
extract_tidytuesday(2018, 1, output_dir = "data")

# Export only named datasets and overwrite existing CSVs
extract_tidytuesday(2018, 1, dataset_names = c("tt_datasets", "tt_summary"), output_dir = "data", overwrite = TRUE)

# Export 10 random single-dataset Tidytuesday weeks across all years
result <- extract_random_single_dataset_tuesdays(10, output_dir = "data", overwrite = TRUE, seed = 123)

# Inspect the metadata returned for README generation
result$tt_summary
result$tt_urls
```

## Extracted datasets

- `datasetname.csv`: Each selected single-dataset week is exported with a file name of the form `datasetname.csv`.

## README dataset descriptions

For the 10 randomly selected single-dataset weeks, use `result$tt_summary` and `result$tt_urls` to generate brief descriptions, including:

- `Year`, `Week`, and `Date`
- Dataset name
- `Title` from the original Tidytuesday data description
- `Source` citation or link source
- `Article` name or the dataset article title
- local CSV path
- number of rows and columns

Example description structure:

- `2024 Week 03` — `polling_places` (1 dataset). Source: `Wikipedia: February 29`. Article: `Polling Places`. CSV: `data/polling_places.csv`.

## Notes

- The script uses `tidytuesdayR::tt_load()` to fetch archive data.
- Only weeks with a single dataset are selected to avoid multi-file joins.
- Existing files are preserved by default; set `overwrite = TRUE` to replace them.

## Disclaimer and citation

This repository uses the `tidytuesdayR` package to access Tidytuesday archive data. The original dataset authors and the Tidytuesday project retain ownership of the published data; this project only exports local CSV copies for analysis and documentation.

Please cite the package and the Tidytuesday project when reusing these datasets:

- `tidytuesdayR` package: https://github.com/rfordatascience/tidytuesdayR
- Tidytuesday project: https://github.com/rfordatascience/tidytuesday

## Example selected datasets

The following datasets were selected using `extract_random_single_dataset_tuesdays(10, output_dir = "data/sample10", overwrite = TRUE, seed = 42)`:

1. `2020 week 44` — `wind-turbine` (Canadian Wind Turbines). Source: `open.canada.ca`. Article: `Canada's National Observer`. CSV: `data/sample10/wind-turbine.csv`. Rows: `6698`, Cols: `15`.
2. `2021 week 02` — `transit_cost` (Transit Cost Project). Source: `TransitCosts.com`. Article: `Transit Costs Case Study`. CSV: `data/sample10/transit_cost.csv`. Rows: `544`, Cols: `20`.
3. `2023 week 21` — `squirrel_data` (Central Park Squirrels). Source: `2018 Central Park Squirrel Census`. Article: `The Squirrel Census`. CSV: `data/sample10/squirrel_data.csv`. Rows: `3023`, Cols: `31`.
4. `2024 week 49` — `A64_traffic` (National Highways Traffic Flow). Source: `WebTRIS Traffic Flow API`. Article: `National Highways`. CSV: `data/sample10/A64_traffic.csv`. Rows: `11904`, Cols: `29`.
5. `2018 week 38` — `allCetaceanData` (Cetaceans Data). Source: `The Pudding`. Article: `The Pudding`. CSV: `data/sample10/allCetaceanData.csv`. Rows: `2194`, Cols: `22`.
6. `2023 week 03` — `artists` (Art history data). Source: `arthistory data package`. Article: `Quantifying Art Historical Narratives`. CSV: `data/sample10/artists.csv`. Rows: `3162`, Cols: `14`.
7. `2020 week 50` — `women` (Women of 2020). Source: `BBC`. Article: `BBC`. CSV: `data/sample10/women.csv`. Rows: `100`, Cols: `6`.
8. `2019 week 27` — `media_franchises` (Media Franchise Revenues). Source: `Wikipedia`. Article: `reddit/dataisbeautiful post`. CSV: `data/sample10/media_franchises.csv`. Rows: `321`, Cols: `7`.
9. `2024 week 37` — `college_admissions` (Economic Diversity and Student Outcomes). Source: `Opportunity Insights: College-Level Data for 139 Selective American Colleges`. Article: `Economic diversity and student outcomes at the University of Texas at Dallas`. CSV: `data/sample10/college_admissions.csv`. Rows: `1946`, Cols: `80`.
10. `2026 week 21` — `energy_cleaned` (Sustainable Energy for All). Source: `SE4ALL Database`. Article: `SE4ALL Database`. CSV: `data/sample10/energy_cleaned.csv`. Rows: `5271`, Cols: `52`.

11. `2018 week 34` — `thanksgiving_meals` (Thanksgiving Dinner or Transgender Day of Remembrance). Source: `fivethirtyeightTDoR`. Article: `fivethirtyeightTDoR`. CSV: `data/sample20/thanksgiving_meals.csv`. Rows: `1058`, Cols: `65`.
12. `2022 week 03` — `chocolate` (Chocolate Bar ratings). Source: `Flavors of Cacao`. Article: `Will Canniford on Kaggle`. CSV: `data/sample20/chocolate.csv`. Rows: `2530`, Cols: `10`.
13. `2020 week 29` — `astronauts` (Astronaut Database). Source: `Corlett, Stavnichuk & Komarova article`. Article: `Corlett, Stavnichuk & Komarova article`. CSV: `data/sample20/astronauts.csv`. Rows: `1277`, Cols: `24`.
14. `2024 week 45` — `democracy_data` (Democracy and Dictatorship). Source: `democracyData R Package`. Article: `Regime types and regime change: A new dataset on democracy, coups, and political institutions`. CSV: `data/sample20/democracy_data.csv`. Rows: `14768`, Cols: `43`.
15. `2021 week 18` — `departures` (CEO Departures). Source: `Gentry et al.`. Article: `investors.com`. CSV: `data/sample20/departures.csv`. Rows: `9423`, Cols: `19`.
16. `2018 week 36` — `medium_datasci` (Medium Article Metadata). Source: `Kaggle.com`. Article: `TidyText package`. CSV: `data/sample20/medium_datasci.csv`. Rows: `78388`, Cols: `21`.
17. `2019 week 45` — `commute` (Bike & Walk Commutes). Source: `ACS`. Article: `ACS`. CSV: `data/sample20/commute.csv`. Rows: `3496`, Cols: `9`.
18. `2024 week 17` — `outer_space_objects` (Objects Launched into Space). Source: `Our World in Data: Annual number of objects launched into space`. Article: `UN Office for Outer Space Affairs: Online index of objects launched into outer space`. CSV: `data/sample20/outer_space_objects.csv`. Rows: `1175`, Cols: `4`.
19. `2021 week 30` — `drought` (US Droughts). Source: `Drought Monitor`. Article: `NYTimes & CNN`. CSV: `data/sample20/drought.csv`. Rows: `325728`, Cols: `10`.
20. `2023 week 12` — `languages` (Programming Languages). Source: `Programming Language DataBase`. Article: `Does every programming language have line comments?`. CSV: `data/sample20/languages.csv`. Rows: `4303`, Cols: `49`.
21. `2019 week 26` — `ufo_sightings` (Global UFO Sightings). Source: `NUFORC`. Article: `Example Plots`. CSV: `data/sample20/ufo_sightings.csv`. Rows: `80332`, Cols: `11`.
22. `2020 week 51` — `ninja_warrior` (Ninja Warrior). Source: `Data.World`. Article: `sasukepedia`. CSV: `data/sample20/ninja_warrior.csv`. Rows: `889`, Cols: `5`.
23. `2026 week 08` — `sfi_grants` (Science Foundation Ireland Grants Commitments). Source: `Science Foundation Ireland Historical Grants Commitments`. Article: `Science Foundation Ireland Historical Grants Commitments`. CSV: `data/sample20/sfi_grants.csv`. Rows: `7269`, Cols: `12`.
24. `2021 week 28` — `holidays` (International Independence Days). Source: `Wikipedia`. Article: `WorldAtlas.com`. CSV: `data/sample20/holidays.csv`. Rows: `216`, Cols: `12`.
25. `2024 week 08` — `isc_grants` (R Consortium ISC Grants). Source: `R Consortium ISC Funded Projects`. Article: `R Consortium ISC Call for Proposals 2024`. CSV: `data/sample20/isc_grants.csv`. Rows: `85`, Cols: `7`.
26. `2025 week 21` — `monsters` (Dungeons and Dragons Monsters (2024)). Source: `System Reference Document v5.2.1`. Article: `You Can Now Publish Your Own Creations Using the New Core Rules`. CSV: `data/sample20/monsters.csv`. Rows: `330`, Cols: `33`.
27. `2019 week 30` — `wildlife_impacts` (Wildlife Strikes). Source: `FAA`. Article: `FAA`. CSV: `data/sample20/wildlife_impacts.csv`. Rows: `56978`, Cols: `21`.
28. `2019 week 44` — `nyc_squirrels` (NYC Squirrel Census). Source: `Squirrel Census`. Article: `CityLab`. CSV: `data/sample20/nyc_squirrels.csv`. Rows: `3023`, Cols: `36`.
29. `2023 week 10` — `numbats` (Numbats in Australia). Source: `Atlas of Living Australia`. Article: `Numbat page at the Atlas of Living Australia`. CSV: `data/sample20/numbats.csv`. Rows: `805`, Cols: `16`.
30. `2022 week 49` — `elevators` (Elevators). Source: `Elevators data`. Article: `Elevators data package and examples`. CSV: `data/sample20/elevators.csv`. Rows: `76088`, Cols: `29`.
