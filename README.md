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
