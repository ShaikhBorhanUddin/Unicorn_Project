# 🦄 Unicorn Company Analysis
<!-- Project Badges -->
![Made with](https://img.shields.io/badge/Made%20with-SQL-blue?logo=database)
![License](https://img.shields.io/github/license/ShaikhBorhanUddin/Inventory_Management_Project)
![Repo Size](https://img.shields.io/github/repo-size/ShaikhBorhanUddin/Inventory_Management_Project)
![Stars](https://img.shields.io/github/stars/ShaikhBorhanUddin/Inventory_Management_Project?style=social)
![Forks](https://img.shields.io/github/forks/ShaikhBorhanUddin/Inventory_Management_Project?style=social)
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

- **Source**: [Unicorn Dataset](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/tree/main/Dataset)
- **Database Name**: `Unicorn_Project`
- **Tables**:
  - `companies`: Company details like name, city, country, and continent.
  - `dates`: Founding year and the date when the company achieved unicorn status.
  - `funding`: Valuation, total funding raised, and selective investors.
  - `industries`: Industry classification for each company.
- **ER Diagram**
###
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

## 📊 Key Questions Answered

Here’s what you’ll uncover with the SQL queries included:

`Top 5 Most Valuable Companies` `Number of Unicorns per Continent` `Early Founders, Late Unicorns` `Average Valuation by Industry` `Companies with the Most Selective Investors` `Top 10 Companies with Highest Funding-to-Valuation Ratio` `Most Common Industry by Continent` `Companies Raising Above Industry Average` `Fastest-Growing Unicorns` `Oldest Unicorns` `Average Time to Unicorn by Continent` `Most Common Founding Years` `Pre-2010 Companies Worth Over $10 Billion` `Continent with the Highest Total Unicorn Valuation` `Top 3 Industries with the Highest Average Funding` `Industry Diversity by Country` `Countries with Most Unicorns Founded After 2022`

These 17 queries are critical in business analytics because they transform raw data into actionable insights that support strategic decision-making. Understanding which companies are the most valuable helps benchmark industry leaders and set performance goals. Analyzing the number of unicorns by continent reveals regional strengths and emerging markets, while insights into early founders and late unicorns help identify companies that succeed through long-term resilience. Average valuation by industry highlights which sectors are receiving the highest market confidence, and analyzing companies with the most selective investors provides a signal of credibility and strong business fundamentals. Looking at funding-to-valuation ratios can uncover capital efficiency and potential overvaluation. Knowing the most common industries by continent helps businesses align their offerings with regional demand. Queries such as identifying companies raising above the industry average or the fastest-growing unicorns are essential for spotting high-potential disruptors. Meanwhile, understanding the oldest unicorns provides insight into business models that are sustainable over time. Metrics like average time to unicorn by continent and most common founding years reveal how ecosystems evolve and when startup surges occurred. Further, identifying pre-2010 companies worth over $10 billion uncovers long-term success stories, and measuring total unicorn valuation by continent supports macroeconomic and investment analysis. Exploring industries with the highest average funding, industry diversity by country, and the most unicorns founded after 2022 helps analysts and investors spot trends, gaps, and opportunities in both mature and emerging ecosystems.

Altogether, these queries offer a 360-degree view of the unicorn startup space, making them highly valuable for investors, analysts, policymakers, and entrepreneurs who rely on data to drive growth, mitigate risks, and identify the next wave of innovation.

## 🧠 Some Sample Queries
SQL codes of some of these queries are included here.

## 🧩 Solution Workflow

Detailed solutions are documented in the [Solutions.md](https://github.com/ShaikhBorhanUddin/Unicorn_Company_Analysis/blob/main/Solutions.md) file.

The workflow includes:
1. **Database Design**: ERD creation and schema setup
2. **Data Cleaning**: Importing and refining raw CSV files
3. **SQL Queries**: Analytical queries to address business questions
4. *(Optional Future Step)*: Data visualization and dashboard creation

## 💡 Tools Used

- **PostgreSQL**: For database creation and query execution.
- **SQL**: Analytical querying language for insights.
- **Tableau**: Visualization of query results.

## 🤝 Contribution

Feel free to fork the repository, improve the queries, or add visualizations!

## 📄 License

This project is licensed under the MIT License.

---

Happy querying! 🚀✨
