# CDC Birth Data SQL Analysis 🍼  
*A public health data project exploring U.S. county-level birth trends using BigQuery SQL (2016–2018)*

---

## 📊 Project Overview

As a public health researcher, I analyzed county-level birth data from the CDC's WONDER Natality dataset using BigQuery SQL. The goal was to identify which counties had the highest and lowest number of births, and to examine birth trends over time in select upstate New York counties.

---

## 📁 Dataset

- **Source:** [CDC WONDER Natality - sdoh_cdc_wonder_natality](https://console.cloud.google.com/marketplace/product/bigquery-public-data/sdoh_cdc_wonder_natality)
- **Table Used:** `county_natality`
- **Years Covered:** 2016–2018

**Key Fields:**
- `Year`
- `County_of_Residence`
- `State`
- `Births`
- `Avg_Age_of_Mother`
- `Ave_OE_Gestational`
- `Ave_LMP_Gestational`

---

## 🎯 Objectives

- Use SQL to explore, sort, and filter public birth data  
- Identify counties with the most and fewest births  
- Analyze birth trends in Erie, Niagara, and Chautauqua Counties (NY)

---

### 💻 SQL Queries Used

### ✅ Query 1: Preview First 1,000 Rows

```sql
SELECT *
FROM
bigquery-public-data.sdoh_cdc_wonder_natality.county_natality
LIMIT
1000;
````

*Used to explore the structure and contents of the dataset.*

---

### 📉 Query 2: 10 Counties with the Fewest Births (Ascending)

```sql
SELECT *
FROM
bigquery-public-data.sdoh_cdc_wonder_natality.county_natality
ORDER BY
Births ASC
LIMIT 10;
```

*Identifies the counties with the lowest birth counts between 2016–2018.*

---

### 📈 Query 3: 10 Counties with the Most Births (Descending)

```sql
SELECT *
FROM
bigquery-public-data.sdoh_cdc_wonder_natality.county_natality
ORDER BY
Births DESC
LIMIT
10;
```

*Shows the counties with the highest birth counts — Los Angeles County consistently ranks at the top.*

---

### 🗺️ Query 4: Birth Trends in Upstate New York Counties

```sql
SELECT *
FROM
bigquery-public-data.sdoh_cdc_wonder_natality.county_natality
WHERE
County_of_Residence = 'Erie County, NY' 
  OR County_of_Residence = 'Niagara County, NY'
  OR County_of_Residence = 'Chautauqua County, NY'
ORDER BY
Births DESC, 
  Year;
```

*Filters the data to only three upstate New York counties and sorts by county and year to examine localized birth trends over time.*

---

### 🏆 Query 5: Highest Birth Counts in Selected NY Counties

```sql
SELECT *
FROM bigquery-public-data.sdoh_cdc_wonder_natality.county_natality
WHERE
  County_of_Residence = 'Erie County, NY' 
  OR County_of_Residence = 'Niagara County, NY'
  OR County_of_Residence = 'Chautauqua County, NY'
ORDER BY
Births DESC,
Year;
```

*Sorts the same three NY counties by births in descending order to identify the highest number of births by county and year.*

---

## 📈 Key Insights

* **Tompkins County, NY** had the fewest births in a single year: only **735 births in 2018**
* **Los Angeles County, CA** had the highest birth counts across all three years
* **Erie, Niagara, and Chautauqua counties** showed subtle but steady declines in births from 2016 to 2018
* Sorting by birth count in descending order revealed that **Erie County peaked in 2016**, while **Niagara and Chautauqua peaked earlier** and declined steadily

---

## 📂 Project Structure

```
/sql
  └── births_by_county.sql

/visualizations
  └── ny-county-trends.png

/README.md
```

---

## 🔧 Tools Used

* Google BigQuery (SQL)
* CDC Public Health Datasets
* Tableau (for visualization)

---

## 👩‍💻 Author

**Angela Perez**
📌 [GitHub](https://github.com/angelaperezdata) • [LinkedIn](https://www.linkedin.com/in/angela-perez-07a28m16/)

---

**Built with BigQuery SQL to uncover trends in U.S. birth data for public health insights. 💡**
