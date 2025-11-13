# SQL Data Analysis Tasks

This repository contains SQL tasks completed as part of my data analytics learning journey.  
The goal is to explore real-world datasets and use SQL to extract meaningful business insights.

---

## Project Overview
These queries were written to practice:
- Data filtering and selection (`WHERE`, `LIMIT`, `ORDER BY`)
- Aggregations and group operations (`SUM`, `AVG`, `COUNT`, `GROUP BY`)
- Conditional logic (`CASE WHEN`)
- Data cleaning and transformations
- Joins between multiple tables (`JOIN-ON`)
- Subqueries and Common Table Expressions (CTEs)

---

##  Tools Used
- **SQL** (SQLite)
- **DB Browser for SQLite** or **MySQL Workbench**
- **DataBase File** as data source

---

##  Files in This Repository
SQL Data Analysis Tasks_AdventureWorks.db.ipynb : SQL queries
AdventureWorksTables : Tables and relationships betwwen thier
AdventureWorks.db : dataset 
README.md file
---

##  Example Query
```%%sql
with english_description as 
( Select pc.productModelID,pd.description 
from productModelProductDescriptionCulture pc 
join productDescription pd
on pc.productDescriptionid=pd.productDescriptionid
where pc.cultureID = 'en'
)
select d.* ,p.name ,sum(s.OrderQty) total_number_of_sales
from english_description d
join product p
on p.productModelID= d.productModelID
join salesorderdetail s
on s.productid=p.productid
group by p.name
order by total_number_of_sales desc
limit 10 
