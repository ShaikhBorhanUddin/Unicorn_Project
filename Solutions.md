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
# Q4️: Find the Average Valuation of Companies by Industry
## Solution
```SQL
SELECT i.industry, ROUND(AVG(f.valuation), 2) AS avg_valuation
FROM funding f
JOIN industries i ON f.company_id = i.company_id
GROUP BY i.industry
ORDER BY avg_valuation DESC;
```
## Output
|industry                           |avg_valuation|
|-----------------------------------|-------------|
|Artificial intelligence            |4488095238.10|
|Other                              |4344827586.21|
|Consumer & retail                  |4240000000.00|
|Fintech                            |3937500000.00|
|E-commerce & direct-to-consumer    |3837837837.84|
|Edtech                             |3571428571.43|
|Data management & analytics        |3317073170.73|
|Travel                             |3285714285.71|
|Auto & transportation              |3193548387.10|
|Supply chain, logistics, & delivery|3105263157.89|
|Hardware                           |2911764705.88|
|Internet software & services       |2902439024.39|
|Health                             |2675675675.68|
|Cybersecurity                      |2580000000.00|
|Mobile & telecommunications        |2342105263.16|

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%204.png?raw=true)
# Q5️: Find Companies with the Most Selective Investors
## Solution
```SQL
SELECT c.company, LENGTH(f.selective_investors) - LENGTH(REPLACE(f.selective_investors, ',', '')) + 1 AS investor_count
FROM funding f
JOIN companies c ON f.company_id = c.company_id
ORDER BY investor_count DESC
LIMIT 15;
```
## Output
|company   |investor_count|
|----------|--------------|
|Yixia     |4             |
|Skydio    |4             |
|Lightricks|4             |
|Niantic   |4             |
|Bytedance |4             |
|SVOLT     |4             |
|Evidation |4             |
|Rappi     |4             |
|eDaili    |3             |
|Darwinbox |3             |
|Mamaearth |3             |
|MobileCoin|3             |
|Clara     |3             |
|CoinDCX   |3             |
|Splashtop |3             |

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%205.png?raw=true)
# Q6️: Find top 10 Companies with the Highest Funding-to-Valuation Ratio
## Solution
```SQL
SELECT c.company, f.funding, f.valuation, ROUND((f.funding::DECIMAL / f.valuation) * 100, 2) AS funding_ratio
FROM funding f
JOIN companies c ON f.company_id = c.company_id
WHERE f.valuation > 0  -- Avoid division by zero
ORDER BY funding_ratio DESC
LIMIT 10;
```
## Output
|company        |funding   |valuation |funding_ratio|
|---------------|----------|----------|-------------|
|Snapdeal       |2000000000|1000000000|200.00       |
|REEF Technology|2000000000|1000000000|200.00       |
|Hello TransTech|2000000000|1000000000|200.00       |
|Fair           |2000000000|1000000000|200.00       |
|Magic Leap     |3000000000|2000000000|150.00       |
|Momenta        |1000000000|1000000000|100.00       |
|SumUp          |1000000000|1000000000|100.00       |
|OVH            |1000000000|1000000000|100.00       |
|SaltPay        |1000000000|1000000000|100.00       |
|Leap Motor     |1000000000|1000000000|100.00       |

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%206.png?raw=true)
# Q7️: Find the Most Common Industry by Continent
## Solution
```SQL
SELECT c.continent, i.industry, COUNT(*) AS industry_count
FROM industries i
JOIN companies c ON i.company_id = c.company_id
GROUP BY c.continent, i.industry
ORDER BY c.continent, industry_count DESC;
```
## Output
|continent    |industry                           |industry_count|
|-------------|-----------------------------------|--------------|
|Africa       |Fintech                            |2             |
|Africa       |Mobile & telecommunications        |1             |
|Asia         |E-commerce & direct-to-consumer    |54            |
|Asia         |Fintech                            |38            |
|Asia         |Internet software & services       |31            |
|Asia         |Supply chain, logistics, & delivery|26            |
|Asia         |Artificial intelligence            |26            |
|Asia         |Auto & transportation              |20            |
|Asia         |Mobile & telecommunications        |19            |
|Asia         |Edtech                             |19            |
|Asia         |Hardware                           |18            |
|Asia         |Health                             |15            |
|Asia         |Other                              |14            |
|Asia         |Consumer & retail                  |12            |
|Asia         |Travel                             |7             |
|Asia         |Cybersecurity                      |7             |
|Asia         |Data management & analytics        |4             |
|Europe       |Fintech                            |47            |
|Europe       |E-commerce & direct-to-consumer    |18            |
|Europe       |Internet software & services       |15            |
|Europe       |Other                              |11            |
|Europe       |Health                             |8             |
|Europe       |Auto & transportation              |7             |
|Europe       |Artificial intelligence            |6             |
|Europe       |Supply chain, logistics, & delivery|6             |
|Europe       |Data management & analytics        |6             |
|Europe       |Mobile & telecommunications        |5             |
|Europe       |Hardware                           |5             |
|Europe       |Travel                             |5             |
|Europe       |Consumer & retail                  |2             |
|Europe       |Cybersecurity                      |1             |
|Europe       |Edtech                             |1             |
|North America|Internet software & services       |154           |
|North America|Fintech                            |129           |
|North America|Health                             |51            |
|North America|Artificial intelligence            |49            |
|North America|Cybersecurity                      |42            |
|North America|E-commerce & direct-to-consumer    |33            |
|North America|Other                              |31            |
|North America|Data management & analytics        |31            |
|North America|Supply chain, logistics, & delivery|21            |
|North America|Mobile & telecommunications        |12            |
|North America|Hardware                           |11            |
|North America|Consumer & retail                  |11            |
|North America|Edtech                             |8             |
|North America|Auto & transportation              |4             |
|North America|Travel                             |2             |
|Oceania      |Internet software & services       |5             |
|Oceania      |Fintech                            |2             |
|Oceania      |E-commerce & direct-to-consumer    |1             |
|South America|Fintech                            |6             |
|South America|E-commerce & direct-to-consumer    |5             |
|South America|Supply chain, logistics, & delivery|4             |
|South America|Artificial intelligence            |3             |
|South America|Other                              |2             |
|South America|Mobile & telecommunications        |1             |

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%207.png?raw=true)
# Q8️: Find Top 20 Companies That Raised More Than Industry Average
## Solution
```SQL
SELECT c.company, f.funding, i.industry
FROM funding f
JOIN industries i ON f.company_id = i.company_id
JOIN companies c ON f.company_id = c.company_id
WHERE f.funding > (
    SELECT AVG(f2.funding) FROM funding f2 
    JOIN industries i2 ON f2.company_id = i2.company_id 
    WHERE i2.industry = i.industry
)
ORDER BY f.funding DESC
Limit 20;
```
## Output
|company           |funding    |industry                           |
|------------------|-----------|-----------------------------------|
|JUUL Labs         |14000000000|Consumer & retail                  |
|Bytedance         |8000000000 |Artificial intelligence            |
|Epic Games        |7000000000 |Other                              |
|SpaceX            |7000000000 |Other                              |
|Global Switch     |5000000000 |Hardware                           |
|J&T Express       |5000000000 |Supply chain, logistics, & delivery|
|Swiggy            |5000000000 |Supply chain, logistics, & delivery|
|Xingsheng Selected|5000000000 |E-commerce & direct-to-consumer    |
|Argo AI           |4000000000 |Artificial intelligence            |
|Northvolt         |4000000000 |Other                              |
|WM Motor          |4000000000 |Auto & transportation              |
|Ola Cabs          |4000000000 |Auto & transportation              |
|BYJU's            |4000000000 |Edtech                             |
|Klarna            |4000000000 |Fintech                            |
|Fanatics          |4000000000 |E-commerce & direct-to-consumer    |
|Chehaoduo         |4000000000 |E-commerce & direct-to-consumer    |
|Yuanfudao         |4000000000 |Edtech                             |
|OYO Rooms         |3000000000 |Travel                             |
|Databricks        |3000000000 |Data management & analytics        |
|SVOLT             |3000000000 |Auto & transportation              |

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%208.png?raw=true)
# Q9️: Find the Fastest-Growing Unicorns (Shortest Time from Founding to Unicorn Status)
## Solution
```SQL
SELECT c.company, d.year_founded, d.date_joined, 
       (d.date_joined - (d.year_founded || '-01-01')::DATE) AS days_to_unicorn
FROM dates d
JOIN companies c ON d.company_id = c.company_id
ORDER BY days_to_unicorn ASC
LIMIT 10;
```
## Output
|company              |year_founded|date_joined|days_to_unicorn|
|---------------------|------------|-----------|---------------|
|Yidian Zixun         |2021        |2017-10-17 |-1172          |
|Ola Electric Mobility|2019        |2019-07-02 |182            |
|Playco               |2020        |2020-09-21 |264            |
|candy.com            |2021        |2021-10-21 |293            |
|ClickHouse           |2021        |2021-10-28 |300            |
|Mensa Brands         |2021        |2021-11-16 |319            |
|Flink Food           |2021        |2021-12-01 |334            |
|Jokr                 |2021        |2021-12-02 |335            |
|Avant                |2012        |2012-12-17 |351            |
|GlobalBees           |2021        |2021-12-28 |361            |

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%209a.png?raw=true)
###
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%209b.png?raw=true)
# Q10: Find the Oldest Unicorns (Companies Founded the Longest Ago but Still Unicorns)
## Solution
```SQL
SELECT c.company, d.year_founded, f.valuation
FROM dates d
JOIN funding f ON d.company_id = f.company_id
JOIN companies c ON d.company_id = c.company_id
ORDER BY d.year_founded ASC
LIMIT 10;
```
## Output
|company                   |year_founded|valuation  |
|--------------------------|------------|-----------|
|Otto Bock HealthCare      |1919        |4000000000 |
|Promasidor Holdings       |1979        |2000000000 |
|Five Star Business Finance|1984        |1000000000 |
|Radius Payment Solutions  |1990        |1000000000 |
|Epic Games                |1991        |32000000000|
|BGL Group                 |1992        |2000000000 |
|Thirty Madison            |1993        |1000000000 |
|Howden Group Holdings     |1994        |5000000000 |
|Vice Media                |1994        |6000000000 |
|Intarcia Therapeutics     |1995        |4000000000 |

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%2010.png?raw=true)
# Q11: Average Time (in Years) from Founding to Unicorn Status by Continent
## Solution
```SQL
SELECT c.continent,
       ROUND(AVG(EXTRACT(YEAR FROM d.date_joined) - d.year_founded), 2) AS avg_years_to_unicorn
FROM companies c
JOIN dates d ON c.company_id = d.company_id
GROUP BY c.continent
ORDER BY avg_years_to_unicorn;
```
## Output
|continent    |avg_years_to_unicorn|
|-------------|--------------------|
|Asia         |6.61                |
|North America|6.88                |
|South America|7.05                |
|Africa       |7.67                |
|Oceania      |7.88                |
|Europe       |8.25                |

## Visualization
![Dasboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%2011.png?raw=true)
# Q12: Most Common Founding Years Among Unicorns
## Solution
```SQL
SELECT year_founded, COUNT(*) AS company_count
FROM dates
GROUP BY year_founded
ORDER BY company_count DESC
LIMIT 10;
```
## Output
|year_founded|company_count|
|------------|-------------|
|2015        |155          |
|2016        |110          |
|2014        |109          |
|2012        |95           |
|2013        |87           |
|2011        |82           |
|2017        |74           |
|2018        |61           |
|2019        |45           |
|2010        |40           |

## Output
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%2012.png?raw=true)
# Q13: Companies Founded Before 2010 but Valued Over $10 Billion
## Solution
```SQL
SELECT c.company, d.year_founded, f.valuation
FROM companies c
JOIN dates d ON c.company_id = d.company_id
JOIN funding f ON c.company_id = f.company_id
WHERE d.year_founded < 2010 AND f.valuation > 10000000000
ORDER BY f.valuation DESC;
```
## Output
|company               |year_founded|valuation   |
|----------------------|------------|------------|
|SpaceX                |2002        |100000000000|
|SHEIN                 |2008        |100000000000|
|Klarna                |2005        |46000000000 |
|Epic Games            |1991        |32000000000 |
|Fanatics              |2002        |27000000000 |
|BYJU's                |2008        |22000000000 |
|Grammarly             |2009        |13000000000 |
|GoodLeap              |2003        |12000000000 |
|Xingsheng Selected    |2009        |12000000000 |
|Biosplice Therapeutics|2008        |12000000000 |
|Global Switch         |1998        |11000000000 |
|Weilong Foods         |1999        |11000000000 |

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%2013.png?raw=true)
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
