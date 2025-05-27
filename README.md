# Home Sales Analysis (Big Data Challenge)

## Overview
This project analyzes home sales data using SparkSQL.
The challenge involved answering key questions about home prices based on various attributes, optimizing query performance by caching data, partitioning, and verifying the effects of these operations.

The code can be found in the [`Home_Sales.ipynb`](Home_Sales.ipynb) file.

Partitioned files are not included in this repository to reduce storage requirements.
If needed, they can be regenerated using the provided scripts.

## Results and Runtime Comparisons
The runtimes for the query calculating average home price per "view" rating (≥ $350,000) were as follows:

| Query Type   | Runtime (seconds) |
|-------------|------------------|
| Original Query | 0.5576 |
| Cached Query   | 0.3964 |
| Partitioned Query | 0.9917 |

### Analysis
- **Caching:** Improved runtime performance significantly, reducing execution time from **0.5576 sec** to **0.3964 sec**.
- **Partitioning:** Increased runtime to **0.9917 sec**, likely due to partitioning by `date_built`, which was not directly relevant to the query (grouping was based on `view`). While partitioning can improve query efficiency in the right context, in this case, it did not align with the query structure, causing a slowdown.
