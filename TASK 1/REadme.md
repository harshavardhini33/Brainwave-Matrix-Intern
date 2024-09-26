

# Amazon Sales Data Analysis

## Overview
This project analyzes the sales data from Amazon, focusing on key insights such as ratings, price ranges, and discount strategies for various products. Using Python libraries such as Pandas, Matplotlib, and Seaborn, we cleaned and visualized the data to uncover important trends and patterns.

## Dataset Description
The dataset (`amazon.csv`) contains information on products sold on Amazon, including:
- **Product Name**: Name of the product.
- **Discounted Price**: The current price after discounts.
- **Actual Price**: The original price of the product.
- **Discount Percentage**: The discount offered on the product.
- **Rating**: User ratings for the product.

## Data Preprocessing
- **Price Cleaning**: Removed `₹` symbols and commas from `discounted_price` and `actual_price` columns, then converted them to numeric format.
- **Discount Cleaning**: Cleaned the `discount_percentage` column by removing the `%` symbol.
- **Rating Cleaning**: Converted the `rating` column to numeric values for analysis.

## Exploratory Data Analysis (EDA)
The exploratory analysis focuses on understanding the price distribution, top-rated products, discount strategies, and rating distribution through various visualizations.

### 1. Top Rated Products
Type: **Textual Summary**
- Displays the top 5 products with the highest ratings.

```python
top_rated_products = sales_data[['product_name', 'rating', 'discounted_price']].sort_values(by='rating', ascending=False).head(5)
print(top_rated_products)
```

### 2. Price Range Analysis
Type: **Histogram & KDE Plot**
- Visualizes the distribution of discounted prices across all products.

```python
plt.figure(figsize=(12, 6))
sns.histplot(sales_data['discounted_price'].dropna(), bins=30, kde=True, color='blue')
plt.xlabel('Discounted Price (₹)')
plt.ylabel('Frequency')
plt.title('Price Range Distribution (Histogram & KDE)')
plt.xlim(0, sales_data['discounted_price'].quantile(0.95))  # Zoom into the 95th percentile
plt.show()
```

### 3. Discount Percentage Distribution
Type: **Histogram**
- Shows the distribution of discount percentages offered across all products.

```python
plt.figure(figsize=(10, 6))
plt.hist(sales_data['discount_percentage'].dropna(), bins=20, color='green')
plt.xlabel('Discount Percentage')
plt.ylabel('Frequency')
plt.title('Distribution of Discount Percentages')
plt.tight_layout()
plt.show()
```

### 4. Rating Distribution
Type: **Bar Chart**
- Illustrates the distribution of ratings given by customers for the products.

```python
plt.figure(figsize=(10, 6))
sns.countplot(x='rating', data=sales_data, palette='Set2')
plt.xlabel('Rating')
plt.ylabel('Number of Products')
plt.title('Rating Distribution')
plt.tight_layout()
plt.show()
```

## Key Insights
- **Top Rated Products**: The top-rated products give insight into customer satisfaction and popularity.
- **Price Range**: Most products fall within a specific price range, providing a clear understanding of the overall pricing strategy.
- **Discount Strategy**: The discount distribution shows how often and by how much products are discounted.
- **Rating Analysis**: The distribution of ratings gives a clear view of how customers perceive the product quality.

## Installation and Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/amazon-sales-data-analysis.git
   cd amazon-sales-data-analysis
   ```

2. Install the required dependencies:
   ```bash
   pip install pandas matplotlib seaborn
   ```

3. Place your dataset (`amazon.csv`) in the root directory.

4. Run the analysis:
   ```bash
   python analysis.py
   ```

## Data Columns
- **product_name**: Name of the product.
- **discounted_price**: The price after the discount (cleaned of ₹ symbol).
- **actual_price**: The original price of the product.
- **discount_percentage**: The percentage discount applied to the product.
- **rating**: The product's average user rating.

## Visualizations
1. **Top Rated Products**: Textual summary of the highest-rated products.
2. **Price Range**: Histogram and KDE plot showing the distribution of discounted prices.
3. **Discount Distribution**: Histogram of discount percentages.
4. **Rating Distribution**: Bar chart representing the distribution of ratings.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request for any enhancements or bug fixes.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

