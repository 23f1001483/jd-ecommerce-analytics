# Analysing Delivery Reliability, Promotion Effectiveness, and Loyalty Programme Value for a Large E-Commerce Retailer

## 📌 Project Overview
This repository contains a descriptive data analytics project evaluating the operational and commercial efficiency of **JD.com**, one of the world's largest e-commerce retailers. The analysis investigates three critical business pillars to uncover bottlenecks and value drivers:
1. **Fulfillment Performance:** Measuring delivery promise reliability and isolating transit bottlenecks.
2. **Promotion Effectiveness:** Comparing different discount mechanisms to identify which drive higher purchase volumes.
3. **Loyalty Programme Value:** Benchmarking the spending habits of premium paid members (PLUS) against ordinary customers.

This project was completed as a **BDM Capstone Project** for the IIT Madras Online BS Degree Program.

---

## 📊 Dataset & Source
The project utilizes secondary transaction-level data released by JD.com for the **2020 MSOM Data-Driven Research Challenge**.
* **Data Scale:** ~550,000 (5.5 lakh) order-SKU records spanning March 2018 across a specific consumable category.
* **Architecture:** 5 relational tables (Orders, Delivery, Users, Distribution Network, and SKUs).
* **Data Source:** [Hugging Face Datasets Mirror](https://huggingface.co)

---

## 🛠️ Tech Stack & Methodology
* **Data Profiling & ETL:** **Power Query** (Power BI) was used to clean text grains, apply outlier rules (e.g., filtering out negative prices and severe delivery delays >168 hours), join relational data tables, and derive specific columns like `CrossRegion`, `Revenue`, and `delivery_hours`.
* **Analysis & Visualization:** **Power BI** and **Google Sheets** for grouped aggregates, pivot tables, summary counts, and distribution charts.
* **Approach:** Strictly **diagnostic and descriptive analytics**, focusing on historical patterns and operational snapshots rather than predictive cause-and-effect modeling.

---

## 🔍 Key Findings

### 1. Delivery & Fulfillment Performance
* **The Benchmark:** Overall promise achievement stood at **84.9%** across known-promise orders.
* **The Route Gap:** Surprisingly, long-distance **Cross-DC routing achieved a higher on-time delivery rate (88.9%)** compared to local warehouse fulfillment (82.4%). 
* **The Bottleneck:** Cross-DC orders add an extra **17.1 hours (a 64% surge)** in overall delivery time. Decomposing these time stamps revealed that the delay occurs almost entirely during **post-dispatch transit**, not warehouse handling.
* **Weakest Links:** Local promise failures are heavily clustered in **Regions 9 and 4**, which together account for 43% of all local delayed orders.

### 2. Promotion Mechanism Effectiveness
* **Volume Drivers:** Volume-linked promotions (**Quantity and Bundle discounts**) correlated with the largest basket sizes, averaging **1.40 and 1.39 units** per order respectively.
* **Underperforming High-Use Offers:** The single most heavily used mechanism—**Direct Discounts**—averaged only **1.11 units**, dropping *below* the baseline of orders containing no discount at all (1.17 units).
* **Depth Threshold:** Increasing discount depth didn't yield a gradual increase in units; instead, it acted like a threshold, only spiking volume significantly once discounts crossed the **40%+ markdown mark**.

### 3. Loyalty (PLUS Membership) Customer Value
* **Spend Premium:** Paid PLUS membership records carried a clear premium, averaging **111.11 dataset currency units** in spend compared to **97.48 units** for ordinary accounts (~14% higher).
* **Baskets vs. Margins:** PLUS members buy about 5.4% more units per transaction, meaning their higher spend is influenced heavily by premium product selection or higher unit prices.
* **Geographic Concentration:** PLUS activity heavily clusters in **City Level 1 (28.5% share)**, scaling down rapidly as you move toward lower-tier cities.

---

## 💡 Business Recommendations

### Operational Action Plan

| Focus Area | Immediate Action | Primary KPI | Expected Benefit |
| :--- | :--- | :--- | :--- |
| **1. Fulfillment** | 30-Day local transit audit in Regions 9 & 4 | On-Time Delivery % & Transit Hours | Locates and isolates controllable delay |
| **2. Promotions** | Run matched-SKU AB test (Direct vs. Quantity) | Incremental Contribution Margin | Tests promotional efficiency & spend waste |
| **3. Loyalty** | Audit unit economics before Tier 5 expansion | Conversion, Renewal, & Customer ROI | Tests viability of targeted growth |

### Core Strategic Takeaways:
1. **Fix Local Deliveries First:** Prioritize auditing station hand-offs and post-dispatch transit in Regions 9 and 4. Elevating these to the regional benchmark can turn roughly 4,300 late orders into on-time deliveries monthly.
2. **Re-evaluate Direct Discounts:** Run a randomized AB test shifting promotional budget away from flat Direct Discounts toward volume-linked alternatives, measuring outcomes against *contribution margins* instead of gross volumes alone.
3. **Cautious PLUS Expansion:** Protect the core base in Tier 1 cities. Do not expand acquisition to Tier 3–5 cities based on order counts alone until subscription margins, benefit costs, and retention metrics are securely quantified.

