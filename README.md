1. LIST OUT THE AVERAGE DEATHS OF ANY 10 COUNTRIES DURING COVID-19.
```SQL
SELECT
   Avg (deaths_total) AS averagedeath,
  countries_and_territories,
FROM
  `bigquery-public-data.covid19_covidtracking.summary`,
  `bigquery-public-data.covid19_ecdc.covid_19_geographic_distribution_worldwide`
GROUP BY
  2
  limit 10
``` 
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/fbc9ed4e-e2a4-4a3e-9c84-5f7a6769547b)

2. WHAT IS THE MINIMUM AND MAXIMUM NUMBER OF CONFIRMED CASES FOR ALL THE COUNTRIES?
```SQL
SELECT
   min(confirmed_cases) as minimum,
   max (confirmed_cases) as maximum,
  countries_and_territories
FROM
  `bigquery-public-data.covid19_covidtracking.summary`,
  `bigquery-public-data.covid19_ecdc.covid_19_geographic_distribution_worldwide`
  GROUP BY 3
```
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/4017fbfc-b8a6-40d0-aa65-7bd89efdfcc6)

3. WHAT IS THE TOTAL DAILY DEATHS OF THE COUNTRY “AFGHANISTAN”?
```SQL
SELECT
  sum(daily_deaths) as `daily deaths of afganistan`
 FROM
   `bigquery-public-data.covid19_ecdc.covid_19_geographic_distribution_worldwide`
 WHERE countries_and_territories = "Afghanistan"
```
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/2e0b0638-0eb3-4945-a4b8-0a4175c0ab0c)

4. WHAT IS THE TOTAL POPULATION AS OF 2019 IN TAIWAN?
```SQL
SELECT
  pop_data_2019 as `population 2019`
FROM
  `bigquery-public-data.covid19_ecdc.covid_19_geographic_distribution_worldwide`
where countries_and_territories = "Taiwan"
```
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/c2757a9a-1c56-4385-922c-3e2d84fb0c50)

5. ILLUSTRATE THE NUMBER OF DEATHS BY YEAR DURING COVID-19.
```SQL
SELECT
  year,
  count(deaths) as deaths
FROM
  `bigquery-public-data.covid19_ecdc.covid_19_geographic_distribution_worldwide`
  group by year
```
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/337bf0d2-39f7-45af-a0f3-b90be2901670)

6. LIST OUT THE AVERAGE OF CONFIRMED CASES YEAR WISE FOR ALL THE COUNTRIES AS A WHOLE.
```SQL
SELECT
  year, avg(confirmed_cases) as `confirmed cases`
FROM
  `bigquery-public-data.covid19_ecdc.covid_19_geographic_distribution_worldwide`
  group by 1
```
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/040bcc19-58b5-4242-ad49-d7af4befb8ac)

7. WHAT IS THE TOTAL SUM OF NEGATIVE CASES INCREASE THAT HAS BEEN SEEN FROM 2nd MARCH,2021 to 7th MARCH, 2021 DURING COVID-19?
```SQL
WITH
  Covid19 AS 
  (
  SELECT
    cases_negative_increase,
    date
  FROM
    `bigquery-public-data.covid19_covidtracking.summary`
  WHERE
    date BETWEEN "2021-03-02"
    AND "2021-03-07")
SELECT
  SUM(cases_negative_increase) as `cases negative`
  from covid19
```
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/b26e2641-bb14-4f7b-9847-f72c024ee414)

8. HOW MANY HOSPITALISATIONS OF PEOPLE HAVE INCREASED DUE TO COVID 19 IN THE COUNTRY “CHAD” BETWEEN 1st OCT,2020 to 31st OCT, 2020?
```SQL
SELECT
  s.date,
  s.hospitalizations_increase 
FROM
  `bigquery-public-data.covid19_ecdc.covid_19_geographic_distribution_worldwide`c 
LEFT JOIN
  `bigquery-public-data.covid19_covidtracking.summary` s 
ON
  c.date=s.date 
WHERE
  c.date BETWEEN "2020-10-01"
  AND "2020-10-31"
  AND c.countries_and_territories = "Chad"
```
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/08311a4a-aabe-496b-86d4-8e07763c688c)
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/e7049258-b1a7-482f-8e2d-bff565d9221a)
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/8ba732eb-822b-487a-bf51-e5eee1f9127a)

9. WHAT IS THE TOATL NUMBER OF VENTILATORS USED IN INDIA DURING COVID19?
```SQL
With covid19 as
(SELECT c.date, c.countries_and_territories, s.ventilator_total
FROM `bigquery-public-data.covid19_covidtracking.summary` s
left join `bigquery-public-data.covid19_ecdc.covid_19_geographic_distribution_worldwide` c
on s.date=c.date)
Select sum(ventilator_total) as `Total ventilator` from covid19
where countries_and_territories="India" 
```
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/0282a7bf-ed00-4a13-a4e1-b91254433a59)

10. GIVE US THE AVEARAGE NO.OF INCREASE IN TOTAL TESTS IN ANY 10 COUNTRIES DURING COVID 19 FOR A OVERVIEW?
```SQL
SELECT
  g.countries_and_territories,
  avg(s.tests_increase) as `test increase`
FROM
  `bigquery-public-data.covid19_ecdc.covid_19_geographic_distribution_worldwide` g
  Inner join `bigquery-public-data.covid19_covidtracking.summary` s
  on g.date=s.date
  group by g.countries_and_territories 
  limit 10
```
![image](https://github.com/SANMATHI-1777/SANMATHI-1777/assets/158753766/bf17d8ed-791f-4c2c-b76b-6b0d13e3872d)













