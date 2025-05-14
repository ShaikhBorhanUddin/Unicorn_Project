# Q1️: Find the Top 5 Most Valuable Companies

This question is critically important in the context of business intelligence because it helps stakeholders—such as investors, analysts, and strategic decision-makers—identify which companies are currently leading in terms of market valuation. High valuations typically signal strong investor confidence, rapid growth, market dominance, or future potential. Knowing the top players enables benchmarking, competitive analysis, and targeted investment strategies. Additionally, these insights can guide startup founders and venture capitalists in understanding what industries or business models are attracting the most capital and attention, shaping future funding and innovation trends.

## Solution
```SQL
SELECT company, valuation 
FROM funding 
JOIN companies ON funding.company_id = companies.company_id
ORDER BY valuation DESC
LIMIT 5;
```
This SQL query is designed to retrieve the **top 5 most valuable unicorn companies** based on their valuation. It begins by selecting the `company` name and its `valuation` from two related tables: `funding` and `companies`. These tables are connected using an **INNER JOIN** on the `company_id` field, which ensures that only records present in both tables are included. The results are then **sorted in descending order** using `ORDER BY valuation DESC`, so that the companies with the highest valuations appear first. Finally, the `LIMIT 5` clause restricts the output to just the top five entries, making the query both efficient and focused on the most significant data points.

## Output
|company     |valuation  |
|------------|-----------|
|Bytedance   |180000000000|
|SpaceX      |100000000000|
|SHEIN       |100000000000|
|Stripe      |95000000000|
|Klarna      |46000000000|

The chart displays the **top 5 most valuable unicorn companies** based on their valuations. **Bytedance** leads the list with a valuation of **$180 billion**, significantly ahead of the others. **SpaceX** and **SHEIN** are tied in second place with **$100 billion** each, followed by **Stripe** at **$95 billion**. **Klarna** rounds out the list with a valuation of **$46 billion**. These figures highlight the dominance of companies in tech and innovation-driven sectors.

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%201.png?raw=true)

# Q2️: Count the Number of Unicorns per Continent

This question helps identify which continents are leading in the creation of high-growth, billion-dollar startups. In a business intelligence context, this insight is valuable for regional market analysis, investment strategy, and economic development planning. Understanding the geographic distribution of unicorns allows investors, policymakers, and stakeholders to recognize innovation hubs, allocate resources effectively, and benchmark performance across regions. It also highlights the impact of regional ecosystems, regulatory environments, and talent pools on startup success.

## Solution
```SQL
SELECT continent, COUNT(*) AS unicorn_count
FROM companies
GROUP BY continent
ORDER BY unicorn_count DESC;
```
This query counts the number of unicorn companies in each continent. It selects the `continent` field from the `companies` table and uses the `COUNT(*)` function to calculate how many companies exist per continent. The `GROUP BY continent` clause groups the data by continent, so the count is calculated separately for each one. Finally, `ORDER BY unicorn_count DESC` sorts the results in descending order to display the continents with the most unicorns at the top.

## Output
|continent    |unicorn_count|
|-------------|-------------|
|North America|589          |
|Asia         |310          |
|Europe       |143          |
|South America|21           |
|Oceania      |8            |
|Africa       |3            |

The chart shows the **distribution of unicorn companies across continents**. **North America** leads by a wide margin with **589 unicorns**, followed by **Asia** with **310**, and **Europe** with **143**. These three continents dominate the global unicorn landscape. In contrast, **South America** has only **21**, **Oceania** has **8**, and **Africa** has just **3** unicorns, indicating a significant gap in startup growth and investment between regions. This highlights how startup ecosystems and access to capital are heavily concentrated in certain parts of the world.

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%202.png?raw=true)

# Q3️: Find Companies Founded Before 2000 That Became Unicorns After 2015

This question is important in business intelligence because it helps identify **long-established companies that achieved unicorn status much later** in their lifecycle. These are often firms that pivoted, underwent digital transformation, or gained traction after years of steady growth. Unlike typical unicorns that scale rapidly, these companies reflect **resilience, adaptability, and long-term strategic success**. Understanding their journey offers valuable lessons for investors and executives about alternative paths to high valuation beyond the fast-growth startup model.

## Solution
```SQL
SELECT c.company, d.year_founded, d.date_joined
FROM dates d
JOIN companies c ON d.company_id = c.company_id
WHERE d.year_founded < 2000 AND d.date_joined >= '2015-01-01';
```
This SQL query identifies unicorn companies that were founded before the year 2000 but only achieved unicorn status after 2015. It joins the `dates` table (which holds founding and unicorn dates) with the `companies` table using the `company_id`. The `WHERE` clause filters the results to include only those companies where `year_founded` is less than 2000 and `date_joined` (i.e., the date they became unicorns) is on or after January 1, 2015. This helps spotlight businesses that had a long growth period before reaching high valuation.

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

The table highlights **23 companies** that were **founded before the year 2000** but achieved **unicorn status only after 2015**. These companies represent **slow-burning success stories** that took **over 15 years or more** to reach billion-dollar valuations. Notable examples include **Otto Bock HealthCare**, founded in **1919**, and **Promasidor Holdings**, founded in **1979**, showing how traditional or long-established businesses can evolve and eventually scale to unicorn status. This trend underscores the importance of **long-term innovation, persistence, and strategic transformation**, challenging the typical fast-growth unicorn narrative often associated with tech startups.

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
# Q14: Continent with the Highest Total Unicorn Valuation
## Solution
```SQL
SELECT c.continent, SUM(f.valuation) AS total_valuation
FROM companies c
JOIN funding f ON c.company_id = f.company_id
GROUP BY c.continent
ORDER BY total_valuation DESC
LIMIT 1;
```
## Output
|continent    |total_valuation|
|-------------|---------------|
|North America|2032000000000  |

# Q15: Top 3 Industries with the Highest Average Funding
## Solution
```SQL
SELECT i.industry, ROUND(AVG(f.funding), 2) AS avg_funding
FROM industries i
JOIN funding f ON i.company_id = f.company_id
GROUP BY i.industry
ORDER BY avg_funding DESC
LIMIT 3;
```
## Output
|industry             |avg_funding  |
|---------------------|-------------|
|Auto & transportation|1131419354.84|
|Consumer & retail    |1019680000.00|
|Travel               |901857142.86 |

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%2015.png?raw=true)
# Q16: Industry Diversity: Number of Different Industries Per Country
## Solution
```SQL
SELECT c.country, COUNT(DISTINCT i.industry) AS industry_count
FROM companies c
JOIN industries i ON c.company_id = i.company_id
GROUP BY c.country
ORDER BY industry_count DESC;
```
## Output
|country             |industry_count|
|--------------------|--------------|
|China               |15            |
|United States       |15            |
|United Kingdom      |12            |
|Israel              |11            |
|India               |11            |
|Germany             |11            |
|South Korea         |9             |
|Canada              |9             |
|France              |8             |
|Sweden              |6             |
|Singapore           |6             |
|Brazil              |6             |
|Switzerland         |5             |
|Indonesia           |5             |
|Hong Kong           |5             |
|Japan               |4             |
|Finland             |4             |
|Netherlands         |4             |
|Belgium             |3             |
|Spain               |3             |
|Australia           |3             |
|Ireland             |3             |
|Turkey              |3             |
|Vietnam             |2             |
|Austria             |2             |
|Colombia            |2             |
|Estonia             |2             |
|Mexico              |2             |
|Norway              |2             |
|Philippines         |2             |
|South Africa        |2             |
|Thailand            |2             |
|United Arab Emirates|2             |
|Senegal             |1             |
|Lithuania           |1             |
|Bermuda             |1             |
|Italy               |1             |
|Denmark             |1             |
|Czech Republic      |1             |
|Croatia             |1             |
|Malaysia            |1             |
|Bahamas             |1             |
|Luxembourg          |1             |
|Nigeria             |1             |
|Chile               |1             |
|Argentina           |1             |

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%2016.png?raw=true)
# Q17: Countries with the Highest Number of Unicorns Founded After 2022
## Solution
```SQL
SELECT c.country, COUNT(*) AS unicorn_count
FROM companies c
JOIN dates d ON c.company_id = d.company_id
WHERE d.date_joined >= '2022-01-01'
GROUP BY c.country
ORDER BY unicorn_count DESC;
```
## Output
|country       |unicorn_count|
|--------------|-------------|
|United States |69           |
|India         |11           |
|United Kingdom|5            |
|France        |4            |
|Canada        |3            |
|Israel        |3            |
|Finland       |2            |
|Ireland       |2            |
|Australia     |2            |
|Germany       |2            |
|China         |2            |
|Italy         |1            |
|Belgium       |1            |
|Chile         |1            |
|Switzerland   |1            |
|Estonia       |1            |
|Indonesia     |1            |
|Norway        |1            |
|Brazil        |1            |
|Turkey        |1            |
|South Korea   |1            |
|Spain         |1            |

## Visualization
![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/Sheet%2017.png?raw=true)
