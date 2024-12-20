# NESO-historical-data-analysis


This readme contains:

1. Information about this dataset
2. A glossary of abbreviations or uncommon terms
3. Details on the meaning of each column
4. Links to each data source used


## Dataset overview:

**Timeframe**: The dataset contains a row for every half hour period from 2009/01/01 00:00 onwards. I have included all data from 2009 - 2023 in this analysis.

**Geography**: The dataset looks at Great Britain (GB) and not Northern Ireland (NI), and it's not completely clear which of the UK's islands are included in the grid system as part of these data. As such, I'll use the term 'GB' to refer the geographical area captured by the data, since it doesn't include NI, but all the areas defined with the legal definition of GB may not be covered.

**Data included**: Each row contains demand estimates, showing how much electricity was produced for GB to consume, estimates on wind & solar energy used, as well as the maximum capacity of GB's wind and solar infrastructure, flow between HDVC interconnectors (substations connecting across the seas around GB to allow for international electricity exchange), and 


## Glossary & Abbreviations: 

**Interconnector**: Structures allowing high voltages to flow between separate electrical grids. As GB is an island, all interconnectors mentioned in this dataset take the form of submarine pipes. GB has one interconnector (the "Moyle" flow) that it shares with NI, which is part of the UK, and several others shared with Ireland, France, and other European countries which allow these nations to buy and sell electricity from one another. This can mutually benefit economies, help with security, and reduce overall electricity production which in turn reduces environmental impacts.

**MW**: MegaWatts - the unit of measurement used to measure all electricity output in this dataset.

**NESO**: "National Energy Systems Operator" - a non-profit public company responsible for controlling the electricity and gas across GB's grids to ensure demand needs are met.


## Columns:

***settlement_date***: date

***settlement_period***: half hourly period number (1 = 00:00, 2 = 00:30... 48 = 23:30)

***nd***: (National Demand). Sum of metered generation, excluding generation required to meet station load, pump storage pumping and interconnector exports. ND is calculated as a sum of generation based on National Grid ESO operationl generation metering. Measured in MW.

***tsd***: (Transmission System Demand). Transmission System Demand is equal to the ND plus the additional generation required to meet station load, pump storage pumping and interconnector exports. Measured in MW

***england_wales_demand***: England and Wales Demand, as ND above but on an England and Wales basis. Measured in MW

***embedded_wind_generation***: This is an estimate of the GB wind generation from wind farms which do not have Transmission System metering installed. These wind farms are embedded in the distribution network and invisible to National Grid ESO. Their effect is to suppress the electricity demand during periods of high wind. The true output of these generators is not known so an estimate is provided based on National Grid ESO’s best model. Measured in MW.

***embedded_wind_capacity***: This is National Grid ESO’s best view of the installed embedded wind capacity in GB. This is based on publicly available information compiled from a variety of sources and is not the definitive view. It is consistent with the generation estimate provided above. Measured in MW.

***embedded_solar_generation***: This is an estimate of the GB solar generation from PV panels. These are embedded in the distribution network and invisible to National Grid ESO. Their effect is to suppress the electricity demand during periods of high radiation. The true output of these generators is not known so an estimate is provided based on National Grid ESO’s best model. Measured in MW.

***embedded_solar_capacity***: As embedded wind capacity above, but for solar generation. Measured in MW.

***non_bm_stor***: (Non-Balancing Mechanism SHort-Term Operating Reserve). For units that are not included in the ND generator definition. This can be in the form of generation or demand reduction. Measured in MW.

***pump_storage_pumping***: The demand due to pumping at hydro pump storage units; the -ve signifies pumping load.

***xxxxx_flow***: Flow on respective interconnector. Negative signifies export power out from GB; positive signifies import power into GB. Measured in MW.

Below are the locations connected to GB via the named interconnector: NB: where there are NaN values in these columns, it means the interconnector was commissioned after the start of the data.

***____ifa***: France ("Interconnexion France-Angleterre")

***____ifa2***: France

***____britned***: Netherlands

***____moyle***: Norther Ireland

***____east_west***: Ireland

***____nemo***: Belgium

***____nsl***: Norway ("North Sea Link"), commissioned in 2021

***____eleclink***: France, commissioned in 2021

***____viking***: Denmark, commissioned in 2024

***scottish_transfer*** an interconnector able to send power quickly between Scotland and England. Since both Scotland and England are included in the nd and tsd data, I am not considering this an international interconnector. Commissioned in 2024.


## Resources: 

### Main data source

**from kaggle, as included here**: https://www.kaggle.com/datasets/albertovidalrod/electricity-consumption-uk-20092022/data

**in its native origin, uncombined with the 2024 file updated daily**: https://www.neso.energy/data-portal/historic-demand-data

### Additional Sources

**list of dates when clocks change**: https://www.metalsmine.com/calendar/400-uk-daylight-saving-time-shift

**population estimates**: https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/datasets/populationestimatesforukenglandandwalesscotlandandnorthernireland (Mid 2011-Mid 2022)

**GeoJSON map of Europe**: https://github.com/leakyMirror/map-of-europe/tree/master

**GeoJSON maps to separate UK countries**:

***England***: https://cartographyvectors.com/map/1321-england-uk

***Wales***: https://cartographyvectors.com/map/1320-wales-uk

***Scotland***: https://cartographyvectors.com/map/1322-scotland-uk

***Northern Ireland***: https://cartographyvectors.com/map/1319-northern-ireland