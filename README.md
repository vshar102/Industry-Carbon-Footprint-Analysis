# Analyzing Product Carbon Footprints
## Project Overview
This project analyzes the carbon footprints of various products to understand their environmental impact. Greenhouse gas emissions attributable to products globally make up more than 75% of total emissions. Using a dataset derived from [The Carbon Catalogue](https://www.nature.com/articles/s41597-022-01178-9) (publicly available on nature.com), this analysis examines Product Carbon Footprints (PCFs) for various companies across different industries. 
The primary objective is to evaluate the total greenhouse gas emissions (measured in CO₂ equivalent) across industries for the most recent year available in the dataset.
## Dataset
The data is stored in a PostgreSQL database consisting of a single table, `product_emissions`. It contains data on product carbon footprints and the stages of production where these emissions occur.
### `product_emissions` Schema:
| Field | Data Type | Description |
|---|---|---|
| `id` | `VARCHAR` | Unique identifier for the product footprint record |
| `year` | `INT` | Year of the carbon footprint data |
| `product_name` | `VARCHAR` | Name of the evaluated product |
| `company` | `VARCHAR` | Company manufacturing the product |
| `country` | `VARCHAR` | Country of origin |
| `industry_group` | `VARCHAR` | Industry sector the company belongs to |
| `weight_kg` | `NUMERIC` | Weight of the product in kilograms |
| `carbon_footprint_pcf` | `NUMERIC` | Product carbon footprint measured in CO₂ equivalent |
| `upstream_percent_total_pcf` | `VARCHAR` | Percentage of emissions from upstream operations |
| `operations_percent_total_pcf` | `VARCHAR` | Percentage of emissions from core operations |
| `downstream_percent_total_pcf` | `VARCHAR` | Percentage of emissions from downstream operations |
## Analysis & Methodology
The analysis is conducted using SQL within a Jupyter Notebook ([notebook.ipynb](cci:7://file:///Users/ashutoshbhardwaj/Downloads/Datacamp%20Projects%20for%20Portfolio-VARUN%20SHARMA/workspace%205/notebook.ipynb:0:0-0:0)). 
Key workflows include:
1. **Data Exploration:** Initial selection and preview of the `product_emissions` dataset.
2. **Timeframe Isolation:** Identifying the maximum `year` present in the table to focus purely on the latest emissions data.
3. **Industry Aggregation:** Grouping records by `industry_group` for the most recent year to calculate:
   - The total number of unique companies represented in each industry.
   - The total carbon footprint per industry (summing the `carbon_footprint_pcf`, rounded to one decimal place).
4. **Ranking:** Sorting the resulting aggregations in descending order by total industry footprint to identify the largest contributing sectors.
## Key Findings
Based on the SQL aggregation of the latest available data, the footprint broken down by industry group is:
1. **Materials** - 107,129.0 total PCF (across 3 companies)
2. **Capital Goods** - 94,942.7 total PCF (across 2 companies)
3. **Technology Hardware & Equipment** - 21,865.1 total PCF (across 4 companies)
4. **Food, Beverage & Tobacco** - 3,161.5 total PCF
5. **Commercial & Professional Services** - 740.6 total PCF
6. **Software & Services** - 690.0 total PCF
## Technical Stack
- **Languages:** SQL
- **Environment:** Jupyter Notebook (DataLab)
- **Database:** PostgreSQL
