# Optimizing Large Datasets with Python and SQLite

## Project Overview

This project analyzes a **Crunchbase investment dataset containing 54,294 company records**, with a focus on processing and exploring data efficiently using **Python, Pandas, and SQLite**.

I built a workflow to clean and analyze the dataset without loading the entire CSV file into memory at once. The approach combines chunk-based processing, selective column loading, and SQL queries for data exploration.

The analysis examines company locations, funding by market, company status, and first-funding activity over time.

## Technologies Used

- **Python and Pandas:** Chunk-based data processing, cleaning, and memory analysis.
- **SQLite and SQL:** Data storage, deduplication, and aggregation queries.
- **Matplotlib:** Data visualization.
- **Jupyter Notebook:** Exploration and documentation.

## Methodology

### 1. Dataset exploration

I started by reading the CSV in **chunks of 5,000 rows** to examine the dataset structure, missing values, and memory usage by column. This allowed me to inspect the data without loading the complete file into memory.

### 2. Memory optimization

Seven unnecessary or redundant columns were excluded during data loading. I compared the estimated DataFrame memory usage before and after this change.

| Metric | Before optimization | After optimization |
|---|---:|---:|
| Estimated DataFrame memory usage | 24.45 MB | 17.49 MB |

The result was an estimated **28.5% reduction in DataFrame memory usage (6.96 MB)**. This measures the footprint of the selected columns, not peak application RAM or execution time.

### 3. Data cleaning and SQLite storage

Each chunk was processed to remove fully empty rows, drop duplicates, trim whitespace, and convert funding amounts to numeric values.

I stored the processed records in a SQLite table called `investments_raw` and created an `investments_clean` table to remove duplicates across chunks.

### 4. SQL analysis and visualization

SQL aggregation queries were used to summarize the cleaned data, while smaller query results were loaded into Pandas for visualization.

The exploratory analysis highlighted the following patterns:

- **Company distribution:** The United States had the highest number of records (**28,793 companies**), followed by the United Kingdom and Canada.
- **Funding by market:** Biotechnology, Mobile, and Software were among the leading markets by recorded funding.
- **Company status:** Most companies were classified as operating.
- **First-funding trends:** Recorded first-funding activity increased after the mid-2000s and peaked in **2013**.

These observations reflect the historical dataset rather than the entire global venture-capital market.


## Conclusion

This project demonstrates how chunk-based processing, column selection, and SQLite aggregation can support memory-efficient data analysis. It also gave me practical experience combining **Pandas, SQL, and data visualization** to explore a real-world dataset.
