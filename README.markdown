# Retail and Wholesale Vendor & Inventory Analysis

## Project Overview
This project analyzes inventory efficiency, vendor performance, and profitability in the retail and wholesale industry using Python-based data analysis and a Power BI dashboard. The goal is to optimize pricing, purchasing, inventory turnover, and vendor relationships to enhance profitability.

## Business Objective
- Minimize losses from inefficient pricing.
- Ensure healthy inventory turnover to avoid capital lock-in.
- Reduce over-reliance on a few vendors.

## Key Goals
- Identify underperforming brands and vendors.
- Assess the impact of bulk purchasing on unit cost and gross profit.
- Evaluate inventory turnover and vendor concentration risks.
- Analyze profitability across vendor segments.

## Power BI Dashboard
- **File**: Project.vendor.pbix
- **Highlights**:
  - KPIs: Total Sales ($441.41M), Total Purchase Cost ($307.34M), Gross Profit ($134.07M), Profit Margin (38.72%), Unsold Capital ($2.71M).
  - Visualizations: Top Brands (e.g., Jack Daniels, Tito’s), Top Vendors (e.g., Diageo North America at $68M), Vendor Contribution (>65% from top 10), Low-Performing Vendors (e.g., Dunn Wine Brokers).

## Analytical Insights
- Bulk purchasing lowers unit costs by up to 72%, boosting profit if managed well.
- Low-performing vendors show high margins (~41.5%) but low sales.
- $2.71M is locked in slow-moving inventory, impacting liquidity.
- Over 65% vendor reliance increases supply chain risk.

## Methodology
- **Data Cleaning**: Removed zero/negative profit transactions.
- **EDA**: Correlation analysis and outlier detection.
- **Statistical Testing**: Hypothesis testing on margin differences.
- **Visualization**: Interactive Power BI dashboard.

## Recommendations
- Adjust pricing for high-margin, low-volume brands.
- Optimize inventory with better forecasting.
- Diversify vendor base to reduce risks.
- Improve logistics to address high freight costs.
- Promote low-performing vendors with marketing efforts.

## Files Included
- `project.ipynb`: Data cleaning, exploration, and analysis.
- `project_cont.ipynb`: Additional analysis and validation.
- `Project.vendor.pbix`: Power BI dashboard with visuals.

## Conclusion
This project delivers data-driven insights for profitability through vendor management, pricing, and inventory control. The dashboard supports ongoing decision-making.

## Setup Instructions & Technical Details

### 1. Project Structure

```
├── project.ipynb            # Main notebook: Data loading, cleaning, merging
├── project_cont.ipynb       # Continued analysis: EDA, statistical insights
├── Project.vendor.pbix      # Power BI Dashboard
├── README.md                # Documentation
└── /data/                   # Folder containing CSVs or source data files (optional)
```

### 2. Python Environment Setup

Make sure you have Python 3.8 or later installed. Use a virtual environment to isolate dependencies.

#### a. Create and activate a virtual environment:
```bash
python -m venv venv
source venv/bin/activate     # For Linux/macOS
venv\Scripts\activate        # For Windows
```

#### b. Install required dependencies:

```bash
pip install -r requirements.txt
```

If `requirements.txt` is not available, the core packages used include:

```txt
pandas
numpy
matplotlib
seaborn
scipy
sqlite3    # Built-in with Python, no separate install needed
```

To generate `requirements.txt` from your environment:

```bash
pip freeze > requirements.txt
```

### 3. Database Connection

The project uses SQLite to store and query data from multiple CSV files.

#### How it works:

- CSV files are loaded as pandas DataFrames.
- Each DataFrame is saved as a separate table in a local SQLite database.
- The database is created and queried using Python’s built-in `sqlite3` module.

#### Code example:

```python
import sqlite3

# Create or connect to a SQLite database
conn = sqlite3.connect('my_database.db')

# Save each DataFrame as a table
for name, df in dataframes.items():
    table_name = name.replace('.csv', '')
    df.to_sql(table_name, conn, if_exists='replace', index=False)
```

#### Querying example:

```python
query = "SELECT * FROM final_table LIMIT 5"
df = pd.read_sql(query, conn)
```

### 4. Power BI Dashboard

- File: `Project.vendor.pbix`
- Load into Power BI Desktop.
- Data should be exported from the final DataFrame in `project_cont.ipynb`, for example:

```python
final_df.to_csv('final_output.csv', index=False)
```

This exported file can then be used in Power BI to refresh the dashboard.

### 5. Execution Order

1. Start with `project.ipynb`: Performs initial data cleaning, merging, and transformation.
2. Continue with `project_cont.ipynb`: Further analysis, visualization, and statistical insights.
3. Export final output if needed for Power BI or reporting.