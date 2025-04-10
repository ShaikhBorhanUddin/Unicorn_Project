# Q1️: Find the Top 5 Most Valuable Companies
## Solution
```SQL
SELECT company, valuation 
FROM funding 
JOIN companies ON funding.company_id = companies.company_id
ORDER BY valuation DESC
LIMIT 5;
```
## Output
|company     |valuation  |
|------------|-----------|
|Bytedance   |180000000000|
|SpaceX      |100000000000|
|SHEIN       |100000000000|
|Stripe      |95000000000|
|Klarna      |46000000000|
## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%201.png?raw=true)
# Q2️: Count the Number of Unicorns per Continent
## Solution
```SQL
SELECT continent, COUNT(*) AS unicorn_count
FROM companies
GROUP BY continent
ORDER BY unicorn_count DESC;
```
## Output
|continent    |unicorn_count|
|-------------|-------------|
|North America|589          |
|Asia         |310          |
|Europe       |143          |
|South America|21           |
|Oceania      |8            |
|Africa       |3            |
## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%202.png?raw=true)
# Q3️: Find Companies Founded Before 2000 That Became Unicorns After 2015
## Solution
```SQL
SELECT c.company, d.year_founded, d.date_joined
FROM dates d
JOIN companies c ON d.company_id = c.company_id
WHERE d.year_founded < 2000 AND d.date_joined >= '2015-01-01';
```
## Output
|company                         |year_founded|date_joined|
|--------------------------------|------------|-----------|
|Otto Bock HealthCare            |1919        |2017-06-24 |
|Numbrs                          |1999        |2019-08-22 |
|YH Global                       |1997        |2017-09-21 |
|Howden Group Holdings           |1994        |2020-09-29 |
|Caris Life Sciences             |1996        |2021-05-12 |
|OVH                             |1999        |2016-08-15 |
|Radius Payment Solutions        |1990        |2017-11-27 |
|Thirty Madison                  |1993        |2021-06-02 |
|National Stock Exchange of India|1998        |2020-07-01 |
|Easyhome                        |1999        |2018-02-12 |
|iTutorGroup                     |1998        |2015-11-18 |
|Starburst                       |1999        |2021-01-06 |
|Five Star Business Finance      |1984        |2021-03-26 |
|Promasidor Holdings             |1979        |2016-11-08 |
|Weilong Foods                   |1999        |2021-05-08 |
|Movile                          |1998        |2018-07-12 |
|Global Switch                   |1998        |2016-12-22 |
|InSightec                       |1999        |2020-03-06 |
|BGL Group                       |1992        |2017-11-24 |
|Epic Games                      |1991        |2018-10-26 |
|Pine Labs                       |1998        |2020-01-24 |
|Carzone                         |1995        |2019-03-01 |
|Workhuman                       |1999        |2020-06-23 |

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%203.png?raw=true)
--4️ Find the Average Valuation of Companies by Industry

SELECT i.industry, ROUND(AVG(f.valuation), 2) AS avg_valuation
FROM funding f
JOIN industries i ON f.company_id = i.company_id
GROUP BY i.industry
ORDER BY avg_valuation DESC;

--5️ Find Companies with the Most Selective Investors

SELECT c.company, LENGTH(f.selective_investors) - LENGTH(REPLACE(f.selective_investors, ',', '')) + 1 AS investor_count
FROM funding f
JOIN companies c ON f.company_id = c.company_id
ORDER BY investor_count DESC
LIMIT 15;

--6️ Find top 10 Companies with the Highest Funding-to-Valuation Ratio

SELECT c.company, f.funding, f.valuation, ROUND((f.funding::DECIMAL / f.valuation) * 100, 2) AS funding_ratio
FROM funding f
JOIN companies c ON f.company_id = c.company_id
WHERE f.valuation > 0  -- Avoid division by zero
ORDER BY funding_ratio DESC
LIMIT 10;

--7️ Find the Most Common Industry by Continent

SELECT c.continent, i.industry, COUNT(*) AS industry_count
FROM industries i
JOIN companies c ON i.company_id = c.company_id
GROUP BY c.continent, i.industry
ORDER BY c.continent, industry_count DESC;

--8️ Find Companies That Raised More Than Industry Average

SELECT c.company, f.funding, i.industry
FROM funding f
JOIN industries i ON f.company_id = i.company_id
JOIN companies c ON f.company_id = c.company_id
WHERE f.funding > (
    SELECT AVG(f2.funding) FROM funding f2 
    JOIN industries i2 ON f2.company_id = i2.company_id 
    WHERE i2.industry = i.industry
)
ORDER BY f.funding DESC;

--9️ Find the Fastest-Growing Unicorns (Shortest Time from Founding to Unicorn Status)

SELECT c.company, d.year_founded, d.date_joined, 
       (d.date_joined - (d.year_founded || '-01-01')::DATE) AS days_to_unicorn
FROM dates d
JOIN companies c ON d.company_id = c.company_id
ORDER BY days_to_unicorn ASC
LIMIT 10;

--10 Find the Oldest Unicorns (Companies Founded the Longest Ago but Still Unicorns)

SELECT c.company, d.year_founded, f.valuation
FROM dates d
JOIN funding f ON d.company_id = f.company_id
JOIN companies c ON d.company_id = c.company_id
ORDER BY d.year_founded ASC
LIMIT 10;

--11 Average Time (in Years) from Founding to Unicorn Status by Continent

SELECT c.continent,
       ROUND(AVG(EXTRACT(YEAR FROM d.date_joined) - d.year_founded), 2) AS avg_years_to_unicorn
FROM companies c
JOIN dates d ON c.company_id = d.company_id
GROUP BY c.continent
ORDER BY avg_years_to_unicorn;

--12 Most Common Founding Years Among Unicorns

SELECT year_founded, COUNT(*) AS company_count
FROM dates
GROUP BY year_founded
ORDER BY company_count DESC
LIMIT 10;

--13 Companies Founded Before 2010 but Valued Over $10 Billion

SELECT c.company, d.year_founded, f.valuation
FROM companies c
JOIN dates d ON c.company_id = d.company_id
JOIN funding f ON c.company_id = f.company_id
WHERE d.year_founded < 2010 AND f.valuation > 10000000000
ORDER BY f.valuation DESC;

--14 Continent with the Highest Total Unicorn Valuation

SELECT c.continent, SUM(f.valuation) AS total_valuation
FROM companies c
JOIN funding f ON c.company_id = f.company_id
GROUP BY c.continent
ORDER BY total_valuation DESC
LIMIT 1;

--15 Top 3 Industries with the Highest Average Funding

SELECT i.industry, ROUND(AVG(f.funding), 2) AS avg_funding
FROM industries i
JOIN funding f ON i.company_id = f.company_id
GROUP BY i.industry
ORDER BY avg_funding DESC
LIMIT 3;

--16 Industry Diversity: Number of Different Industries Per Country

SELECT c.country, COUNT(DISTINCT i.industry) AS industry_count
FROM companies c
JOIN industries i ON c.company_id = i.company_id
GROUP BY c.country
ORDER BY industry_count DESC;

--17 Countries with the Highest Number of Unicorns Founded After 2022

SELECT c.country, COUNT(*) AS unicorn_count
FROM companies c
JOIN dates d ON c.company_id = d.company_id
WHERE d.date_joined >= '2022-01-01'
GROUP BY c.country
ORDER BY unicorn_count DESC;
