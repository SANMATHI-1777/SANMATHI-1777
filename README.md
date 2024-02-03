1. LIST OUT THE AVERAGE DEATHS OF ANY 10 COUNTRIES DURING COVID-19.
```SQL
SELECT
Avg (deaths_total) AS average death, countries_and_territories,
FROM `bigquery-public-data.covid19_covidtracking.summary`,`bigquery-public-data.covid19_ecdc.covid_19_geographic_distribution_worldwide`
GROUP BY 2
limit 10
``` 
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/fbc9ed4e-e2a4-4a3e-9c84-5f7a6769547b)

