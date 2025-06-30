# 🦄 Unicorn Company Analysis
<!-- Project Badges -->
![Made with](https://img.shields.io/badge/Made%20with-SQL-blue?logo=database)
![License](https://img.shields.io/github/license/ShaikhBorhanUddin/Unicorn_Company_Analysis)
![Repo Size](https://img.shields.io/github/repo-size/ShaikhBorhanUddin/Unicorn_Company_Analysis)
![Stars](https://img.shields.io/github/stars/ShaikhBorhanUddin/Unicorn_Company_Analysis?style=social)
![Forks](https://img.shields.io/github/forks/ShaikhBorhanUddin/Unicorn_Company_Analysis?style=social)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-336791?logo=postgresql&logoColor=white)
![Data Visualization](https://img.shields.io/badge/Data%20Visualization-Tableau-E97627?logo=Tableau&logoColor=white)
![Git](https://img.shields.io/badge/Version%20Control-Git-orange?logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/Host-GitHub-black?logo=github)
![Project Status](https://img.shields.io/badge/Project-Completed-brightgreen?style=flat-square)

###
<img src="https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/unicorn_cropped.png?raw=true" alt="Dashboard" style="width:100%;"/>

## 📍 Project Overview

The **Unicorn Company Analysis** project aims to explore and analyze the global landscape of unicorn startups — privately held companies valued at over $1 billion. Using Python and data visualization libraries like Matplotlib and Seaborn, this project uncovers key insights about the distribution, growth trends, and industry representation of unicorns across the world. The main objectives of this project include:
- Understanding the historical growth of unicorns over time.
- Identifying the top countries and industries producing the most unicorns.
- Analyzing valuation ranges and spotting the highest-valued companies.
- Exploring investment patterns and funding trends.

Whether you're an aspiring data analyst, investor, or startup enthusiast, this project provides data-driven perspectives on one of the most exciting segments of the global startup ecosystem.

## 📦 Dataset Information

The database integrates key dimensions such as company identity, location, funding details, industry classification, and timeline to unicorn status. By combining business attributes with geographic and financial metrics, the database enables powerful analysis of growth patterns, market trends, regional distribution, and investment dynamics within the global startup ecosystem. This setup supports complex querying to explore how different industries, continents, and founding years influence the trajectory toward unicorn valuation. To access the database click [link](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/tree/main/Dataset). The tables of the database is described in the following tables.

### 🧾 Dates

| Column        | Description                                           |
|---------------|-------------------------------------------------------|
| `company_id`  | A unique identifier assigned to each company.         |
| `date_joined` | The date the company achieved unicorn status.         |
| `year_founded`| The year the company was originally founded.          |

### 💰 Funding

| Column           | Description                                           |
|------------------|-------------------------------------------------------|
| `company_id`     | A unique identifier assigned to each company.         |
| `valuation`      | The company's valuation in US dollars.                |
| `funding`        | Total funding amount raised by the company in USD.    |
| `select_investors` | A list of notable or key investors in the company. |

### 🏭 Industries

| Column       | Description                                        |
|--------------|----------------------------------------------------|
| `company_id` | A unique identifier assigned to each company.      |
| `industry`   | The industry sector in which the company operates. |

### 🏢 Companies

| Column       | Description                                                  |
|--------------|--------------------------------------------------------------|
| `company_id` | A unique identifier assigned to each company.                |
| `company`    | The name of the unicorn company.                             |
| `city`       | The city where the company is headquartered.                 |
| `country`    | The country where the company is headquartered.              |
| `continent`  | The continent where the company is headquartered.            |

### **ER Diagram**
All 4 tables are linked by company_id column. The ER diagram is given below.

![Dashboard](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Images/ERD.png?raw=true)

## 📁 Folder Structure
```bash
Unicorn_Company_Analysis/
│
├── Dataset/                   # Raw dataset(s)
├── Images/                    # Visualizations
├── Licence                 
├── README.md
├── Solutions.md               # answer to SQL queries with visualizations
├── Unicorn_Project.sql        # SQL codes
```
## 🛠️ Setup

1. Clone the repository.
2. Import the `Unicorn_Project.sql` file into your PostgreSQL environment.
3. Run the queries provided to explore and analyze unicorn companies.

## 🧩 Solution Workflow

Detailed solutions and relevant visualizations are documented in the [Solutions.md](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Solutions.md) file.

The workflow includes:
1. **Database Design**: ERD creation and schema setup
2. **Data Cleaning**: Importing and refining raw CSV files
3. **SQL Queries**: Analytical queries to address business questions
4. **Visualization**: Data visualization from query results
## 📊 Key Questions Answered

Here’s what you’ll uncover with the SQL queries included:

`Top 5 Most Valuable Companies` `Number of Unicorns per Continent` `Early Founders, Late Unicorns` `Average Valuation by Industry` `Companies with the Most Selective Investors` `Top 10 Companies with Highest Funding-to-Valuation Ratio` `Most Common Industry by Continent` `Companies Raising Above Industry Average` `Fastest-Growing Unicorns` `Oldest Unicorns` `Average Time to Unicorn by Continent` `Most Common Founding Years` `Pre-2010 Companies Worth Over $10 Billion` `Continent with the Highest Total Unicorn Valuation` `Top 3 Industries with the Highest Average Funding` `Industry Diversity by Country` `Countries with Most Unicorns Founded After 2022`

These 17 queries are critical in business analytics because they transform raw data into actionable insights that support strategic decision-making. Understanding which companies are the most valuable helps benchmark industry leaders and set performance goals. Analyzing the number of unicorns by continent reveals regional strengths and emerging markets, while insights into early founders and late unicorns help identify companies that succeed through long-term resilience. Average valuation by industry highlights which sectors are receiving the highest market confidence, and analyzing companies with the most selective investors provides a signal of credibility and strong business fundamentals. Looking at funding-to-valuation ratios can uncover capital efficiency and potential overvaluation. Knowing the most common industries by continent helps businesses align their offerings with regional demand. Queries such as identifying companies raising above the industry average or the fastest-growing unicorns are essential for spotting high-potential disruptors. Meanwhile, understanding the oldest unicorns provides insight into business models that are sustainable over time. Metrics like average time to unicorn by continent and most common founding years reveal how ecosystems evolve and when startup surges occurred. Further, identifying pre-2010 companies worth over $10 billion uncovers long-term success stories, and measuring total unicorn valuation by continent supports macroeconomic and investment analysis. Exploring industries with the highest average funding, industry diversity by country, and the most unicorns founded after 2022 helps analysts and investors spot trends, gaps, and opportunities in both mature and emerging ecosystems.

Altogether, these queries offer a 360-degree view of the unicorn startup space, making them highly valuable for investors, analysts, policymakers, and entrepreneurs who rely on data to drive growth, mitigate risks, and identify the next wave of innovation.

## 🧠 Some Sample Queries
SQL codes of some of these queries with explanations are included here.
```sql
SELECT c.country, COUNT(*) AS unicorn_count
FROM companies c
JOIN dates d ON c.company_id = d.company_id
WHERE d.date_joined >= '2022-01-01'
GROUP BY c.country
ORDER BY unicorn_count DESC;
```
**Explanation:** 
This SQL query retrieves the number of unicorn companies founded **from January 1, 2022 onward**, grouped by country. It joins the `companies` and `dates` tables on `company_id`, filters for recent entries using the `date_joined` field, and returns a ranked list of countries based on how many unicorns were created in each, in **descending order** of count.

```sql
SELECT c.country, COUNT(DISTINCT i.industry) AS industry_count
FROM companies c
JOIN industries i ON c.company_id = i.company_id
GROUP BY c.country
ORDER BY industry_count DESC;
```
**Explanation:**
This SQL query identifies the **diversity of industries** in which unicorn companies operate across different countries. By joining the `companies` and `industries` tables on `company_id`, it counts the **distinct industries** represented in each country. The results are grouped by country and sorted in **descending order** of industry count, revealing which countries have the most **industry-diverse unicorn ecosystems**.

```sql
SELECT c.company, d.year_founded, f.valuation
FROM companies c
JOIN dates d ON c.company_id = d.company_id
JOIN funding f ON c.company_id = f.company_id
WHERE d.year_founded < 2010 AND f.valuation > 10000000000
ORDER BY f.valuation DESC;
```
**Explanation:**
This SQL query fetches unicorn companies that were **founded before 2010** and have a **valuation exceeding $10 billion**. It joins the `companies`, `dates`, and `funding` tables on `company_id`, applies filters on founding year and valuation, and returns the company name, founding year, and valuation. The results are sorted in **descending order of valuation**, highlighting the **oldest and most valuable unicorns**.

## 📈 Visual Insights

Data visualization plays a crucial role in translating complex query results into intuitive insights. In this project, **Tableau** was utilized to create a variety of interactive and static visualizations, each tailored to the nature of the analysis for enhanced clarity and storytelling.

### 📊 Bar Charts for Comparative Metrics

For queries involving **aggregated metrics** such as average valuation or the funding-to-valuation ratio, bar charts were used for their clarity and simplicity. These visuals are effective in highlighting top-performing industries or companies, and help compare values across categories in a visually direct manner.

<p align="center">
  <img src="Images/Sheet 4.png" alt="Average Valuation by Industry" width="52%" />
  <img src="Images/Sheet 6.png" alt="Top Funding-to-Valuation Ratios" width="47.1%" />
</p>

### ⏱️ Gantt Charts and Tree Maps for Multivariate and Time-Series Data

Queries that involve **time-based patterns** or **multidimensional parameters**, such as unicorns over time, founding year vs. valuation, or investor complexity, benefit from Gantt charts, line plots, or tree maps. These chart types provide layered insights, making it easier to detect temporal trends, relationships, and nested structures.

<div align="center" style="display: flex; flex-wrap: wrap; justify-content: space-between; width: 100%; gap: 10px;">
<img src="Images/Sheet 3.png" alt="Unicorn Growth Over Time" style="width: 48%; height: 250px; object-fit: cover; margin: 5px;" />
<img src="Images/Sheet 13.png" alt="Investor Network Tree Map" style="width: 48%; height: 250px; object-fit: cover; margin: 5px;" />
</div>

### 🌍 Geographical Insights via World Maps

For **country-specific and region-based queries**, such as the number of unicorns per continent, total valuation by region, or industry dominance by country, choropleth or world maps were used. These maps visually convey geographic concentrations and disparities in unicorn activity, helping to highlight regional strengths and gaps in the global startup ecosystem.

<div align="center" style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 20px;">
<img src="Images/Sheet 16.png" alt="Delivery Time Analysis" width="49%" />
<img src="Images/Sheet 17.png" alt="Payment Type Distribution" width="49%" />
</div>

Each visualization was carefully chosen to enhance understanding, enable pattern recognition, and support effective storytelling through data. For all visualization, please follow the [website](https://shaikhborhanuddin.github.io/Unicorn_Company_Analysis).

## 🎯 Key Insights & Recommendations
- The USA and China account for 80% of unicorns—indicating regional startup dominance.
- Fintech and E-Commerce are the most common unicorn industries.
- Majority of unicorns were founded post-2010, suggesting acceleration in recent years.
- Tiger Global and Sequoia Capital are among the most active investors—key VCs to watch.

📌 **Business Tip:** Investors and startup founders should focus on tech-driven sectors in USA or Asia and target growth funding rounds post-Series A.

## 💡 Tools Used

**`PostgreSQL`** **`Tableau`** **`Microsoft Excel`**

PostgreSQL served as the primary database management system for this project. It was used to store, manage, and query the unicorn company dataset efficiently. Complex SQL queries were executed to extract insights on valuation trends, industry diversity, regional growth patterns, and more. Its powerful support for joins, aggregations, and window functions made it ideal for analytical exploration. Tableau was used for data visualization and storytelling. The insights generated through SQL were visualized using interactive dashboards and charts, enabling clearer pattern recognition and comparison. From bar charts and tree maps to time series and world maps, Tableau helped translate raw data into intuitive and visually compelling narratives. Excel played a key role in initial data cleaning, quick summaries, and exploratory analysis. It was also used for formatting raw CSV files before importing them into PostgreSQL, and for creating pivot tables and supplementary charts to support deeper inspection of individual metrics.

These tools together provided a robust end-to-end workflow—from querying and analysis to visualization and presentation.

## 📄 Licence

This project is licensed under the **MIT License** — a permissive open-source license that allows reuse, modification, and distribution with attribution. You are free to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the project, provided that the original copyright and license notice are included in all copies or substantial portions of the software.

For more details, refer to the [LICENCE](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Licence) file in this repository.

## 🤝 Contact

If you have any questions or would like to connect, feel free to reach out!

**Shaikh Borhan Uddin**  
📧 Email: [`shaikhborhanuddin@gmail.com`](mailto:shaikhborhanuddin@gmail.com)  
🔗 [`LinkedIn`](https://www.linkedin.com/in/shaikh-borhan-uddin-905566253/)  
🌐 [`Portfolio`](https://github.com/ShaikhBorhanUddin)


Feel free to fork the repository, improve the queries, or add visualizations!


---

Happy querying! 🚀✨
