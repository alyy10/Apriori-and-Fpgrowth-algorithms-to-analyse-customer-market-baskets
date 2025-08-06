# Market Basket Analysis Project

## 📊 Project Overview

This project implements **Market Basket Analysis**, a data mining technique used by large retailers to discover associations between items purchased together. By analyzing transaction patterns, retailers can identify relationships between products that frequently appear in the same shopping basket, enabling better inventory management, product placement, and cross-selling strategies.

## 🎯 Objectives

Market Basket Analysis helps answer key business questions:
- Which products are frequently bought together?
- What items should be placed near each other in stores?
- Which products can be cross-promoted to increase sales?
- How can we optimize product bundling strategies?

## 📁 Dataset Description

The project utilizes a comprehensive retail dataset with multiple interconnected tables:

### 📋 Data Structure

| Dataset | File | Records | Description |
|---------|------|---------|-------------|
| **Sales** | `sales.csv` | Transaction records | Core transactional data with product, customer, store, and sales information |
| **Products** | `product.csv` | Product catalog | Detailed product information including brands, prices, and specifications |
| **Customers** | `customer.csv` | Customer profiles | Demographics, income, location, and customer characteristics |
| **Stores** | `store.csv` | Store information | Store details, locations, types, and features |
| **Product Classes** | `product_class.csv` | Product hierarchy | Product categorization and department structure |
| **Regions** | `region.csv` | Geographic data | Sales regions and districts |
| **Time** | `time_by_day.csv` | Date dimensions | Time-based data for temporal analysis |

### 🔍 Key Data Features

#### Sales Data (`sales.csv`)
- **product_id**: Unique product identifier
- **customer_id**: Unique customer identifier  
- **store_id**: Store location identifier
- **time_id**: Transaction timestamp reference
- **store_sales**: Total sales amount
- **store_cost**: Product cost
- **unit_sales**: Number of units sold

#### Product Data (`product.csv`)
- **product_id**: Product identifier
- **product_class_id**: Product category reference
- **brand_name**: Product brand
- **product_name**: Full product name
- **SKU**: Stock Keeping Unit
- **SRP**: Suggested Retail Price
- **gross_weight** & **net_weight**: Product weights
- **recyclable_package**: Environmental indicator
- **low_fat**: Health indicator

#### Customer Data (`customer.csv`)
- **customer_id**: Unique customer identifier
- **city**, **state_province**, **country**: Geographic location
- **yearly_income**: Income bracket
- **gender**: Customer gender
- **total_children**: Number of children
- **education**: Education level
- **occupation**: Job category
- **member_card**: Loyalty card type

#### Store Data (`store.csv`)
- **store_id**: Store identifier
- **store_type**: Store category (Supermarket, Small Grocery, etc.)
- **store_city**, **store_state**: Store location
- **store_sqft**: Store size
- **coffee_bar**, **video_store**, **salad_bar**: Store features

## 🛠️ Technology Stack

### Libraries & Tools
```python
import pandas as pd          # Data manipulation and analysis
import numpy as np           # Numerical computations
import matplotlib.pyplot as plt  # Data visualization
from IPython.core.interactiveshell import InteractiveShell  # Enhanced output display
```

### Development Environment
- **Language**: Python 3.11.0
- **IDE**: Jupyter Notebook
- **Data Format**: CSV files
- **Visualization**: Matplotlib

## 📈 Analysis Workflow

### 1. Data Loading & Exploration
```python
# Load all datasets
customer = pd.read_csv("data/customer.csv")
product = pd.read_csv("data/product.csv") 
product_class = pd.read_csv("data/product_class.csv")
region = pd.read_csv("data/region.csv")
sales = pd.read_csv("data/sales.csv")
store = pd.read_csv("data/store.csv")
time_by_day = pd.read_csv("data/time_by_day.csv")
```

### 2. Data Understanding
- **Customer Analysis**: Demographics, geographic distribution, purchasing behavior
- **Product Analysis**: Product categories, brands, pricing structures
- **Sales Analysis**: Transaction patterns, seasonal trends, store performance
- **Geographic Analysis**: Regional sales patterns and preferences

### 3. Market Basket Analysis Implementation
The analysis typically involves:
- **Association Rule Mining**: Identify frequently occurring item combinations
- **Support Calculation**: Measure how frequently itemsets appear
- **Confidence Analysis**: Determine the likelihood of purchasing item B given item A
- **Lift Calculation**: Measure the strength of association between items

## 🔧 Setup & Installation

### Prerequisites
```bash
pip install pandas numpy matplotlib jupyter
```

### Running the Analysis
1. Clone the repository
2. Ensure all CSV files are in the `data/` directory
3. Open `Market+Basket.ipynb` in Jupyter Notebook
4. Run all cells to execute the complete analysis

### Data Directory Structure
```
project/
├── data/
│   ├── customer.csv
│   ├── product.csv
│   ├── product_class.csv
│   ├── region.csv
│   ├── sales.csv
│   ├── store.csv
│   └── time_by_day.csv
└── MarketBasketAnalysis.ipynb
```

## 📊 Sample Data Insights

### Customer Demographics
- **Geographic Spread**: Customers from USA, Canada, and Mexico
- **Income Distribution**: Ranges from $10K to $90K+ brackets
- **Education Levels**: From Partial High School to Bachelor's Degree
- **Occupations**: Professional, Manual, Skilled Manual categories

### Product Portfolio
- **Brand Diversity**: Multiple brands including Washington products
- **Category Range**: From beverages to various food categories
- **Price Points**: Wide range from $0.74 to $3.64+ per item
- **Health Options**: Low-fat and recyclable package options available

### Store Network
- **Store Types**: Headquarters, Supermarkets, Small Grocery, Gourmet Supermarkets
- **Geographic Coverage**: Locations across North America
- **Store Features**: Coffee bars, salad bars, prepared food sections
- **Size Variation**: From small grocery stores to large supermarkets

## 🎯 Business Applications

### Retail Strategy Optimization
- **Product Placement**: Position frequently bought-together items nearby
- **Inventory Management**: Optimize stock levels based on association patterns
- **Promotional Planning**: Create effective bundle offers and discounts
- **Category Management**: Reorganize product categories for better customer flow

### Marketing Insights
- **Cross-selling Opportunities**: Recommend complementary products
- **Customer Segmentation**: Target specific customer groups with relevant offers
- **Seasonal Planning**: Identify seasonal buying patterns
- **Regional Preferences**: Adapt product mix to regional preferences

## 📈 Expected Outcomes

The Market Basket Analysis will reveal:
- **Strong Associations**: Product pairs with high confidence and lift scores
- **Popular Baskets**: Most common product combinations
- **Customer Segments**: Different buying behaviors across demographics
- **Store Performance**: Variation in basket patterns across store types
- **Seasonal Trends**: Time-based purchasing patterns

## 🔍 Key Performance Indicators

### Association Metrics
- **Support**: Frequency of itemset occurrence
- **Confidence**: Conditional probability of purchasing items together  
- **Lift**: Measure of association strength (>1 indicates positive correlation)

### Business Metrics
- **Average Basket Size**: Number of items per transaction
- **Cross-sell Rate**: Percentage of customers buying multiple categories
- **Revenue Impact**: Sales increase from recommended associations

## 📝 Analysis Features

### Data Quality Management
- **Display Configuration**: Full dataframe display without truncation
- **Warning Management**: Filtered deprecation and general warnings
- **Multiple Output Support**: Enhanced cell output display

### Comprehensive Data Coverage
- **Multi-dimensional Analysis**: Customer, product, geographic, and temporal dimensions
- **Hierarchical Product Structure**: From product level to family categories
- **Complete Transaction Records**: Full sales transaction details

## 🚀 Future Enhancements

### Advanced Analytics
- **Sequential Pattern Mining**: Identify buying sequences over time
- **Customer Lifetime Value**: Predict long-term customer value
- **Recommendation Systems**: Build personalized product recommendations
- **Price Sensitivity Analysis**: Understand price impact on associations


