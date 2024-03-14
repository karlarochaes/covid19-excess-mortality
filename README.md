# COVID-19 Excess Mortality Rate
![image](https://github.com/karlarochaes/covid19-excess-mortality/assets/88100992/91800f41-b158-48ce-963b-f8770fff51e3)

---
## Table of Contents
- [Introduction](#introduction)
- [Tools](#tools)
- [Data Sourcing](#data-sourcing)
- [Data Cleaning](#data-cleaning)
- [Excess Mortality and Normalization](#excess-mortality-and-normalization)
- [Results](#results)
- [Visualization](#visualization)
- [Conclusions and Recommendations](#conclusions-and-recommendations)
- [References](#references)

## Introduction
During the COVID-19 pandemic, deaths attributed to this disease were not accurately recorded for various reasons. To provide a more precise estimate of the number of COVID-19 deaths, excess mortality—defined as the difference between recorded deaths and expected deaths based on historical data—was calculated. This project focused on calculating excess mortality in four Latin American countries: Mexico, Peru, Chile, and Colombia. The resulting numbers were normalized to enable a fair comparison of the results for each country.

## Tools
Google Spreadsheets.

## Data Sourcing
The client provided two tables. The first one was named as **covid_dataset** with 1252 rows and 6 columns:
- `country`: name of the country (Mexico, Peru, Chile, or Colombia).
- `starting date`: starting date of the week.
- `ending date`: final date of the week.
- `week`: number of week of the year.
- `total of reported deaths`: total deaths reported from any cause (not just COVID-19) in the established date range that corresponds to one week.
- `total of reported covid deaths`: total number of reported deaths caused by COVID-19 in the established date range that corresponds to one week.

The second one was named as **population** with only 4 rows and 2 columns:
- `country`: name of the country (Mexico, Peru, Chile, or Colombia).
- `population`: number of people living in the corresponding country.

## Data Cleaning
The original **covid_dataset** table was further divided into four sheets (one for each country). 

## Excess Mortality and Normalization
Excess mortality is calculated with the following formula:

$Excess\ mortality = {Reported\ deaths - Expected\ deaths}$

Reported deaths corresponds to the column `total of reported covid deaths` for a given country. In the other hand, it is necessary to calculate the expected number of deaths. This number is the average deaths per week based on the previous years records. In Google Spreadsheets, you can use the AVERAGEIFS formula with the following syntax: AVERAGEIFS(average_range, criteria_range, criteria). In this case, the average_range is the `total of reported deaths` column and the criteria is the week number (1-52).

```
=AVERAGEIFS(E2:E273, D2:D273, $G$2:$G$54)
```
The calculated values are saved in a column named `excess mortality`.

As all the four countries have different populations, analyzing both the reported deaths and the excess mortality numbers directly would not be a fair comparison. Thus, in order to compare these numbers, a normalization was carried out calculating the rate per 100,000 inhabitants as follows:

$Reported\ deaths\ rate\ per\ 100,000\ inhabitants = {Reported\ deaths \over Population}*100,000$

$Excess\ mortality\ rate\ per\ 100,000\ inhabitants = {Excess\ mortality \over Population}*100,000$

## Results

## Visualization

## Conclusions and Recommendations
- There was a significant gap between the reported number of deaths from COVID-19 and the estimated real numbers, especially for Mexico. The highest peak occurred shortly after New Year's Eve festivities, so these should be dates of especial restrictions in order to avoid contagions and deaths.
- Peru was the country with the highest mortality numbers, with two long-lasting waves of deaths.

## References
Ritchie, H., Ortiz-Ospina, E., Beltekian, D., Mathieu, E., Hasell, J., Macdonald, B., ... & Roser, M. (2020). Coronavirus pandemic (COVID-19). Our world in data. https://ourworldindata.org/excess-mortality-covid
