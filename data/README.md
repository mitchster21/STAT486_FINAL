# Data Access Instructions (November 2025 Archive)

To keep the repository lightweight, the raw dataset files are not tracked by Git. Because this project focus on a specific holiday snapshot, you must download the **November 2025 archived data**.

## 1. Download the Data
1. Go to [Inside Airbnb: Get the Data](https://insideairbnb.com/get-the-data/).
2. Scroll down to the **New York City, New York, United States** section.
3. Look for the **Archived Data** subsection within NYC.
4. Locate the dataset dated **November 2025** (or the closest date in Nov 2025).
5. Download the following files:
   * **listings.csv.gz** (Detailed Listings Data)
   * **reviews.csv.gz** (Detailed Review Data - *Optional*)

## 2. Setup
1. Unzip the downloaded `.gz` files.
2. Place the resulting `.csv` files directly into this `/data` folder.
3. **Important:** Ensure the filenames are exactly `listings.csv` and `reviews.csv`.

## 3. Data Dictionary
A full description of the columns in these files can be found on the [Inside Airbnb website](https://insideairbnb.com/behind-the-data/). 

Key columns for the November 2025 analysis include:
* `price`: Target variable (nightly cost).
* `latitude`/`longitude`: Primary features for K-Means geographic clustering.
* `amenities`: Text-based list of features for feature engineering.
* `neighbourhood_group_cleansed`: Used for borough-based comparison.