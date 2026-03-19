# STAT 486 Project Proposal: New York City Airbnb Analysis (Nov 2025)

**Team Members:** Mitchell Heaton, Sammi Hilton, Ella Walker

---

## 1. AI-Generated Project Ideas
To satisfy the course requirement of combining supervised learning with another ML technique, the following three ideas were generated using generative AI (Gemini 3 Flash) based on the "Inside Airbnb" NYC dataset:

* **Idea 1: Price Prediction & Market Segmentation (Selected)**
    * **Supervised:** Predict nightly rental prices using listing features (amenities, bathrooms, bedrooms, etc.).
    * **Additional Technique (Clustering):** Use K-Means to group listings into "Market Segments" (e.g., Luxury, Budget-Friendly, Business-Travel) to see if price prediction accuracy improves when models are trained on specific clusters.
* **Idea 2: Review Sentiment & Rating Classification**
    * **Supervised:** Classify listings as "High Rated" or "Low Rated" based on amenities and price.
    * **Additional Technique (NLP/Sentiment Analysis):** Extract sentiment scores from the `reviews.csv` file to determine if host hospitality is a stronger predictor of price than physical location.
* **Idea 3: Detecting Pricing Anomalies & Scams**
    * **Supervised:** Build a regression model to estimate the "fair market value" of a listing.
    * **Additional Technique (Anomaly Detection):** Use Isolation Forests to identify listings where the price is significantly higher or lower than the predicted value, potentially flagging data entry errors or "bait-and-switch" listings.

---

## 2. AI Reflection & Exchange

**AI Influence Note:**
Generative AI was instrumental in helping our team move beyond a simple "linear regression" mindset. Initially, we focused only on predicting price, but the AI suggested that price is heavily dependent on the *type* of listing (Cluster), which often crosses traditional borough boundaries. This led us to include unsupervised clustering as a pre-processing step to create more specialized models. The AI also helped identify specific columns in the Inside Airbnb dataset, like `amenities`, that would require significant feature engineering before they could be used in a supervised model. Using AI as a collaborator allowed us to increase the technical depth of our project while ensuring the scope remained manageable for a single semester.

**AI Exchange Excerpt:**
> **User:** "I want to use Inside Airbnb for a housing project. How can I add a second ML technique beyond just regression?"  
> **AI:** "Since Airbnb listings vary wildly in quality, you could use **Clustering** first. Group the listings into segments like 'Luxury Suites' or 'Budget Rooms' based on their amenities and location. Then, run separate supervised regression models on each cluster. This usually results in higher accuracy than a one-size-fits-all model."

---

## 3. Project Details

### **Final Research Question**
How accurately can we predict nightly Airbnb prices in **New York City during the November 2025 holiday season** using property characteristics, and how does the accuracy vary when listings are first segmented into unsupervised "Market Clusters" compared to traditional borough-based groupings?

### **Candidate Target Variable**
The target variable for the supervised analysis will be **price per night**, which will be predicted using listing features such as number of bathrooms, bedrooms, and available amenities to understand how these characteristics influence pricing.

### **Dataset Choice & Backup**
* **Primary Dataset:** The primary dataset for this project will be sourced from [Inside Airbnb](https://insideairbnb.com/get-the-data/), which provides detailed data on listings in New York City. We will focus specifically on the **November 2025 dataset**, as it includes complete and reliable price information needed for our analysis, while more recent months have missing or incomplete price variables. November is also a particularly relevant time period to study due to increased tourism associated with Thanksgiving, including major events such as the Macy's Thanksgiving Day Parade, which may influence Airbnb pricing patterns across different neighborhoods.
* **Backup Dataset:** To ensure the project can still be completed if issues arise, a backup dataset from [Kaggle (New York Airbnb dataset)](https://www.kaggle.com/datasets/vrindakallu/new-york-dataset) will be used as an alternative.

---

## 4. Feasibility, Ethics, and Methodology

### **Feasibility (Time, Compute, Scope)**
This project is highly feasible as it utilizes a **cross-sectional "market snapshot"** of November 2025. By focusing on a single month, we eliminate the complexity of seasonal time-series fluctuations while maintaining a robust sample size of ~40,000 listings. The supervised learning component (XGBoost/Random Forest) and the clustering step (K-Means) are computationally efficient and can be implemented using standard Python libraries on local hardware.

### **Ethical & Legal Considerations**
This project uses publicly available data from Airbnb listings, which minimizes privacy concerns since no sensitive personal information is included. However, ethical considerations still apply. For example, the model could unintentionally reinforce existing socioeconomic or geographic biases (e.g., higher predicted prices in wealthier neighborhoods), so results should be interpreted carefully and not used to justify inequities. Additionally, care should be taken not to misrepresent findings in a way that could impact hosts or renters unfairly. From a legal perspective, the dataset must be used in accordance with the terms provided by Inside Airbnb.

### **Planned Additional ML Methods**
In addition to the supervised learning approach for price prediction, this project will incorporate **K-Means clustering** as an unsupervised learning technique. The goal of clustering is to group Airbnb listings into distinct “market segments” based on features such as location, amenities, property type, and accommodates. After forming clusters, we will evaluate whether training separate predictive models within each cluster improves overall accuracy (RMSE) compared to a single global model for the entire city.

---

## 5. Minimum Evidence Checklist
- [x] `progress/01_proposal.md` exists
- [x] 2-3 AI-generated ideas included
- [x] AI reflection and excerpt included
- [x] Final question (specified for Nov 2025) and target variable included
- [x] Dataset choice (Nov 2025 snapshot) and backup dataset included