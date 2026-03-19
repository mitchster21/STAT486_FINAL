# NYC Airbnb Price Optimization & Market Analysis (Nov 2025)

## Project Overview
This project analyzes the short-term rental market in **New York City** using a high-resolution snapshot from **November 2025** provided by Inside Airbnb. Our primary goal is to build a hybrid machine learning pipeline that combines **unsupervised clustering** to segment the diverse NYC market and **supervised regression** to predict optimal nightly prices during the peak holiday transition period.

By identifying "market micro-segments" across the five boroughs (Manhattan, Brooklyn, Queens, The Bronx, and Staten Island), we aim to provide hosts with highly localized pricing recommendations that account for holiday-specific demand drivers, such as Thanksgiving festivities and the Macy's Day Parade.

---

## The Team
* **Sammi Hilton** — [wella2@byu.edu](mailto:wella2@byu.edu) | [@Sammi02](https://github.com/Sammi02)
* **Ella Walker** — [rasbands@byu.edu](mailto:rasbands@byu.edu) | [@ella-walker](https://github.com/ella-walker)
* **Mitch Heaton** — [mheat21@byu.edu](mailto:mheat21@byu.edu) | [@mitchster21](https://github.com/mitchster21)

---

## Research Question
> **How accurately can we predict nightly Airbnb prices in NYC during the November 2025 holiday season by first segmenting listings into unsupervised "Market Clusters" compared to traditional borough-based grouping?**

Furthermore, we will investigate which features (such as *specific amenities, host "Superhost" status, or proximity to transit*) drive the highest price premiums within each identified cluster during this unique tourism window.

---

## Data Source
We utilize publicly available data from [Inside Airbnb](https://insideairbnb.com/get-the-data/).
* **Location:** New York City, NY
* **Snapshot Date:** November 2025
* **Primary File:** `listings.csv` (Detailed data on ~40,000+ active listings)
* **Secondary File:** `reviews.csv` (Used for sentiment analysis and trend tracking)

---

## Technical Approach
This project utilizes a two-stage Machine Learning approach:
1.  **Unsupervised Learning (K-Means Clustering):** We will cluster listings based on latitude, longitude, price, and amenity density to find distinct market segments (e.g., Luxury lofts, Budget rooms, Business-Travel suites).
2.  **Supervised Learning (XGBoost/Random Forest):** We will train regression models on these clusters to predict the `price` target variable with high precision, leveraging the segmented data to minimize error.

---

## Project Roadmap
- [ ] **Phase 1: Data Cleaning & EDA**
    - Handle missing values, convert currency strings to floats, and visualize price distribution across NYC boroughs for the November period.
- [ ] **Phase 2: Feature Engineering**
    - One-hot encode the five boroughs.
    - Parse the `amenities` string into a binary matrix (e.g., "Has Wifi", "Has Elevator").
- [ ] **Phase 3: Market Clustering**
    - Implement K-Means to identify 4–6 distinct NYC market types that may cross traditional borough lines.
- [ ] **Phase 4: Predictive Modeling**
    - Train and tune XGBoost and Random Forest models on clustered data subsets.
- [ ] **Phase 5: Evaluation & Deployment**
    - Compare RMSE across clusters and visualize feature importance (e.g., identifying the "Thanksgiving Premium").

---

### **Quick Note on Setup**
To avoid repository bloat, the raw data files are not uploaded to GitHub. Please refer to the [data/README.md](./data/README.md) for instructions on how to download the November 2025 NYC `listings.csv` and where to place it in your local directory.