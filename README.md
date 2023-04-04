# CoronaVirus-Dashboard (Done by Qlik Sense)

![image](https://user-images.githubusercontent.com/24377958/229694560-27108937-3d08-43da-9209-5d6630105487.png)
# Vaccination Dashboard
![image](https://user-images.githubusercontent.com/24377958/229694738-8615adbf-7ed3-4b82-92b6-8c59b19a740b.png)

# Table of Contents

- [Problem Statement](https://github.com/jiang54/CoronaVirus-Dashboard#problem-statement)
- [Data Sourcing](https://github.com/jiang54/CoronaVirus-Dashboard#data-sourcing)
- [Data Preparation](https://github.com/jiang54/CoronaVirus-Dashboard#data-preparation)
- [Data Modeling](https://github.com/jiang54/CoronaVirus-Dashboard#data-modeling)
- [Data Analysis](https://github.com/jiang54/CoronaVirus-Dashboard#data-visualization)
- [Data Visualization](https://https://github.com/jiang54/CoronaVirus-Dashboard#Data-Visualization)
- [Insights](https://github.com/jiang54/CoronaVirus-Dashboard#insights)
- [Data Source](https://github.com/jiang54/CoronaVirus-Dashboard#data-source)


---
# Problem Statement

Despite the ongoing vaccination efforts, the COVID-19 pandemic continues to have a significant impact on the global population. As of March 29, 2023, there have been over 761 million confirmed cases of COVID-19 and more than 6.8 million deaths reported to WHO. The administration of over 13 billion vaccine doses has helped to mitigate the spread of the virus, but there is still a need for effective COVID-19 visualization dashboard to track the progress of the pandemic and inform decision-making at the local, national, and global levels. The dashboard should provide timely and accurate data on COVID-19 cases, deaths, and vaccinations, and should allow users to explore the data through various visualizations and filters.

---

# Data Sourcing

The Dataset used for this analysis was presented by [World Health Organization](https://covid19.who.int/data) and also available at:

- [WHO-COVID-19-global-data](https://github.com/jiang54/CoronaVirus-Dashboard/blob/main/WHO-COVID-19-global-data.csv)
- [WHO-COVID-19-global-table-data](https://github.com/jiang54/CoronaVirus-Dashboard/blob/main/WHO-COVID-19-global-table-data.csv)
- [vaccination-data](https://github.com/jiang54/CoronaVirus-Dashboard/blob/main/vaccination-data.csv)
- [vaccination-metadata](https://github.com/jiang54/CoronaVirus-Dashboard/blob/main/vaccination-metadata.csv)

---

# Data Preparation

Data transformation was done in Excel and the dataset was loaded into Qlik Sense for Visualization.

The call center dataset is given by a table named:

- `WHO-COVID-19-global-data` which has `8 columns and 280134 rows` of observation

Possible KPIs include(but not limited to):
- Overall Cumulatives
- Overall Deaths
- Death Rate
- Vaccine
- 24h or 7 days Newly Reported
- Total Vaccinations
- One Plus Dose
- Fully Vaccinated People



Data Understanding with 4 datasets:

- `WHO-COVID-19-global-data` which has `8 columns and 280134 rows` of observation

The tabulation below shows the `WHO-COVID-19-global-data` table with its column names and their description:
| Column Name    | Description                                                                                                      |
| -------------- | ---------------------------------------------------------------------------------------------------------------- |
| Date_reported  | Date of reporting to WHO                                                                                          |
| Country_code   | ISO Alpha-2 country code                                                                                          |
| Country        | Country, territory, area                                                                                          |
| WHO_region     | WHO regional offices: WHO Member States are grouped into six WHO regions -- Regional Office for Africa (AFRO), Regional Office for the Americas (AMRO), Regional Office for South-East Asia (SEARO), Regional Office for Europe (EURO), Regional Office for the Eastern Mediterranean (EMRO), and Regional Office for the Western Pacific (WPRO). |
| New_cases      | New confirmed cases. Calculated by subtracting previous cumulative case count from current cumulative cases count. |
| Cumulative_cases | Cumulative confirmed cases reported to WHO to date.                                                              |
| New_deaths     | New confirmed deaths. Calculated by subtracting previous cumulative deaths from current cumulative deaths.         |
| Cumulative_deaths | Cumulative confirmed deaths reported to WHO to date.                                                             |

- `WHO-COVID-19-global-table-data` which has `12 columns and 238 rows` of observation

The tabulation below shows the `WHO-COVID-19-global-table-data` table with its column names and their description:
| Column Name                                          | Description                                                                                                      |
| ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Name                                                 | Country, territory, area                                                                                          |
| WHO_region                                           | WHO regional offices: WHO Member States are grouped into six WHO regions -- Regional Office for Africa (AFRO), Regional Office for the Americas (AMRO), Regional Office for South-East Asia (SEARO), Regional Office for Europe (EURO), Regional Office for the Eastern Mediterranean (EMRO), and Regional Office for the Western Pacific (WPRO). |
| Cases - cumulative total                             | Cumulative confirmed cases reported to WHO to date.                                                              |
| Cases - cumulative total per 100000 population       | Cumulative confirmed cases reported to WHO to date per 100,000 population.                                        |
| Cases - newly reported in last 7 days                | New confirmed cases reported in the last 7 days. Calculated by subtracting previous cumulative case count (8 days prior) from current cumulative cases count. |
| Cases - newly reported in last 7 days per 100000 population | New confirmed cases reported in the last 7 days per 100,000 population.                                   |
| Cases - newly reported in last 24 hours              | New confirmed cases reported in the last 24 hours. Calculated by subtracting previous cumulative case count from current cumulative cases count. |
| Deaths - cumulative total                            | Cumulative confirmed deaths reported to WHO to date.                                                             |
| Deaths - cumulative total per 100000 population      | Cumulative confirmed deaths reported to WHO to date per 100,000 population.                                       |
| Deaths - newly reported in last 7 days               | New confirmed deaths reported in the last 7 days. Calculated by subtracting previous cumulative death count (8 days prior) from current cumulative deaths count. |
| Deaths - newly reported in last 7 days per 100000 population | New confirmed deaths reported in the last 7 days per 100,000 population.                                |
| Deaths - newly reported in last 24 hours             | New confirmed deaths reported in the last 24 hours. Calculated by subtracting previous cumulative death count from current cumulative deaths count. |

- `Vaccination data` which has `16 columns and 229 rows` of observation

The tabulation below shows the `Vaccination data` table with its column names and their description:
| Field name                        | Description                                                                                                                                                                                                                                       |
|----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| COUNTRY                          | Country, territory, area                                                                                                                                                                                                                          |
| ISO3                             | ISO Alpha-3 country code                                                                                                                                                                                                                          |
| WHO_REGION                       | WHO regional offices: WHO Member States are grouped into six WHO regions: Regional Office for Africa (AFRO), Regional Office for the Americas (AMRO), Regional Office for South-East Asia (SEARO), Regional Office for Europe (EURO), Regional Office for the Eastern Mediterranean (EMRO), and Regional Office for the Western Pacific (WPRO). |
| DATA_SOURCE                      | Indicates data source: - REPORTING: Data reported by Member States, or sourced from official reports - OWID: Data sourced from Our World in Data: https://ourworldindata.org/covid-vaccinations                                                           |
| DATE_UPDATED                     | Date of last update                                                                                                                                                                                                                               |
| TOTAL_VACCINATIONS               | Cumulative total vaccine doses administered                                                                                                                                                                                                       |
| PERSONS_VACCINATED_1PLUS_DOSE    | Cumulative number of persons vaccinated with at least one dose                                                                                                                                                                                   |
| TOTAL_VACCINATIONS_PER100        | Cumulative total vaccine doses administered per 100 population                                                                                                                                                                                    |
| PERSONS_VACCINATED_1PLUS_DOSE_PER100 | Cumulative persons vaccinated with at least one dose per 100 population                                                                                                                                                                        |
| PERSONS_FULLY_VACCINATED         | Cumulative number of persons fully vaccinated                                                                                                                                                                                                     |
| PERSONS_FULLY_VACCINATED_PER100  | Cumulative number of persons fully vaccinated per 100 population                                                                                                                                                                                  |
| VACCINES_USED                    | Combined short name of vaccine: “Company - Product name” (see below)                                                                                                                                                                              |
| FIRST_VACCINE_DATE               | Date of first vaccinations. Equivalent to start/launch date of the first vaccine administered in a country.                                                                                                                                        |
| NUMBER_VACCINES_TYPES_USED       | Number of vaccine types used per country, territory, area                                                                                                                                                                                         |
| PERSONS_BOOSTER_ADD_DOSE         | Persons received booster or additional dose                                                                                                                                                                                                       |
| PERSONS_BOOSTER_ADD_DOSE_PER100  | Persons received booster or additional dose per 100 population                                                                                                                                                                                    |

- `Vaccination metadata` which has `9 columns and 1074 rows` of observation

The tabulation below shows the `Vaccination metadata` table with its column names and their description:
| Field name        | Description                                                                                                                   |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| ISO3              | ISO Alpha-3 country code                                                                                                      |
| VACCINE_NAME      | Combined short name of vaccine: “Company - Product name” (see below)                                                           |
| PRODUCT_NAME      | Name or label of vaccine product, or type of vaccine (if unnamed).                                                             |
| COMPANY_NAME      | Marketing authorization holder of vaccine product.                                                                             |
| FIRST_VACCINE_DATE| Date of first vaccinations. Equivalent to start/launch date of the first vaccine administered in a country.                    |
| AUTHORIZATION_DATE| Date vaccine product was authorised for use in the country, territory, area.                                                   |
| START_DATE        | Start/launch date of vaccination with vaccine type (excludes vaccinations during clinical trials).                            |
| END_DATE          | End date of vaccine rollout                                                                                                   |
| COMMENT           | Comments related to vaccine rollout                                                                                            |
| DATA_SOURCE       | Indicates data source - REPORTING: Data reported by Member States, or sourced from official reports - OWID: Data sourced from Our World in Data: https://ourworldindata.org/covid-vaccinations |

---

# Data Modeling

After the dataset was cleaned and transformed, it was ready to be modeled.
The fact and dimension have been combined into one table and is shown in the data model below

![image](https://user-images.githubusercontent.com/24377958/229691752-57011922-4db0-421a-b822-004371a0afc2.png)


# Data Analysis
Add Necessary Measures


| Measure                    | Description                                                                                                                        |
| --------------------------| -----------------------------------------------------------------------------------------------------------------------------------|
| Cummulative                | Sum({<Date_reported={"$(=Max({<Country=>} Date(Date_reported, 'YYYY-MM-DD')))"}>} Cumulative_cases)                              |
| Death                      | Sum({<Date_reported={"$(=Max(Date(Date_reported, 'YYYY-MM-DD')))"}>} Cumulative_deaths)                                         |
| Death Rate                 | Sum({<Date_reported={\"\$(=Max(Date(Date_reported, 'YYYY-MM-DD')))"}>} Cumulative_deaths)/Sum({<Date_reported={"$(=Max(Date(Date_reported, 'YYYY-MM-DD')))"}>} Cumulative_cases) |
| 24h Newly Reported        | Sum({<Date_reported={"$(=Max(Date(Date_reported, 'YYYY-MM-DD')))"}>} New_cases)                                                 |
| 24h Dealth                 | Sum({<Date_reported={"$(=Max(Date(Date_reported, 'YYYY-MM-DD')))"}>} New_deaths)                                                |
| 7 d Newly Reported        | Sum({<Date_reported={">=$(=Date(Max(Date_reported)-6, 'YYYY-MM-DD'))"}>} New_cases)                                             |
| 7 d Dealth                 | Sum({<Date_reported={">=$(=Date(Max(Date_reported)-6, 'YYYY-MM-DD'))"}>} New_deaths)                                            |
| Total Vaccinations         | Sum(TOTAL_VACCINATIONS)                                                                                                            |
| Average Vaccinations/100   | AVG(TOTAL_VACCINATIONS_PER100)                                                                                                      |
| One Plus Dose              | Sum(PERSONS_VACCINATED_1PLUS_DOSE)                                                                                                  |
| One Plus Dose Per 100      | avg(PERSONS_VACCINATED_1PLUS_DOSE_PER100)                                                                                            |
| Fully Vaccinated           | Sum(PERSONS_FULLY_VACCINATED)                                                                                                       |
| Fully Vaccinated Per 100   | avg(PERSONS_FULLY_VACCINATED_PER100)                                                                                                |
| Booster Add Dose           | Sum(PERSONS_BOOSTER_ADD_DOSE)                                                                                                       |
| Booster Add Dose Per 100   | avg(PERSONS_BOOSTER_ADD_DOSE_PER100)                                                                                                |
| Unchange Total Vaccinations| Sum({1}TOTAL_VACCINATIONS)                                                                                                         |

# Data Visualization
I show the KPIs, e.g. Cummulative, Death, Death, Rate and so on. Furthermore, I add the filter Pane to help better understanding, and horizontal combo chart, bar chart, map, pie chart to make it more readable.

![image](https://user-images.githubusercontent.com/24377958/229694560-27108937-3d08-43da-9209-5d6630105487.png)
![image](https://user-images.githubusercontent.com/24377958/229694738-8615adbf-7ed3-4b82-92b6-8c59b19a740b.png)

Furthermore, I insert some alternative measures or dimensions to make it more interactive and better representation of data.

![image](https://user-images.githubusercontent.com/24377958/229694902-25765c58-cecb-461a-a0b8-ca7d21fc33fd.png)
![image](https://user-images.githubusercontent.com/24377958/229694982-de4aa47b-9a91-4c32-aff4-bc7f692ad881.png)
![image](https://user-images.githubusercontent.com/24377958/229695025-f363488e-211f-474a-bd50-2c424a14a221.png)
![image](https://user-images.githubusercontent.com/24377958/229695116-27647a48-1f65-42da-8eae-47d28ee8bdc1.png)
![image](https://user-images.githubusercontent.com/24377958/229702780-70c27a7e-f724-4050-86a5-44d47f376fdb.png)


# Insights

- The highest number of comfirmed COVID-19 cases globally occurred in January and Decemeber. These months are the critical period in the spread of virus, possible due to hoilday travel and gatherings and seasonal factors,e.g. winter.
- The high deaths happens in January, December and April. This could be the challenaging in terms of healthcare capability and should take effective measures to deal with it, e.g. public the danger of COVID and the useful measures and ensure the smooth flow of the rescue hotline.
- The death rate is decreasing year by year, and the infection rate is increasing, indicating that the medical system can better face these challenges, and the lethality of the virus is waning.
- The United States, India, and Brazil have higher death rates from COVID-19, while China, Japan, and South Korea have lower death rates. France and Germany fall in the middle. The vaccination rates of these countries also correspond to their death rates, with the United States at 68 per 100 people, China at 87 per 100 people, and Germany at 76. This suggests that vaccination is an effective means of reducing the death rate from COVID-19 from start to end.
# Data Source

Virtual Case Experience: 

[WHO COVID-19](https://covid19.who.int/data)
