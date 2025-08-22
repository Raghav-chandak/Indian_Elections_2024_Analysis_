# Indian_Elections_2024_Analysis_
---
##  Project Overview  
This project analyzes the **India General Election Results – 2024** using **Power BI dashboards** and **SQL queries**.  
It provides insights into party performance, state demographics, constituency-level outcomes, and overall election trends.  

The project is designed for **political analysts, researchers, policymakers, and the public** to better understand the 2024 Lok Sabha results.  

---

##  Dashboards  

### 1. **Overview Analysis**  
- NDA seats, % share, and detailed breakdown  
- I.N.D.I.A. seats, % share, and detailed breakdown  
- Independent & Other party seats  
- Party-wise performance with logos
- <img width="1142" height="654" alt="image" src="https://github.com/user-attachments/assets/a14c99c4-3729-4e00-80ac-6b658391b13b" />

---

### 2. **State Demographics Analysis**  
- State-wise total seats, NDA seats, I.N.D.I.A. seats  
- Map chart with tooltips (majority alliance, total seats)  
- Winning candidate & margin (bubble map view)  
- State with maximum seats won
- <img width="1144" height="656" alt="image" src="https://github.com/user-attachments/assets/825971db-3edf-44b4-909c-b7e9bc868d82" />

---

### 3. **Political Landscape by State**  
- Dynamic state filter  
- Party-wise grid results with alliances  
- Party-wise seat share (donut chart)  
- Map of constituencies in the selected state
- <img width="1140" height="656" alt="image" src="https://github.com/user-attachments/assets/7f061ca3-5ba7-4de3-a4c3-1b4c68ffec26" />

---

### 4. **Details Grid**  
- Full tabular dataset (constituency → winner, runner-up, alliance, votes, margin)  
- Drill-through from other dashboards  
- Export to Excel option
<img width="1138" height="652" alt="image" src="https://github.com/user-attachments/assets/ce0bdac5-ef69-4b6c-99b8-0e4ae6312aac" />

---

##  Tech Stack  
- **Power BI Desktop** – Data visualization & dashboard building  
- **SQL (MS SQL Server)** – Data extraction and transformation  
- **Dataset(Kaggle)** – Constituency-wise, state-wise, and party-wise election results (India 2024)  

---

##  Dataset  
The dataset includes:  
- **Constituency-wise results**  
- **State-wise results**  
- **Party-wise results**  
- Candidate-level details (EVM votes, postal votes, margins)  

---

##  SQL Queries & Analysis  

Some example queries used in the analysis:  

```sql
-- Total Seats
SELECT DISTINCT COUNT(Parliament_Constituency) AS Total_Seats
FROM constituencywise_results;

-- Total Seats by State
SELECT s.State AS State_Name,
       COUNT(cr.Constituency_ID) AS Total_Seats_Available
FROM constituencywise_results cr
JOIN statewise_results sr ON cr.Parliament_Constituency = sr.Parliament_Constituency
JOIN states s ON sr.State_ID = s.State_ID
GROUP BY s.State
ORDER BY s.State;

-- NDA Total Seats Won
SELECT SUM(CASE WHEN party IN ('Bharatiya Janata Party - BJP', 'Telugu Desam - TDP', 'JD(U)', 'Shiv Sena - SHS', ...)
                THEN [Won] ELSE 0 END) AS NDA_Total_Seats_Won
FROM partywise_results;
```
Full list of queries - see SQL_queries_file from files uploaded

---

## Key Insights

- **NDA Alliance won 292 seats (54%) across India.**

-**I.N.D.I.A. Alliance secured 234 seats (43%).**

-**Others & Independents managed 17 seats (3%).**

-**Largest NDA contribution: BJP (240 seats).**

-**Largest I.N.D.I.A. contribution: INC (99 seats).**

---

## How to Use

**Clone this repository**
```bash
git clone https://github.com/Raghav-chandak/Indian_Elections_2024_Analysis_.git
cd Indian_Elections_2024_Analysis_
```

**Open the dataset (data.csv) in SQL Server and run the queries (SQL_Queries_file).**

**Open the Power BI file (power_bi_analysis.pbix) to explore dashboards.**

**Refer to power_bi_analysis.pdf for a static preview.**

---

## Future Improvements

**Add predictive analytics (seat forecasting models).**

**Build interactive web dashboard using Plotly/Dash or Streamlit.**

**Expand dataset to include voter turnout demographics.**
