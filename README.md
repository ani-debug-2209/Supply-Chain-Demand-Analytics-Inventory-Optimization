# Supply Chain Demand Analytics & Inventory Optimization

A Python-based supply-chain analytics project for analyzing demand, forecasting future requirements, and optimizing inventory levels using data-driven techniques.

## Overview

This project provides an end-to-end workflow for supply-chain and inventory analysis. It uses historical demand and inventory information to identify demand patterns, forecast future demand, calculate safety stock and reorder points, and recommend inventory levels.

The project is implemented in a Jupyter Notebook:

`Supply-Chain-Demand-Analytics-Inventory-Optimization.ipynb`

If a real dataset is not provided, the notebook automatically generates a realistic synthetic supply-chain dataset so the complete analysis can be executed immediately.

## Features

- Historical demand analysis
- Demand trend and seasonality visualization
- 30-day demand forecasting
- Moving-average forecasting model
- Forecast accuracy evaluation using MAE and RMSE
- Safety stock calculation
- Reorder point calculation
- Inventory target calculation
- Current vs. target inventory analysis
- Stockout-risk identification
- Excess inventory analysis
- ABC inventory classification
- Economic Order Quantity (EOQ) calculation
- Inventory holding-cost analysis
- Supply-chain summary dashboard
- Export of optimization results to CSV

## Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib

## Project Workflow

```text
Supply-Chain Data
       ↓
Data Validation
       ↓
Demand Analysis
       ↓
Demand Forecasting
       ↓
Forecast Accuracy
       ↓
Safety Stock
       ↓
Reorder Point
       ↓
Inventory Optimization
       ↓
ABC Classification
       ↓
EOQ Analysis
       ↓
Inventory Cost Analysis
       ↓
Supply-Chain Dashboard
```

## Dataset

The notebook can work with either synthetic or real data.

### Synthetic Data

By default, the notebook generates approximately two years of daily data containing:

- Date
- Product ID
- Category
- Daily demand
- Inventory
- Lead time
- Unit cost
- Orders

### Custom Dataset

A custom CSV file can be supplied by changing:

```python
DATA_PATH = None
```

to:

```python
DATA_PATH = "supply_chain_data.csv"
```

The minimum required columns are:

```text
date
product_id
demand
inventory
lead_time_days
unit_cost
```

## Forecasting

The project uses a 28-day moving-average model as a transparent baseline for short-term demand forecasting.

The forecast is generated for the next 30 days.

Forecast performance is evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)

## Inventory Optimization

### Safety Stock

Safety stock is calculated using demand variability, lead time, and the selected service level:

```text
Safety Stock = z × Demand Standard Deviation × √Lead Time
```

The default target service level is:

```python
TARGET_SERVICE_LEVEL = 0.95
```

### Reorder Point

The reorder point is calculated as:

```text
Reorder Point = Average Daily Demand × Lead Time + Safety Stock
```

Products whose current inventory falls below the reorder point are identified as being at risk and may require replenishment.

### Inventory Target

The project calculates a target inventory level using demand, lead time, review period, demand variability, and service-level assumptions.

## ABC Classification

ABC analysis categorizes products based on annual consumption value:

```text
Annual Consumption Value =
Annual Demand × Unit Cost
```

Products are classified into:

- **A** — highest consumption-value contribution
- **B** — medium contribution
- **C** — lower contribution

This helps prioritize inventory-management attention.

## EOQ

Economic Order Quantity is estimated using:

```text
EOQ = √(2DS / H)
```

Where:

- `D` = annual demand
- `S` = ordering cost per order
- `H` = annual holding cost per unit

The default assumptions can be changed in the notebook.

## Installation

Install the required Python packages:

```bash
pip install pandas numpy matplotlib jupyter
```

## Running the Notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
Supply-Chain-Demand-Analytics-Inventory-Optimization.ipynb
```

Run the cells from top to bottom.

## Output

After execution, the notebook generates:

```text
inventory_optimization_results.csv
```

This file contains the main inventory-planning results, including:

- Current inventory
- Target inventory
- Safety stock
- Reorder point
- Inventory gap
- Recommended order quantity
- Stockout-risk status
- Excess inventory
- Excess inventory value

## Business Applications

The project can help answer questions such as:

- Which products may need replenishment?
- Which products have excessive inventory?
- How much safety stock should be maintained?
- When should a replenishment order be placed?
- Which products require closer inventory monitoring?
- What ordering quantity can be used as a planning reference?
- How can inventory holding costs be reduced?

## Limitations

This is an analytical prototype and uses simplified assumptions. A production implementation should additionally consider:

- Supplier minimum order quantities
- Order multiples
- Supplier reliability
- Variable lead times
- Promotions
- Pricing changes
- Lost sales
- Warehouse capacity
- Multiple warehouses
- Multi-echelon inventory
- Real-time ERP data

## Future Improvements

Potential extensions include:

- XGBoost or LightGBM forecasting
- SARIMA and Prophet forecasting
- LSTM/GRU forecasting
- Croston's method for intermittent demand
- Promotion and pricing features
- Supplier reliability analysis
- Multi-echelon inventory optimization
- Automated procurement alerts
- Power BI dashboard
- Streamlit web application
- ERP integration

## Author

**Bikram Singh**

Supply Chain Demand Analytics & Inventory Optimization project built with Python.
