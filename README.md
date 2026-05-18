# 🏢 RheinTrade Solutions V2: Enterprise BI, Advanced DAX & ML-Driven Analytics

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python_3.10-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Machine Learning](https://img.shields.io/badge/Machine_Learning-K--Means_&_Holt--Winters-FF6F00?style=for-the-badge)
![DAX](https://img.shields.io/badge/Advanced_DAX-Data_Modeling-005571?style=for-the-badge)

## 📌 Executive Summary
**RheinTrade Solutions V2** represents the advanced Business Intelligence and Machine Learning evolution of the foundational ERP system. Transitioning from SQL/Excel analytics, this comprehensive Power BI web-application empowers executives with dynamic deep-dive insights into product profitability, historical cost tracking, customer risk segmentation, and time-series revenue forecasting.

At the core of this project is a seamless integration of **App-like UI/UX design**, **Advanced DAX temporal modeling**, and **Unsupervised Machine Learning (K-Means Clustering & Exponential Smoothing)** to identify high-value B2B partners at risk of churn and project future growth.

---

## 🤖 Machine Learning Integration (Python)

### 1. Advanced K-Means Clustering (B2B Churn Prediction)
* **Objective:** Move beyond static categorization by dynamically grouping B2B partners based on a custom 4-dimensional behavior model (Recency, Total Orders, Revenue, and Net Profit) using Scikit-Learn.
* **Business Logic Tuning:** Calibrated the Recency threshold to **210 days** in collaboration with domain logic, ensuring active clients are not falsely flagged as churning.
* **Insight:** The ML model successfully isolated high-value B2B partners who exceeded critical inactivity thresholds, categorizing them as "Sleeping Giants" and "Churning Stars". 
* **Executive Action:** Identified critical historical revenue currently at risk, prompting immediate targeted interventions by the sales team.

> * **🧠 Model Variance Analysis (Feature Importance):**
> * *Recency (31.16%) | Monetary/Revenue (24.02%) | Frequency/Orders (23.50%) | Net Profit (21.32%)*

📊 **K-Means Cluster Personas & Risk Matrix**

| Cluster Persona | Risk Level | Recency | Frequency (Orders) | Monetary (Revenue/Profit) | Strategic Action |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Platinum Champions** | Low 🟢 | < 210 Days | High Volume | High Yield | VIP Loyalty & Retention |
| **Active Regulars** | Low 🟢 | < 210 Days | Consistent | Moderate Yield | Upsell / Cross-sell |
| **Sleeping Giants** | High 🔴 | ~ 180 Days | Historically Low | Historically High | Targeted Re-engagement |
| **Churning Stars** | Critical 🚨 | > 210 Days | Historically High | Historically High | Immediate Intervention |

* 📁 [View Python ML Notebook](scripts/01_B2B_Customer_Segmentation_KMeans.ipynb) 

### 2. Holt-Winters Time-Series Forecasting
* **Objective:** Generate Macro (company-wide) and Granular (Sub-Category level) revenue forecasts for Q1 2026.
* **Insight:** Utilized Exponential Smoothing (`statsmodels`) with additive trend and seasonality. Truncated sparse early-2026 data to prevent artificial model skewing. The granular forecasts enable highly targeted operational and inventory planning per product category.

* 📁 [View Python Forecasting Notebook](scripts/02_Revenue_Forecasting_HoltWinters.ipynb) 

---

## 📊 Interactive BI Dashboards & Analytical Modules

### 1. Executive Overview & ML Forecasting
* **Objective:** Provide a high-level, actionable snapshot of company-wide KPIs, combining historical quarter-over-quarter (QoQ) performance with forward-looking predictive analytics.
* **Technical Implementation:** Integrated Python-generated time-series forecasts directly into the main revenue trendline. Utilized a Decomposition Tree for dynamic root-cause analysis (drilling down from Main Category to specific Product Groups) and engineered custom report page tooltips to reveal hidden trendlines (e.g., Monthly Orders) on hover.
* **Business Insight:** Executives can instantly evaluate current performance against previous quarters while viewing the Q1 2026 revenue trajectory. The combination of the decomposition tree and dynamic tooltips allows users to rapidly investigate specific portfolios (e.g., *Indoor AI Cameras*) without leaving the macro-level view, enabling quick identification of profitability and return rate anomalies.

  *(Main Executive Dashboard with Q1 2026 Forecast)*
* ![Executive Overview](images/1.ExecutiveOverviewPage.png)

  *(Custom Interactive Category Tooltip)*
* ![Category Tooltip](images/1.ExecutiveOverviewPage2.png)

### 2. Customer Retention & ML Risk Assessment
* **Objective:** Operationalize the Python K-Means clustering model within Power BI to proactively monitor and mitigate B2B customer churn.
* **Technical Implementation:** Translated the Python-generated RFM clusters into a dynamic scatter plot, plotting Recency (Days) against Total Revenue. Engineered targeted DAX measures to instantly calculate the exact monetary value and percentage of historical revenue currently at risk.
* **Business Insight:** The dashboard visually isolates the "at-risk" personas ("Churning Stars" and "Sleeping Giants") from healthy accounts. It clearly identifies that 6 high-value partners have exceeded the critical 210-day inactivity threshold, putting €1.57M (15.38% of total B2B revenue) at risk. This specific quantification provides the executive team with a concrete, data-driven action plan for immediate sales intervention.


* ![Customer Retention](images/5.CustomerRetention&RiskPage.png)

### 3. Product 360° Deep-Dive (Drill-through)
* **Objective:** Deliver an isolated, highly granular analytical environment dedicated to individual product performance, accessible via drill-through from macro-level summary dashboards.
* **Technical Implementation:** Integrated "Dynamic Field Parameters," empowering users to seamlessly toggle the primary area chart across multiple metrics (Revenue, Profit, Margin, Returns, etc.) without cluttering the canvas. Additionally, engineered a DAX-driven "What-If" parameter to simulate price elasticity.
* **Business Insight:** This module transforms static reporting into an interactive scenario-planning tool. Product managers can use the "Price Adjustment" slider to instantly project how a hypothetical price change (e.g., a 10% increase) would alter the profit trajectory of a specific item like the *VisionAI Indoor 360 Cam*. Coupled with real-time quarterly target tracking gauges, it enables rapid, data-driven pricing and marketing decisions.

* ![Product 360](images/3.Product360Page.png)

### 4. B2B Customer Intelligence & Segmentation
* **Objective:** Deliver a comprehensive analytical environment to evaluate the overall performance of the corporate customer base, providing a unified view of all B2B accounts alongside broader segment comparisons.
* **Technical Implementation:** Engineered interactive bookmark toggles to seamlessly switch between revenue and active customer metrics. The page integrates strict DAX filter contexts (e.g., calculating `Average Revenue per Customer` exclusively for the selected tier) and utilizes dynamic Smart Narratives to auto-generate text summaries of top-performing accounts.
* **Business Insight:** The segmentation charts reveal a critical strategic takeaway: Although the "Unsegmented" group generates the highest overall Total Revenue, it yields the lowest Average Revenue per Customer (€106K). In stark contrast, "B2B - Strategic Partners" deliver nearly triple that average (€297K). This proves that directing sales resources toward dedicated corporate accounts is significantly more efficient and lucrative than relying on mass-market volume.


* ![B2B Customer Intelligence](images/4.B2BCustomerIntelligencePage.png)

### 5. Spatial Revenue Analysis (Global Interactive Map)
* **Objective:** Provide a geographical breakdown of sales performance, profitability, and customer distribution for all customers globally.
* **Technical Implementation:** Enhanced the standard map visual with macro-regional slicers (North America vs. Europe) and a custom multi-KPI tooltip. Hovering over any country (e.g., United States) instantly displays a complete regional snapshot, including Revenue, Net Profit, Total Customers, and Quantity Sold.
* **Business Insight:** Executives can identify regional inefficiencies at a glance. Spotting territories with high order volumes but disproportionately low profit margins enables rapid adjustments to regional logistics and pricing strategies.

* ![Geographical Analysis Map](images/2.MapPage.png)

### 6. Persistent Sidebar Navigation & Global Control Panel
* **Objective:** Transform the standard Power BI report into a seamless, SaaS-like web application with intuitive UI/UX design.
* **Insight:** Engineered a static left-hand navigation pane featuring synchronized global slicers (Year and Region) that maintain strict filter context across all analytical modules. 
* **Smart Features:** Includes custom page navigation flows, a dedicated "Clear Filters" action powered by advanced bookmarking, and strategic alert shortcuts routing executives directly to the high-priority "Customer Risk" matrix.


* ![Navigation Sidebar](images/7.Navigation&SlicerPanel.png)

---

## ⚙️ Advanced Data Engineering & DAX Architecture
Building upon the foundational SQL database, this phase introduces a highly sophisticated tabular data model optimized for complex analytical contexts.

* **Temporal Data & SCD Type 2 (Historical Costing):** Engineered a robust time-travel DAX architecture. The `Total Cost` and `Total Profit` measures dynamically scan the `Product Price History` table to fetch the exact historical cost based on the specific `OrderDate`. This preserves data integrity and prevents historical margin mutation over time.
* **Denominator Trap Prevention & Return Analytics:** Redesigned gross-to-net return rate measures utilizing `COALESCE` and targeted context filters. This eliminates infinity/blank errors during zero-sales months and prevents misleading flatlines on temporal area charts.
* **Smart Bookmarking & Contextual Navigation:** Developed a persistent, SaaS-like sidebar navigation pane. Implemented strict "Selected Visuals" bookmarking to allow users to reset specific global slicers without breaking page-level drill-through context filters.

---

## 🚀 How to Use This Repository

1. **Explore the Machine Learning Models:**
   * Navigate to the `scripts/` folder to view the Python Jupyter Notebooks.
   * `01_B2B_Customer_Segmentation_KMeans.ipynb`: Contains the data preprocessing and clustering logic.
   * `02_Revenue_Forecasting_HoltWinters.ipynb`: Contains the time-series forecasting algorithms and visualizations.

2. **Interact with the Power BI Dashboard:**
   * Download the `dashboards/RheinTrade_Analytics_V2.pbix` file.
   * Open it using **Microsoft Power BI Desktop**.
   * *Pro-Tip for the best UI/UX experience:* Once opened, click the **"Full Screen"** icon in the bottom right corner (or collapse the side panels) to interact with the dashboard in an app-like, SaaS environment.


---
*If you have any questions or would like to discuss the methodologies used in this project, feel free to reach out via LinkedIn.*
