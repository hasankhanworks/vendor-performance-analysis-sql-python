# vendor-performance-analysis-sql-python

Vendor Performance Analysis | EDA Project

This project performs end-to-end analysis of vendor performance using purchase, sales, and inventory data.
It includes data ingestion, cleaning, transformation, summarization, and detailed Exploratory Data Analysis (EDA) to generate actionable business insights.

The goal is to help identify profitable vendors, slow-moving inventory, pricing patterns, and opportunities for business optimization.

1. Project Structure
├── Exploratory_data_analysis.ipynb       # EDA on final vendor summary
├── vendor_performance_analysis.ipynb     # Vendor-level insights & visualizations
├── get_vendor_summary.py                 # Merges raw tables into vendor summary
├── ingestion_db.py                       # Loads CSV data into SQLite database
├── ingestion_db.log                      # Log file for ingestion process
├── README.md                             # Project documentation
└── data/                                 # Raw CSV files (not uploaded to GitHub)

2. Objective of the Project

Ingest raw CSV files into a SQLite database.

Merge sales, purchases, and vendor invoice tables into a single summary table.

Clean and transform the data for meaningful analysis.

Perform Exploratory Data Analysis (EDA) to understand:

Sales performance

Profit margins

Vendor efficiency

Inventory turnover

Correlation between key metrics

Identify high-performing and low-performing vendors.

Provide actionable insights for pricing, purchasing, and inventory decisions.

3. Data Engineering Workflow
Step 1: Data Ingestion

All CSV files in the data/ folder are loaded into SQLite using:

df.to_sql(table_name, con=engine, if_exists='replace')

Step 2: Vendor Summary Creation

Using SQL joins on:

purchases

sales

purchase_prices

vendor_invoice

The script generates:

vendor_sales_summary table


containing:

Total purchases

Total sales

Freight cost

Profit metrics

Stock turnover

Sales-to-purchase ratio

4. Key Features of Analysis
4.1 Correlation Insights

The correlation heatmap revealed:

PurchasePrice has almost no impact on Total Sales or Gross Profit.

TotalPurchaseQuantity and TotalSalesQuantity have a perfect correlation (1.00), indicating efficient inventory flow.

ProfitMargin and TotalSalesPrice show a weak negative correlation (−0.18), suggesting higher selling price does not always increase margins.

StockTurnover shows:

Almost no relationship with Gross Profit

Mild positive correlation (+0.40) with ProfitMargin

4.2 Vendor Profitability Insights

A confidence-interval test showed:

Low-performing vendors have higher average margins (40–42%).

High-performing vendors have lower margins (30–31%).
This suggests premium vendors sell less but earn higher margins, while bulk vendors sell more at lower margins.

4.3 Inventory & Pricing Insights

Bulk orders receive the lowest unit cost (~72% reduction vs small orders).

Fast-moving items do not always generate high gross profit.

Some vendors show high purchase values but low sales conversion.

5. Visualizations Included

The analysis includes:

Correlation Heatmap

Pareto Analysis (Top Vendors Contribution)

Scatterplots: Sales vs Profit Margin

Bar Charts: Top 10 Vendors and Top 10 Brands

Boxplots: Bulk Order Impact on Unit Price

Distribution Plots with Confidence Intervals

6. Technologies Used

Python

Pandas

NumPy

Matplotlib & Seaborn

SciPy (statistical testing)

SQLite (local database)

SQLAlchemy

Logging module

7. How to Run the Project
1. Clone the Repository
  

2. Install Dependencies
pip install -r requirements.txt

3. Run Data Ingestion
python ingestion_db.py

4. Generate Vendor Summary Table
python get_vendor_summary.py

5. Run EDA Notebooks

Open .ipynb files in Jupyter Notebook or VS Code.

8. Insights for Business Decision Making

High-performing vendors can improve profitability through cost optimization and selective pricing.

Low-performing vendors need stronger marketing and distribution strategies to increase volume.

Bulk purchasing strategies significantly reduce per-unit cost and increase margins.

Inventory management is efficient, but certain brands show overstock risk.
