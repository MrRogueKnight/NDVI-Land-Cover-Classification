# 🌿 NDVI-based Land Cover Classification – Summer Analytics 2025 Hackathon

This repository contains my submission for the **Summer Analytics 2025 Mid Hackathon**, hosted by the **Consulting & Analytics Club (CAC), IIT Guwahati**, in collaboration with **GeeksforGeeks (GFG)**. The challenge focused on building a **Logistic Regression** model to classify land cover types using time-series NDVI (Normalized Difference Vegetation Index) data derived from satellite imagery.

---

## 🧠 Problem Statement

Participants were provided with NDVI time-series data (27 timestamps) for various land patches and asked to classify each sample into one of the following six land cover classes:

- `Water`
- `Impervious`
- `Farm`
- `Forest`
- `Grass`
- `Orchard`

### Constraints:
- **Only Logistic Regression was allowed**
- Evaluation was based on **Accuracy Score**
- Dataset contained significant **noise** (e.g., due to cloud cover)

---

## 🏆 Competition Results

| Metric                 | Value        |
|------------------------|--------------|
| 🧑‍🤝‍🧑 Entrants            | 1,942        |
| 🧑 Participants         | 1,395        |
| 🧠 Teams                | 1,395        |
| 📤 Total Submissions   | 6,504        |
| 📊 Public Leaderboard  | **Rank 56 / 1,395** |
| 🔐 Private Leaderboard | **Rank 192 / 1,395** |
| 🏅 Awards              | Kudos        |
| 📛 Rated Competition?  | No – Not eligible for medals/points |

---

## 📁 Dataset Description

The dataset consists of two files:

- `hacktrain.csv`: Training data (noisy NDVI values and ground truth)
- `hacktest.csv`: Test data (used for public/private leaderboard)

Each sample contains:
- `ID`: Unique identifier
- 27 NDVI values (e.g., `20150720_N`)
- `class`: Land cover label (train only)

🧪 **Note:** The test set is a mix of:
- **89% noisy** samples → used for **public leaderboard**
- **11% clean** samples → used for **private leaderboard**

---

## 🧪 My Approach

### 1. 🔧 Preprocessing

- **Missing Values**:
  - Filled using **median imputation** across each column.
- **Outlier Handling**:
  - Removed extreme NDVI values using IQR filtering (likely cloud artifacts).
- **Feature Engineering**:
  - Computed statistical aggregates:
    - `mean`, `std`, `min`, `max`, `skew`, `kurtosis`
  - Seasonal pattern extraction:
    - Early-season vs. late-season NDVI mean
  - Other signals:
    - Count of NDVI values below 0 (possible non-vegetated land)
    - NDVI change metrics (max - min)

### 2. ⚙️ Model Training

- **Model Used**: Logistic Regression (`One-vs-Rest`)
- **Library**: `scikit-learn`
- **Regularization**: L2 (Ridge penalty)
- **Scaler**: StandardScaler
- **Validation**:
  - Used 5-fold stratified cross-validation on training data
  - Tracked mean accuracy and standard deviation

### 3. 📤 Prediction & Submission

- Final model trained on full training set
- Predictions made on test set
- Created `submission.csv` with format:

```csv
ID,class
1,water
2,impervious
3,grass
...

# Instructions

---

# 🌿 Summer Analytics 2025 Hackathon: NDVI-based Land Cover Classification

Welcome to the **First Course Hackathon of Summer Analytics 2025**, organized by the **Consulting & Analytics Club** in collaboration with **GeeksforGeeks (GFG)**. In this challenge, you'll develop a machine learning model to classify land cover types using **NDVI (Normalized Difference Vegetation Index) time-series data** derived from satellite imagery and **OpenStreetMap (OSM)** annotations.

🔗 **[Hackathon Link (Kaggle)](https://www.kaggle.com/competitions/summer-analytics-mid-hackathon/overview)**

🎁 **Prizes**: Top performers will receive **GFG Premium memberships**, and all participants are eligible for **exclusive discounts**!

---

## 🎯 Problem Statement

You are tasked with building a **Logistic Regression model** that classifies land cover types based on noisy NDVI data. Despite imperfections in the data, your model should generalize well—particularly to the clean, unseen test subset.

---

## 🌱 What is NDVI?

**NDVI (Normalized Difference Vegetation Index)** is a remote sensing index used to monitor vegetation health. It is calculated as:

$$
\text{NDVI} = \frac{\text{NIR} - \text{RED}}{\text{NIR} + \text{RED}}
$$

Where:

* **NIR**: Near-Infrared Reflectance
* **RED**: Red Reflectance

High NDVI values typically indicate healthy vegetation, while low or negative values may indicate water, barren land, or impervious surfaces.

---

## 🗂️ Dataset Description

Each row in the dataset includes:

* **`ID`**: A unique identifier for each sample
* **`class`**: Ground truth land cover label (`{Water, Impervious, Farm, Forest, Grass, Orchard}`)
* **27 NDVI Time Points**: Columns like `20150720_N`, `20150602_N`, representing NDVI values over time

### 📁 Files Provided

* `hacktrain.csv`: Training dataset (contains noise due to cloud cover and digitization errors)
* `hacktest.csv`: Test dataset (89% noisy, 11% clean — used for private leaderboard evaluation)

📥 **Download Command (Kaggle CLI):**

```bash
kaggle competitions download -c summer-analytics-mid-hackathon
```

> *Ensure you’ve set up the Kaggle API correctly.*

---

## ⚙️ Model Requirements & Evaluation

### ✅ Model Constraints

* Use **Logistic Regression only**
* Multiclass classification setup

### 🧪 Preprocessing Encouraged

* **Denoising**: Filter out NDVI outliers caused by cloud cover
* **Missing Value Handling**: Impute missing NDVI values
* **Feature Engineering**: Extract seasonal patterns, trends, or aggregate statistics

### 📊 Evaluation Metric

* **Accuracy Score**

### 🏆 Leaderboards

* **Public Leaderboard**: Based on 89% noisy test data
* **Private Leaderboard**: Based on the clean 11% — final rankings depend on this!

---

## 📝 Submission Guidelines

Your final submission should be a `.csv` file with:

* `ID`
* `class`

**Example:**

```csv
ID,class
1,water
2,water
3,grass
4,impervious
...
```

### 🚨 Rules

* Only two submissions will be evaluated for final scoring
* The **best private leaderboard score** among your submissions determines your rank

---

## 🙌 Final Notes

* Stay focused on building a robust model that **generalizes well**, not just one that scores high on noisy data.
* Engage with the [Kaggle Discussion Tab](https://www.kaggle.com/competitions/summer-analytics-mid-hackathon/discussion) for help and updates.

Good luck, and happy hacking! 🍀

---
