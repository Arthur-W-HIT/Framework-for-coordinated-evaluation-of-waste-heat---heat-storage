# Waste heat and thermal storage data for combined heat and power district heating

This dataset accompanies *An optimization-based framework for coordinated evaluation of waste heat and thermal storage integration in combined heat and power district heating* by Zhonghao Wang, Fuxiang Dong, Yongcheng Zhou, Ruiyang Jiang, Jinfu Liu and Daren Yu. It contains the processed inputs and summary results supporting the main comparisons in the article. Additional simulation records are available from the corresponding authors upon reasonable request.

## Study cases and time

N denotes the existing district heating system, W adds direct waste-heat recovery, and WS adds recovery and a thermal storage tank. A and B refer to the trunk and building-group-1 station, respectively. R, S and X refer to return-water heating, supply-water heating and the return-to-supply connection. Figure and table numbers below follow the article and its supplementary material.

Elapsed time starts at 00:00 on 1 March 2024, Brussels local time. The 120 hourly inputs end at 00:00 on 6 March. The electricity and weather series are aligned on UTC timestamps. The original calendar dates of the industrial batch profile are unspecified. Its relative sequence is aligned to the study period. An interval midpoint labels the value for that interval, whereas the tank inventory and room temperatures are evaluated at grid times.

## Data files

| File | Contents and location in the article |
|---|---|
| inputs/industrial_waste_heat.csv | Hourly reconstructed industrial resource temperature and cooling power, with the study scaling and temperature cap. Fig. 3. |
| inputs/electricity_and_weather.csv | Hourly day-ahead prices, wind and solar generation, electricity demand, residual load and outdoor temperature. Fig. S2. |
| inputs/case_parameters.csv | Network, exchanger, tank, cost and service parameters. Table 2 and Supplementary Section S3. |
| inputs/evaluation_tasks.csv | Cases, matched service requirements and time windows. Table 3. |
| results/connection_configurations.csv | Heat, electricity and economic results for the 12 five-day configurations. Fig. 4. |
| results/operating_cost_components.csv | A-R fuel, electricity, carbon, recovery, pumping and fixed-cost contributions. Fig. 5 and Table S1. |
| results/additional_storage.csv | Incremental storage benefit and annualized fixed-cost limit at each connection. Table 4. |
| results/five_day_heat_balance.csv | Recovered heat, network injection, plant heat, system losses and stored-energy changes. Table 5. |
| results/storage_time_shifting.csv | Generation and electricity revenue for the identical-equipment comparison. Fig. 7 and the revenue decomposition. |
| results/regulation_performance.csv | Sustained output and operating costs under a common regulation requirement. Table 6. |

CSV column names give units. A suffix of _MWh or _kWh denotes energy, and _MW or _kW denotes power. EUR denotes euros. In the economic tables, costs and savings are listed in their named columns and subtracted or added to obtain net benefit. Heat-balance inventory columns give end-minus-start changes. The annualized cost limits use 180 heating days to allocate fixed costs. The series retain the saved numerical precision, while the article rounds its reported values.

## Input sources and processing

- The industrial series was digitized for this study from Fig. 4 of de Boer, Smeding and Biesheuvel (2017), *Waste Heat Recovery in Industrial Batch Processes*, ECN-M--17-008. The original cooling power was scaled by 0.015 and the exchanger inlet temperature was capped at 90 °C under the study's recirculation rule. Reading bounds reflect chart resolution. [Source report](https://publications.tno.nl/publication/34631725/1M36oD/m17008.pdf)
- Electricity demand, wind and solar series come from Energy-Charts / Fraunhofer ISE under CC BY 4.0. Wind includes onshore and offshore generation. The study uses hourly means of the power inputs and calculates residual load by subtracting wind and solar generation from total demand. [Provider dataset](https://api.energy-charts.info/v2/public_power?country=be&start=2024-03-01&end=2024-03-05)
- Day-ahead prices for bidding zone BE are from Bundesnetzagentur | SMARD.de via Energy-Charts / Fraunhofer ISE. The provider labels the linked series CC BY 4.0. The values are reported in EUR/MWh and aligned to the other study inputs by timestamp. [Provider dataset](https://api.energy-charts.info/v2/price?bzn=BE&start=2024-03-01&end=2024-03-05)
- The hourly outdoor temperatures use ERA5-Land data via Open-Meteo, at approximately 50.98° N and 5.50° E. Open-Meteo supplies these data under CC BY 4.0. [ERA5-Land description](https://doi.org/10.5194/essd-13-4349-2021), [Open-Meteo Historical Weather API](https://open-meteo.com/en/docs/historical-weather-api), [Open-Meteo data license](https://open-meteo.com/)
- Published parameter sources are described in the supplementary material, including the MODESTO network case. [MODESTO release source](https://github.com/energyville/modesto/tree/79d4af558cf4d9ebe80d32fd2be8988101f8eb4f)

The [Creative Commons Attribution 4.0 license](https://creativecommons.org/licenses/by/4.0/) applies to the third-party columns identified above under their stated provider terms. The simulation outputs and processed series support the numerical comparisons in the article. Consult the article and its supplementary material for the model equations and operating constraints.

## Citation and file integrity

Use the attribution in CITATION.cff for this dataset and cite the source datasets when reusing their inputs. SHA256SUMS.txt lists checksums for the files in this release.
