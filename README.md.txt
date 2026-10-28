# Mobile Game Monetization Analytics & Data Engineering 🎮📊

## 📌 Project Overview
This project demonstrates a full-cycle Data Engineering and Analytics pipeline for a Free-to-Play (F2P) mobile game. The primary goal is to simulate, process, and analyze in-app purchase (IAP) data to understand user retention and lifetime value (LTV).

*   **Role:** Data Engineer / Product Analyst
*   **Industry:** Gaming / Mobile Apps
*   **Key Metrics Analyzed:** Retention Rate, ARPU, Cumulative LTV, Churn.

## 🛠 Tech Stack
*   **Languages:** Python (Pandas, Numpy)
*   **Database:** SQLite
*   **SQL Concepts:** Common Table Expressions (CTE), Window Functions (`SUM() OVER()`), Date/Time manipulation (`JULIANDAY`).
*   **Visualization:** Matplotlib

## 🏗 Architecture & Pipeline
The project is divided into three main phases:

### 1. Data Synthesis (Python)
Due to the confidentiality of real gaming financial data, a custom Python script was created to simulate realistic user behavior.
*   Generated **2,000+ unique users** and **9,800+ event logs**.
*   Implemented cohort logic: **90% F2P (Free-to-Play), 8% Dolphins, 2% Whales**, with respective retention and purchase probabilities.
*   Introduced data anomalies (e.g., `NaN` timestamps) to simulate real-world raw data conditions.

### 2. ETL Process (Pandas & SQLite)
*   **Extract & Transform:** Loaded the raw data, cleaned missing values, formatted timestamps, and normalized the dataset into two distinct entities (`users` and `events`).
*   **Load:** Used Python's `sqlite3` library (`executemany`) for fast batch insertion into a local relational database (`game_analytics.db`).

### 3. Advanced SQL Analytics
Wrote complex SQL queries to calculate business metrics. The core query calculates **Cumulative LTV by Day of Life (Day 0 to Day 14)** using:
*   `WITH` clauses to isolate user cohorts and calculate daily revenue.
*   Window functions (`ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW`) to calculate the running total of revenue per user.

## 📈 Key Insights & Results

![LTV Chart](ltv_chart.png)

*   **LTV Growth:** The cumulative ARPU grows from **$0.32** on Day 0 to **$3.50** by Day 14.
*   **Retention:** A sharp drop-off is observed after Day 1 (typical for F2P games), highlighting the importance of early monetization strategies for "Whale" segments.

## 🚀 How to Run Locally
1. Clone this repository to your local machine.
2. Ensure you have the required libraries installed: `pip install pandas numpy matplotlib`
3. Open and run the Jupyter Notebook `main.ipynb` step-by-step.