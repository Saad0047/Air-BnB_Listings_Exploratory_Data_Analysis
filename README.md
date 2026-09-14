# NYC Airbnb Listings — Exploratory Data Analysis

An exploratory data analysis of NYC Airbnb Open Data, investigating what drives price differences across listings and how listings vary by neighbourhood, room type, and availability.

## Key Question

**What drives price differences across listings in NYC Airbnb data?**

## Dataset

The dataset contains NYC Airbnb listings with details on:
- Location (`neighbourhood_group`, `latitude`, `longitude`)
- Pricing (`price`, `minimum_nights`)
- Listing type (`room_type`, `beds`)
- Engagement (`number_of_reviews`, `reviews_per_month`, `availability_365`)

> Source: [Kaggle — NYC Airbnb Open Data](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)

## What This Notebook Covers

1. **Dataset Overview** — shape, structure, and statistical summary of the raw data
2. **Data Cleaning** — handling missing values, duplicates, and type inconsistencies (`id`, `host_id` cast to `object`)
3. **Outlier Handling** — removing extreme price outliers (listings >$1,700/night) that distorted the initial distribution
4. **Univariate Analysis** — distribution of price and availability
5. **Feature Engineering** — derived `price_per_bed` (with zero-bed edge case handled)
6. **Bivariate & Multivariate Analysis**:
   - Average price by neighbourhood group
   - Price by neighbourhood group and room type
   - Price vs. number of reviews
   - Pairwise relationships across price, reviews, and availability by room type
   - Correlation matrix across all numeric features

## Key Findings

Three that hold up across the plots:

1. **Price is heavily right-skewed, and availability is bimodal.** Most listings sit under $250/night with a long tail of expensive outliers (Image 1, left). Availability splits into two extremes — a large cluster of listings almost never available (near 0 days) and an even larger cluster available almost year-round (near 350-365 days), with relatively few in between (Image 1, right).

2. **Location within NYC is a stronger price driver than room type alone.** Manhattan has the highest average price across every room type — especially Entire home/apt and Hotel room, both averaging $240-300+ — while Bronx and Staten Island are consistently the cheapest across the board (Image 2, left).

3. **Price barely correlates with reviews, minimum nights, or geographic coordinates.** The correlation matrix shows all of these near 0 with price; the only meaningful positive correlation is with `beds` (0.41) (Image 4). The scatterplot backs this up — listings with high review counts cluster at low prices, while the priciest listings tend to have very few reviews (Image 2, right), so popularity and price move independently, if not slightly opposite.

## Tools Used

| Tool | Purpose |
|------|---------|
| `pandas` | Data loading, cleaning, aggregation |
| `numpy` | Numeric operations, handling edge cases (e.g. division by zero) |
| `matplotlib` | Custom plot layout and figure control |
| `seaborn` | Statistical visualizations (boxplot, histplot, barplot, scatterplot, pairplot, heatmap) |

## Project Structure

```
├── analysis.ipynb        # Main EDA notebook
├── datasets.csv           # Raw dataset (not included — see Setup)
└── README.md              # This file
```

## Setup

1. Clone the repository
   ```bash
   git clone https://github.com/Saad0047/<repo-name>.git
   cd <repo-name>
   ```
2. Install dependencies
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```
3. Download the dataset from Kaggle and place it in the project root as `datasets.csv`
4. Launch the notebook
   ```bash
   jupyter notebook analysis.ipynb
   ```

## Author

**Saad** — Software Engineering student, self-taught in Python and ML
GitHub: [@Saad0047](https://github.com/Saad0047)

*This project is part of a self-directed AI/ML learning journey, focused on building EDA fundamentals before moving into deep learning and computer vision.*
