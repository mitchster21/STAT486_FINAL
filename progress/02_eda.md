# STAT 486 Project Data and EDA Checkpoint

**Team Members:** Mitchell Heaton, Sammi Hilton, Ella Walker

---

## 1. Research Question and Dataset Overview

**Research Question:** What listing characteristics most strongly predict the nightly price of an Airbnb in November in New York City?

Our dataset is the NYC Airbnb listings file sourced from [Inside Airbnb](http://insideairbnb.com/get-the-data/), a public platform that scrapes and publishes Airbnb listing data for transparency and research purposes. The scrape used here was collected in November 2025 and contains 36,353 listings across New York City's five boroughs, with 79 columns covering host attributes, property details, availability, pricing, and guest reviews.

Inside Airbnb publishes data under a [Creative Commons CC0 1.0 Universal license](https://creativecommons.org/publicdomain/zero/1.0/), making it freely available for analysis. The dataset contains no personally identifiable information (PII) beyond publicly listed host names and profile photos, which are already visible on Airbnb's platform. No ethical concerns are present; we are using publicly available, anonymized listing data for academic purposes.

---

## 2. Data Description and Variables

**Key variables used in this analysis:**

- `price` *(target)*: Nightly listing price in USD. Parsed from a string format (e.g., `$120.00`) to a float.
- `room_type`: Categorical — one of "Entire home/apt," "Private room," and "Shared room,."
- `bedrooms`: Number of bedrooms in the listing (float; some missing values).
- `neighbourhood_group_cleansed`: Borough (Manhattan, Brooklyn, Queens, Bronx, Staten Island).
- `accommodates`: Number of guests the listing can host.
- `latitude` / `longitude`: Geographic coordinates used for spatial analysis.
- `reviews`: Ranging from 1-5, the number of reviews per month for a given listing.

**Preprocessing steps completed:**

- Stripped `$` and `,` from `price` and cast to float.
- Removed listings with missing `price` values (36,353 to 21,415 usable price observations).
- Applied a log transformation to `price` (`log_price`) to reduce right skew caused by extreme luxury listings.
- Filtered to the bottom 95th percentile of prices for spatial mapping to reduce distortion from outliers.
- Missing values in `bedrooms` and `bathrooms` were noted but not yet imputed; these columns are handled on a per-analysis basis.

---

## 3. Summary Statistics

**Price (raw, n = 21,415):**

| Statistic | Value |
|-----------|-------|
| Mean | ~$184 |
| Std Dev | ~$240 |
| Min | $10 |
| 25th pct | $89 |
| Median | $135 |
| 75th pct | $210 |
| Max | $10,000+ |

The raw price distribution is heavily right-skewed, with a long tail driven by luxury listings. After applying a log transformation, the distribution becomes approximately normal, which is more appropriate for regression modeling.

**Bedrooms (n = 30,273):**

| Statistic | Value |
|-----------|-------|
| Mean | 1.39 |
| Std Dev | 0.95 |
| Median | 1.0 |
| Max | 16.0 |

**Room Type (n = 36,353):**

| Room Type | Count |
|-----------|-------|
| Entire home/apt | ~22,000 |
| Private room | ~12,000 |
| Shared room | ~300 |

Entire home/apt listings dominate the dataset. Price varies considerably across room types, with entire homes commanding substantially higher nightly rates than private or shared rooms. The number of bedrooms shows a moderate positive relationship with price, as expected. Larger properties tend to list at higher rates.

---

## 4. Visual Exploration

### Figure 1: Price by Room Type and Number of Bedrooms

The box plot reveals clear pricing patterns across room types and bedroom counts. Entire home/apt listings command the highest prices overall, with 3+ bedroom units showing the widest price range — medians around $300–$350 and upper whiskers stretching past $550, reflecting strong demand for larger full-unit rentals. Private rooms are considerably more affordable, with most bedroom categories clustering between $75–$200, though studios in private rooms show a surprisingly high median near $160 with notable upside variation. Shared rooms occupy an interesting middle ground, where larger units (2BR and 3+ BR) actually price comparably to entire home listings, likely because the cost is split among more guests. Across all room types, the 1 BR category tends to have the tightest interquartile ranges, suggesting more consistent and predictable pricing, while 3+ BR units show the most volatility regardless of room type — likely driven by location, amenities, and seasonal demand. Overall, bedroom count has a more dramatic effect on price within entire home/apt listings than in private or shared room contexts.

![Airbnb Prices by Room Type and Number of Bedrooms](STAT486_FINAL/demo/figures/Airbnb_Prices_by_Room_Type_and_Bedrooms.png)

---

### Figure 2: Reviews per Month by Room Type

Shared rooms show the highest variability in monthly reviews, while entire home/apt listings are the most consistent but tend to receive fewer reviews. Private and hotel rooms fall in between, with medians clustering below 1 review per month across all room types — suggesting that most listings, regardless of type, receive reviews relatively infrequently.

![Reviews per Month by Room Type](demo/figures/reviews_per_month_by_room_type.png)

---

### Figure 3: Geographic Price Map of NYC

The map indicates that Airbnb prices in Manhattan are higher than in other areas of New York City. Listings are sparse on Staten Island and in the outer areas of Queens, suggesting that visitors tend to prefer more urban neighborhoods. Manhattan’s status as the most expensive borough is an important factor to consider in our analysis. The color scale represents price in dollars per night.

![NYC Geographic Price Map of NYC](demo/figures/NYC_map_prices.png)

---

## 5. Challenges and Reflection

The most significant challenge so far has been dealing with the missingness in `price` — nearly 15,000 listings had no price listed, which is a substantial portion of the dataset. It's unclear whether these are inactive listings, pending approvals, or simply data gaps in the scrape. We chose to drop them for now, but this may introduce selection bias if inactive listings differ systematically from active ones.

We are also deciding how to handle `bedrooms` missingness (~6,000 missing values) before modeling. Simple imputation with the median is a likely approach, but we want to verify that missingness is random and not concentrated in a particular borough or room type before proceeding.

The last challenge we faced was that hotel prices were extremely skewed and may have been inaccurately recorded, reporting values $40,000 higher than the average prices, so we decided to drop `hotel` room type for now, to prevent dominating the model.

