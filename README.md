# Bengaluru House Price Analysis

Exploratory data analysis of Bengaluru house listings using Python (pandas, matplotlib) and SQL (SQLite). The goal was to find out which areas are priciest and cheapest, and what drives price.

**Notebook:** `housing_analysis.ipynb`
**Data:** [Bengaluru House Price Data (Kaggle)](https://www.kaggle.com/datasets/amitabhajoy/bengaluru-house-price-data), 13,320 listings, 9 columns

## Data cleaning
Cleaned 13,320 rows down to 10,198:
- Dropped `society` and `balcony` (too many missing values / not needed)
- Removed rows with other missing values
- Converted `size` (e.g. "2 BHK") to a numeric `bhk` column
- Converted `total_sqft` ranges to their average and dropped rows with other units (e.g. Sq. Meter, Perch)
- Grouped locations with 10 or fewer listings as "other"
- Removed unrealistic homes (under 300 sqft per bedroom, bathrooms 2+ more than bedrooms)
- Removed price-per-sqft outliers within each location (beyond 1 standard deviation)

## Key findings
1. **Price per sqft varies about 5x across areas.** Among areas with 30+ listings, Rajaji Nagar is priciest (₹13,943/sqft) and Chandapura is cheapest (₹2,764/sqft).
2. **Small samples can mislead.** Areas like Cunningham Road topped my first chart (about ₹20,000/sqft) but have fewer than 30 listings, so I excluded them from the final ranking.
3. **Price rises sharply with bedrooms up to 4 BHK:** average ₹37L (1 BHK), ₹59L (2), ₹102L (3), ₹220L (4). 5 and 6 BHK (₹227L) have much less data (104 and 57 listings), so I don't treat them as a trend.
4. **Ready-to-move vs under construction makes almost no difference:** median ₹5,152 vs ₹5,215 per sqft.
5. **Plot Area listings cost more per sqft:** median ₹6,500 vs ₹5,088 for Super built-up (about 28% higher).
6. **Uttarahalli** averages ₹4,064/sqft across 168 listings, about 28% below the city average of ₹5,637.

## Tools
Python, pandas, matplotlib, SQLite, Google Colab

## Limitations
- Data is from listings, not final sale prices
- Averages can still be affected by remaining outliers
- This shows patterns, not causes

## How to run
Download the CSV from Kaggle, upload it to Google Colab, update `file_path` in the first cell, and run all cells.

Built by Rishika | [GitHub](https://github.com/rishika182)
