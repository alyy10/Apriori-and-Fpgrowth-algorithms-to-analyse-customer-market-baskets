# Apriori-and-Fpgrowth-algorithms-to-analyse-customer-market-baskets

## Overview

This repository hosts a comprehensive **Market Basket Analysis (MBA)** project. Market Basket Analysis is a powerful data mining technique used to uncover associations between items frequently purchased together in transactional datasets. By applying the **Apriori algorithm**, this project identifies strong relationships between products, enabling retailers to optimize strategies such as product placement, cross-selling, promotional bundling, and targeted marketing campaigns.

The project provides an end-to-end example of MBA, from data loading and preprocessing to generating and interpreting association rules. It serves as a valuable resource for data analysts, business intelligence professionals, and students interested in applying association rule mining to real-world retail scenarios.

## Project Purpose

The primary objectives of this project are:

- **Illustrate MBA Concepts**: Clearly explain core metrics such as *support*, *confidence*, and *lift*, and demonstrate their application in identifying meaningful product associations.
- **Demonstrate Data Preparation**: Showcase the steps required to clean, merge, and transform raw transactional data into a format suitable for MBA.
- **Implement Apriori Algorithm**: Provide a working implementation of the Apriori algorithm to discover frequent itemsets and derive association rules.
- **Deliver Actionable Insights**: Translate analytical findings into practical business strategies, such as optimizing store layouts, enhancing cross-selling opportunities, and improving inventory management.

## Datasets

The project utilizes eight datasets, stored in the `data/` directory, to perform the Market Basket Analysis. These datasets simulate a retail environment, providing information about customers, products, product categories, and transactions.

## Methodology

The Market Basket Analysis follows a structured pipeline implemented in the `Market+Basket.ipynb` notebook:

1. **Data Loading and Initial Exploration**

   - Loads `customer.csv`, `product.csv`, `product_class.csv`, and `sales.csv` into pandas DataFrames.
   - Uses `.head()` to inspect the structure and content of each dataset, ensuring correct loading and data integrity.
2. **Data Merging and Integration**

   - **Product Enrichment**: Merges `product.csv` with `product_class.csv` on `product_class_id` (left join) to add hierarchical classification (subcategory, category, department, family).
   - **Customer Integration**: Merges `sales.csv` with `customer.csv` on `customer_id` (left join) to include customer demographics in transaction records.
   - **Full Integration**: Merges the resulting sales DataFrame with the enriched product DataFrame on `product_id` to create a comprehensive dataset combining transaction, customer, and product details.
3. **Data Preprocessing for MBA**

   - **Missing Value Check**: Uses `.isnull().sum()` to identify missing values in the sales DataFrame.
   - **Unique Value Count**: Applies `.nunique()` to assess the cardinality of each column, aiding in data understanding.
   - **Filtering**: Filters transactions to include only products in the 'Food' family to focus the analysis on a specific product domain.
   - **Transaction-Item Mapping**: Groups transactions by `customer_id`, aggregating `product_name` into lists to create customer baskets (one row per customer with a list of purchased products).
4. **Apriori Algorithm and Association Rule Mining**

   - **One-Hot Encoding**: Transforms the customer baskets into a binary DataFrame where rows are customers, columns are products, and values are 1 (purchased) or 0 (not purchased) using a custom `encode_units` function and pandas' `get_dummies`.
   - **Frequent Itemset Generation**: Applies the `apriori` function from `mlxtend.frequent_patterns` with a minimum support threshold of 0.07, identifying itemsets that appear in at least 7% of transactions.
   - **Association Rule Derivation**: Uses `association_rules` with `metric="lift"` and `min_threshold=1` to generate rules, ensuring only rules with positive associations (lift > 1) are included.
   - **Sorting Rules**: Sorts rules by lift in descending order to highlight the strongest associations.
5. **Analysis and Interpretation**

   - Displays the association rules in a DataFrame with metrics: *antecedents*, *consequents*, *support*, *confidence*, and *lift*.
   - Interprets rules to identify product pairs frequently purchased together, providing insights for business applications.

## Prerequisites

To run the notebook, ensure the following are installed:

- **Python 3.11** or higher
- **Jupyter Notebook** or **JupyterLab**
- **Required Libraries**:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `mlxtend`
  - `IPython`

Install dependencies using pip:

```bash
pip install pandas numpy matplotlib mlxtend IPython
```

## Usage

The `Market+Basket.ipynb` notebook guides users through the MBA process:

1. **Introduction**: Markdown cells explain MBA concepts and the project's objectives.
2. **Library Imports**: Imports `pandas`, `numpy`, `matplotlib`, `mlxtend`, and configures IPython for multiple outputs and full DataFrame display.
3. **Data Loading**: Loads and previews the datasets using `.head()`.
4. **Data Merging**: Combines datasets to create a unified transaction dataset.
5. **Data Preparation**: Filters for 'Food' family products, checks for missing values, and transforms data into customer baskets.
6. **Apriori Analysis**: Generates frequent itemsets and association rules, sorted by lift.
7. **Results**: Displays rules for interpretation, ready for business applications.

To extend the analysis, consider:

- **Parameter Tuning**: Adjust `min_support` or `min_threshold` to explore different rule sets.
- **Visualization**: Add network graphs or heatmaps to visualize associations (e.g., using `seaborn` or `networkx`).
- **Custom Analysis**: Incorporate temporal trends or customer segment analysis by leveraging additional columns like `sale_date` or `yearly_income`.

## Key Findings and Recommendations

### Key Findings

- **Frequent Itemsets**: The Apriori algorithm identifies product combinations appearing in at least 7% of transactions, forming the basis for association rules.
- **Association Rules**: Rules with lift > 1 indicate strong positive associations (e.g., "Customers who buy Milk also buy Cereal").
- **Metrics**:
  - *Support*: Frequency of itemset occurrence.
  - *Confidence*: Likelihood of purchasing the consequent given the antecedent.
  - *Lift*: Strength of association compared to independent purchases.

### Business Recommendations

- **Product Placement**: Place associated products (e.g., Bread and Butter) closer in stores to encourage impulse buys.
- **Cross-Selling**: Train staff to suggest related items based on strong rules (e.g., recommend Cheese with Wine purchases).
- **Promotional Bundling**: Offer discounts on frequently co-purchased items (e.g., Pasta and Sauce bundles).
- **Targeted Marketing**: Use rules for personalized recommendations in email campaigns or e-commerce platforms (e.g., suggest Baby Wipes to Diaper buyers).
- **Inventory Optimization**: Ensure associated products are stocked together to avoid missed sales opportunities.
- **E-commerce Enhancements**: Implement "Customers who bought this also bought..." features based on association rules.
