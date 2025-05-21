
# 🏏 IPL Data Analysis with SQL

This project showcases an end-to-end analysis of IPL (Indian Premier League) data using advanced SQL techniques. It includes creating tables from CSV files, cleaning data, deriving insights, and building analytical outputs for potential use in player performance evaluation and auction strategy.

---

## 📁 Dataset Overview

Two main datasets were used:

- `IPL_BALL.csv`: Ball-by-ball delivery level data
- `IPL_MATCHES.csv`: Match metadata

---

## 🛠️ Technologies Used

- PostgreSQL (SQL)
- CSV Data Import
- Analytical Querying & Data Derivation

---

## 🗃️ Database Schema

**Tables Created:**

- `IPL_BALL`: Contains delivery-level information
- `IPL_MATCH`: Match metadata like city, teams, toss, etc.
- `DELIVERIES_V02`: Derived table adding `BALL_RESULT` (Boundary, Dot, Others)
- `DELIVERIES_V03`: Further enriched with match venue and date

---

## 📊 Key Analyses Performed

### 🔥 Top Batsmen
- **Aggressive Batsmen** by Strike Rate
- **Anchor Batsmen** by Batting Average
- **Boundary Hitters** by % of Runs from 4s and 6s

### 🎯 Top Bowlers
- **Economical Bowlers** by Economy Rate
- **Wicket-Takers** by Bowling Strike Rate

### 🏆 All-Rounders
- Players with high Batting and Bowling Strike Rates

### 📍 Venue & Match Insights
- Total Cities Hosting Matches
- Venue-wise Runs
- Eden Gardens: Yearly Runs Trend

### 💡 Additional Stats
- Most Extra Runs Conceded
- Dot Ball & Boundary Distribution
- Dismissal Types Breakdown

---

## 🧮 Sample Queries

```sql
-- Top 10 Aggressive Batsmen
SELECT BATSMAN, SUM(BATSMAN_RUNS) AS TOTAL_RUNS, COUNT(BALL) AS BALLS_PLAYED,
ROUND((SUM(BATSMAN_RUNS)*1.0/COUNT(BALL))*100,2) AS STRIKE_RATE
FROM IPL_BALL
WHERE EXTRA_TYPE NOT IN ('wides')
GROUP BY BATSMAN
HAVING COUNT(BALL)>500
ORDER BY STRIKE_RATE DESC
LIMIT 10;
```

---

## 📌 Note

This project was created as part of a data science course to demonstrate SQL-based analytics on sports datasets.

---

