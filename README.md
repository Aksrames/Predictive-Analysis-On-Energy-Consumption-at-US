# Predictive-Analysis-On-Energy-Consumption-at-US

This is the final project for the course Machine Learning in Public Policy (UAPP 667) at the University of Delaware. The course instructor is Prof. Gregory Dobler. The team members associated with this project are Prosper Kosi Anyidoho, Stephanie Zmina and Akshaya Ramesh who are all students at UD.

# PROBLEM STATEMENT

Energy consumption is of interest for short term planning of energy production, meeting demands of customers, transitioning to renewable sources, and ultimately breaking the fossil fuel feedback loop that is directly causing global climate change.

Therefore, our group's goal is to investigate the factors that contribute to the magnitude of US energy consumption. A predictive model based on a few important factors could elucidate how energy consumption is predicted to change into the future.

# DATA DESCRIPTION
Data utilized in this project is in four components— energy consumption, temperature, population and business. All four datasets are publicly available.

The energy consumption data was obtained from the Kaggle platform. It consist of hourly energy consumption data measured in megawatts for zones under the Pensylvannia, New Jersey, and Maryland Power Pool (PJM). We focused on four states where the energy data coverage matched the state boundaries fairly well (some of the data covered only a small portion of the state). The four chosen states are Illinois, Kentucky, Ohio, and Virginia, using the power providers ComEd / Northern Illinois (NI), East Kentucky Power Coporation (EKPC), American Electric Power (AEP)/ Dayton Power and Light (DAYTON), and Dominion energy (DOM), respectively. It is important to note that the date ranges of the energy providers data vary, but overall the time range for all data spanned from 2004 to 2018.

Temperature data was obtained from NOAA's Climate Divisional Database nCLIMDIV. This database is based on the Global Historical Climatology Network GHCN, which includes records from over 100,000 stations all over the world. Data collected at these stations includes daily temperature min/ max, and precipitation levels. Some of the stations have been active since the 1800s (over 175 years of data). The NOAA Climate Divisional Database interpolates the records from GHCN to a 5km grid, giving a full coverage map of environmental data. These data are then aggregated at different divisional levels - state, regional, and national. For this project, the data file that we are using has the average monthly temperature for each state, from 1895 - 2021.

Population data was taken from US Census State and County Population Estimate 2000 - 2019 at yearly resolution. The columns in the data set are State_name, State_FIPS (Federal Information Processing Standards), and pop_2006 - pop_2019 ( population from 2006 - 2019). State data was selected based on FIPS code ((Illinois 17, Kentucky 21, Ohio 39, Virginia 51).

The business data source is US Census - Statistics of US Businesses (SUSB) Annual Datasets by Establishment Industry. These datasets contain annual data about business establishments separated by state. The SUSB database contains consistent files from 2007 - 2017. We attempted to use earlier years in SUSB or supplement this datasource with another Census data source, however the establishments per state were vastly different from the 2007 - 2017 SUSB dataset, so it seemed they were measured/calculated differently and it was not appropriate to stitch the two sets together. Therefore we are solely working with the SUSB 2007 - 2017 data. The columns we are interested in are: FIPS state code, NAICS industry code, and number of establishments. We selected rows from each database that corresponded to the study states, based on their FIPS code (Illinois 17, Kentucky 21, Ohio 39, Virginia 51). The NAICS codes were 6-digit, which indicate quite specific subsections of businesses. We decided to aggregate establishments based on the first 2-digit codes, which correspond to a high level industry classification.

# DATA LIMITATIONS

The Kaggle energy dataset limited our spatial scope in terms of what states were available, which is why we were only able to extract the four chosen states for the model. Additionally the energy data was limited in time scope for each of the states. The earliest (2004) and latest (2018) years in the dataset did not have data for the entire year, and the Kentucky dataset only had 2013-2018. We were careful to match the factor data only to months which had the target energy data.

Furthermore, the population and business data are reported yearly by the US Census, but we wanted to match the input variables to the energy data on a more granual time scale in order to include the affects of seasonal variability. Therefore, those data had to be interpolated to monthly time scale before inputting to the model.

The business data also had to be extrapolated to earlier and later years because the continuous dataset was limited from 2007 to 2017 when the desired time series was 2004 - 2018.

