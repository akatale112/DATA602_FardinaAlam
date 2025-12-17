# Dynamic Pricing Model: Seasonal and Competitive Analysis

## DATA 602 - Principles of Data Science Final Project

### Project Overview

This project develops a **dynamic pricing model** that predicts optimal product prices by considering:
1. **Seasonal factors** (holidays, seasons, time of year)
2. **Competitor pricing** (prices from competing sellers/companies)
3. **Historical patterns** (price trends over time)

### Research Question

**How can we dynamically adjust product prices based on seasons and competitor pricing to maximize competitiveness?**

**Example Scenario:**
- Company A: Sweater priced at $12
- Company B: Same sweater priced at $13
- During Christmas: Model predicts Company B should reduce price to $11 to remain competitive

---

## Dataset Information

**Dataset:** Olist Brazilian E-commerce Dataset

**Source:** [Kaggle - Brazilian E-commerce Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

**Dataset Characteristics:**
- **Size:** 100K+ orders, 32K+ products, 3K+ sellers
- **Time Period:** 2016-2018
- **Key Features:** Multiple sellers (competitors), temporal data, product categories

**Why This Dataset:**
- Enables competitor analysis (multiple sellers selling same products)
- Temporal data allows seasonal/holiday analysis
- Large enough for meaningful ML analysis
- Real-world e-commerce pricing patterns

**Dataset Files:**
- `olist_customers_dataset.csv` - Customer information
- `olist_geolocation_dataset.csv` - Geographic data
- `olist_order_items_dataset.csv` - Order items with prices
- `olist_order_payments_dataset.csv` - Payment information
- `olist_order_reviews_dataset.csv` - Customer reviews
- `olist_orders_dataset.csv` - Order details with timestamps
- `olist_products_dataset.csv` - Product information
- `olist_sellers_dataset.csv` - Seller information
- `product_category_name_translation.csv` - Category translations

---

## Project Structure

```
602 Project/
├── Dataset/
│   ├── olist_customers_dataset.csv
│   ├── olist_geolocation_dataset.csv
│   ├── olist_order_items_dataset.csv
│   ├── olist_order_payments_dataset.csv
│   ├── olist_order_reviews_dataset.csv
│   ├── olist_orders_dataset.csv
│   ├── olist_products_dataset.csv
│   ├── olist_sellers_dataset.csv
│   └── product_category_name_translation.csv
├── Dynamic_Pricing.ipynb
├── README.md
└── requirements.txt (optional)
```

---

## Installation & Setup

### Prerequisites

- **Python Version:** 3.9 or higher
- **Jupyter Notebook** (for running the notebook)

### Required Libraries

Install the required packages using pip:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```

Or create a `requirements.txt` file with:

```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=1.0.0
scipy>=1.7.0
```

Then install with:

```bash
pip install -r requirements.txt
```

---

## Project Checkpoints

### Checkpoint 1: Data Preprocessing & Cleaning (10 points)

This section covers:
- **(a)** Import your chosen dataset
- **(b)** Parse and transform as needed (convert data types, extract features, format conversion)
- **(c)** Organize into appropriate data structures (pandas DataFrame)
- **(d)** Clean the data (address missing values, correct inconsistencies, remove duplicates, handle data quality issues)

**Key Steps:**
1. Import all 9 CSV files into pandas DataFrames
2. Convert date columns to datetime format
3. Convert numeric columns to appropriate types
4. Handle missing values (median for numeric, mode for categorical)
5. Remove duplicates and invalid data (negative/zero prices)
6. Merge datasets for comprehensive analysis

### Checkpoint 2: Exploratory Data Analysis with Statistical Methods (15 points)

This section presents **three conclusions** using **at least three different statistical methods** including **hypothesis testing**, each supported by visually appealing plots.

#### Statistical Method 1: Correlation Analysis (Pearson Correlation)
- **Research Question:** Are product price and freight value correlated?
- **Hypothesis:** H₀: No correlation (ρ = 0) vs H₁: Correlation exists (ρ ≠ 0)
- **Result:** Statistically significant moderate positive correlation (r=0.411)
- **Visualization:** Scatter plots and box plots

#### Statistical Method 2: Hypothesis Testing (Two-Sample T-Test)
- **Research Question:** Do product prices differ significantly between holiday seasons (Christmas) and non-holiday periods?
- **Hypothesis:** H₀: Mean prices equal vs H₁: Mean prices differ
- **Result:** Analysis of seasonal price differences
- **Visualization:** Histograms, box plots, monthly averages, violin plots

#### Statistical Method 3: Chi-Square Test for Independence
- **Research Question:** Are product categories evenly distributed, or are some categories over-represented?
- **Hypothesis:** H₀: Categories evenly distributed vs H₁: Categories not evenly distributed
- **Result:** Categories are significantly over-represented (p < 0.05)
- **Visualization:** Bar charts, pie charts, observed vs expected comparisons

### Checkpoint 3: Dynamic Pricing Model Implementation

**Features Engineered:**
- Temporal features: month, day of week, weekend indicator
- Seasonal features: season, Christmas season, Black Friday, days to Christmas
- Competitor features: average competitor price, min competitor price, competitor count, price differences
- Product features: category, weight

**Model:**
- **Algorithm:** Random Forest Regressor
- **Training:** Time-based split (80% train, 20% test)
- **Performance Metrics:**
  - Test RMSE: ~25.90 BRL
  - Test MAE: ~2.00 BRL
  - Test R²: ~0.9823

**Key Features (by importance):**
1. Price difference from minimum competitor price
2. Minimum competitor price
3. Price difference from average competitor price
4. Average competitor price
5. Competitor count

---

## How to Run

1. **Clone or download this repository**

2. **Ensure the Dataset folder is in the project directory**
   - The notebook expects the dataset files in `Dataset/` folder
   - Alternatively, update the path in the notebook if using a different location

3. **Open the Jupyter Notebook:**
   ```bash
   jupyter notebook Dynamic_Pricing.ipynb
   ```

4. **Run all cells sequentially:**
   - The notebook is designed to run from top to bottom
   - Some cells may take several minutes to execute (especially competitor feature calculation)

5. **Expected Runtime:**
   - Data loading and preprocessing: ~1-2 minutes
   - EDA and statistical analysis: ~2-3 minutes
   - Competitor feature calculation: ~5-10 minutes (depending on sample size)
   - Model training: ~1-2 minutes
   - Total: ~10-20 minutes

---

## Key Findings

### Statistical Conclusions

1. **Price-Freight Correlation:** There is a statistically significant moderate positive correlation (r=0.411) between product price and freight value, indicating that higher-priced items typically have higher shipping costs.

2. **Seasonal Price Differences:** Analysis shows the importance of considering seasonal factors in pricing strategies, though specific results depend on the data.

3. **Category Over-Representation:** Product categories are not evenly distributed; certain categories (e.g., 'bed_bath_table') dominate the marketplace, which should be factored into pricing strategies.

### Model Performance

- **High Predictive Accuracy:** R² score of 0.9823 indicates strong predictive capability
- **Low Error:** Mean Absolute Error of 2.00 BRL on test set
- **Feature Importance:** Competitor pricing features are the most important predictors

### Business Implications

1. **Seasonal Pricing Strategy:** Companies should adjust prices during holiday seasons to remain competitive
2. **Competitor Monitoring:** Tracking competitor prices is crucial for dynamic pricing decisions
3. **Category-Specific Pricing:** Different product categories may require different pricing strategies

---

## Results & Visualizations

The notebook includes comprehensive visualizations for:
- Dataset characteristics and summary statistics
- Correlation analysis (scatter plots, box plots)
- Hypothesis testing (histograms, box plots, monthly trends, violin plots)
- Chi-square test results (bar charts, pie charts, observed vs expected)
- Feature importance analysis
- Prediction vs actual price comparisons
- Dynamic pricing recommendations

---

## Dependencies

### Python Libraries

- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computing
- **matplotlib** - Plotting and visualization
- **seaborn** - Statistical data visualization
- **scikit-learn** - Machine learning algorithms
- **scipy** - Statistical functions and hypothesis testing

### Python Version

- Python 3.9 or higher recommended

---

## Limitations & Future Work

### Current Limitations

1. **Data Limitations:** Limited competitor data for some products (used fallback strategies)
2. **Feature Engineering:** Could incorporate more features like customer behavior, inventory levels, demand forecasts
3. **Model Optimization:** Could experiment with other algorithms (XGBoost, Neural Networks) and hyperparameter tuning
4. **Real-time Implementation:** Model would need to be deployed in a real-time system for production use

### Future Enhancements

- Incorporate customer behavior and purchase history
- Add inventory level considerations
- Implement demand forecasting
- Experiment with ensemble methods
- Deploy as a real-time pricing API
- Add A/B testing framework for price optimization

---

## Author Information

**Author:** Aditi Katale  
**Course:** DATA 602 - Principles of Data Science  
**Institution:** UMCP  
**Date:** 16 December 2025

---

## Acknowledgments

- **Dataset Source:** [Kaggle - Olist Brazilian E-commerce Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- **Dataset Provider:** Olist (Brazilian e-commerce platform)
- **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn, scipy

---

## License

This project is for educational purposes as part of the DATA 602 Principles of Data Science course.

---

## Citation

If you use this project or dataset, please cite:

```
Olist Brazilian E-commerce Dataset. (2018). 
Kaggle. https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
```

---



