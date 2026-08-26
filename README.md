# Seattle Airbnb Listings Analysis using Tableau

## Overview
This project involves an exploratory analysis of Seattle Airbnb listings and calendar data using Tableau. The goal is to visualize pricing patterns, availability, and listing characteristics across the city. The following README provides a detailed account of the project's objectives, data, dashboard views, findings, and conclusions.

## Live Dashboard
View the interactive dashboard on Tableau Public:
[AirBnB Project Dashboard](https://public.tableau.com/app/profile/ankur.kumar.jha/viz/AirBnBprojectTableau/Dashboard1)

## Objectives
- Analyze average nightly price by zip code and visualize it geographically.
- Track how total listing price varies over the course of a year.
- Understand how price scales with the number of bedrooms.
- Explore how listings are distributed across bedroom counts.
- Build a set of Tableau worksheets that together give a full picture of the Seattle short-term rental market.

## Dataset
The data is sourced from the Inside Airbnb Seattle listings dataset, joined with daily calendar data (price and availability by date). The combined extract contains approximately 1,048,575 calendar-day rows covering 2,873 unique listings, spanning from January 2016 to January 2017, with 96 fields including:

`id`, `name`, `host_id`, `host_since`, `neighbourhood`, `city`, `zipcode`, `latitude`, `longitude`, `property_type`, `room_type`, `accommodates`, `bathrooms`, `bedrooms`, `beds`, `price`, `date`, `available`, `minimum_nights`, `maximum_nights`, `number_of_reviews`, `review_scores_rating`, and related host, review, and policy fields.

All listings are located in the Seattle, Washington area (Ballard, Phinney Ridge, West Seattle, and other neighborhoods), United States.

The workbook (`.twbx`) is a self-contained Tableau packaged file, bundling both the workbook and the underlying data extract (`.hyper`), so it can be opened directly in Tableau Desktop or Tableau Reader without needing a separate data connection.

## Dashboard Views (Worksheets)

### 1. Average Price by Zip Code
Rows: `AVG(price)` · Columns: `zipcode`

A bar chart showing the average nightly price for each Seattle zip code.

**Objective:** Identify which areas of the city command the highest and lowest average nightly rates. Zip code 98134 (SoDo/Industrial District) and 98101 (Downtown) had the highest average prices, both above $200/night.

### 2. Price by Location (Map)
Rows: `Latitude (generated)` · Columns: `Longitude (generated)` · Mark type: Filled Map (Multipolygon)

A geographic map of Seattle with zip code regions shaded by average price.

**Objective:** Visualize pricing patterns spatially, making it easy to spot high-cost pockets near downtown and the waterfront versus more affordable outer neighborhoods.

### 3. Total Price Over Time
Rows: `SUM(price)` · Columns: `date`

A time series showing total calendar price across all listings by date, covering January 2016 through January 2017.

**Objective:** Reveal seasonal demand and pricing trends throughout the year, useful for spotting peak travel periods.

### 4. Average Price by Number of Bedrooms
Rows: `AVG(price)` · Columns: `bedrooms`

| Bedrooms | Avg. Price | Listings |
|----------|------------|----------|
| 0 (Studio) | $114 | 288 |
| 1 | $102 | 1,811 |
| 2 | $201 | 483 |
| 3 | $291 | 206 |
| 4 | $335 | 55 |
| 5 | $563 | 20 |
| 6 | $661 | 5 |

**Objective:** Quantify how strongly bedroom count drives price. Price scales roughly linearly with bedroom count, with a sharp jump for listings with 5 or more bedrooms.

### 5. Listing Count by Number of Bedrooms
Rows: `bedrooms` · Values: `Distinct Count of id`

**Objective:** Show the composition of the market by unit size. One-bedroom listings dominate the inventory (over 60% of all listings), followed by studios and two-bedroom units.

## Additional Findings
- **Room Type Pricing:** Entire homes/apartments average $176/night, private rooms average $79/night, and shared rooms average $49/night.
- **Market Composition:** The Seattle market is overwhelmingly made up of entire home/apartment listings (around 68% of all listings), followed by private rooms (around 30%).
- **Price Range:** Nightly prices in the dataset range from $10 to $1,650, with an overall average of about $140.

## Findings and Conclusion
- **Location matters:** Downtown and near-downtown zip codes command the highest average nightly prices, while outer neighborhoods are more affordable.
- **Size drives price:** Price increases steadily with bedroom count, and listings with 5+ bedrooms carry a significant premium, likely reflecting whole-house rentals for larger groups.
- **Inventory is skewed toward smaller units:** Most listings are studios or one-bedroom units, suggesting the market is geared primarily toward solo travelers and couples rather than large groups.
- **Seasonality exists:** Total pricing activity fluctuates across the year, which can inform when hosts might adjust rates or when travelers can find better deals.

This analysis provides a clear picture of how location, size, and room type shape Airbnb pricing in Seattle, and can help hosts benchmark their pricing and help travelers understand what drives cost across the city.

## Data Source
The raw dataset is not included in this repository due to its size (~45MB). It is sourced from Inside Airbnb's public Seattle listings and calendar data, available at [insideairbnb.com/get-the-data](http://insideairbnb.com/get-the-data/). The full dataset is already packaged inside the `.twbx` file (via its bundled `.hyper` extract), so no separate download is needed to open and explore the workbook.

## How to Open
1. Download `AirBnB_project_Tableau.twbx`.
2. Open it in [Tableau Desktop](https://www.tableau.com/products/desktop) or the free [Tableau Reader](https://www.tableau.com/products/reader).
3. No additional data setup is required, the data extract is packaged inside the `.twbx` file.
